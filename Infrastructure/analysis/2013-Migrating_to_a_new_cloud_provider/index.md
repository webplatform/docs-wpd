= 2013 - Migrating to a new cloud provider =

== Introduction ==
This document follows [[WPD:Infrastructure/analysis/2013-Usage and future state]] and should help with the [[WPD:Infrastructure/analysis/2013-Usage and future state#3. Refactored infrastructure]] objectives.

While we were running on original deployment infrastructure, configuration was built empirically to suit the site visitors demand. 

If you are searching for detailed technical requirements, they are [[WPD:Infrastructure/analysis/2013-Hardware and software requirements]]

__TOC__ this is bullshit

== Phases ==
Broken down into phases...


=== Phase 0: Prepare upcoming migration ===

==== Dry run some salt stack states in HPCloud ====
Just to run Salt state scripts to test if all is fine. We never know if things broke along the changes made on the master branch.

==== Create a temporary MySQL replication node on selected provider ====

Will help speed up when it is time to flip the switch.

A Read-Only Database server; basically a slave of db1 in production (HPCloud), that other VMs in selected provider's infrastructure will read from.


===  Phase 1: Getting access to selected provider's to prepare new environment ===

==== Getting access to selected provider's OpenStack controller ====

So we can start working.


==== Make a new 'deployment' node on the selected provider infrastructure ====

So we can start working.

# Move configuration files from /srv/code, /srv/salt, /srv/pillar and other important files.

==== Re-create the environment on the selected provider infrastructure ====

Instantiate nodes with the same specs (or as close as possible) to what we have.

# Test locally by overriding host names in own hosts file
# Ensure the new configuration match new private IP addresses
# Read from MySQL replication node on the selected provider VPS node. In read-only mode.
# New database nodes to read data from the MySQL replication node on selected provider VPS node


==== Create a copy of each Fastly services to point on nodes within selected provider infrastructure ====

Will be used through the reinstallation on the new environment and allow us to test prior to flipping the switch.



=== Phase 2: Testing phase ===

==== Ask people to test the new infrastructure  ====
Local database nodes will be read-only and getting synced from production.

Warn community that it is to test, and they will not be able to edit pages there.

==== Prepare flipping the switch ====

Script to make what is described in "Flip the switch" below as quick as possible.


=== Phase 3: Flip the switch ===

This has to be scripted to be as quick as possible.

Assuming we have a sign-off from previous phase.

This step is leveraging the fact that Fastly configuration can be changed quickly. This will ensure us that in case of a problem, we can easily revert and therefore ease the pressure during the actual change.

==== Executing ====

In HPCloud environment:
# Make db1 (master) read only
# Make show a 'Migration in progress' note so users are not surprised if they cannot save

In selected provider environment:
# Make new db1 the master, disconnect from replication node 
# Make new db2 the slave of db1, disconnect from replication node

In fastly:
# Change each 'service' to use new backend nodes from dream host, deploy them


==== Clean up ====

Assuming all is fine.

# Delete MySQL replication node on selected provider VPS node 
# Delete Fastly temporary services
# Deprecate HPCloud