jkomoros_
9:08

scribenick: jkomoros_
9:08

topic: MDN Compat Tables
jentesting
9:08

I won't be on the phone today, but I'll lurk in this channel if my tethered phone connection says working. This is Jen Simmons, btw.
jkomoros_
9:08

shepazu: frozenice made a script to pull in data from MDN
9:09

... renoirb made a conversion script from that format into more clean data
renoirb
9:09

is sorry to be late
jkomoros_
9:10

... we're using MDN as the starting point for compat data, since it's tehc loest match to our page structure.
9:10

... using the caniuse json format to format the JSON
9:10

... later we'll work with our own data format that will be able to accomodate data from our sources
9:10

... but this is an easy first pass
9:11

... next we should be able to work on the medaiwiki extension that takes the json and injects into web pages
9:11

... uses something like this format
9:11

... we're going to modify that script slightly to work with the new data
9:11

... then I think we're good to put this data out
9:11

renoirb: There's some limitations on the script that frozenice mentioned
9:12

... trying to understand it, but basically it doesn't fetch all because of limitations on paginations on kuma
9:12

... so we might need to dig a bt deeper on that
9:12

shepazu: Might have to do with ratelimiting
renoirb
9:12

Look at the "Current issues" https://github.com/webplatform/mdn-compat-importer/blob/master/README.md#current-issues
jkomoros_
9:12

... the big thing is that we have a working conversion script
9:12

renoirb: This link ^ has information on the current issues
9:12

... so it's probably not all data, but we can compare later when we can get more
9:13

karlcow [~karl@nerval.la-grange.net] entered the room.
jkomoros_
9:13

jkomoros_: Is this a run-once-and-never-again kind of thing?
9:13

shepazu: We've been assumign we're going to run it once
9:13

... MDN data isn't updated all of that often
9:13

... renoirb wrote a rigorous script (with frozenice ), so if we need to, we can run it again
9:14

jkomoros_: I was more thinking, if we work on the data, later imports could blow it away
9:14

shepazu: I wish jswisher were here today, but we'd love to work closer with MDN
9:14

... there's room for improvement in the data, especially when we merge in caniuse
9:14

... we could have different data sources all munged into one data source
9:15

... we're going to do that with caniuse and W3C test suite anyway
9:15

... we could store our own updated data in a separate store and then merge those on
9:15

... so our data would take precedence over MDN (likely)
9:15

... make all the data available via the same API from multiple sources
9:16

shepazu: Jeremie Pationnier (sp?) is driving an effort in MDN to improve their compat tables data
9:16

... they weren't aware of this project. We'll make the normalized data available to them, obviously
9:17

... to help them structure their data more consistently. Hopefully we can convince the MDN folks to join forces with this project
9:17

hyperair left the room (quit: Ping timeout: 245 seconds).
jkomoros_
9:17

jkomoros_: That could be difficult in practice, but if it works, great!
9:18

shepazu: I'll reach out to MDN folks about what we're doing, our next steps, our current status, etc on Compat tables
9:18

... I'm going to try to work on the script (working with renoirb) over the next week to try to get the script (the extension for mediawiki) going
9:18

... will also work with ryanlane
9:19

... hopefully we'll have, by next friday, the compat table information generated and displayed in the site
9:19

[much rejoicing]
9:19

... after that, major blocker for announcing CSS prop project is the ready/not-ready flag
9:19

... we have the groundwork laid for that so hopefully it won't be too challenging
9:20

... eliezerb already wrote the template for that
9:20

... and then we need to start talking about how to make the announcement
9:21

topic: WPW for JS
9:21

shepazu: since jen isn't here we can't talk about home page effort
9:21

... so I think the rest of this meeting should be about JS WPW
9:21

... eliot helped drive a blog post from maxpolk about JS and the community
9:22

... I thought it was very nicely done
9:22

... we now have the JS stuff imported
9:22

... and have WPW coming up.
9:22

julee__:
9:23

... this week I tried to get folks to contribute to the Gold Standard JS page
renoirb
9:23

julee: I did a little bit  
jkomoros_
9:23

... no one volunteered. I did some work and then requested that folks contribute examples, and no one stepped up
9:23

... eliot added a sub-agenda item about what's the plan
9:23

...we have everything set up, we just need to have contributors and coordinators
9:23

... I'm a little hesitant about what will happen next week, since no one has stepped up yet
9:24

... maybe if we can have some of us on this phone call volunteer to coordinate
9:24

... and maye amplify the blog post
9:24

... and tweet
9:24

... to get some folks back into the fold
9:24

shepazu: I think there's a matter of bringing more people into the fold
9:24

... the people who care about JS might be different than the ones who helped out with WPW for CSS
9:25

... maybe we should have two WPW's running: JS and HTML at the same time?
jkomoros_
9:25

julee: Given that we can't find enough for one, I think we should just focus on JS
jkomoros_
9:25

eliot: We need to walk before we run
9:25

... the bottleneck now is getting it going, and JS is the priority above HTML
9:26

... if we have momentum from that we can look at also kicking off JS
9:26

... I agree that audiences are different potentially
9:26

shepazu: I think it will be harder to find JS people to contribute than HTML people to contrbute
9:26

... so it seems harder to start on JS than HTML
jkomoros_
9:26

julee: i see that as well
jkomoros_
9:27

... I was being firm on JS project since we had excitement about it this summer and had announced our intention
9:27

... but I'm willing to reassess
9:28

eliot: I think you're both right but [scribe was asleep at the wheel for a minute]
9:28

shepazu: so maybe we start more modestly as we ramp up. we have say 5 people
9:28

... maybe we do 5 JS pages a week to start (or maybe 10) and build up a base of contributors that way
9:29

... I'm concerned with having a gap if we aim too high (like 20), that could have us lose momentum
9:29

... maybe if we shoot for 5 and ramp up as capacity increases
jkomoros_
9:29

julee: I'm less worried about numbers than having hte commitment to be coordinators
jkomoros_
9:29

... and do the community work to pull folks in
9:30

shepazu: Filling out reference pages is easy but boring
9:30

... what if we tried to pair (or gave as an option) take a reference page, and also consider writing a longer article/tutorial about using the feature
9:30

... there might be some peopel that woudl appeal to
9:31

jkomoros_: My gut is that's more work for them to do, making it less likely
jkomoros_
9:31

julee: But making the work more interesting is a good idea
jkomoros_
9:31

shepazu: So maybe we need to highlight the more interesting aspects
9:32

Jeremie [~Jeremie@89.202.203.52] entered the room.
jkomoros_
9:32

eliot: I think that's what came out in the CSS props project: people liked the example code bits best
9:32

julee__: And if there are good examples on the page, then people who are less knolwedgable can pull from those to write reference
9:32

... this week when I tried to get people involved I asked fo rpeople to write examples
9:33

shepazu: I don't think I could write a good article on JS
9:33

... I could do it for SVG or HTML or CSS
9:33

... JS feels like it has a higher bar for quality
renoirb
9:33

q+
9:34

shepazu, julee__
9:34

Go ahead Eliott
jkomoros_
9:34

eliot: What I say at doc sprints to that: "we're nto writing the definitive book, we're writing a wiki"
9:34

... others can come to edit/contribute/amend
9:34

... we're not shooting for perfect, but solid
9:35

shepazu: I still feel like JS is harder
9:35

... and that there will be others like me who are intimidated
9:36

renoirb: How about some of us take some time looking at good blogs/sites and ask them to help?
9:36

... and JS communities to contact
9:37

shepazu: What's the timing on all of this?
jkomoros_
9:37

julee: I outlined in the blog post that we'll release the pages on tuesday nights
jkomoros_
9:37

... and blog post specifically mentioned next tuesday
9:37

ACTION: everyone to share the blog post about JS WPW and contact people in their community to amplify and join
9:38

[renoirb, eliot, shepazu commit to being coordinators]
jkomoros_
9:38

julee: Process can be same as before
jkomoros_
9:39

... once people know what they're doing we can have people volunteer to coordinate
9:39

... plan was to get import done in Jan, WPW in Feb, and then we have the fluentconft
9:39

... where there are a lot of folks who can join us
9:39

... then the docsprint in... belgium?
9:39

shepazu: Isn't that on hold?
9:40

julee__: After the docsprint in march we can assess if we're getting enough contributors, how it's going, or if we should move over to HTML
9:40

eliot: What about having HTML ready for fluent?
9:40

... to leverage that expertise there?
9:40

shepazu: That seems reasonable
jkomoros_
9:40

julee: I thought fluent was more about JS developers
jkomoros_
9:40

eliot: I think it will be both
jentesting
9:41

Fluent used to be about JS only, but they are pushing hard to make it Web Platform in general
jkomoros_
9:41

shepazu: Just want to make sure we don't turn people away who don't want to do JS
jentesting
9:41

and yes, the Belgium doc sprint doesn't have any dates. April was proposed, but won't work.
jkomoros_
9:41

eliot: I'm willing to drive that effort to get ready for HTML by then
jkomoros_
9:42

julee: and I can help as well... I just don't know if we have enough consistent community management to be able to handle both
9:42

_cheney left the room (quit: Read error: Connection reset by peer).
9:43

_cheney [~cheney@nat.sierrabravo.net] entered the room.
9:43

mode (+o _cheney) by ChanServ
jkomoros_
9:43

eliiot: I think most important is getting the golden example pages for element + attribute
jkomoros_
9:43

julee: I'm okay with that
jkomoros_
9:43

... especially given the number of peopel who will be there
9:43

eliot: I'll be there, too
9:44

... docsprint is open to public
9:45

shepazu: So we have a plan to announce and what we'll be doing
9:45

eliot: I'm sitll a little unclear about this coming week's
9:45

shepazu: My perception is that we have a: we work on a blogpost and each of us tries to find at least one expert to volunteer
9:45

julee__: The blgopost is already out to point people at
9:45

... sot he idea is to announce that the WPW will start next wek
9:45

... and send out to folks
9:45

... on tuesday we should have a blog post about the topics for the first week
9:46

... I was going to start with Array and see who shows up
9:46

shepazu: MDN has excellent JS docs
9:47

... maybe we should see if people who contributed there would be interested in being involved
9:47

ACTION shepazu to reach out to MDN folks who contributed to JS documentation and see if they want to be involved in JS WPW
renoirb
9:49

wants to have your feeling about http://www.w3.org/mid/2703272A-5C27-4FDE-A62A-7133307BE3D2@w3.org
9:49

AGENDA+ ^
jkomoros_
9:50

[scribe was distracted for a few minutes]
9:50

shepazu: I think to keep the community we need to keep up the engagement
9:50

... short term we just need to find people to help with JS stuff
9:53

ACTION: shepazu to create a doodle poll about moving this meeting