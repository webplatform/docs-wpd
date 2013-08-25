= ''Renoir’s'' priorities =
== Summary ==
Outline page describing '''In progress''', the high-level '''Current priorities''', and some nice-to-have '''Suggestions''' (i.e. ''WishList'') attributed to  [http://w3.org/People/#renoirb Renoir].

== Scratch pad ==
Make clear what is going to be kept
Where is the redundancy
Minimal setup (staging, test)


== In progress ==
# Prepare moving infra [http://project.webplatform.org/infrastructure/issues/INFR-38 #INFR-38]
# Stabilize piwik installation into a self-contained VM while documenting a maintenance workflow
#* [[WPD:Infrastructure/MaintenanceWorkflow]], reporting [http://project.webplatform.org/infrastructure/issues/INFR-35 INFR-35]
#* Resolving issue, reporting [http://project.webplatform.org/infrastructure/issues/INFR-7 #INFR-7]
# Create an analytics dashboard (pending)

== Current Priorities ==
# Stability ''(ongoing)''
# Deployment strategy and migrations ''(long-term, parallel with other tasks)''
# Analytics/reporting ''(first phase, iterating over time)''
# Compatibility table ''(important for first beta)''

== Suggestions ==
"''WishList''", listed in no particular order.

Please note that most of them should be listed within the [http://project.webplatform.org/infrastructure/issues/wishlist project management issue tracker, in the '''INFR''' project in the "''wishlist''" list].

Also, others that has yet to be added:
* Find a SSL certificate provider for the WPD site
* NGINX and WordPress
* WordPress: Allow uploads, update to latest version
* ''App server false positives notifications'': Find a way to detect locally whether local app server has database access failure and send an e-mail
* ''Installation automation'':  Usage of DHCP/DNS to allocate new nodes: <br/>use-case: Start me a ‘app’ server, it’ll bootstrap a vanilla Ubuntu machine using TFTP, register to Salt stack, and install itself.
* ''Balance non http work load'': Leverage the present message queuing and by creating subscribers to take tasks: e.g. build e-mail to send, update data from remote web service.

=== Notes from Lea ===
# Whoever deploys, has to clear the cache
# Recommendation status icons http://dabblet.com/gist/5922066 
# Status flags http://result.dabblet.com/gist/6127923/b774fa5a44a0d7b6a1c752868cd47c67c31327b8

== Projects ==
=== Community management system ===
See [[WPD:Requirements/Community_Management_System]] ''Requirements'' and the hot-word "'''&CCMS'''"

=== Compatibility table ===
Yet to be described here.