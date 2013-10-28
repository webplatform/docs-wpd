= 2013 - Migrating to a new cloud provider =

== Introduction ==
While we were running on original deployment infrastructure, configuration was built empirically to suit the site visitors demand. Due to the fact that most configuration was written to be specific to the current environment, we need to review all configurations allowing us to change provider and to rebuild on demand a new deployment without impacting the production environment.

The objective of this project is to migrate out of our cloud provider but to make such migration, there are some configuration changes to make.

In consequence, the new configuration should enable us:
# to rebuild the complete infrastructure anywhere (even locally).
# to use services in other cloud (e.g. Database hot backup in an other provider location) 

=== Benefits ===
All environments (production, staging, testing, dev) are going to be completely independent, not even in the same cloud provider.

It will give the following benefits:
* capacity to test all the stack without impacting the live (production) site.
* capacity to create your own development environment wherever we can instantiate virtual machines
* capacity to build an ad-hoc clone of the production environment to develop with

== Phases ==
{{TOC limit|3}}



=== Analysis document (this document) ===
In progress...


=== Rework hard-coded configurations ===

What must be ready prior to change phase:
# test in a separate environment the configuration management scripts
# create two new environments in new cloud provider (test, production)
# code a synchronization script (files, replace database) to make final migration flip be as quick as possible
# test whether we can send play log to new production db server deployment


=== Replicating installation outside of current cloud provider ===
stub.

What must be ready prior to change phase:
# Database servers has hot backup in both locations


=== Replicating installation to new cloud provider ===
stub.

What must be ready prior to change phase:
# Complete new Fastly configuration mirroring current production


=== Testing ===
stub.


=== Flipping the switch ===
This step is leveraging the fact that Fastly configuration can be changed quickly. This will ensure us that in case of a problem, we can easily revert and therefore ease the pressure during the actual change.

Regarding the switch-flip period. Since fastly allows us to say which nodes are used as backend, flipping from one to the other can be done in seconds. And, sure, we will have a testing environment.

For example, at the moment I built a test host using fastly at [1]. But it is using the same environment, but using a different set of backend servers than the real is using. It is not complete, but at least filled some testing needs. Something that has to change.