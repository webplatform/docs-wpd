---
title: WPD:Infrastructure/proposals/Site status problem notification messages
---
<h1><span class="mw-headline" id="Site_status_problem_notification_messages">Site status problem notification messages</span></h1>
<h2><span class="mw-headline" id="Description">Description</span></h2>
<p>In case of an site problem, some boilerplate error messages to start from. Generally we publish them to <a rel="nofollow" class="external text" href="http://status.webplatform.org">status.webplatform.org</a> and broadcast them to Twitter <a rel="nofollow" class="external text" href="https://twitter.com/WebPlatform">@WebPlatform</a> and other Social media accounts.
</p>
<h3><span class="mw-headline" id="TODO">TODO</span></h3>
<ul><li> When we need to block writes for backup/maintenance purposes</li>
<li> When a problem is caused by code being deployed <a rel="nofollow" class="external text" href="http://status.twitter.com/post/63765159379/issue-viewing-timelines">Example: this status text</a></li>
<li> When we need to shut down</li>
<li> What to put as general note after a problem notification message</li>
<li> Maintenance window warning</li>
<li> Error pages text, add link to advise looking at <b>status.webplatform.org</b> site on <a rel="nofollow" class="external text" href="http://www.webplatform.org/errors/404.html">404 Error page</a>, <a rel="nofollow" class="external text" href="http://www.webplatform.org/errors/503.html">503 Error page</a>, and also (missing) <b>500 Error page</b></li></ul>
<h3><span class="mw-headline" id="Inspiration_and_similar_micro_sites">Inspiration and similar micro sites</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="https://community.hpcloud.com/status">HP Cloud status</a></li>
<li> <a rel="nofollow" class="external text" href="http://status.twitter.com">Twitter status</a></li>
<li> <a rel="nofollow" class="external text" href="https://developers.facebook.com/live_status/">Facebook live status</a></li></ul>
<h2><span class="mw-headline" id="Messages_per_problem_type">Messages per problem type</span></h2>
<h3><span class="mw-headline" id="Generic">Generic</span></h3>
<p><b>Title:</b>: WebPlatform Site Issue
</p><p>Some users may be experiencing an issue with our service. Our team are currently working on this issue.
</p>
<h3><span class="mw-headline" id="Currently_working_on_.28....29">Currently working on (...)</span></h3>
<p>We are currently working to repair a problem with (...)  and in consequence affecting (...).
</p><p>Some small down time might happen, but it is under control. We are sorry for the inconvenience.
</p>
<h3><span class="mw-headline" id="There_has_been_issues_.28....29">There has been issues (...)</span></h3>
<p>(In case the issue is still unknown)
</p><p>For the last two hours, there has been issues visiting or editing pages. We are investigating the situation and will keep you updated.
</p>
<h3><span class="mw-headline" id="Database_server_problem">Database server problem</span></h3>
<p>The database server is currently not answering requests properly. Some pages are still available due to caching. We are investigating the situation and will keep you updated.
</p>
<hr />
<h2><span class="mw-headline" id="Notifying_problem_resolution">Notifying problem resolution</span></h2>
<ol><li> Prepend 'FIXED: ' to the status message title</li>
<li> Add first line of status message <b>Update: This issue has been resolved as of 24:00 EST.</b></li>
<li> Put a <b>Original announcement</b> title before the original announcement message</li>
<li> Describe what was the problem (optional)</li>
<li> Add comment from first line status message "Update: ..." as comment on all social media sites that had the status report</li></ol>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:12041-0!*!*!!*!*!*!esi=1 and timestamp 20150731184729 and revision id 40896
 -->
