---
title: WPD:Infrastructure/procedures/Deploying code changes
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
<ul><li> <strong class="selflink">Deploying code changes</strong></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Replacing_a_VM" title="WPD:Infrastructure/procedures/Replacing a VM">Replacing a VM</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration" title="WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration">Maintaining Fastly configuration</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Managing_MySQL_replication" title="WPD:Infrastructure/procedures/Managing MySQL replication">Managing MySQL replication</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it" title="WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it">Create new database credentials and configure a web application to use it</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">Maintaining ElasticSearch cluster</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_email_services" title="WPD:Infrastructure/procedures/Maintaining email services">Maintaining email services</a></li></ul>
</div>
<h1><span class="mw-headline" id="Deploying_code_changes">Deploying code changes</span></h1>
<p>This document describes how to apply code changes on managed web applications that runs <i>webplatform.org</i>.
</p><p>The way we update code is handled from the salt master and apply changes where it applies. To see the detail of what every VM has in common, refer to <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM" title="WPD:Infrastructure/architecture/Base configuration of a VM">WPD:Infrastructure/architecture/Base_configuration_of_a_VM</a>.
</p><p>The process of deploying is going to change into something that will allow us to ensure that we can revert to the same state the web app was built from without any risks of broken external dependencies. <a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues?milestone=1">see the project <i>webplatform/ops</i> milestone</a> that has this objective.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Procedure">Procedure</span></h2>
<p>This procedure will take into account that you have an existing set of VMs already installed  <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM" title="WPD:Infrastructure/architecture/Base configuration of a VM">WPD:Infrastructure/architecture/Base_configuration_of_a_VM</a> and managed by the <a href="/wiki/WPD:Infrastructure/architecture/The_salt_master" title="WPD:Infrastructure/architecture/The salt master">WPD:Infrastructure/architecture/The_salt_master</a>.
</p><p>In this example we’ll update the code on all VMs that fills the <i>role</i> of <b>app</b>.
</p><p><b>Related</b>; if you want to see how to update a database password and apply the changes to a managed web application, go to  <a href="/wiki/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it" title="WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it">Create new database credentials and configure a web application to use it</a>
</p>
<ul><li> First, make sure the role you want to target touches the VMs you want</li></ul>
<pre> salt app\* grains.get roles
 app1-jobrunner:
   - app
   - jobrunner
 app2:
   - app
 app3:
   - app
</pre>
<h3><span class="mw-headline" id="Running_a_code_update">Running a code update</span></h3>
<p>Deploying code on VMs of a given role:
</p>
<pre> salt app\* state.sls code
</pre>
<p>You can also target the same set of VM using salt <i>grains</i> <a rel="nofollow" class="external text" href="http://docs.saltstack.com/en/latest/topics/targeting/grains.html">targeting variant</a>;
</p>
<pre> salt -G 'roles:app' state.sls code
</pre>
<p>Which is basically what the following command do;
</p>
<pre> wpd-deploy app
</pre>
<p>The latter is an alias for the comfort of everyday use and can be done without being root.
</p><p>Output should look like this;
</p><p><a href="/wiki/File:Running_wpd-deploy.png" class="image"><img alt="Running wpd-deploy.png" src="//static.webplatform.org/w/public/0/0d/Running_wpd-deploy.png" width="1291" height="1004" /></a>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Deploying.2Fupdating_a_web_app">Deploying/updating a web app</span></h2>
<p>ANY deployment is made through Salt Stack. The deployment code is publicly available on <i>GitHub</i> as  <a rel="nofollow" class="external text" href="https://github.com/webplatform/salt-states"><b>webplatform/salt-states</b></a>.
</p><p>Each role name states are defined in an <i>sls</i> file in <code>/srv/salt/roles</code> and from there, you’ll see any rsync scripts it uses to copy code the salt master hosts in <i>/srv/code/foo/repo</i>. 
</p><p><b>NOTE</b> the command <i>wpd-deploy foo</i> <b>ISN’T LIMITED</b> to copying files from folders in <i>/srv/code/foo/bar</i>, its also about ensuring that some configuration are applied.  Its prudent to double check what will happen always check the matching state (e.g.  <i>wpd-deploy foo</i>) in the matching <i>sls</i> file (e.g. <i>/srv/salt/roles/foo.sls</i>)
</p><p>To update a webapp, run the following commands. Salt will know which VM has to get the code:
</p>
<dl><dt>app</dt>
<dd><code>wpd-deploy app</code>&#160;&#160;[''/srv/code/www/repo'', ''/srv/code/compat/repo'', ''/srv/code/dabblet/repo'', ''/srv/code/wiki/repo'']</dd>
<dt>blog</dt>
<dd><code>wpd-deploy blog</code>&#160;&#160;[''/srv/code/blog/repo'']</dd>
<dt>notes</dt>
<dd><code>wpd-deploy notes</code>&#160;&#160;[''/srv/code/notes-server/repo'']</dd>
<dt>piwik</dt>
<dd><code>wpd-deploy piwik</code>&#160;&#160;[''/srv/code/piwik/repo'']</dd>
<dt>project</dt>
<dd><code>wpd-deploy project</code>&#160;&#160;[''/srv/code/buggenie/repo'']</dd>
<dt>accounts</dt>
<dd><code>wpd-deploy accounts</code></dd></dl>
<h2><span class="mw-headline" id="Related">Related</span></h2>
<ul><li> The detail of what each roles does is described in <a href="/wiki/WPD:Infrastructure/architecture/VM_roles" title="WPD:Infrastructure/architecture/VM roles">WPD:Infrastructure/architecture/VM_roles</a>.</li>
<li> How to replace a VM has details on how to deploy code too <a href="/wiki/WPD:Infrastructure/procedures/Replacing_a_VM" title="WPD:Infrastructure/procedures/Replacing a VM">WPD:Infrastructure/procedures/Replacing_a_VM</a>.</li>
<li> To know what code is going to be deployed, refer to <a href="/wiki/WPD:Infrastructure/architecture/Roles_and_environment_level" title="WPD:Infrastructure/architecture/Roles and environment level">WPD:Infrastructure/architecture/Roles_and_environment_level</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Useful_commands#Create_a_database.2C_a_user.2C_set_new_privileges_and_update_a_web_application" title="WPD:Infrastructure/architecture/Useful commands">How to update database details in a web application</a></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:2-0!*!0!!*!5!*!esi=1 and timestamp 20150731180819 and revision id 101526
 -->
