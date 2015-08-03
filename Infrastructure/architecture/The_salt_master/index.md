---
title: WPD:Infrastructure/architecture/The salt master
---
<div style="float:right;width:33%;word-wrap:break-word;clear:both;">
<h3><span class="mw-headline" id="WebPlatform_server_Infrastructure_architecture_menu"><a href="/wiki/WPD:Infrastructure/architecture" title="WPD:Infrastructure/architecture">WebPlatform server Infrastructure architecture menu</a></span></h3>
<div class="subpagelist">
<ul><li> <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM" title="WPD:Infrastructure/architecture/Base configuration of a VM">Base configuration of a VM</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status" title="WPD:Infrastructure/architecture/Reports to review status">Reports to review status</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Roles_and_environment_level" title="WPD:Infrastructure/architecture/Roles and environment level">Roles and environment level</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/SSL_certificates" title="WPD:Infrastructure/architecture/SSL certificates">SSL certificates</a></li>
<li> <strong class="selflink">The salt master</strong></li>
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
<h1><span class="mw-headline" id="The_Salt_Master">The Salt Master</span></h1>
<p><a href="/wiki/WPD:Infrastructure/procedures/Deploying_code_changes" title="WPD:Infrastructure/procedures/Deploying code changes">Deploying code changes on the site</a> is made through a VM, named "salt" we refer to this machine as the "Salt Master" we generally connect through SSH at the name <b>salt.webplatform.org</b>.
</p><p><b>Note</b> <i>staging</i> environment’ <i>salt master</i> is accessible as <b>salt.webplatformstaging.org</b>
</p><p>The software we use for configuration management is called <b><a rel="nofollow" class="external text" href="http://saltstack.com/">Salt Stack</a></b>, we refer to the machine that has a copy of all the configuration files.
</p><p>Commands that can be done from the <i>salt</i> VM in the terminal, but some could also be visualized from within your local web browser through <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status#Read_reports_from_a_VM_through_private_network" title="WPD:Infrastructure/architecture/Reports to review status">Read reports from a VM through private network</a> in <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status" title="WPD:Infrastructure/architecture/Reports to review status">WPD:Infrastructure/architecture/Reports_to_review_status</a>.
</p>
<h2><span class="mw-headline" id="Also_configured_...">Also configured ...</span></h2>
<ul><li> Runs fail2ban and <i>bans</i> successive unsuccessful login attempts (Possible attacks)</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Centralized_logging">Centralized logging</span></h2>
<p>The salt master in every environment receives raw logs from all the <i>minions</i> it controls. Here are a few log files you can tail.
</p>
<dl><dt>/var/log/messages</dt>
<dd> local syslog-ng</dd>
<dt>/mnt/logs/caching.log</dt>
<dd> Sent by Fastly</dd>
<dt>/mnt/logs/mw-logs/exception.log</dt>
<dd> Sent by MediaWiki</dd>
<dt>/mnt/logs/mw-logs/memcached-serious.log</dt>
<dd> Sent by MediaWiki</dd>
<dt>/mnt/logs/error.log</dt>
<dd> Sent through UDP</dd></dl>
<h3><span class="mw-headline" id="Sent_by_MediaWiki">Sent by MediaWiki</span></h3>
<p>MediaWiki config has a line <b>$wpdUdp2logDest = 'salt:8420';</b> and other directives. All is setup via salt from the template at <b>/srv/salt/code/files/docs/Settings.php.jinja</b> and gets written to the wiki configuration at deploy time.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Sent_through_UDP">Sent through UDP</span></h3>
<p>Each VM, except the salt master itself, should have a file in `/etc/rsyslog.d/60-local1.conf` for this purpose.
The salt master is using syslog-ng to receive and write the log messages from the minions.
</p><p>Setup is not fully trusted/reliable yet. I’m affraid we are losing packets due to many factors (if a minion VM doesnt find the salt master for any reason for example). This will be addressed, see <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/117">webplatform/ops#117</a></b>
</p><p><br />
</p>
<h3><span class="mw-headline" id="Sent_by_Fastly">Sent by Fastly</span></h3>
<p>Each service has a "Logging" setting to send through TCP from their respective services.
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:58603-0!*!0!!*!*!*!esi=1 and timestamp 20150731185730 and revision id 101112
 -->
