= 2013 WebPlatform Docs infrastructure usage and future state =

== Introduction ==

[http://webplatform.org/ WebPlatform Docs] is now closing to a year of life. The goal of this document is to describe the current health of the system and how we can make it better.

As [http://blog.webplatform.org/2012/10/building-web-platforms-infrastructure/ Ryan described in the lauch post], we can see a year later that the structure is handling fairly well the load. 

But as anything, we also learned that we have to improve the system to make it more stable. Since the last year was mostly focussing on the content than the infrastructure, things at some spots were left behind and made the system in a need for a good maintenance.

This is why [http://blog.webplatform.org/2013/08/hi-my-name-s-renoir-ill-be-your-devops-for-the-web-platform/ ''Renoir'' has been hired]: To make the system stable, and maintain it. 

This document will describe in depth the usage, statistics of the current infrastructure and what is to come about it.


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


''Note'': In Temporary environment, numbers may vary, we might want to always have a temporary environment running for common (non-local) development purposes.


=== 1.2. Some facts about the current environment ===
* Fastly is reporting 3.4 Million requests for the month of August 2013;
* Some VMs are used for development and should be removed or migrated to an isolated environment, see [[#3.1._Type_of_deployment|3.1. Type of deployment]];
* No other environment than production (it has to change); The development work made in the production environment and might affect it;
* Everybody with a shared account can do everything with no real control in the privileges;
* 4 VMs has to be Ubuntu 10.04, solely required for the instances described [[#2.2.1.1._MediaWiki.2C_WordPress.2C_Dabblet.2C_Talk|2.2.1.1. MediaWiki, WordPress, Dabblet, Talk]]
, to be solved in [[#3.2.1._Operating_System_version_discrepancy_to_solve|3.2.1. Operating System version discrepancy to solve]].




=== 1.3. Current environment summary ===
The following information summarizes the resources allocation used in the current environment. 

See section 2. Current environment to get more details.

* '''Production environment'''
**  25  Public IP addresses; it could be possible to work with 12 static IP addresses for production 
**  18  VMs production instances
** 5 http/php (app servers)
** 2 memcached
** 2 mysql/db
** ... misc apps, storage, backup, monitoring, salt master, etc…
**  4  VMs for testing or upcoming projects (not advertized)
* '''Temporary environment'''
** N/A

''Important'': The current environment on HPCloud has no isolated “staging”, nor “test” deployment environment (i.e. “Temporary environment”), see [[#3.2._Refactor_overview|3.2. Refactor overview]] for problems it might cause.




=== 1.4. Refactored infrastructure estimation summary ===

The following describes the estimated resources required to build the new infrastructure to be used by September 2014.

See [[#3._Refactored_infrastructure|3. Refactored infrastructure]] to get more details.

Although the fact that the desired production environment infrastructure could be sufficient by itself, the new infrastructure should support multi-site deployment.

The new infrastructure with support multi-site replication to a secondary site where database and files can be synced from one datacenter to another. Resource allocation for a secondary site has an estimated resource allocation similar to a “Temporary environment” in terms of numbers and will be improving service redundancy.


'''Production environment'''
* 9-12 Public IP address;
* 14-19 VMs; <br />Note: some changes described in 3.2. Refactor overview might require to adjust the numbers;

'''Temporary environment'''
* It should be possible to have more than one deployed “temporary” environment at a time (e.g. one for staging, one for test);
* Number is aproximate as it might change depending of the feature to be deployed and tested (e.g. We want to test fault tolerancy on the DB, we might only need one web application instance, and 5 database servers)
* ~9 Public IP Address;
* ~9 VMs;

'''Secondary environment'''
* Represent a reduced version of the production environment, a secondary site replicating the production;
* Resource allocation is similar to a Temporary environment in terms of IP Addresses and VM quantities.


''Note:'' The numbers described in the ‘Secondary environment’ section are to be considered in surplus, but it should be possible to use in some during defined period of time.

''Note 2:'' We might consider to create a always-running ‘Secondary environment’ for ad-hoc development.




=== 1.5. Common services ===

Although the current infrastructure includes the services in common enumerated below, the Refactored infrastructure will also include them.

* Salt minion agent
* Ganglia monitor agent
* GlusterFS client (in some cases, subject to changement if we have Block storage)
* Rsync xinetd service (rsync key is propagated through Salt)




== 2. Current environment ==

=== 2.2. Instance flavors ===

Even though the current infrastructure do not have an explicit categorization scheme, each instances are conceptually separated in the following categories and the new infrastructure will have a similar categorization.




==== 2.2.1. Application services ====

===== 2.2.1.1. MediaWiki, WordPress, Dabblet, Talk =====

A generic profile server that should serve only as a redundant HTTP app service. Each application server has a public IP address, but they are not broadcasted publicly in DNS records. Instead, it uses a third-party service (fastly) to balance the load.

'''Linux release:''' Ubuntu 11.04 LTS Lucid
'''Node name:''' app[n]
'''Current usage'''
* Number of nodes: 5 (app1, app2, …)
* Web application profiles:
** MediaWiki
** Dabblet
** WordPress
** Talk
* Specs: 
** 4 vCPU / 8 GB RAM / 240 GB HD
* Load average: 
** 0.20, 0.14, 0.10
** 0.13, 0.12, 0.14
** 0.20, 0.17, 0.14
** 0.24, 0.66, 0.42
** 0.49, 0.42, 0.39
* Services:
** 1.5. Common services
** Apache2 w/ mpm-prefork
* Disk usage:
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




===== 2.2.1.2. Monitor =====

This instance provides a web frontend to ganglia reports, and publish them publicly.

Linux release: Ubuntu 12.04.2 LTS Precise
Node name: monitor 
Current usage
* Number of nodes: 1
* Web application profiles
** Ganglia frontend
* Specs: 2 vCPU / 2 GB RAM / 60 GB HD
* Load average: 0.40, 0.42, 0.45
* Services:
** 1.5. Common services
** Ganglia server
* Disk usage:
  monitor:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  1.5G  7.9G  16% /
    /dev/vdb         50G  180M   47G   1% /mnt




===== 2.2.1.3. Piwik =====

This instance provides piwik dashboard web frontend and tracking beacon.

''Note:'' currently disabled.

Linux release: Ubuntu 12.04.1 LTS
Node name: piwik[n]
Current usage
* Number of nodes: 2
* Specs: 4 vCPU / 8 GB RAM / 240 GB HD
* Load average: 
** 0.00, 0.01, 0.05
** 0.00, 0.01, 0.05
* Services:
** 1.5. Common services
** Apache2 w/ mpm-prefork
* Disk usage:
  piwik1:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  1.3G  8.2G  13% /
    /dev/vdb        227G  188M  215G   1% /mnt
  piwik0:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  1.3G  8.1G  14% /
    /dev/vdb        227G  188M  215G   1% /mnt




===== 2.2.1.4. Project =====

This node hosts a dedicated version of Bug Genie, available here.

Linux release: Ubuntu 12.04.1 LTS
Node name: project 
Current usage
* Number of nodes: 1
* Specs: 2 vCPU / 2 GB RAM / 60 GB HD
* Load average: 0.00, 0.01, 0.05
* Current services:
** 1.5. Common services
** Apache2 w/ mpm-prefork
* Disk usage:
  project:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  1.1G  8.3G  12% /
    /dev/vdb         50G  180M   47G   1% /mnt




===== 2.2.1.5. Code =====

This node is not fully working at the moment and it was planned to host code repositories and Gerrit application server.

Linux release: Ubuntu 12.04 LTS
Node name: code 
Current usage
* Number of nodes: 1
* Specs: 2 vCPU / 2 GB RAM / 60 GB HD
* Load average: 0.03, 0.04, 0.05
* Services:
** 1.5. Common services
* Disk usage:
  code:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  1.1G  8.4G  12% /
    /dev/vdb         50G  180M   47G   1% /mnt




==== 2.2.2. Infrastructure services ====

===== 2.2.2.1. Deployment =====

This node is the central point of access, it manages the local datacenter. From it, is possible to apply configuration settings through a remote execution and configuration management system called Salt Stack.

'''From this instance, it is aggregating:'''
* Log files
* State change execution

Linux release: Ubuntu 12.04 LTS Precise
Node name: deployment
Current usage
* Number of nodes: 1
* Specs: 2 vCPU / 2 GB RAM / 60 GB HD
* Load average: 0.38 0.31 0.26
* Services:
** Salt master
** 1.5. Common services
* Disk usage:
  Filesystem   Size  Used Avail  Use% Mounted on
  /dev/vda1    9.9G  4.6G  4.8G  50%  /
  /dev/vdb      50G   17G   31G  36%  /mnt




===== 2.2.2.2. Database =====

This node type is a database cluster. The current setup has a master and a read-only node.

'''Instance goals:'''
* Provide database access
* Manage various database systems (e.g. MySQL)

Linux release: Ubuntu 10.04.3 LTS Lucid
Node name: db[n]
Current usage
* Number of nodes: 2
* Specs: 
* 4 vCPU / 16 GB RAM / 480 GB HD
* Load average:
** 0.13, 0.07, 0.02
** 0.32, 0.27, 0.20
* Services:
** 1.5. Common services
** MySQL server (5.1.62-0ubuntu0.10.04.1)
* Disk usage:
  db1:
    Filesystem   Size  Used Avail  Use% Mounted on
    /dev/vda     9.9G  3.5G  5.9G  38% /
    /dev/vdb     463G  3.1G  437G   1% /mnt
  db2:
    Filesystem   Size  Used Avail Use% Mounted on
    /dev/vda     9.9G  2.7G  6.7G  29% /
    /dev/vdb     463G  3.1G  437G   1% /mnt




===== 2.2.2.1. Memcache =====

Current MediaWiki uses memcache services, but it is not validated whether it is used to its full potential.

Linux release: Ubuntu 12.04.2 LTS Precise
Node name: memcache[n]
Current usage
* Number of nodes: 2 (memcache1, …)
* Specs: 2 vCPU / 4 GB RAM / 120 GB HD
* Load average: 
** 0.00, 0.01, 0.05
** 0.01, 0.03, 0.05
* Services:
** 1.5. Common services
** Memcached
* Disk usage:
  memcache1:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G 1017M  8.4G  11% /
    /dev/vdb        109G  188M  103G   1% /mnt
  memcache2:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G 1017M  8.4G  11% /
    /dev/vdb        109G  188M  103G   1% /mnt




===== 2.2.2.1. Storage =====

Currently, the storage is using GlusterFS as the system and many instances are using it as well.

Linux release: Ubuntu 12.04.2 LTS Precise
Node name: memcache[n] 
Current usage
* Number of nodes: 2 (storage1, …)
* Specs: 2 vCPU / 2 GB RAM / 60 GB HD
* Load average: 
** 0.04, 0.03, 0.05
** 0.04, 0.04, 0.05
* Profiles
* Images volume mountpoint
* App specific user uploads storage
* Services:
** 1.5. Common services
** GlusterFS server
* Disk usage:
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




==== 2.2.3. Process services ====

===== 2.2.3.1. Backup =====

Linux release: Ubuntu 12.04 LTS
Node name: backup 
Current usage
* Number of nodes: 1
* Specs: 2 vCPU / 2 GB RAM / 60 GB HD
* Load average:  0.00, 0.01, 0.05
* Current services:
** 1.5. Common services
* Disk usage:
  Filesystem                     Size  Used Avail Use% Mounted on
  /dev/vda1                      9.9G  887M  8.5G  10% /
  /dev/vdb                        50G   50G     0 100% /mnt
  /dev/mapper/backup1-lvbackup1   40G   40G  122M 100% /mnt/backup




===== 2.2.3.2. Bots =====

This node is hosting a Python program called ‘Lumberjack’ that is acting as a IRC bot logging chat events on some channels.
 
Linux release: Ubuntu 12.04 LTS
Node name: bots 
Current usage
* Number of nodes: 1
* Specs: 1 vCPU / 1 GB RAM / 30 GB HD
* Load average: 0.18, 0.17, 0.21
* Services:
** 1.5. Common services
** Lumberjack python process
* Disk usage:
  bots:
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1       9.9G  896M  8.5G  10% /
    /dev/vdb         20G  173M   19G   1% /mnt 




== 3. Refactored infrastructure ==

=== 3.1. Type of deployment ===

The objective is to enforce testing prior to applying it to the production environment. 

Although the production environment has fixed resources, the Staging/testing environment can be built on demand with flexible amount of IP/VMs to ensure the developed configuration works prior to apply it to production.


==== Production ====

Production environment is very important and it must be fully tested in Staging/Testing before make them available to the user.


==== Staging/testing ====

The objective of this server environment is to reproduce an isolated version of the production environment. 

Therefore,  the idea is to have the capability of a fully working and isolated environment version for short and temporary period for development and/or testing purposes.

It is estimated that during a period of time, we might have 2 distinct deployment running for testing and acceptance testing prior to be applied in production. 




=== 3.2. Refactor overview ===

* Linux release: Ubuntu 12.04 LTS is planned to be used on ALL instances;
* Some other ideas to improve the infrastructure are described in this wiki page, altough relevant to the project, they are considered out of scope of the present document;
* In addition to the ideas described in the wiki, some other changes are described considered key to this refactor and has an issue number to work on:
** http://project.webplatform.org/infrastructure/issues/INFR-39
** http://project.webplatform.org/infrastructure/issues/INFR-40
** http://project.webplatform.org/infrastructure/issues/INFR-41




==== 3.2.1. Operating System version discrepancy to solve ====

The objective is to migrate the Operating System version to current Ubuntu LTS version. In the meantime, two LTS versions will be supported.




=== 3.3. Instance flavors ===

The architecture of the solution is going to be re-evaluated, as there are also other instances that do not need to be exactly the same. 




==== 3.3.1. Application servers ====

An app server should have deployed one or more web application virtual host. This should not be impacted by whether application A is also present with application B on the same node. It is a current issue which causes some false-positive errors in the logs and creates unneeded noise.


'''Provisioning:'''
# 7  Public IP addresses
# 8  VMs

'''Application profile distribution proposal:'''

''Profile “A”''
* qty: 5
* using: 
** WordPress
** MediaWiki
** BugGenie

''Profile “B”''
* qty: 1
* using:
** Gerrit
** Talk
** Monitor

''Profile “C”''
* qty: 2
* using:
** Piwik
** Dabblet


'''To analyze:'''
* Not all node types requires a public IP address, nodes like Ganglia, Bug genie, and Piwik could be behind a single NGINX proxy server as it is likely to be less used than a typical MediaWiki/WordPress;
* See to support both NGINX AND Apache2 as HTTP server for all web applications;
* Use secondary partition for manifest storage mount as XFS for quick snapshots;
* Block storage/NFS mount point for same data across instances;
* Find pro and cons regarding multiple web application server sharing the same storage service (e.g. NFS cluster) spanning on multiple instances. What is recommended, how is it failure resilient?
* Nice to have: KVM-like console access (in case of firewall problem, or hard failure);


'''Profiles:'''
* '''WordPress'''
** Software: WordPress, in PHP
** virtual host name: blog.webplatform.org
* '''MediaWiki'''
** Software: MediaWiki, in PHP
** virtual host name: docs.webplatform.org
* '''Ganglia frontend'''
** Software: Ganglia web frontend
** virtual host name: monitor.webplatform.org
* '''Piwik'''
** Software: Piwik, in PHP
** virtual host name: stats.webplatform.org
* '''Talk'''
** Software: Question2Answer
** virtual host name: talk.webplatform.org
* '''Bug genie'''
** Software: Bug Genie
** virtual host name: project.webplatform.org
* '''Gerrit''' <br />''Note:'' Although there is an instance in the current state that is called code, it is NOT for Gerrit, but for Dabblet.
** Software: Gerrit
** virtual host name: TBD
* '''Dabblet'''
** Software: Dabblet
** virtual host name: code.webplatform.org




==== 3.3.2. Infrastructure servers ====

'''Provisioning:'''

The following is a sum of the described profiles below.
 
# 2  Public IP addresses
# database node (DB hot backup)
# deployment node
# 5-11  VMs




===== 3.3.2.1. Deployment =====

The objective of this instance is to be the only machine to connect to. Not only should it manage Nova and Salt stack commands, but also assist in other various tasks.

Assuming multi-site hosting system is built, we will use Salt Stack’s ‘Syndic’ feature to pass along from the central master (to be yet determined).


'''Provisioning:'''
* 1 VM
* This node do not need direct access to big amount of CPU/RAM/HD as it is used solely to receiving/sending data from other members of the local network.


'''To be analyzed:'''
# Logging aggregation system for both reporting and analysis
# DHCP server
# DNS server
# Logging aggregator client
# Elastic search client
# Database benchmarking tools
# HTTP server benchmarking tools
# Mailing testing utilities
# Mailing relay exit


'''Requirements:'''
# Block storage, or mount-point (NFS?) for state manifests and user data
# Use secondary partition for manifest storage mount as XFS for quick snapshots
# Nice to have: KVM-like access




===== 3.3.2.2. Database =====

The current setup of 2 is estimated to be enough for our needs; however, it is also happens to be a  bottle neck in some situations, as we only have 1 read-write AND 1 read-only machines (2 total). 

The most of the current application stack do not necessarily have drop-in caching mechanism. We should analyze in depth whether we can detect the ‘too many connections’ problem, and analyze its usage.


'''Provisioning:''' 
* 2-4 VMs
* 1 Public IP address
* Prefered to have significant amount of vCPU/vRAM

'''To be analyzed:'''
* we should have one name but multiple A entries of write(able) database servers for round-robin).
* or maybe is broken, something yet to evaluate. 
* Create hot backup replication to shelter site (on W3C infra)
* Database connector proxy (see [http://dev.mysql.com/doc/refman/5.6/en/mysql-proxy.html mysql-proxy])
* Upgrade MySQL version and/or see for alternate (compatible) distribution: Percona, MariaDB

'''Requirements:'''
# Make secondary drive as XFS, and to configure MySQL/etc database storage so we can make ‘snapshots’ 
# Block storage, or mount-point (NFS?);
# Use secondary partition for database data as XFS for snapshots




===== 3.3.2.3. Memcache =====

'''Provisioning:'''
* 1-2 VMs
* Should have good amount of vCPU/vRAM (add number)

'''To be analyzed:'''
* If we get memcached with other similar technologies, we can create a cluster of services (e.g. memcached, elastic search, redis).




===== 3.3.2.4. Storage =====

'''Provisioning:'''
* 1-2 VMs
* Should have a good amount of storage capacity, and leverage XFS’s snapshot feature.

'''To be analyzed:'''
* If we have block storage service, this node should only handle data transfers to the block storage service by creating a local copy, then copy it over.
* This node might change its purpose and be replaced by a rsync orchestration system to move files around, e.g.:
* Making a local copy, then creating incremental backups on block storage service
* Updating CDN static files




==== 3.3.3. Process servers ====

Similar to the Web application profile, a node providing a process service should be installable to any server without impacting or breaking other managed services.

Although the refactor will make sure the two profiles are independent and applicable anywhere in the infrastructure, it is considered to merge the two profiles on the same Instance.


'''Provisioning:'''
# 1-2  VMs
# Lower vHD is acceptable


'''Profiles:'''
* Backup <br \>''Note:'' This configuration might change as we have block storage and we might use storage as a handlers to move backup around.
* IRC Bot




== 4. Service provider infrastructure ==

Although it might be impossible to the provider offer a fully featured Open Stack environment with Public facing web dashboard, we would appreciate to have access to bare-metal machines to your capabilities with the latest stable OpenStack version (Folsom, Grizzly).

Our usage level does not require access to a web frontend, nor a web control pannel. Our infrastructure has already systems configured to communicate to OpenStack using the ‘nova’ utility.




=== 4.1. Questions ===

Some details to clarify about what is available within our upcoming provider infrastructure.

* Is there a local … ?
** Ubuntu/Debian repository mirror
** NTP server
** SMTP relay or exit relays
** Do you provide/have recommendations regarding VPN deployment for cross-site replication and security?