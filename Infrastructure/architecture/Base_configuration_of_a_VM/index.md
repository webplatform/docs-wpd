---
title: WPD:Infrastructure/architecture/Base configuration of a VM
---
<div style="float:right;width:33%;word-wrap:break-word;clear:both;">
<h3><span class="mw-headline" id="WebPlatform_server_Infrastructure_architecture_menu"><a href="/wiki/WPD:Infrastructure/architecture" title="WPD:Infrastructure/architecture">WebPlatform server Infrastructure architecture menu</a></span></h3>
<div class="subpagelist">
<ul><li> <strong class="selflink">Base configuration of a VM</strong></li>
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
<li> <a href="/wiki/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it" title="WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it">Create new database credentials and configure a web application to use it</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">Maintaining ElasticSearch cluster</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_email_services" title="WPD:Infrastructure/procedures/Maintaining email services">Maintaining email services</a></li></ul>
</div>
<h1><span class="mw-headline" id="Base_configuration_of_a_VM">Base configuration of a VM</span></h1>
<p>Here is a few details that every VMs has in common
</p>
<ul><li> Ubuntu 14.04 LTS</li>
<li> <i>Apt</i> is configured to have security updates installed automatically</li>
<li> IPv6 is supported by DreamCompute, but we aren’t using it yet. It’s disabled at <i>sysctl</i> level for now</li>
<li> Private IPv4 networking <i>security groups</i> is allowing VMs to communicate among themselves</li>
<li> Nothing is exposed to the public <i>Floating IPs</i>, except the bare minimum (e.g. TCP 80, 443 on web servers). Security groups are selectively opening ports to enforce the policy</li>
<li> Access to ANY VM is only made through the salt master acting as a <i>Jump box</i>, see <a href="#Accessing_a_VM_using_SSH">Accessing a VM using SSH</a></li>
<li> Every VM is booted from a basic Ubuntu 14.04 LTS image. A minimal <i>cloud-init</i> script installs <i>salt-minion</i> and makes it poke the <i>salt master</i>.</li>
<li> Each VM can consult their initial <i>cloud-init</i> script using OpenStack internal API by doing: <code>curl http://169.254.169.254/openstack/2013-10-17/user_data</code></li>
<li> The VM name define what softwares, services, and  web apps deployed on them. For more details about it, refer to the section about "roles" at <a href="/wiki/WPD:Infrastructure/architecture/Roles_and_environment_level" title="WPD:Infrastructure/architecture/Roles and environment level"><b>Roles and environment level</b></a></li>
<li> Monit has automatic service checks definitions installed through Salt stack. <a href="/wiki/WPD:Infrastructure/Monitoring/Monit" title="WPD:Infrastructure/Monitoring/Monit">More about <b>Monit</b></a> and about how to <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status#Using_Monit" title="WPD:Infrastructure/architecture/Reports to review status">get Monit reports</a>.</li>
<li> Each VM has a full name describing its role and environment level known internally pointing to private IPs (e.g. <i>app3-jobrunner.production.wpdn</i>).</li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="Every_VMs.2C_except_ones_with_the_mail_role">Every VMs, except ones with the mail role</span></h3>
<ul><li> Uses locally configured <i>exim4</i> to send email through the <i>email relay</i> (<i>mail.webplatform.org</i>) allowing us to have only one mail server to maintain.</li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="Only_VMs_with_mail_role">Only VMs with mail role</span></h3>
<ul><li> The mail relay (e.g. <i>mail.webplatform.org</i>) takes care of converting to publicly addressable origin but has headers to know which VM sent the message</li></ul>
<h3><span class="mw-headline" id="Every_VMs_that_has_frontend_role">Every VMs that has frontend role</span></h3>
<ul><li> At this time they have the name <i>nginx</i> in them, they should be renamed <i>frontend</i> as its what they’ll do. Besides VMs with the <i>backend</i> role will also have NGINX to serve internally static assets for the frontend so it would make more sense to remove potential confusion with the software name</li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="Every_VMs_with_a_backend">Every VMs with a backend</span></h3>
<p>At this time its the VM with roles: <b>app</b>, <b>project</b>, <b>piwik</b>, <b>blog</b>. But eventually it’ll be attached differently.
</p>
<ul><li> Every web app configuration (e.g. <i>/srv/salt/code/files/wiki/Settings.php.jinja</i>) uses Redis and Memcached as if it was local</li>
<li> Nutcracker acts as a Redis and Memcached proxy on every VMs of the roles listed above</li>
<li> Nutcracker configuration is managed by salt, lists of nodes are in <i>/srv/pillar/infra/staging.sls</i> with pillar keys <i>infra:sessions_redis</i>, <i>infra:sessions_memcache</i>, <i>infra:alpha_redis</i>, <i>infra:alpha_memcache</i>, list them like this:</li></ul>
<pre> salt app\* pillar.get infra:sessions_redis
</pre>
<ul><li> Only Sessions data MUST be sent to localhost keystore at default port number, configured at both web app level and/or backend configuration itself (e.g. <i>php.ini</i>)</li>
<li> Other keystore caches uses a different port, ending by <b>55</b> (e.g. Memcached 127.0.0.1:11255, Redis 127.0.0.1:6355) local nutcracker proxy </li>
<li> Should have a minimal NGINX server to serve static assets as part of the web software package its serving as a backend. The <i>frontend</i> VMs will poll static assets from there.</li></ul>
<h3><span class="mw-headline" id="VMs_with_either_redis_or_memcache_or_session_roles">VMs with either redis or memcache or session roles</span></h3>
<ul><li> Listens on default port on private IPv4 interface of their respective service</li>
<li> No web app should call them directly, use Nutcracker as a proxy instead</li>
<li> VMs with role <i>sessions</i> are separate from the other keystores by design so we can purge data from any other clusters without destroying our user sessions</li></ul>
<h2><span class="mw-headline" id="Accessing_a_VM_using_SSH">Accessing a VM using SSH</span></h2>
<p>To work on any VM on WebPlatform architecture, you have to have one of the site operators to add your SSH public key. Once you have access, you’ll be able to jump to the VMs you are granted access through what’s called a <i>SSH Jump box</i>.
</p><p>One of the common use-case for this setup is to gain access to <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status" title="WPD:Infrastructure/architecture/Reports to review status">WPD:Infrastructure/architecture/Reports_to_review_status</a>, or to make some random checks.
</p><p>The following will explain how you can install on your local machine the configuration you need to connect to the VMs through SSH.
</p><p><br />
</p>
<h3><span class="mw-headline" id="How_it_works">How it works</span></h3>
<p>In summary, a <i>SSH Jump box</i> is basically a way to refer to a VM within a private network using a publicly available SSH server acting as a proxy.
</p><p>To work on a cluster on a given level, you can use the salt master as a SOCKS proxy to view privileged reports such as service health and usage reports.  
</p><p>To view the internal only reports, configure one of your web browser to use your local computer as a proxy through the SSH tunnel we will create.
</p>
<pre> ssh salt.webplatform.org -C -D 1080
</pre>
<p>This would allow you to connect only to the salt master and have a SOCKS proxy. To access all VMs and simplify the commands to use, read on.
</p>
<h3><span class="mw-headline" id="Setting_automatically_a_SOCKS_proxy_in_your_SSH_configuration">Setting automatically a SOCKS proxy in your SSH configuration</span></h3>
<p>A reliable solution is to setup your local ssh client to do things for you automatically.
</p><p>Those things can be done in <b>~/.ssh/config</b> file the following line within the appropriate <b>Host</b> block. Or using PuTTY, if you use Windows.
</p>
<pre>### WPD Production
Host production.wpdn
  Hostname salt.webplatform.org
  ProxyCommand none
  DynamicForward 1080
Host *.production.wpdn
  ProxyCommand ssh -e @ -o StrictHostKeyChecking=no -a -W&#160;%h:%p production.wpdn
</pre>
<p><b>Note</b> this block is an example of what you can use to have a <b>DynamicForward</b> automatically installed. 
</p><p>To connect to the salt master, you’d have to do this instead and all will be setup automatically:
</p>
<pre> ssh production.wpdn
</pre>
<p>You can even connect to a VM directly using the salt master as a <i>Jump box</i>
</p>
<pre> ssh app1.production.wpdn
</pre>
<p>To use the proxy, you need at least one SSH connection established to the infrastructure.
</p><p><b>IMPORTANT</b> Make sure you always use the connection block that the salt master provides you at connection time as this example here might become outdated.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Configuring_a_web_browser_to_use_the_proxy">Configuring a web browser to use the proxy</span></h3>
<p>Once connected, you have to configure a web browser to use your new <b>DynamicForward</b> SOCKS proxy. 
</p><p>In modern Firefox version, you can do that by going into <b>Preferences</b>, <b>Advanced</b>, <b>Network</b> tab, then <b>Connection</b> button. You’ll see a window similar to below. Adjust accordingly.
</p><p><a href="/wiki/File:201502-Firefox-Network-settings.png" class="image"><img alt="201502-Firefox-Network-settings.png" src="//static.webplatform.org/w/public/e/ee/201502-Firefox-Network-settings.png" width="1079" height="850" /></a>
</p><p>To learn how to configure your web browser to use SSH as a SOCKS proxy, you can view the <a rel="nofollow" class="external text" href="https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Dynamic_Port_Forwarding">SSH Port forwarding help pages on <b>help.ubuntu.com</b></a>
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:58604-0!*!0!!*!5!*!esi=1 and timestamp 20150731185737 and revision id 101063
 -->
