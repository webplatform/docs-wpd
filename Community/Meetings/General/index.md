Web Platform content architecture meetings occur on Thursdays, 20:00 UTC / 15:00 ET / Noon PT. 

{{Note | Each week we will decide if next week's meeting is necessary. }}

==Telcon Info==

'''Zakim Bridge:''' +1.617.761.6200

'''Conference code:''' 3627 ("DOCS") 

'''VOIP:'''  sip:zakim@w3.org

We simultaneously meet in the #webplatform-site IRC channel. Afterwards we will send out minutes.

{{Note | If you haven't already done so, please volunteer to scribe. }}

==Agenda 2013-01-10==

* Roll call
* Review of open action items
* Triage of new content architecture issues
** https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2513 content bugs
* Anything blocking you from creating great content?
* Any new or notable content to promote?

==Agenda 2013-01-03==

* Roll call
* Review of open action items
* Triage of new content architecture issues
** All [https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2513 content bugs] are assigned to either Chris or Garbee. Do we want to re-assign some of them?
* Status on [https://www.w3.org/Bugs/Public/show_bug.cgi?id=20160 bug#20160]
* Current workflow for promoting new/great content? (Propose, Review, Sign-off?)
* DocSprint in Germany
** Anyone going?
** Registration for the first european Doc Sprint in Berlin, Feb 8+9 2013, is now open. Please help to spread the word:
*** [https://plus.google.com/100575683580946332118/posts/iLxwzGU6zac Share]
*** [https://alpha.app.net/klick_ass/post/2113801 Repost]
*** [https://twitter.com/klick_ass/status/281775907734167553 Retweet]
* Scott is working on Listing pages (Per Scott's email Thursday, December 20, 2012 11:35 AM; Subject: Re: New topic landing pages installed (was Re: We have a new front page))
* Status on Dabblet?
* Anything blocking you from creating great content?

==Meeting Summary==

===Discussion===

* We're adding an API section to the topic landing pages. We need to include APIs and their icons on those pages. Seb is working on an icon, and Chris will put that in the landing page
* Concept_Listing template is done
* Continuing to work on API area: reorganizing it and following through on previous work we've done. The APIs section is starting to come around, with help from Dave Gash.
* Promoting new or great content. To post about WPD topics, see  http://docs.webplatform.org/wiki/WPD:Marketing/Posting_Guidelines. 
** The process right now is shoot it into the Mailing List, wait a bit, and see if anyone disagrees with it. Doug will set up additional bloggers. This content task force will continue to request suggestions for "Any new and notable content to promote"
* DocSprint Germany: Scott Rowe is probably going.
* We received status on the Dabblet extensions. The consensus on the list was code.webplatform.org. Lea has put the technical things in place in her codebase there's still some work to do to link from. First is a dabbler instance on code.webplatform.org. The second phase is to make it easy to open examples on the site in that instance (a "try now" button). Third phase is actual live code examples in the pages themselves. (possibly) via iframes. (There's actually a phase 4 that allows us to decouple a dependency on github.) We're aiming to have first phase done by next week. And we should have a blog post about it. We also need to get a template made with the form to submit/change code in the forms. Garbee is emailing Tomato this afternoon to see if she would be up for that. 
* We need more work on getting started pages (bug : https://www.w3.org/Bugs/Public/show_bug.cgi?id=20160). At last doc sprint was they just can't get through them -- somewhere between five and ten people. When we walked them through the basics, they had a hard time getting productive. Following through the instructions is difficult. It should be more self-serve. Julee to send outline of new Editor's Guide next week. Scott to work on usability testing. Also, there are going to be some people who don't respond to the given way. So maybe we have other docs for different mind sets. Scott and Peter are working on Getting Started videos. 
** Additional Getting Started problems: 
*** The form system. For example, we've seen people wanting to use API_Listing template on other pages, which breaks pages (it uses two forms).
*** There was a glitch in the process for updating compatibility tables. A lot of the pages in the "Pages that need compatibility table" weren't working.
*** A lot of people at the Sprint were confused with them. I actually spent most of the day there explaining it to people.
*** A handful actually went to editing source because the button was there. Some of us want to remove that button unless you are an admin or in the template corp group whenever that gets made.
*** Besides forms people were getting hit hard by the template bugs that require the hacks like {{!}} and {{=}}. We need to either fix it so those hacks aren't required or look at another way of doing things.
** Additional solutions:
*** One way to fix the hacks would be editing as much as possible in raw HTML. Leaving mostly only links to be made in the wiki markup.
*** Garbee has an open bug report for it iirc. Has been there for a while. I will bring attention to it once we get an in-house system going.
*** People also seemed to be lost in what was needed to be done. We should try to use the content tracker to a greater extent once we get it in-house.
*** Another way to approach it is that it will always be hard for new editors--so we can also focus on making EXISTING editors more productive and effective.
*** "If you know something that needs to be done but don't have the time, even if it is a 5 minute thing, file a bug report." We should try to encourage that more.
*** We also need better ways for people to get in touch with existing editors if they have questions. Not having a web chat system hurts a bit probably. (We could iframe freenode's webchat today and have a safe system online!)
* Alex gives us a tantalizing tease: join meeting next week for some good news.
* Everyone should feel free to add agenda items for these content meetings.


==Action Items==

* ACTION: Julee to add to weekly agenda template: "Any new and notable content to promote?" UPDATE: DONE
* ACTION: Doug to add folks who responded to email thread as contributing bloggers.
* ACTION: Julee and klick_ass to write up WPD blog post about Germany Doc Sprint.
* ACTION: Julee to send out Ed Guide outline. UPDATE: DONE
* ACTION: Scott to work on usability of Ed Guide.
* LAST WEEK ACTION: Julee to update Topic Hierarchy and Architecture pages. UPDATE: in progress
* LAST WEEK ACTION: Julee to send out an email discussing how we should "take" and re-assign bugs to even the work out more. UPDATE: Julee sent an email.
* LAST WEEK ACTION: Eliot to do an editorial pass on the proposed top-level pages. UPDATE: No status.
* LAST WEEK ACTION: Jswisher to request the next level of detail on the global nav and how the reader accesses the content types as well as the technology areas. UPDATE: Janet sent out the email.
* PREVIOUS ACTION: Julee to find out how to add a meeting bot to the Content TF Meeting. UPDATE: in progress
* PREVIOUS ACTION: Julee to file a bug about the design of reference pages with a non-standard standardization status. UPDATE: needs to be revised: Julee to file a UI bug about the design of reference pages with non-stable status, so that they look distinct. UPDATE: Filed two bugs:
** For needing the categories
** For needing the UI updated to reflect the categories
* PREVIOUS ACTION: Garbee to send out his awesome task organization plan. UPDATE: sending it out today.


==Agenda 2012-12-13==
* Roll call
* Review of open action items
* Triage of new content architecture issues
** All [https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2513 content bugs] are assigned to either Chris or Garbee. Do we want to re-assign some of them?
* Top-level navigation and design update from Chris Mills
** [http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0172.html Main landing page prototypes completed/subpage structures?/domain leads?]
** [http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0235.html allow people to start their search by technology or page type]
** [http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0221.html Different ways to browse]
* Anything blocking you from creating great content?


==Meeting summary==
===Discussion===

* Note that the [https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2513 content bugs] are assigned to either Chris or Garbee. We wonder how do we spread these out to others? Maybe a larger issue than with just the content bugs?
* Discussed top-level pages sent out by Chris. We generally thought Chris's [http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0172.html proposed pages] were excellent. Eliot volunteered to do an edit pass on the descriptions.
* We discussed the [http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0235.html navigation proposals] (and [http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0221.html Proposal for updating links on webplatform.org proposal for updating links]) that have been in the email list. We discussed the pros and cons of providing the reader with a choice of content type or topic area, via hover links on the global nav. We would appreciate a mock-up. We are not sure how the different proposals would actually pan out. Jswisher took the action to follow up in the email threads and request the next level of detail.
* We identified four priorities we're working on to make editing the site easier and hope to have this work completed by the new year:
** The global nav/landing pages, discussed above, that Chris Mills is working on
** The [https://www.w3.org/Bugs/Public/show_bug.cgi?id=20160 consolidation of editorial pages] that Garbee is working on
** Updating the Topic Hierarchy and Architecture pages that Julee is working on
** The [https://www.w3.org/Bugs/Public/show_bug.cgi?id=19390 session bug] that shepazu hopes will be resolved this weekend.
* The Content Task Force will not meet for the next two weeks. We will resume again 1/3/2013.

===Action Items===

* Julee to update Topic Hierarchy and Architecture pages.
* Julee to send out an email discussing how we should "take" and re-assign bugs to even the work out more.
* Eliot to do an editorial pass on the [http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0172.html proposed top-level pages]. 
* Jswisher to request the next level of detail on the global nav and how the reader accesses the content types as well as the technology areas.
* LAST WEEK ACTION: Julee to find out how to add a meeting bot to the Content TF Meeting.
** UPDATE: in progress
* LAST WEEK ACTION: Julee to file a bug about the design of reference pages with a non-standard standardization status.
** UPDATE: needs to be revised: Julee to file a UI bug about the design of reference pages with non-stable status, so that they look distinct.
** Filed two bugs:
*** [https://www.w3.org/Bugs/Public/show_bug.cgi?id=20386 For needing the categories]
*** [https://www.w3.org/Bugs/Public/show_bug.cgi?id=20387 For needing the UI updated to reflect the categories]
* LAST WEEK ACTION: Garbee to send out his awesome task organization plan
** UPDATE: still working on it

==Agenda 2012-12-06==
* Roll call
* Review of open action items
* Triage of new content architecture issues
** Identifying stable vs. proprietary and experimental features
** Style guide for example code [[https://www.w3.org/Bugs/Public/show_bug.cgi?id=20227|bug 20227]]
** Topic hierarchy needs updating
* Anything blocking you from creating great content?
* [[https://www.w3.org/Bugs/Public/show_bug.cgi?id=20180|Main bug of site UX]]
** Please review, especially in terms of content discoverability
** [[https://www.w3.org/Bugs/Public/show_bug.cgi?id=20250|Bug on adding a menu]]
** [[https://www.w3.org/Bugs/Public/show_bug.cgi?id=19386|Bug for fixing top-level buckets]]
* New templates this week: listing pages
* 12/12/12 DocSprint?
** Any content-specific focus?
** Going? Going to be on IRC? 
* [[https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2496|content bugs]]: Content bugs in bugzilla need your input and resolution.

==Meeting summary==
===Topics discussed===
* We discussed the status on the project/program manager for the content tasks. Alex said he realized that the term "project manager" might have caused some confusion and may have implied too big a scope. Really, it's more about someone who just follows through on Action items. We're continuing to discuss this with those who have volunteered for the role.
* We discussed categorizing the features as stable, proprietary, experimental, and so on.We do have a page that calls out the different statuses: http://docs.webplatform.org/wiki/Property:Standardization_Status. We need to further discuss what are the appropriate categories for WPD. The http://docs.webplatform.org/wiki/WPD:Pillars page says that we should aim to be useful documentation for the web as it is, so categories such as "proprietary" are important, because we might document something that's useful but has legal restrictions. If there's something TOTALLY proprietary, we had talked about having that in a special vendor section as well 
* We discussed the example code style bug [https://www.w3.org/Bugs/Public/show_bug.cgi?id=20227|Bug 20227], but decided to table it for a couple of weeks, because Lea's dabbler code highlighting might land next Friday. (Here's what we have so far: http://docs.webplatform.org/wiki/WPD:Manual_Of_Style/Sample_best_practices)
* Topic hierarchy page and architecture page is one place where people go to figure out where things go and where they will be. It needs updating. Julee volunteered to do this. We predicted that questions will probably arise from this task.
* We want to ask each week: Anything blocking you from creating great content? This week, it's the session bug. Ryan has installed the newest version of mediawiki. There are a few conflicts, he's working to resolve those before deploying.
* We called out the user experience bugs for this task force to review, especially to confirm designs are discoverable, accessible, and follows content architecture:
** https://www.w3.org/Bugs/Public/show_bug.cgi?id=20180 (site organization)
** https://www.w3.org/Bugs/Public/show_bug.cgi?id=20250 (global nav)
** https://www.w3.org/Bugs/Public/show_bug.cgi?id=19386 (links from main)
* This brought up another topic:
* Use Meta bugs on bugzilla are big and fuzzy. Plans, proposals, and scratch pad work should be kept as subpages: http://docs.webplatform.org/wiki/WPD:Plans. Not in Bugzilla, and not in another site, such as GitHub. They keep the substantive discussion/plans in WPD:Plans/FOO, and then as actionable sub-items pop out, we file them as bugs that the meta bug depends on.
* Garbee mentioned that one of the things with using Bug genie is we can edit comments.  So we could actually use that as our place to put things like my Beginner's Guide outline as a comment, then just edit that comment when we update things.  Further centralizing some creation there if we 1) Go with Bug Genie and 2) decide to use it that way. So an issue is just opened for it to be created, then the outline is one of the comments.
* When new templates appear, such as the listing pages that were sent out for review this week, call it out in terms of content, reviewing it to make sure they make sense from content perspective.
* We talked about the coming DocSprint at Google. Several folks are going. Several suggestions regarding promoting, gathering like-skilled folks together via tweeting and other social channels. Also several folks are going to try to get editors' feedback about their experience of the site.
* We talked about the template corp and giving access to those who want to edit templates. But not on a one-off basis, more like giving group access.

===Decisions===
* Until we have a project management system in place, plans, proposals, and scratch pad work should be kept as subpages: http://docs.webplatform.org/wiki/WPD:Plans. Not in Bugzilla, and not in another site, such as GitHub.

===Action items===
* Julee to find out how to add a meeting bot to the Content TF Meeting.
* Julee to file a bug about the design of reference pages with a non-standard standardization status.
* Eliot to update bug 20227 with pointer to the style guide he wrote
* Garbee to send out his awesome task organization plan
* Scott and Peter to explore social media channels about next week's docsprint
Proposed next discussion topics

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