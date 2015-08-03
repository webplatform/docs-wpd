---
title: WPD:Projects/QASprints/2014-june
---
<h1><span class="mw-headline" id="Quality_Assurance_.26_Readiness_Review_.28aka_QA_Sprint.29.2C_June_2014">Quality Assurance &amp; Readiness Review <br />(aka QA Sprint), <br />June 2014</span></h1>
<h2><span class="mw-headline" id="Overview">Overview</span></h2>
<p>As part of the progression of Webplatform.org to Beta stage (see the <a href="/wiki/WPD:Project_Status" title="WPD:Project Status"> Project Status</a> or <a href="/wiki/WPD:Projects/Beta_Requirements" title="WPD:Projects/Beta Requirements"> Beta requirements</a> pages), we need to assign <a href="/wiki/Property:State" title="Property:State"> readiness state properties</a> to every reference article.  Once individual articles have markers of their quality, we can remove the "Web Platform Docs is in alpha" warning from every page.
</p><p>As this will require a manual review of every page by experienced contributors, this is also a good time to do other quick and simple clean-up and quality assurance (QA) tasks that can only be done manually.
</p>
<h2><span class="mw-headline" id="UPDATE">UPDATE</span></h2>
<p>We're in the final stretch, and to make sure everything gets done, I've broken the remaining articles into the bite-size lists, available on a separate sign-up page:  
</p><p><a href="/wiki/WPD:Projects/QASprints/2014-june/Sign-up" title="WPD:Projects/QASprints/2014-june/Sign-up">  <span style="font-size:larger;font-weight:bold">Sign up here</span> </a>
</p><p><b>If you can work on a batch of articles, edit the sign-up page to put your name above the article list</b> (in the place that currently says "Your name here").  Please don't sign up until you're ready to sit down and start working!  That way, whoever has the time can get the work done.
</p><p>There are 80 batches, each with about 15-20 articles; I tried to split them at logical topic changes.  The more you can do the better, but even if you only do one batch that's a big help.   If you haven't already been working on the QA review, scroll down this page for information on what to do.
</p>
<h2><span class="mw-headline" id="Progress">Progress</span></h2>
<p>Current Article Count:
</p>
<ul><li> Needs Review:  103 articles</li>
<li> Readiness Assessed: 4367 articles</li></ul>
<p>(You can see the counts by readiness state, with links to all articles given that state, on the <a href="/wiki/Property:State" title="Property:State">Property:State</a> page.)
</p>
<h2><span class="mw-headline" id="Review_Tasks">Review Tasks</span></h2>
<p>The following is a list of tasks which have been suggested for this review.  
</p>
<ol><li> Assign a readiness state.  <a href="/wiki/WPD:Content/Readiness_Markers" title="WPD:Content/Readiness Markers"> More about readiness states</a></li>
<li> <del>Add any details about readiness/what is required to the editorial notes box.</del></li>
<li> For DOM method pages, assign index values to the parameter entries in order to get the correct syntax to display, as <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2014May/0026.html">described in this email post</a>.</li>
<li> For pages without a default form, ensure that they have the basic <code>{{Page Title}}</code> template to make them searchable by name and path.</li>
<li> <del>Confirm that the new compatibility tables are pulling in the correct data (Doug Schepers is going to give us more information about this once the import from MDN happens later this week).</del></li>
<li> For almost-done pages, check that the W3C status icon is correct.</li>
<li> <del> Ensure that every page has a summary section.</del></li></ol>
<h2><span class="mw-headline" id="Checklist">Checklist</span></h2>
<p>We have a lot of pages to get through, so this checklist has been designed to make the assessment quick and consistent.  Follow the decision tree until you reach a readiness state.  For some pages there are extra to-do lists, given below.
</p>
<h3><span class="mw-headline" id="Decision_Tree_for_all_pages">Decision Tree for all pages</span></h3>
<ol><li> Does the page have an editing form?  
<dl><dt>	NO</dt>
<dd>	
<ul><li>		follow basic templates to-do list.  </li>
<li>		Readiness = NOT READY.  </li></ul></dd></dl></li>
<li> <b>Is there a title at the top of the page?</b>
<dl><dt>	NO</dt>
<dd>	
<ul><li>		follow basic templates to-do list, using the "Edit Source" button to get to the template code.  </li>
<li>		continue with rest of checklist</li></ul></dd></dl></li>
<li> Is the page in a language other than English?
<dl><dt>	YES</dt>
<dd>  leave Readiness = UNREVIEWED</dd></dl></li>
<li> Is the page an obvious mistake or deletion candidate?
<dl><dt>	YES</dt>
<dd>  
<ul><li>		add an explanation to the Details field (the text box under the Readiness State selector in the form), if it isn't already there</li>
<li>		delete all content from the page if it is particularly objectionable (It would be preferable if you don't delete the page even if you have permission, as this will throw off the search listings used to assign articles)</li>
<li>		Readiness = NOT READY</li></ul></dd></dl></li>
<li> Is this a DOM method page?  
<dl><dt>	YES</dt>
<dd>	
<ul><li>		follow DOM method to-do list.</li>
<li>		continue with the checklist.</li></ul></dd></dl></li>
<li> Is there substantial content on the page?
<dl><dt> <i>For REFERENCE DOCS:</i> </dt>
<dd> Are there fewer than 3 of the following sections?
<ul><li>		Summary</li>
<li>		Values for info tables / syntax (if relevant)</li>
<li>		Written description / notes</li>
<li>		Examples</li>
<li>		Specifications </li>
<li>		Compatibility</li></ul></dd></dl>
<dl><dt>  <i>For TUTORIAL/CONCEPT pages:</i>  </dt>
<dd>   Is this obviously a stub page without much content?</dd>
<dt>	YES</dt>
<dd> Readiness = NOT READY</dd></dl></li>
<li> Is there a good summary?
<dl><dt>	NO</dt>
<dd> Readiness = IN PROGRESS</dd></dl></li>
<li> Is there obvious bias towards one software (IE, Firefox)?  
<dl><dt>	YES</dt>
<dd> Readiness = IN PROGRESS</dd></dl></li>
<li> Is there any major content quality problem (spelling/grammar/formatting)?
<dl><dt>	YES</dt>
<dd> Readiness = IN PROGRESS</dd></dl></li>
<li> Is there still a lot of work to do?
<dl><dt> <i>For REFERENCE DOCS:</i> </dt>
<dd>   How many of the sections from (3) are missing?</dd>
<dt>	2-3 sections missing</dt>
<dd> Readiness = IN PROGRESS</dd>
<dt>	1 section missing</dt>
<dd> Readiness = ALMOST READY</dd>
<dt>	All sections included</dt>
<dd> continue to next step</dd>
<dt>   <i>For TUTORIALS/CONCEPT pages:</i></dt>
<dd>   Are there signs that this is half-done?</dd>
<dt>	YES</dt>
<dd> Readiness = IN PROGRESS</dd>
<dt>	NO</dt>
<dd> continue to next step</dd></dl></li>
<li> Is there a circular W3C icon on the page?
<dl><dt>	YES</dt>
<dd> Follow the Standardization Status to-do list.</dd></dl></li>
<li> Are there any other problems you can see at a glance?  
<ul><li> Could there obviously be better/more detailed explanations? </li>
<li> Do you have any concerns about whether the content is accurate and up-to-date?</li></ul>
<dl><dt>	YES</dt>
<dd> Readiness = ALMOST READY</dd>
<dt>	NO, everything looks good</dt>
<dd> Readiness = READY TO USE</dd></dl></li></ol>
<h3><span class="mw-headline" id="DOM_Method_To-Do_List">DOM Method To-Do List</span></h3>
<ol><li> Does the syntax block have the words "see parameter list" insted of parameters?
<dl><dt>	YES</dt>
<dd> Open the editing form, and assign consecutive integer values (0,1,2,3...) to the "Argument Index" field for each parameter (in the order they are given in the page)</dd></dl></li>
<li> Continue with the readiness checklist</li></ol>
<h3><span class="mw-headline" id="Standardization_Status_To-Do_List">Standardization Status To-Do List</span></h3>
<ol><li> In the edit form, ensure that the value for Standardization Status matches the most recent value in the Specifications table.</li>
<li> Continue with the readiness checklist</li></ol>
<h3><span class="mw-headline" id="Basic_Templates_To-Do_List">Basic Templates To-Do List</span></h3>
<p>For pages that don't currently have a page template/default form (the "Edit" button opens a text box):
</p>
<ol><li> Make sure that the first line in the code is the <code>{{Page Title}}</code> template.</li>
<li> If the page currently has an h1 heading (surrounded by one '=' on either side), add it as a parameter to the template, like <code>{{Page Title | Text to use as title}}</code>; delete it from the main text and don't include the `=` in the template parameter value.</li>
<li> Manually add the line <code>|State=Not Ready</code> to the <code>{{Flags}}</code> template (or one of the other state values, although I'm fairly certain any pages that don't have default forms will be "Not Ready").  
<ul><li> If the flags template isn't there, add it as <code>{{Flags|State=Not Ready}}</code>.  </li>
<li> If there is a Flags template, be sure not to delete any existing parameters.</li></ul></li></ol>
<p>The bare minimum will look like
</p>
<pre>
   {{Page Title}}
   {{Flags|State=Not Ready}}
</pre>
<p>An example with a custom title and existing flag information will look like
</p>
<pre>
   {{Page Title|multiply()}}
   {{Flags
   |State=Not Ready
   |High-level issues=Needs Topics, Missing Relevant Sections, Data Not Semantic, Unreviewed Import
   |Content=Incomplete, Not Neutral, Compatibility Incomplete, Examples Best Practices, Cleanup
   }}
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="List_of_Volunteers">List of Volunteers</span></h2>
<p><b>Thanks for everyone who volunteered.</b>  If anyone else wants to help, get in touch with one of the people on the list and ask them if they need help on their assigned articles.
</p><p><del><b>Please add your name to this list if you're willing to contribute.</b>  The amount of work that can be done will depend on the number of people we have.  There are 4400+ articles to review, it would be nice to have 20+ people tackling them; more people means fewer articles each.  However, we are not trying to solicit brand new contributors for this, like in a DocSprint.  Participants must be familiar with the mediawiki structure and understand the content quality expectations.</del>
</p><p>If you indicate topic areas you are comfortable with, I'll try to make most of your assigned articles in that domain, but there will be some overlap and I'm assigning things alphabetically (by file path) since that's how search results are ordered.
</p>
<ol><li> shepazu  (SVG, etc)</li>
<li> renoirb</li>
<li> jensimmons (CSS &amp; HTML)</li>
<li> julee</li>
<li> eliot (Javascript)</li>
<li> AmeliaBR (SVG, whatever's needed)</li>
<li> eliezerb</li>
<li> garbee</li>
<li> frozenice (HTML &amp; DOM)</li>
<li> Michaela (CSS &amp; HTML)</li>
<li> Paulv</li>
<li> emerson (HTML/CSS/DOM)</li>
<li> brianjhong (HTML &amp; CSS)</li>
<li> Rob^_^ (any)</li>
<li> Hiroki</li>
<li> Roberto</li>
<li> caraya (late addition, may be able to help out with other people's article blocks)</li></ol>
<h2><span class="mw-headline" id="Article_Blocks">Article Blocks</span></h2>
<p><ins>  See the update above for information about the new article blocks, or go to the <a href="/wiki/WPD:Projects/QASprints/2014-june/Sign-up" title="WPD:Projects/QASprints/2014-june/Sign-up">sign-up page</a> to claim your block.</ins>
</p><p>The following articles have been assigned to each volunteer by breaking the alphabetical search results into blocks of 275 articles each:
</p>
<dl><dt> renoirb
<ul><li> <a href="/w/index.php?title=WPD:Projects/QASprints/2014-june/WPD:Editors_Guide/step_2_communicate_with_the_online_community/ko&amp;action=edit&amp;redlink=1" class="new" title="WPD:Projects/QASprints/2014-june/WPD:Editors Guide/step 2 communicate with the online community/ko (page does not exist)">/WPD:Editors Guide/step 2 communicate with the online community/ko</a> to <a href="/wiki/apis/filesystem/Entry/isDirectory" title="apis/filesystem/Entry/isDirectory">apis/filesystem/Entry/isDirectory</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=0&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 234</li></ul></dt></dl>
<dl><dt> garbee
<ul><li> <a href="/wiki/apis/filesystem/Entry/isFile" title="apis/filesystem/Entry/isFile">apis/filesystem/Entry/isFile</a> to <a href="/wiki/apis/navigation_timing/PerformanceTiming/domainLookupStart" title="apis/navigation timing/PerformanceTiming/domainLookupStart">apis/navigation timing/PerformanceTiming/domainLookupStart</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=275&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 288</li></ul></dt></dl>
<dl><dt> eliot <ins>and Dave Gash</ins>
<ul><li> <a href="/wiki/apis/navigation_timing/PerformanceTiming/fetchStart" title="apis/navigation timing/PerformanceTiming/fetchStart">apis/navigation timing/PerformanceTiming/fetchStart</a> to <a href="/wiki/apis/webrtc/RTCPeerConnection/icechange" title="apis/webrtc/RTCPeerConnection/icechange">apis/webrtc/RTCPeerConnection/icechange</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=550&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 328</li></ul></dt></dl>
<dl><dt> Paulv
<ul><li> <a href="/wiki/apis/webrtc/RTCPeerConnection/identityresult" title="apis/webrtc/RTCPeerConnection/identityresult">apis/webrtc/RTCPeerConnection/identityresult</a> to <a href="/wiki/concepts/ux/user_experience_design" title="concepts/ux/user experience design">concepts/ux/user experience design</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=825&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 263</li></ul></dt></dl>
<dl><dt> brianjhong
<ul><li> <a href="/wiki/concepts/ux/what_does_a_good_web_page_need" title="concepts/ux/what does a good web page need">concepts/ux/what does a good web page need</a> to <a href="/wiki/css/functions/translateY()" title="css/functions/translateY()">css/functions/translateY()</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=1100&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 268</li></ul></dt></dl>
<dl><dt> Michaela
<ul><li> <a href="/wiki/css/functions/translateZ()" title="css/functions/translateZ()">css/functions/translateZ()</a> to <a href="/wiki/css/properties/min-height" title="css/properties/min-height">css/properties/min-height</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=1375&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 278</li></ul></dt></dl>
<dl><dt> jensimmons
<ul><li> <a href="/wiki/css/properties/min-width" title="css/properties/min-width">css/properties/min-width</a> to <a href="/wiki/dom/Document/close" title="dom/Document/close">dom/Document/close</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=1650&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 257</li></ul></dt></dl>
<dl><dt> emerson
<ul><li> <a href="/wiki/dom/Document/cookie" title="dom/Document/cookie">dom/Document/cookie</a> to <a href="/wiki/dom/HTMLElement/clientLeft" title="dom/HTMLElement/clientLeft">dom/HTMLElement/clientLeft</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=1925&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 272</li></ul></dt></dl>
<dl><dt> <del>frozenice</del> <del><i>needs a volunteer</i></del> AmeliaBR 
<ul><li> <a href="/wiki/dom/HTMLElement/clientTop" title="dom/HTMLElement/clientTop">dom/HTMLElement/clientTop</a> to <a href="/wiki/dom/MouseEvent/layerX" title="dom/MouseEvent/layerX">dom/MouseEvent/layerX</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=2200&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 269</li></ul></dt></dl>
<dl><dt> Rob^_^
<ul><li> <a href="/wiki/dom/MouseEvent/layerY" title="dom/MouseEvent/layerY">dom/MouseEvent/layerY</a> to <a href="/wiki/dom/constants/DOM_exception_error_codes" title="dom/constants/DOM exception error codes">dom/constants/DOM exception error codes</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=2475&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 268</li></ul></dt></dl>
<dl><dt> julee
<ul><li> <a href="/wiki/dom/constants/HTTP_response_headers" title="dom/constants/HTTP response headers">dom/constants/HTTP response headers</a> to <a href="/wiki/html/attributes/valueType" title="html/attributes/valueType">html/attributes/valueType</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=2751&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 257</li></ul></dt></dl>
<dl><dt> Hiroki
<ul><li> <a href="/wiki/html/attributes/vcard_name" title="html/attributes/vcard name">html/attributes/vcard name</a> to <a href="/wiki/javascript/Date/constructor" title="javascript/Date/constructor">javascript/Date/constructor</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=3025&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 283</li></ul></dt></dl>
<dl><dt> Roberto
<ul><li> <a href="/wiki/javascript/Date/getDate" title="javascript/Date/getDate">javascript/Date/getDate</a> to <a href="/wiki/javascript/operators/logical_and" title="javascript/operators/logical and">javascript/operators/logical and</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=3300&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 287</li></ul></dt></dl>
<dl><dt> Eliezerb
<ul><li> <a href="/wiki/javascript/operators/logical_not" title="javascript/operators/logical not">javascript/operators/logical not</a> to <a href="/wiki/svg/methods/inverse" title="svg/methods/inverse">svg/methods/inverse</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=3575&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 263</li></ul></dt></dl>
<dl><dt> AmeliaBR
<ul><li> <a href="/wiki/svg/methods/item" title="svg/methods/item">svg/methods/item</a> to <a href="/wiki/svg/properties/type_(SVGTransform)" title="svg/properties/type (SVGTransform)">svg/properties/type (SVGTransform)</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=3850&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 275</li></ul></dt></dl>
<dl><dt> shepazu
<ul><li> <a href="/wiki/svg/properties/unitType" title="svg/properties/unitType">svg/properties/unitType</a> to <a href="/wiki/tutorials/workers_basics" title="tutorials/workers basics">tutorials/workers basics</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=4125&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 255</li></ul></dt></dl>
<dl><dt> caraya
<ul><li> <a href="/wiki/tutorials/working_with_objects_in_JavaScript" title="tutorials/working with objects in JavaScript">tutorials/working with objects in JavaScript</a> to <a href="/wiki/xslt" title="xslt">xslt</a></li>
<li> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;q=%5B%5BState%3A%3A%2B%5D%5D&amp;offset=4400&amp;limit=275&amp;po=%3FState+%0A%3FState+Details">search page</a></li>
<li> # completed: 11</li></ul></dt></dl>
<p><br />
</p>
<h2><span class="mw-headline" id="Plan_of_Attack">Plan of Attack</span></h2>
<p>If you need help, <a href="/wiki/WPD:Community#Chat_with_us_on_IRC" title="WPD:Community"> ask on IRC </a>.  If you can't complete your assigned tasks, send a note to the email list clearly indicating what range of articles still needs to be done, so that other people can take over.
</p>
<h2><span class="mw-headline" id="Timeline">Timeline</span></h2>
<ul><li> <del>Comments and volunteers ASAP</del></li>
<li> Articles to be assigned Thursday June 12, 2014</li>
<li> Work completed <del>by July 1</del><ins> as soon as possible</ins></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.203 seconds
Real time usage: 1.236 seconds
Preprocessor visited node count: 303/1000000
Preprocessor generated node count: 1210/1000000
Post‐expand include size: 3265/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 3/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:22818-0!*!0!!*!*!*!esi=1 and timestamp 20150731111112 and revision id 66402
 -->
