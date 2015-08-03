---
title: WPD:Annotations/Workflows/WPW Task Assignment
---
<p>One of the ways in which Web Platform Docs has solicited contributions has been through the [<a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/Meta:web_platform_wednesday%7CWeb">Platform Wednesday</a>] project. With so much work to do, literally hundreds or even thousands of reference pages for features to be documented, it was difficult to let interested contributors know where to start, or to let them discover tasks on their own. Even when we decided to focus on only one topic, CSS, there were hundreds of pages to be created, and organizing volunteers to contribute to them was difficult. So, we decided to break the task down into more manageable chunks; each Wednesday, we would select 20 pages that needed to be created or edited, and then broke each of those pages down into 5 content tasks:
</p>
<ul><li> <b>Basic facts</b>, such as overview table, syntax, and values</li>
<li> <b>Explanatory text</b>, such as the introduction (summary), usage, and notes</li>
<li> <b>Examples</b>, with explanations</li>
<li> <b>Links</b> to tutorials and other materials (either inside WPD or on the wider web), to the relevant specifications, and cross-linking keywords to other reference articles</li>
<li> <b>Review</b>, including flagging and unflagging</li></ul>
<p>This worked much better, but it was still logistically difficult. We had to assign coordinators for sets of pages, each of whom would be the point person for finding a volunteer for each task for each page, checking up on their progress, and managing that data in a table. This was made more difficult by the clumsy syntax required for tables in Semantic MediaWiki, and by the fact that there was no automation or central data reporting for keeping track of progress. We even resorted to spreadsheets in Google Docs, because the collaboration experience of MediaWiki was not conducive to large data sets: hundreds of CSS properties, with 5 tasks for each, as well as volunteer and coordinator names, along with other information like their URLs, status, notes, and so on. It was too complicated a process for part-time volunteers to manage their own data, given these constraints, so we couldn't rely on crowdsourcing for that. 
</p><p>Here is a proposal for how this process could be made much better and easier with an annotation system.
</p>
<ol><li> The topics for the week are chosen, and a page for each topic created.
<ul><li> On creation, each page is automatically annotated with a unique tag for that week (e..g. <i>wpw-15</i>) and an annotation for each of the 5 tasks, with a tag for that task, and an explanation of how to do it as the annotation body, as well as a selection anchor to the appropriate part of the page (e.g. mousing over the task annotation for "Examples" would highlight the "Examples" heading).</li></ul></li>
<li> A custom link is created that points to all the pages tagged with the unique WPW tag; the search and filtering capabilities of the annotation system make this trivial to do.</li>
<li> A volunteer is pointed to this page, from which they select a page to edit, and follow that link.</li>
<li> Arriving at the page, the contributor sees the different tasks that are still unassigned, in the annotation sidebar
<ol><li> The contributor selects a task, replying to the task annotation stating their intent to do that task, using the tag "assigned"</li>
<li> The contributor completes the task, and replies to their own intent annotation, using the tag "completed"</li></ol></li>
<li> The coordinators (and everyone else) has a view of the status of all these pages and tasks, using filtered views with tags; they can see all the pages and tasks that are still undone, and reassign tasks to new contributors if necessary</li></ol>
<p>At any point, if the contributor gets lost in this process or isn't sure how to solve a content problem, they create an annotation with the tag "help", and one of the coordinators will be notified, and will jump on the thread to assist the contributor, often in real-time, but sometimes time-delayed (the contributor could also use email or IRC). Annotation enables a clearer and more contextualized communication channel than existing methods.
</p><p>With these annotations left behind as a record of contributions, we maintain a more direct and visible attribution chain, to reward contributors. 
</p><p>With the planned addition of an up/down-voting mechanism in the annotation system, not only can individual contributors be given more visibility, but also more credit for particularly good work.
</p><p>So, rather than the time-intensive and centralized process used for the CSS Web Platform Wednesdays, an annotation system will allow for a easy distributed process for managing contributors and content.
</p>
<!-- 
NewPP limit report
CPU time usage: 0.012 seconds
Real time usage: 0.014 seconds
Preprocessor visited node count: 1/1000000
Preprocessor generated node count: 4/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 1/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:13394-0!*!*!*!*!*!*!esi=1 and timestamp 20150731012645 and revision id 42899
 -->
