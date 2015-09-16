---
title: 2013
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - 'TEST:beginners'
    - 'Template:NeedsWork'
uri: 'WPD:Community/Meetings/General/Earlier/2013'

---
## Earlier Web Platform general status meeting

For the most recent notes on the webplatform.org general status meetings, go to [WPD:Community/Meetings/General](/WPD:Community/Meetings/General).

## Agenda 2013-12-06

-   Jen Simmons has a mock up of the HTML elements pages
-   Max Polk has done the 3rd JS import
-   Eliezer Bernart is on templates
-   David Singer has proposed a WebVTT content project

### Raw meeting notes

## Agenda 2013-11-22

-   JS import
-   HTML Elements
-   CSS compatibility
-   How was TPAC?
-   Pointers to info about Universal Access
-   Migration
-   Dave's working on DOM re-org

### Raw meeting notes

[WPD:Community/Meetings/General/2013/1206\_raw\_mtg\_notes](/WPD:Community/Meetings/General/2013/1206_raw_mtg_notes)

## Agenda 2013-11-08: Canceled due to lack of agenda

## Agenda 2013-11-01

-   Jen Simmons
-   TPAC
-   CSS properties project
-   Compatibility tables
-   The next content project?
-   Status on migration project
-   Doug will be out the next two Fridays, should we meet anyway?

### Discussion

julee, shepazu, peterlubbers, jswisher, scottrowe\_, jensimmons, renoirb, eliot, patrickdsouza, eliezerb are all on the line or on IRC

scribenick: renoirb

#### TOPIC: Jen Simmons is contracting

Good news: Jen Simmons is going to work for at least 6 months or so, starting part time, she is a developer/designer. she is going to be part time for a few weeks and then be full time after she finished her other already planned arrangements.

Jen had a chance to talk with a few folks at Html5DevConf, at Google. A lot to work on. Jen is thinking she will work on usability issues and improve it as well as how to help contributors to contribute (making it easier).

Doug believes we should prioritize usability to the users (i.e. not a contributor). we should have a conversation about those on the list. We need to prioritize.

#### TOPIC: TPAC

TPAC is W3C's annual "all hands" face-to-face meeting. Where we gather (almost) all the groups in a big conference. This year it is in Shenzhen, China. Renoir, Doug and Eliott will be there. Doug and Renoir be there between 11/9-17. Eliott: 11/10-16.

Renoir will be going around and learn with various working groups. Granted to be on an offset time zone and will be there for emergencies and things that have to be done.

Renoir will also be organizing TPAC's "Lightnening talks" sub-event.

Doug will be presenting with Eliot about WPD at TPAC to raise awareness.

Doug is part of many working groups, and so will have limited availability.

Doug & Renoir will not be available for the next 2 General meetings, so Doug will provide Julee with status before the general meetings, so they can continue as needed.

ACTION: While at TPAC, Doug will convey status on all pending projects before Friday General Meetings.

#### TOPIC: Migration

Renoir has done a plan. <http://docs.webplatform.org/wiki/WPD:Infrastructure/analysis/2013-Migrating_to_a_new_cloud_provider>

The HP contract is over. Doug is going to ask HP for another extension & offer HP visibility (find better word later) on the fact they started the project with us

Dreamhost is enthusiastic to host for free our full environment, but their new system is not ready for us. They will provide a full (vanilla) OpenStack environment. They are providing us a Replication MySQL node to help the migration and testing. As soon as the OpS installation is ready, Renoir set up the full migration work.

The time line depends upon Dreamhost to provide the environment (a blocker). Once we have in control immediately, Renoir thinks it should take a few days, then testing, as described in the doc. But the time he can't say, a lot of search & replace, and then the test, and then the live db transfer is the longest time.

Renoir says he's ready, just waiting. Doug says Renoir already started the migration, that the migration is going started ASAP.

The css properties has a dependency on a stable site. That's why we need to know when the migration work is being done.

Renoirb wants to make it clear that we MUST have a clone of the full production/live environment as soon as possible. as when we make changes, we are working on the production and a simple mistake can impact stability, and a change should only be a run of a script been tested many times before being run on the live site.

ACTION: Doug will contact Dream host and get dates, today.

#### TOPIC: Compatibility tables

Ronald Mansveld is working on the data model so all contributing sites can provide content according to the model.

We then need to find a way to present to the users, and how mechanically to sync the data. Doug did contract [Aaron Schulz](http://www.mediawiki.org/wiki/User:Aaron_Schulz) to prepare an utility to cache generated data, and thinks he's close to completion. But, since we might migrate away from MW. We do not need to have this data live. We just need to refresh the data, say, once per week.

We do not need an automated data at this time. Priority is to have the data available in a re-usable format and present within the wiki. Need to test (today) on the computability table.

We will disable editing the compatibility section. Julee suggested previously that if users find contrary data, they could submit an update (preferably test-driven, conforming to data model) to github. This community data source will then be one of the data sources. We might also find a way to plug to TestTheWebForward data.

Eliot request a mechanism to report an error or flag.

Phase one, however, is just to get some data into the css pages so we can get the css properties project out. We want to use MDN data first, and maybe caniuse.

Janet Swisher didn't know Ronald Mansveld was working on MDN data. If jswisher had known, she could have connected him with the right folks, she'll try and do so in the future. (jswisher confirmed that ronaldmasveld did talk to appropriate people at Mozilla London)

Doug believes we can finish Compatibility tables by the end of TPAC and possibly during it, should be at least in a working state and to test it. It would include not only the CSS properties, but be done across all features.

ACTION: Doug will confirm dates with Ronald Mansveld & Aaron Schulz today.

#### TOPIC: CSS vs. Beta announcement

For the CSS properties project, Doug suggests we "Declare victory and go home"

There is a need for us to say thank you to the community. By mid-November, we will be in a moment where we can do so.

But as jkomoros said, we have 1 more chance to make a big splash. So, we shouldn't call this beta.

Questions: why have a beta? when is a good time to have a beta?

Maybe it isn't good to announce between thanksgiving & xmas. Let's give a status update and showing achievements, just announce round 1 of css properties. Then, find an appropriate time to announce a beta when we have enough "meat" to show off as we only have one shot.

We could make a big fanfare, a coming ceremony for the beta, but we might never come to a point where we are in a complete, final state as it is the nature of the subject of the project. But we're not close to a beta announcement right now. A beta launch needs to be to the same level of efforts as the launch announcement. It might not be sufficient to only announce the css properties as the beta. The beta should include more. We should carefully consider what we have to say and what we're going to. How we are going to frame this. This round 1 of the css properties edits will be one of many granular announcements.

We've been talking publically about CSS properties, that's what we should announce.

Many folks agreed.

Julee again mentioned that we need to have a timeline for the compatibility tables & migration, so we know when css properties can be launched. (See discussions & outstanding action items from previous meetings.)

(On the IRC, renoirb also suggests also this as a blog post: <http://lists.w3.org/Archives/Public/public-webplatform/2013Oct/0148.html>)

#### TOPIC: Next content project

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

### ACTION ITEMS

-   While at TPAC, Doug will convey status on all pending projects before Friday General Meetings.
-   Doug will contact Dream host and get dates, today.
-   Doug will confirm dates with Ronald Mansveld & Aaron Schulz today.
-   Julee to send out notes so more folks can comment on the next content project.
-   Doug will contact Max Polk today.

## Agenda 2013-10-25: Canceled due to lack of quorum

## Agenda 2013-10-18

-   CSS Properties Project

|Status|Number|
|:-----|:-----|
|done|257|
|In Progress (Dave)|3|
|Low Priority|105|
|Needs examples (clip-rule, Doug)|1|
|Obso/Deprec|28|
|Vivienne just took! (table-layout)|1|
|Grand Total|395|

-   CSS Properties Project
    -   clip-rule status, Doug?
    -   who will volunteer for table-layout?
    -   other dependencies?
        -   compatibility tables
        -   legacy MSDN samples, related pages, and syntax section?
        -   flag simplification?
        -   review from CSS experts, spec editors & rockstars?
        -   launch plan?
        -   should we migrate first?
-   migration plan
-   JS project plan
    -   Should we do a plan, including community management, after a post-mortem on the CSS properties project?
    -   A bulk of work gets done at Doc Sprints, should plan include proposing Doc Sprints on a regular basis to get a bunch of stuff done?
-   WPD table at [html5devconf](http://html5devconf.com/) in SF: please volunteer
-   Internal Doc Sprint to get landing page & other site organization cleared up?
-   Doc-Sprint-In-A-Box, Piwik reporting: this is a job for the Cracker-Jack Analytics Team!
    -   A cogent set of steps for generating reports
    -   What metrics shall we report?
    -   Better UI for Piwik (presently unintelligible) - if possible
        -   "Goals \> Saves a Page" path makes no sense (what is this, some kind of mangled translation?)
        -   What the heck is a "conversion?"
        -   (I mean, really, sometimes this open-source stuff is incorrigible!)
-   Doc Sprint, New York in December
    -   Pro: New York, baby!
    -   Con: We're not ready yet; let's get JavaScript imported and scoped first

### Discussion

#### TOPIC: CSS Properties Project

Last night we had one property unowned but vivienne (who was at Zurich's docsprint) took it (yay!!!) she's great, from Jay's group what we have outstanding are a few properties that Dave is working on. We're not going to do an example for knockout. We created a correct syntax example, but put a larger example on hold. All of the remainders will get live code examples at code.webplatform.org. clip-rule example, Doug is working on. We should be done mid next week (Dave is out next Wed-Fri). [much rejoicing]

##### Subtopic: Dependency on compatibility tables

-   compatibility tables: first one is compat tables lots of activity about that this week, shepazu provided an update: at the doc sprint in amsterdam, we got to gether with PPK (he's from quirksmode, obviously) he invited the guy who does html5test.com he's been doing something like caniuse for something like ten years they're test driven what we want to do with this project is have a single data model that captures browser compat/test results for as much as we can we have permission to use MDN data, and because they are facts, we don't HAVE to attribute that use (but we plan to give attribution, just not changing the license on the articles that include it) Max Firdman (sp?) from MobileHtml5 wants to help too <http://mobilehtml5.org/> <http://html5test.com/> shepazu has a running prototype of a mediawiki extension that inserts compat information but it's a naive implementation and would cause caching problems html5test.com source code: <https://github.com/NielsLeenheer/html5test> the page would be constantly changing so it wouldn't be able to be cached by CDN I'm working on another approach renoirb has good ideas on that I got renewed energy from several people a guy named Ronald Manzfeld (sp?) stepped up and said, "if you need some server-side help, I could help" he got really into the idea of making the unified data model he started on that and has a first draft available. Niels Leenheer, guy behind html5test.com PPK, NIls (HTML5Test) and others are all on a new list: public-webplatform test. Ronald has been very active, interested in driving things forward we're also going to provide an aPI so others can get it (same API we will use) I think within a couple of weeks we'll have at least something workable

Granularity is part of the data model at docsprint, we all kind of agreed that we like the way that MDN chose a good level of granularity. there are several kinds of granularity: per feature, per browser version we thought the MDN model was pretty good, so we'll start with that. if we don't have the right kind of granularity, we'll fall back to MDN which will also be good in terms of completeness. lik ecaniuse only tests things that are new and up and coming and MobileHTML5, his granularity is quite different from caniuse. We're going to try to categorize their broader categories and capture that at a diferent level of granularity.

public-webplatform-tests?

ACTION: shepazu to send link to the public-webplatform-test list to main list [DONE]

 We'll do batch updates once a week or so the people who are involved in this (the data sources) are likely all amendable to changing their own data models a little bit. to make it easier to integrate one exception to the updates: probably won't pull from MDN very frequently probably a one time, given that there's not as good of an API there we'll have to come up with some tests for the tests to make sure our data retrieval kept the integrity of the system. This is great, especially having so many people pitching in with experience in this area. Hoping to complete by end of november at latest.

Do we have a plan for if someone finds an error in the data on WPD? The plan was to punt on that for now. Will expose our data on GitHub as well. we'll likely ask people (to start) to submit a PR wonders if we could have useful data from there <http://www.chromestatus.com/features> although of course ultimately we'll need to come up with an easy way to change it from our system probably not all that useful, but might be good for spot checking. Could be a phased approach where for the 260 properties if we do an early import, even if it's just from one source so we could not wait too long. ACTION: shepazu Talk to Ronald about perhaps doing a phased compat table approach, where we just do one data source to start (in order to move faster)

what does a conteingency plan look like? if we run into problems with the extension I'm writing (I'm going to talk to trenoirb and ryanlane later today about that, by the way) one possible contingency is to make a script to use the API for MDN to pull out their compat information, and we write a script to inserts that compat information into our pages. not generate a new page, just edit the apges we have make sure it's not automatically generated at serve time. Even if it's not possible to fully automate, even if we can automate the hard parts, we might be able to make it feasible for a small number of volunteers to copy/paste/massage my point is mainly "just think scrappy" If full-automatic isn't easy, even semi-automatic is better than nothing.

##### Subtopic: Dependency on legacy MDN samples

Some residual sections were imported (especially code examples, related pages and syntax) automatically. we had talked with renoirb about doing a bulk find/replace operation if we can't do it by script, we can probably do it manually--just need some volunteers Eliot: We're hoping to get confirmation today for a facilities reservation for University of Washington on 11/2 that sounds like a great project for students to tackle. [murmurs of agreement] if renoirb can run a script to at least identify pages that need this, that would be helpful, but he has a lot to tackle right now I have a lot of other things on my plate scottrowe\_: There's a lot on renoirb's plate, we should have a separate meeting to figure out prioritzation of infrastructure tassks renoirb: For now my focus is on migration ACTION: julee to write up bug (cc eliot) about investigating feasibility of finding pages that need old MSDN sections removed

##### Subtopic: Dependency on reviews by experts

Review by experts & get them thinking about the project so they're ready to talk about the launch when it happens. Two categories: spec experts, and rockstars the former is for shepazu, the latter is for jkomoros ACTION: jkomoros to ask paul\_irish to do a spot check of WPD CSS properties

##### Subtopic: Dependency on launch plan

jkomoros on that AI basic idea is a plan for a few weeks from now about blog post, who to get to support the launch. ACTION: jkomoros to create strawman launch plan (including relative timeline) What's the timeline? The long pole is the compat tables for now so that will depend on information from that taskforce about if they can do a quick and dirty import. So we're going to say we're dependent on that functionality, it's a good idea to have compat information, even if it's not the Super Awesome Amazing Automatic version We might have a contingency plan for CSS properties, even if the SAAA version isn't ready yet so let's get feedback from compat table group, and base dates on that.

##### Subtopic: Dependency on migration

Doug earlier brought up: should we migrate before announcing? But says "no." The new provider is getting prepped to beta, a feature we could use at the end of the month I told renoirb to consider migration as top priority. Ideally ryan can help with it as well [09:41:14] Ryan\_Lane nods [09:41:14] \<Ryan\_Lane\> I can Since we're blocked on compat tables, at least starting the migration could be a good thing. One question is: if we finish before migration, do we wait for migration/ slash, is there enough bandwidth to do compat tables and migration? renoirb will advise on compat tables, but the two work streams don't overlap TOO much but I'll verify with Ronald ACTION: shepazu to verify with Ronald/renoirb that compat tables and migration work streams are independent.

Renoirb has a branch where I got less-and-less hardcoded configuration. Which is the main requirement to migrate. We can almost definitely do it without downtime.

The other question is the risk of the migration: Whether it will cause more problems. We're not not sure. We have a known "OK-not-great" solution now. The new solution is an unknown. We should COUNT on errors during migration. No matter what, after a migration we'd need to test. We have a hard stop with current provider so we need to work back from that key date. It would be nice to see what that timeline looks like--a couple of days, a couple of years--then we can map that against a timeline for releasing CSS properties project if we find that things like "announcing" are overlapping with "testing", it won't be good. ACTION: shepazu to confirm date of contract expiration with current hosting provider ACTION: julee to make basic timeline for completing CSS prop project; ACTION: renorib to create basic timeline on migration

Then, we can see how they interact.

#### TOPIC: JS project plan

We could do a postmortem on CSS props project (even in email), figure out what worked and what didn't. Use that to inform a high-level plan of tackling JS project Doc Sprints lead to TONS of work getting done so JS project plan should incorporate a schedule of doc sprints that different folks could volunteer to run. About.com who is enthusiastic about JS topic in particular for their upcoming doc sprint. JS plan should be ready by December. During November, we should prep for this. ACTION: shepazue to work with Max Polk to make sure his migration is up to speed we got review from two different experts on the JS architecture ACTION: shepazu to forward e-mails from JS experts about architecture on to list ideally we'd run through a few WPW sprints before the doc sprint to make sure we're ready for the doc sprint WPW is an ongoing second tier to in person doc sprints so we should pay attention to that during planning.

#### TOPIC: WPD table at HTML5DevConf

Shepazu got a table for W3C at the HTML5DevConf in SF next week we have me, Rebecca Hauk manning table but we need more volunteers we have some shirts and stickers, but we could use more swag. Shepazu has 3 free tickets for volunteers. We left a big pile of t-shirts in Amsertdam

#### TOPIC: PiWik reports for Doc Sprints

scottrowe\_ looked into generating the PiWik reports about doc sprint played around for awhile, but there's no way to scale this. We need to make some decsiions about what reports we're going to generate and provide steps for doc sprint owners and fix some things about piwik user interface but we should defer to analytics meeting.

#### TOPIC: Google contractor!

Alex will let us know if Google adds another contractor. Stay tuned…

### Action Items

-   shepazu to send link to the public-webplatform-test list to main list [DONE]
-   shepazu Talk to Ronald about perhaps doing a phased compat table approach, where we just do one data source to start (in order to move faster)
-   julee to write up bug (cc eliot) about investigating feasibility of finding pages that need old MSDN sections removed
-   jkomoros to ask paul\_irish to do a spot check of WPD CSS properties
-   jkomoros to create strawman launch plan (including relative timeline)
-   shepazu to verify with Ronald/renoirb that compat tables and migration work streams are independent.
-   shepazu to confirm date of contract expiration with current hosting provider
-   julee to make basic timeline for completing CSS prop project;
-   renorib to create basic timeline on migration
-   shepazu to work with Max Polk to make sure his migration is up to speed we got review from two different experts on the JS architecture
-   shepazu to forward e-mails from JS experts about architecture on to list ideally we'd run through a few WPW sprints before the doc sprint to make sure we're ready for the doc sprint

## Agenda 2013-10-11: Canceled due to lack of quorum

## Agenda 2013-10-04

### Agenda

-   CSS Properties status

|Status|Number|
|:-----|:-----|
|done|209|
|In Progress|20|
|Low Priority|113|
|Needs Review|37|
|Obso/Deprec|8|
|TBD|60|
|Grand Total|447|

-   site stability
-   Doc Sprint in a Box
-   WPD Birthday next Tue: list activities/URLs
-   Change this meeting time/day?
-   Anything else?

#### Topic: CSS property status

scottrowe\_ emailed the list of 95 properties … the coordinators should contact those people individually … and if we can't get those people, we'll reassign them <http://docs.webplatform.org/wiki/WPD:Community/Meetings/General> while scott compiled the list of properties, Julee reconstructed a master list & categorized them according to status. She will put this in a google doc to manipulate it more easily we should still have TBDs on the wiki, so people can sign up… and it's out of date

there are about 60 that need to be done, and 35 need review

#### Topic: Doing experimental properties

some have said we should only work on things that are not experimental, but there's value for us to do more cutting-edge stuff since we're closer to the development of the specs and implementations also good for SEO we need to be careful about updating examples The idea we had in mind is a mechanism. Isn't going to happen in the next 6 months for now maybe we could do this: W3C has a DB, with a unique URL for each spec, so we could come up with something where we are working off a draft version , script that trolls publications every day, sends an email w/ a list of specs that have changed, validated against URL ACTION: shepazu & eliot to brainstorm w/ Robin at TPAC

#### TOPIC: site stability

Getting server & client-side errors on dabblet Are we doing any stability testing? ACTION: Renoir to write up his testing plan, and add all relevant systems to that plan, such as Dabblet instance julee: we could also ask the community to help with testing

#### Topic: Doc Sprint in a Box

<https://docs.google.com/document/d/1fIDssDZln2Z_DrnKliT1ymZpn_OTqdYA7rVgMaTsSk4/edit> ACTION: Millo to review doc sprint in a box, add some comments, and update it based on what we've learned internally

ACTION: scottrowe do an edit pass stripped down to its main purpose which is to have community members throw doc sprint ACTION: scottrowe to share with Patrick D'Souza for review

#### Topic: WPD Birthday next Tue: list activities/URLs

doing it on OCtober 8 would be best, since it's the birthday, but we have no volunteers; maybe the WPD twitter account could be the lead, and eveyone else could retweet

scottrowe\_ needs anecdotes, but I'll write the blog post ACTION: Julee to forward Scott's email & get them to commit to tweet & point to the blog post. We looked very much on the same page 1 yr ago: we should look that way now. ACTION: scottrowe\_ will write the blog post, hopefully by Thursday.

#### topic: Change this meeting time/day?

ACTION: Julee to send a query email & ask if we should Change this meeting time/day?

### Action Items

-   shepazu & eliot to brainstorm w/ Robin at TPAC
-   Renoir to write up his testing plan, and add all relevant systems to that plan, such as Dabblet instance
-   Millo to review doc sprint in a box, add some comments, and update it based on what we've learned internally
-   scottrowe do an edit pass stripped down to its main purpose which is to have community members throw doc sprint
-   scottrowe to share with Patrick D'Souza for review
-   Julee to forward Scott's email & get them to commit to tweet & point to the blog post. We looked very much on the same page 1 yr ago: we should look that way now.
-   scottrowe\_ will write the blog post, hopefully by Thursday.
-   Julee to send a query email & ask if we should Change this meeting time/day?

## Agenda 2013-09-27

### Agenda

-   Piwik and the Analytics is back on track!
    -   Analytics: Create a secret starting page that will help track activity during a doc sprint (TBD, probably next week)
    -   Analytics: Improve the goal tracking using Piwik's API and JavaScript
    -   Infra: Changing datacenter?
-   Doc-Sprint-In-A-Boxathon scheduled for next wednesday.
    -   Everyone is welcome to join, Patrick.
    -   Scott will send out a note.
    -   Goal is to have this done before the Amsterdam Doc Sprint, possibly even earlier.
-   CSS properties tables

### Discussion

#### TOPIC: PiWik/ Analytics

Piwik and the Analytics are back on track. Two weeks ago Renoir deployed PiWik in a different way than before without going too deep, it was in the same way as before (Fastly), putting a different tracking code on all of the pages should have covered all of the pages, with the help of Patrick, create goals in the dashboard & campaigns. Now forwarding all of the e-mails to the analytics mailing list. Julee & Eliot filed a bug and I responded to an earlier filed one that represents requirements for the dashboard. At the analytics meeting next week we could consolidate requirements and finalize that list. All bugs & discussion is on <http://docs.webplatform.org/wiki/WPD:Requirements/Analytics> Renoirb gives a rough geolocation, might need to recrunch the database; some other work: a way to trigger conversions in the goals (like clicking on edit or save), will require adding JS if we get it in place before the docsprint, we can track progress. Scott\_rowe will show up at next analytics meeting to discuss.

-   ACTION: Scott\_rowe to attend analytics meeting on Monday 4pm pdt

#### TOPIC: Infra: Changing datacenter?

No news. Worked with Doug on that. Didn't get any feedback from anyone yet, but time is passing working to rebuild the VM from scratch as much as renoir can in the same environment. We either need to move soon, or do the move next month Still trying to connect up with Dreamhost and other folks

#### TOPIC: Doc-Sprint-In-A-Boxathon scheduled for next wednesday

I asked Jay to take leadership of kicking this off I think that he is working on the general structure of the thing right now, Jay sent an e-mail about the timing, but also an e-mail from Scott and Peter where they had a draft docsprint in a box: a brain dump about all of the things we thought should be in there. Not intended to dictate the structure. just making sure that before the meeting we wrote down what we had learned from doing a few. Jay also had an idea of the structure he wanted.

-   ACTION: scottrowe to send an e-mail to the list to invite anyone who's interested to get involved with the docsprint in a box I think Jay sent an invite to Patrick, but we should confirm

#### TOPIC: CSS properties tables

We discussed how to manage the tables. Also, coordinators need to verify that each property they are coordinator for is properly reflected in table. Julee & Eliot have done this. Chris Mills, Shepazu & Nic d'Costa needs to do this.

-   ACTION: Julee to remind Nic & Doug to update their properties in the tables. [DONE]
-   ACTION: ??? to contact Chris.

We discussed doing a script to import all properties into project.webplatform.org, but really the work is manual checking at this point. <https://scraperwiki.com/>

Creating a JS project in the project tracker and populating it makes sense for when we start a new project, especially since we've fixed the sendmail time-out bug.

-   ACTION: scottrowe\_ and julee to work at creating a new list of unfinished CSS properties

### Action Items

-   Scott\_rowe to attend analytics meeting on Monday 4pm pdt [STATUS: Everyone was a no-show. Will happen next Monday, instead.]
-   scottrowe to send an e-mail to the list to invite anyone who's interested to get involved with the docsprint in a box I think Jay sent an invite to Patrick, but we should confirm [DONE]
-   Julee to remind Nic & Doug to update their properties in the tables. [DONE - Julee & scottrowe did them]
-    ??? to contact Chris. [Resolved]
-   scottrowe\_ and julee to work at creating a new list of unfinished CSS properties [DONE]

## Agenda 2013-09-20

Objective: Describe the current state of the project.

Note, the objective does not include making any decisions or otherwise taking any actions other than those required to understand the state of the project. This should be a very short, concise meeting.

-   WPW update - status?
    -   Have coordinators verified the status of each page in their purview?
    -   We need to consolidate the tables into a final master list of properties to be worked on, and we want to include only those properties still being worked.
-   WPW reinvigoration - what do we need to do to put some life back into this?
    -   We've dropped to 50 active users/month.
    -   Are site performance problems a contributing factor?
-   State of WPD for the birthday - what have we accomplished?
-   Who's in for Amsterdam?
-   Doc Sprint New York?
-   We're out: print up some new t-shirts?
-   Reminder: Doc Sprint in a Box, Oct. 2
-   JavaScript import status?
-   Compatibility automation status?
-   Analytics & reporting?
-   Back-end update from Renoir?
    -   Piwik enhancements in a nutshell
    -   Site performance - what are the problems and what is preventing solutions?
-   Next week's blog post author
-   Anything else?

## Agenda 2013-08-23

-   Roll call
-   Review of open action items
-   [WPW](/Meta:web_platform_wednesday) - how is it going?
    -   [Additional properties to add to this project?](http://lists.w3.org/Archives/Public/public-webplatform/2013Aug/0146.html)
-   Anything blocking you from creating great content?
-   Anything new & notable? (Blogs or other communications planned for next week?)

## Agenda 2013-08-16

-   Roll call
-   Review of open action items
-   [WPW](/Meta:web_platform_wednesday) - how is it going?
    -   Schedule
    -   Who's coordinating?
    -   Action items cleanup: Please search for your name on this page.
-   Infrastructure meetings
-   Communications plan
-   Anything blocking you from creating great content?
-   Anything new & notable? (Blogs or other communications planned for next week?)

### Discussion

#### TOPIC: WPW - how is it going?

julee: We have three coordinators, but no contributors. A lot of people are busy or on vacation. Originally we had an optimistic schedule to be done by august after reviewing with a few folks, everyone thought that was way too optimistic especially given summer vacation period. We will put in a buffer week after labor day, & add incomplete properties back onto the pile. After the end of august, Microsoft will have some resources that we'll be adding to this one of my writers will be helping, another writer who hasn't worked on this yet will be helping as well. Google is working on a contractor as well, and scottrowe will be helping out with coordinating as well

Bumping up the boolean values for things like animated values in the CSS properties template, and also Inherited field. Maybe Frozenice can ? ACTION: julee to reach out to frozenice assigning the "non-boolean properties for animatable, etc" template issue to him

#### TOPIC: Servers

shepazu: We'll be talking to dreamhost later but ryan and renoirb think it's a good thing to have redundancy across hosts renoir contacted a few different hosts including Digital Ocean and iWeb the latter is based in Quebec so renoirb can talk to them in shepazu: Dreamhost asctually wants to be involved in the project as a steward \<patrickdsouza1\> renoirb: good to look at hosts in a different time zone like europe. \<renoirb\> iWeb data center: <http://iweb.com/green-data-centers> renoirb: I talked to them. The idea is a main one and another one that's latent, that we have a copy of everything; if we need to change we just flip a switch. Looked around for one with a good reptuation with multi site. iWeb's president is going to talk to us by Tuesday of next week We need to have a different company/place to back up stuff on a regular basis, but if you have multiple instances across diffferent companies, you have a huge latency issue. Ryan\_Lane has a preference towards openstack clouds, as its open source nature aligns well with our project if dreamhost can provide us with the different locations/datacenters, then is the secondary company just a single backup instance? We will roll out redundancy as needed the idea is to have redundancy between prod and test. Julee asked for an architecture document that describes our setup with a nice diagram, and references to justifing it.

#### TOPIC: Server status

Also, server status page (going to be on our own sub-domain for sure): <http://webplatform.tumblr.com/>

#### TOPIC: Infrastructure meeting

At infrastructure meeting, most of the discussion was about how to prioritize renoirb's work schedule; we're going to use projects.webplatform.org. Once community has a decision, having execution focused meetings is helpful to add it into the issue tracker (if there are issues that aren't recorded yet, we'll raise them there), executing on things that have already been decided in the community meetings or over e-mail on the list, taking the decisions from the group and parsing down into actionable things and track them in project.wwebplatofm.orgexposing it in the dashboards/reports, so the current health is viewable by anyone. Everyone is welcome at the infrastructure meeting, but because julee/shepazue/renoirb are full-time on this project, we'll take responsibility to keep track. 11am Pacific on Mondays, and we can move it if others want to attend regularly.

#### TOPIC: Communications plan

There's been so much activity, I want to have people talk about what they're doing Renoirb got access to the social medial outlets, G+, twitter, FaceBook. Ideally we'd be able to automate publishing a post to all outlets, with a buffer system to space out updates too and space out updates on different channels. Updates should be scheduled to not only USA time but for those in Europe and the rest of the world and the status tumblr, when something happens that we want to talk about, the conversation wil lgo to the tumblr status regarding the policies, I think we should keep it the same: vendor neutral, information on status eliots blog proposal : how & why we blog; we'll have an editorial calendar; start looking for repeating blog posts; \<nicdaCosta\> with regards to tumblr and the new G+ community, is it necessary to have so many outlets? And would there be a given "purpose" for each outlet? WPD calendar in g+ may not be sufficient for an editorial calendar

looking forward to seeing Coalie Mercier, from the W3C MarComm staff, her work & what she wants to do for the future we need a regular voice AI: R/S/J in project.wp.org, we could rename project community management; create tasks, give ownership, tag twitter, blogpost, whatever, infographics, etc.

### Action Items

-   CARRIED FORWARD: Everyone to review the general meeting notes for actions assigned to them that aren't marked "(DONE)" and update with status as described above. (Mostly done: Doug & Renoir to do.) (CARRY FORWARD)
-   CARRIED FORWARD: shepazu make "can you tell if this page is ready for consumption or needs more work" an active question for css project reviewers. (CARRY FORWARD)
-   CARRIED FORWARD: Julee make sure editing guide is updated with new flag values, when flags are done. (Has a dependency on flags being done) (CARRY FORWARD)
-   CARRIED FORWARD: Alex to talk to Paul irish & other folks on the list that Eliot pointed him to (a list that we created at launch?) about reviewing "done" pages. (In progress: jkomoros talked to paulirish yesterday, who is in when needed; dependency on more content being done. Tracking this in the CSS Properties endgame schedule.)
-   CARRIED FORWARD: shepazu to figure out how to move current flags to new flag types and cc jkomoros and frozenice. (CARRY FORWARD Tracking this in the CSS Properties endgame schedule.)
-   shepazu to make sure Lea incorporated Chris Coyier's feeedback as appropriate.
-   CARRY FORWARD: Shepazu & renoirb to review Lea's actions item and reassign and to reassign ownership of project.webplatform.org. (CARRIED FORWARD)
-   R/S/J in project.wp.org, we could rename project community management; create tasks, give ownership, tag twitter, blogpost, whatever, infographics, etc.

## Agenda 2013-08-09 Meeting canceled due to lack of agenda

## Agenda 2013-08-02

-   Roll call
-   Welcome to Renoir!
-   Review of open action items
-   [WPW](/Meta:web_platform_wednesday) - how is it going?
    -   Endgame schedule
    -   We need coordinators & contributors -- but especially coordinators
    -   Action items cleanup: Please search for your name on this page.
        -   It's probably associated with an action item. Either:
            -   Mark it as (DONE)
            -   Mark it as (DUE: \<date\>) (really, only pre-launch or post-launch)
            -   Mark it as (STATUS: NO LONGER IMPORTANT) or some other STATUS
        -   Next week, Julee will email you, and cc list, all Action items that need to be done before launch.
-   Analytics meeting is moving to Monday 4pmPDT/7pmEDT
-   We're going to move to proactive notification regarding system issues:
    -   We'll set up a status page of server
    -   We'll email public list and update the irc channel status (webplatform webplatform-site) when there's problems; when work on the system affects UX.
-   Max's [JS file import plan](/WPD:Projects/javascript) ready for language expert reviews
-   [Group calendar](https://www.google.com/calendar/embed?src=gqaik6l023aodhh4m24qapctpg%40group)
-   SSL Certificate for TLD and sub-domains
-   Dev backlog in a new Wiki namespace; e.g. WPD:Development/ProjectA

### Discussion

#### TOPIC: Welcome to Renoir!

[much rejoicing]

Shepazu chose Renoir because he has a good balance of backend/sysadmin skills, frontend/backend development, design, and also because of his interest in the topic and history of community outreach. Great combination of skills for this project.

Renoir is based in Montreal, so on east coast time-zone, which is convenient for working with Shepazu but also he can be up early enough to work with europeans, but also people on the West Coast.

We'll keep contracting with Ryan as we need him, given his expertise. Renoir has already helped with the recent instability problem.

Official start date was August 1. Vacation to Paris for one week, August 30th

#### TOPIC: Lea is not at W3C

Wednesday was Lea's last day at W3C. Lea had a great mix of design/front end skills. Renoir has some of those skills (mostly on development side). She didn't design icons, illustrations, etc, so as I'm looking for a new person we can focus on people with strong UX/UI skills, ooking at 10-12 candidates already. We have a job description on W3C's site. <http://www.w3.org/Consortium/Recruitment/#design-webplatform>

 ACTION ITEM: julee: We need someone to review Lea's actions item and reassign, and to reassign ownership of project.webplatform.org.

#### TOPIC: Action items cleanup

-   Action items cleanup: Please search for your name on this page.
    -   It's probably associated with an action item. Either:
    -   Mark it as (DONE)
    -   Mark it as (DUE: \<date\>) (really, only pre-launch or post-launch)
    -   Mark it as (STATUS: NO LONGER IMPORTANT) or some other STATUS
    -   Next week, Julee will email you, and cc list, all Action items that need to be done before launch.

ACTION: Everyone to review the general meeting notes for actions assigned to them that aren't marked "(DONE)".

#### TOPIC: WPW - how is it going?

#### SUBTOPIC: Endgame schedule

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

##### SUBTOPIC: Flags

Lea & shepazu have the action item to actively ask reviewers:

"can you tell if this page is ready for consumption or needs more work"

Basically, the requirement that when a person lands--we have 4500 pages on WPD, we've been working on 200-300. Users need to figure out when they're looking at an article, whether it's ready to consume or not.

So flags will be moved to a more discrete place.

Lea has prototyped the flags. renoirb has extracted those, we're ready to put them in when we get the flag stuff done.

#### TOPIC: dreamhost

Shepazu talked to dreamhost (at least one person there) at hosting the site. And possibly being an active steward.

ACTION: renoirb: needs to be involved in the dreamhost conversations to make sure they have what we need.

#### TOPIC: Analytics meeting moving to Mondays

Analytics meeting is moving to Monday 4pmPDT / 7pmEDT.

#### TOPIC: Max's JS file import plan

Max's JS file import plan ready for language expert reviews <http://docs.webplatform.org/wiki/WPD:Projects/javascript>

#### TOPIC: Google Calendar

Google calendar is up. This is most presently for folks to add the times where they're available to help with WPD, and when they're unavailable.

renoirb: can see the calendar there, no events

<https://www.google.com/calendar/embed?src=gqaik6l023aodhh4m24qapctpg%40group>

#### TOPIC: proactive notification regarding system issues

We're going to move to proactive notification regarding system issues

-   We'll set up a status page of server
-   We'll email public list and update the irc channel status (webplatform webplatform-site) when there's problems; when work on the system affects UX.

Renoir set up a system that will notify himself and Doug when the site is down.

Low-hanging fruit to set up have a simple system that lets people know what the status is if it's going wrong. Something like status.webplatform.org, to say either it's a known outage or unknown.

#### TOPIC: Dev backlog

Dev backlog in a new Wiki namespace; e.g. WPD:Development/ProjectA

That way, we can store dev projects there.

When your infra fails… it happens to also affect the status view.

Please use project.webplatform.org when possible to create and track projects once they move from the proposals phase.

#### TOPIC: SSL Certificate for TLD and sub-domains

No time to discuss SSL Certificate for TLD and sub-domains.

renoirb & shepazu will take it off line.

### ACTION ITEMS

-   CARRY FORWARD: Everyone to review the general meeting notes for actions assigned to them that aren't marked "(DONE)" and update with status as described above. (STATUS: Mostly done: Doug & Renoir to do.) (CARRIED FORWARD)

AI: renoirb: needs to be involved in the dreamhost conversations to make sure they have what we need. (DONE & ongoing) AI: shepazu and julee to make a more concrete plan with numbers about steward asks, and eliot/alex will respond with their donations. (DONE) AI: shepazu to reach out to other stewards to make sure they respond to the concrete plan asking for help. (STATUS: In progress - eliot found that mail to be eloquent and effective. Tracking this in the CSS Properties endgame schedule.)

-   shepazu to look into if we need separate HTMLElement and SVGElement templates for ITS project (Unless they come to us with problems, we'll assume they're okay)
-   Jirka to create overview/tutorial on ITS. (STATUS: In progress.)
-   shepazu to confirm compatibility tables will be done in time. (STATUS: Not much progress because of renoir's other duties, we made good progress before that, it's high on Renoir's priority list, once stability stuff and reporting stuff is done, it's not going to be that much work after that. Tracking this in the CSS Properties endgame schedule.)
-   Julee to call out in property review checklist that people should verify MSDN examples, and either replace with better examples or move to code.webplatform.org. (DONE: <http://docs.webplatform.org/wiki/Meta:web_platform_wednesday/reviewer_checklist>)
-   CARRY FORWARD: shepazu make "can you tell if this page is ready for consumption or needs more work" an active question for css project reviewers. (CARRIED FORWARD)
-   CARRY FORWARD: Julee make sure editing guide is updated with new flag values, when flags are done. (Has a dependency on flags being done) (CARRIED FORWARD)
-   CARRY FORWARD: shepazu to figure out how to move current flags to new flag types and cc jkomoros and frozenice. (CARRIED FORWARD Tracking this in the CSS Properties endgame schedule.)
-   CARRY FORWARD: shepazu to contact CSS wg about reviewing "done" pages. (Leaverou started a thread, but not to CSSWG. Dependency on more content being done.) (CARRIED FORWARD Tracking this in the CSS Properties endgame schedule.)
-   CARRY FORWARD: Alex to talk to Paul irish & other folks on the list that Eliot pointed him to (a list that we created at launch?) about reviewing "done" pages. (STATUS: In progress: jkomoros talked to paulirish yesterday, who is in when needed; dependency on more content being done.) (CARRIED FORWARD Tracking this in the CSS Properties endgame schedule.)
-   CARRY FORWARD: Shepazu & renoirb to review Lea's actions item and reassign and to reassign ownership of project.webplatform.org. (CARRIED FORWARD)
-   ACTION ITEM: Shepazu to talk to Ryan about the 503s. (DONE: Garbee and Renoir talked to him more extensively, a bunch of jobs weren't getting performed, and the backlog was causing problems. Think he's resolved that.)
-   renoir to look at server errors in more depth. (DONE: Got more confirmation last week; a hard confirmation. Working this afternoon to make the piwik switch today. Trying to recreate infrastructure locally to be able to test it. Succeeded in getting it running locally, will publish my workspace on github soon, so anyone else can build it completely after, of course, removing sensitive information and history
-   CARRY FORWARD: shepazu to reach out to Julien and Rick Byers regarding JS plan. (STATUS: In progress: Shepazu reached out to rick byers, julien, and rick Waldron. Needs to pass info back to Max.)

## Agenda 2013-07-26 Meeting canceled due to lack of quorum

## Agenda 2013-07-19 Meeting canceled due to lack of quorum

## Agenda 2013-07-12

-   Roll call
-   Review of open action items
-   ITS
-   [WPW](/Meta:web_platform_wednesday) - how is it going?
    -   Other MBF issues?
        -   compatibility tables (Doug)
        -   data types & units done (Julee) (DONE)
        -   code samples switched from MSDN to code.webplatform.org
            -   Julee to add it as a review checklist (DONE)
        -   schedule high-level reviews (Doug & Lea)
            -   CSS WG, for instance: template change recommendations of WG? (e.g.: animatable is not a simple boolean)
            -   visual, or UI indication of whether or not any given page is ready or not
            -   incorporate Chris Coyers UI feedback (Lea)
        -   review from famous devrel people (paul irish, chris coyier) (Alex)
            -   visual, or UI indication of whether or not any given page is ready or not
        -   a launch plan (Alex)
        -   All systems ready check
            -   We can handle additional traffic
            -   All SysOps & DevOps folks are notified to expect additional traffic & should not tweak the site during the first
    -   Who will be a coordinator for the next 2 weeks?
-   Max's JS file import
-   Anything blocking you from creating great content?
-   Anything new & notable? (Blogs or other communications planned for next week?)

### Discussion

#### Topic: Zurich docsprint

Jay asked for retweeting from various official twitter handles about the Zurich Docsprint.

Please retweet and otherwise promote: here: <https://twitter.com/klick_ass/status/355063210086383619> +1/Share this:<https://plus.google.com/u/0/100575683580946332118/posts/EjJ9r6WCBXg> Repost here: <https://alpha.app.net/klick_ass/post/7550831>

#### Topic: Jirka's ITS project

Jirka shared with us:

ITS developed something back 6 years ago in Firefox, mainly for XML, also XHTML just a set of metadata that could help translation like a translate attribute that could say whether or not the content should be translated. ITS developed several such attributes, and because it was not sufficient for more complex things, we developed v2.0 which added more localization metadata. because it was clear that HTML5 was taking off, we provided a way to map those attributes to they have a prefix. It's published as a proposed recommendation. Not expecting any changes to not all implementations make use of all ITS attributes yet. For example, Google Translate and Microsoft Translate support translate attribute. And that attribute also is now in HTML5 formally. We thought it might be a good idea to recommend those attributes on web platform.org, since they're an integral part of HTML (or becoming that way).

Action Item: Jirka to send to the public email list something where we can see it in action? public showcases, videos, slides.

ITS should have its own namespace on WPD. But we should consider other things about the translation or multi-lingual stuff that might be a better larger bucket, such as unicode stuff, or some other internationalization bucket, a internationalization/multi-lingual namespace…

Reference area as well.

ITS is mostly attributes, with a few elements. It's a little bit tricky because HTML doesn't allow you to use your own elements in own namespace. So you can interlink to an external ITS file, similar to linking a stylesheet.

ITS probably will not require any templates than our current Element and Attribute templates.

#### Topic: CSS Properties project end game

##### Subtopic: Stuff to do before we are "done"

(See outline of things blocking us completing the project.)

We think we can get the compatibility tables done in time.

ACTION ITEM: shepazu to confirm compatibility tables will be done in time.

ACTION ITEM: julee to explain on the list what's happening with the messy data types, defining what we need to do to fix it. (DONE)

A lot of the content that was donated had samples in them. The view sample link points to MSDN. We need to switch the code samples from MSDN to code.webplatform.org.

But really, a lot of the samples are stale. They should be reviewed.

Easiest fix: after pages have been updated and reviewed, search for MSDN links and delete any of those links. More complex: programmatically update to move to code.webplatform.org.

ACTION ITEM: Julee to call out in property review checklist that people should verify MSDN examples, and either replace with better examples or move to code.webplatform.org. (DONE)

##### Subtopic: Visual indication that a page is "done"

How can the user tell if a page is ready for consumption or not. We're working on P2-P3 properties, but there are a bunch more. Want to make it clear to users which ones are vetted.

Are our new flags a good enough indication to first-time visitor that it's ready for consumption? Yes, if we are consistent.

ACTION ITEM: Lea & shepazu make "can you tell if this page is ready for consumption or needs more work" an active question that they're asking people in the other reviews, validate with folks that it's clear with them.

ACTION ITEM: Julee make sure editing guide is updated with new flag values, when flags are done.

ACTION ITEM: Lea & shepazu to figure out how to move current flags to new flag types and cc jkomoros and frozenice.

##### Subtopic: High level "expert" reviews

We'd like to get feedback, fine touches, and the green light from CSS working group and other "famous devrel people".

ACTION ITEM: shepazu to contact CSS wg about reviewing "done" pages. ACTION ITEM: Alex to talk to Paul irish & other folks on the list that Eliot pointed him to (a list that we created at launch?) about reviewing "done" pages.

ACTION ITEM: Lea to incorporate Chris Coyier's feeedback as appropriate.

##### Subtopic: System stability

Julee & others are getting a lot of 503 issues.

ACTION ITEM: Shepazu to talk to Ryan about the 503s

Maybe we need a "systems ready" line item in the guidelines for launching. If we get activity for this "launch", we should be confident we aren't going to crash.

Also, need to let Ryan and all know not to tweak production site for first few weeks of launch.

Also leaverou reported a bug on production site. She can't deploy to test wiki, only production wiki.

ACTION ITEM: Lea to send infrastructure bug (can't deploy to test wiki, only production wiki) directly to Ryan. (DONE)

##### Subtopic: we need more coordinators

Julee and shepazu cannot keep up with the contributors and properties. We need coordinators. So, every Tuesday, please volunteer. Eliot is busy until August. (Props to Eliot for calling in on vacation!)

When active folks are going to be unavailable, we need to have people hand off the things to someone else.

Up-front work, but then we have another coordinator!

We had some good coordination beginning, but it's petered off. Folks are generally concurring: people are distracted with other things, it's the middle of summer…

Julee is manually going back to previous contributors and re-engaging.

It's fine to have this problem NOW, but to make sure it doesn't happen in the future, we need to establish a mechanism.

#### Topic: JS import project

Max and Phistuck have been working out the final structure of the JS import. Let's get some JS experts who would be interested in reviewing the structure they're working out. Also, they might be at a blocking point; relying on naming convention for DOM, which I'm not sure if we settled or not. We need to sort out the details for the import.

We want to make sure they're not aiming at a moving target on the DOM side.

ACTION ITEM: shepazu to reach out to Julien and Rick Byers.

ACTION ITEM: Julee to make sure we have one page where we solidify what Phistuck and Max want.

ACTION ITEM: jswisher to reach out to Dave Brouant (sp?)

### Action Items

-   shepazu to look into if we need separate HTMLElement and SVGElement templates for ITS project
-   Jirka to create overview/tutorial on ITS.
-   shepazu to confirm compatibility tables will be done in time.
-   julee to explain on the list what's happening with the messy data types, defining what we need to do to fix it. (DONE)
-   Julee to call out in property review checklist that people should verify MSDN examples, and either replace with better examples or move to code.webplatform.org. (DONE)
-   Lea & shepazu make "can you tell if this page is ready for consumption or needs more work" an active question that they're asking people in the other reviews, validate with folks that it's clear with them.
-   Julee make sure editing guide is updated with new flag values, when flags are done.
-   Lea & shepazu to figure out how to move current flags to new flag types and cc jkomoros and frozenice.
-   shepazu to contact CSS wg about reviewing "done" pages.
-   Alex to talk to Paul irish & other folks on the list that Eliot pointed him to (a list that we created at launch?) about reviewing "done" pages.
-   Lea to incorporate Chris Coyier's feeedback as appropriate.
-   Shepazu to talk to Ryan about the 503s
-   Lea to send infrastructure bug (can't deploy to test wiki, only production wiki) directly to Ryan. (DONE)
-   julee to explain on the list what's happening with the messy data types, defining what we need to do to fix it. (DONE)
-   shepazu to reach out to Julien and Rick Byers regarding JS plan.
-   Julee to make sure we have one page where we solidify what Phistuck and Max want.(DONE)
-   jswisher to reach out to Dave Brouant (DONE)

## Agenda 2013-06-28

-   Roll call
-   Review of open action items
-   [WPW](/Meta:web_platform_wednesday) - how is it going?
    -   Who will be a coordinator for the next 4 weeks?
    -   How should we circle back around to folks who have previously showed interest?
        -   Julee started a CRM for community contributors. (DONE)
    -   What MBF for CSS properties?
        -   compatibility tables
        -   data types & units done
-   Demian's Tech Centers - how is it going?
-   [Max's JS file import](http://lists.w3.org/Archives/Public/public-webplatform/2013Jun/0075.html)
-   [revamping flags!](http://lists.w3.org/Archives/Public/public-webplatform/2013Jun/0174.html)
-   Anything blocking you from creating great content?
-   Anything new & notable? (Blogs or other communications planned for next week?)

## DISCUSSION

#### TOPIC: WPW - how is it going?

##### SUBTOPIC: Who will be a coordinator for the next 4 weeks?

People aren't officially signing up to be a coordinator, so Doug is basically signed up for all properties. We need people signed up to help. It's not that hard to coordinate. Just mark down when people volunteer, help them out. Recruit people actively, on the properties you're coordinating. It's too much for doug on his own; other people are helping out ad hoc, but aren't following through to make sure the contributor has actually completed the work. Alex signed up for last three weeks in July.

ACTION: julee to e-mail list to try to get others to coordinate. (DONE)

We're still targeted for end of July for first round of P0 CSS properties. Don't want things to fall apart for lack of resources. There are enough volunteers that people can actually get this thing done. ACTION: Eliot to move Seattle Doc Sprint properties to a new table on the WPW page. (DONE)

##### SUBTOPIC: How should we circle back around to folks who have previously showed interest?

Julee started a CRM spreadsheet

If anyone needs access, e-mail Julee. We won't send out public link because it has e-mail addresses on it.

Other things we could do for contributors?

 Lea sent a link to a site that has a contributor spotlight <http://thenounproject.com/>

We talked about doing something like that in the past. We should definitely recognize. As a blog post or on the home page. There are a bunch of people. Contributer "cred"

Having a contributor highlight on the site shows visitors that there is an active community. Be a little careful--some people are rather shy and don't want public exposure

 We don't have profiles right now to configure that. Ryan needs to fix the user profiles. He's actively working on it--it's a MW bug.

 Just to reiterate, when Julee and I emailed the people who had been past contributors, saying, "you were in the top 20/3o people". That pulled several people back in. People really responded well to the fact that we were acknowledging their contribution.

That model is very useful. Even like FitBit sends out little emails to congratulate.

shepazu to prod the discussion about recognizing contributors on the mailing list and look for an extension to mediawiki to do the sidebar

We could have a per-page thing and the overall site notice thing, profiling people who have done a lot of stuff. People like Garbee and Max have done a great job, really gone above and beyond. Either in the TYPE of thing they've done, or the AMOUNT of work they've done There's a number of bots at Wikipedia that detect things like this automatically

 Because we need to explicitly let people opt in at this time, it would be just adding a little section on the home page manually. That would be easier to get going. We do want to execute on the leaderboards thing. It's an automatic way to get people's constructive competition going, if you're \#3, you want to reach \#2 gamification kicks in…

We should talk about all of these analytics in the analytics meeting. i'm going to make a note of these.

##### SUBTOPIC: What MBF for CSS properties?

compatibility tables data types & units done get the code samples switched from MSDN to code.webplatform.org

checklist to make it quick to review some kind of visual, or UI indication of whether or not any given page is ready or not

a template added to the top like [Template:NeedsWork](/w/index.php?title=Template:NeedsWork&action=edit&redlink=1) is helpful for "not ready yet"; visitors and new contributors are not sure what 'flags' means

a high-level gut check as a group before we go forward

high-level CSS WG review, even just flagging issues I think it should be done, maybe even fairly soon they might suggest ways in which we should be changing the pages overall at the docsprint there were a few people from the CSSWG. They had some good review comments. Alan Stearns, Arron Eicholz. Some of them required template changes, like animatable is not a simple boolean unfortunately. Some of them were stylistic

Arron Eicholz has many more suggestions.

ACTION: shepazu to following up with CSS WG review -- especially Arron Eicholz , who was in the IRC for this meeting -- to get more suggestions on CSS properties pages

review from famous devrel people, they have good reach?

people like paul irish or Chris... coyier (sp?)

 ACTION: jkomoros to work with Paul Irish to coordinate getting devrel type folks to review the docs.

 ACTION: Lea to incorporate Chris Coyers UI feedback (<http://lists.w3.org/Archives/Public/public-webplatform/2013May/0241.html>)

a launch plan make sure we're contextualizing what we consider this launch to be

ACTION: jkomoros to help coordinate a launch plan once we decide to go forward with launch.

#### TOPIC: Max's JS file import

<http://dev.maxpolk.org/msdnjs/index.php?title=Special:AllPages&from=Constants&to=Objects%2Farguments> Max has a link to first full upload: <http://dev.maxpolk.org/msdnjs/index.php?title=Special%3AAllPages&from=Objects%2Farguments&to=&namespace=0> <http://lists.w3.org/Archives/Public/public-webplatform/2013Jun/0075.html>

Chrismills and scottrowe, as content architects, give an official response? They may not be available right now.

We should have a calendar or something.

ACTION: julee to create a high-level calendar for people to mark when they're available or not. (DONE: <https://www.google.com/calendar/render?tab=oc&pli=1&gsessionid=P71QgXQ4uw2jGWqFWW6lLA>)

Limited resources on JS, but other things we can do to support this project?

Max is a software developer at ATT mobility. When someone says "we could try one way or another", someone needs to TRY and see if it works.

Need folks to review and try the proposals Max is putting out in email.

Max needs to explicitly state what he needs.

We need a template.

 frozenice, is just too slammed

All template ninjas are too busy.

ACTION: shepazu to mock up types of JS pages with examples, so we can think about templates from there.

We do have tools to edit a page programmatically after the fact, and do mass page renaming, so we should just go forward with it.

ACTION: Max to configure the project page with the tasks. ACTION: Julee to rally an IA overview (DONE)

ACTION: shepazu and maxpolk to meet up in person to work on JS page organization

#### TOPIC: revamping flags!

Eliot provided last set of flags that we had settled on We should go ahead and do it; enough people concurred

#### TOPIC: Demian's Tech Centers - how is it going?

The general overview is that blackberry is paying for some time to use these tech centers in brazil (schools that are paid to do lab time, basically interns). 4 students who have signed on to take on editing/ css properties. Julee and I met with them last week, will meet again on Monday.

we have four people who will spend 20% of their time a week working on WPD, with Blackberry sponsoring. University students. They have ten sites. This is a pilot.

They have a separate table on WPW <http://docs.webplatform.org/wiki/Meta:web_platform_wednesday#BlackBerry_Tech_Centers> Interested in being part of the community as we go through. You might see e-mails, or IRC. Down the road, we hope more of the tech centers will help out. Millo said Microsoft has similar programs, so once this gets going, we can add on some Microsoft sites.

 They're mostly CS students, so maybe can help with infrastructure.

#### TOPIC: Anything new & notable?

(Blogs or other communications planned for next week?) ACTION: Eliot to write up blog post about Seattle Doc Sprint. (DONE)

## ACTION ITEMS

-   julee to e-mail list to try to get others to coordinate. (DONE)
-   Eliot to move Seattle Doc Sprint properties to a new table on the WPW page. (DONE)
-   shepazu to following up with CSS WG review -- especially Arron Eicholz , who was in the IRC for this meeting -- to get more suggestions on CSS properties pages
-   jkomoros to work with Paul Irish to coordinate getting devrel type folks to review the docs.
-   Lea to incorporate Chris Coyers UI feedback (<http://lists.w3.org/Archives/Public/public-webplatform/2013May/0241.html>)
-   jkomoros to help coordinate a launch plan once we decide to go forward with launch.
-   julee to create a high-level calendar for people to mark when they're available or not. (DONE <https://www.google.com/calendar/render?tab=oc&pli=1&gsessionid=P71QgXQ4uw2jGWqFWW6lLA>)
-   shepazu to mock up types of JS pages with examples, so we can think about templates from there.
-   Max to configure the JS project page with the tasks.
-   Julee to rally an IA overview of Max's JS emails (in progress. PhishtucK is doing great.)
-   shepazu and maxpolk to meet up in person to work on JS page organization

## Agenda 2013-06-21: Meeting canceled due to lack of quorum

## Agenda 2013-06-14: Meeting canceled due to lack of quorum

## Agenda 2013-06-07

-   Roll call
-   Demian Borba of Blackberry and his university program.
-   Review of open action items
-   [WPW](/Meta:web_platform_wednesday) - how is it going?
    -   How's video going
    -   should we ask Hiroki Yamada to repost announcements to public-webplatform-jp@w3.org?
-   Ryan Lane upgraded site.
-   [Naming conventions thread](http://lists.w3.org/Archives/Public/public-webplatform/2013Jun/0024.html)
-   Anything blocking you from creating great content?
-   Anything new & notable? (Blogs or other communications planned for next week?)

### DISCUSSION

#### TOPIC: Demian Borba of Blackberry and his university program

Demian Borba has a webkit implementation in our phone

-   … focusing on HTML5
-   … want to make developers successful
-   … started a program called Blackberry Tech Center
-   … Brazil, Argentina, US
-   … find professors, pick 10 tech students to sponsor
-   … could donate 20% of time to Web Platform Docs
-   … in Brazil, we have 5 tech centers
-   …. 1 in Argentina, Mexico, US

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

#### TOPIC: WPW - how is it going?

scott is working on video

snafu this week, we didn't realize that Scott had already done Flexbox….

… so we pulled together an examples week

… gathered together things that hadn't been done

… on Monday, we're going to work with Nic deCosta, and set forward the next several weeks

we meant to put things together earlier, having a set plan in place will give us consistency, we can write blog posts in advance

…also folks can do things in advance and have it done by the designated week.

…NicDaCosta is in EU; announcing at 11am on Wednesday PDT, kills it for EU; asked that we announce it late Tuesday night, early Wednesday morning

..so folks can do it on Wednesday.

#### TOPIC: Japanese email list

julee: should we ask Hiroki Yamada to repost announcements to public-webplatform-jp@w3.org?

#### Topic: Naming Conventions

julee\_: we should be consistent about where landing pages are located

shepazu: let's move forward with our master list of topic locations

julee\_: should Ben Lobaugh do it?

Eliot: I'll do it

shepazu: ben was also trying to link to the talk page for pointer events

#### Topic: Anything blocking you from creating great content?

shepazu: We got an upgrade on MW; some folks have seen some weird quirks - please continue to report anything strange

#### TOPIC: Doc Sprints

MS is having a Doc Sprint 6/22

Brazil Doc Sprint TBD

<http://docs.webplatform.org/wiki/WPD:Community/Community_Events>

### ACTION ITEMS

-   CARRIED FORWARD: shepazu to post on job sites and sysops lists
-   shepazu & julee to do a promo check list, including concrete details on how stewards can propagate (Eliot is working on this)
-   Millo to cc shepazu on his email to new IEEE contact
-   shepazu to ask Hiroki to propagate announcements to the JP list
-   We will blog and tweet WPW late Tuesday night

## Agenda 2013-05-31

-   Roll call
-   Review of open action items
-   [WPW](/Meta:web_platform_wednesday) - how is it going?
    -   Coordinators finding contributors?
    -   Topic clusters done with instrux?
    -   How's video going
-   [Spam](/Special:RecentChanges%26limit%3D300%26days%3D1) fixing?
-   Anything blocking you from creating great content?
-   Anything new & notable? (Blogs or other communications planned for next week?)

### Discussion

#### TOPIC: DevOps

Recruiting is going slowly.

#### TOPIC WPW

coordinators should socialize the list each week

coordinators need more time to reach out to contributors: do topics earlier

problem: many people are not joining the e-mail list

A lot of people already have email overload.

project.webplatform.org was partially to cure that; there people can jump on and join an issue's discussion jswisher said mail list is not part of site: not one experience; psychological barrier to "subscribing to an e-mail list"

<http://www.discourse.org/> contextual chatting

But, we already have a few systems up that don't talk well with one another.

Garbee is working on an actual working Proof of Concept for a new 'wiki' engine. He will share his PoC next week.

 Denis spent some time trying to get Kuma to work. Persona was a block.

 We couldn't figure out how to make a page in Kuma

If Kuma is worth it, could someone help us from the Kuma community?

Imagine this as our editor: <http://jejacks0n.github.io/mercury/>

[09:25:07] \<julee\> jswisher: devs are helpful, but doesn't know about how things would work from the outside.

    scottrowe worked with mindtouch before http://www.mindtouch.com/

 we're not going to move forward on a system without having a dedicated devops person.

ACTION: shepazu: get ahold of Kuma to get an evaluation copy going

 Garbee is trying to rope people in from other communities he frequents. A few have shown interest in helping and at least one has already started (brbcoding).

go on IRC and ask: who's here right who can help

what are the 100 folks on webplatform doing? Lurking.

We also had major noise/spam issues right after launch. So, in us trying to control those issues we may have scared people off.

 IRC people don't like to be told what specifically to discuss. If you are too strict on things, you end up like \#html and people don't like you too much.

#### TOPC: Topic clusters done with instrux?

scottrowe has the Action item to of a proposal to create a new set of topic clusters that are pertinent to the page type

we need clusters that are relevant to the page type: CSS properties, API, HTML

How do we get a specific topic cluster type form field into each page type?

scottrowe: we think we can do this, but in the short term, we'll have to have folks put manual links

#### TOPIC: WPW Video

scottrowe has instrux in the video script

    julee: get a checklist out of script for folks to follow?

ACTION: scottrowe to derive a checklist from the video script for editing CSS properties

 ACTION: scottrowe to send out script to a couple of folks to get feedback before taping.

ACTION: scottrowe will tape next week.

#### TOPIC: spam

600+ spam pages should Admins approve new user creation?

ACTION: Garbee and shepazu to get a captcha system that works.

 [09:58:45] \<Garbee\> I'd set it up with Questy (with custom questions/answers) to start.

<http://www.mediawiki.org/wiki/Extension:QuestyCaptcha> --Something like the first example code.

 We also need to improve abusefilters.

Garbee is working with MicroFormats on sharing stuff once they get their system online.

Jswisher said MDN watches the revisions feed and has a dedicated delete; switching to persona has helped - although it might be a temporary effect; Persona for auth is actually a pretty good helper. It, like oAuth, is harder to fake outright.

### Action Items

-   shepazu to send email to most active users
-   shepazu to reach out to Kuma ops (Aly).
-   shepazu to post on job sites and sysops lists
-   julee to ask direct and actionable question on IRC at 11am

## Agenda 2013-05-24

-   Roll call
-   Review of open action items
-   [ToC](http://docs.webplatform.org/test/css/properties/border-radius)
-   [WPW](/Meta:web_platform_wednesday) - how is it going?
    -   New and improved: only one table to fill out! (Master page is what we're pulling from. But <http://docs.webplatform.org/wiki/Meta:web_platform_wednesday> will become the final master list.)
    -   We have a standing IRC meeting at 11am PDT, Wednesdays, on \#webplatform -- but nothing seems to be happening there.
        -   We should be active on IRC at that time, at least promoting the current week's blog post, and let folks know we're available to answer any questions at that time.
    -   What is workflow for WPWs?
        1.  Shepazu to pick topic.
        2.  Blog written on Tuesday, promo'd Wednesday morning.
        3.  Coordinators get volunteers and sign folks up on the WPW page, adding "In Progress"
        4.  Coordinators help contributors do properties.
        5.  Coordinators should update tables by Tuesday, with "Done" or "Not done".
    -   Anyone going to [CSSConf](http://cssconf.com/)? Any opportunity to promote WPW?
-   [Getting to Beta](/WPD:Project_Status)
    -   The bug genie is returning connection errors. Seems to be associated with writing certain files.
    -   How to mark bugs that are not in beta - postponed?
-   [changing www page to focus on community](https://docs.google.com/spreadsheet/ccc?key=0Ao_fDuA-PPFydE9vbkR4UWpPRHNjaGFxcjA5WXd5SVE#gid=0)
-   Embedding external pages in WPD? (If Lea's not here, move to next week.)
-   Anything blocking you from creating great content?
-   Anything new & notable? (Blogs or other communications planned for next week?)

### DISCUSSION

#### TOPIC: Scott to do a video on how to do a CSS property

It would be cool if people could share tips about doing CSS properties for the video If we tell people to not fill in compat table information, make sure to emphasize the compat NOTES section Let's talk about more examples for video, too.

 We can easily do other ones in the future about how to edit wiki, contribute, etc

#### TOPIC: ToC

mockup: <http://docs.webplatform.org/test/css/properties/border-radius>

Lea pulled ToC out to the side.

Suggestions on how to make it better, but acceptable to deploy for now? Yes.

#### TOPIC: Web Platform Wednesdays

    http://docs.webplatform.org/wiki/Meta:web_platform_wednesday

 now coordinators have only one table to update.

Shepazu is still tweeking it.

Stuff that doesn't get done, gets pushed to next week, or goes back to the hopper to come back in later weeks.

coordinator's job is NOT to do all these tasks. The corodinator is supposed to go out and actively recruit people to work on their items. If they can't get anybody, then sure work on them themselves.

Master list of what hasn't been done: <http://docs.webplatform.org/wiki/Meta:web_platform_wednesday/master_list> or <https://docs.google.com/spreadsheet/ccc?key=0AkRs-89PKiZpdE0xdm9Sb1ZvRW1ZRzMtWEdyU0Z4OEE#gid=14>

Master list of what has been done: <http://docs.webplatform.org/wiki/Meta:web_platform_wednesday>

 ONLY COORDINATORS should fill out that table

 Workflow is:

1.  Shepazu to pick topic.
2.  Blog written on Tuesday, promo'd Wednesday morning.
3.  Coordinators get volunteers and sign folks up on the WPW page, adding "In Progress"
4.  Coordinators help contributors do properties.
5.  Coordinators should update tables by Tuesday, with "Done" or "Not done".

We should get topic clusters determined more in advance? like two or three week out

Leaverou will speak about WPW at <http://cssconf.com/>

#### TOPIC: landing page/home page for site

<https://docs.google.com/spreadsheet/ccc?key=0Ao_fDuA-PPFydE9vbkR4UWpPRHNjaGFxcjA5WXd5SVE#gid=0>

General idea: current goal is to get people active, so show community activity!

Changes should be done incrementally.

#### TOPIC: Beta

Connection errors on project.webplatform.org are preventing triaging of bugs.

In order to easily and quickly view bugs for current milestone within each project's open bugs page, bugs that are not part of the beta should be set to postponed.

#### TOPIC: Embedding external pages in WPD

it would be cool if we could add screencaps from other pages leaverou got this from the cubic-bezier page, somebody added screencaps from my tool cubic-bezier.com. She asked him if he thought it was a good idea to embed the tool (assuming I added media queries to make it look good on small viewports). She's wondering if it's possible and allowed.

### ACTION ITEMS

-   julee to start thread on where new guides exist, where to link them to and what to call them (our Ed, Getting Started, WPW, and Coordinator's guides have confusing names and do not properly reference each other.) (DONE)
-   Scott to do a video on how to edit a CSS properties page.
-   Leaverou to email about embedding a screencaps tool. (CARRIED FORWARD)
-   shepazu to write up guide on what coordinators do on WPW
-   leaverou to work on home page design, with the goal of highlighting community activity (CARRIED FORWARD)
-   shepazu to figure out what connection bug is in project.webplatform.org
-   Julee to write up an email about "postponing" non-beta bugs. (DONE)
-   shepazu to figure out what connection bug is in project.webplatform.org
-   (CARRIED FORWARD) leaverou to send out e-mail asking people to vote on which skin bugs are more important (DONE)
-   (CARRIED FORWARD) shepazu to e-mail ML about latest plans for talk.webplatform.org (CARRIED FORWARD)
-   (CARRIED FORWARD) shepazu & leaverou to mock up what the improved flags will look like. (CARRIED FORWARD)
-   (CARRIED FORWARD) shepazu to ensure forums banner explicitly states it's for accessibility question only. (CARRIED FORWARD)
-   (CARRIED FORWARD) shepazu writes down "How to review a page" and the workflow, so coordinators and contributors know what to do and workflow for whole WPW ideally (CARRIED FORWARD)

## 2013-05-17: Meeting canceled due to lack of quorum

## Agenda 2013-05-10

-   Roll call
-   Review of open action items
-   [WPW](/Meta:web_platform_wednesday) - how is it going?
    -   Coordinators:
        -   Doug:
        -   Chris: did all of his, himself -- next time will get others to help
        -   Julee: did some, got help with border-color and examples
        -   Scott:
        -   Janet:
    -   Process:
        -   Coordinators please:
            -   update [WPDW](/Meta:web_platform_wednesday) main page with assigned items having check marks
            -   update [this week's page](/Meta:web_platform_wednesday/2013-05-08) with status
            -   update [master list](/Meta:web_platform_wednesday/master_list) when things are done
        -   Doug is working on a [coordinator's guide](/Meta:web_platform_wednesday/coordinator_guide)
        -   Do all pages need a different reviewer? At least a "peer" review?
-   [Getting to Beta](/WPD:Project_Status)
    -   Bug count: 141
    -   How to mark bugs that are not in beta - postponed?
-   Onboarding
    -   Need a stock response to people like Konstantinos who reach out to the list and want to join. And maybe a rotating member of the community team to send them?
-   Any updates?
    -   We have ToCs!
-   [changing www page to focus on community](https://docs.google.com/spreadsheet/ccc?key=0Ao_fDuA-PPFydE9vbkR4UWpPRHNjaGFxcjA5WXd5SVE#gid=0)
-   Anything blocking you from creating great content?
-   Anything new & notable? (Blogs or other communications planned for this week?)

## DISCUSSION

### TOPIC: W3C accessibility folks to use our forums

We need to ensure forums banner explicitly states it's for accessibility question only.

There is a cost to everything we maintain. We'd de-emphasize it from the site (well, we already have). The accessibility people have a dedicated, funded person to fund the boards.

### TOPIC: WPD Wednesdays

<http://docs.webplatform.org/wiki/Meta:web_platform_wednesday>

#### WPDW Status

We're in good shape, 25 knocked out this week, someone committed for everything but outlines

jkomoros can't come next week because of I/O, but have it blocked on my calendar going forward

Let's remember to send out inspirational articles when we blog about topics we're focusing on.

Weekly cycle is over on Tuesday.

#### Do all pages need a different reviewer? At least a "peer" review?

Important that the person who reviews the page is not the person who worked on it.

Review shouldn't come across as too much of a blocker. Don't want it to be counter productive

Informal coordinator review, peer review, with official tech review later in 1.0 perfect cycle. We should not declare failure if we don't get review. Set review flag, and reviewers clear it. When flags are removed, that shows the pages are the quality that should be standard

Peer review to make sure the checklist is taken care of. Coordinator can do the checklist review

If the coordinator can't do it, maybe just pair writers together

Technical review for correctness and example is correct

Two different levels of review might make the procedure too long winded. Expert review should come later, if needed.

 The whole point of this exercise is to... get the work done, but mainly to grow contributor base, make it clear how to contribute.

some people have already spoken up and started contributing because this makes it easier. Don't take the work away from other people if you can help develop them. It will take some effort to get people into the habit of contributing and building up the contributor base

#### Coordinators responsibilities

Doug is working on a coordinator's guide

WPDW will be on \#webplatform NOT \#webplatform-site

 All coordinators should:

-   update WPDW main page with assigned items having check marks
-   update this week's page with status
-   update master list when things are done

Coordinators should still do one page. That helps them understand what the pain points are.

Coordinators have 1 or 2 volunteers for each WPDW

When we have a short-hand property that encompasses all of the other properties for individual settings

That's why we chose more properties this week, to keep shorthand/longhand sets together. One person can write the individual longhand properties (which may be in more than one shorthand property), and then do the short hand version.

A lot of pages in mine that said, "just see short hand page". That's annoying to click through. Because we don't have transclusion, we should copy paste.

### TOPIC: Getting to beta

<http://docs.webplatform.org/wiki/WPD:Community/Meetings/General#Project_Status>

The project leads to review the criteria and update the bugs Extended deadline until mid week next week

#### Project Status

[Project Status Page for Getting to Beta](/WPD:Project_Status)

Bug count: 141

|Project|Lead|Open Issues|Beta defined|beta bugs assigned|
|:------|:---|:----------|:-----------|:-----------------|
|Analytics|patrickdsouza|10|Yes|Yes|
|Blog|Eliot-MSFT|4|Yes|Yes|
|commentsextension|shepazu|8|???|???|
|community|jswisher|1|Yes|Yes|
|compatibilitytables|shepazu|1|Yes|Yes|
|content|Julee|40|Yes|in progress|
|dabblet|Lea|2|Yes|Yes|
|InfoArch|Scottrowe|9|Yes|Yes|
|infrastructure|shepazu|14|Yes|???|
|prmg|Garbee|17|Shooting for 5/15|Shooting for 5/15|
|Q&A|shepazu|2|???|???|
|skin|Lea|17|Yes|Yes|
|templates|jkoromo|7|dependency on content & ia beta definition|No|

### TOPIC: Onboarding

Need a stock response to people like Konstantinos who reach out to the list and want to join. And maybe a rotating member of the community team to send them?

Eliot: We're getting a regular stream of new people, asking how they can help. We need a stock mail to send out, and someone on point to respond

people should feel comfortable to customize it.

Tell them that wiki wednesday is a great way to get started

### ACTION ITEMS

-   (CARRIED FORWARD) shepazu to revamp CSS WG e-mail to be call for contributors (DONE)
-   (CARRIED FORWARD) leaverou to send out e-mail asking people to vote on which skin bugs are more important
-   (CARRIED FORWARD) shepazu to e-mail ML about latest plans for talk.webplatform.org (CARRIED FORWARD)
-   (CARRIED FORWARD) shepazu & leaverou to mock up what the improved flags will look like. (CARRIED FORWARD)
-   (CARRIED FORWARD) shepazu to ensure forums banner explicitly states it's for accessibility question only. (CARRIED FORWARD)
-   shepazu to consider putting table at the top of the page (DONE)
-   shepazu send out an email asking for someone to work on outline (DONE)
-   Julee to update editor's guide with links to WPDW (DONE)
-   shepazu to start thread on where new guides exists, where to link them to and what to call them (ACTION transferred to Julee) (DONE)
-   (CARRIED FORWARD) shepazu writes down "How to review a page" and the workflow, so coordinators and contributors know what to do and workflow for whole WPDW ideally (CARRIED FORWARD)
-   Scott to write up quick guide on dealing with shorthand properties (ACTION evolved to: Scott to do a video on how to edit a CSS properties page)

## Agenda 2013-05-03

-   Roll call
-   Review of open action items
-   [Getting to Beta](/WPD:Project_Status)
    -   We assigned project owners. Those owners should review the beta criteria and update it with what their "group" thinks should be in the beta.
    -   Beta criteria needs to be clarified at the higher level as well. For example:
        -   [Scott's take](http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0370.html)
        -   We need more folks vetting the content that's there. The community TF will do a recruiting plan.
        -   We need folks to work on content, especially CSS properties pages. We may ask folks to own certain portions, to be divvied up amongst their friends and family, or otherwise focus on that.
        -   For each content area, we should have exemplar content
        -   Each page should be clearly designated as either ready to consume or needing additional contributions.
    -   What you can do:
        -   If you're a project leader:
            -   discuss beta criteria with stakeholders and update the Project Status page.
            -   make sure you have tasks and bugs relating to beta in project.webplatform.org, and that they're assigned to someone.
            -   if you find blockers, file a bug, and broadcast it to the public list
        -   If you're an individual contributor:
            -   work on some CSS properties
            -   if you find blockers, file a bug, and broadcast it to the public list
-   CSS Properties pages

## DISCUSSION

### TOPIC: Beta

<http://docs.webplatform.org/wiki/WPD:Community/Meetings/General> <http://docs.webplatform.org/wiki/WPD:Project_Status> <http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0370.html>

About Beta: we aren't out of the woods until we get to Beta, at that point, we can be comfortable saying "use this content". That's the critical mass point. Watching all the sub-task forces doing their work, it's great, but imagine that there's a day when stewards or others leave and it starts a mass exodus. Get to critical mass: instead of doing so across the site. Set up a beta based on a content category. The beta can apply to one part of the site. There is a risk that if the project does not achieve a measure of usability, stakeholders may lose interest. The CSS properties project was that set that folks could use as a resource. This calls for focusing on content, to the exclusion of other things.

This should be a fundamental shift in how we do this. Not beta criteria for all of WPD, but define beta criteria for individual content areas, and define beta status on each bucket. Define "beta" as pertaining to discrete content areas. First "beta": CSS Properties.

We need a milestone achievement - CSS Properties. If work doesn't lead to that, defer it. This week, we realized we're spreading our energies too thin. So we should focus our energies on CSS properties project. But, volunteer help is not fungible. For example, Max Polk is willing to work on the MSDN stuff but not interested in other bits. The only thing I would say that needs to be done is:

1) have the compatibility tables from MSDN and caniuse working (because that's a big part of content creation and user experience). If people come to the site and don't see consistent compat tables, it doesn't look good. So our work there is better spent finishing up compat extension.

2) Also, we need to have an exemplar for each page, which is the criteria we had for beta--that's the other thing we we should have for beta.

We all agree on CSS Properties. Other content areas will be deferred.

What about other beta tasks?

Do we want to go back to the project status page and look at those and say if any of those are direct for beta? If we focus on this stuff and don't try to recruit additional contributors, and we say CSS properties are beta, will we have a site that people can consume and contribute to?

Eliot: There are two things there. There's the content effort and the infrastructure effort. (The latter includes compat tables, community, etc.) community growth can still go on, it's separated from what the community is working on. Even MDN is mostly people consuming. Really only about 15 contributors.

Want to reframe a bit: "What is beta" ? what are we trying to accomplish? who is the audience?

1) ourselves. To push ourselves and feel momentum 2) an opportunity to talk to, after the alpha announcement, to engage public and say hey look, another chance to introduce ourselves 3) is the stewards

If we talk about this awesome resource, and we don't have it yet, web developers need to see progress, momentum. if they see value, they'll respond, if devs promote, we're successful. We aren't changing our goals. We need to change focus and messaging for this content only. This was the general plan from the beginning of the CSS properties project?

If we do micro-betas, it may dilute the impact of a general beta. It will be virtually impossible for us to get \_all\_ of the content to beta.

But if we have a set of clear, well-defined criteria for the different sections, that shows evidence of progress. So it's the only path to success.

Then we need to be clear that we're focused on the \_content\_, not the \_site\_. We'll continually revise and refine our processes around recruitment and participation. We've already got a lot more than what we started with. We've made some strides in that area. Some efforts in regard to recruiting may not be timed appropriately to achieve a short-term objective.

When Eliot sent the mail out, he was looking at was our loss of focus on the content front. We're putting together a LARGE project with many different facets. At Microsoft, we have a team of writers, and a production team, and a marketing team and we don't take marketing people off that when we need to do a content push.

We shouldn't do it here. We should identify who's working on what, and what they're doing. The note was really just about loss of focus on Content front. We'll continue to look at bugs and project status page focus on other areas, but as far as content effort goes, we focus on CSS properties. Other aspects are secondary but still important.

Folks will review their bugs:

Infrastrucutre is Doug. Content is Scott, Chris, and Julee. Community is Janet for beta criteria.

Right now, the site notice has a new call to action on JS.

### TOPIC: CSS Properties work

The CSS properties sheet is overwhelming folks. [Julee updated it](https://docs.google.com/spreadsheet/ccc?key=0AkRs-89PKiZpdE0xdm9Sb1ZvRW1ZRzMtWEdyU0Z4OEE#gid=17).

We need to ensure that new contributors are properly supported. [Plan to help contributors](/WPD:CSS_property_guide/supporting_new_contributors#Helping_contributors_with_CSS_properties_page)

Everyone on this call who's not up for this, e-mail me specifically, otherwise you're on the hook for being an ambassador or greeter. Weekly content-wrangling events on IRC is being scheduled for the West coast first, as Scott and Julee have already volunteered as consistant facilitators. Please fill out [doodle poll](http://www.doodle.com/y4bdnrg4ycdk4i25)

### TOPIC: Forums

w3c accessibility folks want to use our forums. So, let's keep them open, we've already deemphasized them on the site and communications channels. But let's keep them open so accessibility folks can use it.

## ACTION ITEMS

-   Shepazu to mock up how project should be represented in the wiki (DONE)
-   shepazu: update the site notice about the CSS Properties push and how to get started AND use the piwik tracking campaign code. (DONE)
-   shepazu to draft up CSS properties project blog post (circulate for comment) AND use the piwik tracking campaign code. (DONE)
-   shepazu to revamp CSS WG e-mail to be call for contributors
-   leads to review the bugs for project areas on project.webplatform.org (jswisher, shepazu, cmills, julee, scottrowe) (In progress: See: [Project Status table](/WPD:Community/Meetings/General#Project_Status))
-   shepazu to send out e-mail asking people to vote on which skin bugs are more important
-   shepazu will send an email about change in forums with w3c accessibility folks using it to answer questions
-   (CARRIED FORWARD) shepazu to e-mail ML about latest plans for talk.webplatform.org
-   (CARRIED FORWARD) leaverou: to talk with Chris Coyier regarding reviewing css properties template.
-   (CARRIED FORWARD) leaverou: will follow up with Denis where global nav didn't get implemented.
-   (CARRIED FORWARD) shepazu to work with lea to mock up what the improved flags will look like.

## Agenda 2013-04-26

-   Roll call
-   Review of open action items.
-   Appearance of content flags.

<dl>
<dd>
Limited, but pointed feedback (from doc sprinters, others) suggests that these may be a deterrent to editing content. Consider toning them down?

</dd>
</dl>
-   [DOM API Doc Reorganization Proposal](/WPD:Projects/DOM_API_docs).
-   Task forces reporting back to this general meeting.
-   Anything blocking you from creating great content?
-   Any new or notable content to promote?

## DISCUSSION

### TOPIC: Appearance of content flags

Limited, but pointed feedback (from doc sprinters, others) suggests red flags may be a deterrent to editing content. Consider toning them down?

... it's a bit "boy who cried wolf"

Should the meaning of flags be explained more explicitly when being set and viewed?

Some of them should be stronger than others

being able to change the priorities/visibility, and actions that are obvious from them

ideally, stub should be more inviting, for example

Back at the beginning, the plan was to display them differently to signed in vs signed out people

Also, flag banner is broken: <http://docs.webplatform.org/wiki/html/elements/!DOCTYPE>

[agreement that this is something to fix]

 For beta, clear visual representation that this page is considered Beta-ready or not, we won't be able to touch all of the pages for beta

That's especially important given that some parts of site will be ready to be called beta before others

Could just have a banner that says "flags associated" or "this article is not beta ready", and when you go down to the \_bottom\_ it shows the flags

If you look at the compat table's output, when you mouse over it shows one thing for all mobiles; then when you mouse over it shows details

Also, I think a simple tooltip for explanation of flags (on hover) would be sufficient, maybe have popup appear on mobile devices but something like that that says "there are flags on this page" and when you hover over see the specific ones

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

### Topic: DOM API reorganization proposal

<http://docs.webplatform.org/wiki/WPD:Projects/DOM_API_docs>

Adopted with the following discussion:

Want to make sure it's predictable and avoids conflicts Follow basic object hierachy but flatten it out

Shepazu provided one example of proper DOM hierarchy:

<http://objjob.phrogz.net/>

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

### Topic: Task force statuses

#### Community Development

we firmed up out plans for upcoming doc sprints

 Any updates to any of the events should be reflected on the [events page](/WPD:Community/Community_Events).

shepazu's great idea : have a non-political description of DRM and DNT, have technical articles about those and make a blog post.

... the TECHNICAL aspect, not political, social, or standardization aspect

and the ancillary idea was: we have an alpha banner, but we don't have anything about the campaigns we're working on (like CSS properties)

... when we have a push, we should highlight them in the banner

Redesiging the notice so it's not quite so ugly and what our current call to action

So, we have the blog, but do we also need a News or Current Events page linked to from the home page?

More controversial topics might get more vandalism, we'll need to be vigilant.

And we'll want to make it clear we're trying to just be about TECHNICAL aspects.

Have a disclaimer, if you want to discuss social aspects, here are some links for you to go to to do that

 the blog entry where we say "we realize these are controversial, this is the role we're trying to play"

### TOPIC: Status of CSS properties project

We're stalled on contributors to content. Not too much to review compared to content we need to create

We might need to broaden our base to get more contributors

### TOPIC: compatibility tables

<http://docs.webplatform.org/wiki/WPD:Compatibility_Info>

 There's a disconnect between pages that we have and granularity of caniuse data

If we're going to replace our existing compat tables, we'll need to do so comprehensively.

MOzilla agreed that we can crawl MDN's compat information, as this is public domain content. They agreed that we can use this data, and are not required to mark it as their \_license\_, although of course we'll say we got the info from them.

Shepazu is working on a script to extract data from them, merge with caniuse

If there's a test missing, then we'll provide a simple interface for folks to provide one, or at least some input.

if you see something missing, if you want to give the test to help with that it will take them to a thing to let them contribute a test

That's huge overhead, will discourage contributions.

But how will we know it's good if they just make an assertion?

 We can have a way to put in unverified information, but it should be tagged that it needs tests

## ACTION ITEMS

-   julee to email project leads inviting them to Monday's meeting. (DONE)
-   pending Alex's amazing, insightful review of the DOM API proposal, Scott to begin implementing (DONE)
-   Julee to file a bug to get a visual representation of the DOM hierarchy (DONE: <http://project.webplatform.org/content/issues/46>)
-   Julee to add CSS properties recruting to communications meeting (DONE)
-   shepazu to propose concrete proposal on compat info to list once it's done (ON-GOING)
-   shepazu to e-mail ML about latest plans for talk.webplatform.org (CARRY FORWARD)
-   leaverou: to talk with Chris Coyier regarding reviewing css properties template. (CARRY FORWARD)
-   leaverou: will follow up with Denis where global nav didn't get implemented. (CARRY FORWARD)
-   shepazu to work with lea to mock up what the improved flags will look like (CARRY FORWARD)

## Agenda 2013-04-19

-   Roll call
-   Review of open action items
-   Task forces reporting back to this general meeting:
    -   Community
    -   Analytics
    -   Program Management
-   Anyone want to share any status on any project? Can we get completion dates?
-   Review proposed URL/structure of [DOM API docs](/WPD:Projects/DOM_API_docs).
-   Has anyone seen the Evil Session Bug lately?
-   When you tweet, don't forget to check conversation for follow-up!
-   Anything blocking you from creating great content?
-   Any new or notable content to promote?

## DISCUSSION

### TOPIC: CSS Properties reviewers

Doug and Chris Mills commented. Maybe have design experts join in, but unclear if they were to be SME to review content or the design of the pages. we did a couple of rounds on the template.

We did another round in January, so I don't think we need to review the design further. Does anyone else?

Lea's been good about finding optimizations and fixing problems.

Joanie Rustalkin who helped design said we could contact her. She'd be an obvious choice. But let's not revisit design of the template.

The idea was to get feedback on the content. But Lea can review design and discuss with other designers, such as Chris Coyier.

### TOPIC: Compatibility tables

May be able to pull in data for mobile, too. <http://mobilehtml5.org/> <http://firt.mobi/about.php>

Any others?

<http://html5test.com/results/desktop.html> Their methodology did not--ironically-seem test-based. Shepazu to contact them anyway.

### TOPIC: TF updates:

#### Community

had a meeting last week

university outreach: established a spreadsheet. Will list contact there, but we won't make that public.

We will invite people to contribute to that list. [ We're considering doc sprints. Still working on that.

Established a regular meeting time. Tuesdays at 10am Pacific time.

If we have an agenda, we'll use the time. Otherwise cancel instance.

#### Analytics

Topic clusters.

Setting up a human readable site map. We'll track campaign and emails.

    Before any doc sprint, need to set up a campaign.

Our SEO: Setting it up. Next step is to optimize the content. We have this tracked in Bug Genie.

#### Program Management

Meetings 11am Pacific time on Mondays.

Triaging bugs and gathering information about the state of the beta work.

This week we asked people to take ownership of the different project buckets. Owners will define the deliverables and build a time, triaging issues, reporting back to the PM group on progress towards beta.

We also talked about BugGenie and how to get reporting done ACROSS projects.

Hopefully, we can get away from meetings and get a dashboard look at status.

### TOPIC: URL structure DOM, JS, and topic clusters

URL/structure of DOM API docs.

<http://docs.webplatform.org/wiki/WPD:Projects/DOM_API_docs>

follows the same scheme as API docs, but without the API listing pages that describe the common names. Since the common name for all of these is DOM.

Doesn't affect how we're going to deal with the JS docs from Microsoft.

scottrowe: If folks would review that, it'd be great. I added some more info.

You coulld make a case that everything's in the DOM, but that wouldn't help people delineate anything from DOM down.

We've done that in our top level buckets , and now we're isolating a subgroup of the DOM and calling that the DOM APIs.

.They're the interfaces and objects you use when interfacing with the object model. I can make it clearer in the proposal, but I thought that was an established methodology.

this came up earlier, and I hashed it out with some architects. We couldn't come up with a sensible way of doing an alternate view. Scott's proposal is widely accepted.

We still need to have some kind of instruction--even visual representation--of the DOm, interfaces, JS, etc. That might be an article, so then we could explain why we put things places.

We haven't talked a lot about interlinking between articles and we should look at that a lot.

We should cross-reference related things. MediaWiki doesn't make it as easy as a dedicated documentation CMS, but.

We'd talked about topic clusters as doing this.

There's an issue filed. Let's use that to discuss this.

There may be a passive-aggressive way to make them enter links: topic cluster UI based on links within doc, so if you don't have links, your topic cluster doesn't look right.

<http://project.webplatform.org/content/issues/42>

### TOPIC: Session Bug

MIA Close it!

### TOPIC: Watch channel after tweeting

When you tweet, don't forget to check conversation for follow-up!

### TOPIC: blogging about new SVG articles

julee: I think Mike Sierra has moved to something else at Adobe. Finished out a bunch of SVG work. HTML5 weekly mentioned the articles.

### TOPIC: table styles

In some pages, there are tables without a class to target. If I style all tables inside the container, it'll have unforseen effects. Regarding the font, I am fine changing it. PErsonally, I think bitter looks better. Is there an automated way to add a class to tables that don't have one?

A lot of tables were generated by authors and some use the pipe hack, so there are some issues with tables we generated.

## ACTION ITEMS

• leaverou: to talk with Chris Coyier regarding reviewing css properties template. (STATUS: Lea is at a conference right now, and will be mentioning WPD explicitly) • leaverou: will follow up with Denis where global nav didn't get implemented. (STATUS: carried forward) • shepazu: change the messaging on talk.webplatform.org. (STATUS: not sure that changing messaging is the right thing at this point. Shepazu to send an e-mail to ML) • Patrick: to give us optimal day and time to launch a blog post. (DONE) • Analytics TF: set up page optimization in the next two weeks. (likely won't happen right now, it's ongoing) • Project area leads: join next week's call so we can define what it means to be head of a task force. (STATUS: Meeting didn't happen, due to zakim snafu. Please join us next week.)

## Agenda 2013-04-12

-   Roll call
-   Review of open action items
-   April 3 Doc Sprint
    -   How was it?
-   A lot of meetings next week
    -   Community
    -   Analytics
    -   Programming
-   Closing out some items
    -   [Forum dependencies](http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0121.html) - completion date?
    -   [Translation URL schema](http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0090.html) (<http://docs.webplatform.org/wiki/lang/es/Main_Page>) - decision final?
    -   [Session bug](http://project.webplatform.org/infrastructure/issues/1) is gone again! Is this issue closed?
-   Anyone want to share any status on any project? Can we get completion dates?
    -   CSS Properties project
        -   Discuss sending out a "call for review"
    -   Project.\* project
    -   Global nav project
    -   [Beginners guide](http://project.webplatform.org/content/issues/41) to web dev - Status from Chris: created all of the [landing pages](/w/index.php?title=TEST:beginners&action=edit&redlink=1) and writing updated text for the landing page
    -   Populating news email list with [university contacts](/WPD:Projects/Communications/Universities)
        -   Fellowships, interships, mentoring programs for students
        -   Please gather university contacts to add to an announce email list
-   Anything blocking you from creating great content?
-   Any new or notable content to promote?

### Discussion

#### TOPIC: April 3 Doc Sprint

It was great. Scott did a blog post about it.

#### TOPIC: A lot of meetings next week

We should confirm that these meetings are productive: resulting in getting work done. If not, we should review.

#### TOPIC: Forums dependencies

#### TOPIC: \*

We want to [close down forums](http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0121.html), but we need to get some things done first. See dependencies:

<http://project.webplatform.org/content/issues/40>

#### TOPIC: Translation URL schema

We came close to a decision on the URL schema for other languages:

<http://docs.webplatform.org/wiki/lang/es/Main_Page>

But shepazu said we rejected this many times before.

What we have now is almost the worst of both worlds. Bad design by W3C LOC experts, MW's auto URL schema isn't good, what we're doing now is bad for SEO.

Shepazu will follow up with Richard Ishida, W3C's internationalization and localization expert

#### TOPIC: Session bug is gone again!

People haven't seen it, but let's give it a little more time to test. It was a token bug. There's a token that ID's the session, depending on the memcache. It wasn't able to find the session and the session was lost. Ryan removed single-signon, and changed the memcache server.

#### TOPIC: CSS Properties project

Discuss sending out a "call for review". See [ <http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0148.html> thread].

But what's the process? Is Julee the right person to send reviewers to? What does she then do? How do we handle comments, store them, deal with them after we get the review? Seems like we don't have any system. Do we have the list of pages to review?

We're talking about SME, we can just ask them to just to edit the page. We won't track what changes they're making. But, what if the change should be made across more pages? So our pages are consistent in org or style?

Also, do we have a golden standard? If folks want to talk about specific styles, it's in one location: the golden standard. Is there a WPD voice? We added the golden standard to the top of the [<https://docs.google.com/spreadsheet/ccc?key=0AkRs-> 89PKiZpdE0xdm9Sb1ZvRW1ZRzMtWEdyU0Z4OEE spreadsheet].

Julee will work with SME to decide what pages they're going to review. If it's something global, they need to call that out and we need to fix it across the docs.

SMEs are looking for whether he doc is technically accurate. What we're asking them to determine if the article is "technically accurate?" We're not asking them to set the style of content.

So we do need to hand pick some pages to get SME feedback, but once they say a doc is good, that's good enough.

We're going to get different voices in a Wiki. But, maybe less so in reference docs. But the priorities are:

• quality content • then i18l English • Then down the line comes the issue of voice. So, the ref should be in active voice and some other things, but we shouldn't impose too much at the beginning. Not before we see how things evolve.

Let's have as little process as possible. This is our first major writing project, let's put the least process in the beginning and put checkpoints in place later.

We should make it clear that SMEs need to let us know if there's something global.

And the letter needs to say if they see something that should be fixed across pages, or if they see any problems, contact julee. Want to make it easy for the SMEs to give feedback but doesn't need an official process to make that happen.

shepazu: is concerned that we would make a call for review and problems that would cause them not to come back later. this is a push to a larger community than we've had, so we want them to feel satisfied.

Julee will send out an email clarifying process.

#### TOPIC: Project.\* project

Garbee writing instrux. Having a state view of the beta is a dependency on reporting progress. This can be accomplished with a master project bucket.

shepazu: julee & shepazu will follow up

#### TOPIC: Global nav project

The [global nav](http://project.webplatform.org/content/issues/14) has not been implemented consistently. Forums closing has a dependencies on this project.

Lea's out this week. She's going to point to WPD in her preso!

#### TOPIC: Beginners guide to web dev

Chris Mills created all of the landing pages and writing updated text for the landing page.

<http://docs.webplatform.org/wiki/TEST:beginners>

<http://project.webplatform.org/content/issues/41>

Note we have commenting on the issue page! Try to move discussion about implementation to project.\* page.

#### TOPIC: Populating news email list with university

This is probably a comm & recruiting item. In the meantime, we're asking everyone to please gather university contacts to add to an announce email list.

ALSO: Fellowships, interships, mentoring programs for students: GSoC: we got rejected (explicitly not for documentation). But w3c did get approved. Shepazu will follow up.

Media Wiki has a mentoring program, can we add our project to their list? Julee will follow up. (DONE)

#### TOPIC: status of table styles

Lea will incorporate scott's feedback.

#### TOPIC: W3C WG

W3C WG is the week after next, may interfere with this meeting. Eliot and Shepazu will talk about presenting there.

#### TOPIC: Compatibility tables project

Shepazu has been working on extension with caniuse data; alexsis d. & ppk: quirks mode data is all HTML.

PPK will package this data. Shepazu is merging these data sets. We may use MDN data as a fallback for the gaps in the caniuse and quirksmode datasets.

Need to optimize with edge side includes (tell fastly to cache it as a special case) Fastly said we can do this.

Need to work out a process for manual customization? (Maybe just the open text field?)

Shooting for end of April to deploy on all ref pages.

#### TOPIC: WPD AS PLUGIN

Tom Ortega wants to participate by investigate building plugins for standard editors: to have WPD be a plugin for these IDE. Julee referred him to frozenice as an initial contact.

### ACTION ITEMS

-   shepazu will call in Richard Ishida, W3C's internationalization and localization expert (DONE)
-   Julee to write a draft email outlining the process to use for CSS properties review as instructions for SMEs. (DONE <http://project.webplatform.org/content/issues/43>)
-   shepazu to follow up with Lea regarding global nav (<http://project.webplatform.org/content/issues/14>) (DONE)
-   Julee to talk to ryan about this (DONE: Only GNOME project might apply. Pursuing as part of community & recruiting agenda.)
-   shepazu to send out timeline for W3C GSoC (STATUS: We discussed during analytics that it probably wasn't the right)
-   Eliot & shepazu to talk re: presenting at W3C WGs. (DONE: saw no follow up from julee or scottrowe. check your inboxes.)
-   shepazu to work with PPK/Verio/Alexis Deveria on public-webplatform-tests@w3.org (ON-GOING: shepazu: will report back if there's anything to report.)

## Agenda 2013-03-29

-   Roll call
-   Review of open action items
-   Status on project.\*?
-   Program management meetings will be set up to:
    -   Derive a final list of deliverables.
    -   Get a schedule.
    -   Work out how the dev/qa/launch/communication cycle will go.
    -   Triage bugs.
-   Please respond to [email](http://lists.w3.org/Archives/Public/public-webplatform/2013Mar/0315.html) re: IRC hours and
-   Anyone want to share any status on any project?
    -   Lea updated www.\* with new global nav, can we get docs.\* updated?
    -   CSS Properties project
        -   Sending out [emails](http://lists.w3.org/Archives/Public/public-webplatform/2013Mar/0308.html) to Doc Sprint registrants to ask them to re-try getting started. Anticipating some will participate.
        -   Any one else want to take on a few?
-   Anything blocking you from creating great content?
-   Any new or notable content to promote?
-   Julee taking a personal day next Friday. Someone willing to run this meeting?

### DISCUSSIONS

#### TOPIC: hiring a scribe

shepazu proposes hiring a scribe shepazu will report back with more information

#### TOPIC: CSS properties project

ACTION (CARRIED OVER): shepazu to recruit volunteer reviewers from the public list for CSS WG [STATUS: Prepared email. Do we have a systematic way of processing feedback? See 2013-04-12 meeting notes, above, for discussion.]

ACTION: Julee to assign owners for properties after Doc Sprint. (DONE)

shepazu started work on recruiting reviewers, wrote e-mail; consulted with Fantasai

ACTION: shepazu to send out e-mail with process/plan for tech reviewers

We would like to get spec authors more involved with the documentation, with the caveat that spec authors are not the ultimate responsible party, nor should beta criteria be dependent on spec author approval

#### TOPIC: DOM API pages

ACTION: Content Task Force Lead [scottrowe\_] should set up a meeting to talk about overall site organization and how we want to handle DOM API pages.

scottrowe\_ volunteers to be CTL for DOM API pages, julee also volunteers

#### TOPIC: Edit Dismissible Alpha

Scott's an admin, but can't change the alpha note on the main page.

ACTION: scottrowe\_ to follow up with Alex about editing the dismissible message.

#### TOPIC: Status on project.\*

ACTION: shepazu and julee to coordinate with garbee on project buckets, testing (DONE)

#### TOPIC: Google Summer of Code

<http://docs.webplatform.org/wiki/WPD:GSoC>

browser compat API in the works; maybe POC next week

anyone can contribute to the GSoC proposal

Shepazu - will you also be working on <http://mobilehtml5.org/> to be implemented through the compat API?

Millo, we're open to any data source that meets our criteria

#### TOPIC: Please respond to email re: IRC hours

ACTION: If folks don't respond to email, Julee to set up an IRC calendar page (DONE)

#### TOPIC: API Project almost done!

Scott will send out email when it's done.

#### TOPIC: Custom error pages!

Lea did the error pages!

<http://www.webplatform.org/errors/404.html>

<http://www.webplatform.org/errors/images/numbers.html>

#### TOPIC: Bug Genie skinning

<http://project.webplatform.org/skin/issues/3>

<http://project.webplatform.org/prmg/issues/PRMG-10>

### ACTION ITEMS

-   (CARRIED OVER): shepazu to recruit volunteer reviewers from the public list for CSS WG (STATUS: Prepared email. Do we have a systematic way of processing feedback? See 2013-04-15 meeting notes, above, for discussion.)
-   Julee to assign owners for properties after Doc Sprint. (DONE)
-   scottrowe\_ to ping jkomoros about how to fix the dismissible alpha message (DONE)
-   (CARRIED OVER): shepazu to send localization guide to public list (STATUS: Chris Mills now has this action item. Doug will bring in Richard Ishida, W3C's internationalization and localization expert)
-   Lea to implement content/issues/14 on docs.\* as well (STATUS: Lea's away this week)
-   Julee set up CSS Properties project page with custom queries (Scott did this.)
-   Analytics team to develop report of key analytics, leading indicators, share at general meeting regularly (STATUS: We got the sitemap! Otherwise, carry forward)
-   shepazu to take point on next week's meeting, if there is a quorum (Meeting didn't have a quorum)
-   Content Task Force Lead [scottrowe\_] should set up a meeting to talk about overall site organization and how we want to handle DOM API pages.
-   shepazu and julee to coordinate with garbee on project buckets, testing (IN PROGRESS: also programming meeting is next Wednesday)
-   If folks don't respond to email, Julee to set up an IRC calendar page [IRC hangout hours on IRC page](/WPD:Editors_Guide/step_2_communicate_with_the_online_community#IRC_hours) (DONE)

## Agenda 2013-03-22

-   Roll call
-   Review of open action items
-   Review [WPD:Project\_Status](/WPD:Project_Status) and related [WPD:Proposals/Organizing\_projects](/WPD:Proposals/Organizing_projects)
-   April 3 Doc Sprint
-   Dealing with "issues". For each project, do we have:
    -   A lead and team members assigned? If not, do we have volunteers?
    -   Open issues assigned? If not, can we get a deadline for triaging all issues?
-   404 page, and other errors. - Lea volunteered to address these.
-   Anyone want to share any status on any project?
    -   CSS Properties project
        -   Going to CSSConf in FL in May? Do we want to plan on promoting this new content then?
-   Anything blocking you from creating great content?
-   Any new or notable content to promote?

### DISCUSSIONS

#### TOPIC: CSS properties

We will have a CSS property guide (<http://docs.webplatform.org/wiki/WPD:Proposals/CSS_Property_Milestone>) for the upcoming doc sprint.

The last docsprint was successful with that. There are about 160 left, and only one docsprint coming up. So we need contributors and reviewers.

#### TOPIC: proposal vs. projects space

Scott wants only 1 area. Does not see a difference between the two.

#### TOPIC: search

Denis needs to confirm, but we might install a new extension based on Google search (temporarily)

#### TOPIC: session bug

[Issue \#1](http://project.webplatform.org/infrastructure/issues/1) was reopened [Issue \#3, update error message](http://project.webplatform.org/infrastructure/issues/3) was closed [Issue \#2, page not refreshing](http://project.webplatform.org/infrastructure/issues/2) is not to be confused with [Issue \#1](http://project.webplatform.org/infrastructure/issues/1)

 Ryan Lane has identified this issue as an edit token issue. Excerpt from IRC of community mtg:

Ryan\_Lane: the memcache configuration we're using now is the new style available in mediawiki since 1.18. It's what's used in production at wikimedia, and it uses the pecl memcache client, rather than mediawiki's home brewed in-php support.

Ryan\_Lane: Are we still using the SSO plugin? And if so, do we still need it? It screws around with what's in memcache

patrickdsouza: if someone could look into the logs and check julee's logins you could try reproducing the bug.

julee: If user edits the page for a long time it is more likely to happen.

Ryan\_Lane: Are we still using the SSO plugin? And if so, do we still need it? It screws around with what's in memcache.

Ryan\_Lane: Are people actually logged out, or does it just say "a loss of session data" when trying to save an edit?

julee: I just got this error: "Oops! We seem to have a conflict. Please try saving again. If it still does not work after 2 or 3 attempts, try logging out and logging back in." I knew I was going to get that error because I had my page open in edit mode for so long

Ryan\_Lane: that's not actually a session issue. That's an edit token issue. I'd need to see where the edit token is stored. I'd imagine memcache, but maybe not. I'm positive this could be fixed by ensuring logged in users always hit the same application server once they are logged in, but that's really just avoiding the real problem

#### TOPIC: 4/3 Doc Sprint

Peter already has secured facilities and catering. It's at Google's offices in SFL:

-   very much like previous doc sprints
-   the big ticket item this time is CSS properties project, but other people should suggest other projects
-   Scott to run new people through a getting started observe whether the getting started pages/workflow is working for people. 4 or 5 people .
-   So many Doc Sprints in the Bay Area. We might really want to try to incorporate remote participation again.
-   It starts at 9, but you can come early. I'll be there by 8, 8:30.
-   We'll have schwag, a bunch of t-shirts

#### TOPIC: Dom API

A quick huddle to talk about overall site organization and how we want to handle DOM API pages. There are multiple ways to look at DOM. We want to entertain different viewpoints into the model, based on the way people experience it. We're not locked into a single hierarchy because this isn't a book. Only one URL structure, but maybe multiple views?

We may begin talk at Doc Sprint or Content project area lead will set a meeting to discuss.

#### TOPIC: Dealing with "issues"

A bunch of issues are sitting around. Let's get project owners and encourage triage and status on bugs, at the project level. Then these projects roll up in some way in summary.

Minimally, we should get all issues in bug genie assigned (something that bugzilla requires).

#### TOPIC: 404 page

Lea agreed to look into the UX for 404 pages. She will design and will request fine tuning of content. <http://docs.webplatform.org/wiki/WPD:Projects/ErrorPages>

#### TOPIC: Code styles

shepazu hid code markup styling because it were ugly, but leaverou restyled and brought back. She added Prism.js. Before, the code examples had an indication of what language they were in, but the markup wasn't in the format prism expected. So, leaverou wrote some code to transform to the right format, so we now have nicely highlighted ones! It only works on samples with a language set.

#### TOPIC: Global navs

leaverou implemented the bottom global content navs! She is also willing to take up [Issue \#14](http://project.webplatform.org/content/issues/14):

### ACTION ITEMS

ACTION (CARRIED OVER): EVERYONE:

-   if you haven't been editing pages, can you volunteer to do a CSS property? that will get you used to editing the wiki and experiencing what our users are experiencing?
-   also try to recruit one or two people to do some property pages.
-   and if you could help me with the review process. If there are certain pages that should be reviewed by an expert, call them out to me.
-   and if you have ideas of experts who would be good reviewers, let me know--we need a significant number of them before we can claim that the docs are good
-   Use the new "needs review" tag to tag articles that need review

ACTION (CARRIED OVER): shepazu to recruit volunteer reviewers from the public list for CSS WG

ACTION (CARRIED OVER): shepazu to send localization guide to public list

ACTION (CARRIED OVER): Julee to call it out to the l18n folks to make sure it makes sense & add it to the Ed-Guide. (Shepazu wants Richard I to be involved.)

ACTION: scottrowe, update the Proposals section to be Projects [DONE]

ACTION: Julee to send out Beta Plan decision to public list [DONE]

ACTION: Lea to implement content/issues/14

ACTION: Julee to update issue with URL that new links should point to. [DONE]

ACTION: Content Task Force Lead [TBD] should set up a meeting to talk about overall site organization and how we want to handle DOM API pages.

ACTION: Julee to send out e-mail asking for a lead, at least temporarily, for each project area, so we can get bug triaged and some movement. [DONE]

## Agenda 2013-03-15

-   Roll call
-   Review of open action items
-   [CSS Properties project](http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone)
    -   Volunteer to get pages written.
    -   Send Julee your recommendation for props that really should be reviewed & suggested experts.
    -   Pointer to APIs.
-   Topic vs. Topic Clusters?
-   Filling out the taxonomy of the site
    -   Generate a site map of the current site
    -   Identify what pages should be there that aren't
    -   Stub in those pages with details on priority, etc.
-   URLs for translation
    -   What can we tell translators now?
        -   Why can't we do ..wiki/lang/.. now?
    -   Should we have a task force?
-   Fix Search
    -   Duplicate pages in results
    -   Crawl/index WPD: pages for help
-   Session bug?
-   Dabblet?
-   Community development task force
    -   Press kit?
        -   Brief recap of [Verbatims](/WPD:Community/Survey/Verbatims) and [Survey](/WPD:Community/Survey/Doc_Sprint/Berlin_2-2013).
        -   Plan next Doc Sprint: April 3, 2013 in San Francisco at the Google office.
-   Analytics task force
    -   Getting together in the next week
-   Content-complete questions:
    -   How can we get a seal of approval from the community? Can SME review content?
    -   What is the criteria for calling something complete?
    -   What is the announcement plan to promote completed content?
-   Anything blocking you from creating great content?
-   Any new or notable content to promote?

### Discussion

#### TOPIC: CSS Properties

ACTION: \* everyone:

-   -   if you haven't been editing pages, can you volunteer to do a CSS property? that will get you used to editing the wiki and experiencing what our users are experiencing?
    -   also try to recruit one or two people to do some property pages.
    -   and if you could help me with the review process. If there are certain pages that should be reviewed by an expert, call them out to me.
    -   and if you have ideas of experts who would be good reviewers, let me know--we need a significant number of them before we can claim that the docs are good
    -   Use the new "needs review" tag to tag articles that need review

ACTION: shepazu to reach out to public CSS WG list and ask for experts to review CSS pages

For the beginning, the webkit team will likely just need a stable URL scheme and that's it, so they can generate lists

Eliot said that, unfortunately, someone who was going to join the project won't be able to join due to personal reasons. looking for someone to take his place, but no great options at the moment

#### TOPIC: Topic vs Topic Clusters

scottrowe\_ did docs on that. more usable and better-accessed during the getting started flow and editor's guide

#### TOPIC: Taxonomy of the site

We still want to generate a sitemap. Doug and I spoke about this over e-mail to the list. Doug is going to get Julee access so she can experiment with generating a sitemap.

ACTION: Denis to follow up with Julee about sitemap generation [DONE]

scottrowe\_ has been looking into the DOM project in relation to the Shadow DOM documentation. He's trying to figure out how we should design our DOM API pages generally. He will propose the DOM project as next quarter's project, just like CSS was this quarter's project.

Let's focus on CSS properties first.

DOM organization & refactoring is a pre-beta criteria. Even if we could just settle how we're going to organize it, then we could have a solid beta presentation.

Coming up with a set of beta guidelines soon. It will include the DOM is part of the architecture of the site is a pre-beta criteria

Segment the site (E.g. css properties) getting to "beta" individually as their quality gets to the right level.

But make it clear what's beta and what isn't. Add visual cues to each section so the solid stuff looks solid, and placeholders look partly there.

And map out what ALL of the pages are and creating stubs. And that goes along with the sitemap that Julee's working on. And helps us not have to explain the new page flow to new contributors – they'll be pre-populated.

This conference is full, no more parties can be added.

ACTION: Shepazu to allocate more spaces in future calls

#### TOPIC: URLs for translation

Some concern over current URL naming schema. We have a page that writes up how to do this. It's not a great process, but it is possible.

We should do one or more BoF sessions at the html5devcon, to generate buzz, invite folks to grapple with how to handle i18n, catch folks who can't make the sprint, help pack the sprint, etc.

We should address this now if we have volunteers who want to help out.

ACTION: Shepazu to get richard ishia [sp?] comment on what a better solution will be. He's the W3C l18n expert

The localization guide isn;'t in the editor's guide.

ACTION: shepazu to send localization guide to public lis ACTION: Julee to call it out to the l18n folks to make sure it makes sense (shepazu wanted to get Richard I involved...)

We will table the long-term solution for now

#### TOPIC: Search

Why we can't fix this part with duplicate results? the default search is bad for mediawiki. We thought we replaced it with Lucene. With the advanced search you can already include WPD pages

ACTION: Denis and shepazu to talk about improving built-in search. (Did we replace default search with Lucene?) (Lea to shepazu: this might help: <http://www.mediawiki.org/wiki/Extension:SphinxSearch>)

#### TOPIC: Session bug status

Feedback from users: it's still happening.

Denis talked to fastly guys two weeks ago. He said to change something in the config of servers. But it must not have worked.

ACTION: Denis to continue debugging the session bug

#### TOPIC: Taskforces

Do we want to report status here, or just in project.webplatform.org?

We can subscribe to updates from task forces via project.webplatform.org

Also, cover highlights from the task teams in this weekly meeting.

##### SUBTOPIC: Community development task force

Not enough data from Feb 23rd DocSprint. Next DocSprint 4/3 around HTML5DevConf. They have on their conference webpage they have a signup for WPD. They have about 35 people signed up through EventBrite for conference website, and we have 70 or so on our site.

Sync community TF goals with project planning.

ACTION: scottrowe\_ to set up meeting about next doc sprint

There are young CS students who are interested in getting involved in community.

We are planning to have doc sprints on the east coast. One in Ohio this summer, and at least 2 doc sprints in NC (one in summer, one in fall) – NYC has been requested.

##### SUBTOPIC: Analytics task force

We're having our first meeting this week.

#### TOPIC: Content completeness

Now that we have project.webplatform.org, we'll build it into the workflow.

Promotion: Blog posts for even small new additions are great, but for big milestones, we should have more press outreach

ACTION: julee to follow up with garbee on how to do workflows and forms in BG (DONE)

We talked yesterday about figuring out fields and milestones. Garbee has promised to document things about BG and has committed to do some videos. We may want to set up another session for other people.

#### TOPIC: Any new or notable content to promote?

Adobe gave us some of Mike Sierra's times. He created several articles, one on transforms that's quite good. He's currently working on SVG I think that's notable and good to share. We've shared some of it and got a bunch of retweets. We should be more aggressive about tweeting out new batches of articles that we've created.

Also, for the last 6 months we've benefited from the participation of Dave Gash, a contractor at Google, worked on API pages and CSS properties. There are a handful more to do, then we should put together a comm plan for that content.

ACTION: shepazu to invite people to twitter account

Remember it's good to get a quick LGTM from someone in IRC for spelling, links, etc.

ACTION: peterlubbers to invite people to the Google+ admins

Folks are putting bylines on articles. That's appropriate for primary authors. It's a nice incentive.

perhaps we should have a clearer policy around author attribution or have a significant contributions page to highlight contributions? It's capture din MediaWiki, but not highlighted well.

publicity workflow -- it should be easy to rain kudos on a team member when they earn it

mozilla blog they have open badges 1.0 <https://blog.mozilla.org/blog/2013/03/14/open_badges/>

 ACTION: Julee to add comm plan as a topic for the community taskforce. (DONE)

#### TOPIC: Kuma

Denis has been reviewing Kuma, made a local installation. So far, it's been easy to install. But he needs to figure out if it can be a good fit. Janet sent Denis some contacts, Kuma developers. They've been very helpful. This is background stuff, shouldn't affect any work going on.

### Actions

-   Denis to follow up with Julee about sitemap generation [DONE]
-   Shepazu to allocate more spaces in future community meeting calls [DONE]
-   Shepazu to get richard ishia [sp?] comment on what a better solution will be. He's the W3C l18n expert [DEFERRED]
-   Denis and shepazu to talk about improving built-in search. [Denis is working on this.]
-   Denis to continue debugging the session bug [Denis is working on this.]
-   scottrowe\_ to set up meeting about next doc sprint [DONE – this meeting ;-) ]
-   julee to follow up with garbee on how to do workflows and forms in BG [Garbee is working on this.]
-   shepazu to invite people to twitter account [DONE]
-   peterlubbers to invite people to the Google+ admins [DONE]
-   Julee to add comm plan as a topic for the community taskforce [DONE]

## Agenda 2013-03-08

Meeting adjourned for lack of a quorum.

## Agenda 2013-03-01

-   Roll call
-   Review of open action items
-   [CSS Properties project](http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone)
    -   What are the next steps for this project?
-   DocSprints
    -   How was w3cconf DocSprint @ Adobe?
    -   Next DocSprint?
-   Session bug status?
-   Bug Genie status?
-   Dabblet status?
-   template for the native JS objects?
-   New task forces
    -   Communications and recruiting
    -   Analytics
    -   Reporting back to this meeting?
-   Anything blocking you from creating great content?
-   Any new or notable content to promote?

### Doc Sprints

<http://docs.webplatform.org/wiki/WPD:Community/Community_Events>

-   2/23 DocSprint: attendance: 27; CSS Properties worked on: 23
-   Possibility of next Docsprint at HTML5DevConf - Mid-April
-   Possible Docsprint in Puget Sound Area Mid-April
-   <http://openhelpconference.com/>

### Action items

-   JULEE will work on getting a burndown together [DONE]
-   Julee - Setup Analytics project at project.webplatform.org [DONE]
-   Eliot: Follow up on getting documentation into Editing Guidelines for using codelet at DocSprints to do code examples [DONE] [[[1]](http://docs.webplatform.org/wiki/WPD:Manual_Of_Style/Sample_best_practices)]
-   Julee to add agenda item for next week: Topic vs. Topic Clusters [DONE]
-   Julee to add agenda item for next week: Getting SME to review content [DONE]

## Agenda 2013-02-15

-   Roll call
-   Review of open action items
-   [CSS Properties status](http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone)
    -   How did the testing go? Were folks able to create property pages?
    -   Do we want to do some sort of review? How?
    -   How shall we divy up the remaining properties?
    -   What are the next steps for this project?
-   w3cconf DocSprint @ Adobe
    -   Who's going? (Shepazu, Craig, Eliot, Julee maybe Peter)
    -   What should we focus on?
-   Session bug status?
-   Bug Genie
-   Webplatform preso for w3cconf
-   Anything blocking you from creating great content?
-   Any new or notable content to promote?

### Summary

#### CARRIED OVER FROM LAST WEEK

1. ACTION (carried forward): shepazu + denis to implement sitemap extension

-   Carried forward again

2. ACTION (carried forward): Alex to sort out updating the CSS properties template to reflect Mike S's Gold standard CSS property page

-   Carried forward again

3. ACTION (carried forward): others should try to implement a CSS property page, and use chrismills' instructions when they are finished

-   Finished

4. ACTION (carried forward): determine a set of properties we know to be complex outliers

-   Finished

5. ACTION: JULEE to send out email to public list to get input regarding spec status (DONE)

-   Finished

6. ACTION: Shepazu to investigate cloud infrastructure and latency as possible roots of session bug

-   Investigated with help from HP Cloud people, no resolution as yet. Ongoing.

7. ACTION: chrismills: recruit more participants to css properties project, augmenting tracking spreadsheet, actively tracking progress

-   Ongoing. Has invited one person to take part (Rachel Andrew), who agreed to help out.

#### NEW ACTIONS FOR THIS WEEK

-   ACTION: chrismills, make google spreadsheet just show p0-p2, css properties
-   ACTION: chrismills: pull together 10-15 good CSS example pages and mail them around. People from different companies will then send these example pages to their resident CSS spec gurus, e.g Tab Atkins, Fantasai, Howcome, etc. and see what they think, as well as real world CSS gurus, e.g. Rachel Andrew, Chris Coyier, Peter Gasston, Dan Cederholm, Ethan Marcotte, Nicole Sullivan (their needs will be different.)
-   ACTION: all, give Doug suggestions on what to add to WPD session him and Janet are doing at W3Conf
-   ACTION: Scott to spruce up the APIs landing page

## Agenda 2013-02-01

-   Roll call
-   Review of open action items
-   [CSS Properties status](http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone)
    -   Exemplar and instructions are completed; 5 folks are testing the workflow.
    -   [Session bug](https://www.w3.org/Bugs/Public/buglist.cgi?query_format=specific&order=relevance%20desc&bug_status=__open__&product=webplatform.org&content=session&list_id=4654) was a blocker. Ryan tried to resolve the issue. Observations?
    -   Spec status values should be resolved. Lea brings up a good point: maybe we should be calling it "browser support". [20386](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20386) [18896](https://www.w3.org/Bugs/Public/show_bug.cgi?id=18896)
-   Dealing with browser compat info — it is hard and time consuming; can we automate it? See mail from Doug May: <http://lists.w3.org/Archives/Public/public-webplatform/2013Feb/0002.html>. See also: <http://docs.webplatform.org/wiki/WPD:Compatibility_Info>
-   Analytics?
-   Attracting contributors:
    -   Session bug needs resolving
    -   Getting started experience validated via usability study @ DocSprint Berlin
    -   Communications on blogs picking up
    -   Additional plans?
-   Anything blocking you from creating great content?
-   Any new or notable content to promote? Does someone want to write up a blog post for Web Audio API?

### Topics

-   TOPIC: CSS Properties project status
    -   SUBTOPIC: spec status value on exemplar page.
        -   <http://docs.webplatform.org/wiki/css/properties/font-size>
        -   <https://www.w3.org/Bugs/Public/show_bug.cgi?id=20386>
        -   font-style property page spec status: values are not usable; bug filed; considering different values than those of W3C
        -   How to represent feature status so visitor knows whether it's in most browsers? Production-ready?
        -   Community does need to know the status so it can participate. Need to bring the community in the standard development process; need to know if a spec is in "last call" or what, so the community can know whether/how to participate.
        -   Should we add information about level of usability? Providing both values? Should we move this info to the bottom of the page? Near compatibility? Or should it stay up top for easy identification? Maybe an easy flag up top with details below?
        -   html5please.com was offered up as a site that does it well: <http://html5please.com/#gradients>
    -   ACTION: JULEE to send out email to public list to get input.
    -   SUBTOPIC: The dreaded SESSION BUG!!! (Bug\#19914). Memcache fix does not appear to solve the problem. It might be cloud infrastructure issue.
    -   ACTION: Shepazu to investigate cloud infrastructure and latency
    -   SUBTOPIC: recruiting participants for CSS properties project
        -   ACTION: cmills: recruit more participants to css properties project, augmenting tracking spreadsheet, actively tracking progress
-   TOPIC: Doug May has a way of dealing with browser compat info — it is hard and time consuming; can we automate it? See mail from Doug May: <http://lists.w3.org/Archives/Public/public-webplatform/2013Feb/0002.html>. See also: <http://docs.webplatform.org/wiki/WPD:Compatibility_Info>
    -   shepazu: idea: to update compat from different sources: quirksmode, caniuse, w3c test suites/test the web forward and auto-generate from that
    -   Doug May is investigating data-tree based solution to assess the suitability of data point, then refine algorithm for data retrieval that includes human-intervention provision.
-   ACTION: Doug May and Chris to collaborate on solution in Berlin, and hopefully define a solution for SF doc sprint.
-   TOPIC: Analytics?
    -   What is the current status of work on analytics? Site traffic, usage, etc.

<http://docs.webplatform.org/wiki/Special:Statistics>

-   ACTION: Julee to call for participation/leadership on e-mail. [DONE]
-   TOPIC: Recruiting experts and editors.
    -   Cmills is working on recruiting CSS experts, get them to contribute.
-   ACTION: cmills: to contact university lecturers on garnering participation of college students.
    -   shepazu: maybe we could do college campus doc sprints
    -   shepazu: wary of unleashing this ahead of site estabilshment, Julee seconds
    -   Craig: need to improve the Getting Started workflows,

need to identify content areas of priority, focus on areas that provide sense of satisfaction

-   -   shepazu: would like to prioritize blog posts around content that is usable, current
    -   shepazu: use the blog software to draft, instead of e-mails
-   Motion to establish a working group to investigate, develop communications plan
-   ACTION: Scott to focus survey on doc sprints
-   ACTION: Julee: to mail calling for participation in communication/outreach working group (DONE)
-   ACTION: Eliot to start off-line thread around blog posting priorities, suitability
-   TOPIC: New and notable activities on WPD?
    -   <https://github.com/webplatform/Shortlinks> - fr0zenice's shortlinks system for WPD

### ACTIONS

-   ACTION (carried forward): shepazu + denis to implement sitemap extension: Concerns about current solution viability; looking for alternate.
-   ACTION (carried forward): julee and garbee to look into installing meetbot: Garbee to try to work on it more on the weekend. (DONE)
-   ACTION (carried forward): Alex to sort out updating the CSS properties template to reflect Mike S's Gold standard CSS property page: IN PROGRESS, Alex to consult w frozenice on scope.
-   ACTION (carried forward): others should try to implement a CSS property page, and use chrismills' instructions when they are finished: IN PROGRESS
-   ACTION (carried forward): determine a set of properties we know to be complex outliers: in progress

-   ACTION: JULEE to send out email to public list to get input regarding spec status (DONE)
-   ACTION: Shepazu to investigate cloud infrastructure and latency as possible roots of session bug
-   ACTION: cmills: recruit more participants to css properties project, augmenting tracking spreadsheet, actively tracking progress

#### Completed Actions

-   ACTION (carried forward): eliot to edit top level landing pages:DONE
-   ACTION: Mike S to move his static font-size example into the appropriate Wiki page:DONE
-   ACTION: Chris to finish writing a guide to implementing a CSS properties page:DONE
-   ACTION: Mike to work out how to specify "dependant/dependency properties":DONE
-   ACTION: Scott to add an instruction in the attribution template that says "hey - don't delete this or change this unless you have a really good reason":DONE
-   ACTION: Doug, Denis, Lea, work on implementing first phase of Dabblet live coding examples:DONE

## Agenda 2013-01-25

-   Roll call
-   Review of open action items
-   [CSS Properties milestones](http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone)
    -   Pick a few for folks to try out using Mike's example.
    -   Any volunteer to write up instructions based on Mike's gold standard?
-   Attributions
-   Status on code.webplatform.org?
-   Moving from MediaWiki
-   Status on "discoverability" [Search Bug](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19401)
    -   Do we have an interim solution we can implement quickly & easily
    -   We're going to put a search box on the [main page](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19694)
-   Analytics
-   Anything blocking you from creating great content?
-   Any new or notable content to promote?

### Actions

-   ACTION: shepazu + denis to implement sitemap extension
-   ACTION (carried forward): eliot to edit top level landing pages [DONE]
-   ACTION (carried forward): julee and garbee to look into installing meetbot (DONE)
-   ACTION: Alex to sort out updating the CSS properties template to reflect Mike S's Gold standard CSS property page
-   ACTION: Mike S to move his static font-size example into the appropriate Wiki page
-   ACTION: Chris to finish writing a guide to implementing a CSS properties page
-   ACTION: others should try to implement a CSS property page, and use chrismills' instructions when they are finished
-   ACTION: determine a set of properties we know to be complex outliers, and make sure they fit with Mike's scheme, for example background-image (with radial gradient, linear gradient, etc) perspective transforms with multiple values set (crazy: transforms take any \# of functions & assume defaults; "filter" prop takes functions in sequence) properties that don't have any effect unless another property is set. So for example, top, left, bottom, right don't have any effect unless you already set position: relative or position: absolute, flex and order do not have an effect unless display: flex is set properties that are proprietary and are only ever used with -ms- or -webkit-, for example
-   ACTION: Mike to work out how to specify "dependant/dependency properties"
-   ACTION: Scott to add an instruction in the attribution template that says "hey - don't delete this or change this unless you have a really good reason"
-   ACTION: Doug, Denis, Lea, work on implementing first phase of Dabblet live coding examples
-   ACTION: Doug to get together a task force to continue investigating an alternative to MW for our platform

## Agenda 2013-01-17

-   Roll call
-   Review of open action items
-   Status on code.webplatform.org?
-   [Scott's API proposal](http://docs.webplatform.org/wiki/WPD:Proposals/api_docs) ([See thread.](http://lists.w3.org/Archives/Public/public-webplatform/2013Jan/0069.html))
-   [CSS Properties milestones](http://docs.webplatform.org/wiki/WPD:Tasks/CSS_Property_Milestone).
-   Status from Chris Mills: "I made loads of progress on filling in the master CSS properties list today, building on top of Alex's great work. I'll try to finish this list tomorrow."
-   Status on "discoverability"
    -   [Search](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19401)
        -   Do we have an interim solution we can implement quickly & easily
        -   We're going to put a search box on the [main page](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19694)
    -   Global nav
    -   In-context ToCs
-   Anything blocking you from creating great content?
-   Any new or notable content to promote?
-   Need a new time for this meeting?

### Meeting Summary

-   Several folks weren't available to discuss open issues and action items.
-   We talked about a Table of Contents or nav at the top of articles. There was a TOC in the skin, and also one based on a user preference. They conflicted, so we took it out of the skin but if no users have set the preference to show it, we could bring the skin TOC back. But the default ToC was ever styled since

someone had a plugin they wanted to use.

-   We are planning blog posts on Audio API and CSS regions
-   Janet is going to FOSDEM. Anyone else?
-   CSS properties proposal: about 2/3 thru prioritization of properties. Goal is to finish tomorrow, and work on a "representative" article. Then we need to create an author's guide based on the representative article. The property worked on previously was 'font-size'. Mike Sierra to work on making a "gold standard" example page, that others can use as a model. <http://docs.webplatform.org/wiki/css/properties/font-size>

### Actions

ACTION: Julee to send out a Doodle poll to figure out a better time. [Done] ACTION: Mike Sierra to work on making a "gold standard" example page, that others can use as a model. [DONE] LAST WEEK ACTION: Julee to update Topic Hierarchy and Architecture pages. UPDATE: need site map LAST WEEK ACTION: Eliot to do an editorial pass on the proposed top-level pages. [DONE] LAST WEEK ACTION: Julee to set up meetbot. UPDATE: Garbee now has action item. (DONE)

## Agenda 2013-01-10

-   Roll call
-   Review of open action items
-   Triage of new content architecture issues
    -   All [content bugs](https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2513) are assigned to either Chris or Garbee. Do we want to re-assign some of them?
-   Status on [bug\#20160](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20160)
-   Current workflow for promoting new/great content? (Propose, Review, Sign-off?)
-   DocSprint in Germany
    -   Anyone going?
    -   Registration for the first european Doc Sprint in Berlin, Feb 8+9 2013, is now open. Please help to spread the word:
        -   [Share](https://plus.google.com/100575683580946332118/posts/iLxwzGU6zac)
        -   [Repost](https://alpha.app.net/klick_ass/post/2113801)
        -   [Retweet](https://twitter.com/klick_ass/status/281775907734167553)
-   Scott is working on Listing pages (Per Scott's email Thursday, December 20, 2012 11:35 AM; Subject: Re: New topic landing pages installed (was Re: We have a new front page))
-   Status on Dabblet?
-   Anything blocking you from creating great content?

## Meeting Summary

### Discussion

-   We're adding an API section to the topic landing pages. We need to include APIs and their icons on those pages. Seb is working on an icon, and Chris will put that in the landing page
-   Concept\_Listing template is done
-   Continuing to work on API area: reorganizing it and following through on previous work we've done. The APIs section is starting to come around, with help from Dave Gash.
-   Promoting new or great content. To post about WPD topics, see <http://docs.webplatform.org/wiki/WPD:Marketing/Posting_Guidelines>.
    -   The process right now is shoot it into the Mailing List, wait a bit, and see if anyone disagrees with it. Doug will set up additional bloggers. This content task force will continue to request suggestions for "Any new and notable content to promote"
-   DocSprint Germany: Scott Rowe is probably going.
-   We received status on the Dabblet extensions. The consensus on the list was code.webplatform.org. Lea has put the technical things in place in her codebase there's still some work to do to link from. First is a dabbler instance on code.webplatform.org. The second phase is to make it easy to open examples on the site in that instance (a "try now" button). Third phase is actual live code examples in the pages themselves. (possibly) via iframes. (There's actually a phase 4 that allows us to decouple a dependency on github.) We're aiming to have first phase done by next week. And we should have a blog post about it. We also need to get a template made with the form to submit/change code in the forms. Garbee is emailing Tomato this afternoon to see if she would be up for that.
-   We need more work on getting started pages (bug : <https://www.w3.org/Bugs/Public/show_bug.cgi?id=20160>). At last doc sprint was they just can't get through them -- somewhere between five and ten people. When we walked them through the basics, they had a hard time getting productive. Following through the instructions is difficult. It should be more self-serve. Julee to send outline of new Editor's Guide next week. Scott to work on usability testing. Also, there are going to be some people who don't respond to the given way. So maybe we have other docs for different mind sets. Scott and Peter are working on Getting Started videos.
    -   Additional Getting Started problems:
        -   The form system. For example, we've seen people wanting to use API\_Listing template on other pages, which breaks pages (it uses two forms).
        -   There was a glitch in the process for updating compatibility tables. A lot of the pages in the "Pages that need compatibility table" weren't working.
        -   A lot of people at the Sprint were confused with them. I actually spent most of the day there explaining it to people.
        -   A handful actually went to editing source because the button was there. Some of us want to remove that button unless you are an admin or in the template corp group whenever that gets made.
        -   Besides forms people were getting hit hard by the template bugs that require the hacks like | and =. We need to either fix it so those hacks aren't required or look at another way of doing things.
    -   Additional solutions:
        -   One way to fix the hacks would be editing as much as possible in raw HTML. Leaving mostly only links to be made in the wiki markup.
        -   Garbee has an open bug report for it iirc. Has been there for a while. I will bring attention to it once we get an in-house system going.
        -   People also seemed to be lost in what was needed to be done. We should try to use the content tracker to a greater extent once we get it in-house.
        -   Another way to approach it is that it will always be hard for new editors--so we can also focus on making EXISTING editors more productive and effective.
        -   "If you know something that needs to be done but don't have the time, even if it is a 5 minute thing, file a bug report." We should try to encourage that more.
        -   We also need better ways for people to get in touch with existing editors if they have questions. Not having a web chat system hurts a bit probably. (We could iframe freenode's webchat today and have a safe system online!)
-   Alex gives us a tantalizing tease: join meeting next week for some good news.
-   Everyone should feel free to add agenda items for these content meetings.

## Action Items

-   ACTION: Julee to add to weekly agenda template: "Any new and notable content to promote?" UPDATE: DONE
-   ACTION: Doug to add folks who responded to email thread as contributing bloggers.
-   ACTION: Julee and klick\_ass to write up WPD blog post about Germany Doc Sprint. (DONE)
-   ACTION: Julee to send out Ed Guide outline. (DONE)
-   ACTION: Scott to work on usability of Ed Guide.
-   LAST WEEK ACTION: Julee to update Topic Hierarchy and Architecture pages. (DONE)
-   LAST WEEK ACTION: Julee to send out an email discussing how we should "take" and re-assign bugs to even the work out more. (DONE)
-   LAST WEEK ACTION: Eliot to do an editorial pass on the proposed top-level pages. UPDATE: No status. now [DONE]
-   LAST WEEK ACTION: Jswisher to request the next level of detail on the global nav and how the reader accesses the content types as well as the technology areas. UPDATE: Janet sent out the email.
-   PREVIOUS ACTION: Julee to find out how to add a meeting bot to the Content TF Meeting. (DONE)
-   PREVIOUS ACTION: Julee to file a bug about the design of reference pages with a non-standard standardization status. (DONE)
    -   For needing the categories
    -   For needing the UI updated to reflect the categories
-   PREVIOUS ACTION: Garbee to send out his awesome task organization plan. UPDATE: sending it out today.

## Agenda 2012-12-13

-   Roll call
-   Review of open action items
-   Triage of new content architecture issues
    -   All [content bugs](https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2513) are assigned to either Chris or Garbee. Do we want to re-assign some of them?
-   Top-level navigation and design update from Chris Mills
    -   [Main landing page prototypes completed/subpage structures?/domain leads?](http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0172.html)
    -   [allow people to start their search by technology or page type](http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0235.html)
    -   [Different ways to browse](http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0221.html)
-   Anything blocking you from creating great content?

## Meeting summary

### Discussion

-   Note that the [content bugs](https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2513) are assigned to either Chris or Garbee. We wonder how do we spread these out to others? Maybe a larger issue than with just the content bugs?
-   Discussed top-level pages sent out by Chris. We generally thought Chris's [proposed pages](http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0172.html) were excellent. Eliot volunteered to do an edit pass on the descriptions. [DONE]
-   We discussed the [navigation proposals](http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0235.html) (and [Proposal for updating links on webplatform.org proposal for updating links](http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0221.html)) that have been in the email list. We discussed the pros and cons of providing the reader with a choice of content type or topic area, via hover links on the global nav. We would appreciate a mock-up. We are not sure how the different proposals would actually pan out. Jswisher took the action to follow up in the email threads and request the next level of detail.
-   We identified four priorities we're working on to make editing the site easier and hope to have this work completed by the new year:
    -   The global nav/landing pages, discussed above, that Chris Mills is working on
    -   The [consolidation of editorial pages](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20160) that Garbee is working on
    -   Updating the Topic Hierarchy and Architecture pages that Julee is working on
    -   The [session bug](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19390) that shepazu hopes will be resolved this weekend.
-   The Content Task Force will not meet for the next two weeks. We will resume again 1/3/2013.

### Action Items

-   Julee to update Topic Hierarchy and Architecture pages.
-   Julee to send out an email discussing how we should "take" and re-assign bugs to even the work out more.
-   Eliot to do an editorial pass on the [proposed top-level pages](http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0172.html). [DONE]
-   Jswisher to request the next level of detail on the global nav and how the reader accesses the content types as well as the technology areas.
-   LAST WEEK ACTION: Julee to find out how to add a meeting bot to the Content TF Meeting. (DONE)
    -   UPDATE: in progress
-   LAST WEEK ACTION: Julee to file a bug about the design of reference pages with a non-standard standardization status. (DONE)
    -   UPDATE: needs to be revised: Julee to file a UI bug about the design of reference pages with non-stable status, so that they look distinct. (DONE)
    -   Filed two bugs:
        -   [For needing the categories](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20386)
        -   [For needing the UI updated to reflect the categories](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20387)
-   LAST WEEK ACTION: Garbee to send out his awesome task organization plan
    -   UPDATE: still working on it

## Agenda 2012-12-06

-   Roll call
-   Review of open action items
-   Triage of new content architecture issues
    -   Identifying stable vs. proprietary and experimental features
    -   Style guide for example code [[20227](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20227%7Cbug)]
    -   Topic hierarchy needs updating
-   Anything blocking you from creating great content?
-   [[bug of site UX](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20180%7CMain)]
    -   Please review, especially in terms of content discoverability
    -   [[on adding a menu](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20250%7CBug)]
    -   [[for fixing top-level buckets](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19386%7CBug)]
-   New templates this week: listing pages
-   12/12/12 DocSprint?
    -   Any content-specific focus?
    -   Going? Going to be on IRC?
-   [[bugs](https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2496%7Ccontent)]: Content bugs in bugzilla need your input and resolution.

## Meeting summary

### Topics discussed

-   We discussed the status on the project/program manager for the content tasks. Alex said he realized that the term "project manager" might have caused some confusion and may have implied too big a scope. Really, it's more about someone who just follows through on Action items. We're continuing to discuss this with those who have volunteered for the role.
-   We discussed categorizing the features as stable, proprietary, experimental, and so on.We do have a page that calls out the different statuses: <http://docs.webplatform.org/wiki/Property:Standardization_Status>. We need to further discuss what are the appropriate categories for WPD. The <http://docs.webplatform.org/wiki/WPD:Pillars> page says that we should aim to be useful documentation for the web as it is, so categories such as "proprietary" are important, because we might document something that's useful but has legal restrictions. If there's something TOTALLY proprietary, we had talked about having that in a special vendor section as well
-   We discussed the example code style bug [20227](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20227%7CBug), but decided to table it for a couple of weeks, because Lea's dabbler code highlighting might land next Friday. (Here's what we have so far: <http://docs.webplatform.org/wiki/WPD:Manual_Of_Style/Sample_best_practices>)
-   Topic hierarchy page and architecture page is one place where people go to figure out where things go and where they will be. It needs updating. Julee volunteered to do this. We predicted that questions will probably arise from this task.
-   We want to ask each week: Anything blocking you from creating great content? This week, it's the session bug. Ryan has installed the newest version of mediawiki. There are a few conflicts, he's working to resolve those before deploying.
-   We called out the user experience bugs for this task force to review, especially to confirm designs are discoverable, accessible, and follows content architecture:
    -   <https://www.w3.org/Bugs/Public/show_bug.cgi?id=20180> (site organization)
    -   <https://www.w3.org/Bugs/Public/show_bug.cgi?id=20250> (global nav)
    -   <https://www.w3.org/Bugs/Public/show_bug.cgi?id=19386> (links from main)
-   This brought up another topic:
-   Use Meta bugs on bugzilla are big and fuzzy. Plans, proposals, and scratch pad work should be kept as subpages: <http://docs.webplatform.org/wiki/WPD:Plans>. Not in Bugzilla, and not in another site, such as GitHub. They keep the substantive discussion/plans in WPD:Plans/FOO, and then as actionable sub-items pop out, we file them as bugs that the meta bug depends on.
-   Garbee mentioned that one of the things with using Bug genie is we can edit comments. So we could actually use that as our place to put things like my Beginner's Guide outline as a comment, then just edit that comment when we update things. Further centralizing some creation there if we 1) Go with Bug Genie and 2) decide to use it that way. So an issue is just opened for it to be created, then the outline is one of the comments.
-   When new templates appear, such as the listing pages that were sent out for review this week, call it out in terms of content, reviewing it to make sure they make sense from content perspective.
-   We talked about the coming DocSprint at Google. Several folks are going. Several suggestions regarding promoting, gathering like-skilled folks together via tweeting and other social channels. Also several folks are going to try to get editors' feedback about their experience of the site.
-   We talked about the template corp and giving access to those who want to edit templates. But not on a one-off basis, more like giving group access.

### Decisions

-   Until we have a project management system in place, plans, proposals, and scratch pad work should be kept as subpages: <http://docs.webplatform.org/wiki/WPD:Plans>. Not in Bugzilla, and not in another site, such as GitHub.

### Action items

-   Julee to find out how to add a meeting bot to the Content TF Meeting. (DONE)
-   Julee to file a bug about the design of reference pages with a non-standard standardization status. (DONE)
-   Eliot to update bug 20227 with pointer to the style guide he wrote (DONE)
-   Garbee to send out his awesome task organization plan
-   Scott and Peter to explore social media channels about next week's docsprint

Proposed next discussion topics

## Agenda 2012-11-28

-   Roll call
-   Triage of new content architecture issues
-   Review of open action items
    -   The [New\_Page](/WPD:New_Page) page is up to date with example text and links
    -   just like the Getting Started page which has a [section that anticipates additional guides](/WPD:Getting_Started#Guides_to_creating_pages) with a link to
    -   the [Creating API Pages guide](/WPD:Creating_API_pages), where all of the above is captured, if not tamed.
    -   Action item for Mike and Julee to try out structure resulted in some issues which we'll continue to discuss today. (See Mike's email to public list 2012-11-15 re: creating api pages.)
-   Handling specialized API [in light of new guidelines](/WPD:Creating_API_pages).
    -   How to represent constants and exceptions on separate pages?
    -   Should APIs that add members to existing core interfaces be listed separately?
    -   Where appropriate, note the DOM node used to access each interface object: document, navigator, window, video, audio, etc.
-   [Task roadmap](/WPD:Task_Roadmap) includes content track, prioritizing content issues. (See email re: task roadmap for content, infrastructure and styling tasks from Chris Mills \<cmills@opera.com\>.)
-   [[bugs](https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2496%7Ccontent)]: Content bugs in bugzilla need your input and resolution.

## Meeting summary

### Topics discussed

-   We asked editors to review, update, address content bugs in the bug base: <https://www.w3.org/Bugs/Public/buglist.cgi?product=webplatform.org&component=content&resolution=---&list_id=2513>
-   We pointed out the new task roadmap: <http://docs.webplatform.org/wiki/WPD:Task_Roadmap>, and related email, and asked for comments. It's a high-level view that's very readable. Editing it (e.g.: adding columns) might be a bit tricky.
-   We discussed the need for a project management system and a program manager to ensure content tasks are triaged. WPD:Most\_Wanted\_Tasks isn't working and we need motivational leaders and tools.
-   We continued discussion on creating API pages, focusing on exceptions to the guidelines (WPD:Creating\_API\_pages).
    -   What to do for API that add members to an existing interface. For example, CSS Regions includes a new member in the Document interface - keep it with the API or the existing interface? Probably in both. But where does canonical page reside?
    -   What to do with lots of little bits of information, for example SVG attribute values or the HTML type element? For data modeling purposes, it might be best to create separate pages for each and then include them in the main page. What is best for folks importing, managing content? For the end-user?
-   We need to change the meeting time.

### Decisions

-   We will use bug base for tracking content areas that need to be created, such as DOM ranges.
-   Until project management for whole project is resolved, we will call out high-level direction on WPD:Task\_Roadmap and track specific content issues in bug base.
-   We will file content bugs on any additional open issues with the API.

### Action items

-   chrismills to set up a Doodle poll for next meeting times.
-   garbee to write guidelines on creating content bugs.
-   (was julee, is now) Garbee to write down (in bug creation guidelines) what issues go where (Bugzilla vs. WPD:Task\_Roadmap, WPD:Most\_Wanted\_Tasks, Special:WantedPages, WPD:Getting\_Started, etc.)
-   Alex to write up a description of the project manager's role.
-   All: review this summary to ensure accuracy.

### Proposed next discussion topics

Address any open issues with concepts and tutorials pages.
