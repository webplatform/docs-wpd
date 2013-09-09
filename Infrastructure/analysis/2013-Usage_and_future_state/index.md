= 2013 WebPlatform Docs infrastructure usage and future state =

== Introduction ==

[http://webplatform.org/ WebPlatform Docs] is now close to a year old. The goal of this document is to describe the current health of the system and how we can make it better.

As [http://blog.webplatform.org/2012/10/building-web-platforms-infrastructure/ Ryan described in the launch post], we can see a year later that the structure is handling the load fairly well.

But as with anything, we also learned that we have to improve the system to make it more stable. Since the last year was mostly focussing on the content than the infrastructure, things at some spots were left behind and the system is in a need of a good maintenance.

This is why [http://blog.webplatform.org/2013/08/hi-my-name-s-renoir-ill-be-your-devops-for-the-web-platform/ ''Renoir'' has been hired]: To maintain the system and contribute to the site success, full time.

This document describes in depth the usage, statistics of the current infrastructure, and what is to come with it.



----



== 1. Executive Summary ==

=== 1.1. Usage comparison table ===

{| class="mw-datatable os-suggest-results filehistory"
|+VMs usage comparsion
|-
|
|Current
|Future
|-
|'''Application services'''
|production:
* app: 5
* monitor:1
* piwik: 2
* project: 1
* code:1
|production:
* 8
temporary * :
* 3
|-
|'''Infrastructure services'''
|''production'':
* deployment: 1
* db: 2
* memcache: 2
* storage: 2
|''production'':
* 5-9
''temporary *'':
* 5
|-
|'''Process services'''
|''production'':
* backup: 1
* bots: 1
|''production'':
* 1-2
''temporary *'':
* 1
|-
|'''Sub-total'''
|''production'':
* 19 VMs
|''production'':
* 14-19 VMs
''temporary *'':
* 9
|-
|'''Total'''
| 19 VMs
| 23-28 VMs <br/> ''Including *one only* one "temporary environment" up''
|}

{{Quote box
 |title = Note 4
 |align = none
 |quote  = In Temporary environment, numbers may vary, we might want to always have a temporary environment running for common (non-local) development purposes.
}}
<!--{{clear}}-->

=== 1.2. Some facts about the current environment ===
* Fastly is reporting 3.4 Million requests for the month of August 2013;
* Some VMs are used for development and should be removed or migrated to an isolated environment, see [[#3.1. Type of deployment]];
* No other environment than production (it has to change); The development work made in the production environment and might affect it;
* Everybody with a shared account can do everything with no real control in the privileges;
* 4 VMs has to be Ubuntu 10.04, solely required for the instances described [[#2.2.1.1. MediaWiki, WordPress, Dabblet, Talk]], to be solved in [[#3.2.1. Operating System version discrepancy to solve]].




=== 1.3. Current environment summary ===

The following information summarizes the resources allocation used in the current environment.

See section [[#2. Current environment]] for more details.

* '''Production environment'''
**  25  Public IP addresses; it could be possible to work with 12 static IP addresses for production
**  18  VMs production instances
** 5 http/php (app servers)
** 2 memcached
** 2 mysql/db
** ... misc apps, storage, backup, monitoring, salt master, etc…
**  4  VMs for testing or upcoming projects (not advertised)
* '''Temporary environment'''
** N/A

{{Quote box
 |title = Note 5 ''''Important!''''
 |align = none
 |quote  = The current environment on HPCloud has no isolated “staging”, nor “test” deployment environment (i.e. “Temporary environment”), see [[#3.2. Refactor overview]] for problems it might cause.
}}

<!--{{clear}}-->



=== 1.4. Refactored infrastructure estimation summary ===

The following describes the estimated resources required to build the new infrastructure to be used by September 2014.

See [[#3. Refactored infrastructure]] for more details.

Although the fact that the desired production environment infrastructure could be sufficient by itself, the new infrastructure should support multi-site deployment.

The new infrastructure with support multi-site replication to a secondary site where database and files can be synced from one datacenter to another. Resource allocation for a secondary site has an estimated resource allocation similar to a “Temporary environment” in terms of numbers and will be improving service redundancy.

{{Quote box
 |align = none
 |title = Note 1
 |quote  = The numbers described in the ‘Secondary environment’ section are to be considered in surplus, but it should be possible to use in some during defined period of time.
}}

{{Quote box
 |align = none
 |title = Note 2
 |quote  = We might consider creating an always-running ‘Secondary environment’ for ad-hoc development.
}}
<!--{{clear}}-->

==== Production environment ====

* 9-12 Public IP address;
* 14-19 VMs; <br />Note: some changes described in 3.2. Refactor overview might require to adjust the numbers;

==== Temporary environment ====

* It should be possible to have more than one deployed “temporary” environment at a time (e.g. one for staging, one for test);
* Number is approximate as it might change depending of the feature to be deployed and tested (e.g. We want to test fault tolerance on the DB, we might only need one web application instance, and 5 database servers)
* ~9 Public IP Address;
* ~9 VMs;

==== Secondary environment ====
* Represent a reduced version of the production environment, a secondary site replicating the production;
* Resource allocation is similar to a Temporary environment in terms of IP Addresses and VM quantities.







=== 1.5. Common services ===

Although the current infrastructure includes the services in common enumerated below, the Refactored infrastructure will also include them.

* Salt minion agent
* Ganglia monitor agent
* GlusterFS client (in some cases, subject to change if we have Block storage)
* Rsync xinetd service (rsync key is propagated through Salt)



----




== 2. Current environment ==

=== 2.2. Instance flavors ===

Even though the current infrastructure does not have an explicit categorization scheme, each instance is conceptually separated into the following categories. The new infrastructure will have a similar categorization.

==== 2.2.1. Application services ====

===== 2.2.1.1. MediaWiki, WordPress, Dabblet, Talk =====

A generic profile server should serve only as a redundant HTTP app service. Each application server has a public IP address, but they are not broadcasted publicly in DNS records. Instead, it uses a third-party service (fastly) to balance the load.

{|
|+Node <tt>app[n]</tt>
|-
|'''Linux release:'''
|Ubuntu 11.04 LTS Lucid
|-
|'''Web application profiles:'''
|
* MediaWiki
* Dabblet
* WordPress
* Talk
|-
|'''Services:'''
|
* [[#1.5. Common services]]
* Apache2 w/ mpm-prefork
|-
|'''Specs:'''
|4 vCPU / 8 GB RAM / 240 GB HD
|-
|'''Load average:'''
|
* 0.20, 0.14, 0.10
* 0.13, 0.12, 0.14
* 0.20, 0.17, 0.14
* 0.24, 0.66, 0.42
* 0.49, 0.42, 0.39
|-
|'''Disk usage:'''
|
  app3:
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
|}



===== 2.2.1.2. Monitor =====

This instance provides a web frontend to ganglia reports, and publish them publicly.

{|
|+Node <tt>monitor</tt>
|-
|'''Linux release:'''
|Ubuntu 12.04.2 LTS Precise
|-
|'''Web application profiles:'''
|
* Ganglia frontend
|-
|'''Services:'''
|
* Ganglia server
* [[#1.5. Common services]]
|-
|'''Specs:'''
|2 vCPU / 2 GB RAM / 60 GB HD
|-
|'''Load average:'''
|0.40, 0.42, 0.45
|-
|'''Disk usage:'''
|
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  1.5G  7.9G  16% /
    /dev/vdb         50G  180M   47G   1% /mnt
|}




===== 2.2.1.3. Piwik =====

This instance provides piwik dashboard web front-end and tracking beacon.


{|
|+Node <tt>piwik[n]</tt>
|-
|'''Linux release:'''
|Ubuntu 12.04.1 LTS
|-
|'''Number of nodes:'''
|2
|-
|'''Web application profiles:'''
|
* Piwik
|-
|'''Services:'''
|
* Apache2 w/ mpm-prefork
* [[#1.5. Common services]]
|-
|'''Specs:'''
|4 vCPU / 8 GB RAM / 240 GB HD
|-
|'''Load average:'''
|
* 0.00, 0.01, 0.05
* 0.00, 0.01, 0.05
|-
|'''Disk usage:'''
|
  piwik1:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  1.3G  8.2G  13% /
    /dev/vdb        227G  188M  215G   1% /mnt
  piwik0:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  1.3G  8.1G  14% /
    /dev/vdb        227G  188M  215G   1% /mnt
|}





===== 2.2.1.4. Project =====

This node hosts a dedicated version of Bug Genie, available here.

{|
|+Node <tt>project</tt>
|-
|'''Linux release:'''
|Ubuntu 12.04.1 LTS
|-
|'''Number of nodes:'''
|1
|-
|'''Web application profiles:'''
|
* 
|-
|'''Services:'''
|
* [[#1.5. Common services]]
* Apache2 w/ mpm-prefork
|-
|'''Specs:'''
|2 vCPU / 2 GB RAM / 60 GB HD
|-
|'''Load average:'''
|0.00, 0.01, 0.05
|-
|'''Disk usage:'''
|
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  1.1G  8.3G  12% /
    /dev/vdb         50G  180M   47G   1% /mnt
|}



===== 2.2.1.5. Code =====

This node is not fully working at the moment and it was planned to host code repositories using Gerrit application server.

{|
|+Node <tt>code</tt>
|-
|'''Linux release:'''
|Ubuntu 12.04 LTS
|-
|'''Number of nodes:'''
|1
|-
|'''Web application profiles:'''
|
* Gerrit (unfinished)
|-
|'''Services:'''
|
* [[#1.5. Common services]]
* Java (J2EE container)
|-
|'''Specs:'''
|2 vCPU / 2 GB RAM / 60 GB HD
|-
|'''Load average:'''
|0.03, 0.04, 0.05
|-
|'''Disk usage:'''
|
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  1.1G  8.4G  12% /
    /dev/vdb         50G  180M   47G   1% /mnt
|}





==== 2.2.2. Infrastructure services ====

===== 2.2.2.1. Deployment =====

This node is the central point of access, it manages the local datacenter. From it, is possible to apply configuration settings through a remote execution and configuration management system called Salt Stack.

'''From this instance, it is aggregating:'''
* Log files
* State change execution

{|
|+Node <tt>deployment</tt>
|-
|'''Linux release:'''
|Ubuntu 12.04 LTS Precise
|-
|'''Number of nodes:'''
|1
|-
|'''Web application profiles:'''
|
* N/A
|-
|'''Services:'''
|
* [[#1.5. Common services]]
* Salt stack master
|-
|'''Specs:'''
|2 vCPU / 2 GB RAM / 60 GB HD
|-
|'''Load average:'''
|0.38 0.31 0.26
|-
|'''Disk usage:'''
|
  Filesystem   Size  Used Avail  Use% Mounted on
  /dev/vda1    9.9G  4.6G  4.8G  50%  /
  /dev/vdb      50G   17G   31G  36%  /mnt
|}





===== 2.2.2.2. Database =====

This node type is a database cluster. The current setup has a master and a read-only node.

'''Instance goals:'''
* Provide database access
* Manage various database systems (e.g. MySQL)

{|
|+Node <tt>db[n]</tt>
|-
|'''Linux release:'''
|Ubuntu 10.04.3 LTS Lucid
|-
|'''Number of nodes:'''
|2
|-
|'''Web application profiles:'''
|
* N/A
|-
|'''Services:'''
|
* [[#1.5. Common services]]
* MySQL server (5.1.x), an old version, upgrade? (see [[#3.3.2.2. Database]] notes)
|-
|'''Specs:'''
|4 vCPU / 16 GB RAM / 480 GB HD
|-
|'''Load average:'''
|
* 0.13, 0.07, 0.02
* 0.32, 0.27, 0.20
|-
|'''Disk usage:'''
|
  db1:
    Filesystem   Size  Used Avail  Use% Mounted on
    /dev/vda     9.9G  3.5G  5.9G  38% /
    /dev/vdb     463G  3.1G  437G   1% /mnt
  db2:
    Filesystem   Size  Used Avail Use% Mounted on
    /dev/vda     9.9G  2.7G  6.7G  29% /
    /dev/vdb     463G  3.1G  437G   1% /mnt
|}



===== 2.2.2.1. Memcache =====

Current MediaWiki uses memcache services, but it is not validated whether it is used to its full potential.

{|
|+Node <tt>memcache[n]</tt>
|-
|'''Linux release:'''
|Ubuntu 12.04.2 LTS Precise
|-
|'''Number of nodes:'''
|2
|-
|'''Web application profiles:'''
|
* N/A
|-
|'''Services:'''
|
* [[#1.5. Common services]]
* Memcached
|-
|'''Specs:'''
|2 vCPU / 4 GB RAM / 120 GB HD
|-
|'''Load average:'''
|
* 0.00, 0.01, 0.05
* 0.01, 0.03, 0.05
|-
|'''Disk usage:'''
|
  memcache1:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G 1017M  8.4G  11% /
    /dev/vdb        109G  188M  103G   1% /mnt
  memcache2:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G 1017M  8.4G  11% /
    /dev/vdb        109G  188M  103G   1% /mnt
|}



===== 2.2.2.1. Storage =====

Currently, the storage is using GlusterFS as the system and many instances are using it as well.

Usage:
* Images volume mountpoint
* App specific user uploads storage

{|
|+Node <tt>storage[n]</tt>
|-
|'''Linux release:'''
|Ubuntu 12.04.2 LTS Precise
|-
|'''Number of nodes:'''
|2
|-
|'''Web application profiles:'''
|
* 
|-
|'''Services:'''
|
* [[#1.5. Common services]]
* GlusterFS server
|-
|'''Specs:'''
|2 vCPU / 2 GB RAM / 60 GB HD
|-
|'''Load average:'''
|
* 0.04, 0.03, 0.05
* 0.04, 0.04, 0.05
|-
|'''Disk usage:'''
|
  storage3:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  2.5G  6.9G  27% /
    /dev/vdb         50G  466M   47G   1% /mnt
    /dev/vdc         50G  832M   50G   2% /srv/storage
  storage5:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  2.5G  6.9G  27% /
    /dev/vdb         50G  180M   47G   1% /mnt
    /dev/vdc         50G  492M   50G   1% /srv/storage
|}



==== 2.2.3. Process services ====

===== 2.2.3.1. Backup =====

{|
|+Node <tt>backup</tt>
|-
|'''Linux release:'''
|Ubuntu 12.04 LTS
|-
|'''Number of nodes:'''
|1
|-
|'''Web application profiles:'''
|
* 
|-
|'''Services:'''
|
* [[#1.5. Common services]]
|-
|'''Specs:'''
|2 vCPU / 2 GB RAM / 60 GB HD
|-
|'''Load average:'''
|0.00, 0.01, 0.05
|-
|'''Disk usage:'''
|
  Filesystem                     Size  Used Avail Use% Mounted on
  /dev/vda1                      9.9G  887M  8.5G  10% /
  /dev/vdb                        50G   50G     0 100% /mnt
  /dev/mapper/backup1-lvbackup1   40G   40G  122M 100% /mnt/backup
|}


===== 2.2.3.2. Bots =====

This node is hosting a Python program called ‘Lumberjack’ that is acting as a IRC bot logging chat events on some channels.

{|
|+Node <tt>bots</tt>
|-
|'''Linux release:'''
|Ubuntu 12.04 LTS
|-
|'''Number of nodes:'''
|1
|-
|'''Web application profiles:'''
|
* 
|-
|'''Services:'''
|
* [[#1.5. Common services]]
* Lumberjack python process
|-
|'''Specs:'''
|1 vCPU / 1 GB RAM / 30 GB HD
|-
|'''Load average:'''
|0.18, 0.17, 0.21
|-
|'''Disk usage:'''
|
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  896M  8.5G  10% /
    /dev/vdb         20G  173M   19G   1% /mnt
|}



----



== 3. Refactored infrastructure ==

=== 3.1. Type of deployment ===

The objective is to enforce testing prior to applying it to the production environment.

Although the production environment has fixed resources, the Staging/testing environment can be built on demand with flexible amount of IP/VMs to ensure the developed configuration works prior to apply it to production.


==== Production ====

Production environment is very important and it must be fully tested in Staging/Testing before make them available to the user.


==== Staging/testing ====

The objective of this server environment is to reproduce an isolated version of the production environment.

Therefore,  the idea is to have the capability of a fully working and isolated environment version for short and temporary period for development and/or testing purposes.

It is estimated that during a period of time, we might have 2 distinct deployments running for testing and acceptance testing prior to be applied in production.




=== 3.2. Refactor overview ===

* Linux release: Ubuntu 12.04 LTS is planned to be used on ALL instances;
* Some other ideas to improve the infrastructure are described in [[WPD:Infrastructure/priorities]], although relevant to the project, they are considered out of scope of the present document;
* In addition to the ideas described in the wiki, some other changes are described considered key to this refactor and has an issue number to work on:
** [http://project.webplatform.org/infrastructure/issues/INFR-39 #INFR-39]
** [http://project.webplatform.org/infrastructure/issues/INFR-40 #INFR-40]
** [http://project.webplatform.org/infrastructure/issues/INFR-41 #INFR-41]



==== 3.2.1. Operating System version discrepancy to solve ====

The objective is to migrate the Operating System version to current Ubuntu LTS version. In the meantime, two LTS versions will be supported.




==== 3.2.2. Misc. tasks ====

Some tasks might improve the overall performance of the system, they should be analyzed and reported into [http://project.webplatform.org/infrastructure/issues the issue tracker]

'''High gain, low ETA'''
* Install Logstash and ensure ALL services reports logs to it (install on [[#3.3.2.1. Deployment]]?)
* VHost configuration (both NGINX than Apache)
** Default vhost (e.g. via the IP) to serve a static file
** Each vhost only allows http communication to known hosts (i.e. fastly, aremysiteup, monitoring, etc)
** Clean up the hosts with only the minimal web applications deployed with their vhosts
* Use/configure fastly monitoring (I need to read about what we can get out of it)
* Use fastly 50x error pages with static  
* Hide to a maximum server version in vhosts/php configuration

'''Lower priority but important'''
* Install StartSSL certificate 
** Ensure login forms uses the SSL VHost
** Ensure all services with login has a SSL VHost
* Use secondary partition for manifest storage mount as XFS for quick snapshots
* Ensure tracking code is installed through salt stack, and not manually (!)


==== 3.2.3. To be analyzed ====

* Analyse whether we can MySQL server version (possible, would break things?)
** See [[#3.3.2.2. Database]] notes
* DHCP server (install on [[#3.3.2.1. Deployment]]?)
* DNS server (install on [[#3.3.2.1. Deployment]]?)
* Elastic search 
** client on which node? 
** server on which node?
* Benchmarking tools
** Database
** Memcached with libmemcached-tools (see [http://docs.libmemcached.org/ docs])
** HTTP server benchmarking tools
** Mailing testing utilities
* Mailing relay exit node


=== 3.3. Instance flavors ===

The architecture of the solution is going to be re-evaluated, as there are also other instances that do not need to be exactly the same.




==== 3.3.1. Application servers ====

An app server should have deployed one or more web application virtual host. This should not be impacted by whether application A is also present with application B on the same node. It is a current issue, which causes some false-positive errors in the logs and creates unneeded noise.


:'''Provisioning:'''
:# 7  Public IP addresses
:# 8  VMs

:'''Application profile distribution proposal:'''
:
:''Profile “A”''
:* qty: 5
:* using:
:** WordPress
:** MediaWiki
:** BugGenie
:
:''Profile “B”''
:* qty: 1
:* using:
:** Gerrit
:** Talk
:** Monitor
:
:''Profile “C”''
:* qty: 2
:* using:
:** Piwik
:** Dabblet

:'''To analyze:'''
:* Not all node types requires a public IP address, nodes like Ganglia, Bug genie, and Piwik could be behind a single NGINX proxy server as it is likely to be less used than a typical MediaWiki/WordPress;
:* See to support both NGINX AND Apache2 as HTTP server for all web applications;:* Block storage/NFS mount point for same data across instances;
:* Find pro and cons regarding multiple web application server sharing the same storage service (e.g. NFS cluster) spanning across multiple instances. What is recommended, how is it failure resilient?
:* Nice to have: KVM-like console access (in case of firewall problem, or hard failure);
:
:'''Profiles:'''
:* '''WordPress'''
:** Software: WordPress, in PHP
:** virtual host name: blog.webplatform.org
:* '''MediaWiki'''
:** Software: MediaWiki, in PHP
:** virtual host name: docs.webplatform.org
:* '''Ganglia frontend'''
:** Software: Ganglia web frontend
:** virtual host name: monitor.webplatform.org
:* '''Piwik'''
:** Software: Piwik, in PHP
:** virtual host name: stats.webplatform.org
:* '''Talk'''
:** Software: [http://www.question2answer.org/ Question2Answer]
:** virtual host name: talk.webplatform.org
:* '''Bug genie'''
:** Software: [http://www.thebuggenie.com/ Bug Genie]
:** virtual host name: project.webplatform.org
:* '''Gerrit''' <br />''Note:'' Although there is an instance in the current state that is called code, it is NOT for Gerrit, but for Dabblet.
:** Software: [https://code.google.com/p/gerrit/ Gerrit]
:** virtual host name: TBD
:* '''Dabblet'''
:** Software: [https://github.com/LeaVerou/dabblet Dabblet]
:** virtual host name: code.webplatform.org




==== 3.3.2. Infrastructure servers ====

:'''Provisioning:'''
:
:The following is a sum of the described profiles below.
:
:# 2  Public IP addresses
:# database node (DB hot backup)
:# deployment node
:# 5-11  VMs




===== 3.3.2.1. Deployment =====

The objective of this instance is to be the only machine to connect to. Not only should it manage Nova and Salt stack commands, but also assist in other various tasks.

Assuming multi-site hosting system is built, we will use [http://docs.saltstack.com/ref/cli/salt-syndic.html Salt Stack’s ‘Syndic’ feature] to pass along from the central master (to be yet determined).


:'''Provisioning:'''
:* 1 VM
:* This node does not need direct access to a large amount of CPU/RAM/HD, as it is used solely for receiving/sending data from other members of the local network.

:'''Requirements:'''
:# Block storage, or mount-point (NFS?) for state manifests and user data
:# Use secondary partition for manifest storage mount as XFS for quick snapshots
:# Nice to have: KVM-like access




===== 3.3.2.2. Database =====

The current setup of 2 is estimated to be enough for our needs; however, it is also happens to be a  bottleneck in some situations, as we only have 1 read-write AND 1 read-only machines (2 total).

The most of the current application stack do not necessarily have drop-in caching mechanism. We should analyze in depth whether we can detect the ‘too many connections’ problem, and its usage.


:'''Provisioning:'''
:* 2-4 VMs
:* 1 Public IP address
:* Preferred to have significant amount of vCPU/vRAM
:
:'''To be analyzed:'''
:* We should have one name, but multiple A entries, of write(able) database servers for round-robin.
:* or maybe is broken, something yet to evaluate.
:* Create hot backup replication to shelter site (on W3C infra)
:* Database connector proxy (see [http://dev.mysql.com/doc/refman/5.6/en/mysql-proxy.html mysql-proxy])
:* Upgrade MySQL version and/or see for alternate (compatible) distribution: Percona, MariaDB
:
:'''Requirements:'''
:# Make secondary drive as XFS, and to configure MySQL/etc database storage so we can make ‘snapshots’
:# Block storage, or mount-point (NFS?);
:# Use secondary partition for database data as XFS for snapshots




===== 3.3.2.3. Memcache =====

:'''Provisioning:'''
:* 1-2 VMs
:* Should have good amount of vCPU/vRAM (add number)
:
:'''To be analyzed:'''
:* If we get memcached with other similar technologies, we can create a cluster of services (e.g. memcached, elastic search, redis).




===== 3.3.2.4. Storage =====

:'''Provisioning:'''
:* 1-2 VMs
:* Should have a good amount of storage capacity, and leverage XFS’s snapshot feature.
:
:'''To be analyzed:'''
:* If we have block storage service, this node should only handle data transfers to the block storage service by creating a local copy, then copy it over.
:* This node might change its purpose and be replaced by a rsync orchestration system to move files around, e.g.:
:* Making a local copy, then creating incremental backups on block storage service
:* Updating CDN static files




==== 3.3.3. Process servers ====

Similar to the Web application profile, a node providing a process service should be installable to any server without impacting or breaking other managed services.

Although the refactor will make sure the two profiles are independent and applicable anywhere in the infrastructure, it is considered to merge the two profiles on the same Instance.


:'''Provisioning:'''
:# 1-2  VMs
:# Lower vHD is acceptable
:
:'''Profiles:'''
:* Backup <br \>''Note:'' This configuration might change as we have block storage and we might use storage as handlers to move backup around.
:* IRC Bot




----




== 4. Service provider infrastructure ==

Although it might be impossible to the provider offer a fully featured Open Stack environment with Public facing web dashboard, we would appreciate to have access to bare-metal machines to your capabilities with the latest stable OpenStack version (Folsom, Grizzly).

Our usage level does not require access to a web front end, nor a web control panel. Our infrastructure has already systems configured to communicate to OpenStack using the ‘nova’ utility.




=== 4.1. Questions ===

Some details to clarify about what may be available within our upcoming provider infrastructure.

Is there a local...?

* Ubuntu/Debian repository mirror
* NTP server
* SMTP relay or exit relays
* Do you provide/have recommendations regarding VPN deployment for cross-site replication and security?