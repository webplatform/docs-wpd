---
title: 2013 WebPlatform Docs infrastructure usage and future state
uri: 'WPD:Infrastructure/analysis/2013-Usage and future state'

---
**NOTE**: There is a *TLDR* version describing software and hardware requirement available [WPD:Infrastructure/analysis/2013-Hardware and software requirements](/WPD:Infrastructure/analysis/2013-Hardware_and_software_requirements)

## <span>Introduction</span>

[WebPlatform Docs](http://webplatform.org/) is now close to a year old. The goal of this document is to describe the current health of the system and how we can make it better.

As [Ryan described in the launch post](http://blog.webplatform.org/2012/10/building-web-platforms-infrastructure/), we can see a year later that the structure is handling the load fairly well.

But as with anything, we also learned that we have to improve the system to make it more stable. Since the last year was mostly focussing on the content than the infrastructure, things at some spots were left behind and the system is in a need of a good maintenance.

This is why [*Renoir* has been hired](http://blog.webplatform.org/2013/08/hi-my-name-s-renoir-ill-be-your-devops-for-the-web-platform/): To maintain the system and contribute to the site success, full time.

This document describes in depth the usage, statistics of the current infrastructure, and what is to come with it.

* * * * *

## <span>1. Executive Summary</span>

### <span>1.1. Usage comparison table</span>

<table>
<caption>VMs usage comparsion</caption>
<col width="33%" />
<col width="33%" />
<col width="33%" />
<tbody>
<tr class="odd">
<td align="left"></td>
<td align="left">Current</td>
<td align="left">Future</td>
</tr>
<tr class="even">
<td align="left"><strong>Application services</strong></td>
<td align="left">production:
<ul>
<li>app: 5</li>
<li>monitor:1</li>
<li>piwik: 2</li>
<li>project: 1</li>
<li>code:1</li>
</ul></td>
<td align="left">production:
<ul>
<li>8</li>
</ul>
<p>temporary * :</p>
<ul>
<li>3</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Infrastructure services</strong></td>
<td align="left"><em>production</em>:
<ul>
<li>deployment: 1</li>
<li>db: 2</li>
<li>memcache: 2</li>
<li>storage: 2</li>
</ul></td>
<td align="left"><em>production</em>:
<ul>
<li>5-9</li>
</ul>
<p><em>temporary *</em>:</p>
<ul>
<li>5</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Process services</strong></td>
<td align="left"><em>production</em>:
<ul>
<li>backup: 1</li>
<li>bots: 1</li>
</ul></td>
<td align="left"><em>production</em>:
<ul>
<li>1-2</li>
</ul>
<p><em>temporary *</em>:</p>
<ul>
<li>1</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Sub-total</strong></td>
<td align="left"><em>production</em>:
<ul>
<li>19 VMs</li>
</ul></td>
<td align="left"><em>production</em>:
<ul>
<li>14-19 VMs</li>
</ul>
<p><em>temporary *</em>:</p>
<ul>
<li>9</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Total</strong></td>
<td align="left">19 VMs</td>
<td align="left">23-28 VMs <br /><em>Including *one only* one &quot;temporary environment&quot; up</em></td>
</tr>
</tbody>
</table>

Note 4

In Temporary environment, numbers may vary, we might want to always have a temporary environment running for common (non-local) development purposes.

### <span>1.2. Some facts about the current environment</span>

-   Fastly is reporting 3.4 Million requests for the month of August 2013;
-   Some VMs are used for development and should be removed or migrated to an isolated environment, see [\#3.1. Type of deployment](#3.1._Type_of_deployment);
-   No other environment than production (it has to change); The development work made in the production environment and might affect it;
-   Everybody with a shared account can do everything with no real control in the privileges;
-   4 VMs has to be Ubuntu 10.04, solely required for the instances described [\#2.2.1.1. MediaWiki, WordPress, Dabblet, Talk](#2.2.1.1._MediaWiki.2C_WordPress.2C_Dabblet.2C_Talk), to be solved in [\#3.2.1. Operating System version discrepancy to solve](#3.2.1._Operating_System_version_discrepancy_to_solve).

### <span>1.3. Current environment summary</span>

The following information summarizes the resources allocation used in the current environment.

See section [\#2. Current environment](#2._Current_environment) for more details.

-   **Production environment**
    -   25 Public IP addresses; it could be possible to work with 12 static IP addresses for production
    -   18 VMs production instances
    -   5 http/php (app servers)
    -   2 memcached
    -   2 mysql/db
    -   ... misc apps, storage, backup, monitoring, salt master, etc…
    -   4 VMs for testing or upcoming projects (not advertised)
-   **Temporary environment**
    -   N/A

Note 5 '**Important!'**

The current environment on HPCloud has no isolated “staging”, nor “test” deployment environment (i.e. “Temporary environment”), see [\#3.2. Refactor overview](#3.2._Refactor_overview) for problems it might cause.

### <span>1.4. Refactored infrastructure estimation summary</span>

The following describes the estimated resources required to build the new infrastructure to be used by September 2014.

See [\#3. Refactored infrastructure](#3._Refactored_infrastructure) for more details.

Although the fact that the desired production environment infrastructure could be sufficient by itself, the new infrastructure should support multi-site deployment.

The new infrastructure with support multi-site replication to a secondary site where database and files can be synced from one datacenter to another. Resource allocation for a secondary site has an estimated resource allocation similar to a “Temporary environment” in terms of numbers and will be improving service redundancy.

Note 1

The numbers described in the ‘Secondary environment’ section are to be considered in surplus, but it should be possible to use in some during defined period of time.

Note 2

We might consider creating an always-running ‘Secondary environment’ for ad-hoc development.

#### <span>Production environment</span>

-   9-12 Public IP address;
-   14-19 VMs;
    Note: some changes described in 3.2. Refactor overview might require to adjust the numbers;

#### <span>Temporary environment</span>

-   It should be possible to have more than one deployed “temporary” environment at a time (e.g. one for staging, one for test);
-   Number is approximate as it might change depending of the feature to be deployed and tested (e.g. We want to test fault tolerance on the DB, we might only need one web application instance, and 5 database servers)
-   \~9 Public IP Address;
-   \~9 VMs;

#### <span>Secondary environment</span>

-   Represent a reduced version of the production environment, a secondary site replicating the production;
-   Resource allocation is similar to a Temporary environment in terms of IP Addresses and VM quantities.

### <span>1.5. Common services</span>

Although the current infrastructure includes the services in common enumerated below, the Refactored infrastructure will also include them.

-   Salt minion agent
-   Ganglia monitor agent
-   GlusterFS client (in some cases, subject to change if we have Block storage)
-   Rsync xinetd service (rsync key is propagated through Salt)

* * * * *

## <span>2. Current environment</span>

### <span>2.2. Instance flavors</span>

Even though the current infrastructure does not have an explicit categorization scheme, each instance is conceptually separated into the following categories. The new infrastructure will have a similar categorization.

#### <span>2.2.1. Application services</span>

##### <span>2.2.1.1. MediaWiki, WordPress, Dabblet, Talk</span>

A generic profile server should serve only as a redundant HTTP app service. Each application server has a public IP address, but they are not broadcasted publicly in DNS records. Instead, it uses a third-party service (fastly) to balance the load.

<table>
<caption>Node <code>app[n]</code></caption>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><strong>Linux release:</strong></td>
<td align="left">Ubuntu 11.04 LTS Lucid</td>
</tr>
<tr class="even">
<td align="left"><strong>Web application profiles:</strong></td>
<td align="left"><ul>
<li>MediaWiki</li>
<li>Dabblet</li>
<li>WordPress</li>
<li>Talk</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Services:</strong></td>
<td align="left"><ul>
<li><a href="#1.5._Common_services">#1.5. Common services</a></li>
<li>Apache2 w/ mpm-prefork</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Specs:</strong></td>
<td align="left">4 vCPU / 8 GB RAM / 240 GB HD</td>
</tr>
<tr class="odd">
<td align="left"><strong>Load average:</strong></td>
<td align="left"><ul>
<li>0.20, 0.14, 0.10</li>
<li>0.13, 0.12, 0.14</li>
<li>0.20, 0.17, 0.14</li>
<li>0.24, 0.66, 0.42</li>
<li>0.49, 0.42, 0.39</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Disk usage:</strong></td>
<td align="left"><pre><code> app3:
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
   storage3:/wiki-images  50G  832M   50G   2% /srv/webplatform/wiki/images</code></pre></td>
</tr>
</tbody>
</table>

##### <span>2.2.1.2. Monitor</span>

This instance provides a web frontend to ganglia reports, and publish them publicly.

<table>
<caption>Node <code>monitor</code></caption>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><strong>Linux release:</strong></td>
<td align="left">Ubuntu 12.04.2 LTS Precise</td>
</tr>
<tr class="even">
<td align="left"><strong>Web application profiles:</strong></td>
<td align="left"><ul>
<li>Ganglia frontend</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Services:</strong></td>
<td align="left"><ul>
<li>Ganglia server</li>
<li><a href="#1.5._Common_services">#1.5. Common services</a></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Specs:</strong></td>
<td align="left">2 vCPU / 2 GB RAM / 60 GB HD</td>
</tr>
<tr class="odd">
<td align="left"><strong>Load average:</strong></td>
<td align="left">0.40, 0.42, 0.45</td>
</tr>
<tr class="even">
<td align="left"><strong>Disk usage:</strong></td>
<td align="left"><pre><code>   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  1.5G  7.9G  16% /
   /dev/vdb         50G  180M   47G   1% /mnt</code></pre></td>
</tr>
</tbody>
</table>

##### <span>2.2.1.3. Piwik</span>

This instance provides piwik dashboard web front-end and tracking beacon.

<table>
<caption>Node <code>piwik[n]</code></caption>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><strong>Linux release:</strong></td>
<td align="left">Ubuntu 12.04.1 LTS</td>
</tr>
<tr class="even">
<td align="left"><strong>Number of nodes:</strong></td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left"><strong>Web application profiles:</strong></td>
<td align="left"><ul>
<li>Piwik</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Services:</strong></td>
<td align="left"><ul>
<li>Apache2 w/ mpm-prefork</li>
<li><a href="#1.5._Common_services">#1.5. Common services</a></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Specs:</strong></td>
<td align="left">4 vCPU / 8 GB RAM / 240 GB HD</td>
</tr>
<tr class="even">
<td align="left"><strong>Load average:</strong></td>
<td align="left"><ul>
<li>0.00, 0.01, 0.05</li>
<li>0.00, 0.01, 0.05</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Disk usage:</strong></td>
<td align="left"><pre><code> piwik1:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  1.3G  8.2G  13% /
   /dev/vdb        227G  188M  215G   1% /mnt
 piwik0:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  1.3G  8.1G  14% /
   /dev/vdb        227G  188M  215G   1% /mnt</code></pre></td>
</tr>
</tbody>
</table>

##### <span>2.2.1.4. Project</span>

This node hosts a dedicated version of Bug Genie, available here.

<table>
<caption>Node <code>project</code></caption>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><strong>Linux release:</strong></td>
<td align="left">Ubuntu 12.04.1 LTS</td>
</tr>
<tr class="even">
<td align="left"><strong>Number of nodes:</strong></td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left"><strong>Web application profiles:</strong></td>
<td align="left"><ul>
<li></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Services:</strong></td>
<td align="left"><ul>
<li><a href="#1.5._Common_services">#1.5. Common services</a></li>
<li>Apache2 w/ mpm-prefork</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Specs:</strong></td>
<td align="left">2 vCPU / 2 GB RAM / 60 GB HD</td>
</tr>
<tr class="even">
<td align="left"><strong>Load average:</strong></td>
<td align="left">0.00, 0.01, 0.05</td>
</tr>
<tr class="odd">
<td align="left"><strong>Disk usage:</strong></td>
<td align="left"><pre><code>   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  1.1G  8.3G  12% /
   /dev/vdb         50G  180M   47G   1% /mnt</code></pre></td>
</tr>
</tbody>
</table>

##### <span>2.2.1.5. Code</span>

This node is not fully working at the moment and it was planned to host code repositories using Gerrit application server.

<table>
<caption>Node <code>code</code></caption>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><strong>Linux release:</strong></td>
<td align="left">Ubuntu 12.04 LTS</td>
</tr>
<tr class="even">
<td align="left"><strong>Number of nodes:</strong></td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left"><strong>Web application profiles:</strong></td>
<td align="left"><ul>
<li>Gerrit (unfinished)</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Services:</strong></td>
<td align="left"><ul>
<li><a href="#1.5._Common_services">#1.5. Common services</a></li>
<li>Java (J2EE container)</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Specs:</strong></td>
<td align="left">2 vCPU / 2 GB RAM / 60 GB HD</td>
</tr>
<tr class="even">
<td align="left"><strong>Load average:</strong></td>
<td align="left">0.03, 0.04, 0.05</td>
</tr>
<tr class="odd">
<td align="left"><strong>Disk usage:</strong></td>
<td align="left"><pre><code>   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  1.1G  8.4G  12% /
   /dev/vdb         50G  180M   47G   1% /mnt</code></pre></td>
</tr>
</tbody>
</table>

#### <span>2.2.2. Infrastructure services</span>

##### <span>2.2.2.1. Deployment</span>

This node is the central point of access, it manages the local datacenter. From it, is possible to apply configuration settings through a remote execution and configuration management system called Salt Stack.

**From this instance, it is aggregating:**

-   Log files
-   State change execution

<table>
<caption>Node <code>deployment</code></caption>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><strong>Linux release:</strong></td>
<td align="left">Ubuntu 12.04 LTS Precise</td>
</tr>
<tr class="even">
<td align="left"><strong>Number of nodes:</strong></td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left"><strong>Web application profiles:</strong></td>
<td align="left"><ul>
<li>N/A</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Services:</strong></td>
<td align="left"><ul>
<li><a href="#1.5._Common_services">#1.5. Common services</a></li>
<li>Salt stack master</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Specs:</strong></td>
<td align="left">2 vCPU / 2 GB RAM / 60 GB HD</td>
</tr>
<tr class="even">
<td align="left"><strong>Load average:</strong></td>
<td align="left">0.38 0.31 0.26</td>
</tr>
<tr class="odd">
<td align="left"><strong>Disk usage:</strong></td>
<td align="left"><pre><code> Filesystem   Size  Used Avail  Use% Mounted on
 /dev/vda1    9.9G  4.6G  4.8G  50%  /
 /dev/vdb      50G   17G   31G  36%  /mnt</code></pre></td>
</tr>
</tbody>
</table>

##### <span>2.2.2.2. Database</span>

This node type is a database cluster. The current setup has a master and a read-only node.

**Instance goals:**

-   Provide database access
-   Manage various database systems (e.g. MySQL)

<table>
<caption>Node <code>db[n]</code></caption>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><strong>Linux release:</strong></td>
<td align="left">Ubuntu 10.04.3 LTS Lucid</td>
</tr>
<tr class="even">
<td align="left"><strong>Number of nodes:</strong></td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left"><strong>Web application profiles:</strong></td>
<td align="left"><ul>
<li>N/A</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Services:</strong></td>
<td align="left"><ul>
<li><a href="#1.5._Common_services">#1.5. Common services</a></li>
<li>MySQL server (5.1.x), an old version, upgrade? (see <a href="#3.3.2.2._Database">#3.3.2.2. Database</a> notes)</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Specs:</strong></td>
<td align="left">4 vCPU / 16 GB RAM / 480 GB HD</td>
</tr>
<tr class="even">
<td align="left"><strong>Load average:</strong></td>
<td align="left"><ul>
<li>0.13, 0.07, 0.02</li>
<li>0.32, 0.27, 0.20</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Disk usage:</strong></td>
<td align="left"><pre><code> db1:
   Filesystem   Size  Used Avail  Use% Mounted on
   /dev/vda     9.9G  3.5G  5.9G  38% /
   /dev/vdb     463G  3.1G  437G   1% /mnt
 db2:
   Filesystem   Size  Used Avail Use% Mounted on
   /dev/vda     9.9G  2.7G  6.7G  29% /
   /dev/vdb     463G  3.1G  437G   1% /mnt</code></pre></td>
</tr>
</tbody>
</table>

##### <span>2.2.2.1. Memcache</span>

Current MediaWiki uses memcache services, but it is not validated whether it is used to its full potential.

<table>
<caption>Node <code>memcache[n]</code></caption>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><strong>Linux release:</strong></td>
<td align="left">Ubuntu 12.04.2 LTS Precise</td>
</tr>
<tr class="even">
<td align="left"><strong>Number of nodes:</strong></td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left"><strong>Web application profiles:</strong></td>
<td align="left"><ul>
<li>N/A</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Services:</strong></td>
<td align="left"><ul>
<li><a href="#1.5._Common_services">#1.5. Common services</a></li>
<li>Memcached</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Specs:</strong></td>
<td align="left">2 vCPU / 4 GB RAM / 120 GB HD</td>
</tr>
<tr class="even">
<td align="left"><strong>Load average:</strong></td>
<td align="left"><ul>
<li>0.00, 0.01, 0.05</li>
<li>0.01, 0.03, 0.05</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Disk usage:</strong></td>
<td align="left"><pre><code> memcache1:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G 1017M  8.4G  11% /
   /dev/vdb        109G  188M  103G   1% /mnt
 memcache2:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G 1017M  8.4G  11% /
   /dev/vdb        109G  188M  103G   1% /mnt</code></pre></td>
</tr>
</tbody>
</table>

##### <span>2.2.2.1. Storage</span>

Currently, the storage is using GlusterFS as the system and many instances are using it as well.

Usage:

-   Images volume mountpoint
-   App specific user uploads storage

<table>
<caption>Node <code>storage[n]</code></caption>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><strong>Linux release:</strong></td>
<td align="left">Ubuntu 12.04.2 LTS Precise</td>
</tr>
<tr class="even">
<td align="left"><strong>Number of nodes:</strong></td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left"><strong>Web application profiles:</strong></td>
<td align="left"><ul>
<li></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Services:</strong></td>
<td align="left"><ul>
<li><a href="#1.5._Common_services">#1.5. Common services</a></li>
<li>GlusterFS server</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Specs:</strong></td>
<td align="left">2 vCPU / 2 GB RAM / 60 GB HD</td>
</tr>
<tr class="even">
<td align="left"><strong>Load average:</strong></td>
<td align="left"><ul>
<li>0.04, 0.03, 0.05</li>
<li>0.04, 0.04, 0.05</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Disk usage:</strong></td>
<td align="left"><pre><code> storage3:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  2.5G  6.9G  27% /
   /dev/vdb         50G  466M   47G   1% /mnt
   /dev/vdc         50G  832M   50G   2% /srv/storage
 storage5:
   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  2.5G  6.9G  27% /
   /dev/vdb         50G  180M   47G   1% /mnt
   /dev/vdc         50G  492M   50G   1% /srv/storage</code></pre></td>
</tr>
</tbody>
</table>

#### <span>2.2.3. Process services</span>

##### <span>2.2.3.1. Backup</span>

<table>
<caption>Node <code>backup</code></caption>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><strong>Linux release:</strong></td>
<td align="left">Ubuntu 12.04 LTS</td>
</tr>
<tr class="even">
<td align="left"><strong>Number of nodes:</strong></td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left"><strong>Web application profiles:</strong></td>
<td align="left"><ul>
<li></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Services:</strong></td>
<td align="left"><ul>
<li><a href="#1.5._Common_services">#1.5. Common services</a></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Specs:</strong></td>
<td align="left">2 vCPU / 2 GB RAM / 60 GB HD</td>
</tr>
<tr class="even">
<td align="left"><strong>Load average:</strong></td>
<td align="left">0.00, 0.01, 0.05</td>
</tr>
<tr class="odd">
<td align="left"><strong>Disk usage:</strong></td>
<td align="left"><pre><code> Filesystem                     Size  Used Avail Use% Mounted on
 /dev/vda1                      9.9G  887M  8.5G  10% /
 /dev/vdb                        50G   50G     0 100% /mnt
 /dev/mapper/backup1-lvbackup1   40G   40G  122M 100% /mnt/backup</code></pre></td>
</tr>
</tbody>
</table>

##### <span>2.2.3.2. Bots</span>

This node is hosting a Python program called ‘Lumberjack’ that is acting as a IRC bot logging chat events on some channels.

<table>
<caption>Node <code>bots</code></caption>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><strong>Linux release:</strong></td>
<td align="left">Ubuntu 12.04 LTS</td>
</tr>
<tr class="even">
<td align="left"><strong>Number of nodes:</strong></td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left"><strong>Web application profiles:</strong></td>
<td align="left"><ul>
<li></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Services:</strong></td>
<td align="left"><ul>
<li><a href="#1.5._Common_services">#1.5. Common services</a></li>
<li>Lumberjack python process</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Specs:</strong></td>
<td align="left">1 vCPU / 1 GB RAM / 30 GB HD</td>
</tr>
<tr class="even">
<td align="left"><strong>Load average:</strong></td>
<td align="left">0.18, 0.17, 0.21</td>
</tr>
<tr class="odd">
<td align="left"><strong>Disk usage:</strong></td>
<td align="left"><pre><code>   Filesystem      Size  Used Avail Use% Mounted on
   /dev/vda1       9.9G  896M  8.5G  10% /
   /dev/vdb         20G  173M   19G   1% /mnt</code></pre></td>
</tr>
</tbody>
</table>

* * * * *

## <span>3. Refactored infrastructure</span>

### <span>3.1. Type of deployment</span>

The objective is to enforce testing prior to applying it to the production environment.

Although the production environment has fixed resources, the Staging/testing environment can be built on demand with flexible amount of IP/VMs to ensure the developed configuration works prior to apply it to production.

#### <span>Production</span>

Production environment is very important and it must be fully tested in Staging/Testing before make them available to the user.

#### <span>Staging/testing</span>

The objective of this server environment is to reproduce an isolated version of the production environment.

Therefore, the idea is to have the capability of a fully working and isolated environment version for short and temporary period for development and/or testing purposes.

It is estimated that during a period of time, we might have 2 distinct deployments running for testing and acceptance testing prior to be applied in production.

### <span>3.2. Refactor overview</span>

-   Linux release: Ubuntu 12.04 LTS is planned to be used on ALL instances;
-   Some other ideas to improve the infrastructure are described in [WPD:Infrastructure/priorities](/WPD:Infrastructure/priorities), although relevant to the project, they are considered out of scope of the present document;
-   In addition to the ideas described in the wiki, some other changes are described considered key to this refactor and has an issue number to work on:
    -   [\#INFR-39](http://project.webplatform.org/infrastructure/issues/INFR-39)
    -   [\#INFR-40](http://project.webplatform.org/infrastructure/issues/INFR-40)
    -   [\#INFR-41](http://project.webplatform.org/infrastructure/issues/INFR-41)

#### <span>3.2.1. Operating System version discrepancy to solve</span>

The objective is to migrate the Operating System version to current Ubuntu LTS version. In the meantime, two LTS versions will be supported.

#### <span>3.2.2. Misc. tasks</span>

Some tasks might improve the overall performance of the system, they should be analyzed and reported into [the issue tracker](http://project.webplatform.org/infrastructure/issues)

**High gain, low ETA**

-   Install Logstash and ensure ALL services reports logs to it (install on [\#3.3.2.1. Deployment](#3.3.2.1._Deployment)?)
-   VHost configuration (both NGINX than Apache)
    -   Default vhost (e.g. via the IP) to serve a static file
    -   Each vhost only allows http communication to known hosts (i.e. fastly, aremysiteup, monitoring, etc)
    -   Clean up the hosts with only the minimal web applications deployed with their vhosts
-   Use/configure fastly monitoring (I need to read about what we can get out of it)
-   Use fastly 50x error pages with static
-   Hide to a maximum server version in vhosts/php configuration

**Lower priority but important**

-   Install StartSSL certificate
    -   Ensure login forms uses the SSL VHost
    -   Ensure all services with login has a SSL VHost
-   Use secondary partition for manifest storage mount as XFS for quick snapshots
-   Ensure tracking code is installed through salt stack, and not manually (!)

#### <span>3.2.3. To be analyzed</span>

-   Analyse whether we can MySQL server version (possible, would break things?)
    -   See [\#3.3.2.2. Database](#3.3.2.2._Database) notes
-   DHCP server (install on [\#3.3.2.1. Deployment](#3.3.2.1._Deployment)?)
-   DNS server (install on [\#3.3.2.1. Deployment](#3.3.2.1._Deployment)?)
-   Elastic search
    -   client on which node?
    -   server on which node?
-   Benchmarking tools
    -   Database
    -   Memcached with libmemcached-tools (see [docs](http://docs.libmemcached.org/))
    -   HTTP server benchmarking tools
    -   Mailing testing utilities
-   Mailing relay exit node

### <span>3.3. Instance flavors</span>

The architecture of the solution is going to be re-evaluated, as there are also other instances that do not need to be exactly the same.

#### <span>3.3.1. Application servers</span>

An app server should have deployed one or more web application virtual host. This should not be impacted by whether application A is also present with application B on the same node. It is a current issue, which causes some false-positive errors in the logs and creates unneeded noise.

<dl>
<dd>
**Provisioning:**

1.  7 Public IP addresses
2.  8 VMs

</dd>
</dl>
<dl>
<dd>
**Application profile distribution proposal:**

</dd>
<dd>
</dd>
<dd>
*Profile “A”*

-   qty: 5
-   using:
    -   WordPress
    -   MediaWiki
    -   BugGenie

</dd>
<dd>
</dd>
<dd>
*Profile “B”*

-   qty: 1
-   using:
    -   Gerrit
    -   Talk
    -   Monitor

</dd>
<dd>
</dd>
<dd>
*Profile “C”*

-   qty: 2
-   using:
    -   Piwik
    -   Dabblet

</dd>
</dl>
<dl>
<dd>
**To analyze:**

-   Not all node types requires a public IP address, nodes like Ganglia, Bug genie, and Piwik could be behind a single NGINX proxy server as it is likely to be less used than a typical MediaWiki/WordPress;
-   See to support both NGINX AND Apache2 as HTTP server for all web applications;:\* Block storage/NFS mount point for same data across instances;
-   Find pro and cons regarding multiple web application server sharing the same storage service (e.g. NFS cluster) spanning across multiple instances. What is recommended, how is it failure resilient?
-   Nice to have: KVM-like console access (in case of firewall problem, or hard failure);

</dd>
<dd>
</dd>
<dd>
**Profiles:**

-   **WordPress**
    -   Software: WordPress, in PHP
    -   virtual host name: blog.webplatform.org
-   **MediaWiki**
    -   Software: MediaWiki, in PHP
    -   virtual host name: docs.webplatform.org
-   **Ganglia frontend**
    -   Software: Ganglia web frontend
    -   virtual host name: monitor.webplatform.org
-   **Piwik**
    -   Software: Piwik, in PHP
    -   virtual host name: stats.webplatform.org
-   **Talk**
    -   Software: [Question2Answer](http://www.question2answer.org/)
    -   virtual host name: talk.webplatform.org
-   **Bug genie**
    -   Software: [Bug Genie](http://www.thebuggenie.com/)
    -   virtual host name: project.webplatform.org
-   **Gerrit**
    *Note:* Although there is an instance in the current state that is called code, it is NOT for Gerrit, but for Dabblet.
    -   Software: [Gerrit](https://code.google.com/p/gerrit/)
    -   virtual host name: TBD
-   **Dabblet**
    -   Software: [Dabblet](https://github.com/LeaVerou/dabblet)
    -   virtual host name: code.webplatform.org

</dd>
</dl>

#### <span>3.3.2. Infrastructure servers</span>

<dl>
<dd>
**Provisioning:**

</dd>
<dd>
</dd>
<dd>
The following is a sum of the described profiles below.

</dd>
<dd>
1.  2 Public IP addresses
2.  database node (DB hot backup)
3.  deployment node
4.  5-11 VMs

</dd>
</dl>

##### <span>3.3.2.1. Deployment</span>

The objective of this instance is to be the only machine to connect to. Not only should it manage Nova and Salt stack commands, but also assist in other various tasks.

Assuming multi-site hosting system is built, we will use [Salt Stack’s ‘Syndic’ feature](http://docs.saltstack.com/ref/cli/salt-syndic.html) to pass along from the central master (to be yet determined).

<dl>
<dd>
**Provisioning:**

-   1 VM
-   This node does not need direct access to a large amount of CPU/RAM/HD, as it is used solely for receiving/sending data from other members of the local network.

</dd>
</dl>
<dl>
<dd>
**Requirements:**

1.  Block storage, or mount-point (NFS?) for state manifests and user data
2.  Use secondary partition for manifest storage mount as XFS for quick snapshots
3.  Nice to have: KVM-like access

</dd>
</dl>

##### <span>3.3.2.2. Database</span>

The current setup of 2 is estimated to be enough for our needs; however, it is also happens to be a bottleneck in some situations, as we only have 1 read-write AND 1 read-only machines (2 total).

The most of the current application stack do not necessarily have drop-in caching mechanism. We should analyze in depth whether we can detect the ‘too many connections’ problem, and its usage.

<dl>
<dd>
**Provisioning:**

-   2-4 VMs
-   1 Public IP address
-   Preferred to have significant amount of vCPU/vRAM

</dd>
<dd>
</dd>
<dd>
**To be analyzed:**

-   We should have one name, but multiple A entries, of write(able) database servers for round-robin.
-   or maybe is broken, something yet to evaluate.
-   Create hot backup replication to shelter site (on W3C infra)
-   Database connector proxy (see [mysql-proxy](http://dev.mysql.com/doc/refman/5.6/en/mysql-proxy.html))
-   Upgrade MySQL version and/or see for alternate (compatible) distribution: Percona, MariaDB

</dd>
<dd>
</dd>
<dd>
**Requirements:**

1.  Make secondary drive as XFS, and to configure MySQL/etc database storage so we can make ‘snapshots’
2.  Block storage, or mount-point (NFS?);
3.  Use secondary partition for database data as XFS for snapshots

</dd>
</dl>

##### <span>3.3.2.3. Memcache</span>

<dl>
<dd>
**Provisioning:**

-   1-2 VMs
-   Should have good amount of vCPU/vRAM (add number)

</dd>
<dd>
</dd>
<dd>
**To be analyzed:**

-   If we get memcached with other similar technologies, we can create a cluster of services (e.g. memcached, elastic search, redis).

</dd>
</dl>

##### <span>3.3.2.4. Storage</span>

<dl>
<dd>
**Provisioning:**

-   1-2 VMs
-   Should have a good amount of storage capacity, and leverage XFS’s snapshot feature.

</dd>
<dd>
</dd>
<dd>
**To be analyzed:**

-   If we have block storage service, this node should only handle data transfers to the block storage service by creating a local copy, then copy it over.
-   This node might change its purpose and be replaced by a rsync orchestration system to move files around, e.g.:
-   Making a local copy, then creating incremental backups on block storage service
-   Updating CDN static files

</dd>
</dl>

#### <span>3.3.3. Process servers</span>

Similar to the Web application profile, a node providing a process service should be installable to any server without impacting or breaking other managed services.

Although the refactor will make sure the two profiles are independent and applicable anywhere in the infrastructure, it is considered to merge the two profiles on the same Instance.

<dl>
<dd>
**Provisioning:**

1.  1-2 VMs
2.  Lower vHD is acceptable

</dd>
<dd>
</dd>
<dd>
**Profiles:**

-   Backup
    *Note:* This configuration might change as we have block storage and we might use storage as handlers to move backup around.
-   IRC Bot

</dd>
</dl>

* * * * *

## <span>4. Service provider infrastructure</span>

Although it might be impossible to the provider offer a fully featured Open Stack environment with Public facing web dashboard, we would appreciate to have access to bare-metal machines to your capabilities with the latest stable OpenStack version (Folsom, Grizzly).

Our usage level does not require access to a web front end, nor a web control panel. Our infrastructure has already systems configured to communicate to OpenStack using the ‘nova’ utility.

### <span>4.1. Questions</span>

Some details to clarify about what may be available within our upcoming provider infrastructure.

Is there a local...?

-   Ubuntu/Debian repository mirror
-   NTP server
-   SMTP relay or exit relays
-   Do you provide/have recommendations regarding VPN deployment for cross-site replication and security?
