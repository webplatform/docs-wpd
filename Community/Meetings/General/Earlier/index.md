==Earlier Web Platform general status meeting==

For the most recent notes on the webplatform.org general status meetings, go to [[WPD:Community/Meetings/General]].
==Agenda 2013-04-26==

* Roll call
* Review of open action items.
* Appearance of content flags.
: Limited, but pointed feedback (from doc sprinters, others) suggests that these may be a deterrent to editing content. Consider toning them down?
* [[WPD:Projects/DOM_API_docs|DOM API Doc Reorganization Proposal]].
* Task forces reporting back to this general meeting.
* Anything blocking you from creating great content?
* Any new or notable content to promote?

==DISCUSSION==

===TOPIC: Appearance of content flags===

Limited, but pointed feedback (from doc sprinters, others) suggests red flags may be a deterrent to editing content. Consider toning them down?

... it's a bit "boy who cried wolf"

Should the meaning of flags be explained more explicitly when being set and viewed?

Some of them should be stronger than others

being able to change the priorities/visibility, and actions that are obvious from them

ideally, stub should be more inviting, for example

Back at the beginning, the plan was to display them differently to signed in vs signed out people

Also, flag banner is broken: http://docs.webplatform.org/wiki/html/elements/!DOCTYPE

[agreement that this is something to fix]


For beta, clear visual representation that this page is considered Beta-ready or not, we won't be able to touch all of the pages for beta

That's especially important given that some parts of site will be ready to be called beta before others

Could just have a banner that says "flags associated" or "this article is not beta ready", and when you go down to the _bottom_ it shows the flags

If you look at the compat table's output, when you mouse over it shows one thing for all mobiles; then when you mouse over it shows details

Also, I think a simple tooltip for explanation of flags (on hover) would be sufficient, maybe have popup appear on mobile devices
but something like that that says "there are flags on this page" and when you hover over see the specific ones

vs going to a whole separate page

... also we haven't done a great job of encouraging a culture of using flags

... we need to work those flagged pages back into the work flow

Making each flag a call to action could help

I think a tooltip explanation on the page whee it happens and a longer explanation linked from the editing page, where you set the flags would work

... comments thing was also supposed to help with flagging

... we want the comments thing to plug in to the issue tracker. Ideally the flags would go into the issue tracker

... ideally on the page you check off, I've done this, it hits the API to issue tracker and says "this action ahs been done"


A lot of work, but there could be phases to it. If we can get the current UI to reflect the call to action


and then later on hook up to project tracking


My original ideas was to have them discrete and off to the sdie

... right now they're a banner at the top of most pages


Also, if you could be clear about what the workflow should be

... in other words, contributor goes to edit the page, see one banner, they click on that, then they see all flags as calls to action...


===Topic: DOM API reorganization proposal===

http://docs.webplatform.org/wiki/WPD:Projects/DOM_API_docs

Adopted with the following discussion:

Want to make sure it's predictable and avoids conflicts
Follow basic object hierachy but flatten it out

Shepazu provided one example of proper DOM hierarchy:

http://objjob.phrogz.net/

that lets you drill around all around everywhere within the DOM. I had a vision that all of these things would be interlinked

URL schema for DOM API and visual representation of the DOM don't have to be the same thing. There's a lot of depth to the DOM that users don't need exposure to when they're coding. There are two use cases. The one we're solving for primarily is to figure out what a particular method does--they don't care about where it is in the dom tree. But that would address the other use case of exploring

We should have a widget that allows you to explore the particular object and its hierarchy as a UI element as opposed to a URL element

Are these two problems: 1) URL hierarchy 2) rendering of content to readers?


It's about 1200 pages tagged as DOM. And you need to be an admin to do moves


We should have a big push where we move the pages.

Fr0zenice might know if there's an extension


dunno, but the "move only for admins" thing was never really implemented btw

We don't want to lose this idea of a visual representation of the DOM. something we could point to as a differentiator. Because there's no good place to see that today

What we're documenting here is one ideal reference implementation of all the specs and we can show that to you in this visual way

We do want our work on web platform to help people working on standards

Not in URL structure, but in a separate experience

===Topic:  Task force statuses===

====Community Development====

we firmed up out plans for upcoming doc sprints


Any updates to any of the events should be reflected on the [[WPD:Community/Community_Events|events page]].

shepazu's great idea : have a non-political description of DRM and DNT, have technical articles about those and make a blog post.

... the TECHNICAL aspect, not political, social, or standardization aspect

and the ancillary idea was: we have an alpha banner, but we don't have anything about the campaigns we're working on (like CSS properties)

... when we have a push, we should highlight them in the banner

Redesiging the notice so it's not quite so ugly and what our current call to action

So, we have the blog, but do we also need a News or Current Events page linked to from the home page?

More controversial topics might get more vandalism, we'll need to be vigilant.

And we'll want to make it clear we're trying to just be about TECHNICAL aspects.

Have a disclaimer, if you want to discuss social aspects, here are some links for you to go to to do that


the blog entry where we say "we realize these are controversial, this is the role we're trying to play"

===TOPIC: Status of CSS properties project===

We're stalled on contributors to content. Not too much to review compared to content we need to create

We might need to broaden our base to get more contributors

===TOPIC: compatibility tables===
http://docs.webplatform.org/wiki/WPD:Compatibility_Info


There's a disconnect between pages that we have and granularity of caniuse data

If we're going to replace our existing compat tables, we'll need to do so comprehensively.

MOzilla agreed that we can crawl MDN's compat information, as this is public domain content. They agreed that we can use this data, and are not required to mark it as their _license_, although of course we'll say we got the info from them.

Shepazu is working on a script to extract data from them, merge with caniuse

If there's a test missing, then we'll provide a simple interface for folks to provide one, or at least some input.

if you see something missing, if you want to give the test to help with that
it will take them to a thing to let them contribute a test

That's huge overhead, will discourage contributions.

But how will we know it's good if they just make an assertion?


We can have a way to put in unverified information, but it should be tagged that it needs tests



==ACTION ITEMS==

* julee to email project leads inviting them to Monday's meeting. (DONE)
* pending Alex's amazing, insightful review of the DOM API proposal, Scott to begin implementing (DONE)
* Julee to file a bug to get a visual representation of the DOM hierarchy (DONE: http://project.webplatform.org/content/issues/46)
* Julee to add CSS properties recruting to communications meeting (DONE)
* shepazu to propose concrete proposal on compat info to list once it's done (ON-GOING)
* shepazu to e-mail ML about latest plans for talk.webplatform.org (CARRY FORWARD)
* leaverou: to talk with Chris Coyier regarding reviewing css properties template. (CARRY FORWARD)
* leaverou: will follow up with Denis where global nav didn't get implemented. (CARRY FORWARD)
* shepazu to work with lea to mock up what the improved flags will look like (CARRY FORWARD)

==Agenda 2013-04-19==

* Roll call
* Review of open action items
* Task forces reporting back to this general meeting:
** Community
** Analytics
** Program Management
* Anyone want to share any status on any project? Can we get completion dates?
* Review proposed URL/structure of [[WPD:Projects/DOM_API_docs|DOM API docs]].
* Has anyone seen the Evil Session Bug lately?
* When you tweet, don't forget to check conversation for follow-up!
* Anything blocking you from creating great content?
* Any new or notable content to promote?

==DISCUSSION==

===TOPIC: CSS Properties reviewers===

Doug and Chris Mills commented. Maybe have design experts join in, but unclear if they were to be SME to review content or the design of the pages.
we did a couple of rounds on the template.

We did another round in January, so I don't think we need to review the design further. Does anyone else?

Lea's been good about finding optimizations and fixing problems.

Joanie Rustalkin who helped design said we could contact her. She'd be an obvious choice.
But let's not revisit design of the template.

The idea was to get feedback on the content. But Lea can review design and discuss with other designers, such as Chris Coyier.

===TOPIC: Compatibility tables===

May be able to pull in data for mobile, too. http://mobilehtml5.org/ http://firt.mobi/about.php

Any others?

http://html5test.com/results/desktop.html
Their methodology did not--ironically-seem test-based. Shepazu to 
contact them anyway.

===TOPIC: TF updates:===

====Community====

had a meeting last week

university outreach: established a spreadsheet. Will list contact there, but we won't make that public.

We will invite people to contribute to that list.
[
We're considering doc sprints. Still working on that.

Established a regular meeting time. Tuesdays at 10am Pacific time.

If we have an agenda, we'll use the time. Otherwise cancel instance.
====Analytics====

Topic clusters.

Setting up a human readable site map.
We'll track campaign and emails.

 Before any doc sprint, need to set up a campaign.

Our SEO: Setting it up. Next step is to optimize the content. We have this tracked in Bug Genie.

==== Program Management====

Meetings 11am Pacific time on Mondays.

Triaging bugs and gathering information about the state of the beta work.

This week we asked people to take ownership of the different project buckets. Owners will define the deliverables and build a time, triaging issues, reporting back to the PM group on progress towards beta.

We also talked about BugGenie and how to get reporting done ACROSS projects.

Hopefully, we can get away from meetings and get a dashboard look at status.

===TOPIC: URL structure DOM, JS, and topic clusters===

URL/structure of DOM API docs.

http://docs.webplatform.org/wiki/WPD:Projects/DOM_API_docs

follows the same scheme as API docs, but without the API listing pages that describe the common names. Since the common name for all of these is DOM.

Doesn't affect how we're going to deal with the JS docs from Microsoft.

scottrowe: If folks would review that, it'd be great. I added some more info.

You coulld make a case that everything's in the DOM, but that wouldn't help people delineate anything from DOM down.

We've done that in our top level buckets , and now we're isolating a subgroup of the DOM and calling that the DOM APIs.

.They're the interfaces and objects you use when interfacing with the object model. I can make it clearer in the proposal, but I thought that was an established methodology.

this came up earlier, and I hashed it out with some architects. We couldn't come up with a sensible way of doing an alternate view. Scott's proposal is widely accepted.

We still need to have some kind of instruction--even visual representation--of the DOm, interfaces, JS, etc.
That might be an article, so then we could explain why we put things places.

We haven't talked a lot about interlinking between articles and we should look at that a lot.

We should cross-reference related things. MediaWiki doesn't make it as easy as a dedicated documentation CMS, but.

We'd talked about topic clusters as doing this.

There's an issue filed. Let's use that to discuss this.

There may be a passive-aggressive way to make them enter links: topic cluster UI based on links within doc, so if you don't have links, your topic cluster doesn't look right.

http://project.webplatform.org/content/issues/42

===TOPIC: Session Bug===

MIA Close it!

===TOPIC: Watch channel after tweeting===

When you tweet, don't forget to check conversation for follow-up!

===TOPIC: blogging about new SVG articles===

julee: I think Mike Sierra has moved to something else at Adobe. Finished out a bunch of SVG work. HTML5 weekly mentioned the articles.

===TOPIC: table styles===

In some pages, there are tables without a class to target. If I style all tables inside the container, it'll have unforseen effects. 
Regarding the font, I am fine changing it. PErsonally, I think bitter looks better.
Is there an automated way to add a class to tables that don't have one?

A lot of tables were generated by authors and some use the pipe hack, so there are some issues with tables we generated.

==ACTION ITEMS==

•	leaverou: to talk with Chris Coyier regarding reviewing css properties template. (STATUS: Lea is at a conference right now, and will be mentioning WPD explicitly)
•	leaverou: will follow up with Denis where global nav didn't get implemented. (STATUS: carried forward)
•	shepazu: change the messaging on talk.webplatform.org. (STATUS: not sure that changing messaging is the right thing at this point. Shepazu to send an e-mail to ML)
•	Patrick: to give us optimal day and time to launch a blog post. (DONE)
•	Analytics TF: set up page optimization in the next two weeks. (likely won't happen right now, it's ongoing)
•	Project area leads: join next week's call so we can define what it means to be head of a task force. (STATUS: Meeting didn't happen, due to zakim snafu. Please join us next week.)

==Agenda 2013-04-12==

* Roll call
* Review of open action items
* April 3 Doc Sprint
** How was it?
* A lot of meetings next week
** Community
** Analytics
** Programming
* Closing out some items
** [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0121.html Forum dependencies] - completion date?
** [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0090.html Translation URL schema] (http://docs.webplatform.org/wiki/lang/es/Main_Page) - decision final?
** [http://project.webplatform.org/infrastructure/issues/1 Session bug] is gone again! Is this issue closed?
* Anyone want to share any status on any project? Can we get completion dates?
** CSS Properties project
*** Discuss sending out a "call for review"
** Project.* project
** Global nav project
** [http://project.webplatform.org/content/issues/41 Beginners guide] to web dev - Status from Chris: created all of the [[TEST:beginners|landing pages]] and writing updated text for the landing page
** Populating news email list with [[WPD:Projects/Communications/Universities|university contacts]]
*** Fellowships, interships, mentoring programs for students
*** Please gather university contacts to add to an announce email list
* Anything blocking you from creating great content?
* Any new or notable content to promote?

===Discussion===

====TOPIC: April 3 Doc Sprint====
It was great. Scott did a blog post about it.
====TOPIC: A lot of meetings next week====
We should confirm that these meetings are productive: resulting in getting work done. If not, we should review.
====TOPIC: Forums dependencies====
====TOPIC: *====
 
We want to [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0121.html close down forums], but we need to get some things done first. See dependencies: 

http://project.webplatform.org/content/issues/40

====TOPIC: Translation URL schema==== 
We came close to a decision on the URL schema for other languages:

http://docs.webplatform.org/wiki/lang/es/Main_Page

But shepazu said we rejected this many times before.

What we have now is almost the worst of both worlds. Bad design by W3C LOC experts, MW's auto URL schema isn't good, 
what we're doing now is bad for SEO.

Shepazu will follow up with Richard Ishida, W3C's internationalization and localization expert

====TOPIC: Session bug is gone again!====

People haven't seen it, but let's give it a little more time to test.
It was a token bug. There's a token that ID's the session, depending on the memcache. It wasn't able to find the session and the session was lost. Ryan removed single-signon, and changed the memcache server.

====TOPIC: CSS Properties project====
Discuss sending out a "call for review". See [
http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0148.html thread].

But what's the process? Is Julee the right person to send reviewers to? What does she then do? How do we handle comments, store them, deal with them after we get the review? Seems like we don't have any system. Do we have the list of pages to review?

We're talking about SME, we can just ask them to just to edit the page. We won't track what changes they're making. But, what if the change should be made across more pages? So our pages are consistent in org or style?

Also, do we have a golden standard? If folks want to talk about specific styles, it's in one location: the golden standard.
Is there a WPD voice? We added the golden standard to the top of the [https://docs.google.com/spreadsheet/ccc?key=0AkRs-
89PKiZpdE0xdm9Sb1ZvRW1ZRzMtWEdyU0Z4OEE spreadsheet].

Julee will work with SME to decide what pages they're going to review. If it's something global, they need to call that out and we need to fix it across the docs. 

SMEs are looking for whether he doc is technically accurate.
What we're asking them to determine if the article is "technically accurate?" We're not asking them to set the style of content.

So we do need to hand pick some pages to get SME feedback, but once they say a doc is good, that's good enough.

We're going to get different voices in a Wiki. But, maybe less so in reference docs. But the priorities are:

•	quality content
•	then i18l English
•	Then down the line comes the issue of voice.
So, the ref should be in active voice and some other things, but we shouldn't impose too much at the beginning. Not before we see how things evolve.

Let's have as little process as possible. This is our first major writing project, let's put the least process in the beginning and put checkpoints in place later.

We should make it clear that SMEs need to let us know if there's something global.

And the letter needs to say if they see something that should be fixed across pages, or if they see any problems, contact julee. Want to make it easy for the SMEs to give feedback but doesn't need an official process to make that happen.

shepazu: is concerned that we would make a call for review and problems that would cause them not to come back later. this is a push to a larger community than we've had, so we want them to feel satisfied.

Julee will send out an email clarifying process. 

====TOPIC: Project.* project====
Garbee writing instrux. Having a state view of the beta is a dependency on reporting progress. This can be accomplished with a master project bucket.

shepazu: julee & shepazu will follow up

====TOPIC: Global nav project====
The [http://project.webplatform.org/content/issues/14 global nav] has not been implemented consistently. Forums closing has a dependencies on this project.

Lea's out this week. She's going to point to WPD in her preso!


====TOPIC: Beginners guide to web dev====

Chris Mills created all of the landing pages and writing updated text for the landing page.

http://docs.webplatform.org/wiki/TEST:beginners

http://project.webplatform.org/content/issues/41

Note we have commenting on the issue page! Try to move discussion about implementation to project.* page.

====TOPIC: Populating news email list with university====

This is probably a comm & recruiting item. In the meantime, we're asking everyone to please gather university contacts to add to an announce email list.

ALSO: Fellowships, interships, mentoring programs for students: GSoC: we got rejected (explicitly not for documentation). But w3c did get approved. Shepazu will follow up.

Media Wiki has a mentoring program, can we add our project to their list? Julee will follow up.  (DONE)

====TOPIC: status of table styles====

Lea will incorporate scott's feedback.

====TOPIC: W3C WG====

W3C WG  is the week after next, may interfere with this meeting. Eliot and Shepazu will talk about presenting there.

====TOPIC: Compatibility tables project====

Shepazu has been working on extension with caniuse data; alexsis d. & ppk: quirks mode data is all HTML.

PPK will package this data. Shepazu is merging these data sets. We may use MDN data as a fallback for the gaps in the caniuse and quirksmode datasets.

Need to optimize with edge side includes (tell fastly to cache it as a special case) Fastly said we can do this.

Need to work out a process for manual customization? (Maybe just the open text field?)

Shooting for end of April to deploy on all ref pages.

====TOPIC: WPD AS PLUGIN==== 
Tom Ortega wants to participate by investigate building plugins for standard editors: to have WPD be a plugin for these IDE. Julee referred him to frozenice as an initial contact.

===ACTION ITEMS===

* shepazu will call in Richard Ishida, W3C's internationalization and localization expert (DONE)
* Julee to write a draft email outlining the process to use for CSS properties review as instructions for SMEs. (DONE http://project.webplatform.org/content/issues/43) 
* shepazu to follow up with Lea regarding global nav (http://project.webplatform.org/content/issues/14) (DONE)
* Julee to talk to ryan about this (DONE: Only GNOME project might apply. Pursuing as part of community & recruiting agenda.)
* shepazu to send out timeline for W3C GSoC (STATUS: We discussed during analytics that it probably wasn't the right)
* Eliot & shepazu to talk re: presenting at W3C WGs. (DONE: saw no follow up from julee or scottrowe. check your inboxes.)
* shepazu to work with PPK/Verio/Alexis Deveria on public-webplatform-tests@w3.org (ON-GOING: shepazu: will report back if there's anything to report.)

==Agenda 2013-03-29==

* Roll call
* Review of open action items
* Status on project.*?
* Program management meetings will be set up to:
** Derive a final list of deliverables.
** Get a schedule.
** Work out how the dev/qa/launch/communication cycle will go.
** Triage bugs.
* Please respond to [http://lists.w3.org/Archives/Public/public-webplatform/2013Mar/0315.html email] re: IRC hours and 
* Anyone want to share any status on any project?
** Lea updated www.* with new global nav, can we get docs.* updated?
** CSS Properties project
*** Sending out [http://lists.w3.org/Archives/Public/public-webplatform/2013Mar/0308.html emails] to Doc Sprint registrants to ask them to re-try getting started. Anticipating some will participate.
*** Any one else want to take on a few?
* Anything blocking you from creating great content?
* Any new or notable content to promote?
* Julee taking a personal day next Friday. Someone willing to run this meeting?

===DISCUSSIONS===

====TOPIC: hiring a scribe ====

shepazu proposes hiring a scribe
shepazu will report back with more information

====TOPIC: CSS properties project ====

ACTION (CARRIED OVER): shepazu to recruit volunteer reviewers from the public list for CSS WG [STATUS: Prepared email. Do we have a systematic way of processing feedback? See 2013-04-12 meeting notes, above, for discussion.]

ACTION: Julee to assign owners for properties after Doc Sprint.  (DONE)

shepazu started work on recruiting reviewers, wrote e-mail; consulted with Fantasai

ACTION: shepazu to send out e-mail with process/plan for tech reviewers

We would like to get spec authors more involved with the documentation, 
with the caveat that spec authors are not the ultimate responsible party, nor should beta criteria be dependent on spec author approval

====TOPIC: DOM API pages ====

ACTION: Content Task Force Lead [scottrowe_] should set up a meeting to talk about overall site organization and how we want to handle DOM API pages.

scottrowe_ volunteers to be CTL for DOM API pages, julee also volunteers

====TOPIC: Edit Dismissible Alpha ====

Scott's an admin, but can't change the alpha note on the main page.

ACTION: scottrowe_ to follow up with Alex about editing the dismissible message.

====TOPIC: Status on project.* ====

ACTION: shepazu and julee to coordinate with garbee on project buckets, testing  (DONE)

====TOPIC: Google Summer of Code ====

http://docs.webplatform.org/wiki/WPD:GSoC

browser compat API in the works; maybe POC next week

anyone can contribute to the GSoC proposal

Shepazu - will you also be working on http://mobilehtml5.org/ to be implemented through the compat API?

Millo, we're open to any data source that meets our criteria

====TOPIC: Please respond to email re: IRC hours====

ACTION: If folks don't respond to email, Julee to set up an IRC calendar page  (DONE)

====TOPIC: API Project almost done!====

Scott will send out email when it's done. 

====TOPIC: Custom error pages!====
Lea did the error pages!

http://www.webplatform.org/errors/404.html

http://www.webplatform.org/errors/images/numbers.html

====TOPIC: Bug Genie skinning====

http://project.webplatform.org/skin/issues/3

http://project.webplatform.org/prmg/issues/PRMG-10

===ACTION ITEMS===

* (CARRIED OVER): shepazu to recruit volunteer reviewers from the public list for CSS WG (STATUS: Prepared email. Do we have a systematic way of processing feedback? See 2013-04-15 meeting notes, above, for discussion.)
* Julee to assign owners for properties after Doc Sprint. (DONE)
* scottrowe_ to ping jkomoros about how to fix the dismissible alpha message (DONE)
* (CARRIED OVER): shepazu to send localization guide to public list (STATUS: Chris Mills now has this action item. Doug will bring in Richard Ishida, W3C's internationalization and localization expert)
* Lea to implement content/issues/14 on docs.* as well (STATUS: Lea's away this week)
* Julee set up CSS Properties project page with custom queries (Scott did this.)
* Analytics team to develop report of key analytics, leading indicators, share at general meeting regularly (STATUS: We got the sitemap! Otherwise, carry forward)
* shepazu to take point on next week's meeting, if there is a quorum (Meeting didn't have a quorum)
* Content Task Force Lead [scottrowe_] should set up a meeting to talk about overall site organization and how we want to handle DOM API pages.
* shepazu and julee to coordinate with garbee on project buckets, testing (IN PROGRESS: also programming meeting is next Wednesday)
* If folks don't respond to email, Julee to set up an IRC calendar page [[WPD:Editors_Guide/step_2_communicate_with_the_online_community#IRC_hours|IRC hangout hours on IRC page]] (DONE)

==Agenda 2013-03-22==

* Roll call
* Review of open action items
* Review [[WPD:Project_Status]] and related [[WPD:Proposals/Organizing_projects]]
* April 3 Doc Sprint
* Dealing with "issues". For each project, do we have:
** A lead and team members assigned? If not, do we have volunteers?
** Open issues assigned? If not, can we get a deadline for triaging all issues?
* 404 page, and other errors. - Lea volunteered to address these.
* Anyone want to share any status on any project?
** CSS Properties project
*** Going to CSSConf in FL in May? Do we want to plan on promoting this new content then?
* Anything blocking you from creating great content?
* Any new or notable content to promote?

===DISCUSSIONS===

====TOPIC: CSS properties====

We will have a CSS property guide (http://docs.webplatform.org/wiki/WPD:Proposals/CSS_Property_Milestone) for the upcoming doc sprint.

The last docsprint was successful with that. There are about 160 left, and only one docsprint coming up. So we need contributors and reviewers. 

====TOPIC: proposal vs. projects space====

Scott wants only 1 area. Does not see a difference between the two. 

====TOPIC: search====

Denis needs to confirm, but we might install a new extension based on Google search (temporarily)

====TOPIC: session bug====

[http://project.webplatform.org/infrastructure/issues/1 Issue #1] was reopened
[http://project.webplatform.org/infrastructure/issues/3 Issue #3, update error message] was closed
[http://project.webplatform.org/infrastructure/issues/2 Issue #2, page not refreshing] is not to be confused with [http://project.webplatform.org/infrastructure/issues/1 Issue #1]


Ryan Lane has identified this issue as an edit token issue. Excerpt from IRC of community mtg: 

Ryan_Lane: the memcache configuration we're using now is the new style available in mediawiki since 1.18. It's what's used in production at wikimedia, and it uses the pecl memcache client, rather than mediawiki's home brewed in-php support. 

Ryan_Lane: Are we still using the SSO plugin? And if so, do we still need it? It screws around with what's in memcache 

patrickdsouza: if someone could look into the logs and check julee's logins you could try reproducing the bug. 

julee: If user edits the page for a long time it is more likely to happen. 

Ryan_Lane: Are we still using the SSO plugin? And if so, do we still need it? It screws around with what's in memcache. 

Ryan_Lane: Are people actually logged out, or does it just say "a loss of session data" when trying to save an edit? 

julee: I just got this error: "Oops! We seem to have a conflict. Please try saving again. If it still does not work after 2 or 3 attempts, try logging out and logging back in." I knew I was going to get that error because I had my page open in edit mode for so long 

Ryan_Lane: that's not actually a session issue. That's an edit token issue. I'd need to see where the edit token is stored. I'd imagine memcache, but maybe not. I'm positive this could be fixed by ensuring logged in users always hit the same application server once they are logged in, but that's really just avoiding the real problem 

====TOPIC: 4/3 Doc Sprint====

Peter already has secured facilities and catering. It's at Google's offices in SFL:
* very much like previous doc sprints
* the big ticket item this time is CSS properties project, but other people should suggest other projects
* Scott to run new people through a getting started observe whether the getting started pages/workflow is working for people. 4 or 5 people .
* So many Doc Sprints in the Bay Area. We might really want to try to incorporate remote participation again.
* It starts at 9, but you can come early. I'll be there by 8, 8:30.
* We'll have schwag, a bunch of t-shirts

====TOPIC: Dom API====

A quick huddle to talk about overall site organization and how we want to handle DOM API pages. There are multiple ways to look at DOM. We want to entertain different viewpoints into the model, based on the way people experience it. We're not locked into a single hierarchy because this isn't a book. Only one URL structure, but maybe multiple views?

We may begin talk at Doc Sprint or Content project area lead will set a meeting to discuss.

====TOPIC: Dealing with "issues"====
A bunch of issues are sitting around. Let's get project owners and encourage triage and status on bugs, at the project level. Then these projects roll up in some way in summary.

Minimally, we should get all issues in bug genie assigned (something that bugzilla requires).

====TOPIC: 404 page====

Lea agreed to look into the UX for 404 pages. She will design and will request fine tuning of content. 
http://docs.webplatform.org/wiki/WPD:Projects/ErrorPages

====TOPIC: Code styles====

shepazu hid code markup styling because it were ugly, but leaverou restyled and brought back. She added Prism.js. Before, the code examples had an indication of what language they were in, but the markup wasn't in the format prism expected. So, leaverou wrote some code to transform to the right format, so we now have nicely highlighted ones! It only works on samples with a language set.

====TOPIC: Global navs====

leaverou implemented the bottom global content navs! She is also willing to take up [http://project.webplatform.org/content/issues/14 Issue #14]: 

===ACTION ITEMS===

ACTION (CARRIED OVER): EVERYONE:

* if you haven't been editing pages, can you volunteer to do a CSS property? that will get you used to editing the wiki and experiencing what our users are experiencing?
* also try to recruit one or two people to do some property pages.
* and if you could help me with the review process. If there are certain pages that should be reviewed by an expert, call them out to me.
* and if you have ideas of experts who would be good reviewers, let me know--we need a significant number of them before we can claim that the docs are good
* Use the new "needs review" tag to tag articles that need review

ACTION (CARRIED OVER): shepazu to recruit volunteer reviewers from the public list for CSS WG

ACTION (CARRIED OVER): shepazu to send localization guide to public list

ACTION (CARRIED OVER): Julee to call it out to the l18n folks to make sure it makes sense & add it to the Ed-Guide.  (Shepazu wants Richard I to be involved.)

ACTION: scottrowe, update the Proposals section to be Projects [DONE]

ACTION: Julee to send out Beta Plan decision to public list [DONE]

ACTION: Lea to implement content/issues/14

ACTION: Julee to update issue with URL that new links should point to. [DONE]

ACTION: Content Task Force Lead [TBD] should set up a meeting to talk about overall site organization and how we want to handle DOM API pages. 

ACTION: Julee to send out e-mail asking for a lead, at least temporarily, for each project area, so we can get bug triaged and some movement. [DONE]

==Agenda 2013-03-15==

* Roll call
* Review of open action items
* [http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone CSS Properties project]
** Volunteer to get pages written.
** Send Julee your recommendation for props that really should be reviewed & suggested experts.
** Pointer to APIs.
* Topic vs. Topic Clusters?
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
* Community development task force
** Press kit?
*** Brief recap of [[WPD:Community/Survey/Verbatims|Verbatims]] and [[WPD:Community/Survey/Doc_Sprint/Berlin_2-2013|Survey]].
*** Plan next Doc Sprint: April 3, 2013 in San Francisco at the Google office.
* Analytics task force
** Getting together in the next week
* Content-complete questions:
** How can we get a seal of approval from the community? Can SME review content?
** What is the criteria for calling something complete?
** What is the announcement plan to promote completed content?
* Anything blocking you from creating great content?
* Any new or notable content to promote?

===Discussion===

====TOPIC: CSS Properties====

ACTION: * everyone:

** if you haven't been editing pages, can you volunteer to do a CSS property? that will get you used to editing the wiki and experiencing what our users are experiencing?
** also try to recruit one or two people to do some property pages.
** and if you could help me with the review process. If there are certain pages that should be reviewed by an expert, call them out to me.
** and if you have ideas of experts who would be good reviewers, let me know--we need a significant number of them before we can claim that the docs are good
** Use the new "needs review" tag to tag articles that need review

ACTION: shepazu to reach out to public CSS WG list and ask for experts to review CSS pages

For the beginning, the webkit team will likely just need a stable URL scheme and that's it, so they can generate lists

Eliot said that, unfortunately, someone who was going to join the project won't be able to join due to personal reasons. looking for someone to take his place, but no great options at the moment

====TOPIC: Topic vs Topic Clusters====
scottrowe_ did docs on that. more usable and better-accessed during the getting started flow and editor's guide

====TOPIC: Taxonomy of the site====
We still want to generate a sitemap. Doug and I spoke about this over e-mail to the list. Doug is going to get Julee access so she can experiment with generating a sitemap.

ACTION: Denis to follow up with Julee about sitemap generation [DONE]

scottrowe_ has been looking into the DOM project in relation to the Shadow DOM documentation. He's trying to figure out how we should design our DOM API pages generally. He will propose the DOM project as next quarter's project, just like CSS was this quarter's project.

Let's focus on CSS properties first.

DOM organization & refactoring is a pre-beta criteria. Even if we could just settle how we're going to organize it, then we could have a solid beta presentation.

Coming up with a set of beta guidelines soon. It will include the DOM is part of the architecture of the site is a pre-beta criteria

Segment the site (E.g. css properties) getting to "beta" individually as their quality gets to the right level.

But make it clear what's beta and what isn't. Add visual cues to each section so the solid stuff looks solid, and placeholders look partly there.

And map out what ALL of the pages are and creating stubs. And that goes along with the sitemap that Julee's working on. And helps us not have to explain the new page flow to new contributors – they'll be pre-populated.

This conference is full, no more parties can be added.

ACTION: Shepazu to allocate more spaces in future calls

====TOPIC: URLs for translation====

Some concern over current URL naming schema. We have a page that writes up how to do this. It's not a great process, but it is possible. 

We should do one or more BoF sessions at the html5devcon, to generate buzz, invite folks to grapple with how to handle i18n, catch folks who can't make the sprint, help pack the sprint, etc.

We should address this now if we have volunteers who want to help out. 

ACTION: Shepazu to get richard ishia [sp?] comment on what a better solution will be. He's the W3C l18n expert

The localization guide isn;'t in the editor's guide.

ACTION: shepazu to send localization guide to public lis
ACTION: Julee to call it out to the l18n folks to make sure it makes sense (shepazu wanted to get Richard I involved...)

We will table the long-term solution for now

====TOPIC: Search====

Why we can't fix this part with duplicate results? the default search is bad for mediawiki. We thought we replaced it with Lucene.
With the advanced search you can already include WPD pages

ACTION: Denis and shepazu to talk about improving built-in search. (Did we replace default search with Lucene?) (Lea to shepazu: this might help: http://www.mediawiki.org/wiki/Extension:SphinxSearch)

====TOPIC: Session bug status====
Feedback from users: it's still happening.

Denis talked to fastly guys two weeks ago. He said to change something in the config of servers. But it must not have worked.

ACTION: Denis to continue debugging the session bug

====TOPIC: Taskforces====

Do we want to report status here, or just in project.webplatform.org?

We can subscribe to updates from task forces via project.webplatform.org

Also, cover highlights from the task teams in this weekly meeting.

=====SUBTOPIC: Community development task force=====

Not enough data from Feb 23rd DocSprint. Next DocSprint 4/3 around HTML5DevConf. They have on their conference webpage they have a signup for WPD. They have about 35 people signed up through EventBrite for conference website, and we have 70 or so on our site. 

Sync community TF goals with project planning.

ACTION: scottrowe_ to set up meeting about next doc sprint

There are young CS students who are interested in getting involved in community.

We are planning to have doc sprints on the east coast. One in Ohio this summer, and at least 2 doc sprints in NC (one in summer, one in fall) – NYC has been requested.

=====SUBTOPIC: Analytics task force=====

We're having our first meeting this week.

====TOPIC: Content completeness====

Now that we have project.webplatform.org, we'll build it into the workflow.

Promotion: Blog posts for even small new additions are great, but for big milestones, we should have more press outreach

ACTION: julee to follow up with garbee on how to do workflows and forms in BG  (DONE)

We talked yesterday about figuring out fields and milestones. Garbee has promised to document things about BG and has committed to do some videos. We may want to set up another session for other people.

====TOPIC: Any new or notable content to promote?====

Adobe gave us some of Mike Sierra's times. He created several articles, one on transforms that's quite good. He's currently working on SVG
I think that's notable and good to share. We've shared some of it and got a bunch of retweets. We should be more aggressive about tweeting out new batches of articles that we've created.

Also, for the last 6 months we've benefited from the participation of Dave Gash, a contractor at Google, worked on API pages and CSS properties. There are a handful more to do, then we should put together a comm plan for that content.

ACTION: shepazu to invite people to twitter account

Remember it's good to get a quick LGTM from someone in IRC for spelling, links, etc.

ACTION: peterlubbers to invite people to the Google+ admins

Folks are putting bylines on articles. That's appropriate for primary authors. It's a nice incentive.

perhaps we should have a clearer policy around author attribution or have a significant contributions page to highlight contributions? It's capture din MediaWiki, but not highlighted well.

publicity workflow -- it should be easy to rain kudos on a team member when they earn it

mozilla blog they have open badges 1.0 https://blog.mozilla.org/blog/2013/03/14/open_badges/


ACTION: Julee to add comm plan as a topic for the community taskforce. (DONE)

====TOPIC: Kuma====

Denis has been reviewing Kuma, made a local installation. So far, it's been easy to install. But he needs to figure out if it can be a good fit. Janet sent Denis some contacts, Kuma developers. They've been very helpful. This is background stuff, shouldn't affect any work going on. 

===Actions===

* Denis to follow up with Julee about sitemap generation [DONE]
* Shepazu to allocate more spaces in future community meeting calls [DONE]
* Shepazu to get richard ishia [sp?] comment on what a better solution will be. He's the W3C l18n expert [DEFERRED]
* Denis and shepazu to talk about improving built-in search. [Denis is working on this.]
* Denis to continue debugging the session bug [Denis is working on this.]
* scottrowe_ to set up meeting about next doc sprint [DONE – this meeting ;-) ]
* julee to follow up with garbee on how to do workflows and forms in BG [Garbee is working on this.]
* shepazu to invite people to twitter account  [DONE]
* peterlubbers to invite people to the Google+ admins  [DONE]
* Julee to add comm plan as a topic for the community taskforce  [DONE]



==Agenda 2013-03-08==

Meeting adjourned for lack of a quorum.

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
* template for the native JS objects?
* New task forces
** Communications and recruiting
** Analytics
** Reporting back to this meeting?
* Anything blocking you from creating great content?
* Any new or notable content to promote?

===Doc Sprints===

http://docs.webplatform.org/wiki/WPD:Community/Community_Events

* 2/23 DocSprint: attendance: 27; CSS Properties worked on: 23
* Possibility of next Docsprint at HTML5DevConf - Mid-April
* Possible Docsprint in Puget Sound Area Mid-April
* http://openhelpconference.com/


===Action items ===
* JULEE will work on getting a burndown together [DONE]
* Julee - Setup Analytics project at project.webplatform.org [DONE]
* Eliot: Follow up on getting documentation into Editing Guidelines for using codelet at DocSprints to do code examples [DONE] [[http://docs.webplatform.org/wiki/WPD:Manual_Of_Style/Sample_best_practices]]
* Julee to add agenda item for next week: Topic vs. Topic Clusters [DONE]
* Julee to add agenda item for next week: Getting SME to review content [DONE]

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
5. ACTION: JULEE to send out email to public list to get input regarding spec status  (DONE)
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
* ACTION: Julee: to mail calling for participation in communication/outreach working group  (DONE)
* ACTION: Eliot to start off-line thread around blog posting priorities, suitability
* TOPIC: New and notable activities on WPD?
** https://github.com/webplatform/Shortlinks - fr0zenice's shortlinks system for WPD


===ACTIONS===

* ACTION (carried forward): shepazu + denis to implement sitemap extension: Concerns about current solution viability; looking for alternate. 
* ACTION (carried forward): julee and garbee to look into installing meetbot: Garbee to try to work on it more on the weekend.  (DONE)
* ACTION (carried forward): Alex to sort out updating the CSS properties template to reflect Mike S's Gold standard CSS property page: IN PROGRESS, Alex to consult w frozenice on scope.
* ACTION (carried forward): others should try to implement a CSS property page, and use chrismills' instructions when they are finished: IN PROGRESS
* ACTION (carried forward): determine a set of properties we know to be complex outliers: in progress

* ACTION: JULEE to send out email to public list to get input regarding spec status  (DONE)
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
* ACTION (carried forward): eliot to edit top level landing pages [DONE]
* ACTION (carried forward): julee and garbee to look into installing meetbot  (DONE)
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
LAST WEEK ACTION: Eliot to do an editorial pass on the proposed top-level pages. [DONE]
LAST WEEK ACTION: Julee to set up meetbot. UPDATE: Garbee now has action item.  (DONE)

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
* ACTION: Julee and klick_ass to write up WPD blog post about Germany Doc Sprint.  (DONE)
* ACTION: Julee to send out Ed Guide outline.  (DONE)
* ACTION: Scott to work on usability of Ed Guide.
* LAST WEEK ACTION: Julee to update Topic Hierarchy and Architecture pages.  (DONE)
* LAST WEEK ACTION: Julee to send out an email discussing how we should "take" and re-assign bugs to even the work out more.  (DONE)
* LAST WEEK ACTION: Eliot to do an editorial pass on the proposed top-level pages. UPDATE: No status. now [DONE]
* LAST WEEK ACTION: Jswisher to request the next level of detail on the global nav and how the reader accesses the content types as well as the technology areas. UPDATE: Janet sent out the email.
* PREVIOUS ACTION: Julee to find out how to add a meeting bot to the Content TF Meeting.  (DONE)
* PREVIOUS ACTION: Julee to file a bug about the design of reference pages with a non-standard standardization status.  (DONE)
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
* Discussed top-level pages sent out by Chris. We generally thought Chris's [http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0172.html proposed pages] were excellent. Eliot volunteered to do an edit pass on the descriptions. [DONE]
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
* Eliot to do an editorial pass on the [http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0172.html proposed top-level pages]. [DONE]
* Jswisher to request the next level of detail on the global nav and how the reader accesses the content types as well as the technology areas.
* LAST WEEK ACTION: Julee to find out how to add a meeting bot to the Content TF Meeting.  (DONE)
** UPDATE: in progress
* LAST WEEK ACTION: Julee to file a bug about the design of reference pages with a non-standard standardization status.  (DONE)
** UPDATE: needs to be revised: Julee to file a UI bug about the design of reference pages with non-stable status, so that they look distinct.  (DONE)
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
* Julee to find out how to add a meeting bot to the Content TF Meeting.  (DONE)
* Julee to file a bug about the design of reference pages with a non-standard standardization status.  (DONE)
* Eliot to update bug 20227 with pointer to the style guide he wrote (DONE)
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