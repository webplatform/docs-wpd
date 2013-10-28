= 2013 - Migrating to a new cloud provider =

== Introduction ==
While we were running on original deployment infrastructure, configuration was built empirically to suit the site visitors demand. Due to the fact that most configuration was written to be specific to the current environment, we need to review all configurations allowing us to change provider and to rebuild on demand a new deployment without impacting the production environment.

The objective of this project is to migrate out of our cloud provider but to make such migration, there are some configuration changes to make.

In consequence, the new configuration should enable us:
# to rebuild the complete infrastructure anywhere (even locally).
# to use services in other cloud (e.g. Database hot backup in an other provider location) 

=== Benefits ===
Will give us:
* capacity to test all the stack without impacting the live (production) site.
* a way to create your own development environment wherever we can instantiate virtual machines
* a clone of the live to develop on

== Phases ==
# Analysis document (this document)
# Replicating installation outside of current cloud provider
# Replicating installation to new cloud provider
# Testing
# Flipping the switch

=== Analysis document (this document) ===
In progress..


=== Replicating installation outside of current cloud provider ===
stub.


=== Replicating installation to new cloud provider ===
stub.


=== Testing ===
stub.


=== Flipping the switch ===
stub.