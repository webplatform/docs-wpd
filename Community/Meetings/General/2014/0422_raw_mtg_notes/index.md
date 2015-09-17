---
title: '0422 raw mtg notes'
uri: 'WPD:Community/Meetings/General/2014/0422 raw mtg notes'

---
[Previous meeting notes](http://docs.webplatform.org/wiki/WPD:Community/Meetings/General/2014/0415_raw_mtg_notes)

## Presences

-   Renoir (scribe)
-   Doug
-   Eliot
-   Jen
-   Amelia
-   Elizer (on IRC only)
-   Frozenice (on IRC only)

## Agenda

-   Compatibility Table Project
-   Flag templates
-   Web Platform Wednesday: SVG
-   Review of open action items
-   Amelia's introduction

## Compatibility Table project

Doug: Renoir made a scrip that imports content from MDN and converts it to objects.

... we have problem to get a portion of the data

... [Issue has been raised, and contacted MDN on (see here in our own project GitHub repo)](https://github.com/webplatform/mdn-compat-importer/issues/3)

... we contacted MDN, they cannot help us

... we have something working but still have missing data

... ptressel is currently working on an Apache Nutch scraping project that we can pass our importer against.

... it will prevent to overload servers, and guarantee us to have as much data as possible

... effectively going around the limitation problem

Doug: Renoir is working on SSO stuff.

... more on this later

... hopefully next week Renoir will switch workpile back on CompatTable

... and have it deployed on the main wiki

Doug: Is asking about ... with @@

... to write a blog post related to CompaTables

... [logistics]

ACTION: Doug to sync with Eliot about a Blog post announcing Compatibility tables

[Doug giving context to Amelia]

Renoir pointing to Amelia a test example at <http://w3c-test.org/webstorage/storage_local_getitem.html>

Based off of <https://github.com/w3c/web-platform-tests> \^

## TOPIC Flag and templates

[asking if eliezerb is there, confirming]

[+eliezerb: Yes!]

[we'll add it to the meeting]

Doug: We've had ability to add templates

... flags on templates

... do we know enough; How do we script against SMW so we can trigger flags on or off.

... does anybody else can help on that

 [Doug will talk with eliezerb about what we can do, and what is missing]

Jen: [asks about how to use, and is offering to help]

Doug: We have a solution. But the solution is that we are to remove the old flags, and put the new flags in. But they will all be unchecked

... this is where the script will be usefull. To read what was the old flags, and activate on the new flag model

... using a script

Eliot: I think that this summarizes where we ended up with flags [in the mailing list archive, in December 2013](http://lists.w3.org/Archives/Public/public-webplatform/2013Dec/0035.html)

[+eliezerb: We have another mail comming, under renoirb review]

[Jen is suggesting that we manually adjust flags on each page. It'll be a good way to also have an inventory of what we have]

Renoir: [Mentions to the conf call about the email that elizer sent Renoir]

Jen: Suggesting to have a first pass

 ... instead of a Google Docs, to have a mediawiki managed list of the pages

... will be more useful in the long run

... essentially to have a list of all pages in some way by readyness order

Eliot: suggests that we have a "flagger" badge (or something else more clever)

... for those participating in the manual work.

... There are 5 states, last would be "not marked yet" so we can use it as a TODO

 [confirming the concept of Flags and how to list it]

[Amelia says that she's been reading SMW lately]

Doug: Asking Eliot about the current flags

Eliot: The list of flags [is available from the mailing list archive](http://lists.w3.org/Archives/Public/public-webplatform/2013Dec/0035.html)

... will be very nice to have such "TODO"

[Doug confirms]

Project idea: Walk through ALL CSS content, with a list view based on the "new" flag system, listing by "not flagged at all", then while walking through, contributors will be able to flag appropriately.

 eliot, can you confirm \^

just to be sure it makes sense

[renoir asks Eliot to validate]

Eliot: What we'll have is a set of "readiness" flags: ready to use, almost ready, etc.

Jen: Design wise it will be more useful than a set of flages.

Doug: Asking how do we execute on it

Eliot: ...and then, we can add details in a comment box about what specific deficiencies are there.

... suggesting that we could leverage the "dropdown" concept

... and since its not a checkbox, we can state a default state. That's where we can say "not flagged at all" ... as a TODO list.

[Renoir summarizing the concepts to see agreements, all agreed]

Jen: Wonders if we are actually using MW flags, or something that seems like it.

AmeliaBR: could be an addition and not delete the old flags

Doug: [Reminding about flags and the side effects]

Jen: Strongly suggests to add the flags at the bottom (as metadata), maybe not render them, and stop using RED. Its metadata, not big warning.

Doug: Confirming they should be at the bottom of both views, edit and view ... view.

Jen: Asks that we can make sure we can list pages with same flags

ACTION: To ensure that flag links leads to a page listing pages that has same flag on them

+eliezerb: See [<http://docs.webplatform.org/wiki/Special:SearchByProperty/Content_quality_flag/Incomplete> List of flags link]

... See also Frozenice's special form to list pages based on flags [at "User:Frozenice/Customized\_Lists\_Test&action=formedit", use as example](http://docs.webplatform.org/w/index.php?title=User:Frozenice/Customized_Lists_Test&action=formedit), or [view the source](http://docs.webplatform.org/w/index.php?title=User:Frozenice/Customized_Lists_Test&action=edit)

... or re-use the ["Template:Configurable\_Query" template](http://docs.webplatform.org/wiki/Template:Configurable_Query) as the content of a page with the query you want to see results.

Doug: Suggesting to remove temporarily the flags (without deleting the data) and put the readyness

... workflow. So later we can read the data from the former tags, remove the barrier of "red flags" for the short term, and later we'll script and re-use that data later on.

... the idea is to remove the edition of them, just keep the data without displaying nor editing it

... we'll query it later.

... and focus on the readyness dropdown

eliezerb, shepazu said he'd have a talk with you later.

Eliot: Suggests shepazu to make an implementation proposal on the mailing list

... Shepazu is asking Jen if she can.

[Jen agrees]

[Eliot: +1 to the efficacy of the new solution using readiness states

Doug: We should have a way to query pages based on flags or other properties

AmeliaBR: Example of flag search (this is linked from one of the help pages for beginners, shows all pages with "Needs Summary"): [Semantic MediaWiki Query Editor view](http://docs.webplatform.org/w/index.php?title=Special%3AAsk&q=%5B%5BContent_quality_flag%3A%3A~Needs+Summary%5D%5D%0D%0A++%5B%5BChecked_Out%3A%3Afalse%5D%5D&po=&eq=yes&p%5Bformat%5D=broadtable&sort_num=&order_num=ASC&p%5Blimit%5D=&p%5Boffset%5D=&p%5Blink%5D=all&p%5Bsort%5D=&p%5Bheaders%5D=show&p%5Bmainlabel%5D=)

Renoir validated how to query, points out address and other know tools

... [Documentation page for Semantic MediaWik query API](http://semantic-mediawiki.org/wiki/Ask_API)

... you can see [frozenice's WPD stats info utility](http://webplatform.frozenice.de/pageinfo.html)

... [page example "border radius"](http://webplatform.frozenice.de/pageinfo.html#css/properties/border-radius)

... Or see for a property possible values, e.g. [Content\_quality\_flag](http://docs.webplatform.org/wiki/Special:SearchByProperty?property=Content_quality_flag&value=Examples%20Best%20Practices), and query them [from the Special:SearchByProperty view](http://docs.webplatform.org/wiki/Special:SearchByProperty?property=Content_quality_flag&value=Examples%20Best%20Practices)

Eliot: Could do something like the W3C specs use. See this for the blue stripe: [in TR/html-polyglot, see the blue stripe](http://www.w3.org/TR/html-polyglot/)

... Doug pulls foot from mouth

## Quick status

Jen worked on: Editor guide,

... proposed changes for links

... working on editing pages. Consolidating. Going to keep working.

... deleting pages ultimately. Please provide feedback

... some pages were moved and others moved twice, so we need to check on navigation links.

... says if somebody can go to docsprint in europoe
