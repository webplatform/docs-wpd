---
title: WPD:Infrastructure/analysis/2013-Migrating to a new cloud provider
---
<h1><span class="mw-headline" id="2013_-_Migrating_to_a_new_cloud_provider">2013 - Migrating to a new cloud provider</span></h1>
<h2><span class="mw-headline" id="Introduction">Introduction</span></h2>
<p>This document follows <a href="/wiki/WPD:Infrastructure/analysis/2013-Usage_and_future_state" title="WPD:Infrastructure/analysis/2013-Usage and future state">WPD:Infrastructure/analysis/2013-Usage and future state</a> and should help with the <a href="/wiki/WPD:Infrastructure/analysis/2013-Usage_and_future_state#3._Refactored_infrastructure" title="WPD:Infrastructure/analysis/2013-Usage and future state">WPD:Infrastructure/analysis/2013-Usage and future state#3. Refactored infrastructure</a> objectives.
</p><p>While we were running on original deployment infrastructure, configuration was built empirically to suit the site visitors demand. 
</p><p>If you are searching for detailed technical requirements, they are <a href="/wiki/WPD:Infrastructure/analysis/2013-Hardware_and_software_requirements" title="WPD:Infrastructure/analysis/2013-Hardware and software requirements">WPD:Infrastructure/analysis/2013-Hardware and software requirements</a>
</p>

<h2><span class="mw-headline" id="Phases">Phases</span></h2>
<h3><span class="mw-headline" id="Phase_0:_Prepare_upcoming_migration">Phase 0: Prepare upcoming migration</span></h3>
<h4><span class="mw-headline" id="Dry_run_some_salt_stack_states_in_HPCloud">Dry run some salt stack states in HPCloud</span></h4>
<p>Just to run Salt state scripts to test if all is fine. We never know if things broke along the changes made on the master branch.
</p>
<h4><span class="mw-headline" id="Create_a_temporary_MySQL_replication_node_on_selected_provider">Create a temporary MySQL replication node on selected provider</span></h4>
<p>Will help speed up when it is time to flip the switch.
</p><p>A Read-Only Database server; basically a slave of db1 in production (HPCloud), that other VMs in selected provider's infrastructure will read from.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Phase_1:_Getting_access_to_selected_provider.27s_to_prepare_new_environment">Phase 1: Getting access to selected provider's to prepare new environment</span></h3>
<h4><span class="mw-headline" id="Getting_access_to_selected_provider.27s_OpenStack_controller">Getting access to selected provider's OpenStack controller</span></h4>
<p>So we can start working.
</p><p><br />
</p>
<h4><span class="mw-headline" id="Make_a_new_.27deployment.27_node_on_the_selected_provider_infrastructure">Make a new 'deployment' node on the selected provider infrastructure</span></h4>
<p>So we can start working.
</p>
<ol><li> Move configuration files from /srv/code, /srv/salt, /srv/pillar and other important files.</li></ol>
<h4><span class="mw-headline" id="Re-create_the_environment_on_the_selected_provider_infrastructure">Re-create the environment on the selected provider infrastructure</span></h4>
<p>Instantiate nodes with the same specs (or as close as possible) to what we have.
</p>
<ol><li> Test locally by overriding host names in own hosts file</li>
<li> Ensure the new configuration match new private IP addresses</li>
<li> Read from MySQL replication node on the selected provider VPS node. In read-only mode.</li>
<li> New database nodes to read data from the MySQL replication node on selected provider VPS node</li></ol>
<p><br />
</p>
<h4><span class="mw-headline" id="Create_a_copy_of_each_Fastly_services_to_point_on_nodes_within_selected_provider_infrastructure">Create a copy of each Fastly services to point on nodes within selected provider infrastructure</span></h4>
<p>Will be used through the reinstallation on the new environment and allow us to test prior to flipping the switch.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Phase_2:_Testing_phase">Phase 2: Testing phase</span></h3>
<h4><span class="mw-headline" id="Ask_people_to_test_the_new_infrastructure">Ask people to test the new infrastructure</span></h4>
<p>Local database nodes will be read-only and getting synced from production.
</p><p>Warn community that it is to test, and they will not be able to edit pages there.
</p>
<h4><span class="mw-headline" id="Prepare_flipping_the_switch">Prepare flipping the switch</span></h4>
<p>Script to make what is described in "Flip the switch" below as quick as possible.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Phase_3:_Flip_the_switch">Phase 3: Flip the switch</span></h3>
<p>This has to be scripted to be as quick as possible.
</p><p>Assuming we have a sign-off from previous phase.
</p><p>This step is leveraging the fact that Fastly configuration can be changed quickly. This will ensure us that in case of a problem, we can easily revert and therefore ease the pressure during the actual change.
</p>
<h4><span class="mw-headline" id="Executing">Executing</span></h4>
<p>In HPCloud environment:
</p>
<ol><li> Make db1 (master) read only</li>
<li> Make show a 'Migration in progress' note so users are not surprised if they cannot save</li></ol>
<p>In selected provider environment:
</p>
<ol><li> Make new db1 the master, disconnect from replication node </li>
<li> Make new db2 the slave of db1, disconnect from replication node</li></ol>
<p>In fastly:
</p>
<ol><li> Change each 'service' to use new backend nodes from dream host, deploy them</li></ol>
<p><br />
</p>
<h4><span class="mw-headline" id="Clean_up">Clean up</span></h4>
<p>Assuming all is fine.
</p>
<ol><li> Delete MySQL replication node on selected provider VPS node </li>
<li> Delete Fastly temporary services</li>
<li> Deprecate HPCloud</li></ol>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:11776-0!*!0!!en!*!*!esi=1 and timestamp 20150731184702 and revision id 100246
 -->
