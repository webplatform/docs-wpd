= What’s next with the project? =

== Agenda ==
* Infrastructure overview
* New services
** notes server
** specs
** discourse

== Topics ==
=== Specifiction ===
* Domain name '''talk.webplatform.org'''
* action, ask Robin if he has preferences
* Remember that it might also be taken as a Q&A by the community and not spec centric
* Experimental features

== Scrachpad ==

Ideas we want to propose that are one of WebPlatform/W3C strengths or things we have in place.

We looked at doing documentation like MDN, and it wasn’t particularily successsful. Lots of efforts, can be a resource-blackhole, we can only have a limited success. We should maybe instead focus at things we would bring better value to developers. Not just "replacing" MDN. 

The unique of WebPlatform can offer is the W3C’s association and standards. For both audience, web developers and related to standards (maintenance and new specification). How can we best serve the audience.

What we learned while running WPD in the last years:
* Very little overlap between communities: standards, and web developers (success indicator)
* We didn’t have much attraction of web developer as an audience (new audience, a success)
* Bad thing is that we didn’t get much attraction from the standards community
* Our content might need to do more curation, lets set priorities and  focus on them
** Features that arent’ really well documented (e.g. SVG, Accessibility experts)
** '''Emerging technologies''', recently spec'ed, and not much documentation about them
** Increase involvement from the standards people. Help them participate with us.
* We havent got very much traffic because our focus was always into creating the content. We should focus less on the content, and more on the services.  Content isn’t unique, services can make a distinction.
 
=== Documentation plan ===
* we have a lot of content but its not well organized nor curated
* ''Documentation plan'':
** Features that arent’ really well documented AND/OR emerging technologies that are newly spec’ed
** Hire somebody to help curate and organize the site and do better organization
** Invite experts to help make exemplar pages, details, how tos. To make each pages useful for web developers
** Focus on quality instead of quantity (e.g. SVG, Accessibility)
** Set in place ways to extract out of standard documents to make it a base for documentation
** @TODO compat data? 
* In addition to doing documentation, we want to provide a way for developers to get more involved in the creation and standardization of technologies
* We also learned that we can’t really count on long sustained efforts from volunteers
* Regardless of whether or not we get steward support financially, convince them to make the editors ''also'' participate in documentation along with their work on standards


=== Developer involvement plan ===
* annotation system


=== Infrastructure we have in place ===
Elaborate on @TODO, in high level:
* Which individual software we run, pieces involved, what needs each piece fulfills
* Software we got rid of (web based IRC webclient, buggenie, etc)
* New components (github, huboard)
* We werent assured of long term free hosting form HP, thankfully DreamHost took charge of us
* Automation improvements
* Overview of lessons learned, and wins

==== WIP ====

* 2013:
** Installation of our own Analytics solution through Piwik
** Only one set of Virtual Machines (VMs) exposing live site, no room to work on improvements without risks of affecting live site
** Deployment scripts were assuming exactly one deployment, making it hard to do gradual roll out
** VMs were running with two different OS versions: Ubuntu 10.04 and 12.04 
** Setup of a private OpenStack at DreamHost ("DHO"; DreamHost OpenStack) cluster from a 4 blades server, server was lent by DreamHost
** Server migration from HP Cloud into DHO https://docs.webplatform.org/wiki/WPD:Infrastructure/analysis/2013-Migrating_to_a_new_cloud_provider
** Work on MySQL cluster so we could have off-site hot backup (i.e. database replication on a remote site, with logs transferred through SSL)
** Multiple outages due to a bug in MediaWiki+Semantic MediaWiki affecting the rest of the infrastructure
** Complete rework of MediaWiki installation. Originally it was a clone with bits and pieces pasted without source control to a scripted setup exclusively based on source controlled repositories
** Work with Doug to create a new Compatibility data JSON schema
** Sprint on extracting compatibility data from MDN into new Compatibility JSON schema
** Sprint on Compatibility tables extension
*** see https://docs.webplatform.org/wiki/WPD:Projects/CompaTables/201403-sprint
*** serve a copy of the generated HTML
*** flush the generated HTML copy when JSON source is updated
*** Alternate views and new supported actions:
***# single table view: https://docs.webplatform.org/wiki/Special:Compatables?feature=border-radius&format=table&topic=css
***#single table view, "naked" alternate https://docs.webplatform.org/wiki/Special:Compatables?feature=border-radius&format=table&topic=css&foresi=1
***#manual table flush https://docs.webplatform.org/wiki/Special:Compatables?feature=border-radius&format=table&topic=css&action=purge
*** Work on Semantic MediaWiki template https://docs.webplatform.org/wiki/Template:Compatibility to allow embed in content
*** Creation of a GitHub repository to host compatibility data https://github.com/webplatform/compatibility-data
***  Originally it was regenerating the HTML for EVERY page load based on a previous JSON source
** Removed requirement of shared storage across VMs to use external DreamObjects storage (Swift) at DreamHost 
** Set in place image storage pulling files directly from DreamObjects
* 2014
** Upgraded all VMs to use only Ubuntu 14.04
** Pages are now served under SSL.