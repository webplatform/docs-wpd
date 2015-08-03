---
title: WPD:Projects/api docs
---
<h1><span class="mw-headline" id="API_documentation_proposal">API documentation proposal</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>Some of the most immediately useful technical content that WPD can provide is for the new JavaScript APIs recently developed (or currently being developed) for web applications. These APIs provide new functionality that make web applications as robust and high-performing as desktop or native apps. By focusing on this area of technical content, we can establish WPD as the leading provider of reference information for modern web development.
</p><p>The goal for this project is to bring the API documentation up to date and to make WPD the most current source for this documentation.
</p><p>This proposal outlines a strategy for building out the API documentation, considering the following:
</p>
<ul><li> The current state of the "apis" namespace and extant content</li>
<li> External content that could be imported to WPD</li>
<li> New content that will help developers use the latest features of modern browsers</li>
<li> Creating, updating, and importing content</li>
<li> Template and forms changes that need to be implemented</li>
<li> Priorities and project management</li>
<li> Additional documents</li></ul>
<h2><span class="mw-headline" id="Current_state_of_the_WPD_API_documentation">Current state of the WPD API documentation</span></h2>
<p>With the launch of WPD in October 2012, we received a generous donation of API documentation from Microsoft; it included some 12 APIs: appcache, audio-video (media), canvas, file, geolocation, indexeddb, timing, web-messaging, web-storage, websocket, workers, and xhr. A review of this content revealled that it needed to be reorganized and ammended extensively. While this work began, some new API documentation was developed (mostly to prove the process for creating API documentation). The findings of these efforts are summarized in <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a>.
</p><p>The following table summarizes the current state of the extant API documentation on WPD. Note that all of the extant documentation will require changes associated with new templates and forms as discussed in <a href="#Templates_and_forms">Templates and forms</a>, below. Another (messy) representation of this content may be found on the <a href="/wiki/apis" title="apis">apis</a> page.
</p><p>Where the current state is described as "Content complete" the API has been described with all of the pertinent aspects of the current standard specification for that API. It is organized as the API's component model, with objects, properties (attributes), methods, and events delineated accordingly. Additionally, the following checks apply:
</p>
<ul><li> The API_Listing page has instructions for (or a link to the page with the key method or other instructions on) how to use the API.</li>
<li> The usage of the "key" method is documented and includes example code.</li>
<li> All objects, properties, methods, and events have pages in the appropriate hierarchy.</li>
<li> All pages have a summary description.</li>
<li> All relevant information from the spec is included in the documentation.</li>
<li> A link to the specification is included.</li>
<li> All pages are marked "Needs review".</li>
<li> All pages contain compatibility information if available, or are marked "Compatibility incomplete" if not.</li>
<li> All pages have topic flags of "API" and API type, e.g., "Web Audio".</li></ul>
<p>The API document may or may not include code examples, and it may or may not have been reviewed; see <a href="/wiki/WPD:Projects/api_docs#On-going_work" title="WPD:Projects/api docs">On-going work</a>.
</p>
<table class="sortable">
<tr>
<th> Priority
</th>
<th> API Name
</th>
<th> Handler
</th>
<th> Current State
</th></tr>
<tr>
<td> 1
</td>
<td> <a href="/wiki/apis/appcache" title="apis/appcache">appcache</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 2
</td>
<td> <a href="/wiki/apis/audio-video" title="apis/audio-video">audio-video</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 3
</td>
<td> <a href="/wiki/apis/canvas" title="apis/canvas">canvas</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 4
</td>
<td> <a href="/wiki/apis/css-regions" title="apis/css-regions">css-regions</a>
</td>
<td> <a href="/wiki/User:Sierra" title="User:Sierra">Mike Sierra</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 5
</td>
<td> <a href="/wiki/apis/file" title="apis/file">file</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 6
</td>
<td> <a href="/wiki/apis/filesystem" title="apis/filesystem">filesystem</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 7
</td>
<td> <a href="/wiki/apis/geolocation" title="apis/geolocation">geolocation</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 8
</td>
<td> <a href="/wiki/apis/indexeddb" title="apis/indexeddb">indexeddb</a>
</td>
<td> <a href="/wiki/User:Lleonard" title="User:Lleonard">Lance Leonard</a>
</td>
<td> In progress
</td></tr>
<tr>
<td> 9
</td>
<td> <a href="/wiki/apis/navigation_timing" title="apis/navigation timing">navigation timing</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 10
</td>
<td> <a href="/wiki/apis/user_timing" title="apis/user timing">user timing</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 11
</td>
<td> <a href="/wiki/apis/resource_timing" title="apis/resource timing">resource timing</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 12
</td>
<td> <a href="/wiki/apis/webaudio" title="apis/webaudio">webaudio</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 13
</td>
<td> <a href="/wiki/apis/web-messaging" title="apis/web-messaging">web-messaging</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 14
</td>
<td> <a href="/wiki/apis/webrtc" title="apis/webrtc">webrtc</a>
</td>
<td> <a href="/wiki/User:Scottrowe" title="User:Scottrowe">Scott Rowe</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 15
</td>
<td> <a href="/wiki/apis/websocket" title="apis/websocket">websocket</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 16
</td>
<td> <a href="/wiki/apis/web-storage" title="apis/web-storage">web-storage</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 17
</td>
<td> <a href="/wiki/apis/workers" title="apis/workers">workers</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 18
</td>
<td> <a href="/wiki/apis/xhr" title="apis/xhr">xhr</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Mostly complete, needs to include CORS
</td></tr>
<tr>
<td> 19
</td>
<td> <a href="/wiki/apis/quota_management" title="apis/quota management">quota management</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 20
</td>
<td> <a href="/wiki/apis/gamepad" title="apis/gamepad">gamepad</a>
</td>
<td> <a href="/wiki/User:Dgash" title="User:Dgash">Dave Gash</a>
</td>
<td> Content complete
</td></tr>
<tr>
<td> 21
</td>
<td> <a href="/wiki/apis/canvas" title="apis/canvas">canvas</a> WebGL
</td>
<td> <a href="/wiki/User:Scottrowe" title="User:Scottrowe">Scott Rowe</a>
</td>
<td> Not started (<a rel="nofollow" class="external text" href="https://www.khronos.org/registry/webgl/specs/1.0/WebGL">spec</a>)
</td></tr></table>
<h2><span class="mw-headline" id="On-going_work">On-going work</span></h2>
<p>Although the initial layout and development of these documents is complete, a great deal of work remains in developing code examples and reviewing the content. The following tables list the pages that need these pieces in order for the documentation to attain stardom. The lists are the results of queries for content with <a href="/wiki/WPD:Editors_Guide/step_4_review_existing_content#How_to_add_a_flag" title="WPD:Editors Guide/step 4 review existing content">flags</a> that identify needed improvements; specifically, "Examples Needed" and "Needs Review." 
</p><p><br />
</p>
<h3><span class="mw-headline" id="Examples_development">Examples development</span></h3>
<p>(375 results)
</p><p>These pages need examples to thoroughly explain the documented API artifacts and their usage. When you've completed a page's example, please remove the "Needs Examples" flag.<br /><br />
The following criteria are applied:
</p>
<ul><li> Topics: API</li></ul>
<ul><li> Content quality flags: Examples Needed</li></ul>
<table class="sortable wikitable smwtable" width="100%">
<tr><th class="Page">Page</th>
<th class="Summary">Summary</th></tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/MediaStream/ended" title="apis/MediaStream/ended">apis/MediaStream/ended</a></td>
	<td class="Summary">All tracks of the MediaStream object have ended; the MediaStream is said to be finished.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/appcache/ApplicationCache/abort" title="apis/appcache/ApplicationCache/abort">apis/appcache/ApplicationCache/abort</a></td>
	<td class="Summary">Cancels the application cache download process. This method is intended to be used by Web applications showing their own caching progress UI, in case the user wants to stop the update (e.g., because bandwidth is limited).</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/appcache/ApplicationCache/oncached" title="apis/appcache/ApplicationCache/oncached">apis/appcache/ApplicationCache/oncached</a></td>
	<td class="Summary">The resources listed in the manifest have been downloaded, and the application is now cached.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/appcache/ApplicationCache/onchecking" title="apis/appcache/ApplicationCache/onchecking">apis/appcache/ApplicationCache/onchecking</a></td>
	<td class="Summary">The user agent is checking for an update, or attempting to download the manifest for the first time. This is always the first event in the sequence.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/appcache/ApplicationCache/ondownloading" title="apis/appcache/ApplicationCache/ondownloading">apis/appcache/ApplicationCache/ondownloading</a></td>
	<td class="Summary">The user agent has found an update and is fetching it, or is downloading the resources listed by the manifest for the first time.</td>
</tr>	<tr class="smwfooter"><td class="sortbottom" colspan="2"> <a href="/wiki/Special:Ask/-5B-5BCategory:API-5D-5D-0A-20-20-0A-20-20-5B-5BContent_quality_flag::%7EExamples-20Needed-5D-5D-0A-20-20-5B-5BChecked_Out::false-5D-5D/-3F%3DPage-23/-3FSummary/format%3Dbroadtable/limit%3D5/headers%3Dplain/mainlabel%3DPage/searchlabel%3D-27-27%27More-20results-27-27%27/default%3DNothing-20found!/offset%3D5" title="Special:Ask/-5B-5BCategory:API-5D-5D-0A-20-20-0A-20-20-5B-5BContent quality flag::~Examples-20Needed-5D-5D-0A-20-20-5B-5BChecked Out::false-5D-5D/-3F=Page-23/-3FSummary/format=broadtable/limit=5/headers=plain/mainlabel=Page/searchlabel=-27-27'More-20results-27-27'/default=Nothing-20found!/offset=5"><b>More results</b></a></td></tr>
</table>
<p><br />
</p>
<h3><span class="mw-headline" id="Review_content">Review content</span></h3>
<p>(0 results)
</p><p>These pages need to be reviewed by a community member familiar with the API and its usage in JavaScript. Where you find errors, please correct them; when you're finished, please remove the "Needs Review" flag.<br /><br />
The following criteria are applied:
</p>
<ul><li> Topics: API</li>
<li> High-level issues: Needs Review</li></ul>
<p>Nothing found!
</p><p><br />
</p>
<h2><span class="mw-headline" id="DOM_content">DOM content</span></h2>
<p>Content identified here was originally considered part of the API project, but these APIs are actually DOM APIs, and should be considered in the scope of the DOM project (yet to be started).
</p>
<table class="sortable">
<tr>
<th> Priority
</th>
<th> API Name
</th>
<th> Source
</th>
<th> Description
</th></tr>
<tr>
<td> DOM
</td>
<td> <a rel="nofollow" class="external text" href="https://developer.mozilla.org/en-US/docs/API/Pointer_Lock_API">Pointer Lock API</a>
</td>
<td> MDN
</td>
<td> Provides input methods based on the movement of the mouse over time.
</td></tr>
<tr>
<td> DOM
</td>
<td> <a rel="nofollow" class="external text" href="https://developer.mozilla.org/en-US/docs/DOM/window.navigator.battery">Battery</a>
</td>
<td> MDN
</td>
<td> Battery status.
</td></tr>
<tr>
<td> DOM
</td>
<td> <a rel="nofollow" class="external text" href="https://developer.mozilla.org/en-US/docs/DOM/MutationObserver">MutationObserver</a>
</td>
<td> MDN
</td>
<td> Observes changes to the DOM.
</td></tr>
<tr>
<td> DOM
</td>
<td> <a rel="nofollow" class="external text" href="https://developer.mozilla.org/en-US/docs/DOM/Using_the_Page_Visibility_API">Page Visibility</a>
</td>
<td> MDN
</td>
<td> Tells the application if a page is in focus.
</td></tr>
<tr>
<td> DOM
</td>
<td> <a rel="nofollow" class="external text" href="https://developer.mozilla.org/en-US/docs/Using_fullscreen_mode">Fullscreen</a>
</td>
<td> MDN
</td>
<td> Gives elements access to fullscreen presentation.
</td></tr>
<tr>
<td> DOM
</td>
<td> <a rel="nofollow" class="external text" href="https://developer.mozilla.org/en-US/docs/Detecting_device_orientation">Device Orientation</a>
</td>
<td> MDN
</td>
<td> Events that signal the device's orientation.
</td></tr>
<tr>
<td> DOM
</td>
<td> <a rel="nofollow" class="external text" href="https://dvcs.w3.org/hg/webcomponents/raw-file/tip/spec/shadow/index.html">Shadow DOM</a>
</td>
<td> Dimitri's Blog
</td>
<td> Tip of the Web Components iceberg; Scott is on the hook for this one.
</td></tr></table>
<h2><span class="mw-headline" id="Creating.2C_updating.2C_and_importing_content">Creating, updating, and importing content</span></h2>
<p>Along with importing content from other sources, it is crucial that when you are working with existing content you check that content against the source specification. The document, <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a> has more information about editing API pages. 
</p>
<h2><span class="mw-headline" id="Templates_and_forms">Templates and forms</span></h2>
<p>Several issues with the current design and implementation of the templates and forms for use with the API documentation are noted in the "TODO" sections of the page, <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a>. The issues are summarized as follows:
</p>
<ul><li> The text fields in the page creation forms on the <a href="/wiki/WPD:New_Page" title="WPD:New Page">WPD:New_Page</a> page need to be wider to accomodate longer namespace names. <a rel="nofollow" class="external text" href="https://www.w3.org/Bugs/Public/show_bug.cgi?id=20625">Bug 20625</a></li>
<li> We need a better way to specify non-primitive (or uncommon) return types. [<a rel="nofollow" class="external text" href="https://www.w3.org/Bugs/Public/show_bug.cgi?id=20626">Bug 20626</a>]</li>
<li> Exceptions need to have forms and templates designed for them so that they may be reused between object methods. <a rel="nofollow" class="external text" href="https://www.w3.org/Bugs/Public/show_bug.cgi?id=20627">Bug 20627</a></li>
<li> Constants (or enumerations) used as property and method values need to have forms and templates designed for them so that they may be reused between object properties and methods. <a rel="nofollow" class="external text" href="https://www.w3.org/Bugs/Public/show_bug.cgi?id=20628">Bug 20628</a></li>
<li> For the Syntax section in properties and methods, it is not clear that the way the form enforces the syntax works in all cases. It may be overly specific. We need a tiger team to look at this more carefully to determine if there is an issue.</li>
<li> In the Event template it is not clear how the Overview Table gets populated. Looks like the Event template has not been completed. <a rel="nofollow" class="external text" href="https://www.w3.org/Bugs/Public/show_bug.cgi?id=20629">Bug 20629</a></li></ul>
<h2><span class="mw-headline" id="Additional_documents">Additional documents</span></h2>
<p>The methodology for creating API pages is described in <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a>.
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:7104-0!*!0!!*!*!*!esi=1 and timestamp 20150731183502 and revision id 29975
 -->
