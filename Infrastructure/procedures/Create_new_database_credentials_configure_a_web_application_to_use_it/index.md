---
title: WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it
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
<li> <a href="/wiki/WPD:Infrastructure/procedures/Managing_MySQL_replication" title="WPD:Infrastructure/procedures/Managing MySQL replication">Managing MySQL replication</a></li>
<li> <strong class="selflink">Create new database credentials and configure a web application to use it</strong></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">Maintaining ElasticSearch cluster</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_email_services" title="WPD:Infrastructure/procedures/Maintaining email services">Maintaining email services</a></li></ul>
</div>
<h1><span class="mw-headline" id="Create_new_database_credentials_and_configure_a_web_application_to_use_it">Create new database credentials and configure a web application to use it</span></h1>
<p>... or <b>"How to change database configuration and ensure every affected web application gets the new passswords"</b>.
</p><p>The concept of states are ideal to manage many aspects of a running system. But one of the "gray zones" are about database credentials, or whether or not we should send commands to set database credentials at every deployment system "apply configuration" run. For this reason we do not enforce them in the salt states.
</p><p>But what if we want to change the database details? Here’s how.
</p><p>In this example, we’ll  create a new database for our WordPress blog instance, import an existing snapshot and apply the new database configuration and deploy it. In this tutorial we will focus solely on the use of the deployment system ("salt stack") and the deployment itself.
</p>
<h2><span class="mw-headline" id="Procedure">Procedure</span></h2>
<ul><li> Create a new database</li></ul>
<pre> salt -G 'roles:masterdb' mysql.db_create wpblog utf8 utf8_general_ci
</pre>
<ul><li> Add a new database user and privileges</li></ul>
<pre> salt -G 'roles:masterdb' mysql.user_create user_blog '%' somepassword
 salt -G 'roles:masterdb' mysql.grant_add 'ALL' 'wpblog.*' 'user_blog' '%'
</pre>
<ul><li> Check if the secondary database replication servers are in good state</li></ul>
<pre> salt -G 'roles:db' mysql.get_slave_status
</pre>
<p>The following details of the output means "<i>all is OK!</i>"
</p>
<pre>   Seconds_Behind_Master:
       0
   Slave_IO_Running:
       Yes
   Slave_IO_State:
       Waiting for master to send event
   Slave_SQL_Running:
       Yes
</pre>
<ul><li> Check if Monit says the database servers are fine too. If everything says "<i>running</i>" its all great!</li></ul>
<pre> salt -G 'roles:db' monit.summary
 db2:
   ----------
   Process:
       ----------
       exim4:
           Running
       mysql:
           Running
       openssh-server:
           Running
       salt-minion:
           Running
   System:
       ----------
       db2.production.wpdn:
           Running
 db1-masterdb:
   ----------
   Process:
       ----------
       exim4:
           Running
       mysql:
           Running
       openssh-server:
           Running
       salt-minion:
           Running
   System:
       ----------
       db1-masterdb.production.wpdn:
           Running
</pre>
<ul><li> Import the previous database snapshot
<ul><li> <i>scp</i> the database backup file to the current <b>masterdb</b> VM</li>
<li> import the database into the server (e.g. <b>mysql wpblog &lt; wpblog.sql</b>)</li>
<li> the other VMs with the role db (the ones that doesn’t have "masterdb" in their name) should catch up automatically with the replication</li></ul></li>
<li> Change the database details you just created in the pillar file. If the command was run from production, the file to change would be <b>/srv/private/pillars/accounts/production.sls</b></li>
<li> To review what’s going to be applied will be <i>/srv/salt/vm/blog.sls</i>. That is because the role we are working on at this moment is "blog". If you want to review why, take a look at the <a href="/wiki/WPD:Infrastructure/architecture/Roles_and_environment_level" title="WPD:Infrastructure/architecture/Roles and environment level">section about roles</a> and the <a href="/wiki/WPD:Infrastructure/architecture/VM_roles" title="WPD:Infrastructure/architecture/VM roles">details of each roles</a>. </li>
<li> Make the configuration file to be applied on top of the web app configuration. </li></ul>
<pre> wpd-deploy blog
</pre>
<p>It should look like in this image, with all "green", but of course with the mention of "blog" instead of "app".
</p><p><a href="/wiki/File:Running_wpd-deploy.png" class="image"><img alt="Running wpd-deploy.png" src="//static.webplatform.org/w/public/0/0d/Running_wpd-deploy.png" width="1291" height="1004" /></a>
</p>
<ul><li> Last step is to apply <i>state.highstate</i>. Its OK to run it more than once, the configuration are written to enforce a state and can be applied in any order, the important is to get all "green".</li></ul>
<pre> salt blog state.highstate
</pre>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:58621-0!*!0!!*!5!*!esi=1 and timestamp 20150731185825 and revision id 101258
 -->
