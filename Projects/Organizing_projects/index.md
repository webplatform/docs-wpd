===Background===

Our new [http://project.webplatform.org project] space should help us achieve our mission. The activities around this mission should broken down into [[WPD:Project_Status|milestones]], with all projects and tasks directed toward that milestone, or deferred until a future milestone.

This document proposes an project architecture to reflect these requirements.

{{Note | This document is subject to change based on what we find out about The Bug Genie and what it can and cannot do. }}


===One mission: One master project===

We will a top-level view of the mission's progress. Users of project.webplatform.org will be able to see a top-level status of the progress toward a milestone, and then drill down into functional areas to see the state of that area. 

===Except for what doesn't get done...===

Issues come up that may need to defer to the current milestones. These issues need to be stored until they can be incorporated back into the master project. Given that, there is another top-level bucket "deferred" which mirrors the master project in so far as deferred items exist. This will facilitate mobility of issues in and out of milestones, while keeping the current working space cleaner.

===Project organization===

The following organization of the projects on project.webplatform.org reflects the requirements and dependencies:

* Top level view of activities
** Persistant goal 1
*** Project-or-activity-1
*** Project-or-activity-n
** Persistant goal 2
** Persistant goal 3
** Persistant goal n
* Deferred activities
** Persistant goal 1
** Persistant goal 2
** Persistant goal 3

So, for example, we could have the following projects and/or components (these are illustrative, not actual items):

* Master Project
** Content Quality
*** Information Architecture
** Infrastructure
*** Project Management System (PRMG)
*** Analytics
*** Search
*** Compatibility Tables
** Community
*** Blog
* Deferred
** Items to be address for the next milestone
** Content
** Infrastructure Performance
*** Skin
*** Templates
*** Comments Extension
** Community Growth