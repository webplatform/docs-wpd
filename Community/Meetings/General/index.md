Web Platform content architecture meetings occur on Thursdays, 20:00 UTC / 15:00 ET / Noon PT. 

{{Note | Each week we will decide if next week's meeting is necessary. }}

==Telcon Info==

'''Zakim Bridge:''' +1.617.761.6200

'''Conference code:''' 3627 ("DOCS") 

'''VOIP:'''  sip:zakim@w3.org

We simultaneously meet in the #webplatform-site IRC channel. Afterwards we will send out minutes.

==Agenda 2012-12-06==
* Roll call
* Triage of new content architecture issues
** New templates this week: listing pages
** Identifying stable vs. proprietary and experimental features
** Checking in about dom, cssom, svgom
** Topic hierarchy needs updating
** Style guide for example code [[https://www.w3.org/Bugs/Public/show_bug.cgi?id=20227|bug 20227]]
* Review of open action items
* [[https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2496|content bugs]]: Content bugs in bugzilla need your input and resolution.
* Checking in about dom, cssom, svgom
* Topic hierarchy needs updating

==Agenda 2012-11-28==
* Roll call
* Triage of new content architecture issues
* Review of open action items
** The [[WPD:New_Page|New_Page]] page is up to date with example text and links
** just like the Getting Started page which has a [[WPD:Getting_Started#Guides_to_creating_pages|section that anticipates additional guides]] with a link to
** the [[WPD:Creating_API_pages|Creating API Pages guide]], where all of the above is captured, if not tamed.
** Action item for Mike and Julee to try out structure resulted in some issues which we'll continue to discuss today. (See Mike's email to public list 2012-11-15 re: creating api pages.)
* Handling specialized API [[WPD:Creating_API_pages|in light of new guidelines]].
** How to represent constants and exceptions on separate pages?
** Should APIs that add members to existing core interfaces be listed separately?
** Where appropriate, note the DOM node used to access each interface object: document, navigator, window, video, audio, etc.
* [[WPD:Task_Roadmap|Task roadmap]] includes content track, prioritizing content issues. (See email re: task roadmap for content, infrastructure and styling tasks from Chris Mills <cmills@opera.com>.)
* [[https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2496|content bugs]]: Content bugs in bugzilla need your input and resolution.

==Meeting summary==

===Topics discussed===

* We asked editors to review, update, address content bugs in the bug base: https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2513
* We pointed out the new task roadmap: http://docs.webplatform.org/wiki/WPD:Task_Roadmap, and related email, and asked for comments. It's a high-level view that's very readable. Editing it (e.g.: adding columns) might be a bit tricky.
* We discussed the need for a project management system and a program manager to ensure content tasks are triaged. WPD:Most_Wanted_Tasks isn't working and we need motivational leaders and tools.
* We continued discussion on creating API pages, focusing on exceptions to the guidelines (WPD:Creating_API_pages).
** What to do for API that add members to an existing interface. For example, CSS Regions includes a new member in the Document interface - keep it with the API or the existing interface? Probably in both. But where does canonical page reside?
** What to do with lots of little bits of information, for example SVG attribute values or the HTML type element? For data modeling purposes, it might be best to create separate pages for each and then include them in the main page. What is best for folks importing, managing content? For the end-user?
* We need to change the meeting time.

===Decisions===

* We will use bug base for tracking content areas that need to be created, such as DOM ranges.
* Until project management for whole project is resolved, we will call out high-level direction on WPD:Task_Roadmap and track specific content issues in bug base.
* We will file content bugs on any additional open issues with the API.

===Action items===

* chrismills to set up a Doodle poll for next meeting times.
* garbee to write guidelines on creating content bugs.
* (was julee, is now) Garbee to write down (in bug creation guidelines) what issues go where (Bugzilla vs. WPD:Task_Roadmap, WPD:Most_Wanted_Tasks, Special:WantedPages, WPD:Getting_Started, etc.)
* Alex to write up a description of the project manager's role.
* All: review this summary to ensure accuracy.

===Proposed next discussion topics===

Address any open issues with concepts and tutorials pages.