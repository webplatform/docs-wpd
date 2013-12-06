==Web Platform general status meeting==

Web Platform community meetings occur on Fridays, 16:00 UTC / Noon ET / 9:00 PT. 

{{Note | If you haven't already done so, please volunteer to scribe. }}

==Telcon Info==

'''Time:''' Fridays, 17:00 UTC / Noon ET / 9:00 PT. 

'''Zakim Bridge:''' +1.617.761.6200

'''Conference code:''' 3627 ("DOCS") 

'''VOIP:'''  sip:zakim@voip.w3.org

'''IRC Channel:''' webplatform-site
[irc://irc.freenode.net/webplatform-site irc]
[http://webchat.freenode.net/?channels=#webplatform-site webchat]

We recommend that you follow both the audio conference and the IRC chat.  For those without an audio connection, key updates are provided live on the IRC, courtesy of each week's volunteer scribe.

==Agenda 2013-12-06==

* Jen Simmons has a mock up of the HTML elements pages
* Max Polk has done the 3rd JS import
* Eliezer Bernart is on templates
* David Singer has proposed a WebVTT content project


==Agenda 2013-11-22==

* JS import
* HTML Elements
* CSS compatibility
* How was TPAC?
* Pointers to info about Universal Access
* Migration
* Dave's working on DOM re-org

===Raw meeting notes===

[[WPD:Community/Meetings/General/2013/1122_raw_mtg_notes]]

==Agenda 2013-11-08: Canceled due to lack of agenda==


==Agenda 2013-11-01==

* Jen Simmons
* TPAC
* CSS properties project
* Compatibility tables
* The next content project?
* Status on migration project
* Doug will be out the next two Fridays, should we meet anyway?

===Discussion===

julee, shepazu, peterlubbers, jswisher, scottrowe_, jensimmons, renoirb, eliot, patrickdsouza, eliezerb are all on the line or on IRC

scribenick: renoirb

====TOPIC: Jen Simmons is contracting====

Good news: Jen Simmons is going to work for at least 6 months or so, starting part time, she is a developer/designer. she is going to be part time for a few weeks and then be full time after she finished her other already planned arrangements.

Jen had a chance to talk with a few folks at Html5DevConf, at Google. A lot to work on. Jen is thinking she will work on usability issues and improve it as well as how to help contributors to contribute (making it easier). 

Doug believes we should prioritize usability to the users (i.e. not a contributor). we should have a conversation about those on the list. We need to prioritize.

====TOPIC: TPAC====

TPAC is W3C's annual "all hands" face-to-face meeting. Where we gather (almost) all the groups in a big conference. This year it is in Shenzhen, China. Renoir, Doug and Eliott will be there. Doug and Renoir be there between 11/9-17. Eliott: 11/10-16.

Renoir will be going around and learn with various working groups.  Granted to be on an offset time zone and will be there for emergencies and things that have to be done.

Renoir will also be organizing TPAC's "Lightnening talks" sub-event.

Doug will be presenting with Eliot about WPD at TPAC to raise awareness.

Doug is part of many working groups, and so will have limited availability.

Doug & Renoir will not be available for the next 2 General meetings, so Doug will provide Julee with status before the general meetings, so they can continue as needed.

ACTION: While at TPAC, Doug will convey status on all pending projects before Friday General Meetings.

====TOPIC: Migration====

Renoir has done a plan. http://docs.webplatform.org/wiki/WPD:Infrastructure/analysis/2013-Migrating_to_a_new_cloud_provider

The HP contract is over. Doug is going to ask HP for another extension & offer HP visibility (find better word later) on the fact they started the project with us

Dreamhost is enthusiastic to host for free our full environment, but their new system is not ready for us. They will provide a full (vanilla) OpenStack environment. They are providing us a Replication MySQL node to help the migration and testing. As soon as the OpS installation is ready, Renoir set up the full migration work.

The time line depends upon Dreamhost to provide the environment (a blocker). Once we have in control immediately, Renoir thinks it should take a few days, then testing, as described in the doc. But the time he can't say, a lot of search & replace, and then the test, and then the live db transfer is the longest time.

Renoir says he's ready, just waiting. Doug says Renoir already started the migration, that the migration is going started ASAP.

The css properties has a dependency on a stable site. That's why we need to know when the migration work is being done.

Renoirb wants to make it clear that we MUST have a clone of the full production/live environment as soon as possible. as when we make changes, we are working on the production and a simple mistake can impact stability, and a change should only be a run of a script been tested many times before being run on the live site.

ACTION: Doug will contact Dream host and get dates, today.

====TOPIC: Compatibility tables====

Ronald Mansveld is working on the data model so all contributing sites can provide content according to the model.

We then need to find a way to present to the users, and how mechanically to sync the data. Doug did contract [http://www.mediawiki.org/wiki/User:Aaron_Schulz Aaron Schulz] to prepare an utility to cache generated data, and thinks he's close to completion. But, since we might migrate away from MW. We do not need to have this data live. We just need to refresh the data, say, once per week.

We do not need an automated data at this time. Priority is to have the data available in a re-usable format and present within the wiki. Need to test (today) on the computability table.

We will disable editing the compatibility section. Julee suggested previously that if users find contrary data, they could submit an update (preferably test-driven, conforming to data model) to github. This community data source will then be one of the data sources. We might also find a way to plug to TestTheWebForward data.

Eliot request a mechanism to report an error or flag.

Phase one, however, is just to get some data into the css pages so we can get the css properties project out. We want to use MDN data first, and maybe caniuse.

Janet Swisher didn't know Ronald Mansveld was working on MDN data. If jswisher had known, she could have connected him with the right folks, she'll try and do so in the future. (jswisher confirmed that ronaldmasveld did talk to appropriate people at Mozilla London)

Doug believes we can finish Compatibility tables by the end of TPAC and possibly during it, should be at least in a working state and to test it. It would include not only the CSS properties, but be done across all features.

ACTION: Doug will confirm dates with Ronald Mansveld & Aaron Schulz today.

====TOPIC: CSS vs. Beta announcement ====

For the CSS properties project, Doug suggests we "Declare victory and go home"

There is a need for us to say thank you to the community. By mid-November, we will be in a moment where we can do so.

But as jkomoros said, we have 1 more chance to make a big splash. So, we shouldn't call this beta.

Questions: why have a beta? when is a good time to have a beta?

Maybe it isn't good to announce between thanksgiving & xmas. Let's give a status update and showing achievements, just announce round 1 of css properties. Then, find an appropriate time to announce a beta when we have enough "meat" to show off as we only have one shot.

We could make a big fanfare, a coming ceremony for the beta, but we might never come to a point where we are in a complete, final state as it is the nature of the subject of the project. But we're not close to a beta announcement right now. A beta launch needs to be to the same level of efforts as the launch announcement. It might not be sufficient to only announce the css properties as the beta. The beta should include more. We should carefully consider what we have to say and what we're going to. How we are going to frame this. This round 1 of the css properties edits will be one of many granular announcements.



We've been talking publically about CSS properties, that's what we should announce.

Many folks agreed.

Julee again mentioned that we need to have a timeline for the compatibility tables & migration, so we know when css properties can be launched. (See discussions & outstanding action items from previous meetings.)

(On the IRC, renoirb also suggests also this as a blog post: http://lists.w3.org/Archives/Public/public-webplatform/2013Oct/0148.html)

====TOPIC: Next content project====

We need to find what we work on during DocSprint and WPW.

JavaScript pages? 

What is the timeframe for the JavaScript import?

ACTION: Doug will contact Max Polk today.

Doug thinks we already have the script to import, so should make importing easy. It might take a week or so prior to make it work.

So, if JS is ready to import, do we want to assume that the next subject to be JavaScript?

Doug: (thinks) that we could have room to do two subject in the same time. Doug thinks we can get a limited set of people to contribute to JavaScript, and then have a larger pool of folks who could contribute to HTML pages.

Julee believes we do not have enough resources to manage two content projects at the same time.

Renoirb believes his community management dashboard would help.

ACTION: Julee to send out notes so more folks can comment on the next content project.

===ACTION ITEMS===

* While at TPAC, Doug will convey status on all pending projects before Friday General Meetings.
* Doug will contact Dream host and get dates, today.
* Doug will confirm dates with Ronald Mansveld & Aaron Schulz today.
* Julee to send out notes so more folks can comment on the next content project.
* Doug will contact Max Polk today.

==Agenda 2013-10-25: Canceled due to lack of quorum==

==Agenda 2013-10-18==

* CSS Properties Project
{|class="wikitable" style="text-align: center; width:50%"
! Status
! Number
|-
| done
| 257
|-
| In Progress (Dave)
| 3
|-
| Low Priority
| 105
|-
| Needs examples (clip-rule, Doug)
| 1
|-
| Obso/Deprec
| 28
|-
| Vivienne just took! (table-layout)
| 1
|-
| Grand Total
| 395
|} 

* CSS Properties Project
** clip-rule status, Doug?
** who will volunteer for table-layout?
** other dependencies?
*** compatibility tables
*** legacy MSDN samples, related pages, and syntax section?
*** flag simplification?
*** review from CSS experts, spec editors & rockstars?
*** launch plan?
*** should we migrate first?
* migration plan
* JS project plan
** Should we do a plan, including community management, after a post-mortem on the CSS properties project?
** A bulk of work gets done at Doc Sprints, should plan include proposing Doc Sprints on a regular basis to get a bunch of stuff done?
* WPD table at [http://html5devconf.com/ html5devconf] in SF: please volunteer
* Internal Doc Sprint to get landing page & other site organization cleared up?
* Doc-Sprint-In-A-Box, Piwik reporting: this is a job for the Cracker-Jack Analytics Team!
** A cogent set of steps for generating reports
** What metrics shall we report?
** Better UI for Piwik (presently unintelligible) - if possible
*** "Goals > Saves a Page" path makes no sense (what is this, some kind of mangled translation?)
*** What the heck is a "conversion?"
*** (I mean, really, sometimes this open-source stuff is incorrigible!)
* Doc Sprint, New York in December
** Pro: New York, baby!
** Con: We're not ready yet; let's get JavaScript imported and scoped first

===Discussion===

====TOPIC: CSS Properties Project====
Last night we had one property unowned but vivienne (who was at Zurich's docsprint) took it (yay!!!) she's great, from Jay's group what we have outstanding are a few properties that Dave is working on. We're not going to do an example for knockout. We created a correct syntax example, but put a larger example on hold. All of the remainders will get live code examples at code.webplatform.org. clip-rule example, Doug is working on. We should be done mid next week (Dave is out next Wed-Fri). [much rejoicing]
=====Subtopic: Dependency on compatibility tables =====
* compatibility tables: first one is compat tables lots of activity about that this week, shepazu provided an update: at the doc sprint in amsterdam, we got to gether with PPK (he's from quirksmode, obviously) he invited the guy who does html5test.com he's been doing something like caniuse for something like ten years they're test driven what we want to do with this project is have a single data model that captures browser compat/test results for as much as we can we have permission to use MDN data, and because they are facts, we don't HAVE to attribute that use (but we plan to give attribution, just not changing the license on the articles that include it) Max Firdman (sp?) from MobileHtml5 wants to help too http://mobilehtml5.org/ http://html5test.com/ shepazu has a running prototype of a mediawiki extension that inserts compat information but it's a naive implementation and would cause caching problems html5test.com source code: https://github.com/NielsLeenheer/html5test the page would be constantly changing so it wouldn't be able to be cached by CDN I'm working on another approach renoirb has good ideas on that I got renewed energy from several people a guy named Ronald Manzfeld (sp?) stepped up and said, "if you need some server-side help, I could help" he got really into the idea of making the unified data model he started on that and has a first draft available. Niels Leenheer, guy behind html5test.com PPK, NIls (HTML5Test) and others are all on a new list: public-webplatform test. Ronald has been very active, interested in driving things forward we're also going to provide an aPI so others can get it (same API we will use) I think within a couple of weeks we'll have at least something workable

Granularity is part of the data model at docsprint, we all kind of agreed that we like the way that MDN chose a good level of granularity. there are several kinds of granularity: per feature, per browser version we thought the MDN model was pretty good, so we'll start with that. if we don't have the right kind of granularity, we'll fall back to MDN which will also be good in terms of completeness. lik ecaniuse only tests things that are new and up and coming and MobileHTML5, his granularity is quite different from caniuse. We're going to try to categorize their broader categories and capture that at a diferent level of granularity.

public-webplatform-tests?

ACTION: shepazu to send link to the public-webplatform-test list to main list [DONE]


We'll do batch updates once a week or so the people who are involved in this (the data sources) are likely all amendable to changing their own data models a little bit. to make it easier to integrate one exception to the updates: probably won't pull from MDN very frequently probably a one time, given that there's not as good of an API there we'll have to come up with some tests for the tests to make sure our data retrieval kept the integrity of the system. This is great, especially having so many people pitching in with experience in this area. Hoping to complete by end of november at latest. 

Do we have a plan for if someone finds an error in the data on WPD?
The plan was to punt on that for now. Will expose our data on GitHub as well. we'll likely ask people (to start) to submit a PR wonders if we could have useful data from there http://www.chromestatus.com/features although of course ultimately we'll need to come up with an easy way to change it from our system probably not all that useful, but might be good for spot checking.
Could be a phased approach where for the 260 properties if we do an early import, even if it's just from one source so we could not wait too long. 
ACTION: shepazu Talk to Ronald about perhaps doing a phased compat table approach, where we just do one data source to start (in order to move faster)

what does a conteingency plan look like? if we run into problems with the extension I'm writing (I'm going to talk to trenoirb and ryanlane later today about that, by the way) one possible contingency is to make a script to use the API for MDN to pull out their compat information, and we write a script to inserts that compat information into our pages. not generate a new page, just edit the apges we have make sure it's not automatically generated at serve time. Even if it's not possible to fully automate, even if we can automate the hard parts, we might be able to make it feasible for a small number of volunteers to copy/paste/massage my point is mainly "just think scrappy" If full-automatic isn't easy, even semi-automatic is better than nothing.

=====Subtopic: Dependency on legacy MDN samples =====
Some residual sections were imported (especially code examples, related pages and syntax) automatically. we had talked with renoirb about doing a bulk find/replace operation if we can't do it by script, we can probably do it manually--just need some volunteers
Eliot: We're hoping to get confirmation today for a facilities reservation for University of Washington on 11/2 that sounds like a great project for students to tackle.
[murmurs of agreement]
if renoirb can run a script to at least identify pages that need this, that would be helpful, but he has a lot to tackle right now I have a lot of other things on my plate
scottrowe_: There's a lot on renoirb's plate, we should have a separate meeting to figure out prioritzation of infrastructure tassks
renoirb: For now my focus is on migration
ACTION: julee to write up bug (cc eliot) about investigating feasibility of finding pages that need old MSDN sections removed

=====Subtopic: Dependency on reviews by experts=====
Review by experts & get them thinking about the project so they're ready to talk about the launch when it happens. Two categories: spec experts, and rockstars the former is for shepazu, the latter is for jkomoros
ACTION: jkomoros to ask paul_irish to do a spot check of WPD CSS properties
=====Subtopic: Dependency on launch plan =====
jkomoros on that AI basic idea is a plan for a few weeks from now about blog post, who to get to support the launch.
ACTION: jkomoros to create strawman launch plan (including relative timeline)
What's the timeline?
The long pole is the compat tables for now so that will depend on information from that taskforce about if they can do a quick and dirty import.
So we're going to say we're dependent on that functionality, it's a good idea to have compat information, even if it's not the Super Awesome Amazing Automatic version
We might have a contingency plan for CSS properties, even if the SAAA version isn't ready yet so let's get feedback from compat table group, and base dates on that.

=====Subtopic: Dependency on migration=====

Doug earlier brought up: should we migrate before announcing? But says
"no." The new provider is getting prepped to beta, a feature we could use at the end of the month I told renoirb to consider migration as top priority. Ideally ryan can help with it as well
[09:41:14] Ryan_Lane nods
[09:41:14] <Ryan_Lane> I can
Since we're blocked on compat tables, at least starting the migration could be a good thing.
One question is: if we finish before migration, do we wait for migration/ slash, is there enough bandwidth to do compat tables and migration? renoirb will advise on compat tables, but the two work streams don't overlap TOO much but I'll verify with Ronald
ACTION: shepazu to verify with Ronald/renoirb that compat tables and migration work streams are independent.

Renoirb has a branch where I got less-and-less hardcoded configuration. Which is the main requirement to migrate. We can almost definitely do it without downtime.

The other question is the risk of the migration: Whether it will cause more problems. We're not not sure. We have a known "OK-not-great" solution now. The new solution is an unknown. We should COUNT on errors during migration. 
No matter what, after a migration we'd need to test. We have a hard stop with current provider so we need to work back from that key date. It would be nice to see what that timeline looks like--a couple of days, a couple of years--then we can map that against a timeline for releasing CSS properties project if we find that things like "announcing" are overlapping with "testing", it won't be good.
ACTION: shepazu to confirm date of contract expiration with current hosting provider
ACTION: julee to make basic timeline for completing CSS prop project;
ACTION: renorib to create basic timeline on migration

Then, we can see how they interact.

====TOPIC: JS project plan====
We could do a postmortem on CSS props project (even in email), figure out what worked and what didn't. Use that to inform a high-level plan of tackling JS project
Doc Sprints lead to TONS of work getting done so JS project plan should incorporate a schedule of doc sprints that different folks could volunteer to run.
About.com who is enthusiastic about JS topic in particular for their upcoming doc sprint.
JS plan should be ready by December. During November, we should prep for this.
ACTION: shepazue to work with Max Polk to make sure his migration is up to speed we got review from two different experts on the JS architecture
ACTION: shepazu to forward e-mails from JS experts about architecture on to list ideally we'd run through a few WPW sprints before the doc sprint to make sure we're ready for the doc sprint
WPW is an ongoing second tier to in person doc sprints so we should pay attention to that during planning.

====TOPIC: WPD table at HTML5DevConf====
Shepazu got a table for W3C at the HTML5DevConf in SF next week we have me, Rebecca Hauk manning table but we need more volunteers we have some shirts and stickers, but we could use more swag. Shepazu has 3 free tickets for volunteers.
We left a big pile of t-shirts in Amsertdam
====TOPIC: PiWik reports for Doc Sprints====
scottrowe_ looked into generating the PiWik reports about doc sprint played around for awhile, but there's no way to scale this. We need to make some decsiions about what reports we're going to generate and provide steps for doc sprint owners and fix some things about piwik user interface but we should defer to analytics meeting. 
====TOPIC: Google contractor!====
Alex will let us know if Google adds another contractor. Stay tuned…

===Action Items===


* shepazu to send link to the public-webplatform-test list to main list [DONE]
* shepazu Talk to Ronald about perhaps doing a phased compat table approach, where we just do one data source to start (in order to move faster)
* julee to write up bug (cc eliot) about investigating feasibility of finding pages that need old MSDN sections removed
* jkomoros to ask paul_irish to do a spot check of WPD CSS properties
* jkomoros to create strawman launch plan (including relative timeline)
* shepazu to verify with Ronald/renoirb that compat tables and migration work streams are independent.
* shepazu to confirm date of contract expiration with current hosting provider
* julee to make basic timeline for completing CSS prop project;
* renorib to create basic timeline on migration
* shepazu to work with Max Polk to make sure his migration is up to speed we got review from two different experts on the JS architecture
* shepazu to forward e-mails from JS experts about architecture on to list ideally we'd run through a few WPW sprints before the doc sprint to make sure we're ready for the doc sprint

==Agenda 2013-10-11: Canceled due to lack of quorum==

==Agenda 2013-10-04==

===Agenda===

* CSS Properties status
{|class="wikitable" style="text-align: center; width:50%"
!Status
!Number
|-
| done
| 209
|-
| In Progress
| 20
|-
| Low Priority
| 113
|-
| Needs Review
| 37
|-
| Obso/Deprec
| 8
|-
| TBD
| 60
|-
| Grand Total
| 447
|}
* site stability
* Doc Sprint in a Box
* WPD Birthday next Tue: list activities/URLs
* Change this meeting time/day?
* Anything else?

====Topic: CSS property status====
scottrowe_ emailed the list of 95 properties
… the coordinators should contact those people individually
… and if we can't get those people, we'll reassign them
http://docs.webplatform.org/wiki/WPD:Community/Meetings/General
while scott compiled the list of properties, Julee reconstructed a master list & categorized them according to status. She will put this in a google doc to manipulate it more easily
we should still have TBDs on the wiki, so people can sign up… and it's out of date

there are about 60 that need to be done, and 35 need review

====Topic: Doing experimental properties====

some have said we should only work on things that are not experimental, but there's value for us to do more cutting-edge stuff since we're closer to the development of the specs and implementations
also good for SEO
we need to be careful about updating examples
The idea we had in mind is a mechanism. Isn't going to happen in the next 6 months
for now maybe we could do this: W3C has a DB, with a unique URL for each spec, so we could come up with something where we are working off a draft version , script that trolls publications every day, sends an email w/ a list of specs that have changed, validated against URL
ACTION: shepazu & eliot to brainstorm w/ Robin at TPAC
====TOPIC: site stability====
Getting server & client-side errors on dabblet
Are we doing any stability testing?
ACTION: Renoir to write up his testing plan, and add all relevant systems to that plan, such as Dabblet instance
julee: we could also ask the community to help with testing
====Topic: Doc Sprint in a Box====
https://docs.google.com/document/d/1fIDssDZln2Z_DrnKliT1ymZpn_OTqdYA7rVgMaTsSk4/edit
ACTION: Millo to review doc sprint in a box, add some comments, and update it based on what we've learned internally

ACTION: scottrowe do an edit pass stripped down to its main purpose which is to have community members throw doc sprint
ACTION: scottrowe to share with Patrick D'Souza for review

====Topic: WPD Birthday next Tue: list activities/URLs====
doing it on OCtober 8 would be best, since it's the birthday, but we have no volunteers; maybe the WPD twitter account could be the lead, and eveyone else could retweet

scottrowe_ needs anecdotes, but I'll write the blog post
ACTION: Julee to forward Scott's email & get them to commit to tweet & point to the blog post. We looked very much on the same page 1 yr ago: we should look that way now.
ACTION: scottrowe_ will write the blog post, hopefully by Thursday.
====topic: Change this meeting time/day?====
ACTION: Julee to send a query email & ask if we should Change this meeting time/day?

===Action Items===
* shepazu & eliot to brainstorm w/ Robin at TPAC
* Renoir to write up his testing plan, and add all relevant systems to that plan, such as Dabblet instance
* Millo to review doc sprint in a box, add some comments, and update it based on what we've learned internally
* scottrowe do an edit pass stripped down to its main purpose which is to have community members throw doc sprint
* scottrowe to share with Patrick D'Souza for review
* Julee to forward Scott's email & get them to commit to tweet & point to the blog post. We looked very much on the same page 1 yr ago: we should look that way now.
* scottrowe_ will write the blog post, hopefully by Thursday.
* Julee to send a query email & ask if we should Change this meeting time/day?




==Agenda 2013-09-27==

===Agenda===

* Piwik and the Analytics is back on track!
** Analytics: Create a secret starting page that will help track activity during a doc sprint (TBD, probably next week)
** Analytics: Improve the goal tracking using Piwik's API and JavaScript
** Infra: Changing datacenter?
*  Doc-Sprint-In-A-Boxathon scheduled for next wednesday.
** Everyone is welcome to join, Patrick.
** Scott will send out a note.
** Goal is to have this done before the Amsterdam Doc Sprint, possibly even earlier.
* CSS properties tables

===Discussion===
====TOPIC:  PiWik/ Analytics====
Piwik and the Analytics are back on track. Two weeks ago Renoir deployed PiWik in a different way than before without going too deep, it was in the same way as before (Fastly), putting a different tracking code on all of the pages should have covered all of the pages, with the help of Patrick, create goals in the dashboard & campaigns. Now forwarding all of the e-mails to the analytics mailing list.
Julee & Eliot filed a bug and I responded to an earlier filed one that represents requirements for the dashboard. At the analytics meeting next week we could consolidate requirements and finalize that list. All bugs & discussion is on http://docs.webplatform.org/wiki/WPD:Requirements/Analytics
Renoirb gives a rough geolocation, might need to recrunch the database; some other work: a way to trigger conversions in the goals (like clicking on edit or save), will require adding JS if we get it in place before the docsprint, we can track progress. Scott_rowe will show up at next analytics meeting to discuss.
* ACTION: Scott_rowe to attend analytics meeting on Monday 4pm pdt
====TOPIC:  Infra: Changing datacenter?====
No news. Worked with Doug on that. Didn't get any feedback from anyone yet, but time is passing working to rebuild the VM from scratch as much as renoir can in the same environment.
We either need to move soon, or do the move next month
Still trying to connect up with Dreamhost and other folks
====TOPIC:  Doc-Sprint-In-A-Boxathon scheduled for next wednesday====
I asked Jay to take leadership of kicking this off I think that he is working on the general structure of the thing right now, Jay sent an e-mail about the timing, but also an e-mail from Scott and Peter where they had a draft docsprint in a box: a brain dump about all of the things we thought should be in there. Not intended to dictate the structure. just making sure that before the meeting we wrote down what we had learned from doing a few. Jay also had an idea of the structure he wanted.
* ACTION: scottrowe to send an e-mail to the list to invite anyone who's interested to get involved with the docsprint in a box I think Jay sent an invite to Patrick, but we should confirm
====TOPIC:  CSS properties tables====
We discussed how to manage the tables. Also, coordinators need to verify that each property they are coordinator for is properly reflected in table. Julee & Eliot have done this. Chris Mills, Shepazu & Nic d'Costa needs to do this. 
* ACTION: Julee to remind Nic & Doug to update their properties in the tables. [DONE]
* ACTION: ??? to contact Chris.
We discussed doing a script to import all properties into project.webplatform.org, but really the work is manual checking at this point.
https://scraperwiki.com/

Creating a JS project in the project tracker and populating it makes sense for when we start a new project, especially since we've fixed the sendmail time-out bug.

* ACTION: scottrowe_ and julee to work at creating a new list of unfinished CSS properties

===Action Items===
* Scott_rowe to attend analytics meeting on Monday 4pm pdt [STATUS: Everyone was a no-show. Will happen next Monday, instead.]
* scottrowe to send an e-mail to the list to invite anyone who's interested to get involved with the docsprint in a box I think Jay sent an invite to Patrick, but we should confirm  [DONE]
* Julee to remind Nic & Doug to update their properties in the tables. [DONE - Julee & scottrowe did them]
* ??? to contact Chris. [Resolved]
* scottrowe_ and julee to work at creating a new list of unfinished CSS properties  [DONE]


==Agenda 2013-09-20==

Objective: Describe the current state of the project.

Note, the objective does not include making any decisions or otherwise taking any actions other than those required to understand the state of the project. This should be a very short, concise meeting.

* WPW update - status?
** Have coordinators verified the status of each page in their purview?
** We need to consolidate the tables into a final master list of properties to be worked on, and we want to include only those properties still being worked.
* WPW reinvigoration - what do we need to do to put some life back into this?
** We've dropped to 50 active users/month.
** Are site performance problems a contributing factor?
* State of WPD for the birthday - what have we accomplished?
* Who's in for Amsterdam?
* Doc Sprint New York?
* We're out: print up some new t-shirts?
* Reminder: Doc Sprint in a Box, Oct. 2
* JavaScript import status?
* Compatibility automation status?
* Analytics & reporting?
* Back-end update from Renoir?
** Piwik enhancements in a nutshell
** Site performance - what are the problems and what is preventing solutions?
* Next week's blog post author
* Anything else?

==Agenda 2013-08-23==

* Roll call
* Review of open action items
* [[Meta:web_platform_wednesday|WPW]] - how is it going?
** [http://lists.w3.org/Archives/Public/public-webplatform/2013Aug/0146.html Additional properties to add to this project?]
* Anything blocking you from creating great content?
* Anything new & notable? (Blogs or other communications planned for next week?)

==Agenda 2013-08-16==

* Roll call
* Review of open action items
* [[Meta:web_platform_wednesday|WPW]] - how is it going?
** Schedule
** Who's coordinating?
** Action items cleanup: Please search for your name on this page.
* Infrastructure meetings
* Communications plan
* Anything blocking you from creating great content?
* Anything new & notable? (Blogs or other communications planned for next week?)

===Discussion===
====TOPIC: WPW - how is it going?====
julee: We have three coordinators, but no contributors. A lot of people are busy or on vacation. Originally we had an optimistic schedule to be done by august  after reviewing with a few folks, everyone thought that was way too optimistic  especially given summer vacation period. We will put in a buffer week after labor day, & add incomplete properties back onto the pile.
After the end of august, Microsoft will have some resources that we'll be adding to this  one of my writers will be helping, another writer who hasn't worked on this yet will be helping as well.
Google is working on a contractor as well, and scottrowe will be helping out with coordinating as well

Bumping up the boolean values for things like animated values in the CSS properties template, and also Inherited field. Maybe Frozenice can ?
ACTION: julee to reach out to frozenice assigning the "non-boolean properties for animatable, etc" template issue to him
====TOPIC:  Servers ====

shepazu: We'll be talking to dreamhost later  but ryan and renoirb think it's a good thing to have redundancy across hosts  renoir contacted a few different hosts including Digital Ocean and iWeb  the latter is based in Quebec  so renoirb can talk to them in 
shepazu: Dreamhost asctually wants to be involved in the project as a steward
<patrickdsouza1> renoirb: good to look at hosts in a different time zone like europe.
<renoirb> iWeb data center: http://iweb.com/green-data-centers
renoirb: I talked to them. The idea is a main one and another one that's latent, that we have a copy of everything; if we need to change we just flip a switch. Looked around for one with a good reptuation with multi site. iWeb's president is going to talk to us by Tuesday of next week
We need to have a different company/place to back up stuff on a regular basis, but if you have multiple instances across diffferent companies, you have a huge latency issue. Ryan_Lane has a preference towards openstack clouds, as its open source nature aligns well with our project  if dreamhost can provide us with the different locations/datacenters, then is the secondary company just a single backup instance? We will roll out redundancy as needed  the idea is to have redundancy between prod and test. Julee asked for an architecture document that describes our setup with a nice diagram, and references to justifing it.  

====TOPIC: Server status ====
Also, server status page (going to be on our own sub-domain for sure): http://webplatform.tumblr.com/

====TOPIC: Infrastructure meeting ====

At infrastructure meeting, most of the discussion was about how to prioritize renoirb's work schedule; we're going to use projects.webplatform.org. 
Once community has a decision, having execution focused meetings is helpful to add it into the issue tracker  (if there are issues that aren't recorded yet, we'll raise them there), executing on things that have already been decided in the community meetings or over e-mail on the list, taking the decisions from the group and parsing down into actionable things and track them in project.wwebplatofm.orgexposing it in the dashboards/reports, so the current health is viewable by anyone. Everyone is welcome at the infrastructure meeting, but because julee/shepazue/renoirb are full-time on this project, we'll take responsibility to keep track. 11am Pacific on Mondays, and we can move it if others want to attend regularly.


====TOPIC: Communications plan====
There's been so much activity, I want to have people talk about what they're doing
Renoirb got access to the social medial outlets, G+, twitter, FaceBook. Ideally we'd be able to automate publishing a post to all outlets, with a buffer system to space out updates too and space out updates on different channels. Updates should be scheduled to not only USA time but for those in Europe and the rest of the world  and the status tumblr, when something happens that we want to talk about, the conversation wil lgo to the tumblr status  regarding the policies, I think we should keep it the same: vendor neutral, information on status
eliots blog proposal : how & why we blog; we'll have an editorial calendar; start looking for repeating blog posts;
<nicdaCosta> with regards to tumblr and the new G+ community, is it necessary to have so many outlets? And would there be a given "purpose" for each outlet?
WPD calendar in g+ may not be sufficient for an editorial calendar

looking forward to seeing Coalie Mercier, from the W3C MarComm staff, her work & what she wants to do for the future
we need a regular voice
AI: R/S/J in project.wp.org, we could rename project community management; create tasks, give ownership, tag twitter, blogpost, whatever, infographics, etc.

===Action Items===

* CARRIED FORWARD: Everyone to review the general meeting notes for actions assigned to them that aren't marked "(DONE)" and update with status as described above. (Mostly done: Doug & Renoir to do.) (CARRY FORWARD)
* CARRIED FORWARD: shepazu make "can you tell if this page is ready for consumption or needs more work" an active question for css project reviewers. (CARRY FORWARD)
* CARRIED FORWARD: Julee make sure editing guide is updated with new flag values, when flags are done. (Has a dependency on flags being done) (CARRY FORWARD)
* CARRIED FORWARD: Alex to talk to Paul irish & other folks on the list that Eliot pointed him to (a list that we created at launch?) about reviewing "done" pages. (In progress: jkomoros talked to paulirish yesterday, who is in when needed; dependency on more content being done. Tracking this in the CSS Properties endgame schedule.)
* CARRIED FORWARD: shepazu to figure out how to move current flags to new flag types and cc jkomoros and frozenice. (CARRY FORWARD Tracking this in the CSS Properties endgame schedule.)
* shepazu to make sure Lea incorporated Chris Coyier's feeedback as appropriate.
* CARRY FORWARD: Shepazu & renoirb to review Lea's actions item and reassign and to reassign ownership of project.webplatform.org. (CARRIED FORWARD)
* R/S/J in project.wp.org, we could rename project community management; create tasks, give ownership, tag twitter, blogpost, whatever, infographics, etc.

==Agenda 2013-08-09 Meeting canceled due to lack of agenda==

==Agenda 2013-08-02==

* Roll call
* Welcome to Renoir!
* Review of open action items
* [[Meta:web_platform_wednesday|WPW]] - how is it going?
** Endgame schedule
** We need coordinators & contributors -- but especially coordinators
** Action items cleanup: Please search for your name on this page.
*** It's probably associated with an action item. Either:
**** Mark it as (DONE)
**** Mark it as (DUE: <date>) (really, only pre-launch or post-launch)
**** Mark it as (STATUS: NO LONGER IMPORTANT) or some other STATUS
*** Next week, Julee will email you, and cc list, all Action items that need to be done before launch.
* Analytics meeting is moving to Monday 4pmPDT/7pmEDT
* We're going to move to proactive notification regarding system issues:
** We'll set up a status page of server
** We'll email public list and update the irc channel status (webplatform webplatform-site) when there's problems; when work on the system affects UX.
* Max's [[WPD:Projects/javascript|JS file import plan]] ready for language expert reviews
* [https://www.google.com/calendar/embed?src=gqaik6l023aodhh4m24qapctpg%40group Group calendar]
* SSL Certificate for TLD and sub-domains
* Dev backlog in a new Wiki namespace; e.g. WPD:Development/ProjectA

===Discussion===

====TOPIC: Welcome to Renoir!====

[much rejoicing]

Shepazu chose Renoir because he has a good balance of backend/sysadmin skills, frontend/backend development, design, and also because of his interest in the topic and history of community outreach. Great combination of skills for this project.

Renoir is based in Montreal, so on east coast time-zone, which is convenient for working with Shepazu but also he can be up early enough to work with europeans, but also people on the West Coast.

We'll keep contracting with Ryan as we need him, given his expertise. Renoir has already helped with the recent instability problem.

Official start date was August 1. Vacation to Paris for one week, August 30th

====TOPIC: Lea is not at W3C====

Wednesday was Lea's last day at W3C. Lea had a great mix of design/front end skills. Renoir has some of those skills (mostly on development side). She didn't design icons, illustrations, etc, so as I'm looking for a new person we can focus on people with strong UX/UI skills, ooking at 10-12 candidates already. We have a job description on W3C's site. http://www.w3.org/Consortium/Recruitment/#design-webplatform


ACTION ITEM: julee: We need someone to review Lea's actions item and reassign, and to reassign ownership of project.webplatform.org.

====TOPIC: Action items cleanup====

* Action items cleanup: Please search for your name on this page.
** It's probably associated with an action item. Either:
** Mark it as (DONE)
** Mark it as (DUE: <date>) (really, only pre-launch or post-launch)
** Mark it as (STATUS: NO LONGER IMPORTANT) or some other STATUS
** Next week, Julee will email you, and cc list, all Action items that need to be done before launch.

ACTION: Everyone to review the general meeting notes for actions assigned to them that aren't marked "(DONE)".

====TOPIC: WPW - how is it going?====

====SUBTOPIC: Endgame schedule====

Non-content portion of the plan is probably doable. Need to confirm the compatibility table work. 


The Content part of the schedule is still at risk because of resources. Especially folks who can coordinate.

We have 66 properties that need to be edited and also a review. It's not a huge number and something we can shoot for. We should popularize that number.

We have a good pool of contributors, we need people who have expertise to get them on board.

We need at least 4 coordinators for each week for next four weeks. There's shepazu & julee – who have a lot of other things to do. Shepazu suggested renoirb. If renoirb and Shepazu work on coordinating the community and content, those resources will be pulled off devops, tech support, and system readiness.

We have asked folks like nicdaCosta to coordinate. That works fine, but these volunteers are hard to come by and limited in their time.

Should we extend the project out and give ourselves a more sane cushion, like, into September?

Maybe if Doug/Eliot/Alex responded to stewards list, that would give more momentum.

We need to articulate the specific, scoped work, with realistic time commitment, that might help.

ACTION: shepazu and julie to make a more concrete plan with nubmers about steward asks, and eliot/alex will respond with their donations. [Eliot DONE]

ACTION: shepazu to reach out to other stewards to make sure they respond to the concrete plan asking for help.

=====SUBTOPIC: Flags=====

Lea & shepazu have the action item to actively ask reviewers:

"can you tell if this page is ready for consumption or needs more work" 

Basically, the requirement that when a person lands--we have 4500 pages on WPD, we've been working on 200-300. Users need to figure out when they're looking at an article, whether it's ready to consume or not.

So flags will be moved to a more discrete place.

Lea has prototyped the flags. renoirb has extracted those, we're ready to put them in when we get the flag stuff done.

====TOPIC: dreamhost ====

Shepazu talked to dreamhost (at least one person there) at hosting the site. And possibly being an active steward. 

ACTION: renoirb: needs to be involved in the dreamhost conversations to make sure they have what we need.


====TOPIC: Analytics meeting moving to Mondays====

Analytics meeting is moving to Monday 4pmPDT / 7pmEDT.


====TOPIC: Max's JS file import plan====
Max's JS file import plan ready for language expert reviews
http://docs.webplatform.org/wiki/WPD:Projects/javascript

====TOPIC: Google Calendar ====

Google calendar is up. This is most presently for folks to add the times where they're available to help with WPD, and when they're unavailable.

renoirb: can see the calendar there, no events

 
https://www.google.com/calendar/embed?src=gqaik6l023aodhh4m24qapctpg%40group


====TOPIC: proactive notification regarding system issues====
We're going to move to proactive notification regarding system issues
* We'll set up a status page of server
* We'll email public list and update the irc channel status (webplatform webplatform-site) when there's problems; when work on the system affects UX.

Renoir set up a system that will notify himself and Doug when the site is down.

Low-hanging fruit to set up have a simple system that lets people know what the status is if it's going wrong. Something like status.webplatform.org, to say either it's a known outage or unknown. 

====TOPIC: Dev backlog====
Dev backlog in a new Wiki namespace; e.g. WPD:Development/ProjectA

That way, we can store dev projects there.

When your infra fails… it happens to also affect the status view.

Please use project.webplatform.org when possible to create and track projects once they move from the proposals phase.

====TOPIC: SSL Certificate for TLD and sub-domains ====
No time to discuss SSL Certificate for TLD and sub-domains.

renoirb & shepazu will take it off line.

===ACTION ITEMS===

* CARRY FORWARD: Everyone to review the general meeting notes for actions assigned to them that aren't marked "(DONE)" and update with status as described above. (STATUS: Mostly done: Doug & Renoir to do.) (CARRIED FORWARD)
AI: renoirb: needs to be involved in the dreamhost conversations to make sure they have what we need. (DONE & ongoing)
AI: shepazu and julee to make a more concrete plan with numbers about steward asks, and eliot/alex will respond with their donations. (DONE)
AI: shepazu to reach out to other stewards to make sure they respond to the concrete plan asking for help. (STATUS: In progress - eliot found that mail to be eloquent and effective. Tracking this in the CSS Properties endgame schedule.)
* shepazu to look into if we need separate HTMLElement and SVGElement templates for ITS project (Unless they come to us with problems, we'll assume they're okay)
* Jirka to create overview/tutorial on ITS. (STATUS: In progress.)
* shepazu to confirm compatibility tables will be done in time. (STATUS: Not much progress because of renoir's other duties, we made good progress before that, it's high on Renoir's priority list, once stability stuff and reporting stuff is done, it's not going to be that much work after that. Tracking this in the CSS Properties endgame schedule.)
* Julee to call out in property review checklist that people should verify MSDN examples, and either replace with better examples or move to code.webplatform.org. (DONE: http://docs.webplatform.org/wiki/Meta:web_platform_wednesday/reviewer_checklist)
* CARRY FORWARD: shepazu make "can you tell if this page is ready for consumption or needs more work" an active question for css project reviewers. (CARRIED FORWARD)
* CARRY FORWARD: Julee make sure editing guide is updated with new flag values, when flags are done. (Has a dependency on flags being done) (CARRIED FORWARD)
* CARRY FORWARD: shepazu to figure out how to move current flags to new flag types and cc jkomoros and frozenice. (CARRIED FORWARD Tracking this in the CSS Properties endgame schedule.)
* CARRY FORWARD: shepazu to contact CSS wg about reviewing "done" pages. (Leaverou started a thread, but not to CSSWG. Dependency on more content being done.) (CARRIED FORWARD Tracking this in the CSS Properties endgame schedule.)
* CARRY FORWARD: Alex to talk to Paul irish & other folks on the list that Eliot pointed him to (a list that we created at launch?) about reviewing "done" pages. (STATUS: In progress: jkomoros talked to paulirish yesterday, who is in when needed; dependency on more content being done.) (CARRIED FORWARD Tracking this in the CSS Properties endgame schedule.)
* CARRY FORWARD: Shepazu & renoirb to review Lea's actions item and reassign and to reassign ownership of project.webplatform.org. (CARRIED FORWARD)
* ACTION ITEM: Shepazu to talk to Ryan about the 503s. (DONE: Garbee and Renoir talked to him more extensively, a bunch of jobs weren't getting performed, and the backlog was causing problems. Think he's resolved that.)
* renoir to look at server errors in more depth. (DONE: Got more confirmation last week; a hard confirmation. Working this afternoon to make the piwik switch today. Trying to recreate infrastructure locally to be able to test it. Succeeded in getting it running locally, will publish my workspace on github soon, so anyone else can build it completely after, of course, removing sensitive information and history
* CARRY FORWARD: shepazu to reach out to Julien and Rick Byers regarding JS plan. (STATUS: In progress: Shepazu reached out to rick byers, julien, and rick Waldron. Needs to pass info back to Max.)

==Agenda 2013-07-26 Meeting canceled due to lack of quorum==

==Agenda 2013-07-19 Meeting canceled due to lack of quorum==

==Agenda 2013-07-12==

* Roll call
* Review of open action items
* ITS
* [[Meta:web_platform_wednesday|WPW]] - how is it going?
** Other MBF issues?
*** compatibility tables (Doug)
*** data types & units done (Julee) (DONE)
*** code samples switched from MSDN to code.webplatform.org
**** Julee to add it as a review checklist (DONE)
*** schedule high-level reviews (Doug & Lea)
**** CSS WG, for instance: template change recommendations of WG? (e.g.: animatable is not a simple boolean)
**** visual, or UI indication of whether or not any given page is ready or not
**** incorporate Chris Coyers UI feedback (Lea)
*** review from famous devrel people (paul irish, chris coyier) (Alex)
**** visual, or UI indication of whether or not any given page is ready or not
*** a launch plan (Alex)
*** All systems ready check
**** We can handle additional traffic
**** All SysOps & DevOps folks are notified to expect additional traffic & should not tweak the site during the first
** Who will be a coordinator for the next 2 weeks?
* Max's JS file import
* Anything blocking you from creating great content?
* Anything new & notable? (Blogs or other communications planned for next week?)

===Discussion===

====Topic: Zurich docsprint====
Jay asked for retweeting from various official twitter handles about the Zurich Docsprint.

Please retweet and otherwise promote: here: https://twitter.com/klick_ass/status/355063210086383619  +1/Share this:https://plus.google.com/u/0/100575683580946332118/posts/EjJ9r6WCBXg  Repost here: https://alpha.app.net/klick_ass/post/7550831 

====Topic: Jirka's ITS project====
Jirka shared with us:

ITS developed something back 6 years ago in Firefox, mainly for XML, also XHTML just a set of metadata that could help translation like a translate attribute that could say whether or not the content should be translated. ITS developed several such attributes, and because it was not sufficient for more complex things, we developed v2.0 which added more localization metadata. because it was clear that HTML5 was taking off, we provided a way to map those attributes to they have a prefix. It's published as a proposed recommendation. Not expecting any changes to 
not all implementations make use of all ITS attributes yet. For example, Google Translate and Microsoft Translate support translate attribute. And that attribute also is now in HTML5 formally. We thought it might be a good idea to recommend those attributes on web platform.org, since they're an integral part of HTML (or becoming that way).

Action Item: Jirka to send to the public email list something where we can see it in action? public showcases, videos, slides.

ITS should have its own namespace on WPD. But we should consider other things about the translation or multi-lingual stuff that might be a better larger bucket, such as unicode stuff, or some other internationalization bucket, a internationalization/multi-lingual namespace…

Reference area as well.

ITS is mostly attributes, with a few elements. It's a little bit tricky because HTML doesn't allow you to use your own elements in own namespace. So you can interlink to an external ITS file, similar to linking a stylesheet.

ITS probably will not require any templates than our current Element and Attribute templates.

====Topic: CSS Properties project end game====

=====Subtopic: Stuff to do before we are "done"=====

(See outline of things blocking us completing the project.)

We think we can get the compatibility tables done in time.

ACTION ITEM: shepazu to confirm compatibility tables will be done in time.

ACTION ITEM: julee to explain on the list what's happening with the messy data types, defining what we need to do to fix it. (DONE)

A lot of the content that was donated had samples in them. The view sample link points to MSDN. We need to switch the code samples from MSDN to code.webplatform.org.

But really, a lot of the samples are stale. They should be reviewed.

Easiest fix: after pages have been updated and reviewed, search for MSDN links and delete any of those links. More complex: programmatically update to move to code.webplatform.org.

ACTION ITEM: Julee to call out in property review checklist that people should verify MSDN examples, and either replace with better examples or move to code.webplatform.org. (DONE)
 
=====Subtopic: Visual indication that a page is "done"=====

How can the user tell if a page is ready for consumption or not. We're working on P2-P3 properties, but there are a bunch more. Want to make it clear to users which ones are vetted. 

Are our new flags a good enough indication to first-time visitor that it's ready for consumption? Yes, if we are  consistent. 

ACTION ITEM: Lea & shepazu make "can you tell if this page is ready for consumption or needs more work" an active question that they're asking people in the other reviews, validate with folks that it's clear with them. 

ACTION ITEM: Julee make sure editing guide is updated with new flag values, when flags are done.

ACTION ITEM: Lea & shepazu to figure out how to move current flags to new flag types and cc jkomoros and frozenice.

=====Subtopic: High level "expert" reviews=====

We'd like to get feedback, fine touches, and the green light from CSS working group and other "famous devrel people".

ACTION ITEM: shepazu to contact CSS wg about reviewing "done" pages.
ACTION ITEM: Alex to talk to Paul irish & other folks on the list that Eliot pointed him to (a list that we created at launch?) about reviewing "done" pages.

ACTION ITEM: Lea to incorporate Chris Coyier's feeedback as appropriate.

=====Subtopic: System stability=====
Julee & others are getting a lot of 503 issues.

ACTION ITEM: Shepazu to talk to Ryan about the 503s

Maybe we need a "systems ready" line item in the guidelines for launching. If we get activity for this "launch", we should be confident we aren't going to crash.

Also, need to let Ryan and all know not to tweak production site for first few weeks of launch.

Also leaverou reported a bug on production site. She can't deploy to test wiki, only production wiki.

ACTION ITEM: Lea to send infrastructure bug (can't deploy to test wiki, only production wiki) directly to Ryan. (DONE)

=====Subtopic: we need more coordinators=====

Julee and shepazu cannot keep up with the contributors and properties. We need coordinators. So, every Tuesday, please volunteer. Eliot is busy until August. (Props to Eliot for calling in on vacation!)

When active folks are going to be unavailable, we need to have people hand off the things to someone else.

Up-front work, but then we have another coordinator! 

We had some good coordination beginning, but it's petered off. Folks are generally concurring: people are distracted with other things, it's the middle of summer…

Julee is manually going back to previous contributors and re-engaging.

It's fine to have this problem NOW, but to make sure it doesn't happen in the future, we need to establish a mechanism.

====Topic: JS import project====

Max and Phistuck have been working out the final structure of the JS import.
Let's get some JS experts who would be interested in reviewing the structure they're working out.
Also, they might be at a blocking point; relying on naming convention for DOM, which I'm not sure if we settled or not.
We need to sort out the details for the import.

We want to make sure they're not aiming at a moving target on the DOM side.

ACTION ITEM: shepazu to reach out to Julien and Rick Byers.

ACTION ITEM: Julee to make sure we have one page where we solidify what Phistuck and Max want.

ACTION ITEM: jswisher to reach out to Dave Brouant (sp?) 

===Action Items===

* shepazu to look into if we need separate HTMLElement and SVGElement templates for ITS project
* Jirka to create overview/tutorial on ITS.
* shepazu to confirm compatibility tables will be done in time.
* julee to explain on the list what's happening with the messy data types, defining what we need to do to fix it. (DONE)
* Julee to call out in property review checklist that people should verify MSDN examples, and either replace with better examples or move to code.webplatform.org. (DONE)
* Lea & shepazu make "can you tell if this page is ready for consumption or needs more work" an active question that they're asking people in the other reviews, validate with folks that it's clear with them. 
* Julee make sure editing guide is updated with new flag values, when flags are done.
* Lea & shepazu to figure out how to move current flags to new flag types and cc jkomoros and frozenice.
* shepazu to contact CSS wg about reviewing "done" pages.
* Alex to talk to Paul irish & other folks on the list that Eliot pointed him to (a list that we created at launch?) about reviewing "done" pages.
* Lea to incorporate Chris Coyier's feeedback as appropriate.
* Shepazu to talk to Ryan about the 503s
* Lea to send infrastructure bug (can't deploy to test wiki, only production wiki) directly to Ryan. (DONE)
* julee to explain on the list what's happening with the messy data types, defining what we need to do to fix it. (DONE)
* shepazu to reach out to Julien and Rick Byers regarding JS plan.
* Julee to make sure we have one page where we solidify what Phistuck and Max want.(DONE)
* jswisher to reach out to Dave Brouant (DONE) 


==Agenda 2013-06-28==

* Roll call
* Review of open action items
* [[Meta:web_platform_wednesday|WPW]] - how is it going?
** Who will be a coordinator for the next 4 weeks?
** How should we circle back around to folks who have previously showed interest?
*** Julee started a CRM for community contributors. (DONE)
** What MBF for CSS properties?
*** compatibility tables
*** data types & units done
* Demian's Tech Centers - how is it going?
* [http://lists.w3.org/Archives/Public/public-webplatform/2013Jun/0075.html Max's JS file import]
* [http://lists.w3.org/Archives/Public/public-webplatform/2013Jun/0174.html revamping flags!]
* Anything blocking you from creating great content?
* Anything new & notable? (Blogs or other communications planned for next week?)

==DISCUSSION==

====TOPIC: WPW - how is it going?====
=====SUBTOPIC: Who will be a coordinator for the next 4 weeks?=====

People aren't officially signing up to be a coordinator, so Doug is basically signed up for all properties. We need people signed up to help.
It's not that hard to coordinate. Just mark down when people volunteer, help them out. Recruit people actively, on the properties you're coordinating. It's too much for doug on his own; other people are helping out ad hoc, but aren't following through to make sure the contributor has actually completed the work.
Alex signed up for last three weeks in July.

ACTION: julee to e-mail list to try to get others to coordinate. (DONE)

We're still targeted for end of July for first round of P0 CSS properties. Don't want things to fall apart for lack of resources. There are enough volunteers that people can actually get this thing done. 
ACTION: Eliot to move Seattle Doc Sprint properties to a new table on the WPW page. (DONE)

=====SUBTOPIC: How should we circle back around to folks who have previously showed interest?=====

Julee started a CRM spreadsheet 

If anyone needs access, e-mail Julee. We won't send out public link because it has e-mail addresses on it.

Other things we could do for contributors?


Lea sent a link to a site that has a contributor spotlight http://thenounproject.com/

We talked about doing something like that in the past. We should definitely recognize. As a blog post or on the home page. There are a bunch of people.  Contributer "cred"

Having a contributor highlight on the site shows visitors that there is an active community.
Be a little careful--some people are rather shy and don't want public exposure


We don't have profiles right now to configure that. Ryan needs to fix the user profiles. He's actively working on it--it's a MW bug.


Just to reiterate, when Julee and I emailed the people who had been past contributors, saying, "you were in the top 20/3o people". That pulled several people back in. People really responded well to the fact that we were acknowledging their contribution.

That model is very useful. Even like FitBit sends out little emails to congratulate.

shepazu to prod the discussion about recognizing contributors on the mailing list and look for an extension to mediawiki to do the sidebar

We could have a per-page thing and the overall site notice thing, profiling people who have done a lot of stuff.
People like Garbee and Max have done a great job, really gone above and beyond.
Either in the TYPE of thing they've done, or the AMOUNT of work they've done
There's a number of bots at Wikipedia that detect things like this automatically


Because we need to explicitly let people opt in at this time, it would be just adding a little section on the home page manually. That would be easier to get going.
We do want to execute on the leaderboards thing. It's an automatic way to get people's constructive competition going, if you're #3, you want to reach #2
gamification kicks in…

We should talk about all of these analytics in the analytics meeting. i'm going to make a note of these.

===== SUBTOPIC: What MBF for CSS properties?=====

compatibility tables
data types & units done
get the code samples switched from MSDN to code.webplatform.org

checklist to make it quick to review
some kind of visual, or UI indication of whether or not any given page is ready or not

a template added to the top like {{NeedsWork}} is helpful for "not ready yet"; visitors and new contributors are not sure what 'flags' means

a high-level gut check as a group before we go forward

high-level CSS WG review, even just flagging issues
I think it should be done, maybe even fairly soon
they might suggest ways in which we should be changing the pages overall
at the docsprint there were a few people from the CSSWG. They had some good review comments. Alan Stearns, Arron Eicholz. Some of them required template changes, like animatable is not a simple boolean unfortunately. Some of them were stylistic

Arron Eicholz has many more suggestions.

ACTION: shepazu to following up with CSS WG review  -- especially Arron Eicholz , who was in the IRC for this meeting -- to get more suggestions on CSS properties pages

review from famous devrel people, they have good reach?

people like paul irish or Chris... coyier (sp?)


ACTION: jkomoros to work with Paul Irish to coordinate getting devrel type folks to review the docs.


ACTION: Lea to incorporate Chris Coyers UI feedback (http://lists.w3.org/Archives/Public/public-webplatform/2013May/0241.html)

a launch plan
make sure we're contextualizing what we consider this launch to be

ACTION: jkomoros to help coordinate a launch plan once we decide to go forward with launch.

==== TOPIC: Max's JS file import====
http://dev.maxpolk.org/msdnjs/index.php?title=Special:AllPages&from=Constants&to=Objects%2Farguments
Max has a link to first full upload: http://dev.maxpolk.org/msdnjs/index.php?title=Special%3AAllPages&from=Objects%2Farguments&to=&namespace=0
http://lists.w3.org/Archives/Public/public-webplatform/2013Jun/0075.html

Chrismills and scottrowe, as content architects, give an official response?
They may not be available right now.

We should have a calendar or something.

ACTION: julee to create a high-level calendar for people to mark when they're available or not. (DONE: https://www.google.com/calendar/render?tab=oc&pli=1&gsessionid=P71QgXQ4uw2jGWqFWW6lLA)

Limited resources on JS, but other things we can do to support this project?

Max is a software developer at ATT mobility. When someone says "we could try one way or another", someone needs to TRY and see if it works.

Need folks to review and try the proposals Max is putting out in email.

Max needs to explicitly state what he needs.

We need a template.


frozenice, is just too slammed

All template ninjas are too busy.



ACTION: shepazu to mock up types of JS pages with examples, so we can think about templates from there.

We do have tools to edit a page programmatically after the fact, and do mass page renaming, so we should just go forward with it.

ACTION: Max to configure the project page with the tasks.
ACTION: Julee to rally an IA overview (DONE)

ACTION: shepazu and maxpolk to meet up in person to work on JS page organization

==== TOPIC: revamping flags!====
Eliot provided last set of flags that we had settled on
We should go ahead and do it; enough people concurred
==== TOPIC: Demian's Tech Centers - how is it going?====

The general overview is that blackberry is paying for some time to use these tech centers in brazil (schools that are paid to do lab time, basically interns). 4 students who have signed on to take on editing/ css properties. Julee and I met with them last week, will meet again on Monday. 

we have four people who will spend 20% of their time a week working on WPD, with Blackberry sponsoring.
University students. They have ten sites. This is a pilot.

They have a separate table on WPW http://docs.webplatform.org/wiki/Meta:web_platform_wednesday#BlackBerry_Tech_Centers
Interested in being part of the community as we go through. You might see e-mails, or IRC. Down the road, we hope more of the tech centers will help out. 
Millo said Microsoft has similar programs, so once this gets going, we can add on some Microsoft sites.


They're mostly CS students, so maybe can help with infrastructure.

==== TOPIC: Anything new & notable? ====

(Blogs or other communications planned for next week?)
ACTION: Eliot to write up blog post about Seattle Doc Sprint. (DONE)





== ACTION ITEMS==

* julee to e-mail list to try to get others to coordinate. (DONE)
* Eliot to move Seattle Doc Sprint properties to a new table on the WPW page. (DONE)
* shepazu to following up with CSS WG review  -- especially Arron Eicholz , who was in the IRC for this meeting -- to get more suggestions on CSS properties pages
* jkomoros to work with Paul Irish to coordinate getting devrel type folks to review the docs.
* Lea to incorporate Chris Coyers UI feedback (http://lists.w3.org/Archives/Public/public-webplatform/2013May/0241.html)
* jkomoros to help coordinate a launch plan once we decide to go forward with launch.
* julee to create a high-level calendar for people to mark when they're available or not. (DONE https://www.google.com/calendar/render?tab=oc&pli=1&gsessionid=P71QgXQ4uw2jGWqFWW6lLA)
* shepazu to mock up types of JS pages with examples, so we can think about templates from there.
* Max to configure the JS project page with the tasks.
* Julee to rally an IA overview of Max's JS emails (in progress. PhishtucK is doing great.)
* shepazu and maxpolk to meet up in person to work on JS page organization


==Agenda 2013-06-21: Meeting canceled due to lack of quorum==

==Agenda 2013-06-14: Meeting canceled due to lack of quorum==

==Agenda 2013-06-07==

* Roll call
* Demian Borba of Blackberry and his university program.
* Review of open action items
* [[Meta:web_platform_wednesday|WPW]] - how is it going?
** How's video going
** should we ask Hiroki Yamada to repost announcements to public-webplatform-jp@w3.org?
* Ryan Lane upgraded site.
* [http://lists.w3.org/Archives/Public/public-webplatform/2013Jun/0024.html Naming conventions thread]
* Anything blocking you from creating great content?
* Anything new & notable? (Blogs or other communications planned for next week?)

===DISCUSSION===

====TOPIC: Demian Borba of Blackberry and his university program====

Demian Borba has a webkit implementation in our phone

* … focusing on HTML5
* … want to make developers successful
* … started a program called Blackberry Tech Center
* … Brazil, Argentina, US
* … find professors, pick 10 tech students to sponsor
* … could donate 20% of time to Web Platform Docs
* … in Brazil, we have 5 tech centers
* …. 1 in Argentina, Mexico, US

WPD could do project demand for them; provide a weekly structure and set of directions, that would be great.

Students are comfortable in EN and comfortable editing articles?

Students could also help with software? Kuma, Gollem & GitHub? Some tech centers that are really focused on UX, another on trolling & APIs, for example: blackberry command lines were moved to a UI.

It would be great to have them first work on content so they understand the work flow and requirements, and since they're ready to go

Community Dev folks will meet with Demian next week. And he can get them to meet once we have execution plan 

Millo is looking forward to Tuesdays meeting, can bring in MS similar programs, let's federate the students!

shepazu to send email to most active users DONE

shepazu to reach out to Kuma ops (Aly). Yes, but no progress

shepazu to post on job sites and sysops lists Carry forward

julee to ask direct and actionable question on IRC at 11am n/a (DONE)

shepazu to send email to most active users - DONE

shepazu to reach out to Kuma ops (Aly) - DONE no reply yet

julee to ask direct and actionable question on IRC at 11am - KINDA SORTA

====TOPIC: WPW - how is it going?====

scott is working on video

snafu this week, we didn't realize that Scott had already done Flexbox….

… so we pulled together an examples week

… gathered together things that hadn't been done

… on Monday, we're going to work with Nic deCosta, and set forward the next several weeks

we meant to put things together earlier, having a set plan in place will give us consistency, we can write blog posts in advance

…also folks can do things in advance and have it done by the designated week.

…NicDaCosta is in EU; announcing at 11am on Wednesday PDT, kills it for EU; asked that we announce it late Tuesday night, early Wednesday morning

..so folks can do it on Wednesday.

====TOPIC: Japanese email list====

julee: should we ask Hiroki Yamada to repost announcements to public-webplatform-jp@w3.org?

====Topic: Naming Conventions====

julee_: we should be consistent about where landing pages are located

shepazu: let's move forward with our master list of topic locations

julee_: should Ben Lobaugh do it?

Eliot: I'll do it

shepazu: ben was also trying to link to the talk page for pointer events

====Topic: Anything blocking you from creating great content?====

shepazu: We got an upgrade on MW; some folks have seen some weird quirks - please continue to report anything strange

====TOPIC: Doc Sprints====

MS is having a Doc Sprint 6/22

Brazil Doc Sprint TBD

http://docs.webplatform.org/wiki/WPD:Community/Community_Events

===ACTION ITEMS===

* CARRIED FORWARD: shepazu to post on job sites and sysops lists
* shepazu & julee to do a promo check list, including concrete details on how stewards can propagate (Eliot is working on this)
* Millo to cc shepazu on his email to new IEEE contact
* shepazu to ask Hiroki to propagate announcements to the JP list
* We will blog and tweet WPW late Tuesday night


==Agenda 2013-05-31==

* Roll call
* Review of open action items
* [[Meta:web_platform_wednesday|WPW]] - how is it going?
** Coordinators finding contributors?
** Topic clusters done with instrux?
** How's video going
* [[Special:RecentChanges&limit=300&days=1|Spam]] fixing?
* Anything blocking you from creating great content?
* Anything new & notable? (Blogs or other communications planned for next week?)

===Discussion===
====TOPIC: DevOps====

Recruiting is going slowly.


====TOPIC WPW====

coordinators should socialize the list each week

coordinators need more time to reach out to contributors: do topics earlier



problem: many people are not joining the e-mail list

A lot of people already have email overload.

project.webplatform.org was partially to cure that; there people can jump on and join an issue's discussion
jswisher said mail list is not part of site: not one experience; psychological barrier to "subscribing to an e-mail list"

http://www.discourse.org/ contextual chatting

But, we already have a few systems up that don't talk well with one another.

Garbee is working on an actual working Proof of Concept for a new 'wiki' engine. He will share his PoC next week.


Denis spent some time trying to get Kuma to work. Persona was a block.


We couldn't figure out how to make a page in Kuma

If Kuma is worth it, could someone help us from the Kuma community?

Imagine this as our editor: http://jejacks0n.github.io/mercury/

[09:25:07] <julee> jswisher: devs are helpful, but doesn't know about how things would work from the outside.

 scottrowe worked with mindtouch before http://www.mindtouch.com/


we're not going to move forward on a system without having a dedicated devops person.

ACTION: shepazu: get ahold of Kuma to get an evaluation copy going


Garbee is trying to rope people in from other communities he frequents. A few have shown interest in helping and at least one has already started (brbcoding).

go on IRC and ask: who's here right who can help

what are the 100 folks on webplatform doing? Lurking.

We also had major noise/spam issues right after launch. So, in us trying to control those issues we may have scared people off.


IRC people don't like to be told what specifically to discuss. If you are too strict on things, you end up like #html and people don't like you too much.

====TOPC: Topic clusters done with instrux?====

scottrowe has the Action item to of a proposal to create a new set of topic clusters that are pertinent to the page type

we need clusters that are relevant to the page type: CSS properties, API, HTML

How do we get a specific topic cluster type form field into each page type?

scottrowe: we think we can do this, but in the short term, we'll have to have folks put manual links


====TOPIC: WPW Video====

scottrowe has instrux in the video script

 julee: get a checklist out of script for folks to follow?
ACTION: scottrowe to derive a checklist from the video script for editing CSS properties


ACTION: scottrowe to send out script to a couple of folks to get feedback before taping.

ACTION: scottrowe will tape next week.

====TOPIC: spam====

600+ spam pages
should Admins approve new user creation?

ACTION: Garbee and shepazu to get a captcha system that works.


[09:58:45] <Garbee> I'd set it up with Questy (with custom questions/answers) to start.

http://www.mediawiki.org/wiki/Extension:QuestyCaptcha --Something like the first example code.


We also need to improve abusefilters.

Garbee is working with MicroFormats on sharing stuff once they get their system online.

Jswisher said MDN watches the revisions feed and has a dedicated delete; switching to persona has helped - although it might be a temporary effect; Persona for auth is actually a pretty good helper. It, like oAuth, is harder to fake outright.

===Action Items===

* shepazu to send email to most active users
* shepazu to reach out to Kuma ops (Aly).
* shepazu to post on job sites and sysops lists
* julee to ask direct and actionable question on IRC at 11am



==Agenda 2013-05-24==

* Roll call
* Review of open action items
* [http://docs.webplatform.org/test/css/properties/border-radius ToC]
* [[Meta:web_platform_wednesday|WPW]] - how is it going?
** New and improved: only one table to fill out! (Master page is what we're pulling from. But http://docs.webplatform.org/wiki/Meta:web_platform_wednesday will become the final master list.)
** We have a standing IRC meeting at 11am PDT, Wednesdays, on #webplatform -- but nothing seems to be happening there.
*** We should be active on IRC at that time, at least promoting the current week's blog post, and let folks know we're available to answer any questions at that time.
** What is workflow for WPWs?
**# Shepazu to pick topic.
**# Blog written on Tuesday, promo'd Wednesday morning.
**# Coordinators get volunteers and sign folks up on the WPW page, adding "In Progress"
**# Coordinators help contributors do properties.
**# Coordinators should update tables by Tuesday, with "Done" or "Not done".
** Anyone going to [http://cssconf.com/ CSSConf]? Any opportunity to promote WPW?
* [[WPD:Project_Status|Getting to Beta]]
** The bug genie is returning connection errors. Seems to be associated with writing certain files.
** How to mark bugs that are not in beta - postponed?
* [https://docs.google.com/spreadsheet/ccc?key=0Ao_fDuA-PPFydE9vbkR4UWpPRHNjaGFxcjA5WXd5SVE#gid=0 changing www page to focus on community]
* Embedding external pages in WPD? (If Lea's not here, move to next week.)
* Anything blocking you from creating great content?
* Anything new & notable? (Blogs or other communications planned for next week?)

===DISCUSSION===
====TOPIC: Scott to do a video on how to do a CSS property====
It would be cool if people could share tips about doing CSS properties for the video
If we tell people to not fill in compat table information, make sure to emphasize the compat NOTES section
Let's talk about more examples for video, too.


We can easily do other ones in the future about how to edit wiki, contribute, etc

====TOPIC: ToC====

mockup: http://docs.webplatform.org/test/css/properties/border-radius

Lea pulled ToC out to the side.

Suggestions on how to make it better, but acceptable to deploy for now? Yes.


====TOPIC: Web Platform Wednesdays====
 http://docs.webplatform.org/wiki/Meta:web_platform_wednesday


now coordinators have only one table to update.

Shepazu is still tweeking it.

Stuff that doesn't get done, gets pushed to next week, or goes back to the hopper to come back in later weeks.

coordinator's job is NOT to do all these tasks. The corodinator is supposed to go out and actively recruit people to work on their items. If they can't get anybody, then sure work on them themselves.

Master list of what hasn't been done:
http://docs.webplatform.org/wiki/Meta:web_platform_wednesday/master_list  or https://docs.google.com/spreadsheet/ccc?key=0AkRs-89PKiZpdE0xdm9Sb1ZvRW1ZRzMtWEdyU0Z4OEE#gid=14 

Master list of what has been done:
http://docs.webplatform.org/wiki/Meta:web_platform_wednesday 


ONLY COORDINATORS should fill out that table


Workflow is:

# Shepazu to pick topic.
# Blog written on Tuesday, promo'd Wednesday morning.
# Coordinators get volunteers and sign folks up on the WPW page, adding "In Progress"
# Coordinators help contributors do properties.
# Coordinators should update tables by Tuesday, with "Done" or "Not done".

We should get topic clusters determined more in advance? like two or three week out

Leaverou will speak about WPW at http://cssconf.com/

====TOPIC: landing page/home page for site====

https://docs.google.com/spreadsheet/ccc?key=0Ao_fDuA-PPFydE9vbkR4UWpPRHNjaGFxcjA5WXd5SVE#gid=0

General idea: current goal is to get people active, so show community activity!

Changes should be done incrementally.


====TOPIC: Beta====

Connection errors on project.webplatform.org are preventing triaging of bugs.

In order to easily and quickly view bugs for current milestone within each project's open bugs page, bugs that are not part of the beta should be set to postponed.


====TOPIC: Embedding external pages in WPD====

it would be cool if we could add screencaps from other pages
leaverou  got this from the cubic-bezier page, somebody added screencaps from my tool cubic-bezier.com. She asked him if he thought it was a good idea to embed the tool (assuming I added media queries to make it look good on small viewports). She's wondering if it's possible and allowed.



===ACTION ITEMS===

* julee to start thread on where new guides exist, where to link them to and what to call them (our Ed, Getting Started, WPW, and Coordinator's guides have confusing names and do not properly reference each other.)  (DONE)
* Scott to do a video on how to edit a CSS properties page.
* Leaverou to email about embedding a screencaps tool. (CARRIED FORWARD)
* shepazu to write up guide on what coordinators do on WPW
* leaverou to work on home page design, with the goal of highlighting community activity (CARRIED FORWARD)
* shepazu to figure out what connection bug is in project.webplatform.org
* Julee to write up an email about "postponing" non-beta bugs.  (DONE)
* shepazu to figure out what connection bug is in project.webplatform.org
* (CARRIED FORWARD) leaverou to send out e-mail asking people to vote on which skin bugs are more important (DONE)
* (CARRIED FORWARD) shepazu to e-mail ML about latest plans for talk.webplatform.org (CARRIED FORWARD)
* (CARRIED FORWARD) shepazu & leaverou to mock up what the improved flags will look like. (CARRIED FORWARD)
* (CARRIED FORWARD) shepazu to ensure forums banner explicitly states it's for accessibility question only. (CARRIED FORWARD)
* (CARRIED FORWARD) shepazu writes down "How to review a page" and the workflow, so coordinators and contributors know what to do and workflow for whole WPW ideally (CARRIED FORWARD)



==2013-05-17: Meeting canceled due to lack of quorum==

==Agenda 2013-05-10==

* Roll call
* Review of open action items
* [[Meta:web_platform_wednesday|WPW]] - how is it going?
** Coordinators:
*** Doug: 
*** Chris: did all of his, himself -- next time will get others to help
*** Julee: did some, got help with border-color and examples
*** Scott: 
*** Janet: 
** Process:
*** Coordinators please:
**** update [[Meta:web_platform_wednesday|WPDW]] main page with assigned items having check marks
**** update [[Meta:web_platform_wednesday/2013-05-08|this week's page]] with status
**** update [[Meta:web_platform_wednesday/master_list|master list]] when things are done
*** Doug is working on a [[Meta:web_platform_wednesday/coordinator_guide|coordinator's guide]]
*** Do all pages need a different reviewer? At least a "peer" review?
* [[WPD:Project_Status|Getting to Beta]]
** Bug count: 141
** How to mark bugs that are not in beta - postponed?
* Onboarding
** Need a stock response to people like Konstantinos who reach out to the list and want to join. And maybe a rotating member of the community team to send them?
* Any updates?
** We have ToCs!
* [https://docs.google.com/spreadsheet/ccc?key=0Ao_fDuA-PPFydE9vbkR4UWpPRHNjaGFxcjA5WXd5SVE#gid=0 changing www page to focus on community]
* Anything blocking you from creating great content?
* Anything new & notable? (Blogs or other communications planned for this week?)


==DISCUSSION==

===TOPIC: W3C accessibility folks to use our forums===


We need to ensure forums banner explicitly states it's for accessibility question only.

There is a cost to everything we maintain. We'd de-emphasize it from the site (well, we already have). The accessibility people have a dedicated, funded person to fund the boards.

=== TOPIC: WPD Wednesdays===

http://docs.webplatform.org/wiki/Meta:web_platform_wednesday

====WPDW Status====

We're in good shape, 25 knocked out this week, someone committed for everything but outlines

jkomoros can't come next week because of I/O, but have it blocked on my calendar going forward

Let's remember to send out inspirational articles when we blog about topics we're focusing on.

Weekly cycle is over on Tuesday.


====Do all pages need a different reviewer? At least a "peer" review? ====

Important that the person who reviews the page is not the person who worked on it.

Review shouldn't come across as too much of a blocker. Don't want it to be counter productive

Informal coordinator review, peer review, with official tech review later in 1.0 perfect cycle. We should not declare failure if we don't get review. Set review flag, and reviewers clear it. When flags are removed, that shows the pages are the quality that should be standard

Peer review to make sure the checklist is taken care of.
Coordinator can do the checklist review

If the coordinator can't do it, maybe just pair writers together

Technical review for correctness and example is correct

Two different levels of review might make the procedure too long winded. Expert review should come later, if needed.


The whole point of this exercise is to... get the work done, but mainly to grow contributor base, make it clear how to contribute.

some people have already spoken up and started contributing because this makes it easier. Don't take the work away from other people if you can help develop them. It will take some effort to get people into the habit of contributing and building up the contributor base

==== Coordinators responsibilities====

Doug is working on a coordinator's guide

WPDW will be on #webplatform NOT #webplatform-site


All coordinators should:

* update WPDW main page with assigned items having check marks
* update this week's page with status
* update master list when things are done

Coordinators should still do one page. That helps them understand what the pain points are.

Coordinators have 1 or 2 volunteers for each WPDW

When we have a short-hand property that encompasses all of the other properties for individual settings

That's why we chose more properties this week, to keep shorthand/longhand sets together. One person can write the individual longhand properties (which may be in more than one shorthand property), and then do the short hand version.

A lot of pages in mine that said, "just see short hand page". That's annoying to click through. Because we don't have transclusion, we should copy paste.


===TOPIC: Getting to beta===

http://docs.webplatform.org/wiki/WPD:Community/Meetings/General#Project_Status

The project leads to review the criteria and update the bugs
Extended deadline until mid week next week

====Project Status====
[[WPD:Project_Status|Project Status Page for Getting to Beta]]

Bug count: 141

{|class="wikitable" style="text-align: center; width:50%"
!Project
!Lead
!Open Issues
!Beta defined
!beta bugs assigned
|-
|Analytics
|patrickdsouza
|10
|Yes
|Yes
|-
|Blog
|Eliot-MSFT
|4
|Yes
|Yes
|- style="font-style: italic; color: red;"
|commentsextension
|shepazu
|8
|???
|???
|-
|community
|jswisher
|1
|Yes
|Yes
|-
|compatibilitytables
|shepazu
|1
|Yes
|Yes
|- style="font-style: italic; color: red;"
|content
|Julee
|40
|Yes
|in progress
|-
|dabblet
|Lea
|2
|Yes
|Yes
|- style="font-style: italic; color: red;"
|InfoArch
|Scottrowe
|9
|Yes
|Yes
|- style="font-style: italic; color: red;"
|infrastructure
|shepazu
|14
|Yes
|???
|- style="font-style: italic; color: red;"
|prmg
|Garbee
|17
|Shooting for 5/15
|Shooting for 5/15
|- style="font-style: italic; color: red;"
|Q&A
|shepazu
|2
|???
|???
|-
|skin
|Lea
|17
|Yes
|Yes
|- style="font-style: italic; color: red;"
|templates
|jkoromo
|7
|dependency on content & ia beta definition
|No
|}

===TOPIC: Onboarding===

Need a stock response to people like Konstantinos who reach out to the list and want to join. And maybe a rotating member of the community team to send them?

Eliot: We're getting a regular stream of new people, asking how they can help. We need a stock mail to send out, and someone on point to respond

people should feel comfortable to customize it.

Tell them that wiki wednesday is a great way to get started

===ACTION ITEMS===

* (CARRIED FORWARD) shepazu to revamp CSS WG e-mail to be call for contributors (DONE) 
* (CARRIED FORWARD) leaverou to send out e-mail asking people to vote on which skin bugs are more important
* (CARRIED FORWARD) shepazu to e-mail ML about latest plans for talk.webplatform.org (CARRIED FORWARD)
* (CARRIED FORWARD) shepazu & leaverou to mock up what the improved flags will look like. (CARRIED FORWARD)
* (CARRIED FORWARD) shepazu to ensure forums banner explicitly states it's for accessibility question only. (CARRIED FORWARD)
* shepazu to consider putting table at the top of the page (DONE)
* shepazu send out an email asking for someone to work on outline (DONE)
* Julee to update editor's guide with links to WPDW (DONE)
* shepazu to start thread on where new guides exists, where to link them to and what to call them (ACTION transferred to Julee)  (DONE)
* (CARRIED FORWARD) shepazu writes down "How to review a page" and the workflow, so coordinators and contributors know what to do and workflow for whole WPDW ideally (CARRIED FORWARD)
* Scott to write up quick guide on dealing with shorthand properties (ACTION evolved to: Scott to do a video on how to edit a CSS properties page)


==Agenda 2013-05-03==

* Roll call
* Review of open action items
* [[WPD:Project_Status|Getting to Beta]]
** We assigned project owners. Those owners should review the beta criteria and update it with what their "group" thinks should be in the beta. 
** Beta criteria needs to be clarified at the higher level as well. For example:
*** [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0370.html Scott's take]
*** We need more folks vetting the content that's there. The community TF will do a recruiting plan.
*** We need folks to work on content, especially CSS properties pages. We may ask folks to own certain portions, to be divvied up amongst their friends and family, or otherwise focus on that.
*** For each content area, we should have exemplar content
*** Each page should be clearly designated as either ready to consume or needing additional contributions.
** What you can do:
*** If you're a project leader:
**** discuss beta criteria with stakeholders and update the Project Status page.
**** make sure you have tasks and bugs relating to beta in project.webplatform.org, and that they're assigned to someone.
**** if you find blockers, file a bug, and broadcast it to the public list
*** If you're an individual contributor:
**** work on some CSS properties
**** if you find blockers, file a bug, and broadcast it to the public list
* CSS Properties pages

==DISCUSSION==

===TOPIC: Beta===

http://docs.webplatform.org/wiki/WPD:Community/Meetings/General
http://docs.webplatform.org/wiki/WPD:Project_Status
http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0370.html

About Beta: we aren't out of the woods until we get to Beta, at that point, we can be comfortable saying "use this content". That's the critical mass point. Watching all the sub-task forces doing their work, it's great, but imagine that there's a day when stewards or others leave and it starts a mass exodus. Get to critical mass: instead of doing so across the site. Set up a beta based on a content category. The beta can apply to one part of the site. There is a risk that if the project does not achieve a measure of usability, stakeholders may lose interest. The CSS properties project was that set that folks could use as a resource. This calls for focusing on content, to the exclusion of other things.

This should be a fundamental shift in how we do this. Not beta criteria for all of WPD, but define beta criteria for individual content areas, and define beta status on each bucket. Define "beta" as pertaining to discrete content areas. First "beta": CSS Properties.

We need a milestone achievement - CSS Properties. If work doesn't lead to that, defer it. This week, we realized we're spreading our energies too thin. So we should focus our energies on CSS properties project. But, volunteer help is not fungible. For example, Max Polk is willing to work on the MSDN stuff but not interested in other bits. The only thing I would say that needs to be done is:

1) have the compatibility tables from MSDN and caniuse working (because that's a big part of content creation and user experience). If people come to the site and don't see consistent compat tables, it doesn't look good. So our work there is better spent finishing up compat extension.

2) Also, we need to have an exemplar for each page, which is the criteria we had for beta--that's the other thing we we should have for beta.

We all agree on CSS Properties. Other content areas will be deferred.

What about other beta tasks?

Do we want to go back to the project status page and look at those and say if any of those are direct for beta? If we focus on this stuff and don't try to recruit additional contributors, and we say CSS properties are beta, will we have a site that people can consume and contribute to?

Eliot: There are two things there. There's the content effort and the infrastructure effort. (The latter includes compat tables, community, etc.) community growth can still go on, it's separated from what the community is working on. Even MDN is mostly people consuming. Really only about 15 contributors.

Want to reframe a bit: "What is beta" ? what are we trying to accomplish? who is the audience?

1)	ourselves. To push ourselves and feel momentum
2)	an opportunity to talk to, after the alpha announcement, to engage public and say hey look, another chance to introduce ourselves
3)	is the stewards

If we talk about this awesome resource, and we don't have it yet, web developers need to see progress, momentum. if they see value, they'll respond, if devs promote, we're successful. We aren't changing our goals. We need to change focus and messaging for this content only. This was the general plan from the beginning of the CSS properties project?

If we do micro-betas, it may dilute the impact of a general beta. It will be virtually impossible for us to get _all_ of the content to beta.

But if we have a set of clear, well-defined criteria for the different sections, that shows evidence of progress. So it's the only path to success.

Then we need to be clear that we're focused on the _content_, not the _site_. We'll continually revise and refine our processes around recruitment and participation. We've already got a lot more than what we started with. We've made some strides in that area. Some efforts in regard to recruiting may not be timed appropriately to achieve a short-term objective.

When Eliot sent the mail out, he was looking at was our loss of focus on the content front. We're putting together a LARGE project with many different facets. At Microsoft, we have a team of writers, and a production team, and a marketing team 
and we don't take marketing people off that when we need to do a content push.

We shouldn't do it here. We should identify who's working on what, and what they're doing. The note was really just about loss of focus on Content front. We'll continue to look at bugs and project status page focus on other areas, but as far as content effort goes, we focus on CSS properties. Other aspects are secondary but still important.

Folks will review their bugs:

Infrastrucutre is Doug. Content is Scott, Chris, and Julee. Community is Janet for beta criteria.

Right now, the site notice has a new call to action on JS.

===TOPIC: CSS Properties work===

The CSS properties sheet is overwhelming folks. [https://docs.google.com/spreadsheet/ccc?key=0AkRs-89PKiZpdE0xdm9Sb1ZvRW1ZRzMtWEdyU0Z4OEE#gid=17 Julee updated it].

We need to ensure that new contributors are properly supported. [[WPD:CSS_property_guide/supporting_new_contributors#Helping_contributors_with_CSS_properties_page|Plan to help contributors]]

Everyone on this call who's not up for this, e-mail me specifically, otherwise you're on the hook for being an ambassador or greeter.
Weekly content-wrangling events on IRC is being scheduled for the West coast first, as Scott and Julee have already volunteered as consistant facilitators. Please fill out [http://www.doodle.com/y4bdnrg4ycdk4i25 doodle poll]

===TOPIC: Forums===

w3c accessibility folks want to use our forums. So, let's keep them open, we've already deemphasized them on the site and communications channels. But let's keep them open so accessibility folks can use it.

==ACTION ITEMS==

* Shepazu to mock up how project should be represented in the wiki (DONE)
* shepazu: update the site notice about the CSS Properties push and how to get started AND use the piwik tracking campaign code.  (DONE)
* shepazu to draft up CSS properties project blog post (circulate for comment) AND use the piwik tracking campaign code.  (DONE)
* shepazu to revamp CSS WG e-mail to be call for contributors
* leads to review the bugs for project areas on project.webplatform.org (jswisher, shepazu, cmills, julee, scottrowe)  (In progress: See: [[WPD:Community/Meetings/General#Project_Status|Project Status table]])
* shepazu to send out e-mail asking people to vote on which skin bugs are more important
* shepazu will send an email about change in forums with w3c accessibility folks using it to answer questions
* (CARRIED FORWARD) shepazu to e-mail ML about latest plans for talk.webplatform.org 
* (CARRIED FORWARD) leaverou: to talk with Chris Coyier regarding reviewing css properties template.
* (CARRIED FORWARD) leaverou: will follow up with Denis where global nav didn't get implemented.
* (CARRIED FORWARD) shepazu to work with lea to mock up what the improved flags will look like.

==Earlier meeting notes==
[[WPD:Community/Meetings/General/Earlier]]