---
title: WPD:Content/Readiness Markers
---
<h1><span class="mw-headline" id="Readiness_Markers_.26_Editorial_Notes">Readiness Markers &amp; Editorial Notes</span></h1>
<p>Readiness markers display information about the quality of an article at a glance.  They are visible to anyone arriving at the site, so that it is clear when work is not complete and caution should be used.  The readiness states are also available to be searched, so that site editors can keep track of work to be done.
</p><p>Editorial notes are not displayed to people who are coming to WebPlatform Docs for information.  They are only shown in the editing forms, and provide an open-ended way for contributors to indicate what work still needs to be done.  In particular, they should explain what needs to be done before the page can be marked "ready to use".
</p><p><br />
</p>
<h2><span class="mw-headline" id="Readiness_States">Readiness States</span></h2>
<p>The official definitions for the readiness options are given on their <a href="/wiki/Property:State" title="Property:State"> property page</a>.  The following explanations describe the purpose of the different states more generally:
</p>
<h3><span class="mw-headline" id="Ready_to_Use">Ready to Use</span></h3>
<p>A document should be marked Ready to Use if a developer who is looking for reference material on this topic can randomly land on this page and get complete, accurate information. The information on a Ready to Use page is not outdated, and it's not incomplete in a way that would make the information confusing. Much of the documentation on webplatform.org will need to be continuously be revised and updated as standards and techniques change, so Ready to Use pages don't have to always be 100% perfect. They may need minor errors or quick updates.  Hopefully those kinds of edits are simply done as soon as the need for an edit is discovered. In that case, switching the readiness status of the page in a more complex workflow process isn't needed.
</p>
<h3><span class="mw-headline" id="Almost_Ready">Almost Ready</span></h3>
<p>A document should be marked Almost Ready if it's 80% ready, but still needs something that's clearly missing or incomplete.  Almost Ready might be used when the descriptions are good, but there are no examples. Or when the editing that humans can do is complete, but there's still something else that needs to be coded in the system to make the pages ready — such as connecting the compatibility tables. This could be used as a way to mark a group of pages for review if an initiative needs such a tool, as a kind of Q/A stage. Or this status might not be used at all; pages can go straight from In Progress to Ready to Use if the circumstances warrant it.
</p><p>This state was called Almost Done / Almost Complete in earlier discussions of the readiness states.
</p>
<h3><span class="mw-headline" id="In_Progress">In Progress</span></h3>
<p>A document should be marked In Progress if work on it has officially begun, but it's not close to being ready yet. This marker will tell developers who may stumble across the page — hey, don't trust this documentation yet: It's not a reliable source of information, it's a page that's being heavily rewritten. Any page that's more than 10%, but less than 80% done should be marked In Progress. It doesn't matter whether there is active work being done on it currently or not. 
</p>
<h3><span class="mw-headline" id="Not_Ready">Not Ready</span></h3>
<p>A document should be marked Not Ready when it's just an idea. This can be used when someone has created a page, with a URL and a title, maybe a "stub" summary, but not much else. It should also be used when content is imported from an outside source, but has not been looked at by WPD contributors or restructured for our system yet.
</p><p>This state was called Coming Later in earlier discussions of the readiness states, and may still be renamed.
</p>
<h3><span class="mw-headline" id="Out_of_Date">Out of Date</span></h3>
<p>A document should only be marked Out of Date if it was previously marked "Ready to Use" or "Almost Done", but is no longer accurate due to changes in the standards or implementations discussed.  Whenever possible, a document should be edited to update it instead of marking it out-of-date.
</p>
<h3><span class="mw-headline" id="Unreviewed">Unreviewed</span></h3>
<p>A document is unreviewed if it has not had a state value assigned.  This value should not be set manually.
</p>
<h2><span class="mw-headline" id="Statistics">Statistics</span></h2>
<p>Current numbers of articles with each status:
</p>
<ul><li>Ready to Use: (<a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:SearchByProperty&amp;property=State&amp;value=Ready+to+Use">1633 articles</a>)</li>
<li>Almost Ready: (<a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:SearchByProperty&amp;property=State&amp;value=Almost+Ready">351 articles</a>)</li>
<li>In Progress: (<a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:SearchByProperty&amp;property=State&amp;value=In+Progress">850 articles</a>)</li>
<li>Not Ready: (<a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:SearchByProperty&amp;property=State&amp;value=Not+Ready">1433 articles</a>)</li>
<li>Out of Date: (<a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:SearchByProperty&amp;property=State&amp;value=Out+of+Date">100 articles</a>)</li>
<li>Unreviewed: (<a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:SearchByProperty&amp;property=State&amp;value=Unreviewed">103 articles</a>)</li>
<li>Other values: (<a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:SearchByProperty&amp;property=Has+improper+value+for&amp;value=State">22 articles</a>)</li></ul>
<h2><span class="mw-headline" id="Implementation">Implementation</span></h2>
<p>The readiness marker system is now live on the main wiki.  CSS styling still to come.  The implementation depends on the following templates and Semantic MediaWiki properties:
</p>
<ul><li> <a href="/wiki/Property:State" title="Property:State">Property:State</a><br /></li></ul>
<p>The State property defines the readiness state property, and contains definitions of each value (slightly shorter versions of the ones from Jen's email) and links to search pages for each value.  For now, this is the page you get to when you click on the readiness-related link in the form or main article page.    In the future, that may be changed to link to this page.
</p>
<ul><li> <a href="/wiki/Property:State_Details" title="Property:State Details">Property:State_Details</a><br /></li></ul>
<p>The State Details property will contain any editorial notes related to the page and the reason it was given a certain state.  Nothing prints on the final "View" mode of the article, but by saving the information as a property they can be accessed by search functions (the above link will have a list of all articles with a value set).  Although the property is new, it reuses the "Editorial Notes" form field from the old flags template, which means that any custom editorial notes should be preserved (although it's a little messy, because most of them used their own templates which inject html code).
</p>
<ul><li> <a href="/wiki/Template:Flags_Form_Section" title="Template:Flags Form Section">Template:Flags_Form_Section</a><br /></li></ul>
<p>The old flags form section template has been reused, so that all pages that previously allowed you to set flags now allow you to set a readiness state.  The revised template has three elements: readiness state, state details/editorial notes, and checked out.  Edit any reference page to see what it looks like in action.
</p>
<ul><li>  <a href="/wiki/Template:Flags" title="Template:Flags">Template:Flags</a><br /></li></ul>
<p>Likewise, the old Flags template has been used to print the readiness markers.  Any pages which previously had the option to show flags under the title will instead show the readiness statement (if a value has been set).
</p>
<ul><li> <a href="/wiki/Property:Content_quality_flag" title="Property:Content quality flag">Property:Content_quality_flag</a><br /></li></ul>
<p>The flags property is still used for the automatically-set flags Needs Summary, Examples Needed, and Compatibility Incomplete.  The property page needs to be updated, as does <a href="/wiki/WPD:Flags" title="WPD:Flags">WPD:Flags</a> and its sub-pages.
</p>
<h2><span class="mw-headline" id="Design">Design</span></h2>
<p>The state value is printed to the page in the following format by the Flags template:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"><span class="sc2">&lt;<span class="kw2">div</span> <span class="kw3">class</span><span class="sy0">=</span><span class="st0">&quot;readiness-state Almost_Ready&quot;</span>&gt;</span> 
<span class="sc2">&lt;<span class="kw2">p</span>&gt;</span>This article is <span class="sc2">&lt;<span class="kw2">a</span> <span class="kw3">href</span><span class="sy0">=</span><span class="st0">&quot;/wiki/Property:State&quot;</span> <span class="kw3">title</span><span class="sy0">=</span><span class="st0">&quot;Property:State&quot;</span>&gt;</span>Almost Ready.<span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">a</span>&gt;</span>
<span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">p</span>&gt;</span>
<span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">div</span>&gt;</span></pre></div></div>
<p>The "readiness-state" and state-specific class will be used for the final CSS.  The state-specific classes are created from the property values by replacing spaces with "_", so they are: "Ready_to_Use", "Almost_Ready", "In_Progress", "Not_Ready", "Out_of_Date".  (The "Unreviewed" value currently never results in a div being added to the page.)
</p><p>You can find the latest discussion about (and examples of) the proposed design for the markers on the <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/">webplatform email list</a>.
</p>
<!-- 
NewPP limit report
CPU time usage: 0.076 seconds
Real time usage: 0.083 seconds
Preprocessor visited node count: 108/1000000
Preprocessor generated node count: 404/1000000
Post‐expand include size: 805/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 3/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:22193-0!*!0!!*!*!*!esi=1 and timestamp 20150731163641 and revision id 58141
 -->
