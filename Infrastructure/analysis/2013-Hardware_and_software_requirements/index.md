---
title: WPD:Infrastructure/analysis/2013-Hardware and software requirements
---
<h1><span class="mw-headline" id="Hardware_and_software_requirements">Hardware and software requirements</span></h1>
<p>Summarizing server requirements described in length in <a href="/wiki/WPD:Infrastructure/analysis/2013-Usage_and_future_state" title="WPD:Infrastructure/analysis/2013-Usage and future state">WPD:Infrastructure/analysis/2013-Usage and future state</a> and the execution plan is described in <a href="/wiki/WPD:Infrastructure/analysis/2013-Migrating_to_a_new_cloud_provider" title="WPD:Infrastructure/analysis/2013-Migrating to a new cloud provider">WPD:Infrastructure/analysis/2013-Migrating to a new cloud provider</a>.
</p>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>We are using OpenStack hosted Virtual Machines (VM) as our main computing environment. Our VMs are configured using <a rel="nofollow" class="external text" href="http://saltstack.com">Salt Stack</a> to manage instance states and various aspects of OpenStack. Salt is similar to Puppet by managing machine state, but it also enables remote execution and can communicate with OpenStack services.
</p><p>We require many servers to host our services (memcache, MySQL, NGINX, Varnish, Apache, etc). HTTP requests to these servers are managed by our caching layer, which is provided by <a rel="nofollow" class="external text" href="http://fastly.com">Fastly</a>; this provides a caching and CDN service and improves site performance. In the future, we plan to optimize the infrastructure, and implement <i>continuous deployment</i>.
</p><p>In terms of hosting and server infrastructure, we want to have more than one hosting provider, to enable redundancy and multiple site replication, and to showcase the power of OpenStack. In the short term, we need only a single major host.
</p>
<h2><span class="mw-headline" id="Requirements">Requirements</span></h2>
<h3><span class="mw-headline" id="General">General</span></h3>
<ul><li> Open Stack service environment</li>
<li> Access to Nova API</li>
<li> Open to other managed PaaS service, if available. (e.g. managed <i>MySQL</i> or <i>Memcached</i> server)</li>
<li> See also in <a href="#Current_migration">#Current migration</a> and <a href="#Future">#Future</a></li></ul>
<h3><span class="mw-headline" id="Production_environment">Production environment</span></h3>
<p>These are our minimum requirements for the live site:
</p>
<ul><li> 31 vCPU, 102 Gb vRAM, flavors:
<ul><li> 8x 2 vCPU, 8Gb vRAM (MediaWiki server, slave DB server)</li>
<li> 1x 4 vCPU, 16Gb vRAM (DB)</li>
<li> 4x 2 vCPU, 4Gb vRAM</li>
<li> 3x 1 vCPU, 2Gb vRAM</li></ul></li>
<li> 11 IPv4 Public IP addresses</li></ul>
<h3><span class="mw-headline" id="Staging_and_testing_environments">Staging and testing environments</span></h3>
<p>In addition to the production environment, we want to have a testing and staging deployment running full time.
</p><p>These environments have the same requirements as the production environment,  deployed in a separate network, but do not need guaranteed uptime.
</p>
<h2><span class="mw-headline" id="Our_Infrastructure">Our Infrastructure</span></h2>
<p>Every machine is managed by a set of states and pillars and admins manages the complete infrastructure through the Salt master.
</p><p>This is the current breakdown of machines per service type. Our plan is to eventually slim down the quantity of machines and merge some services together.
</p>
<h3><span class="mw-headline" id="Distribution_by_type">Distribution by type</span></h3>
<h4><span class="mw-headline" id="Infrastructure_servers">Infrastructure servers</span></h4>
<ul><li> Salt master (1 VM, Public IP)</li>
<li> NOC nodes (2 VMs, 1 Public IP)</li>
<li> Memcache (2 VMs)</li>
<li> MySQL (2 VMs)</li>
<li> Storage (2 VMs)</li>
<li> Backup (1 VM)</li></ul>
<h4><span class="mw-headline" id="Frontend_servers">Frontend servers</span></h4>
<p>HTTP servers hosting web application, most of them are behind <a rel="nofollow" class="external text" href="http://fastly.com">Fastly</a>, using Varnish (see <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration" title="WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration">WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration</a>).
</p>
<ul><li> Analytics (2 VMs, Public IP, <i>not behind</i> Fastly)</li>
<li> Blog (1 VM, Public IP)</li>
<li> App server (5 VMs, Public IP)</li>
<li> Project management web app (1 VM, Public IP)</li></ul>
<h2><span class="mw-headline" id="Changes">Changes</span></h2>
<h3><span class="mw-headline" id="Current_migration">Current migration</span></h3>
<p>What we would appreciate to have in a new environment.
</p>
<ul><li> Storage facility/mount-points 
<ul><li> Note: We are currently using a set of VMs with Gluster FS</li></ul></li>
<li> Routing to allow downloading from the Internet for the internal only machines</li>
<li> Images of Ubuntu server 10.04.4 LTS and 12.04 LTS</li></ul>
<h3><span class="mw-headline" id="Future">Future</span></h3>
<p>Upcoming, and nice to have for the current migration:
</p>
<ul><li> Internal DNS
<ul><li> Note: We currently spreading a <i>hosts</i> file with Salt stack</li></ul></li>
<li> Private network to communicate with all the instances
<ul><li> VPN between sites (iWeb site and Dreamhost site)</li></ul></li>
<li> Object storage service (Swift/Ceph or similar; not in use, but planned)
<ul><li> Note: our server setup is using Gluster FS and we are considering switching to use OpenStack's Swift/Ceph to store our static assets.</li></ul></li></ul>
<h3><span class="mw-headline" id="Next_year">Next year</span></h3>
<ul><li> MySQL cluster to be upgraded, multiple site replication</li>
<li> Implementing continuous deployment, configuring states on a local development machine using Vagrant/VirtualBox, test deployment script in staging/test, then deploy in production.</li>
<li> Log management analysis tool to help us audit system symptoms</li>
<li> We plan to leverage <a rel="nofollow" class="external text" href="http://en.wikipedia.org/wiki/Edge_Side_Includes">ESI</a> ("Edge Side Include") for some aspects of the site content.</li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:12766-0!*!0!!*!*!*!esi=1 and timestamp 20150731184845 and revision id 41899
 -->
