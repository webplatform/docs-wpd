---
title: WPD:Infrastructure/procedures/Managing MySQL replication
---
<div style="float:right;width:33%;word-wrap:break-word;clear:both;">
<h3><span class="mw-headline" id="WebPlatform_server_Infrastructure_architecture_menu"><a href="/wiki/WPD:Infrastructure/architecture" title="WPD:Infrastructure/architecture">WebPlatform server Infrastructure architecture menu</a></span></h3>
<div class="subpagelist">
<ul><li> <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM" title="WPD:Infrastructure/architecture/Base configuration of a VM">Base configuration of a VM</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status" title="WPD:Infrastructure/architecture/Reports to review status">Reports to review status</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Roles_and_environment_level" title="WPD:Infrastructure/architecture/Roles and environment level">Roles and environment level</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/SSL_certificates" title="WPD:Infrastructure/architecture/SSL certificates">SSL certificates</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/The_salt_master" title="WPD:Infrastructure/architecture/The salt master">The salt master</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish" title="WPD:Infrastructure/architecture/Things to consider when we expose service via Fastly and Varnish">Things to consider when we expose service via Fastly and Varnish</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Useful_commands" title="WPD:Infrastructure/architecture/Useful commands">Useful commands</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/VM_roles" title="WPD:Infrastructure/architecture/VM roles">VM roles</a></div></li></ul>
<p><b>See also</b>
</p>
<ul><li> <a href="/wiki/WPD:Infrastructure/procedures/Deploying_code_changes" title="WPD:Infrastructure/procedures/Deploying code changes">Deploying code changes</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Replacing_a_VM" title="WPD:Infrastructure/procedures/Replacing a VM">Replacing a VM</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration" title="WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration">Maintaining Fastly configuration</a></li>
<li> <strong class="selflink">Managing MySQL replication</strong></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it" title="WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it">Create new database credentials and configure a web application to use it</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">Maintaining ElasticSearch cluster</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_email_services" title="WPD:Infrastructure/procedures/Maintaining email services">Maintaining email services</a></li></ul>
</div>
<h1><span class="mw-headline" id="Managing_MySQL_Replication_over_SSL">Managing MySQL Replication over SSL</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>How to manage communication and replication between MySQL servers across data-centers.
</p>
<h3><span class="mw-headline" id="Conventions">Conventions</span></h3>
<p>This document will follow those facts as a convention.
</p>
<ul><li> Master MySQL server is known as <i>db1</i> and the replication is <i>db2</i></li></ul>
<h2><span class="mw-headline" id="In_a_few_bullet_points">In a few bullet points</span></h2>
<ol><li> In <code>/etc/mysql/my.cnf</code>, make sure that each node has 'ssl' alone, close to the SSL certificates</li>
<li> Create CA and self-signed certificates, see Salt TLS module (<a rel="nofollow" class="external text" href="http://docs.saltstack.com/ref/modules/all/salt.modules.tls.html">salt.modules.tls</a>)</li>
<li> Remove db2 MySQL entries from MediaWiki configuration files, sync them to <code>app*</code> servers</li>
<li> On db2,  Lock databases</li>
<li> On db2,  Dump database tables</li>
<li> On db2,  Unlock databases</li></ol>
<h3><span class="mw-headline" id="Memory_dump.2C_using_Salt_stack">Memory dump, using Salt stack</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="http://docs.saltstack.com/ref/modules/all/salt.modules.tls.html">TLS salt module</a></li></ul>
<pre>   salt 'db1*' tls.create_ca 'mysql' days=730 CN='db1-masterdb.production.wpdn' O='W3C' OU='WebPlatform Docs' emailAddress='EMAIL'
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="Checks">Checks</span></h2>
<h3><span class="mw-headline" id="Checking_if_SSL_is_supported">Checking if SSL is supported</span></h3>
<p>Connect to the MySQL server in question and check if <code>have_ssl</code> is to <i>YES</i>
</p>
<pre>   mysql&gt; SHOW VARIABLES LIKE 'have_ssl';
   +---------------+-------+
   | Variable_name | Value |
   +---------------+-------+
   | have_ssl      | YES   |
   +---------------+-------+
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="Procedures">Procedures</span></h2>
<h3><span class="mw-headline" id="Changing_MariaDB_replication_master">Changing MariaDB replication master</span></h3>
<p>Quoting what I wrote on <a rel="nofollow" class="external text" href="https://renoirboulanger.com/blog/2015/01/create-mariadb-cluster-replication-ssl-salt-stack/">a blog post I wrote on January 2015: Create a MariaDB cluster with replication over SSL</a>:
</p>
<ul><li> From the masterdb MySQL server, in a command line session</li>
<li> Lock writes on masterdb databases <code>FLUSH TABLES WITH READ LOCK;</code> (make sure this session stays open, the lock only lasts with the session you used to write it. See <a rel="nofollow" class="external text" href="https://mariadb.com/kb/en/mariadb/flush-tables-for-export/">MariaDB flush tables pages</a>)</li>
<li> From a secondary MySQL server; Wait replication to catch up <code>SHOW SLAVE STATUS\G</code></li>
<li> Remove replication configuration </li>
<li> Tell all web apps to use new database master (from the salt master, change the <b>infra:hosts_entries:masterdb</b> key in  <b>/srv/pillar/infra/production.sls</b> (or <b>/srv/pillar/infra/staging.sls</b> for staging).</li>
<li> From the masterdb; remove database lock by closing the session opened earlier</li>
<li> Setup new replication configuration to use new master</li></ul>
<p>@@TODO, Make a more precise procedure with new setup and how to manage.
</p><p><br />
</p>
<h2><span class="mw-headline" id="References">References</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="http://www.howtoforge.com/how-to-set-up-mysql-database-replication-with-ssl-encryption-on-debian-lenny">How to setup MySQL Databaes replication with SSL on Debian</a></li>
<li> <a rel="nofollow" class="external text" href="http://dev.mysql.com/doc/refman/5.1/en/replication-solutions-ssl.html">Oracle reference: MySQL: 16.3.7. Setting Up Replication Using SSL</a></li>
<li> <a rel="nofollow" class="external free" href="http://plusbryan.com/mysql-replication-without-downtime">http://plusbryan.com/mysql-replication-without-downtime</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.rackspace.com/knowledge_center/article/mysql-replication-masterslave">http://www.rackspace.com/knowledge_center/article/mysql-replication-masterslave</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.howtoforge.com/mysql_database_replication_p2">http://www.howtoforge.com/mysql_database_replication_p2</a></li>
<li> <a rel="nofollow" class="external free" href="http://dev.mysql.com/doc/refman/5.0/en/lock-tables.html">http://dev.mysql.com/doc/refman/5.0/en/lock-tables.html</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.mysqlperformanceblog.com/2012/07/31/innodb-table-locks/">http://www.mysqlperformanceblog.com/2012/07/31/innodb-table-locks/</a></li>
<li> <a rel="nofollow" class="external free" href="http://dev.mysql.com/doc/refman/5.0/en/replication-howto.html">http://dev.mysql.com/doc/refman/5.0/en/replication-howto.html</a></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:12487-0!*!0!!*!*!*!esi=1 and timestamp 20150731184838 and revision id 100773
 -->
