= Hardware and software requirements =

Summarizing server requirements described in length in [[WPD:Infrastructure/analysis/2013-Usage and future state]].

== Summary ==

We are using OpenStack hosted Virtual Machines as our main computing environment. Our stack is built using Salt Stack to manage instance states and various aspects of OpenStack. Salt is similar to Puppet by managing machine states, but it also enables remote execution and handles various OpenStack services. 

While we require many servers to host our services (memcache, MySQL, NGINX, Apache, etc), we are currently using a caching layer provided by Fastly  giving us a separate CDN service and improving performance of the site.

Our planned architecture is to use Fastly/Akamai as a caching layer,  in front of our server infrastructure and to have a pool of resource available by more than one hosting provider. Other changes is about leveraging ESI ("Edge Side Include") techniques, have multiple site replication.

== Upcoming changes ==

* Our server setup is using Gluster FS and we are considering switching to use OpenStack's Swift/Ceph to store our static assets.
* Most of our VM are under Ubuntu 10.04 LTS and 12.04 LTS, and we are considering moving toward Debian stable
* MySQL cluster to be upgraded
* Log management analysis tool to help us audit system symptoms


== Requirements ==

=== General ===
* Open Stack service environment
* Object storage service (Swift/Ceph or similar; not in use, but planned)
* Block storage (Cinder or similar, not in use but planned)

=== Delivery environments ===

Although that we will eventually have a way to create a local workspace to develop and improve various aspects of our stack (server deployment scripts, code, etc) we also want to have two other distinct environments.

It means that we might need in some cases to have the equivalent of the production environment deployed in a separate network to allow us testing a change.

==== Production ====
What is minimally required for the live site.

* 8x 2 vCPU, 8Gb vRAM (MediaWiki server, slave DB server)
* 1x 4 vCPU, 16Gb vRAM (DB server)
* 4x 2 vCPU, 4Gb vRAM
* 3x 1 vCPU, 2Gb vRAM
* 7x are Ubuntu 10.04 LTS, rest are Ubuntu 12.04 LTS
* 7 IPv4 Public IP addresses


==== Staging and testing environment ====

Those environments might not need to be running at all time but for the upcoming year, we might need to have a testing deployment running full time.

* Testing environment
* Staging environment