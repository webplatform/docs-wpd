---
title: 1122 raw mtg notes
uri: 'WPD:Community/Meetings/General/2013/1122 raw mtg notes'

---
scribenick: jkomoros

topic: HTML Elements

q+

eliot: Happy to be coordinator on it, in parallel to JS work. important to move forward with a regular heart beat, have WPW on them, etc

shepazu: I think this is a great idea. It's also conspicuous that we don't have them. this content is the kind of stuff that you can find anywhere but people see we don't have HTML, and then are disappointed

eliot: When we did the CSS font property page as an example? we should do the same thing for a representative HTML Element and Attribute

jensimmons: I'd be happy to work on that looking to help with a design. Imaginging: what's it like to be a student, etc, do people understand the page? not visually, but in terms of content. could do a study of how other successful sites are doing it

shepazu: That's how we approached CSS that sounds like a great plan

ACTION: eliot to create example attribute/element pages

maxpolk: There's convergence between elements, apis, etc there are side links between various pages

eliot: That's how it is in the specs as well

topic: Dave Gash is working on reorg of HTML DOM API

dgash: The main thrust is we have 100's or maybe even 1000's of pages that have been imported to long URLs with things like "events" "properties" etc that aren't necessary geting rid of interstitials and moving them to where they sit done this under dom node, and audio/video, and in th emiddle of traversal the end result of this that the pages will be in a more logical order and available for review and editing still have quite a few to go, but that's what I'm working on at the moment.

julee: Eliot's primary project is to get the pages themselves done we've lost some momentum on the actual content creation, want to help bring in contributors again

shepazu: A few peopel has asked me, when will WPW start back again?

eliot: As soon as we have a page template

jensimmons: My other projects will wrap up soon, so I can get started on this next week

maxpolk: There's an html elements effort, right? there's a form, for example

eliot; And we imported elements from MSDN it just needs to be reviewed and given best practices

julee: We like to have a golden example to refer to

jensimmons: It seems like the structure of the content was originally based on the import, but this would be a good time to rethink some of the organization?

shepazu: Absolutely

eliot: We did SOME of it back at the import

jkomoros: Yeah, we made an effort

eliot: So it needs some work, but there's a bit of structure there already

shepazu: And we should never stop thinking about how we can improve the pages

maxpolk: We should try to automate what we can

agenda: CSS Compat tables

julee: Last time someone had done client side stuff and it was getting ready for testing?

shepazu: renoirb deplohyed on the test wiki the extension he said it seemed to work, but we need to put it through its paces

Hey hi the other part of the problem is collecting data Ronald Mansfeld started very enthusiastically but he has lost a bit of momentum a few weeks ago haven't heard from him in awjhile I just e-mailed him last night Ronald has designed a data model and started pulling the data from MDN but he hasn't responded recently I tried e-mail, now I'll try contacting other people who might know him worst case we'll have to start again from the json data model on github

renoirb: Regarding the extension for compat tab les, it's likely a problem with varnish caching; but it's working in the test instance so I just need to adjust the way the tag is written

ESI tags can be seen here <http://docs.webplatform.org/test/Tests/Compatibility_table_and_caching>

ACTION: shepazu and renoirb to figure out how well the compat table extension is working; lock it down

renoirb: I also started talking to fastly people, and they supported me.

Topic: Js Import

maxpolk: I believe renoirb fixed the import bug

renoirb: Yeah, there was some missing part in the caching. It's basically fixed.

maxpolk: So now I'm unblocked for importing JS into the test wiki this includes the changes to the URL scheme it's evolutionary, it's just to have a look at how it feels I dropped it for a bit when it went idle, but now it's my top priority again

shepazu: Max and I met in person and hashed some stuff out over dinner and coffee and we sorted out that this should be a iterative process it's not done yet. like, for example we don't have templates for these. we're going to need to make templates, just regular wiki markup phase 1 is us taking a look at it jensimmons , this is another part where looking at other successful sites for JS reference

eliot: I'd like to urge a sense of urgency. I'm getting questions from the team who donated about when it will show up presumably seeing it on the test wiki would be a step in the right direction

maxpolk: It should be in the next couple of days I came have it up. but some of the text will need work; like things that are IE specific

eliot: We can handle that in manual review, too.

maxpolk: Conceptually the templates aren't hard to output to

shepazu: Does anyone have time/expertise in making expertise tempaltes

maxpolk: Ideally you look at page content before coming up with templates?

jensimmons: Should I focus on HTML or JS first?

(everyone murmurs agreement about JS)

julee: I started a thread on this back in the day so there's some info out there getting some ECMAScript people to help work through it that would really help as well I know shepazu contacted some folks before maybe we could all reach out to our favorite JS expert and ask for their opinion on these threads

shepazu: Another thing that might help is for us to all compile a list of JS doc pages that we like to help seed that

jensimmons: I'll do at a competitive analysis fo other docs sites, but also what other resources do devs use? and talk to some real developers with the goal of making something BETTER

shepazu: It doesn't have to be perfect to start, we can keep iterating

jensimmons: Yeah, I'll do it as quickly as I can

Topic: How was TPAC?

Topic: (As well): Universal Access pointers

eliot: Doug and I did a breakout session on WPD lightly attended, but good representative group and good discussion Brian Sullivan from AT&T pointed out a lack of mobile content Cynthia Shelly from Microsoft is working with W3C taskforce on accessibility Larry Masinter talked about areas of deep knowledges--where beginner and intermediate developers wouldn't go we had outreach by at least two peopel who have tools to grab API information from specs and turn it into content

julee: By the way, I work with a slightly different Larry than the one you talked to

maxpolk: I thought the automation was curious is that even a reasonable possibility for JS, going to ECMA

eliot: The tools currently point at W3C specs but dom on W3C tool is looking at the Khronos WebGL spec as well it woudl be difficult to port over all the WebGL stuff by hand lots of goodness that could potentially come out of this tool

shepazu: There were other good side conversations there I talked to a few guys from GitHub they are investigating W3DC

s/W3DC/W3C I had good conversations about CMS stuff with them also had good conversations with Akamai (one of the biggest CDNs) they collect really good stats on browser usage and content usage maybe they could expose those stats via WPD

eliot: Richard Ashida requestsed that we make available for each templated topic a section on universal accessibility (internationalization and accessibility)

s/Ashida/Ishida/

shepazu: Basically the idea would be a section that links out to other resources about accessibiltity and internationalization in the future getting it folded into content but for now having each page point to good docs for that specific topic would be a good start

eliot: This would be hidden unless it has content in it

shepazu: We'd need to change the template of all of the pages to include Universal Access

eliot: We told him, we're strapped for resources, so can't do this in the near future

ACTION: shepazu to talk to MediaWiki folks and see if someone can help with templates

shepazu: Another piece of feedback someone thought we needed to have more stubs so that there could be all of the relevant links, and then fill it in as we have the time and energy we've talked about this before: a master list of content we know we want I think there's value in that different contributors might have different interests and not be interested in our main push project at the moment

julee: I want to have a clear UI experience for a page ready for consumption vs page that's in progress we've also talked about consolidating flags into one alert icon or something having the whole structure would be good in that case but if we have tons of pages but with no differentiation it could lead to confusion

jensimmons: As a new person to the site, I'm confused when surfing around the site

agenda: Status on migration

s/agenda/topic

renoirb: I need to sync with ryan about making a copy of the database so no news yet on the real meat

shepazu: I'll push the issue with DH today renoirb and ryan will work to be ready to go when DH pushes the button it would be good to talk to Ryan today if we can. The ideal time to pause is probably late at night on a weekend

eliot: So next meeting is two weeks from today, right?

Thanks, jkomoros!

Meeting over