---
title: '0207 raw mtg notes'
uri: 'WPD:Community/Meetings/General/2014/0207 raw mtg notes'

---
      jkomoros_

scribenick: jkomoros\_

topic: MDN Compat Tables

      jentesting

I won't be on the phone today, but I'll lurk in this channel if my tethered phone connection says working. This is Jen Simmons, btw.

    jkomoros_

shepazu: frozenice made a script to pull in data from MDN

... renoirb made a conversion script from that format into more clean data

    renoirb

is sorry to be late

    jkomoros_

... we're using MDN as the starting point for compat data, since it's tehc loest match to our page structure.

... using the caniuse json format to format the JSON

... later we'll work with our own data format that will be able to accomodate data from our sources

... but this is an easy first pass

... next we should be able to work on the medaiwiki extension that takes the json and injects into web pages

... uses something like this format

... we're going to modify that script slightly to work with the new data

... then I think we're good to put this data out

renoirb: There's some limitations on the script that frozenice mentioned

... trying to understand it, but basically it doesn't fetch all because of limitations on paginations on kuma

... so we might need to dig a bt deeper on that

shepazu: Might have to do with ratelimiting

    renoirb

Look at the "Current issues" <https://github.com/webplatform/mdn-compat-importer/blob/master/README.md#current-issues>

    jkomoros_

... the big thing is that we have a working conversion script

renoirb: This link \^ has information on the current issues

... so it's probably not all data, but we can compare later when we can get more

karlcow [\~karl@nerval.la-grange.net] entered the room.

    jkomoros_

jkomoros\_: Is this a run-once-and-never-again kind of thing?

shepazu: We've been assumign we're going to run it once

... MDN data isn't updated all of that often

... renoirb wrote a rigorous script (with frozenice ), so if we need to, we can run it again

jkomoros\_: I was more thinking, if we work on the data, later imports could blow it away

shepazu: I wish jswisher were here today, but we'd love to work closer with MDN

... there's room for improvement in the data, especially when we merge in caniuse

... we could have different data sources all munged into one data source

... we're going to do that with caniuse and W3C test suite anyway

... we could store our own updated data in a separate store and then merge those on

... so our data would take precedence over MDN (likely)

... make all the data available via the same API from multiple sources

shepazu: Jeremie Pationnier (sp?) is driving an effort in MDN to improve their compat tables data

... they weren't aware of this project. We'll make the normalized data available to them, obviously

... to help them structure their data more consistently. Hopefully we can convince the MDN folks to join forces with this project

hyperair left the room (quit: Ping timeout: 245 seconds).

    jkomoros_

jkomoros\_: That could be difficult in practice, but if it works, great!

shepazu: I'll reach out to MDN folks about what we're doing, our next steps, our current status, etc on Compat tables

... I'm going to try to work on the script (working with renoirb) over the next week to try to get the script (the extension for mediawiki) going

... will also work with ryanlane

... hopefully we'll have, by next friday, the compat table information generated and displayed in the site

[much rejoicing]

... after that, major blocker for announcing CSS prop project is the ready/not-ready flag

... we have the groundwork laid for that so hopefully it won't be too challenging

... eliezerb already wrote the template for that

... and then we need to start talking about how to make the announcement

topic: WPW for JS

shepazu: since jen isn't here we can't talk about home page effort

... so I think the rest of this meeting should be about JS WPW

... eliot helped drive a blog post from maxpolk about JS and the community

... I thought it was very nicely done

... we now have the JS stuff imported

... and have WPW coming up.

julee\_\_:

... this week I tried to get folks to contribute to the Gold Standard JS page

    renoirb

julee: I did a little bit

    jkomoros_

... no one volunteered. I did some work and then requested that folks contribute examples, and no one stepped up

... eliot added a sub-agenda item about what's the plan

...we have everything set up, we just need to have contributors and coordinators

... I'm a little hesitant about what will happen next week, since no one has stepped up yet

... maybe if we can have some of us on this phone call volunteer to coordinate

... and maye amplify the blog post

... and tweet

... to get some folks back into the fold

shepazu: I think there's a matter of bringing more people into the fold

... the people who care about JS might be different than the ones who helped out with WPW for CSS

... maybe we should have two WPW's running: JS and HTML at the same time?

    jkomoros_

julee: Given that we can't find enough for one, I think we should just focus on JS

    jkomoros_

eliot: We need to walk before we run

... the bottleneck now is getting it going, and JS is the priority above HTML

... if we have momentum from that we can look at also kicking off JS

... I agree that audiences are different potentially

shepazu: I think it will be harder to find JS people to contribute than HTML people to contrbute

... so it seems harder to start on JS than HTML

    jkomoros_

julee: i see that as well

    jkomoros_

... I was being firm on JS project since we had excitement about it this summer and had announced our intention

... but I'm willing to reassess

eliot: I think you're both right but [scribe was asleep at the wheel for a minute]

shepazu: so maybe we start more modestly as we ramp up. we have say 5 people

... maybe we do 5 JS pages a week to start (or maybe 10) and build up a base of contributors that way

... I'm concerned with having a gap if we aim too high (like 20), that could have us lose momentum

... maybe if we shoot for 5 and ramp up as capacity increases

    jkomoros_

julee: I'm less worried about numbers than having hte commitment to be coordinators

    jkomoros_

... and do the community work to pull folks in

shepazu: Filling out reference pages is easy but boring

... what if we tried to pair (or gave as an option) take a reference page, and also consider writing a longer article/tutorial about using the feature

... there might be some peopel that woudl appeal to

jkomoros\_: My gut is that's more work for them to do, making it less likely

    jkomoros_

julee: But making the work more interesting is a good idea

    jkomoros_

shepazu: So maybe we need to highlight the more interesting aspects

Jeremie [\~Jeremie@89.202.203.52] entered the room.

    jkomoros_

eliot: I think that's what came out in the CSS props project: people liked the example code bits best

julee\_\_: And if there are good examples on the page, then people who are less knolwedgable can pull from those to write reference

... this week when I tried to get people involved I asked fo rpeople to write examples

shepazu: I don't think I could write a good article on JS

... I could do it for SVG or HTML or CSS

... JS feels like it has a higher bar for quality

    renoirb

q+

shepazu, julee\_\_

Go ahead Eliott

    jkomoros_

eliot: What I say at doc sprints to that: "we're nto writing the definitive book, we're writing a wiki"

... others can come to edit/contribute/amend

... we're not shooting for perfect, but solid

shepazu: I still feel like JS is harder

... and that there will be others like me who are intimidated

renoirb: How about some of us take some time looking at good blogs/sites and ask them to help?

... and JS communities to contact

shepazu: What's the timing on all of this?

    jkomoros_

julee: I outlined in the blog post that we'll release the pages on tuesday nights

    jkomoros_

... and blog post specifically mentioned next tuesday

ACTION: everyone to share the blog post about JS WPW and contact people in their community to amplify and join

[renoirb, eliot, shepazu commit to being coordinators]

    jkomoros_

julee: Process can be same as before

    jkomoros_

... once people know what they're doing we can have people volunteer to coordinate

... plan was to get import done in Jan, WPW in Feb, and then we have the fluentconft

... where there are a lot of folks who can join us

... then the docsprint in... belgium?

shepazu: Isn't that on hold?

julee\_\_: After the docsprint in march we can assess if we're getting enough contributors, how it's going, or if we should move over to HTML

eliot: What about having HTML ready for fluent?

... to leverage that expertise there?

shepazu: That seems reasonable

    jkomoros_

julee: I thought fluent was more about JS developers

    jkomoros_

eliot: I think it will be both

    jentesting

Fluent used to be about JS only, but they are pushing hard to make it Web Platform in general

    jkomoros_

shepazu: Just want to make sure we don't turn people away who don't want to do JS

    jentesting

and yes, the Belgium doc sprint doesn't have any dates. April was proposed, but won't work.

    jkomoros_

eliot: I'm willing to drive that effort to get ready for HTML by then

    jkomoros_

julee: and I can help as well... I just don't know if we have enough consistent community management to be able to handle both

\_cheney left the room (quit: Read error: Connection reset by peer).

\_cheney [\~cheney@nat.sierrabravo.net] entered the room.

mode (+o \_cheney) by ChanServ

    jkomoros_

eliiot: I think most important is getting the golden example pages for element + attribute

    jkomoros_

julee: I'm okay with that

    jkomoros_

... especially given the number of peopel who will be there

eliot: I'll be there, too

... docsprint is open to public

shepazu: So we have a plan to announce and what we'll be doing

eliot: I'm sitll a little unclear about this coming week's

shepazu: My perception is that we have a: we work on a blogpost and each of us tries to find at least one expert to volunteer

julee\_\_: The blgopost is already out to point people at

... sot he idea is to announce that the WPW will start next wek

... and send out to folks

... on tuesday we should have a blog post about the topics for the first week

... I was going to start with Array and see who shows up

shepazu: MDN has excellent JS docs

... maybe we should see if people who contributed there would be interested in being involved

ACTION shepazu to reach out to MDN folks who contributed to JS documentation and see if they want to be involved in JS WPW

    renoirb

wants to have your feeling about <http://www.w3.org/mid/2703272A-5C27-4FDE-A62A-7133307BE3D2@w3.org>

AGENDA+ \^

    jkomoros_

[scribe was distracted for a few minutes]

shepazu: I think to keep the community we need to keep up the engagement

... short term we just need to find people to help with JS stuff

ACTION: shepazu to create a doodle poll about moving this meeting
