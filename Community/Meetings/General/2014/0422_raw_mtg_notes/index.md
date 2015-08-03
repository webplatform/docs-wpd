---
title: WPD:Community/Meetings/General/2014/0422 raw mtg notes
---
<p><a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/WPD:Community/Meetings/General/2014/0415_raw_mtg_notes">Previous meeting notes</a>
</p>
<h2><span class="mw-headline" id="Presences">Presences</span></h2>
<ul><li> Renoir (scribe)</li>
<li> Doug</li>
<li> Eliot</li>
<li> Jen</li>
<li> Amelia</li>
<li> Elizer (on IRC only)</li>
<li> Frozenice (on IRC only)</li></ul>
<h2><span class="mw-headline" id="Agenda">Agenda</span></h2>
<ul><li> Compatibility Table Project</li>
<li> Flag templates</li>
<li> Web Platform Wednesday: SVG</li>
<li> Review of open action items</li>
<li> Amelia's introduction</li></ul>
<h2><span class="mw-headline" id="Compatibility_Table_project">Compatibility Table project</span></h2>
<p>Doug: Renoir made a scrip that imports content from MDN and converts it to objects.
</p><p>... we have problem to get a portion of the data
</p><p>... <a rel="nofollow" class="external text" href="https://github.com/webplatform/mdn-compat-importer/issues/3">Issue has been raised, and contacted MDN on (see here in our own project GitHub repo)</a>
</p><p>... we contacted MDN, they cannot help us
</p><p>... we have something working but still have missing data
</p><p>... ptressel is currently working on an Apache Nutch scraping project that we can pass our importer against.
</p><p>... it will prevent to overload servers, and guarantee us to have as much data as possible
</p><p>... effectively going around the limitation problem
</p><p>Doug: Renoir is working on SSO stuff.
</p><p>... more on this later
</p><p>... hopefully next week Renoir will switch workpile back on CompatTable
</p><p>... and have it deployed on the main wiki
</p><p>Doug: Is asking about ... with @@
</p><p>... to write a blog post related to CompaTables
</p><p>... [logistics]
</p><p>ACTION: Doug to sync with Eliot about a Blog post announcing Compatibility tables
</p><p>[Doug giving context to Amelia]
</p><p>Renoir pointing to Amelia a test example at <a rel="nofollow" class="external free" href="http://w3c-test.org/webstorage/storage_local_getitem.html">http://w3c-test.org/webstorage/storage_local_getitem.html</a>
</p><p>Based off of <a rel="nofollow" class="external free" href="https://github.com/w3c/web-platform-tests">https://github.com/w3c/web-platform-tests</a> ^
</p><p><br />
</p>
<h2><span class="mw-headline" id="TOPIC_Flag_and_templates">TOPIC Flag and templates</span></h2>
<p>[asking if eliezerb is there, confirming]
</p><p>[+eliezerb: Yes!]
</p><p>[we'll add it to the meeting]
</p><p>Doug: We've had ability to add templates
</p><p>... flags on templates
</p><p>... do we know enough; How do we script against SMW so we can trigger flags on or off.
</p><p>... does anybody else can help on that
</p><p><br />
[Doug will talk with eliezerb about what we can do, and what is missing]
</p><p>Jen: [asks about how to use, and is offering to help]
</p><p>Doug: We have a solution. But the solution is that we are to remove the old flags, and put the new flags in. But 
they will all be unchecked
</p><p>... this is where the script will be usefull. To read what was the old flags, and activate on the new flag model
</p><p>... using a script
</p><p>Eliot: I think that this summarizes where we ended up with flags <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2013Dec/0035.html">in the mailing list archive, in December 2013</a>
</p><p>[+eliezerb: We have another mail comming, under renoirb review]
</p><p>[Jen is suggesting that we manually adjust flags on each page. It'll be a good way to also have an inventory of 
what we have]
</p><p>Renoir: [Mentions to the conf call about the email that elizer sent Renoir]
</p><p>Jen: Suggesting to have a first pass
</p><p><br />
... instead of a Google Docs, to have a mediawiki managed list of the pages
</p><p>... will be more useful in the long run
</p><p>... essentially to have a list of all pages in some way by readyness order
</p><p>Eliot: suggests that we have a "flagger" badge (or something else more clever) 
</p><p>... for those participating in the manual work.
</p><p>... There are 5 states, last would be "not marked yet" so we can use it as a TODO
</p><p><br />
[confirming the concept of Flags and how to list it]
</p><p>[Amelia says that she's been reading SMW lately]
</p><p>Doug: Asking Eliot about the current flags
</p><p>Eliot: The list of flags <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2013Dec/0035.html">is available from the mailing list archive</a>
</p><p>... will be very nice to have such "TODO"
</p><p>[Doug confirms]
</p><p>Project idea:  Walk through ALL CSS content, with a list view based on the "new" flag system, listing by "not 
flagged at all", then while walking through, contributors will be able to flag appropriately.
</p><p><br />
eliot, can you confirm ^
</p><p>just to be sure it makes sense
</p><p>[renoir asks Eliot to validate]
</p><p>Eliot: What we'll have is a set of "readiness" flags: ready to use, almost ready, etc.
</p><p>Jen: Design wise it will be more useful than a set of flages.
</p><p>Doug: Asking how do we execute on it
</p><p>Eliot: ...and then, we can add details in a comment box about what specific deficiencies are there.
</p><p>... suggesting that we could leverage the "dropdown" concept
</p><p>... and since its not a checkbox, we can state a default state. That's where we can say "not flagged at all" ... 
as a TODO list.
</p><p>[Renoir summarizing the concepts to see agreements, all agreed]
</p><p>Jen: Wonders if we are actually using MW flags, or something that seems like it.
</p><p>AmeliaBR: could be an addition and not delete the old flags
</p><p>Doug: [Reminding about flags and the side effects]
</p><p>Jen: Strongly suggests to add the flags at the bottom (as metadata), maybe not render them, and stop using RED. 
Its metadata, not big warning.
</p><p>Doug: Confirming they should be at the bottom of both views, edit and view ... view.
</p><p>Jen: Asks that we can make sure we can list pages with same flags
</p><p>ACTION: To ensure that flag links leads to a page listing pages that has same flag on them
</p><p>+eliezerb: See [<a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/Special:SearchByProperty/Content_quality_flag/Incomplete">http://docs.webplatform.org/wiki/Special:SearchByProperty/Content_quality_flag/Incomplete</a> List 
of flags link]
</p><p>... See also Frozenice's special form to list pages based on flags <a rel="nofollow" class="external text" href="http://docs.webplatform.org/w/index.php?title=User:Frozenice/Customized_Lists_Test&amp;action=formedit">at "User:Frozenice/Customized_Lists_Test&amp;action=formedit", use as example</a>, or <a rel="nofollow" class="external text" href="http://docs.webplatform.org/w/index.php?title=User:Frozenice/Customized_Lists_Test&amp;action=edit">view the source</a>
</p><p>... or re-use the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/Template:Configurable_Query">"Template:Configurable_Query" template</a> as the content of a page with the query you want to see results.
</p><p>Doug: Suggesting to remove temporarily the flags (without deleting the data) and put the readyness
</p><p>... workflow. So later we can read the data from the former tags, remove the barrier of "red flags" for the 
short term, and later we'll script and re-use that data later on.
</p><p>... the idea is to remove the edition of them, just keep the data without displaying nor editing it
</p><p>... we'll query it later.
</p><p>... and focus on the readyness dropdown
</p><p>eliezerb, shepazu said he'd have a talk with you later.
</p><p>Eliot: Suggests shepazu to make an implementation proposal on the mailing list
</p><p>... Shepazu is asking Jen if she can.
</p><p>[Jen agrees]
</p><p>[Eliot: +1 to the efficacy of the new solution using readiness states
</p><p>Doug: We should have a way to query pages based on flags or other properties
</p><p>AmeliaBR: Example of flag search (this is linked from one of the help pages for beginners, shows all pages with 
"Needs Summary"): <a rel="nofollow" class="external text" href="http://docs.webplatform.org/w/index.php?title=Special%3AAsk&amp;q=%5B%5BContent_quality_flag%3A%3A~Needs+Summary%5D%5D%0D%0A++%5B%5BChecked_Out%3A%3Afalse%5D%5D&amp;po=&amp;eq=yes&amp;p%5Bformat%5D=broadtable&amp;sort_num=&amp;order_num=ASC&amp;p%5Blimit%5D=&amp;p%5Boffset%5D=&amp;p%5Blink%5D=all&amp;p%5Bsort%5D=&amp;p%5Bheaders%5D=show&amp;p%5Bmainlabel%5D=">Semantic MediaWiki Query Editor view</a>
</p><p>Renoir validated how to query, points out address and other know tools
</p><p>... <a rel="nofollow" class="external text" href="http://semantic-mediawiki.org/wiki/Ask_API">Documentation page for Semantic MediaWik query API</a>
</p><p>... you can see <a rel="nofollow" class="external text" href="http://webplatform.frozenice.de/pageinfo.html">frozenice's WPD stats info utility</a>
</p><p>... <a rel="nofollow" class="external text" href="http://webplatform.frozenice.de/pageinfo.html#css/properties/border-radius">page example "border radius"</a>
</p><p>... Or see for a property possible values, e.g. <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/Special:SearchByProperty?property=Content_quality_flag&amp;value=Examples%20Best%20Practices">Content_quality_flag</a>, and query them <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/Special:SearchByProperty?property=Content_quality_flag&amp;value=Examples%20Best%20Practices">from the Special:SearchByProperty view</a>
</p><p>Eliot:   Could do something like the W3C specs use. See this for the blue stripe: <a rel="nofollow" class="external text" href="http://www.w3.org/TR/html-polyglot/">in TR/html-polyglot, see the blue stripe</a>
</p><p>... Doug pulls foot from mouth
</p><p><br />
</p>
<h2><span class="mw-headline" id="Quick_status">Quick status</span></h2>
<p>Jen worked on: Editor guide,
</p><p>... proposed changes for links
</p><p>... working on editing pages. Consolidating. Going to keep working.
</p><p>... deleting pages ultimately. Please provide feedback
</p><p>... some pages were moved and others moved twice, so we need to check on navigation links.
</p><p>... says if somebody can go to docsprint in europoe
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:20125-0!*!*!!*!*!*!esi=1 and timestamp 20150731185147 and revision id 51866
 -->
