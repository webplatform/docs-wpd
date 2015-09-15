---
title: 1206 raw mtg notes
uri: 'WPD:Community/Meetings/General/2013/1206 raw mtg notes'

---
    eliezerb joined  ⇐ mstalfoort, chrismills and Garbee-Shop quit  ↔ paul_irish nipped out

    Hello, everyone!!

    Meeting in a few... http://docs.webplatform.org/wiki/WPD:Community/Meetings/General

    shepazu waves

    eliezerb I guess that I'm online

    phistuck joined (546f0265@gateway/web/freenode/ip.84.111.2.101)

     (phistuck) I am listening, too

    jensimmons joined (~jensimmon@drupal.org/user/140882/view)

     (phistuck) Hello!

     (phistuck) I am a boy. :)

     (jensimmons) "The conference is restricted at this time"?

     (jensimmons) I can't get into the conference call

     (shepazu) jensimmons, try again

     (jensimmons) in

     (jensimmons) thanks

     (phistuck) I am here, too

    jswisher joined (~jswisher@cpe-173-174-55-161.austin.res.rr.com)

     (phistuck) (It is pronounced like "feestook")

    eliot joined us on the phone

    phistuck - oooo! thanks!

     (jswisher) I am not able to join the call today, and I need to leave on the half hour

     (jswisher) But I'm here for now if you need me

    jswisher okay thanks!

    Agenda:

    * Jen Simmons has a mock up of the HTML elements pages

    * Max Polk has done the 3rd JS import

    * Eliezer Bernart is on templates

    * David Singer has proposed a WebVTT content project

    TOPIC : Jen Simmons has a mock up of the HTML elements pages

    jensimmons : this is the 2nd draft of how the html elements pages could display

    ... this was put together with real content

    (there's a bad echo, please mute if you're not talking)

    ... Eliot also gave feedback in email

    shepazu has feedback but wants others to join in first...

    eliot: wants to give a round of applause...

    (everyone claps)

    jensimmons: top section is short. a great introduction that draws from the specs might be good for newbies

    ... for those learning for the first time

    ... examples: like having more than one

    ... walking folks through

    ... official from the w3c, so it should be correct

    ... personal ideas should be left out

    ... also, some will come to learn, others will just come and grab something or as a reminder

    ... we don't want to have css examples, but in the case of nav , but without it, people won't want their output to look that way

    ... common use pattern is not just html

    ... system should be flexible to include css

    shepazu: specs are typically not suitable for the reader. only a limited amount that could be drawn from the specs

    dsinger joined (11c5200b@gateway/web/freenode/ip.17.197.32.11)

     (phistuck) (Rejoined, had issues)

    jensimmons: yes, we need to make it plain

    jensimmons: raw code, but also explanations, would prefer them to be live

    Garbee-Shop joined (~Garbee@192.34.161.117)

    ... not possible right now

    ... no local settings, reload resets page

    shepazu: part of the original mission, but...

    jensimmons: Max Polks suggested "Usage" instead of "Details"

    ... for me, it's more about real use, industry agreed upon suggestions

    ... if you're in the middle of coding, you just want to find out if and how to use something quickly

    ... attribute: should have an introductory paragraph explaining what an attribute is. boiler plate on every page

     (jensimmons) ARIA roles

    ... Details : could use a better word

    ... Max sent links to other sites, such as cheatsheets & another page.

    ... this section can be presented in more than one way. people who don't know what this means

    ... shouldn't feel alienated

    ... Browser compatibility table display should also be looked at

    shepazu: that's part of the compat. projects

    ... many discussions, still up for debate

     (phistuck) I think we should have all of the specifications

    jensimmons: specs are listed on mdn, what specs should be listed?

     (phistuck) Though the obsolete/deprecated/outdated ones should be hidden by default with a "More specifications..." link

    ... history: when was something introduced, how things changed, what exactly changes, becomes less important

    eliezerb will reconnect

    ... as it gets more history

    ... external links : should we do this is up for debate.

    ... we could decide an order...

    shepazu: 1st: examples at the top: thinks there will be a lot, so other content may be pushed down in an unpredictable way

    ... attribs should be above examples

    ... understand why examples are high, but some of the specific details & syntax should be up there as well

    ... even if it's a simple element

    ... idea: every attrib should have its own example as well

    ... if attrib, link to example, below

    ... ergo: lots of examples

    ... maybe they should be accordions?

    ... jensimmons also gave methodology about how to populate sections

    ... (style guide)

    ... content is really handcrafted. Not just anyone can create that kind of content.

    ... in the short term, allow content to be not conforming to the idea style in order to let community contribute content

    jensimmons: I could write a lot of it

     ⇐ jswisher quit (~jswisher@cpe-173-174-55-161.austin.res.rr.com) Quit: jswisher

    ... not all will be good. Rougher out of the gate. Structure may need to support crowdsourcing

    shepazu: most of the handcrafted can't be automated. tedious details can be automated.

    ... if the whole site had this kind of quality, great. We want to have uniformity among sections.

    ... e.g.: syntax section could provide best example to pull out (copy from)

    ... autocompletion for tools that use our syntax section

    dsinger is completely failing to get Colloquy to connect. weird. using web

    jensimmons: yes, other fields that won't be here, what would that be? 100 char string summary?

    ... we're not designing a page, we're designing a system

    shepazu: I think these are considerations.

    jensimmons: want more feedback

    shepazu: meeting next week?

    ... we can do a doodle poll

    jensimmons: and people can continue to email feedback

    jensimmons: javascript is next

    julee: need to prioritize jensimmons ' work

    ACTION ITEM: shepazu send out a doodle poll for next meeting on this

    ACTION ITEM: jensimmons to send out what she'll do with us, so we all can help prioritize

    jensimmons: drupal mock up is coming

    ... also to play with drupal

    Eliot: should be clear about our audience, fractured experience if we're not clear about our intent

    jensimmons: we could take some time to define target audiences

    shepazu: useful, could be part of discussion

    TOPIC: Max Polk has done the 3rd JS import

    julee: is there anyone who thinks Max shouldn't import now?

    shepazu: we must have template before the import, Max will need to change the syntax.

    Eliot: let's start from the current API templates

    TOPIC: David Singer has proposed a WebVTT content project

    dsinger: specs are incomprehensible, we need clear that central authority

    shepazu: 1. the syntax - webvtt uses a different type of parsing. What are the individual elements called?

     (phistuck) A cue

     (phistuck) Regions are coming soon

    dsigner: properties, cues, styles, 608-708 regions

     (phistuck) It seems

     (phistuck) A basic use syntax

     (phistuck) A formatting syntax

     (phistuck) And maybe region syntax

     (phistuck) Once it is in

    shepazu: we break things down into high-level syntax pages, and then a tutorial under our tutorial, and maybe even a conceptual.

    Eliot: we have the building blocks and a volunteer

    Carlos Aroyo is in the commun

    ... Jay Munro may also be able to help, if eliot can spare him

    ... Any time considerations? Laws changing?

    dsigner: there is material out there, so sooner is better, we're looking for WPD to have centralized content

    ... standardization questions, but really want to focus on the fact that we can have a11y now

    shepazu ; would love to host an example

     (dsinger) Silvia Pfieffer

    dsinger : ^ ^ she will know

     (dsinger) Silvia has lots of examples

    TOPIC: Eliezer Bernart is on templates

     ⇐ dsinger quit (11c5200b@gateway/web/freenode/ip.17.197.32.11) Quit: Page closed

    shepazu: technical solution is sound

    ... he knocked out what we needed to get to with flags

    eliezerb: before working with flags, we had decided the types of flags.

    ... a lot of flags didn't make sense. Eliot suggested we summarize to just 5

    ... each one was different, when we wanted to add them, the old flags are hidden.

    ... shepazu discovered.

    ... what will happen with the old flags? What should we do with them?

     (shepazu) s/shepazu /eliezerb /

    shepazu: new flags will supercede the old ones. we'll need to do a script to walk through and set flags accordingly.

    eliezerb: keeping both is silly

    julee: sent out a mapping

    shepazu: good enough

    ... but we need a script

    Eliot: start a culture of using the editorial notes.

    shepazu: who could write the script

    ACTION ITEM: shepazu to email frozenice to ask him to do a script

    ACTION ITEM: Eliezerb: can work on JavaScript templates with shepazu's help

    TOPIC: compatbiility tables delay

    shepazu: busy, need a php parser

    ... read thru tables from MDN and turn it into JSON

    ... will send details

    ACTION ITEM: shepazu to send email describing ask

    TOPIC: dreamhost isn't ready

    shepazu: dreamhost gave us a dedicated machine for now, recreating the environment there.

    .... duplicate site running on dreamhost.

    ACTION ITEM: shepazu will has for testers when we move over

    shepazu: iweb is also interested in being a host

    ... we went to them when we were having trouble with dreamhost

    julee: are they offering tech resources as well?

    shepazu: yes, but still talking about how relationship will work

    shepazu: thanks for all the great work this week!