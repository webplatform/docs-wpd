---
title: 0110 raw mtg notes
uri: 'WPD:Community/Meetings/General/2014/0110 raw mtg notes'

---
Jkomoros is scribenik

topic: Template discussions

shepazu: How many page types are there for JS?

gelph: They all follow the same basic format. There are only a few top-level or summary pages using the semantic extension you're able to pull in sub-pages into the concepts page so for example with CSS elements you might have properties of that as sub-pages get pulled into a summary section we haven't thought about that much for the JS parts

shepazu: I think it will be more difficult to do the import in that way I think for the first import pass, what we have there will be sufficient to get people working on it, and then we can think more deeply about it in the future like when Jen came on the project, she came in and had good ideas to organize pages better seeing it all in context was what allowed her to make those decisions so I'm personally in favor of pushing the button and going with what we have?

elliott: Is there an argument that it will be harder to fix later?

gelph: Once we do the import, as long as people haven't touched them too much in the meantime, we can do another import later

shepazu: We could make a bot that does a batch process, for example that wouldn't need another import Elliott, I think the task would be not much more difficult to do after we import it knowing how long this has taken already, I think we should do it

Elliott: I'm in agreement, just wanted to ask the question to verify we were aware of the constraints

julee\_: If we had the same section heading and wanted to format it in a different way, it could overwrite the data I feel like people should start getting into the pages. I don't think there’s anything with the structure right now that's so horrible that we should hold off the import

shepazu: Worst case scenario we could keep the old changes and then reimport

gelph: The WPD tool which someone else wrote, I was tweaking, it does a lot like bulk import bulk delete we might be able ot use that to do what shepazu just described, relatively easily

shepazu: I think unless anyone has a real game-changer, we should do the import

julee\_: IS hte next step for eliezerb to publish the live template on the site?

gelph: The template we should iterate a little bit over that: try it and iterate and do another import

julee: eliezerb has done the template: max do you find the template to be good enough? so we'll tell eliezerb to go ahead and publish on the live site and then you two can iterate on it together push to the live site, but start with a small batch of test pages I was getting the senses that he's providing you with all of the values necessary to do the import without losing data so do a quick test, then do an import on the live site

gelph: I'm ready to begin that

Right now we have just the JS Object page with a Form and Templates... Should we finish the other pages (JS Properties, and so on)?

ACTION: eliezerb to publish his JS template

ACTION: gelph to do the import to the live site

julee\_: And elizierb should know that right now gelph is his only customer

gelph: Just as a mitigating factor, there are existing pages in that same space that are kind of in the way; there's some work done there already. We'd talked about moving them temporarily the import generally wipes the space clean and then reimports in javascript/array, etc

julee\_: Can we move them to Meta: namespace? just so we don't lose them?

Elliott: And then mark them all as merge candidates that would be a nice item for a docsprint, too. Go through them and see what needs to be merged.

(Reference to existing pages: <http://docs.webplatform.org/wiki/javascript> )

shepazu: eliezerb , it seems as though if we're going to have JS properties right now we're just going to forgo that, because it would complicate the import

Ok and we'll consider doing that at a later stage so we just one template for now so eliezerb are you good to work closely with max?

eliezerb : Sure, I've a lot of free time until end of January

shepazu: Thank you gelph and eliezerb, you are awesome. This is absolutely how we hoped the community would worked

It's always a pleasure work with gelph

jswisher : are you on the phone?

julee: There's a docsprint in march, we can focus on JS stuff

julee: yes, I'm here

jensimmons: There's also a docsprint planned in Belgium in FEb

julee: We'll start the WPDW again after the JS stuff is imported

jswisher: There's a possibility I might be able to go to that I might be in Europe in mid to late Feb, so it will just depend on timing

topic: Landing page

jensimmons: I wrote up a few pages, thinking about who will be going to the homepage of the website how will they get there, what will they be looking for the feedback you sent focused me on collecting contributors to help build content, rather than useful for folks to use the content nwo that the CSS properties work is done, we might want to think about that latter one more while still communicating this is a project with big ambitions and we'd love your help

shepazu: I'm interpreting what you say as "there's value in having the methodology of user stories first," and what you applied that first to is applying it to consumers who want to consume content, but now you recognize there's another constituency: contributors (both content and code, see eliezerb and gelph for great examples of the latter) so maybe we should split the page for the two audiences? like on the left one, on the right the other

jensimmons: I think that makes sense; I think over time the amount of real estate given to those use cases will shift

jswisher: I think splitting it might be a reasonable approach on the one hand, the "what the heck is this?" "I need info on FOO", and "how can I help" are the three main questions

julee: We're talking about www, the main landing page. And then we also have the main page off of docs.webplatform.org, and that's the top-level nav page for the content

[missed a few seconds of that]

jensimmons: I think that's a terrific idea it's also the main landing page for how to contribute as well

shepazu: I propose we take a few actions I like Jen's idea of using user stories. I think the user stories for the consumers were good. I suggest that each of us does a user story (I'll do one) for a contributor I'll do one of ra code contributor maybe another is a designer, one's a developer another one is someone coming from the standards world and I'm sure there are others

zatan left the room (quit: Read error: Connection reset by peer). then we'll have armed jen with what she needs and the other thing is there could be user stories about explaining it to a newbie so the landing page has three areas: what is this, how can I help, how can I use it?

jensimmons: That would be great! especially since you guys have been working with contributors so you know the kinds of typical person who comes to the site that's the area I'm most vague

shepazu: Another area is a user story around docsprints

eliot: Another is for content requests, like WebVTT

shepazu: That's the example I was thinking about for someone from standards

jswisher: I need to drop off the call, but I'm very interested in helping with this I'll still be in IRC, so just ping me if you want my help, I can collaborate over e-mail

jensimmons: These will help us focus, just very tight

A front-end developer

A student

A senior-level programmer

gelph: If you flip this whole thing around: instead of writing a use case, maybe conduct a survey of contributors?

Someone in the web industry googles the phrase “webplatform” because they keep hearing it

A junior-level web developer

Someone who already knows all about Web Platform heads to the website to find out the latest status you might find out that, for example, "I participated because it's related to W3C so much more durable than something done by private company"

shepazu: I love that idea it gives us a great source of blurbs as endorsements of the sites

julee: We should have a quick turnaround on this

shepazu: Let's aim for next Wednesday Jen, can we do this on the website itself?

jensimmons: Sure, although I don't understand how it works

shepazu: I'll help you figure it out, Jen

<http://docs.webplatform.org/wiki/WPD:Projects>

gelph: The fact Jen asked us, that's the first survey result

shepazu: I can put together the survey thing; W3C has a survey tool but it's kind of ugly

eliot: I've used surveymonkey successfully before

shepazu: I'll look at that and Google docs and see what's easiest

jensimmons: There's a great question here around "how did you become a contributor", "how did you hear about us in the first place?" but you could even take an opportunity to do a bigger survey, about what HAPPENS to contributors

gelph: 6 months ago shepazu spoke about recognition and it's importance

s/it's/its

shepazu: Let's take it to the list to design the survey

The survey could help set priorities for the next short-term future

julee: The survey has expanded; we shouldn't have it block the home page redesign

shepazu: We can do them in parallel

eliot: I suggest we design the survey on the wiki

shepazu: We had a decision that eliezerb 's flags thing is good there was a lot of talk about having a bot go through and transfer all the old flags to the new flag system we have a page, each page template has a number of sub-templates one of the subs is about flags, and we currently have them populated by lots of values the feedback is that's scary and discouraging so we've decided to simplify them and subsume the fine-grained flagging eliezerb experimented and figured out how to make a new flag template that was much simpler the data currently stored in the old flag template will still be there, just not shown this flag system is how we're telling people if pages are ready or not ready we don't yet know who will write the bot to transfer old flags into new system I suggest that for the sake of moving forward that we don't do that flag now; we'll always have the data present if we need it. We deploy eliezerb 's template to make sure that pages that need to be flagged as not ready are flagged correclty

We can put those old flags in a text block... simplifying will allow us to solve it more easily

<http://docs.webplatform.org/test/css/properties/border> the old values will be stored in the wikitext, but NOT shown in the output page or the forms unfortunately we can not set a default value (eliezerb investigated) if we could, I would default to say a page is not done, and then over the course of a few days mark them as done if htey ware but we can't do that we still need someone to write a bot--but a simpler bot--and if something's not on a whitelist... someone could write a bot to mark all of them as not done but maybe frozenice could help here?

gelph: THis is surprisingly similar to the earlier task about JS templates and fixing later

shepazu: gelph Would you be interested in looking into this stuff after the JS stuff is done?

gelph: Yep

shepazu: So here's the proposed plan: we remove from the form the existing flags (verifying that the data is not accidentally overwritten when the form is gone and subsequent edits happen) then we replace the old template with the new template on all pages then gelph investigates changing those values to set them to "not done" via a bot and we come up with a whitelist of pages we think we're done which will conveniently be a list of things we can talk about being done it's not jsut CSS stuff; the DOM stuff is pretty solid, too

gelph: At the end of those massive CGI movies, there's a title called "Data Wrangler". Maybe I should have that title

shepazu: We should absolutely call out folks like gelph and frozenice for their amazing work

shepazu: Also on the list we should figure out how to give people titles to recognize the work they do it's another reason for other people to contribute: they can see official recognition comes to anyone who works

julee: I think we definitely need a community management plan

shepazu: What about having those titles on the front page?

jensimmons: What about more blog posts? the whole list on the home page might be too much, but easy to get to from the home page, maybe with a few examples on the home page

shepazu: And then we show people, "here's how these people earned recognition, and you can too"

topic: Compatibility tables

shepazu: I don't have the attention span to solve the problem myself we had a volunteer, but after he recognized the depth of complexity realized that he didn't have the time the problem's not impossible, but outside my expertise the problem is we're using results from MDN as our first-pass solution there's two problems: MDN data is a bit noisy (doesn't have tests to back up data), but people do find the data useful we have the data from MDN, we have a script to pull it down but their API only presents it as tables, not as JSON or anything else we'd need someone to convert it to JSON someone with good Python/Perl/Ruby/etc skills to convert from an HTML table to a normalized data table we've already established in JSON we have samples to scrape from already it's a multi pass thing: first you write something to take care of obvious stuff, then continue targeting the edge cases iteratively there will be some hand-management of the data

jensimmons: Should we write about a blurb of a job description for this?

shepazu: WE have in the past. that's how gelph Found out about it

jensimmons: I know of a bunch of people who would fit the description

ACTION: shepazu to write up a job description of the HTML --\> JSON of MDN compat tables and then jensimmons and others can tweet about it

gelph: Seems like an on-going need for tools assistance

shepazu: I'm feeling better about this than I was feeling 10 minutes ago I'll get to that action today