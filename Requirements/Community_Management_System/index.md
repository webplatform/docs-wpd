---
title: WPD:Requirements/Community Management System
---
<h2><span class="mw-headline" id="Description">Description</span></h2>
<p>Unearthing requirements for an ideal WPD content and community management system
</p>
<h3><span class="mw-headline" id="See_also">See also</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="https://www.w3.org/2011/docs/wiki/Technical_Requirements">WPD first technical requirements document</a></li>
<li> <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/WPD:Projects/Beta_Requirements">WPD Beta requirements</a></li></ul>
<h2><span class="mw-headline" id="Design_choices">Design choices</span></h2>
<ol><li> Technology choice should be all Javascript. </li>
<li> API for content, partial, anything</li>
<li> Everything end-up in a Git repo</li></ol>
<h2><span class="mw-headline" id="Backlog">Backlog</span></h2>
<p>Proposed initial backlog:
</p>
<ul><li> As a person, I want to subscribe so I can be known as a user;</li>
<li> As a user, I want to start contributing by declaring my intention;</li>
<li> As a user, I'd like to know which pages I should start with;</li>
<li> As a coordinator, I want to know who said would work <i>tonight</i>;</li>
<li> As a user, I want to say on which document I am working on;</li>
<li> As a user, I want to tell when I am done working on a document;</li>
<li> As a coordinator, I want to give a list of documents that needs to be worked on;</li>
<li> As a system, I want to make sure a user has access to whatever he has access to;</li>
<li> As a coordinator, I want to assign tasks to a user;</li>
<li> As a coordinator, I want to know what a user has been working on recently;</li>
<li> As a coordinator, I want to know all users who have contributed, but have not contributed recently;</li>
<li> As a coordinator, I want to know whom I've emailed (or otherwise contacted) and when;</li></ul>
<h2><span class="mw-headline" id="Functional_requirements">Functional requirements</span></h2>
<ul><li> Flagging/tagging (users, pages, category)</li>
<li> Object oriented CMS
<ul><li> element knows that it needs links, attributes, API, other elements in same category</li>
<li> <a rel="nofollow" class="external text" href="http://www.neo4j.org/">Relationship graph</a></li></ul></li></ul>
<h3><span class="mw-headline" id="Task_allocation_system">Task allocation system</span></h3>
<ul><li> list of desired task</li>
<li> easy checkbox to claim task</li>
<li> file status and time spent</li>
<li> report on all tasks</li></ul>
<h2><span class="mw-headline" id="Content">Content</span></h2>
<p>Content could be organized in small blocks (feature summary, feature code samples, etc) in a way where we can build views depending of the context. Views could be in listing pages, code samples, etc. and be served through an API.
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:9499-0!*!*!!*!*!*!esi=1 and timestamp 20150731184507 and revision id 49603
 -->
