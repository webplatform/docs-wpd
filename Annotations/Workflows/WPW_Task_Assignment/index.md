---
title: 'WPW Task Assignment'
uri: 'WPD:Annotations/Workflows/WPW Task Assignment'

---
One of the ways in which Web Platform Docs has solicited contributions has been through the [[Platform Wednesday](http://docs.webplatform.org/wiki/Meta:web_platform_wednesday%7CWeb)] project. With so much work to do, literally hundreds or even thousands of reference pages for features to be documented, it was difficult to let interested contributors know where to start, or to let them discover tasks on their own. Even when we decided to focus on only one topic, CSS, there were hundreds of pages to be created, and organizing volunteers to contribute to them was difficult. So, we decided to break the task down into more manageable chunks; each Wednesday, we would select 20 pages that needed to be created or edited, and then broke each of those pages down into 5 content tasks:

-   **Basic facts**, such as overview table, syntax, and values
-   **Explanatory text**, such as the introduction (summary), usage, and notes
-   **Examples**, with explanations
-   **Links** to tutorials and other materials (either inside WPD or on the wider web), to the relevant specifications, and cross-linking keywords to other reference articles
-   **Review**, including flagging and unflagging

This worked much better, but it was still logistically difficult. We had to assign coordinators for sets of pages, each of whom would be the point person for finding a volunteer for each task for each page, checking up on their progress, and managing that data in a table. This was made more difficult by the clumsy syntax required for tables in Semantic MediaWiki, and by the fact that there was no automation or central data reporting for keeping track of progress. We even resorted to spreadsheets in Google Docs, because the collaboration experience of MediaWiki was not conducive to large data sets: hundreds of CSS properties, with 5 tasks for each, as well as volunteer and coordinator names, along with other information like their URLs, status, notes, and so on. It was too complicated a process for part-time volunteers to manage their own data, given these constraints, so we couldn't rely on crowdsourcing for that.

Here is a proposal for how this process could be made much better and easier with an annotation system.

1.  The topics for the week are chosen, and a page for each topic created.
    -   On creation, each page is automatically annotated with a unique tag for that week (e..g. *wpw-15*) and an annotation for each of the 5 tasks, with a tag for that task, and an explanation of how to do it as the annotation body, as well as a selection anchor to the appropriate part of the page (e.g. mousing over the task annotation for "Examples" would highlight the "Examples" heading).

2.  A custom link is created that points to all the pages tagged with the unique WPW tag; the search and filtering capabilities of the annotation system make this trivial to do.
3.  A volunteer is pointed to this page, from which they select a page to edit, and follow that link.
4.  Arriving at the page, the contributor sees the different tasks that are still unassigned, in the annotation sidebar
    1.  The contributor selects a task, replying to the task annotation stating their intent to do that task, using the tag "assigned"
    2.  The contributor completes the task, and replies to their own intent annotation, using the tag "completed"

5.  The coordinators (and everyone else) has a view of the status of all these pages and tasks, using filtered views with tags; they can see all the pages and tasks that are still undone, and reassign tasks to new contributors if necessary

At any point, if the contributor gets lost in this process or isn't sure how to solve a content problem, they create an annotation with the tag "help", and one of the coordinators will be notified, and will jump on the thread to assist the contributor, often in real-time, but sometimes time-delayed (the contributor could also use email or IRC). Annotation enables a clearer and more contextualized communication channel than existing methods.

With these annotations left behind as a record of contributions, we maintain a more direct and visible attribution chain, to reward contributors.

With the planned addition of an up/down-voting mechanism in the annotation system, not only can individual contributors be given more visibility, but also more credit for particularly good work.

So, rather than the time-intensive and centralized process used for the CSS Web Platform Wednesdays, an annotation system will allow for a easy distributed process for managing contributors and content.
