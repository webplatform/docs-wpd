---
title: '2013 - Migrating to a new cloud provider'
uri: 'WPD:Infrastructure/analysis/2013-Migrating to a new cloud provider'

---
## Introduction

This document follows [WPD:Infrastructure/analysis/2013-Usage and future state](/WPD:Infrastructure/analysis/2013-Usage_and_future_state) and should help with the [WPD:Infrastructure/analysis/2013-Usage and future state\#3. Refactored infrastructure](/WPD:Infrastructure/analysis/2013-Usage_and_future_state#3._Refactored_infrastructure) objectives.

While we were running on original deployment infrastructure, configuration was built empirically to suit the site visitors demand.

If you are searching for detailed technical requirements, they are [WPD:Infrastructure/analysis/2013-Hardware and software requirements](/WPD:Infrastructure/analysis/2013-Hardware_and_software_requirements)

## Phases

### Phase 0: Prepare upcoming migration

#### Dry run some salt stack states in HPCloud

Just to run Salt state scripts to test if all is fine. We never know if things broke along the changes made on the master branch.

#### Create a temporary MySQL replication node on selected provider

Will help speed up when it is time to flip the switch.

A Read-Only Database server; basically a slave of db1 in production (HPCloud), that other VMs in selected provider's infrastructure will read from.

### Phase 1: Getting access to selected provider's to prepare new environment

#### Getting access to selected provider's OpenStack controller

So we can start working.

#### Make a new 'deployment' node on the selected provider infrastructure

So we can start working.

1.  Move configuration files from /srv/code, /srv/salt, /srv/pillar and other important files.

#### Re-create the environment on the selected provider infrastructure

Instantiate nodes with the same specs (or as close as possible) to what we have.

1.  Test locally by overriding host names in own hosts file
2.  Ensure the new configuration match new private IP addresses
3.  Read from MySQL replication node on the selected provider VPS node. In read-only mode.
4.  New database nodes to read data from the MySQL replication node on selected provider VPS node

#### Create a copy of each Fastly services to point on nodes within selected provider infrastructure

Will be used through the reinstallation on the new environment and allow us to test prior to flipping the switch.

### Phase 2: Testing phase

#### Ask people to test the new infrastructure

Local database nodes will be read-only and getting synced from production.

Warn community that it is to test, and they will not be able to edit pages there.

#### Prepare flipping the switch

Script to make what is described in "Flip the switch" below as quick as possible.

### Phase 3: Flip the switch

This has to be scripted to be as quick as possible.

Assuming we have a sign-off from previous phase.

This step is leveraging the fact that Fastly configuration can be changed quickly. This will ensure us that in case of a problem, we can easily revert and therefore ease the pressure during the actual change.

#### Executing

In HPCloud environment:

1.  Make db1 (master) read only
2.  Make show a 'Migration in progress' note so users are not surprised if they cannot save

In selected provider environment:

1.  Make new db1 the master, disconnect from replication node
2.  Make new db2 the slave of db1, disconnect from replication node

In fastly:

1.  Change each 'service' to use new backend nodes from dream host, deploy them

#### Clean up

Assuming all is fine.

1.  Delete MySQL replication node on selected provider VPS node
2.  Delete Fastly temporary services
3.  Deprecate HPCloud
