---
title: WPD:Infrastructure/proposals/Initial infrastructure
---
<p><br />
</p>
<div class="note">
<p><b>Note</b>: This page describes the initial plan for webplatform.org, most content is deprecated
</p>
</div>
<p><br />
</p>
<h2><span class="mw-headline" id="Work_Items">Work Items</span></h2>
<table class="wikitable sortable">
<tr>
<th> Priority
</th>
<th> Owner
</th>
<th> Task
</th>
<th> Status
</th>
<th> Time Estimate
</th>
<th> Depends On
</th>
<th> Must Finish By
</th></tr>
<tr>
<td> 1
</td>
<td> Ryan
</td>
<td> New URL structure
</td>
<td> complete
</td>
<td> 2-5 hours
</td>
<td> DNS changes
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Ryan
</td>
<td> Fastly integration
</td>
<td> complete
</td>
<td> 1 hour
</td>
<td> New URL structure
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 2
</td>
<td> Ryan
</td>
<td> Review code (extensions and SemMediaWiki)
</td>
<td>  in progress
</td>
<td> 1-2 hours
</td>
<td> None
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 2
</td>
<td> Ryan
</td>
<td> Move to DB service
</td>
<td>
</td>
<td> 1-2 hours
</td>
<td> None
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Ryan
</td>
<td> Backups/Restore instructions
</td>
<td> in progress
</td>
<td> 2-5 hours
</td>
<td> None
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Ryan
</td>
<td> Move to Block Service for gluster and backups
</td>
<td> complete
</td>
<td> 1-2 hours
</td>
<td> None
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Ryan
</td>
<td> Staging Server
</td>
<td> complete
</td>
<td> 4-5 hours
</td>
<td> New URL structure
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Ryan
</td>
<td> Improve deploy system
</td>
<td> complete
</td>
<td> 1 hour
</td>
<td> None
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Ryan
</td>
<td> Fix deployment code to output results
</td>
<td> open
</td>
<td> 1-2 hours
</td>
<td> None
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 2
</td>
<td> Ryan
</td>
<td> Move to object storage for media uploads
</td>
<td>
</td>
<td> 4-5 hours
</td>
<td> Need to ask Wikimedia about how it works
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Ryan
</td>
<td> Launch add'l app server instances
</td>
<td> complete
</td>
<td> 1-2 hours (took 4 hours)
</td>
<td> None
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Ryan
</td>
<td> Add ganglia monitoring
</td>
<td> complete
</td>
<td> 1-2 hours
</td>
<td> None
</td>
<td> Oct 1
</td></tr>
<tr>
<td> 1
</td>
<td> Ryan
</td>
<td> Add nagios monitoring
</td>
<td> complete
</td>
<td> 2-4 hours
</td>
<td> None
</td>
<td>&#160;?
</td></tr>
<tr>
<td> 1
</td>
<td> Ryan
</td>
<td> Add database replication
</td>
<td> complete
</td>
<td> 1-2 hours
</td>
<td> None
</td>
<td> Oct 3
</td></tr>
<tr>
<td> 1
</td>
<td> Contractors
</td>
<td> Import script (MSDN to Semantic MediaWiki)
</td>
<td> in progress
</td>
<td>
</td>
<td>
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Contractors
</td>
<td> Comments extension (HW)
</td>
<td> in progress, 90% complete
</td>
<td> 10 days
</td>
<td> partly on Skinning
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Contractors
</td>
<td> Site metrics (HW)
</td>
<td> done
</td>
<td> 2 days
</td>
<td> Improve deploy system (?)
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Contractors
</td>
<td> Integration with other software (Single Sign-On): Wordpress (HW)
</td>
<td> in progress
</td>
<td> 2 days
</td>
<td>
<ul><li> Installation of Wordpress</li>
<li> Launch add'l app server instances </li></ul>
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Contractors
</td>
<td> Integration with other software (Single Sign-On): Questions2Answers (HW)
</td>
<td> in progress
</td>
<td> 3 days
</td>
<td>
<ul><li> Installation of Questions2Answers</li>
<li> Launch add'l app server instances </li></ul>
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Contractors
</td>
<td> Search extension (page titles, categories) (HW)
</td>
<td> odone
</td>
<td> 3 days
</td>
<td> partly on Skinning
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 3
</td>
<td> Contractors
</td>
<td> Translation extension (HW)
</td>
<td> postponed
</td>
<td> 8 days
</td>
<td> partly on Skinning
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Contractors
</td>
<td> Breadcrumbs extension (HW?)
</td>
<td> work in progress
</td>
<td>
</td>
<td>
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 1
</td>
<td> Contractors
</td>
<td> Skinning (HW?)
</td>
<td> work in progress
</td>
<td>
</td>
<td>
</td>
<td> Sep 28
</td></tr>
<tr>
<td> 3
</td>
<td> Contractors
</td>
<td> file upload and storage
</td>
<td> postponed
</td>
<td>
</td>
<td>
</td>
<td> Sep 28
</td></tr></table>
<p><br />
</p><p><br />
</p>
<h3><span class="mw-headline" id="WikiWorks_SOW">WikiWorks SOW</span></h3>
<h4><span class="mw-headline" id="Phase_1">Phase 1</span></h4>
<ul><li> Bring up an initial version of MediaWiki on our hosting service that makes best available use of the resources available</li>
<li> Lock down the initial version of the site so only whitelisted users can access before it launches</li>
<li> Set up an account system that has normal users and administrators</li>
<li> Set up webplatform.org to point to the wiki</li>
<li> Get the MediaWiki configured to work with the CDN (e.g. Fastly), including sending site availability notices to team members</li>
<li> Set up the ~10 Semantic MediaWiki forms for different types of article content (e.g. CSS Reference, Tutorial, User page, etc.)</li></ul>
<h4><span class="mw-headline" id="Phase_2">Phase 2</span></h4>
<ul><li> Implement a theme design in MediaWiki based on provided designs, and iterate on the implementation and design in response to feedback from the committee.</li>
<li> Import ~3,000 documents from their existing, disparate sources into as consistent a format as reasonably possible</li>
<li> Teach the committee members how to create their own Semantic MediaWiki forms</li>
<li> Advise on best practices for running and configuring a wiki running on Semantic MediaWiki</li>
<li> Ensure that only administrators can create costly Semantic MediaWiki queries</li>
<li> Various other required minor tasks leading up to the launch that may arise</li></ul>
<h3><span class="mw-headline" id="Scraps">Scraps</span></h3>
<ul><li> Fast.ly CDN</li>
<li> Forums (Q2A)</li>
<li> Internationalization</li>
<li> IRC channel #webplatform</li>
<li> Email feedback account set up</li>
<li> Federated Login feature</li>
<li> Comments</li>
<li> Accessibility</li>
<li> Blog</li>
<li> Deployment script for site</li>
<li> Issue tracker (bugs)</li>
<li> Language switching</li>
<li> Logging bot (IRC)</li>
<li> Metrics and tracking</li>
<li> Single sign in (SSO)</li>
<li> System backup of site</li>
<li> Sandbox (live viewer)</li>
<li> Required email address for accounts</li>
<li> Twitter account @webplatform</li>
<li> Web client (IRC)</li>
<li> Wiki Setup</li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:347-0!*!*!!*!*!*!esi=1 and timestamp 20150731181953 and revision id 62560
 -->
