= 2013 - Migrating to a new cloud provider =

== Introduction ==
This document follows [[WPD:Infrastructure/analysis/2013-Usage and future state]] and should help with the [[WPD:Infrastructure/analysis/2013-Usage and future state#3. Refactored infrastructure]] objectives.

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

__TOC__

== Phases ==
Broken down into phases...

=== Analysis document (this document) ===
In progress...


----
=== Rework hard-coded configurations ===

What must be ready prior to change phase:
# test in a separate environment the configuration management scripts
# create two new environments in new cloud provider (test, production)
# code a synchronization script (files, replace database) to make final migration flip be as quick as possible
# test whether we can send play log to new production db server deployment


----
=== Replicating installation outside of current cloud provider ===
stub.

What must be ready prior to change phase:
# Database servers has working hot-backup from production
# Deployment works fully without Fastly (i.e. by changing a tester's hosts file everything works)


----
=== Replicating installation to new cloud provider ===
Assuming we can replicate in more than one environment (locally, on WikiMediaFoundation cloud, new cloud)

stub.

What must be ready prior to change phase:
# Complete new Fastly configuration mirroring current production
# Complete deployment to the new cloud provider
# Database servers has hot backup in both locations


----
=== Testing ===
Assuming we have a 
This step will allow us to test the full site without using any of the current production allowing us to test-proof the new deployment prior to the sign-off.


----
=== Flipping the switch ===
Assuming we have a sign-off from previous phase.

This step is leveraging the fact that Fastly configuration can be changed quickly. This will ensure us that in case of a problem, we can easily revert and therefore ease the pressure during the actual change.