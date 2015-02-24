= Monit =

== What is Monit ==

Monit is a server monitoring system that ensures that their services are running or enforce them to run. 

Monit has two components:
* '''monit''', an open-source agent with internal reporting
* '''M/Monit''', a paid software that ''monit'' can push updates to

== Monit ==

As described in the Feb. 2015 documentation rework describing the [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM|Base configuration of a VM]], every VM has Monit running.

You can review the Monit report by following steps described in [[WPD:Infrastructure/architecture/Reports_to_review_status#Using_Monit|Reports to review a VM status, at ''Using Monit'' section]].

Here is a preview of how a Monit status report looks like.

[[File:20150224-monit-status-preview.png]]



== ''M/Monit'' ==

Those arescreenshots of '''M/Monit''' while I was testing out the feature differences between the paid app (''M/Monit'') and what comes in the open source version.

* [[File:monit_dashboard_201502_status.png]]
* [[File:monit_dashboard_201502_stats.png]]
* [[File:monit_dashboard_201502_home.png]] 
* [[File:monit_dashboard_201502_vm_detail.png]]