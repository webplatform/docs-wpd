Web Platform content architecture meetings occur on Fridays, 17:00 UTC / Noon ET / 9:00 PT. 

{{Note | If you haven't already done so, please volunteer to scribe. }}

==Telcon Info==

'''Zakim Bridge:''' +1.617.761.6200

'''Conference code:''' 3627 ("DOCS") 

'''VOIP:'''  sip:zakim@w3.org

==Agenda 2013-03-08==

* Roll call
* Review of open action items
* [http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone CSS Properties project]
** What are the next steps for this project?
* Topic vs. Topic Clusters?
* Translation task force?
* Filling out the taxonomy of the site 
** Generate a site map of the current site
** Identify what pages should be there that aren't
** Stub in those pages with details on priority, etc.
* URLs for translation
** What can we tell translators now?
*** Why can't we do ..wiki/lang/.. now?
** Should we have a task force?
* Fix Search
** Duplicate pages in results
** Crawl/index WPD: pages for help
* Session bug?
* Dabblet?
* Community outreach task force
** Press kit?
*** Brief recap of [[WPD:Community/Survey/Verbatims|Verbatims]] and [[WPD:Community/Survey/Doc_Sprint/Berlin_2-2013|Survey]].
*** Consider dates for next Doc Sprint.
* Analytics task force
** Getting together in the next week
* Content questions:
** How can we get a seal of approval from the community? Can SME review content?
** What is the criteria for calling something complete?
** What is the announcement plan to promote completed content?
* Anything blocking you from creating great content?
* Any new or notable content to promote?

==Agenda 2013-03-01==

* Roll call
* Review of open action items
* [http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone CSS Properties project]
** What are the next steps for this project?
* DocSprints
** How was w3cconf DocSprint @ Adobe?
** Next DocSprint?
* Session bug status?
* Bug Genie status?
* Dabblet status?
* New task forces
** Communications and recruiting
** Analytics
** Reporting back to this meeting?
* Anything blocking you from creating great content?
* Any new or notable content to promote?


==Agenda 2013-02-15==


* Roll call
* Review of open action items
* [http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone CSS Properties status]
** How did the testing go? Were folks able to create property pages?
** Do we want to do some sort of review? How?
** How shall we divy up the remaining properties?
** What are the next steps for this project?
* w3cconf DocSprint @ Adobe
** Who's going? (Shepazu, Craig, Eliot, Julee maybe Peter)
** What should we focus on?
* Session bug status?
* Bug Genie
* Webplatform preso for w3cconf
* Anything blocking you from creating great content?
* Any new or notable content to promote?

===Summary===

====CARRIED OVER FROM LAST WEEK====

1. ACTION (carried forward): shepazu + denis to implement sitemap extension
* Carried forward again
2. ACTION (carried forward): Alex to sort out updating the CSS properties template to reflect Mike S's Gold standard CSS property page
* Carried forward again
3. ACTION (carried forward): others should try to implement a CSS property page, and use chrismills' instructions when they are finished
* Finished
4. ACTION (carried forward): determine a set of properties we know to be complex outliers
* Finished
5. ACTION: JULEE to send out email to public list to get input regarding spec status
* Finished
6. ACTION: Shepazu to investigate cloud infrastructure and latency as possible roots of session bug
* Investigated with help from HP Cloud people, no resolution as yet. Ongoing.
7. ACTION: chrismills: recruit more participants to css properties project, augmenting tracking spreadsheet, actively tracking progress
* Ongoing. Has invited one person to take part (Rachel Andrew), who agreed to help out.

====NEW ACTIONS FOR THIS WEEK====

* ACTION: chrismills, make google spreadsheet just show p0-p2, css properties
* ACTION: chrismills: pull together 10-15 good CSS example pages and mail them around. People from different companies will then send these example pages to their resident CSS spec gurus, e.g Tab Atkins, Fantasai, Howcome, etc. and see what they think, as well as real world CSS gurus, e.g. Rachel Andrew, Chris Coyier, Peter Gasston, Dan Cederholm, Ethan Marcotte, Nicole Sullivan (their needs will be different.)
* ACTION: all, give Doug suggestions on what to add to WPD session him and Janet are doing at W3Conf
* ACTION: Scott to spruce up the APIs landing page

==Agenda 2013-02-01==

* Roll call
* Review of open action items
* [http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone CSS Properties status]
** Exemplar and instructions are completed; 5 folks are testing the workflow.
** [https://www.w3.org/Bugs/Public/buglist.cgi?query_format=specific&order=relevance%20desc&bug_status=__open__&product=webplatform.org&content=session&list_id=4654 Session bug] was a blocker. Ryan tried to resolve the issue. Observations?
** Spec status values should be resolved. Lea brings up a good point: maybe we should be calling it "browser support". [https://www.w3.org/Bugs/Public/show_bug.cgi?id=20386 20386] [https://www.w3.org/Bugs/Public/show_bug.cgi?id=18896 18896]
* Dealing with browser compat info — it is hard and time consuming; can we automate it? See mail from Doug May: http://lists.w3.org/Archives/Public/public-webplatform/2013Feb/0002.html. See also: http://docs.webplatform.org/wiki/WPD:Compatibility_Info
* Analytics?
* Attracting contributors:
** Session bug needs resolving
** Getting started experience validated via usability study @ DocSprint Berlin
** Communications on blogs picking up
** Additional plans?
* Anything blocking you from creating great content?
* Any new or notable content to promote? Does someone want to write up a blog post for Web Audio API?

===Topics===

* TOPIC: CSS Properties project status
** SUBTOPIC: spec status value on exemplar page.
*** http://docs.webplatform.org/wiki/css/properties/font-size
*** https://www.w3.org/Bugs/Public/show_bug.cgi?id=20386
*** font-style property page spec status: values are not usable; bug filed; considering different values than those of W3C
*** How to represent feature status so visitor knows whether it's in most browsers? Production-ready?
*** Community does need to know the status so it can participate. Need to bring the community in the standard development process; need to know if a spec is in "last call" or what, so the community can know whether/how to participate.
*** Should we add information about level of usability? Providing both values? Should we move this info to the bottom of the page? Near compatibility? Or should it stay up top for easy identification? Maybe an easy flag up top with details below?
*** html5please.com was offered up as a site that does it well: http://html5please.com/#gradients
** ACTION: JULEE to send out email to public list to get input.
** SUBTOPIC: The dreaded SESSION BUG!!! (Bug#19914). Memcache fix does not appear to solve the problem. It might be cloud infrastructure issue.
** ACTION: Shepazu to investigate cloud infrastructure and latency
** SUBTOPIC: recruiting participants for CSS properties project
*** ACTION: cmills: recruit more participants to css properties project, augmenting tracking spreadsheet, actively tracking progress
* TOPIC: Doug May has a way of dealing with browser compat info — it is hard and time consuming; can we automate it? See mail from Doug May: http://lists.w3.org/Archives/Public/public-webplatform/2013Feb/0002.html. See also: http://docs.webplatform.org/wiki/WPD:Compatibility_Info
** shepazu: idea: to update compat from different sources: quirksmode, caniuse, w3c test suites/test the web forward and auto-generate from that
** Doug May is investigating data-tree based solution to assess the suitability of data point, then refine algorithm for data retrieval that includes human-intervention provision.
* ACTION: Doug May and Chris to collaborate on solution in Berlin, and hopefully define a solution for SF doc sprint.
* TOPIC: Analytics?
** What is the current status of work on analytics? Site traffic, usage, etc.
http://docs.webplatform.org/wiki/Special:Statistics
* ACTION: Julee to call for participation/leadership on e-mail. [DONE]
* TOPIC: Recruiting experts and editors.
** Cmills is working on recruiting CSS experts, get them to contribute.
* ACTION: cmills: to contact university lecturers on garnering participation of college students.
** shepazu: maybe we could do college campus doc sprints
** shepazu: wary of unleashing this ahead of site estabilshment, Julee seconds
** Craig: need to improve the Getting Started workflows, 
need to identify content areas of priority, focus on areas that provide sense of satisfaction
** shepazu: would like to prioritize blog posts around content that is usable, current
** shepazu: use the blog software to draft, instead of e-mails
* Motion to establish a working group to investigate, develop communications plan
* ACTION: Scott to focus survey on doc sprints
* ACTION: Julee: to mail calling for participation in communication/outreach working group:DONE
* ACTION: Eliot to start off-line thread around blog posting priorities, suitability
* TOPIC: New and notable activities on WPD?
** https://github.com/webplatform/Shortlinks - fr0zenice's shortlinks system for WPD


===ACTIONS===

* ACTION (carried forward): shepazu + denis to implement sitemap extension: Concerns about current solution viability; looking for alternate. 
* ACTION (carried forward): julee and garbee to look into installing meetbot: Garbee to try to work on it more on the weekend.
* ACTION (carried forward): Alex to sort out updating the CSS properties template to reflect Mike S's Gold standard CSS property page: IN PROGRESS, Alex to consult w frozenice on scope.
* ACTION (carried forward): others should try to implement a CSS property page, and use chrismills' instructions when they are finished: IN PROGRESS
* ACTION (carried forward): determine a set of properties we know to be complex outliers: in progress

* ACTION: JULEE to send out email to public list to get input regarding spec status:DONE
* ACTION: Shepazu to investigate cloud infrastructure and latency as possible roots of session bug
* ACTION: cmills: recruit more participants to css properties project, augmenting tracking spreadsheet, actively tracking progress



====Completed Actions====


* ACTION (carried forward): eliot to edit top level landing pages:DONE
* ACTION: Mike S to move his static font-size example into the appropriate Wiki page:DONE
* ACTION: Chris to finish writing a guide to implementing a CSS properties page:DONE
* ACTION: Mike to work out how to specify "dependant/dependency properties":DONE
* ACTION: Scott to add an instruction in the attribution template that says "hey - don't delete this or change this unless you have a really good reason":DONE
* ACTION: Doug, Denis, Lea, work on implementing first phase of Dabblet live coding examples:DONE


==Agenda 2013-01-25==

* Roll call
* Review of open action items
* [http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone CSS Properties milestones]
** Pick a few for folks to try out using Mike's example.
** Any volunteer to write up instructions based on Mike's gold standard?
* Attributions
* Status on code.webplatform.org?
* Moving from MediaWiki
* Status on "discoverability" [https://www.w3.org/Bugs/Public/show_bug.cgi?id=19401 Search Bug]
** Do we have an interim solution we can implement quickly & easily
** We're going to put a search box on the [https://www.w3.org/Bugs/Public/show_bug.cgi?id=19694 main page]
* Analytics
* Anything blocking you from creating great content?
* Any new or notable content to promote?

===Actions===

* ACTION: shepazu + denis to implement sitemap extension
* ACTION (carried forward): eliot to edit top level landing pages
* ACTION (carried forward): julee and garbee to look into installing meetbot
* ACTION: Alex to sort out updating the CSS properties template to reflect Mike S's Gold standard CSS property page
* ACTION: Mike S to move his static font-size example into the appropriate Wiki page
* ACTION: Chris to finish writing a guide to implementing a CSS properties page
* ACTION: others should try to implement a CSS property page, and use chrismills' instructions when they are finished
* ACTION: determine a set of properties we know to be complex outliers, and make sure they fit with Mike's scheme, for example background-image (with radial gradient, linear gradient, etc) perspective transforms with multiple values set (crazy: transforms take any # of functions & assume defaults; "filter" prop takes functions in sequence) properties that don't have any effect unless another property is set. So for example, top, left, bottom, right don't have any effect unless you already set position: relative or position: absolute, flex and order do not have an effect unless display: flex is set properties that are proprietary and are only ever used with -ms- or -webkit-, for example
* ACTION: Mike to work out how to specify "dependant/dependency properties"
* ACTION: Scott to add an instruction in the attribution template that says "hey - don't delete this or change this unless you have a really good reason"
* ACTION: Doug, Denis, Lea, work on implementing first phase of Dabblet live coding examples
* ACTION: Doug to get together a task force to continue investigating an alternative to MW for our platform


==Agenda 2013-01-17==


* Roll call
* Review of open action items
* Status on code.webplatform.org?
* [http://docs.webplatform.org/wiki/WPD:Proposals/api_docs Scott's API proposal] ([http://lists.w3.org/Archives/Public/public-webplatform/2013Jan/0069.html See thread.])
* [http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone CSS Properties milestones].
* Status from Chris Mills: "I made loads of progress on filling in  the master CSS properties list today, building on top of Alex's great work. I'll try to finish this list tomorrow."
* Status on "discoverability"
** [https://www.w3.org/Bugs/Public/show_bug.cgi?id=19401 Search]
*** Do we have an interim solution we can implement quickly & easily
*** We're going to put a search box on the [https://www.w3.org/Bugs/Public/show_bug.cgi?id=19694 main page]
** Global nav
** In-context ToCs
* Anything blocking you from creating great content?
* Any new or notable content to promote?
* Need a new time for this meeting?

===Meeting Summary===

* Several folks weren't available to discuss open issues and action items. 
* We talked about a Table of Contents or nav at the top of articles. There was a TOC in the skin, and also one based on a user preference. They conflicted, so we took it out of the skin but if no users have set the preference to show it, we could bring the skin TOC back. But the default ToC was ever styled since
someone had a plugin they wanted to use.
* We are planning blog posts on Audio API and CSS regions
* Janet is going to FOSDEM. Anyone else?
* CSS properties proposal: about 2/3 thru prioritization of properties. Goal is to finish tomorrow, and work on a "representative" article. Then we need to create an author's guide based on the representative article. The property worked on previously was 'font-size'. Mike Sierra to work on making a "gold standard" example page, that others can use as a model. http://docs.webplatform.org/wiki/css/properties/font-size

===Actions===
ACTION: Julee to send out a Doodle poll to figure out a better time. [Done]
ACTION: Mike Sierra to work on making a "gold standard" example page, that others can use as a model. [DONE]
LAST WEEK ACTION: Julee to update Topic Hierarchy and Architecture pages. UPDATE: need site map
LAST WEEK ACTION: Eliot to do an editorial pass on the proposed top-level pages. 
LAST WEEK ACTION: Julee to set up meetbot. UPDATE: Garbee now has action item.

==Agenda 2013-01-10==

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