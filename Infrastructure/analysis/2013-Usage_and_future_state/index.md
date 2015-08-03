---
title: WPD:Infrastructure/analysis/2013-Usage and future state
---
<h1><span class="mw-headline" id="2013_WebPlatform_Docs_infrastructure_usage_and_future_state">2013 WebPlatform Docs infrastructure usage and future state</span></h1>
<p><b>NOTE</b>: There is a <i>TLDR</i> version describing software and hardware requirement available <a href="/wiki/WPD:Infrastructure/analysis/2013-Hardware_and_software_requirements" title="WPD:Infrastructure/analysis/2013-Hardware and software requirements">WPD:Infrastructure/analysis/2013-Hardware and software requirements</a>
</p>
<h2><span class="mw-headline" id="Introduction">Introduction</span></h2>
<p><a rel="nofollow" class="external text" href="http://webplatform.org/">WebPlatform Docs</a> is now close to a year old. The goal of this document is to describe the current health of the system and how we can make it better.
</p><p>As <a rel="nofollow" class="external text" href="http://blog.webplatform.org/2012/10/building-web-platforms-infrastructure/">Ryan described in the launch post</a>, we can see a year later that the structure is handling the load fairly well.
</p><p>But as with anything, we also learned that we have to improve the system to make it more stable. Since the last year was mostly focussing on the content than the infrastructure, things at some spots were left behind and the system is in a need of a good maintenance.
</p><p>This is why <a rel="nofollow" class="external text" href="http://blog.webplatform.org/2013/08/hi-my-name-s-renoir-ill-be-your-devops-for-the-web-platform/"><i>Renoir</i> has been hired</a>: To maintain the system and contribute to the site success, full time.
</p><p>This document describes in depth the usage, statistics of the current infrastructure, and what is to come with it.
</p><p><br />
</p>
<hr />
<p><br />
</p>
<h2><span class="mw-headline" id="1._Executive_Summary">1. Executive Summary</span></h2>
<h3><span class="mw-headline" id="1.1._Usage_comparison_table">1.1. Usage comparison table</span></h3>
<table class="mw-datatable os-suggest-results filehistory">
<caption>VMs usage comparsion
</caption>
<tr>
<td>
</td>
<td>Current
</td>
<td>Future
</td></tr>
<tr>
<td><b>Application services</b>
</td>
<td>production:
<ul><li> app: 5</li>
<li> monitor:1</li>
<li> piwik: 2</li>
<li> project: 1</li>
<li> code:1</li></ul>
</td>
<td>production:
<ul><li> 8</li></ul>
<p>temporary *&#160;:
</p>
<ul><li> 3</li></ul>
</td></tr>
<tr>
<td><b>Infrastructure services</b>
</td>
<td><i>production</i>:
<ul><li> deployment: 1</li>
<li> db: 2</li>
<li> memcache: 2</li>
<li> storage: 2</li></ul>
</td>
<td><i>production</i>:
<ul><li> 5-9</li></ul>
<p><i>temporary *</i>:
</p>
<ul><li> 5</li></ul>
</td></tr>
<tr>
<td><b>Process services</b>
</td>
<td><i>production</i>:
<ul><li> backup: 1</li>
<li> bots: 1</li></ul>
</td>
<td><i>production</i>:
<ul><li> 1-2</li></ul>
<p><i>temporary *</i>:
</p>
<ul><li> 1</li></ul>
</td></tr>
<tr>
<td><b>Sub-total</b>
</td>
<td><i>production</i>:
<ul><li> 19 VMs</li></ul>
</td>
<td><i>production</i>:
<ul><li> 14-19 VMs</li></ul>
<p><i>temporary *</i>:
</p>
<ul><li> 9</li></ul>
</td></tr>
<tr>
<td><b>Total</b>
</td>
<td> 19 VMs
</td>
<td> 23-28 VMs <br /> <i>Including *one only* one "temporary environment" up</i>
</td></tr></table>
<div class="quotebox" style="padding: 6px; border: 1px solid #aaa; font-size: 88%; background-color: #F9F9F9;">
<div style="background: #F9F9F9; color:black; text-align: center; font-size: larger; font-weight: bold;">Note 4</div>
<div style="position: relative; text-align: left;">
<div>
<p>In Temporary environment, numbers may vary, we might want to always have a temporary environment running for common (non-local) development purposes.
</p>
</div>
</div>
<div style="text-align: left;"> </div>
</div>
<h3><span class="mw-headline" id="1.2._Some_facts_about_the_current_environment">1.2. Some facts about the current environment</span></h3>
<ul><li> Fastly is reporting 3.4 Million requests for the month of August 2013;</li>
<li> Some VMs are used for development and should be removed or migrated to an isolated environment, see <a href="#3.1._Type_of_deployment">#3.1. Type of deployment</a>;</li>
<li> No other environment than production (it has to change); The development work made in the production environment and might affect it;</li>
<li> Everybody with a shared account can do everything with no real control in the privileges;</li>
<li> 4 VMs has to be Ubuntu 10.04, solely required for the instances described <a href="#2.2.1.1._MediaWiki.2C_WordPress.2C_Dabblet.2C_Talk">#2.2.1.1. MediaWiki, WordPress, Dabblet, Talk</a>, to be solved in <a href="#3.2.1._Operating_System_version_discrepancy_to_solve">#3.2.1. Operating System version discrepancy to solve</a>.</li></ul>
<p><br />
</p><p><br />
</p>
<h3><span class="mw-headline" id="1.3._Current_environment_summary">1.3. Current environment summary</span></h3>
<p>The following information summarizes the resources allocation used in the current environment.
</p><p>See section <a href="#2._Current_environment">#2. Current environment</a> for more details.
</p>
<ul><li> <b>Production environment</b>
<ul><li>  25  Public IP addresses; it could be possible to work with 12 static IP addresses for production</li>
<li>  18  VMs production instances</li>
<li> 5 http/php (app servers)</li>
<li> 2 memcached</li>
<li> 2 mysql/db</li>
<li> ... misc apps, storage, backup, monitoring, salt master, etc…</li>
<li>  4  VMs for testing or upcoming projects (not advertised)</li></ul></li>
<li> <b>Temporary environment</b>
<ul><li> N/A</li></ul></li></ul>
<div class="quotebox" style="padding: 6px; border: 1px solid #aaa; font-size: 88%; background-color: #F9F9F9;">
<div style="background: #F9F9F9; color:black; text-align: center; font-size: larger; font-weight: bold;">Note 5 '<b>Important!'</b></div>
<div style="position: relative; text-align: left;">
<div>
<p>The current environment on HPCloud has no isolated “staging”, nor “test” deployment environment (i.e. “Temporary environment”), see <a href="#3.2._Refactor_overview">#3.2. Refactor overview</a> for problems it might cause.
</p>
</div>
</div>
<div style="text-align: left;"> </div>
</div>
<p><br />
</p><p><br />
</p>
<h3><span class="mw-headline" id="1.4._Refactored_infrastructure_estimation_summary">1.4. Refactored infrastructure estimation summary</span></h3>
<p>The following describes the estimated resources required to build the new infrastructure to be used by September 2014.
</p><p>See <a href="#3._Refactored_infrastructure">#3. Refactored infrastructure</a> for more details.
</p><p>Although the fact that the desired production environment infrastructure could be sufficient by itself, the new infrastructure should support multi-site deployment.
</p><p>The new infrastructure with support multi-site replication to a secondary site where database and files can be synced from one datacenter to another. Resource allocation for a secondary site has an estimated resource allocation similar to a “Temporary environment” in terms of numbers and will be improving service redundancy.
</p>
<div class="quotebox" style="padding: 6px; border: 1px solid #aaa; font-size: 88%; background-color: #F9F9F9;">
<div style="background: #F9F9F9; color:black; text-align: center; font-size: larger; font-weight: bold;">Note 1</div>
<div style="position: relative; text-align: left;">
<div>
<p>The numbers described in the ‘Secondary environment’ section are to be considered in surplus, but it should be possible to use in some during defined period of time.
</p>
</div>
</div>
<div style="text-align: left;"> </div>
</div>
<div class="quotebox" style="padding: 6px; border: 1px solid #aaa; font-size: 88%; background-color: #F9F9F9;">
<div style="background: #F9F9F9; color:black; text-align: center; font-size: larger; font-weight: bold;">Note 2</div>
<div style="position: relative; text-align: left;">
<div>
<p>We might consider creating an always-running ‘Secondary environment’ for ad-hoc development.
</p>
</div>
</div>
<div style="text-align: left;"> </div>
</div>
<h4><span class="mw-headline" id="Production_environment">Production environment</span></h4>
<ul><li> 9-12 Public IP address;</li>
<li> 14-19 VMs; <br />Note: some changes described in 3.2. Refactor overview might require to adjust the numbers;</li></ul>
<h4><span class="mw-headline" id="Temporary_environment">Temporary environment</span></h4>
<ul><li> It should be possible to have more than one deployed “temporary” environment at a time (e.g. one for staging, one for test);</li>
<li> Number is approximate as it might change depending of the feature to be deployed and tested (e.g. We want to test fault tolerance on the DB, we might only need one web application instance, and 5 database servers)</li>
<li> ~9 Public IP Address;</li>
<li> ~9 VMs;</li></ul>
<h4><span class="mw-headline" id="Secondary_environment">Secondary environment</span></h4>
<ul><li> Represent a reduced version of the production environment, a secondary site replicating the production;</li>
<li> Resource allocation is similar to a Temporary environment in terms of IP Addresses and VM quantities.</li></ul>
<p><br />
</p><p><br />
</p><p><br />
</p>
<h3><span class="mw-headline" id="1.5._Common_services">1.5. Common services</span></h3>
<p>Although the current infrastructure includes the services in common enumerated below, the Refactored infrastructure will also include them.
</p>
<ul><li> Salt minion agent</li>
<li> Ganglia monitor agent</li>
<li> GlusterFS client (in some cases, subject to change if we have Block storage)</li>
<li> Rsync xinetd service (rsync key is propagated through Salt)</li></ul>
<p><br />
</p>
<hr />
<p><br />
</p><p><br />
</p>
<h2><span class="mw-headline" id="2._Current_environment">2. Current environment</span></h2>
<h3><span class="mw-headline" id="2.2._Instance_flavors">2.2. Instance flavors</span></h3>
<p>Even though the current infrastructure does not have an explicit categorization scheme, each instance is conceptually separated into the following categories. The new infrastructure will have a similar categorization.
</p>
<h4><span class="mw-headline" id="2.2.1._Application_services">2.2.1. Application services</span></h4>
<h5><span class="mw-headline" id="2.2.1.1._MediaWiki.2C_WordPress.2C_Dabblet.2C_Talk">2.2.1.1. MediaWiki, WordPress, Dabblet, Talk</span></h5>
<p>A generic profile server should serve only as a redundant HTTP app service. Each application server has a public IP address, but they are not broadcasted publicly in DNS records. Instead, it uses a third-party service (fastly) to balance the load.
</p>
<table>
<caption>Node <tt>app[n]</tt>
</caption>
<tr>
<td><b>Linux release:</b>
</td>
<td>Ubuntu 11.04 LTS Lucid
</td></tr>
<tr>
<td><b>Web application profiles:</b>
</td>
<td>
<ul><li> MediaWiki</li>
<li> Dabblet</li>
<li> WordPress</li>
<li> Talk</li></ul>
</td></tr>
<tr>
<td><b>Services:</b>
</td>
<td>
<ul><li> <a href="#1.5._Common_services">#1.5. Common services</a></li>
<li> Apache2 w/ mpm-prefork</li></ul>
</td></tr>
<tr>
<td><b>Specs:</b>
</td>
<td>4 vCPU / 8 GB RAM / 240 GB HD
</td></tr>
<tr>
<td><b>Load average:</b>
</td>
<td>
<ul><li> 0.20, 0.14, 0.10</li>
<li> 0.13, 0.12, 0.14</li>
<li> 0.20, 0.17, 0.14</li>
<li> 0.24, 0.66, 0.42</li>
<li> 0.49, 0.42, 0.39</li></ul>
</td></tr>
<tr>
<td><b>Disk usage:</b>
</td>
<td>
<pre> app3:
   Filesystem            Size  Used Avail Use% Mounted on
   /dev/vda              9.9G  5.0G  4.5G  53% /
   /dev/vdb              227G  188M  215G   1% /mnt
   storage3:/wiki-images  50G  832M   50G   2% /srv/webplatform/wiki/images
 app2:
   Filesystem            Size  Used Avail Use% Mounted on
   /dev/vda              9.9G  6.8G  2.6G  73% /
   /dev/vdb              227G  457M  215G   1% /mnt
   storage3:/wiki-images  50G  832M   50G   2% /srv/webplatform/wiki/images
 app4:
   Filesystem            Size  Used Avail Use% Mounted on
   /dev/vda              9.9G  5.1G  4.4G  54% /
   /dev/vdb              227G  188M  215G   1% /mnt
   storage3:/wiki-images  50G  832M   50G   2% /srv/webplatform/wiki/images
 app1:
   Filesystem            Size  Used Avail Use% Mounted on
   /dev/vda              9.9G  6.8G  2.6G  73% /
   /dev/vdb              227G  188M  215G   1% /mnt
   storage3:/wiki-images  50G  832M   50G   2% /srv/webplatform/wiki/images
 app5:
   Filesystem            Size  Used Avail Use% Mounted on
   /dev/vda              9.9G  4.9G  4.5G  53% /
   /dev/vdb              227G  188M  215G   1% /mnt
   storage3:/wiki-images  50G  832M   50G   2% /srv/webplatform/wiki/images
</pre>
</td></tr></table>
<p><br />
</p>
<h5><span class="mw-headline" id="2.2.1.2._Monitor">2.2.1.2. Monitor</span></h5>
<p>This instance provides a web frontend to ganglia reports, and publish them publicly.
</p>
<table>
<caption>Node <tt>monitor</tt>
</caption>
<tr>
<td><b>Linux release:</b>
</td>
<td>Ubuntu 12.04.2 LTS Precise
</td></tr>
<tr>
<td><b>Web application profiles:</b>
</td>
<td>
<ul><li> Ganglia frontend</li></ul>
</td></tr>
<tr>
<td><b>Services:</b>
</td>
<td>
<ul><li> Ganglia server</li>
<li> <a href="#1.5._Common_services">#1.5. Common services</a></li></ul>
</td></tr>
<tr>
<td><b>Specs:</b>
</td>
<td>2 vCPU / 2 GB RAM / 60 GB HD
</td></tr>
<tr>
<td><b>Load average:</b>
</td>
<td>0.40, 0.42, 0.45
</td></tr>
<tr>
<td><b>Disk usage:</b>
</td>
<td>
<pre>   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  1.5G  7.9G  16% /
   /dev/vdb         50G  180M   47G   1% /mnt
</pre>
</td></tr></table>
<p><br />
</p><p><br />
</p>
<h5><span class="mw-headline" id="2.2.1.3._Piwik">2.2.1.3. Piwik</span></h5>
<p>This instance provides piwik dashboard web front-end and tracking beacon.
</p><p><br />
</p>
<table>
<caption>Node <tt>piwik[n]</tt>
</caption>
<tr>
<td><b>Linux release:</b>
</td>
<td>Ubuntu 12.04.1 LTS
</td></tr>
<tr>
<td><b>Number of nodes:</b>
</td>
<td>2
</td></tr>
<tr>
<td><b>Web application profiles:</b>
</td>
<td>
<ul><li> Piwik</li></ul>
</td></tr>
<tr>
<td><b>Services:</b>
</td>
<td>
<ul><li> Apache2 w/ mpm-prefork</li>
<li> <a href="#1.5._Common_services">#1.5. Common services</a></li></ul>
</td></tr>
<tr>
<td><b>Specs:</b>
</td>
<td>4 vCPU / 8 GB RAM / 240 GB HD
</td></tr>
<tr>
<td><b>Load average:</b>
</td>
<td>
<ul><li> 0.00, 0.01, 0.05</li>
<li> 0.00, 0.01, 0.05</li></ul>
</td></tr>
<tr>
<td><b>Disk usage:</b>
</td>
<td>
<pre> piwik1:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  1.3G  8.2G  13% /
   /dev/vdb        227G  188M  215G   1% /mnt
 piwik0:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  1.3G  8.1G  14% /
   /dev/vdb        227G  188M  215G   1% /mnt
</pre>
</td></tr></table>
<p><br />
</p><p><br />
</p>
<h5><span class="mw-headline" id="2.2.1.4._Project">2.2.1.4. Project</span></h5>
<p>This node hosts a dedicated version of Bug Genie, available here.
</p>
<table>
<caption>Node <tt>project</tt>
</caption>
<tr>
<td><b>Linux release:</b>
</td>
<td>Ubuntu 12.04.1 LTS
</td></tr>
<tr>
<td><b>Number of nodes:</b>
</td>
<td>1
</td></tr>
<tr>
<td><b>Web application profiles:</b>
</td>
<td>
<ul><li> </li></ul>
</td></tr>
<tr>
<td><b>Services:</b>
</td>
<td>
<ul><li> <a href="#1.5._Common_services">#1.5. Common services</a></li>
<li> Apache2 w/ mpm-prefork</li></ul>
</td></tr>
<tr>
<td><b>Specs:</b>
</td>
<td>2 vCPU / 2 GB RAM / 60 GB HD
</td></tr>
<tr>
<td><b>Load average:</b>
</td>
<td>0.00, 0.01, 0.05
</td></tr>
<tr>
<td><b>Disk usage:</b>
</td>
<td>
<pre>   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  1.1G  8.3G  12% /
   /dev/vdb         50G  180M   47G   1% /mnt
</pre>
</td></tr></table>
<p><br />
</p>
<h5><span class="mw-headline" id="2.2.1.5._Code">2.2.1.5. Code</span></h5>
<p>This node is not fully working at the moment and it was planned to host code repositories using Gerrit application server.
</p>
<table>
<caption>Node <tt>code</tt>
</caption>
<tr>
<td><b>Linux release:</b>
</td>
<td>Ubuntu 12.04 LTS
</td></tr>
<tr>
<td><b>Number of nodes:</b>
</td>
<td>1
</td></tr>
<tr>
<td><b>Web application profiles:</b>
</td>
<td>
<ul><li> Gerrit (unfinished)</li></ul>
</td></tr>
<tr>
<td><b>Services:</b>
</td>
<td>
<ul><li> <a href="#1.5._Common_services">#1.5. Common services</a></li>
<li> Java (J2EE container)</li></ul>
</td></tr>
<tr>
<td><b>Specs:</b>
</td>
<td>2 vCPU / 2 GB RAM / 60 GB HD
</td></tr>
<tr>
<td><b>Load average:</b>
</td>
<td>0.03, 0.04, 0.05
</td></tr>
<tr>
<td><b>Disk usage:</b>
</td>
<td>
<pre>   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  1.1G  8.4G  12% /
   /dev/vdb         50G  180M   47G   1% /mnt
</pre>
</td></tr></table>
<p><br />
</p><p><br />
</p>
<h4><span class="mw-headline" id="2.2.2._Infrastructure_services">2.2.2. Infrastructure services</span></h4>
<h5><span class="mw-headline" id="2.2.2.1._Deployment">2.2.2.1. Deployment</span></h5>
<p>This node is the central point of access, it manages the local datacenter. From it, is possible to apply configuration settings through a remote execution and configuration management system called Salt Stack.
</p><p><b>From this instance, it is aggregating:</b>
</p>
<ul><li> Log files</li>
<li> State change execution</li></ul>
<table>
<caption>Node <tt>deployment</tt>
</caption>
<tr>
<td><b>Linux release:</b>
</td>
<td>Ubuntu 12.04 LTS Precise
</td></tr>
<tr>
<td><b>Number of nodes:</b>
</td>
<td>1
</td></tr>
<tr>
<td><b>Web application profiles:</b>
</td>
<td>
<ul><li> N/A</li></ul>
</td></tr>
<tr>
<td><b>Services:</b>
</td>
<td>
<ul><li> <a href="#1.5._Common_services">#1.5. Common services</a></li>
<li> Salt stack master</li></ul>
</td></tr>
<tr>
<td><b>Specs:</b>
</td>
<td>2 vCPU / 2 GB RAM / 60 GB HD
</td></tr>
<tr>
<td><b>Load average:</b>
</td>
<td>0.38 0.31 0.26
</td></tr>
<tr>
<td><b>Disk usage:</b>
</td>
<td>
<pre> Filesystem   Size  Used Avail  Use% Mounted on
 /dev/vda1    9.9G  4.6G  4.8G  50%  /
 /dev/vdb      50G   17G   31G  36%  /mnt
</pre>
</td></tr></table>
<p><br />
</p><p><br />
</p>
<h5><span class="mw-headline" id="2.2.2.2._Database">2.2.2.2. Database</span></h5>
<p>This node type is a database cluster. The current setup has a master and a read-only node.
</p><p><b>Instance goals:</b>
</p>
<ul><li> Provide database access</li>
<li> Manage various database systems (e.g. MySQL)</li></ul>
<table>
<caption>Node <tt>db[n]</tt>
</caption>
<tr>
<td><b>Linux release:</b>
</td>
<td>Ubuntu 10.04.3 LTS Lucid
</td></tr>
<tr>
<td><b>Number of nodes:</b>
</td>
<td>2
</td></tr>
<tr>
<td><b>Web application profiles:</b>
</td>
<td>
<ul><li> N/A</li></ul>
</td></tr>
<tr>
<td><b>Services:</b>
</td>
<td>
<ul><li> <a href="#1.5._Common_services">#1.5. Common services</a></li>
<li> MySQL server (5.1.x), an old version, upgrade? (see <a href="#3.3.2.2._Database">#3.3.2.2. Database</a> notes)</li></ul>
</td></tr>
<tr>
<td><b>Specs:</b>
</td>
<td>4 vCPU / 16 GB RAM / 480 GB HD
</td></tr>
<tr>
<td><b>Load average:</b>
</td>
<td>
<ul><li> 0.13, 0.07, 0.02</li>
<li> 0.32, 0.27, 0.20</li></ul>
</td></tr>
<tr>
<td><b>Disk usage:</b>
</td>
<td>
<pre> db1:
   Filesystem   Size  Used Avail  Use% Mounted on
   /dev/vda     9.9G  3.5G  5.9G  38% /
   /dev/vdb     463G  3.1G  437G   1% /mnt
 db2:
   Filesystem   Size  Used Avail Use% Mounted on
   /dev/vda     9.9G  2.7G  6.7G  29% /
   /dev/vdb     463G  3.1G  437G   1% /mnt
</pre>
</td></tr></table>
<p><br />
</p>
<h5><span class="mw-headline" id="2.2.2.1._Memcache">2.2.2.1. Memcache</span></h5>
<p>Current MediaWiki uses memcache services, but it is not validated whether it is used to its full potential.
</p>
<table>
<caption>Node <tt>memcache[n]</tt>
</caption>
<tr>
<td><b>Linux release:</b>
</td>
<td>Ubuntu 12.04.2 LTS Precise
</td></tr>
<tr>
<td><b>Number of nodes:</b>
</td>
<td>2
</td></tr>
<tr>
<td><b>Web application profiles:</b>
</td>
<td>
<ul><li> N/A</li></ul>
</td></tr>
<tr>
<td><b>Services:</b>
</td>
<td>
<ul><li> <a href="#1.5._Common_services">#1.5. Common services</a></li>
<li> Memcached</li></ul>
</td></tr>
<tr>
<td><b>Specs:</b>
</td>
<td>2 vCPU / 4 GB RAM / 120 GB HD
</td></tr>
<tr>
<td><b>Load average:</b>
</td>
<td>
<ul><li> 0.00, 0.01, 0.05</li>
<li> 0.01, 0.03, 0.05</li></ul>
</td></tr>
<tr>
<td><b>Disk usage:</b>
</td>
<td>
<pre> memcache1:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G 1017M  8.4G  11% /
   /dev/vdb        109G  188M  103G   1% /mnt
 memcache2:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G 1017M  8.4G  11% /
   /dev/vdb        109G  188M  103G   1% /mnt
</pre>
</td></tr></table>
<p><br />
</p>
<h5><span class="mw-headline" id="2.2.2.1._Storage">2.2.2.1. Storage</span></h5>
<p>Currently, the storage is using GlusterFS as the system and many instances are using it as well.
</p><p>Usage:
</p>
<ul><li> Images volume mountpoint</li>
<li> App specific user uploads storage</li></ul>
<table>
<caption>Node <tt>storage[n]</tt>
</caption>
<tr>
<td><b>Linux release:</b>
</td>
<td>Ubuntu 12.04.2 LTS Precise
</td></tr>
<tr>
<td><b>Number of nodes:</b>
</td>
<td>2
</td></tr>
<tr>
<td><b>Web application profiles:</b>
</td>
<td>
<ul><li> </li></ul>
</td></tr>
<tr>
<td><b>Services:</b>
</td>
<td>
<ul><li> <a href="#1.5._Common_services">#1.5. Common services</a></li>
<li> GlusterFS server</li></ul>
</td></tr>
<tr>
<td><b>Specs:</b>
</td>
<td>2 vCPU / 2 GB RAM / 60 GB HD
</td></tr>
<tr>
<td><b>Load average:</b>
</td>
<td>
<ul><li> 0.04, 0.03, 0.05</li>
<li> 0.04, 0.04, 0.05</li></ul>
</td></tr>
<tr>
<td><b>Disk usage:</b>
</td>
<td>
<pre> storage3:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  2.5G  6.9G  27% /
   /dev/vdb         50G  466M   47G   1% /mnt
   /dev/vdc         50G  832M   50G   2% /srv/storage
 storage5:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  2.5G  6.9G  27% /
   /dev/vdb         50G  180M   47G   1% /mnt
   /dev/vdc         50G  492M   50G   1% /srv/storage
</pre>
</td></tr></table>
<p><br />
</p>
<h4><span class="mw-headline" id="2.2.3._Process_services">2.2.3. Process services</span></h4>
<h5><span class="mw-headline" id="2.2.3.1._Backup">2.2.3.1. Backup</span></h5>
<table>
<caption>Node <tt>backup</tt>
</caption>
<tr>
<td><b>Linux release:</b>
</td>
<td>Ubuntu 12.04 LTS
</td></tr>
<tr>
<td><b>Number of nodes:</b>
</td>
<td>1
</td></tr>
<tr>
<td><b>Web application profiles:</b>
</td>
<td>
<ul><li> </li></ul>
</td></tr>
<tr>
<td><b>Services:</b>
</td>
<td>
<ul><li> <a href="#1.5._Common_services">#1.5. Common services</a></li></ul>
</td></tr>
<tr>
<td><b>Specs:</b>
</td>
<td>2 vCPU / 2 GB RAM / 60 GB HD
</td></tr>
<tr>
<td><b>Load average:</b>
</td>
<td>0.00, 0.01, 0.05
</td></tr>
<tr>
<td><b>Disk usage:</b>
</td>
<td>
<pre> Filesystem                     Size  Used Avail Use% Mounted on
 /dev/vda1                      9.9G  887M  8.5G  10% /
 /dev/vdb                        50G   50G     0 100% /mnt
 /dev/mapper/backup1-lvbackup1   40G   40G  122M 100% /mnt/backup
</pre>
</td></tr></table>
<p><br />
</p>
<h5><span class="mw-headline" id="2.2.3.2._Bots">2.2.3.2. Bots</span></h5>
<p>This node is hosting a Python program called ‘Lumberjack’ that is acting as a IRC bot logging chat events on some channels.
</p>
<table>
<caption>Node <tt>bots</tt>
</caption>
<tr>
<td><b>Linux release:</b>
</td>
<td>Ubuntu 12.04 LTS
</td></tr>
<tr>
<td><b>Number of nodes:</b>
</td>
<td>1
</td></tr>
<tr>
<td><b>Web application profiles:</b>
</td>
<td>
<ul><li> </li></ul>
</td></tr>
<tr>
<td><b>Services:</b>
</td>
<td>
<ul><li> <a href="#1.5._Common_services">#1.5. Common services</a></li>
<li> Lumberjack python process</li></ul>
</td></tr>
<tr>
<td><b>Specs:</b>
</td>
<td>1 vCPU / 1 GB RAM / 30 GB HD
</td></tr>
<tr>
<td><b>Load average:</b>
</td>
<td>0.18, 0.17, 0.21
</td></tr>
<tr>
<td><b>Disk usage:</b>
</td>
<td>
<pre>   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  896M  8.5G  10% /
   /dev/vdb         20G  173M   19G   1% /mnt
</pre>
</td></tr></table>
<p><br />
</p>
<hr />
<p><br />
</p>
<h2><span class="mw-headline" id="3._Refactored_infrastructure">3. Refactored infrastructure</span></h2>
<h3><span class="mw-headline" id="3.1._Type_of_deployment">3.1. Type of deployment</span></h3>
<p>The objective is to enforce testing prior to applying it to the production environment.
</p><p>Although the production environment has fixed resources, the Staging/testing environment can be built on demand with flexible amount of IP/VMs to ensure the developed configuration works prior to apply it to production.
</p><p><br />
</p>
<h4><span class="mw-headline" id="Production">Production</span></h4>
<p>Production environment is very important and it must be fully tested in Staging/Testing before make them available to the user.
</p><p><br />
</p>
<h4><span class="mw-headline" id="Staging.2Ftesting">Staging/testing</span></h4>
<p>The objective of this server environment is to reproduce an isolated version of the production environment.
</p><p>Therefore,  the idea is to have the capability of a fully working and isolated environment version for short and temporary period for development and/or testing purposes.
</p><p>It is estimated that during a period of time, we might have 2 distinct deployments running for testing and acceptance testing prior to be applied in production.
</p><p><br />
</p><p><br />
</p>
<h3><span class="mw-headline" id="3.2._Refactor_overview">3.2. Refactor overview</span></h3>
<ul><li> Linux release: Ubuntu 12.04 LTS is planned to be used on ALL instances;</li>
<li> Some other ideas to improve the infrastructure are described in <a href="/wiki/WPD:Infrastructure/priorities" title="WPD:Infrastructure/priorities">WPD:Infrastructure/priorities</a>, although relevant to the project, they are considered out of scope of the present document;</li>
<li> In addition to the ideas described in the wiki, some other changes are described considered key to this refactor and has an issue number to work on:
<ul><li> <a rel="nofollow" class="external text" href="http://project.webplatform.org/infrastructure/issues/INFR-39">#INFR-39</a></li>
<li> <a rel="nofollow" class="external text" href="http://project.webplatform.org/infrastructure/issues/INFR-40">#INFR-40</a></li>
<li> <a rel="nofollow" class="external text" href="http://project.webplatform.org/infrastructure/issues/INFR-41">#INFR-41</a></li></ul></li></ul>
<p><br />
</p>
<h4><span class="mw-headline" id="3.2.1._Operating_System_version_discrepancy_to_solve">3.2.1. Operating System version discrepancy to solve</span></h4>
<p>The objective is to migrate the Operating System version to current Ubuntu LTS version. In the meantime, two LTS versions will be supported.
</p><p><br />
</p><p><br />
</p>
<h4><span class="mw-headline" id="3.2.2._Misc._tasks">3.2.2. Misc. tasks</span></h4>
<p>Some tasks might improve the overall performance of the system, they should be analyzed and reported into <a rel="nofollow" class="external text" href="http://project.webplatform.org/infrastructure/issues">the issue tracker</a>
</p><p><b>High gain, low ETA</b>
</p>
<ul><li> Install Logstash and ensure ALL services reports logs to it (install on <a href="#3.3.2.1._Deployment">#3.3.2.1. Deployment</a>?)</li>
<li> VHost configuration (both NGINX than Apache)
<ul><li> Default vhost (e.g. via the IP) to serve a static file</li>
<li> Each vhost only allows http communication to known hosts (i.e. fastly, aremysiteup, monitoring, etc)</li>
<li> Clean up the hosts with only the minimal web applications deployed with their vhosts</li></ul></li>
<li> Use/configure fastly monitoring (I need to read about what we can get out of it)</li>
<li> Use fastly 50x error pages with static  </li>
<li> Hide to a maximum server version in vhosts/php configuration</li></ul>
<p><b>Lower priority but important</b>
</p>
<ul><li> Install StartSSL certificate 
<ul><li> Ensure login forms uses the SSL VHost</li>
<li> Ensure all services with login has a SSL VHost</li></ul></li>
<li> Use secondary partition for manifest storage mount as XFS for quick snapshots</li>
<li> Ensure tracking code is installed through salt stack, and not manually (!)</li></ul>
<p><br />
</p>
<h4><span class="mw-headline" id="3.2.3._To_be_analyzed">3.2.3. To be analyzed</span></h4>
<ul><li> Analyse whether we can MySQL server version (possible, would break things?)
<ul><li> See <a href="#3.3.2.2._Database">#3.3.2.2. Database</a> notes</li></ul></li>
<li> DHCP server (install on <a href="#3.3.2.1._Deployment">#3.3.2.1. Deployment</a>?)</li>
<li> DNS server (install on <a href="#3.3.2.1._Deployment">#3.3.2.1. Deployment</a>?)</li>
<li> Elastic search 
<ul><li> client on which node? </li>
<li> server on which node?</li></ul></li>
<li> Benchmarking tools
<ul><li> Database</li>
<li> Memcached with libmemcached-tools (see <a rel="nofollow" class="external text" href="http://docs.libmemcached.org/">docs</a>)</li>
<li> HTTP server benchmarking tools</li>
<li> Mailing testing utilities</li></ul></li>
<li> Mailing relay exit node</li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="3.3._Instance_flavors">3.3. Instance flavors</span></h3>
<p>The architecture of the solution is going to be re-evaluated, as there are also other instances that do not need to be exactly the same.
</p><p><br />
</p><p><br />
</p>
<h4><span class="mw-headline" id="3.3.1._Application_servers">3.3.1. Application servers</span></h4>
<p>An app server should have deployed one or more web application virtual host. This should not be impacted by whether application A is also present with application B on the same node. It is a current issue, which causes some false-positive errors in the logs and creates unneeded noise.
</p><p><br />
</p>
<dl><dd><b>Provisioning:</b>
<ol><li> 7  Public IP addresses</li>
<li> 8  VMs</li></ol></dd></dl>
<dl><dd><b>Application profile distribution proposal:</b></dd>
<dd></dd>
<dd><i>Profile “A”</i>
<ul><li> qty: 5</li>
<li> using:
<ul><li> WordPress</li>
<li> MediaWiki</li>
<li> BugGenie</li></ul></li></ul></dd>
<dd></dd>
<dd><i>Profile “B”</i>
<ul><li> qty: 1</li>
<li> using:
<ul><li> Gerrit</li>
<li> Talk</li>
<li> Monitor</li></ul></li></ul></dd>
<dd></dd>
<dd><i>Profile “C”</i>
<ul><li> qty: 2</li>
<li> using:
<ul><li> Piwik</li>
<li> Dabblet</li></ul></li></ul></dd></dl>
<dl><dd><b>To analyze:</b>
<ul><li> Not all node types requires a public IP address, nodes like Ganglia, Bug genie, and Piwik could be behind a single NGINX proxy server as it is likely to be less used than a typical MediaWiki/WordPress;</li>
<li> See to support both NGINX AND Apache2 as HTTP server for all web applications;:* Block storage/NFS mount point for same data across instances;</li>
<li> Find pro and cons regarding multiple web application server sharing the same storage service (e.g. NFS cluster) spanning across multiple instances. What is recommended, how is it failure resilient?</li>
<li> Nice to have: KVM-like console access (in case of firewall problem, or hard failure);</li></ul></dd>
<dd></dd>
<dd><b>Profiles:</b>
<ul><li> <b>WordPress</b>
<ul><li> Software: WordPress, in PHP</li>
<li> virtual host name: blog.webplatform.org</li></ul></li>
<li> <b>MediaWiki</b>
<ul><li> Software: MediaWiki, in PHP</li>
<li> virtual host name: docs.webplatform.org</li></ul></li>
<li> <b>Ganglia frontend</b>
<ul><li> Software: Ganglia web frontend</li>
<li> virtual host name: monitor.webplatform.org</li></ul></li>
<li> <b>Piwik</b>
<ul><li> Software: Piwik, in PHP</li>
<li> virtual host name: stats.webplatform.org</li></ul></li>
<li> <b>Talk</b>
<ul><li> Software: <a rel="nofollow" class="external text" href="http://www.question2answer.org/">Question2Answer</a></li>
<li> virtual host name: talk.webplatform.org</li></ul></li>
<li> <b>Bug genie</b>
<ul><li> Software: <a rel="nofollow" class="external text" href="http://www.thebuggenie.com/">Bug Genie</a></li>
<li> virtual host name: project.webplatform.org</li></ul></li>
<li> <b>Gerrit</b> <br /><i>Note:</i> Although there is an instance in the current state that is called code, it is NOT for Gerrit, but for Dabblet.
<ul><li> Software: <a rel="nofollow" class="external text" href="https://code.google.com/p/gerrit/">Gerrit</a></li>
<li> virtual host name: TBD</li></ul></li>
<li> <b>Dabblet</b>
<ul><li> Software: <a rel="nofollow" class="external text" href="https://github.com/LeaVerou/dabblet">Dabblet</a></li>
<li> virtual host name: code.webplatform.org</li></ul></li></ul></dd></dl>
<p><br />
</p><p><br />
</p>
<h4><span class="mw-headline" id="3.3.2._Infrastructure_servers">3.3.2. Infrastructure servers</span></h4>
<dl><dd><b>Provisioning:</b></dd>
<dd></dd>
<dd>The following is a sum of the described profiles below.</dd>
<dd>
<ol><li> 2  Public IP addresses</li>
<li> database node (DB hot backup)</li>
<li> deployment node</li>
<li> 5-11  VMs</li></ol></dd></dl>
<p><br />
</p><p><br />
</p>
<h5><span class="mw-headline" id="3.3.2.1._Deployment">3.3.2.1. Deployment</span></h5>
<p>The objective of this instance is to be the only machine to connect to. Not only should it manage Nova and Salt stack commands, but also assist in other various tasks.
</p><p>Assuming multi-site hosting system is built, we will use <a rel="nofollow" class="external text" href="http://docs.saltstack.com/ref/cli/salt-syndic.html">Salt Stack’s ‘Syndic’ feature</a> to pass along from the central master (to be yet determined).
</p><p><br />
</p>
<dl><dd><b>Provisioning:</b>
<ul><li> 1 VM</li>
<li> This node does not need direct access to a large amount of CPU/RAM/HD, as it is used solely for receiving/sending data from other members of the local network.</li></ul></dd></dl>
<dl><dd><b>Requirements:</b>
<ol><li> Block storage, or mount-point (NFS?) for state manifests and user data</li>
<li> Use secondary partition for manifest storage mount as XFS for quick snapshots</li>
<li> Nice to have: KVM-like access</li></ol></dd></dl>
<p><br />
</p><p><br />
</p>
<h5><span class="mw-headline" id="3.3.2.2._Database">3.3.2.2. Database</span></h5>
<p>The current setup of 2 is estimated to be enough for our needs; however, it is also happens to be a  bottleneck in some situations, as we only have 1 read-write AND 1 read-only machines (2 total).
</p><p>The most of the current application stack do not necessarily have drop-in caching mechanism. We should analyze in depth whether we can detect the ‘too many connections’ problem, and its usage.
</p><p><br />
</p>
<dl><dd><b>Provisioning:</b>
<ul><li> 2-4 VMs</li>
<li> 1 Public IP address</li>
<li> Preferred to have significant amount of vCPU/vRAM</li></ul></dd>
<dd></dd>
<dd><b>To be analyzed:</b>
<ul><li> We should have one name, but multiple A entries, of write(able) database servers for round-robin.</li>
<li> or maybe is broken, something yet to evaluate.</li>
<li> Create hot backup replication to shelter site (on W3C infra)</li>
<li> Database connector proxy (see <a rel="nofollow" class="external text" href="http://dev.mysql.com/doc/refman/5.6/en/mysql-proxy.html">mysql-proxy</a>)</li>
<li> Upgrade MySQL version and/or see for alternate (compatible) distribution: Percona, MariaDB</li></ul></dd>
<dd></dd>
<dd><b>Requirements:</b>
<ol><li> Make secondary drive as XFS, and to configure MySQL/etc database storage so we can make ‘snapshots’</li>
<li> Block storage, or mount-point (NFS?);</li>
<li> Use secondary partition for database data as XFS for snapshots</li></ol></dd></dl>
<p><br />
</p><p><br />
</p>
<h5><span class="mw-headline" id="3.3.2.3._Memcache">3.3.2.3. Memcache</span></h5>
<dl><dd><b>Provisioning:</b>
<ul><li> 1-2 VMs</li>
<li> Should have good amount of vCPU/vRAM (add number)</li></ul></dd>
<dd></dd>
<dd><b>To be analyzed:</b>
<ul><li> If we get memcached with other similar technologies, we can create a cluster of services (e.g. memcached, elastic search, redis).</li></ul></dd></dl>
<p><br />
</p><p><br />
</p>
<h5><span class="mw-headline" id="3.3.2.4._Storage">3.3.2.4. Storage</span></h5>
<dl><dd><b>Provisioning:</b>
<ul><li> 1-2 VMs</li>
<li> Should have a good amount of storage capacity, and leverage XFS’s snapshot feature.</li></ul></dd>
<dd></dd>
<dd><b>To be analyzed:</b>
<ul><li> If we have block storage service, this node should only handle data transfers to the block storage service by creating a local copy, then copy it over.</li>
<li> This node might change its purpose and be replaced by a rsync orchestration system to move files around, e.g.:</li>
<li> Making a local copy, then creating incremental backups on block storage service</li>
<li> Updating CDN static files</li></ul></dd></dl>
<p><br />
</p><p><br />
</p>
<h4><span class="mw-headline" id="3.3.3._Process_servers">3.3.3. Process servers</span></h4>
<p>Similar to the Web application profile, a node providing a process service should be installable to any server without impacting or breaking other managed services.
</p><p>Although the refactor will make sure the two profiles are independent and applicable anywhere in the infrastructure, it is considered to merge the two profiles on the same Instance.
</p><p><br />
</p>
<dl><dd><b>Provisioning:</b>
<ol><li> 1-2  VMs</li>
<li> Lower vHD is acceptable</li></ol></dd>
<dd></dd>
<dd><b>Profiles:</b>
<ul><li> Backup <br /><i>Note:</i> This configuration might change as we have block storage and we might use storage as handlers to move backup around.</li>
<li> IRC Bot</li></ul></dd></dl>
<p><br />
</p><p><br />
</p>
<hr />
<p><br />
</p><p><br />
</p>
<h2><span class="mw-headline" id="4._Service_provider_infrastructure">4. Service provider infrastructure</span></h2>
<p>Although it might be impossible to the provider offer a fully featured Open Stack environment with Public facing web dashboard, we would appreciate to have access to bare-metal machines to your capabilities with the latest stable OpenStack version (Folsom, Grizzly).
</p><p>Our usage level does not require access to a web front end, nor a web control panel. Our infrastructure has already systems configured to communicate to OpenStack using the ‘nova’ utility.
</p><p><br />
</p><p><br />
</p>
<h3><span class="mw-headline" id="4.1._Questions">4.1. Questions</span></h3>
<p>Some details to clarify about what may be available within our upcoming provider infrastructure.
</p><p>Is there a local...?
</p>
<ul><li> Ubuntu/Debian repository mirror</li>
<li> NTP server</li>
<li> SMTP relay or exit relays</li>
<li> Do you provide/have recommendations regarding VPN deployment for cross-site replication and security?</li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:9518-0!*!0!!*!*!*!esi=1 and timestamp 20150731184533 and revision id 41689
 -->
