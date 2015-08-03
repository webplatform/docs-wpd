---
title: WPD:Infrastructure/architecture/Reports to review status
---
<div style="float:right;width:33%;word-wrap:break-word;clear:both;">
<h3><span class="mw-headline" id="WebPlatform_server_Infrastructure_architecture_menu"><a href="/wiki/WPD:Infrastructure/architecture" title="WPD:Infrastructure/architecture">WebPlatform server Infrastructure architecture menu</a></span></h3>
<div class="subpagelist">
<ul><li> <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM" title="WPD:Infrastructure/architecture/Base configuration of a VM">Base configuration of a VM</a></li>
<li> <strong class="selflink">Reports to review status</strong></li>
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
<li> <a href="/wiki/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it" title="WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it">Create new database credentials and configure a web application to use it</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">Maintaining ElasticSearch cluster</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_email_services" title="WPD:Infrastructure/procedures/Maintaining email services">Maintaining email services</a></li></ul>
</div>
<h1><span class="mw-headline" id="Reports_to_review_status">Reports to review status</span></h1>
<p>From the  <a href="/wiki/WPD:Infrastructure/architecture/The_salt_master" title="WPD:Infrastructure/architecture/The salt master">The Salt Master</a> we can get various system health status. This document describes how to access them.
</p>

<h1><span class="mw-headline" id="Reports">Reports</span></h1>
<h2><span class="mw-headline" id="How_many_emails_has_been_sent">How many emails has been sent</span></h2>
<p>We have  <a rel="nofollow" class="external text" href="http://mailgraph.schweikert.ch/"><i>Mailgraph</i></a> installed on all <i>mail</i> VMs. With it, we can visualize how many emails are being sent to our mail server. It should display the number of refusals (e.g. somebody outside our network trying to use us) over time.
</p><p>From the browser, through <a href="#Read_reports_from_a_VM_through_private_network">#Read reports from a VM through private network</a>.
</p>
<pre> <a rel="nofollow" class="external free" href="http://mail/cgi-bin/mailgraph.cgi">http://mail/cgi-bin/mailgraph.cgi</a>
</pre>
<p>Should look like this:
</p><p><a href="/wiki/File:20150106_mailgraph_day.png" class="image"><img alt="20150106 mailgraph day.png" src="//static.webplatform.org/w/public/d/da/20150106_mailgraph_day.png" width="637" height="243" /></a>
<a href="/wiki/File:20150104_mailgraph_day.png" class="image"><img alt="20150104 mailgraph day.png" src="//static.webplatform.org/w/public/4/44/20150104_mailgraph_day.png" width="637" height="243" /></a>
</p><p><b>Note</b> please disregard the address in the screenshot, it has been taken during deployment scripts has been set in place.
</p>
<h2><span class="mw-headline" id="Getting_to_know_the_status_of_a_php5-fpm_backend">Getting to know the status of a php5-fpm backend</span></h2>
<p>You can make a basic <i>GET /php-status</i> to any VMs that has <b>php5-fpm</b> running. (@@TODO make a role to get all of them and remove the need to guess)
</p><p>There are a few variants we can get data;
</p>
<ul><li> Simple report</li></ul>
<pre> curl piwik/php-status
</pre>
<ul><li> A more detailed report of each worker process</li></ul>
<pre> curl piwik/php-status?full
</pre>
<ul><li> "Ping" check if <i>php5-fpm</i> connection is accessible from NGINX</li></ul>
<pre> curl piwik/php-ping
</pre>
<p><a href="/wiki/File:nginx_fastcgi_status_full.png" class="image"><img alt="nginx fastcgi status full.png" src="//static.webplatform.org/w/public/3/3f/nginx_fastcgi_status_full.png" width="496" height="838" /></a>
<a href="/wiki/File:nginx_fastcgi_status.png" class="image"><img alt="nginx fastcgi status.png" src="//static.webplatform.org/w/public/f/f5/nginx_fastcgi_status.png" width="690" height="368" /></a>
</p><p><b>Note</b> that in this example I used an SSH tunnel <i>-L 8080:piwik:80</i>, but it could have been done through <a href="#Read_reports_from_a_VM_through_private_network">#Read reports from a VM through private network</a>.
</p>
<h2><span class="mw-headline" id="Getting_to_know_the_status_of_an_NGINX_web_server">Getting to know the status of an NGINX web server</span></h2>
<ul><li> From the local network</li></ul>
<pre> curl piwik/nginx-status
 Active connections: 1
 server accepts handled requests
  3031 3031 3024
 Reading: 0 Writing: 1 Waiting: 0
</pre>
<ul><li> From salt</li></ul>
<pre> salt piwik nginx.status
 piwik:
   ----------
   accepted:
       3030
   active connections:
       1
   handled:
       3030
   reading:
       0
   requests:
       3023
   waiting:
       0
   writing:
       1
 
</pre>
<h2><span class="mw-headline" id="Getting_to_know_the_status_of_an_Apache2_web_server">Getting to know the status of an Apache2 web server</span></h2>
<ul><li> From salt</li></ul>
<pre> salt app\* apache.server_status
 app3:
   ----------
   BusyWorkers:
       3
   BytesPerReq:
       865.907
   BytesPerSec:
       3152.89
   CPULoad:
       0.300867
   IdleWorkers:
       16
   ReqPerSec:
       3.64114
   Scoreboard:
       ----------
       .:
           45
       C:
           2
       D:
           0
       G:
           0
       I:
           0
       K:
           0
       L:
           0
       R:
           0
       S:
           0
       W:
           1
       _:
           16
   Total Accesses:
       40748
   Total kBytes:
       34457
   Uptime:
       11191
</pre>
<h2><span class="mw-headline" id="Nutcracker">Nutcracker</span></h2>
<p>Nutcracker should run on any VM that runs a backend.
</p><p>You can query its status from the VM itself, through the localhost loopback (only!) by doing a <i>GET</i> request like this:
</p>
<pre> curl localhost:22222 | python -m json.tool
 {
   "sessions_redis": {
       "10.10.10.177:6379": {
           "in_queue": 0,
           "in_queue_bytes": 0,
           "out_queue": 0,
           "out_queue_bytes": 0,
           "request_bytes": 2681,
           "requests": 28,
           "response_bytes": 713,
           "responses": 27,
           "server_connections": 0,
           "server_ejected_at": 0,
           "server_eof": 1,
           "server_err": 0,
           "server_timedout": 1
       },
       "client_connections": 0,
       "client_eof": 0,
       "client_err": 14,
       "forward_error": 1,
       "fragments": 0,
       "server_ejects": 0
   },
   "source": "app1",
   "timestamp": 1425064419,
   "uptime": 9285,
   "version": "0.3.0"
 }
</pre>
<p><b>Note</b> the output has been truncated to only one backend to illustrate what data the call provides.
</p>
<ul><li> Use salt to get data</li></ul>
<pre> salt -C 'G@roles:app or G@roles:blog or G@roles:piwik or G@roles:project' cmd.run 'curl -s localhost:22222'
 // Data will be similar to the previous example
</pre>
<p><br />
Notice how I am targeting the minions using <a rel="nofollow" class="external text" href="http://docs.saltstack.com/en/latest/topics/targeting/compound.html">Salt Compound matcher</a> and asking it to give me Nutcracker status data.
</p><p>Eventually we could use similar mechanism to gather status on services to learn how the server is going.
</p>
<h2><span class="mw-headline" id="MySQL.2FMariaDB">MySQL/MariaDB</span></h2>
<p>We can check what’s the state of the MySQL server by issuing the following commands.
</p><p>They are available through <a rel="nofollow" class="external text" href="http://docs.saltstack.com/en/latest/ref/modules/all/salt.modules.mysql.html#salt.modules.mysql.get_slave_status"><i>Salt Stack</i> <b>mysql</b> module</a>
</p>
<h3><span class="mw-headline" id="Get_replication_status">Get replication status</span></h3>
<pre> salt db2 mysql.get_slave_status
 db2:
   ----------
   Connect_Retry:
       10
   Master_Host:
       masterdb.local.wpdn
   Master_SSL_Allowed:
       Yes
   Master_SSL_CA_File:
       /etc/mysql/ca-cert.pem
   Master_SSL_Cert:
       /etc/mysql/client-cert.pem
   Master_SSL_Crl:
       /etc/mysql/ca-cert.pem
   Master_SSL_Key:
       /etc/mysql/client-key.pem
 // ... truncated  

</pre>
<h3><span class="mw-headline" id="Get_replication_master_status">Get replication master status</span></h3>
<pre> salt -G 'roles:masterdb' mysql.get_master_status
 db1-masterdb:
   ----------
   File:
       mariadbrepl-bin.000093
   Position:
       32058870
 // ... truncated
</pre>
<h3><span class="mw-headline" id="Get_process_list">Get process list</span></h3>
<pre> salt -G 'roles:db' mysql.processlist
 db2:
   |_
     ----------
     Command:
         Connect
     Id:
         3
     Info:
         None
     Progress:
         0.0
     State:
         Slave has read all relay log; waiting for the slave I/O thread to update it
     Time:
         1
     User:
         system user
     db:
         None
</pre>
<h3><span class="mw-headline" id="Misc._reports_available_on_MySQL_servers_through_Salt_stack">Misc. reports available on MySQL servers through Salt stack</span></h3>
<p>Here are a few possibly useful commands to pick from;
</p><p><b>Note</b> its even possible to work on grants/privileges, add/delete databases. Note that if you do so, you MUST make sure that you do it ONLY on the salt master. To learn more, refer to <a rel="nofollow" class="external text" href="http://docs.saltstack.com/en/latest/ref/modules/all/salt.modules.mysql.html#salt.modules.mysql.get_slave_status"><i>Salt Stack</i> documentation at <b>mysql</b> module</a>.
</p>
<pre> salt db2 mysql.get_slave_status
 salt -G 'roles:masterdb' mysql.get_master_status
 salt -G 'roles:db' mysql.status
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="MediaWiki">MediaWiki</span></h2>
<p>Some reports can be gathered from the MediaWiki API. Here’s a list of a few useful ones. If you want to change the way they are displayed, you can change the <i>&amp;format=</i> URL fragment (ref: <a class="external text" href="https://www.mediawiki.org/wiki/API:Main_page#The_format"><i>MediaWiki.org</i> documentation</a>.
</p>
<h3><span class="mw-headline" id="Misc._reports">Misc. reports</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="https://docs.webplatform.org/w/api.php?format=jsonfm&amp;action=query&amp;prop=contributors&amp;continue=&amp;titles=css/properties/border">Contributors on <b>css/properties/border</b> page (through the API)</a></li>
<li> <a rel="nofollow" class="external text" href="https://docs.webplatform.org/wiki/Special:Contributions/Renoirb">Contributions made by a specific user</a></li>
<li> <a rel="nofollow" class="external text" href="https://docs.webplatform.org/w/api.php?format=jsonfm&amp;action=query&amp;list=users&amp;ususers=Renoirb&amp;usprop=blockinfo%7Cgroups%7Ceditcount%7Cemailable">More details about a user (through the API)</a></li></ul>
<h3><span class="mw-headline" id="User_creation_log">User creation log</span></h3>
<p>As long as we don’t have a separate accounts system in place for every components, including our wiki, we need to review in each web application the new accounts that are being created. If we have too many accounts created, it means that we might be under spambot attacks.
</p>
<ul><li> <a rel="nofollow" class="external text" href="https://docs.webplatform.org/w/api.php?format=jsonfm&amp;action=query&amp;list=logevents&amp;letype=newusers&amp;lelimit=50&amp;leprop=user%7Ctimestamp">list new users (through the API)</a></li></ul>
<p><a href="/wiki/File:20150106-account-creation-log-api.png" class="image"><img alt="20150106-account-creation-log-api.png" src="//static.webplatform.org/w/public/d/d3/20150106-account-creation-log-api.png" width="1878" height="1270" /></a>
</p>
<h3><span class="mw-headline" id="What.E2.80.99s_the_IP_address_of_a_given_user.3F">What’s the IP address of a given user?</span></h3>
<p>In case of need to review how our infrastructure is being abused, we can get to know the IP address of visitors so that we can effectively ban them.
</p><p>To do so, we are using the <a class="external text" href="https://www.mediawiki.org/wiki/Extension:CheckUser"><i>MediaWiki CheckUser</i> Extension</a>. Only users of the wiki with sysop privileges can review this information.
</p><p><a href="/wiki/File:20150108-visualizing-visitor-IP-vs-users.png" class="image"><img alt="20150108-visualizing-visitor-IP-vs-users.png" src="//static.webplatform.org/w/public/a/a3/20150108-visualizing-visitor-IP-vs-users.png" width="1768" height="1166" /></a>
</p>
<h2><span class="mw-headline" id="Using_Monit">Using Monit</span></h2>
<p>Monit is a software that you can configure to check if a service is accessible or running and how it can make sure its up automatically for you.
</p><p><b>More about Monit in <a href="/wiki/WPD:Infrastructure/Monitoring/Monit" title="WPD:Infrastructure/Monitoring/Monit">WPD:Infrastructure/Monitoring/Monit</a></b>
</p>
<h3><span class="mw-headline" id="From_the_salt_master">From the salt master</span></h3>
<p>We can get <b>monit</b> reports <b>from the salt master</b> like this
</p>
<pre> salt -G 'roles:app' monit.summary
 app2-jobrunner:
   ----------
   Process:
       ----------
       apache2:
           Running
       nutcracker:
           Running
       openssh-server:
           Running
       salt-minion:
           Running
   System:
       ----------
       app2-jobrunner.production.wpdn:
           Running
 app1:
   ----------
   Process:
       ----------
       apache2:
           Running
       nutcracker:
           Running
       openssh-server:
           Running
       salt-minion:
           Running
   System:
       ----------
       app1.production.wpdn:
           Running
</pre>
<p>Or from the same VM:
</p>
<pre> sudo salt-call monit.summary
 [INFO    ] Executing command 'monit summary' in directory '/root'
 local:
   ----------
   Process:
       ----------
       exim4:
           Running
       gdnsd:
           Running
       openssh-server:
           Running
       salt-master:
           Running
       salt-minion:
           Running
       syslog-ng:
           Running
   System:
       ----------
       salt.production.wpdn:
           Running
</pre>
<h3><span class="mw-headline" id="From_the_web_frontend">From the web frontend</span></h3>
<p>To do this, you need to create a SOCKS proxy like its described in <a href="#Read_reports_from_a_VM_through_private_network">#Read reports from a VM through private network</a>
</p><p>Once connected through ssh with the proxy described, you can connect like this:
</p>
<pre> <a rel="nofollow" class="external free" href="http://monit:p4ssword@sessions1:2812/">http://monit:p4ssword@sessions1:2812/</a>
</pre>
<p>Which should look like this;
</p><p><a href="/wiki/File:20150224-monit-status-preview.png" class="image"><img alt="20150224-monit-status-preview.png" src="//static.webplatform.org/w/public/5/5d/20150224-monit-status-preview.png" width="1079" height="850" /></a>
</p>
<h4><span class="mw-headline" id="Monit_password">Monit password</span></h4>
<p>The password is not "p4ssword", you’ll have to look at <b>/srv/private/pillar/accounts/</b> file yourself at <b>accounts:monit:admin_password</b> or in the VM itself at <b>/etc/monit/conf.d/defaults.conf</b>.
</p><p>An alternate way to get to know the password is to use salt like this:
</p>
<pre> salt-call pillar.get accounts:monit:admin_password
 local:
   p4ssword
</pre>
<h2><span class="mw-headline" id="Read_reports_from_a_VM_through_private_network">Read reports from a VM through private network</span></h2>
<p>To view the internal only reports, you need to setup your local machine to pass through our <i>Jumpbox</i>. The instructions are available in <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM#Accessing_a_VM_using_SSH" title="WPD:Infrastructure/architecture/Base configuration of a VM">Accessing a VM using SSH in <b>Base configuration of a VM'</b></a>
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:58607-0!*!0!!en!5!*!esi=1 and timestamp 20150731185754 and revision id 101036
 -->
