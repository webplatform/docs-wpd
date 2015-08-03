---
title: WPD:Infrastructure/procedures/Replacing a VM
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
<li> <strong class="selflink">Replacing a VM</strong></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration" title="WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration">Maintaining Fastly configuration</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Managing_MySQL_replication" title="WPD:Infrastructure/procedures/Managing MySQL replication">Managing MySQL replication</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it" title="WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it">Create new database credentials and configure a web application to use it</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">Maintaining ElasticSearch cluster</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_email_services" title="WPD:Infrastructure/procedures/Maintaining email services">Maintaining email services</a></li></ul>
</div>
<h1><span class="mw-headline" id="Replacing_a_VM">Replacing a VM</span></h1>
<p>This document describes how to replace any VM in an existing deployment (e.g. staging) with a new one, install/update targeted web application and apply current configurations. All of that is done in a way that we can replace a faulty VM without affecting the site uptime.
</p><p>Using our <i>Salt Stack</i> (not published yet, see <i>/srv/salt</i> and <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/48">webplatform/ops#48</a></b>), rebuilding a VM is reduced to a few commands and makes it cheap to replace any components which gives us the insurance that we can consistently have the same outcome.
</p><p><b>Remember</b> most recurring commands are listed at the bottom of <code>/srv/salt/README.md</code> on the salt master.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Introduction">Introduction</span></h2>
<p><b>EVERYTHING</b> in WebPlatform infrastructure is managed through source control, including what configures (i.e. the  <a rel="nofollow" class="external text" href="https://github.com/webplatform/states">states</a>) from the VM acting as a <i>salt-master</i>, every VM can be replaced at will. Our infrastructure and scripts are specifically crafted to communicate with an <a rel="nofollow" class="external text" href="http://www.openstack.org/">OpenStack cluster</a>. Over the years we’ve moved from multiple clusters without any problems and we are very happy with how reliable the <i>OpenStack</i> components are.
</p><p>Our infrastructure runs currently on <b><a rel="nofollow" class="external text" href="http://www.dreamhost.com/cloud/computing/">DreamCompute</a></b>, a managed OpenStack cluster graciously sponsored to us by <b><a rel="nofollow" class="external text" href="http://www.dreamhost.com/">DreamHost</a></b> and the configuration is managed by a software called <b><a rel="nofollow" class="external text" href="http://saltstack.com/">Salt Stack</a></b>.
</p>
<h2><span class="mw-headline" id="Procedure">Procedure</span></h2>
<p>In this procedure we will replace a app2 VM with another that has more <i>vRAM</i> and <i>vCPU</i>.
</p><p>Technically OpenStack allows us to "resize" a VM and after a few minutes get the new capacity. Depending of the OpenStack deployment, its even possible to make such resizes without interruption. For the purpose of this tutorial, we’ll walk through the steps of replacing a VM regardless of whether or not our current OpenStack host supports resizing.
</p><p>Since we have either Fastly or a NGINX proxy in front of most web applications, the fact that a VM isn’t live doesn’t break the site as the frontends already takes care of asking other VMs in the same cluster.
</p><p>In the end of this document, we will should be able to swap two VMs without interruptions.
</p><p><br />
<b>About Fastly/Varnish</b> if you need to work with Fastly/Varnish, refer to <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration" title="WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration">WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration</a>
</p><p><b>Note</b>; the output of the commands shown in this document were done from the staging deployment level.
</p>
<h3><span class="mw-headline" id="Get_the_details_of_one_VM">Get the details of one VM</span></h3>
<pre> nova list | grep app2
 | ... | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.215, 173.236.254.224 |
</pre>
<p>We know that <i>app2</i> has two IP addresses assigned
</p>
<ul><li> private: <i>10.10.10.215</i></li>
<li> public: <i>173.236.254.224</i>. If we look at the <i>Fastly</i> dashboard, we should have this IP in; <i>docs (staging)</i>, <i>www (staging)</i>, <i>code (staging)</i> services.</li></ul>
<p>What is the flavor (i.e. Size of RAM and number of CPUs)  <i>app2</i> has?
</p>
<pre> nova show app2|grep flavor
 | flavor                               | supersonic (200)                                                       |
</pre>
<p><br />
What <i>supersonic</i> has (showing only some here);
</p>
<pre> nova flavor-list
 +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+
 | ID  | Name       | Memory_MB | Disk | Ephemeral | Swap | VCPUs | RXTX_Factor | Is_Public | 
 +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+
 | 100 | subsonic   | 1024      | 80   | 0         |      | 1     | 1.0         | True      |
 | 200 | supersonic | 2048      | 80   | 0         |      | 1     | 1.0         | True      |
 | 300 | lightspeed | 4096      | 80   | 0         |      | 2     | 1.0         | True      |
 +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+
</pre>
<p><br />
</p>
<h3><span class="mw-headline" id="Prepare_to_replace_app2">Prepare to replace app2</span></h3>
<p>Let’s unregister <i>app2</i>’s <i>salt-minion</i> from the <i>salt-master</i>
</p>
<pre> salt-key -y -d app2
</pre>
<p><i>app2</i> still has its public IP address —we didn’t delete it— we only did remove it from the <i>salt-master</i>. Benefit here is that we will refer to our new VM as <i>app2</i> without conflicts when interacting via the <i>salt</i> commands. 
</p><p><b>Tip</b> Unless the VM in question is "<i>flapping</i>" (inconsistently breaks the site), we could delete the faulty VM right away. If that VM is behind a proxy such as <i>Fastly</i> or part of a NGINX backends, other servers will take the load until a new one is in place.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Create_a_new_VM">Create a new VM</span></h3>
<p>Boot a new VM;
</p>
<pre>nova boot --image Ubuntu-14.04-Trusty --user-data /srv/opsconfigs/userdata.txt --key_name renoirb-staging --flavor lightspeed --security-groups default,frontend app2
</pre>
<p>Notice a few details:
</p>
<dl><dt><code>/srv/opsconfigs/userdata.txt</code></dt>
<dd> is a configuration file that gets adjusted by the salt master from the salt master itself. It enforces a few details such as DNS and the IP address of the salt master</dd>
<dt><code>--key_name renoirb-staging</code></dt>
<dd> assumes you would have your own passphrase protected SSH public key  in the OpenStack Horizon dashboard</dd>
<dt><code>--security-groups default,frontend</code></dt>
<dd> Are the firewall rules managed by OpenStack, make sure they exists in the OpenStack Horizon dashboard</dd></dl>
<p><b>Tip</b> Since every VM has a private network and that we dont give public IP address to all of them, we instead give a passphrase protected SSH public key per user, per environment. The reason is that if it is required to SSH to a new VM that didn’t yet have had "state.highstate" run on it, you won’t be able to access it anyway. To do so, make sure the OpenStack Horizon dashboard has at least two public keys and that you made a copy of both public and private keys in the private pillars in <i>/srv/private/pillars/sshkeys/</i> on the salt master.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Wait_until_the_VM_is_ready">Wait until the VM is ready</span></h3>
<p>The <i>cloud-init</i> script we gave at <i>/srv/opsconfigs/userdata.txt</i> does also ensure the VM will have the lastest version of everything, plus salt stack minion installed.
</p><p>That way, all we have to do is to check from the salt master if we can see it.
</p>
<pre> salt-key
 Accepted Keys:
   accounts
   app1
   app3
   backup
   blog
   db1-masterdb
   elastic
   mail
   memcache-alpha1
   notes
   piwik
   project
   redis-alpha1
   salt
   sessions1
 Unaccepted Keys:
   app2
 Rejected Keys:
</pre>
<p>We should see <b>app2</b> in <b>Unaccepted Keys</b>, we can accept the new VM like this:
</p>
<pre> salt-key -y -a app2
</pre>
<p>Then, wait a few seconds. You can see if the VM is ready by issuing a <i>test.version</i> command.
</p>
<pre> salt app2 test.version
</pre>
<p><i>Note</i> Accepting a new VM to the salt master is very quick. Sometimes it takes more time to get a response because the salt master might have a few automated scripts to run. Those scripts are called <b>Salt Reactor</b> (see <i><code>/srv/salt/reactor/reactions/*.sls</code></i>) that are configured to run when a VM has been added.
</p><p><br />
</p>
<h3><span class="mw-headline" id="The_VM_is_ready">The VM is ready</span></h3>
<p>Once the "test.version" test answers quickly, we are ready to continue.  Before going any further, always run a sanity check if the VM has the essential "level" grain at the value. In our case, we should get "staging".
</p>
<pre> salt app2 grains.get level
 app2:
    staging
</pre>
<p>We are ready! 
</p><p><b>Tip</b> every salt commands are run from their targeted minion (in this example; <i>app2</i>). It means that if we lose SSH connection from the master will not break the salt run. In fact the command waits for the execution to complete as a comfort for us.
</p>
<pre> salt app2 state.highstate
</pre>
<p>Go drink a glass of water. It takes a while.
</p>
<h2><span class="mw-headline" id="Replacing_something_else_than_app2.3F">Replacing something else than app2?</span></h2>
<p>Replacing a <i>web app runner</i> role VM such as <i>app</i>, <i>piwik</i>, <i>project</i>, or <i>notes</i> is pretty straight forward.
</p><p>In other cases, we need also to update the a few pillars of the current environment. 
</p><p>The essential pillars to look for are the following:
</p>
<ul><li> <code>/srv/private/pillar/accounts/staging.sls</code></li>
<li> <code>/srv/private/pillar/accounts/staging_oauth.sls</code></li>
<li> <code>/srv/pillar/infra/staging.sls</code></li></ul>
<p><b>Tip</b> if you are in "production" level, just look at the files with <b>production</b> instead.
</p><p>The rule of thumb is that what’s in <b>/srv/pillar</b> MUST have nothing private as its publicly visible on GitHub.
</p><p>All private data is stored in <b>/srv/private</b> and have its own separate Git repository that only trusted people should have access.
</p><p>Here are a few situations where you have to update contents in one of those files:
</p>
<h3><span class="mw-headline" id="Infra_pillar">Infra pillar</span></h3>
<p>The configurations in <b>/srv/pillar/infra/</b> are mostly about what’s the current IP address to use for a given use. Each configuration file (in <b>/srv/salt/code/files</b>) gets the exact IP it need from there.
</p>
<ul><li> Adding/Removing a VM with the <b>memcached</b> role</li>
<li> Adding/Removing a VM with the <b>sessions</b> role</li>
<li> Adding/Removing a VM with the <b>redis</b> role</li>
<li> Adding/Removing a VM with the <b>db</b> role</li>
<li> Adding/Removing a VM with the <b>elastic</b> role</li>
<li> Adding/Removing a VM with the <b>mail</b> role</li>
<li> Update the internal DNS zone (<b>gdnsd_timestamp</b>). Most useful if you change any of the above</li></ul>
<h3><span class="mw-headline" id="Accounts_pillar">Accounts pillar</span></h3>
<p>This is where we store the private data. Database passwords, external providers API keys and so on.  The convention is to have a specific set per environment level so we keep a separate deployment and can throughly test every layers somewhere safe before affecting the live site.
</p>
<ul><li> Every password and private keys are stored in <b>/srv/private/pillar/accounts/staging.sls</b>.</li>
<li> Accounts system OAuth2 relying parties client configurations and private keys are in <b>/srv/private/pillar/accounts/staging_oauth.sls</b>.</li></ul>
<p>With this, it will be possible to change service passwords across only by changing the private pillar and the service itself. Each relying web application will read the new password from there.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Apply_configuration_and_code_packages">Apply configuration and code packages</span></h2>
<p>@@TODO adjust once we harmonized the way to install web apps.
</p><p>To apply configuration according to current set of VMs we have do the following.
</p><p><b>Tip</b> always make sure every VM are "awake" and replies to ping commands before running them. You can run the following commands a few times, sometimes some might been sleepy.
</p>
<pre> salt-run manage.status
 down:
 up:
   - accounts
   - app1
   - app2
   - app3
   - backup
   - blog
   - db1-masterdb
   - elastic
   - mail
   - memcache-alpha1
   - notes
   - piwik
   - project
   - redis-alpha1
   - salt
   - sessions1
</pre>
<p>Now let’s deploy the code and apply regenerate configuration files
</p>
<pre> wpd-deploy app
</pre>
<p>This commands ensures that configuration files are applied on top of each web app with the current configuration.  This ensure that can minimize hardcoded information.
</p><p>The output should look like this;
</p><p><a href="/wiki/File:Running_wpd-deploy.png" class="image"><img alt="Running wpd-deploy.png" src="//static.webplatform.org/w/public/0/0d/Running_wpd-deploy.png" width="1291" height="1004" /></a>
</p>
<h2><span class="mw-headline" id="Testing_before_flipping_the_switch.3F">Testing before flipping the switch?</span></h2>
<p>If you are testing a new configuration or plugin, it might be prudent to ensure that what you’ve worked on works before making it visible through the sites (i.e. <b>webplatformstaging.org</b> or <b>webplatform.org</b>). To do we can map a temporary public IP address and add it to your local <b>hosts</b> file.
</p><p>You can do so by following the next steps with another IP address, or use the OpenStack Horizon Dashboard the site is running on. Technically each VM requires first to have a public IP address so that a proxy (in most case; Fastly) can serve from it.
</p><p>Remember that each web app is deployed based on the role name, you can get them in <a href="/wiki/WPD:Infrastructure/procedures/Deploying_code_changes#Deploying.2Fupdating_a_web_app" title="WPD:Infrastructure/procedures/Deploying code changes">WPD:Infrastructure/procedures/Deploying_code_changes#Deploying.2Fupdating_a_web_app</a>.
</p>
<h2><span class="mw-headline" id="Prepare_to_flip_the_Floating_IP_address">Prepare to flip the Floating IP address</span></h2>
<p>Let’s get the network adapter details of our new VM. This procedure will take into account that we didn’t test with another temporary IP address.
</p><p><b>Note</b> you might get two entries if you didn’t delete yet the old VM, the new VM should be the one that has only a private IP address.
</p>
<ul><li> We first need to know what is the private IP address of our VMs</li></ul>
<pre> nova list | grep app2
 | ... | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.218 |
 | ... | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.215, 173.236.254.224 |
</pre>
<p>Remember when we asked app2 what was their public and private IP addresses.
</p><p>Old app2 has:
</p>
<ul><li> 10.10.10.215 (private)</li>
<li> 173.236.254.224 (public, that we’ll give to the new app2)</li></ul>
<p>New app2 has:
</p>
<ul><li> 10.10.10.218 (private)</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Flipping_the_floating_IP">Flipping the floating IP</span></h2>
<p>The following commands in the order in which we need the proper values. Each field are generally hexadecimal strings of about 64 characters and dashes. In this example, they are replaced as "foo" and "bar" to illustrate their appropriate positions.
</p>
<ul><li> Get the <b>id</b> of the floating IP we need. Fields from this command are in the order: id, fixed IP address, Floating IP address, port Id. We only care about the id, here: <b>foo</b>.</li></ul>
<pre> neutron floatingip-list | grep 173.236.254.224
 | foo |  10.10.10.215   |  173.236.254.224  |    |
</pre>
<ul><li> We also need what’s called the port id identifier. Its the first column, here: "bar".</li></ul>
<pre> neutron port-list | grep 10.10.10.218
 | bar |      | fa:16:3e:c1:6c:a0 | {"subnet_id": "...", "ip_address": "10.10.10.218"}
</pre>
<ul><li> We do have what we need to assign, enter them in this order:</li></ul>
<pre> neutron floatingip-associate --fixed-ip-address 10.10.10.218 foo bar
</pre>
<p>The new vm <i>app2</i> has now the public IP and the old VM is not used anymore
</p>
<h2><span class="mw-headline" id="Delete_the_old_app2_VM">Delete the old app2 VM</span></h2>
<p>Now that we have two app2 VMs in our OpenStack cluster, we cannot refer to the name to <i>nova</i>.  Not a big deal, we can use the uuid string to refer to a VM. Note that I renamed the UUID here as "buzz" and "bizz", they won’t look like this in a real deployment.
</p><p>Since we already know that we just changed the Floating IP to the <i>app2</i> VM we want to keep, it means that we know which one to delete.
</p>
<pre> nova list | grep app2
 | buzz | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.215 |
 | bizz | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.218, 173.236.254.224 |
</pre>
<p>We can delete the VM
</p>
<pre> nova delete buzz
</pre>
<p>We are done!
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:58605-0!*!0!!*!5!*!esi=1 and timestamp 20150731185747 and revision id 101373
 -->
