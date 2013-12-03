= Hardware and software requirements =

Summarizing server requirements described in length in [[WPD:Infrastructure/analysis/2013-Usage and future state]].

== Summary ==

We are using OpenStack hosted Virtual Machines as our main computing environment. Our stack is built using Salt Stack to manage instance states and various aspects of OpenStack. Salt is similar to Puppet by managing machine states, but it also enables remote execution and handles various OpenStack services. 

We require many servers to host our services (memcache, MySQL, NGINX, Apache, etc). HTTP requests to these servers are managed by our caching layer, which is provided by Fastly; this provides a separate CDN service and improves site performance. In the future, we plan to improve site performance, implement ''continuous deployment'' and use OpenStack's Object/Block services.

In terms of hosting and server infrastructure, we want to have more than one hosting provider, to enable redundancy and multiple site replication, and to showcase the power of OpenStack. In the short term, we need only a single major host.

== Requirements ==

=== General ===
* Open Stack service environment
* Object storage service (Swift/Ceph or similar; not in use, but planned)
* Block storage (Cinder or similar, not in use but planned)

=== Production environment ===
These are our minimum requirements for the live site:

* 8x 2 vCPU, 8Gb vRAM (MediaWiki server, slave DB server)
* 1x 4 vCPU, 16Gb vRAM (DB server)
* 4x 2 vCPU, 4Gb vRAM
* 3x 1 vCPU, 2Gb vRAM
* 7x are Ubuntu 10.04 LTS, rest are Ubuntu 12.04 LTS
* 7 IPv4 Public IP addresses

=== Staging and testing environments ===
In addition to the production environment, we want to have a testing and staging deployment running full time.

These environments have the same requirements as the production environment,  deployed in a separate network, but do not need guaranteed uptime.

== Future Requirements ==
* Our server setup is using Gluster FS and we are considering switching to use OpenStack's Swift/Ceph to store our static assets.
* Most of our VM are under Ubuntu 10.04 LTS and 12.04 LTS, and we are considering moving toward Debian stable
* MySQL cluster to be upgraded
* Log management analysis tool to help us audit system symptoms
* We want to leveraging [http://en.wikipedia.org/wiki/Edge_Side_Includes ESI] ("Edge Side Include") for some aspects of the site content.