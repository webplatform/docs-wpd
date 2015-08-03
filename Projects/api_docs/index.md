---
title: WPD:Projects/api docs
---
<h1><span class="mw-headline" id="API_documentation_proposal">API documentation proposal</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></span></h2>
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

<h2><span class="mw-headline" id="Current_state_of_the_WPD_API_documentation">Current state of the WPD API documentation</span></span></h2>
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
<table class="sortable jquery-tablesorter">
<thead><tr>
<th class="headerSort" tabindex="0" role="columnheader button" title="Sort ascending"> Priority
</th>
<th class="headerSort" tabindex="0" role="columnheader button" title="Sort ascending"> API Name
</th>
<th class="headerSort" tabindex="0" role="columnheader button" title="Sort ascending"> Handler
</th>
<th class="headerSort" tabindex="0" role="columnheader button" title="Sort ascending"> Current State
</th></tr></thead><tbody>
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
</td></tr></tbody><tfoot></tfoot></table>

<h2><span class="mw-headline" id="On-going_work">On-going work</span></h2>
<p>Although the initial layout and development of these documents is complete, a great deal of work remains in developing code examples and reviewing the content. The following tables list the pages that need these pieces in order for the documentation to attain stardom. The lists are the results of queries for content with <a href="/wiki/WPD:Editors_Guide/step_4_review_existing_content#How_to_add_a_flag" title="WPD:Editors Guide/step 4 review existing content">flags</a> that identify needed improvements; specifically, "Examples Needed" and "Needs Review."
</p><p><br>
</p>
<h3><span class="mw-headline" id="Examples_development">Examples development</span></h3>
<p>(375 results)
</p><p>These pages need examples to thoroughly explain the documented API artifacts and their usage. When you've completed a page's example, please remove the "Needs Examples" flag.<br><br>
The following criteria are applied:
</p>
<ul><li> Topics: API</li></ul>
<ul><li> Content quality flags: Examples Needed</li></ul>
<table class="sortable wikitable smwtable jquery-tablesorter" width="100%">
<thead><tr><th class="Page headerSort" tabindex="0" role="columnheader button" title="Sort ascending">Page</th>
<th class="Summary headerSort" tabindex="0" role="columnheader button" title="Sort ascending">Summary</th></tr></thead><tbody>
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
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/appcache/ApplicationCache/onerror" title="apis/appcache/ApplicationCache/onerror">apis/appcache/ApplicationCache/onerror</a></td>
	<td class="Summary">Indicates an error has occurred.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/audio-video/track" title="apis/audio-video/track">apis/audio-video/track</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/audio-video/video" title="apis/audio-video/video">apis/audio-video/video</a></td>
	<td class="Summary">HTML Video element allows creator of a HTML document or view of a Web Application to embed a video for display when a user visits the view or opens HTML document in a web browser.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/charging" title="apis/battery status/BatteryManager/charging">apis/battery status/BatteryManager/charging</a></td>
	<td class="Summary">Represents if the system's battery is charging.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/chargingTime" title="apis/battery status/BatteryManager/chargingTime">apis/battery status/BatteryManager/chargingTime</a></td>
	<td class="Summary">Represents the time remaining in seconds until the system's battery is fully charged.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/chargingchange" title="apis/battery status/BatteryManager/chargingchange">apis/battery status/BatteryManager/chargingchange</a></td>
	<td class="Summary">Fired when the battery charging state is updated.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/chargingtimechange" title="apis/battery status/BatteryManager/chargingtimechange">apis/battery status/BatteryManager/chargingtimechange</a></td>
	<td class="Summary">Fired when the battery charging time is updated.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/dischargingTime" title="apis/battery status/BatteryManager/dischargingTime">apis/battery status/BatteryManager/dischargingTime</a></td>
	<td class="Summary">Represents the time remaining in seconds until the system's battery is completely discharged and the system is about to be suspended.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/dischargingtimechange" title="apis/battery status/BatteryManager/dischargingtimechange">apis/battery status/BatteryManager/dischargingtimechange</a></td>
	<td class="Summary">Fired when the battery discharging time is updated.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/level" title="apis/battery status/BatteryManager/level">apis/battery status/BatteryManager/level</a></td>
	<td class="Summary">Represents the current battery level scaled from 0 to 1.0.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/levelchange" title="apis/battery status/BatteryManager/levelchange">apis/battery status/BatteryManager/levelchange</a></td>
	<td class="Summary">Fired when the battery level is updated.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/onchargingchange" title="apis/battery status/BatteryManager/onchargingchange">apis/battery status/BatteryManager/onchargingchange</a></td>
	<td class="Summary">Handles the chargingchange event.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/onchargingtimechange" title="apis/battery status/BatteryManager/onchargingtimechange">apis/battery status/BatteryManager/onchargingtimechange</a></td>
	<td class="Summary">Handles the chargingtimechange event.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/ondischargingtimechange" title="apis/battery status/BatteryManager/ondischargingtimechange">apis/battery status/BatteryManager/ondischargingtimechange</a></td>
	<td class="Summary">Handles the dischargingtimechange event.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/battery_status/BatteryManager/onlevelchange" title="apis/battery status/BatteryManager/onlevelchange">apis/battery status/BatteryManager/onlevelchange</a></td>
	<td class="Summary">Handles the levelchange event.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/canvas/CanvasRenderingContext2D/drawCustomFocusRing" title="apis/canvas/CanvasRenderingContext2D/drawCustomFocusRing">apis/canvas/CanvasRenderingContext2D/drawCustomFocusRing</a></td>
	<td class="Summary">Draw a focus ring of the appropriate style along the intended path, and sets result to <i>false</i>.
<b>Removed from spec; deletion candidate.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/canvas/CanvasRenderingContext2D/drawSystemFocusRing" title="apis/canvas/CanvasRenderingContext2D/drawSystemFocusRing">apis/canvas/CanvasRenderingContext2D/drawSystemFocusRing</a></td>
	<td class="Summary">Draws a focus ring of the appropriate style along the intended path, following platform conventions.
<b>Removed from spec; deletion candidate.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/canvas/CanvasRenderingContext2D/ellipse" title="apis/canvas/CanvasRenderingContext2D/ellipse">apis/canvas/CanvasRenderingContext2D/ellipse</a></td>
	<td class="Summary">Draws the specified ellipse. If the object's path has any subpaths, this method adds a straight line from the last point in the subpath to the start point of the arc. Then, it adds the start and end points of the arc to the subpath, and connects them with an arc.
<b>Experimental, subject to change or removal; deletion candidate.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/file/FileError" title="apis/file/FileError">apis/file/FileError</a></td>
	<td class="Summary">Represents an error that occurs while using the FileReader interface.
Obsolete per latest specification. Use <a href="/wiki/dom/DOMError" title="dom/DOMError">DOMError</a> instead.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/file/MSStreamError" title="apis/file/MSStreamError">apis/file/MSStreamError</a></td>
	<td class="Summary">The MSStreamError object reports file-related errors asynchronously.
Obsolete per latest specification. Use <a href="/wiki/dom/DOMError" title="dom/DOMError">DOMError</a> instead.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/file/MSStreamReader" title="apis/file/MSStreamReader">apis/file/MSStreamReader</a></td>
	<td class="Summary">Creates random access data (Blob) from an MSStream object.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/file/MSStreamReader/onabort" title="apis/file/MSStreamReader/onabort">apis/file/MSStreamReader/onabort</a></td>
	<td class="Summary">Indicates that the read has been aborted (for example, by calling <b>abort()</b>).</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/file/MSStreamReader/readAsBlob" title="apis/file/MSStreamReader/readAsBlob">apis/file/MSStreamReader/readAsBlob</a></td>
	<td class="Summary">Performs an asynchronous read of an <a href="/w/index.php?title=apis/file/MSStream&amp;action=edit&amp;redlink=1" class="new" title="apis/file/MSStream (page does not exist)">MSStream</a> object in order to create a <a href="/wiki/apis/file/Blob" title="apis/file/Blob">Blob</a> object.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/file/MSStreamReader/readAsText" title="apis/file/MSStreamReader/readAsText">apis/file/MSStreamReader/readAsText</a></td>
	<td class="Summary">Returns partial Blob data representing the number of bytes currently loaded (as a fraction of the total), decoded into memory according to the encoding determination.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/file/URL/revokeObjectURL" title="apis/file/URL/revokeObjectURL">apis/file/URL/revokeObjectURL</a></td>
	<td class="Summary">Revokes a URL from a document and frees the object associated with that URL.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/DirectoryEntry/createReader" title="apis/filesystem/DirectoryEntry/createReader">apis/filesystem/DirectoryEntry/createReader</a></td>
	<td class="Summary">Creates a new DirectoryReader to read Entries from this Directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/DirectoryEntry/getDirectory" title="apis/filesystem/DirectoryEntry/getDirectory">apis/filesystem/DirectoryEntry/getDirectory</a></td>
	<td class="Summary">Creates or looks up a directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/DirectoryEntry/getFile" title="apis/filesystem/DirectoryEntry/getFile">apis/filesystem/DirectoryEntry/getFile</a></td>
	<td class="Summary">Creates or looks up a file.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/DirectoryEntry/removeRecursively" title="apis/filesystem/DirectoryEntry/removeRecursively">apis/filesystem/DirectoryEntry/removeRecursively</a></td>
	<td class="Summary">Deletes a directory and all of its contents, if any. In the event of an error [e.g. trying to delete a directory that contains a file that cannot be removed], some of the contents of the directory may be deleted. It is an error to attempt to delete the root directory of a filesystem.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/DirectoryEntrySync/createReader" title="apis/filesystem/DirectoryEntrySync/createReader">apis/filesystem/DirectoryEntrySync/createReader</a></td>
	<td class="Summary">Creates a new DirectoryReaderSync to read EntrySyncs from this DirectorySync.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/DirectoryEntrySync/getDirectory" title="apis/filesystem/DirectoryEntrySync/getDirectory">apis/filesystem/DirectoryEntrySync/getDirectory</a></td>
	<td class="Summary">Creates or looks up a directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/DirectoryEntrySync/getFile" title="apis/filesystem/DirectoryEntrySync/getFile">apis/filesystem/DirectoryEntrySync/getFile</a></td>
	<td class="Summary">Creates or looks up a file.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/DirectoryEntrySync/removeRecursively" title="apis/filesystem/DirectoryEntrySync/removeRecursively">apis/filesystem/DirectoryEntrySync/removeRecursively</a></td>
	<td class="Summary">Deletes a directory and all of its contents, if any. In the event of an error [e.g. trying to delete a directory that contains a file that cannot be removed], some of the contents of the directory may be deleted. It is an error to attempt to delete the root directory of a filesystem.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/DirectoryReader/readEntries" title="apis/filesystem/DirectoryReader/readEntries">apis/filesystem/DirectoryReader/readEntries</a></td>
	<td class="Summary">Read the next block of entries from this directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/DirectoryReaderSync/readEntries" title="apis/filesystem/DirectoryReaderSync/readEntries">apis/filesystem/DirectoryReaderSync/readEntries</a></td>
	<td class="Summary">Read the next block of entries from this directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/EntriesCallback/handleEvent" title="apis/filesystem/EntriesCallback/handleEvent">apis/filesystem/EntriesCallback/handleEvent</a></td>
	<td class="Summary">Used to supply an array of Entries as a response to a user query.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/Entry/copyTo" title="apis/filesystem/Entry/copyTo">apis/filesystem/Entry/copyTo</a></td>
	<td class="Summary">Copy an Entry to a different location on the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/Entry/filesystem" title="apis/filesystem/Entry/filesystem">apis/filesystem/Entry/filesystem</a></td>
	<td class="Summary">The file system on which the Entry resides.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/Entry/fullPath" title="apis/filesystem/Entry/fullPath">apis/filesystem/Entry/fullPath</a></td>
	<td class="Summary">The full absolute path from the root to the Entry.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/Entry/getMetadata" title="apis/filesystem/Entry/getMetadata">apis/filesystem/Entry/getMetadata</a></td>
	<td class="Summary">Look up metadata about this Entry.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/Entry/getParent" title="apis/filesystem/Entry/getParent">apis/filesystem/Entry/getParent</a></td>
	<td class="Summary">Look up the parent DirectoryEntry containing this Entry. If this Entry is the root of its filesystem, its parent is itself.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/Entry/isDirectory" title="apis/filesystem/Entry/isDirectory">apis/filesystem/Entry/isDirectory</a></td>
	<td class="Summary">True if the Entry is a directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/Entry/isFile" title="apis/filesystem/Entry/isFile">apis/filesystem/Entry/isFile</a></td>
	<td class="Summary">True if the Entry is a file.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/Entry/moveTo" title="apis/filesystem/Entry/moveTo">apis/filesystem/Entry/moveTo</a></td>
	<td class="Summary">Move an Entry to a different location on the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/Entry/name" title="apis/filesystem/Entry/name">apis/filesystem/Entry/name</a></td>
	<td class="Summary">The name of the Entry, excluding the path leading to it.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/Entry/remove" title="apis/filesystem/Entry/remove">apis/filesystem/Entry/remove</a></td>
	<td class="Summary">Deletes a file or directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/Entry/toURL" title="apis/filesystem/Entry/toURL">apis/filesystem/Entry/toURL</a></td>
	<td class="Summary">Returns a URL that can be used to identify this Entry.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/EntryCallback/handleEvent" title="apis/filesystem/EntryCallback/handleEvent">apis/filesystem/EntryCallback/handleEvent</a></td>
	<td class="Summary">Used to supply an Entry as a response to a user query.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/EntrySync/copyTo" title="apis/filesystem/EntrySync/copyTo">apis/filesystem/EntrySync/copyTo</a></td>
	<td class="Summary">Copy an EntrySync to a different location on the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/EntrySync/filesystem" title="apis/filesystem/EntrySync/filesystem">apis/filesystem/EntrySync/filesystem</a></td>
	<td class="Summary">The file system on which the EntrySync resides.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/EntrySync/fullPath" title="apis/filesystem/EntrySync/fullPath">apis/filesystem/EntrySync/fullPath</a></td>
	<td class="Summary">The full absolute path from the root to the EntrySync.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/EntrySync/getMetadata" title="apis/filesystem/EntrySync/getMetadata">apis/filesystem/EntrySync/getMetadata</a></td>
	<td class="Summary">Look up metadata about this EntrySync.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/EntrySync/getParent" title="apis/filesystem/EntrySync/getParent">apis/filesystem/EntrySync/getParent</a></td>
	<td class="Summary">Look up the parent DirectoryEntrySync containing this EntrySync. If this EntrySync is the root of its filesystem, its parent is itself.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/EntrySync/isDirectory" title="apis/filesystem/EntrySync/isDirectory">apis/filesystem/EntrySync/isDirectory</a></td>
	<td class="Summary">True if the EntrySync is a directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/EntrySync/isFile" title="apis/filesystem/EntrySync/isFile">apis/filesystem/EntrySync/isFile</a></td>
	<td class="Summary">True if the EntrySync is a file.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/EntrySync/moveTo" title="apis/filesystem/EntrySync/moveTo">apis/filesystem/EntrySync/moveTo</a></td>
	<td class="Summary">Move an EntrySync to a different location on the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/EntrySync/name" title="apis/filesystem/EntrySync/name">apis/filesystem/EntrySync/name</a></td>
	<td class="Summary">The name of the EntrySync, excluding the path leading to it.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/EntrySync/remove" title="apis/filesystem/EntrySync/remove">apis/filesystem/EntrySync/remove</a></td>
	<td class="Summary">Deletes a file or directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/EntrySync/toURL" title="apis/filesystem/EntrySync/toURL">apis/filesystem/EntrySync/toURL</a></td>
	<td class="Summary">Returns a URL that can be used to identify this EntrySync.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/ErrorCallback/handleEvent" title="apis/filesystem/ErrorCallback/handleEvent">apis/filesystem/ErrorCallback/handleEvent</a></td>
	<td class="Summary">There was an error with the request. Details are provided by the err parameter.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/FileCallback/handleEvent" title="apis/filesystem/FileCallback/handleEvent">apis/filesystem/FileCallback/handleEvent</a></td>
	<td class="Summary">Used to supply a File as a response to a user query.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/FileEntry/createWriter" title="apis/filesystem/FileEntry/createWriter">apis/filesystem/FileEntry/createWriter</a></td>
	<td class="Summary">Creates a new FileWriter associated with the file that this FileEntry represents.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/FileEntry/file" title="apis/filesystem/FileEntry/file">apis/filesystem/FileEntry/file</a></td>
	<td class="Summary">Returns a File that represents the current state of the file that this FileEntry represents.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/FileEntrySync/createWriter" title="apis/filesystem/FileEntrySync/createWriter">apis/filesystem/FileEntrySync/createWriter</a></td>
	<td class="Summary">Creates a new FileWriterSync associated with the file that this FileEntrySync represents.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/FileEntrySync/file" title="apis/filesystem/FileEntrySync/file">apis/filesystem/FileEntrySync/file</a></td>
	<td class="Summary">Returns a File that represents the current state of the file that this FileEntrySync represents.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/FileSystem/name" title="apis/filesystem/FileSystem/name">apis/filesystem/FileSystem/name</a></td>
	<td class="Summary">The name of the file system. The specifics of naming filesystems is unspecified, but a name must be unique across the list of exposed file systems.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/FileSystem/root" title="apis/filesystem/FileSystem/root">apis/filesystem/FileSystem/root</a></td>
	<td class="Summary">The root directory of the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/FileSystemCallback/handleEvent" title="apis/filesystem/FileSystemCallback/handleEvent">apis/filesystem/FileSystemCallback/handleEvent</a></td>
	<td class="Summary">The file system was successfully obtained.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/FileSystemSync/name" title="apis/filesystem/FileSystemSync/name">apis/filesystem/FileSystemSync/name</a></td>
	<td class="Summary">The name of the file system. The specifics of naming filesystems is unspecified, but a name must be unique across the list of exposed file systems.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/FileSystemSync/root" title="apis/filesystem/FileSystemSync/root">apis/filesystem/FileSystemSync/root</a></td>
	<td class="Summary">The root directory of the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/FileWriterCallback/handleEvent" title="apis/filesystem/FileWriterCallback/handleEvent">apis/filesystem/FileWriterCallback/handleEvent</a></td>
	<td class="Summary">Used to supply a FileWriter as a response to a user query.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/LocalFileSystem/requestFileSystem" title="apis/filesystem/LocalFileSystem/requestFileSystem">apis/filesystem/LocalFileSystem/requestFileSystem</a></td>
	<td class="Summary">Requests a file system where data should be stored. You access a sandboxed file system by requesting a LocalFileSystem object using this global method, window.requestFileSystem().
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/LocalFileSystem/resolveLocalFileSystemURL" title="apis/filesystem/LocalFileSystem/resolveLocalFileSystemURL">apis/filesystem/LocalFileSystem/resolveLocalFileSystemURL</a></td>
	<td class="Summary">Allows the user to look up the Entry for a file or directory referred to by a local URL.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/LocalFileSystemSync/requestFileSystemSync" title="apis/filesystem/LocalFileSystemSync/requestFileSystemSync">apis/filesystem/LocalFileSystemSync/requestFileSystemSync</a></td>
	<td class="Summary">Requests a file system where data should be stored. You access a sandboxed file system by requesting a LocalFileSystemSync object from within a web worker using this global method, window.requestFileSystemSync().
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/LocalFileSystemSync/resolveLocalFileSystemSyncURL" title="apis/filesystem/LocalFileSystemSync/resolveLocalFileSystemSyncURL">apis/filesystem/LocalFileSystemSync/resolveLocalFileSystemSyncURL</a></td>
	<td class="Summary">Allows the user to look up the Entry for a file or directory referred to by a local URL.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/filesystem/MetadataCallback/handleEvent" title="apis/filesystem/MetadataCallback/handleEvent">apis/filesystem/MetadataCallback/handleEvent</a></td>
	<td class="Summary">Used to supply file or directory metadata as a response to a user query.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/filesystem/VoidCallback/handleEvent" title="apis/filesystem/VoidCallback/handleEvent">apis/filesystem/VoidCallback/handleEvent</a></td>
	<td class="Summary">Indicates success of an asynchronous method.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/image_capture/ImageCapture/getFrame" title="apis/image capture/ImageCapture/getFrame">apis/image capture/ImageCapture/getFrame</a></td>
	<td class="Summary">Gathers data from the VideoStreamTrack into a ImageData object.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/image_capture/ImageCapture/onerror" title="apis/image capture/ImageCapture/onerror">apis/image capture/ImageCapture/onerror</a></td>
	<td class="Summary">Register/unregister for Image Capture error events of type ImageCaptureErrorEvent.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/image_capture/ImageCapture/onframegrab" title="apis/image capture/ImageCapture/onframegrab">apis/image capture/ImageCapture/onframegrab</a></td>
	<td class="Summary">Register/unregister for frame capture events of type FrameGrabEvent.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/image_capture/ImageCapture/onphoto" title="apis/image capture/ImageCapture/onphoto">apis/image capture/ImageCapture/onphoto</a></td>
	<td class="Summary">Register/unregister for photo events of type BlobEvent.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/image_capture/ImageCapture/onphotosettingschange" title="apis/image capture/ImageCapture/onphotosettingschange">apis/image capture/ImageCapture/onphotosettingschange</a></td>
	<td class="Summary">Register/unregister for photo settings change events of type SettingsChangeEvent.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/image_capture/ImageCapture/photoSettingsOptions" title="apis/image capture/ImageCapture/photoSettingsOptions">apis/image capture/ImageCapture/photoSettingsOptions</a></td>
	<td class="Summary">Describes current photo settings.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/image_capture/ImageCapture/setOptions" title="apis/image capture/ImageCapture/setOptions">apis/image capture/ImageCapture/setOptions</a></td>
	<td class="Summary">Applies the settings specified by the PhotoSettings object passed by parameter.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/image_capture/ImageCapture/takePhoto" title="apis/image capture/ImageCapture/takePhoto">apis/image capture/ImageCapture/takePhoto</a></td>
	<td class="Summary">Gathers data from the VideoStreamTrack into a Blob containing a single still image.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/image_capture/ImageCapture/videoStreamTrack" title="apis/image capture/ImageCapture/videoStreamTrack">apis/image capture/ImageCapture/videoStreamTrack</a></td>
	<td class="Summary">The MediaStream passed into the constructor.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBCursor/delete" title="apis/indexeddb/IDBCursor/delete">apis/indexeddb/IDBCursor/delete</a></td>
	<td class="Summary">Returns an IDBRequest object and, in a separate thread, deletes the record at the cursor's position, without changing the cursor's position. Once the record is deleted, the cursor's value is set to null.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBCursor/direction" title="apis/indexeddb/IDBCursor/direction">apis/indexeddb/IDBCursor/direction</a></td>
	<td class="Summary">Indicates the direction of travel within a cursor.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBCursor/key" title="apis/indexeddb/IDBCursor/key">apis/indexeddb/IDBCursor/key</a></td>
	<td class="Summary">The key value for the record currently displayed by the cursor.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBCursor/primaryKey" title="apis/indexeddb/IDBCursor/primaryKey">apis/indexeddb/IDBCursor/primaryKey</a></td>
	<td class="Summary">Returns the cursor's current effective key.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBCursor/source" title="apis/indexeddb/IDBCursor/source">apis/indexeddb/IDBCursor/source</a></td>
	<td class="Summary">On getting, returns the IDBObjectStore or IDBIndex that the cursor is iterating. This function never returns null or throws an exception, even if the cursor is currently being iterated, has iterated past its end, or its transaction is not active.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBCursor/update" title="apis/indexeddb/IDBCursor/update">apis/indexeddb/IDBCursor/update</a></td>
	<td class="Summary">Creates a structured clone of the value parameter.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBCursorWithValue/value" title="apis/indexeddb/IDBCursorWithValue/value">apis/indexeddb/IDBCursorWithValue/value</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBDatabase/deleteObjectStore" title="apis/indexeddb/IDBDatabase/deleteObjectStore">apis/indexeddb/IDBDatabase/deleteObjectStore</a></td>
	<td class="Summary">Destroys an object store with the given name as well as all indexes that are referencing that object store.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBDatabase/name" title="apis/indexeddb/IDBDatabase/name">apis/indexeddb/IDBDatabase/name</a></td>
	<td class="Summary">Name of the connected database.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBDatabase/objectStoreNames" title="apis/indexeddb/IDBDatabase/objectStoreNames">apis/indexeddb/IDBDatabase/objectStoreNames</a></td>
	<td class="Summary">Returns a list of names of the object stores currently in the connected database.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBDatabase/setVersion" title="apis/indexeddb/IDBDatabase/setVersion">apis/indexeddb/IDBDatabase/setVersion</a></td>
	<td class="Summary">Deletion candidate. Not in spec: <a rel="nofollow" class="external free" href="http://www.w3.org/TR/IndexedDB/">http://www.w3.org/TR/IndexedDB/</a></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBDatabase/transaction" title="apis/indexeddb/IDBDatabase/transaction">apis/indexeddb/IDBDatabase/transaction</a></td>
	<td class="Summary">Execute the steps for creating a transaction in a sychronous fashion.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBDatabase/version" title="apis/indexeddb/IDBDatabase/version">apis/indexeddb/IDBDatabase/version</a></td>
	<td class="Summary">Returns the version of the database when this IDBDatabaseSync instance was created.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBDatabaseException" title="apis/indexeddb/IDBDatabaseException">apis/indexeddb/IDBDatabaseException</a></td>
	<td class="Summary">Not supported.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBDatabaseException/code" title="apis/indexeddb/IDBDatabaseException/code">apis/indexeddb/IDBDatabaseException/code</a></td>
	<td class="Summary">Not supported.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBDatabaseException/message" title="apis/indexeddb/IDBDatabaseException/message">apis/indexeddb/IDBDatabaseException/message</a></td>
	<td class="Summary">Not supported.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBIndex/count" title="apis/indexeddb/IDBIndex/count">apis/indexeddb/IDBIndex/count</a></td>
	<td class="Summary">Runs the steps for asynchronously executing a request and returns the IDBRequest created by these steps.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBIndex/get" title="apis/indexeddb/IDBIndex/get">apis/indexeddb/IDBIndex/get</a></td>
	<td class="Summary">Runs the steps for asynchronously executing a request and returns the IDBRequest created by these steps.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBIndex/keyPath" title="apis/indexeddb/IDBIndex/keyPath">apis/indexeddb/IDBIndex/keyPath</a></td>
	<td class="Summary">The key path of this index. If null, this index is not auto-populated.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBIndex/multiEntry" title="apis/indexeddb/IDBIndex/multiEntry">apis/indexeddb/IDBIndex/multiEntry</a></td>
	<td class="Summary">Affects how the index behaves when the result of evaluating the index's key path yields an array. If true, there is one record in the index for each item in an array of keys. If false, then there is one record for each key that is an array.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBIndex/name" title="apis/indexeddb/IDBIndex/name">apis/indexeddb/IDBIndex/name</a></td>
	<td class="Summary">The name of this index.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBIndex/objectStore" title="apis/indexeddb/IDBIndex/objectStore">apis/indexeddb/IDBIndex/objectStore</a></td>
	<td class="Summary">Returns a reference to the IDBObjectStore instance for the referenced object store in this IDBIndex's transaction.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBIndex/openCursor" title="apis/indexeddb/IDBIndex/openCursor">apis/indexeddb/IDBIndex/openCursor</a></td>
	<td class="Summary">Creates a cursor.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBIndex/openKeyCursor" title="apis/indexeddb/IDBIndex/openKeyCursor">apis/indexeddb/IDBIndex/openKeyCursor</a></td>
	<td class="Summary">Creates a cursor.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBIndex/unique" title="apis/indexeddb/IDBIndex/unique">apis/indexeddb/IDBIndex/unique</a></td>
	<td class="Summary">Provides the unique flag of this index.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBKeyRange/lower" title="apis/indexeddb/IDBKeyRange/lower">apis/indexeddb/IDBKeyRange/lower</a></td>
	<td class="Summary">This value is the lower-bound of the key range.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBKeyRange/lowerBound" title="apis/indexeddb/IDBKeyRange/lowerBound">apis/indexeddb/IDBKeyRange/lowerBound</a></td>
	<td class="Summary">Creates and returns a new key range with lower set to lower, lowerOpen set to open, upper set to undefined and and upperOpen set to true.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBKeyRange/lowerOpen" title="apis/indexeddb/IDBKeyRange/lowerOpen">apis/indexeddb/IDBKeyRange/lowerOpen</a></td>
	<td class="Summary">Returns false if the lower-bound value is included in the key range. Returns true if the lower-bound value is excluded from the key range.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBKeyRange/only" title="apis/indexeddb/IDBKeyRange/only">apis/indexeddb/IDBKeyRange/only</a></td>
	<td class="Summary">Creates and returns a new key range with both lower and upper set to value and both lowerOpen and upperOpen set to false.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBKeyRange/upperBound" title="apis/indexeddb/IDBKeyRange/upperBound">apis/indexeddb/IDBKeyRange/upperBound</a></td>
	<td class="Summary">Creates and returns a new key range with lower set to undefined, lowerOpen set to true, upper set to upper and and upperOpen set to open.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBKeyRange/upperOpen" title="apis/indexeddb/IDBKeyRange/upperOpen">apis/indexeddb/IDBKeyRange/upperOpen</a></td>
	<td class="Summary">Returns false if the upper-bound value is included in the key range. Returns true if the upper-bound value is excluded from the key range.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBObjectStore/autoIncrement" title="apis/indexeddb/IDBObjectStore/autoIncrement">apis/indexeddb/IDBObjectStore/autoIncrement</a></td>
	<td class="Summary">Provides the auto increment flag for this object store.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBObjectStore/count" title="apis/indexeddb/IDBObjectStore/count">apis/indexeddb/IDBObjectStore/count</a></td>
	<td class="Summary">The count method returns the number of records in an object store.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBObjectStore/get" title="apis/indexeddb/IDBObjectStore/get">apis/indexeddb/IDBObjectStore/get</a></td>
	<td class="Summary">Runs the steps for asynchronously executing a request and returns the IDBRequest created by these steps.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBObjectStore/index" title="apis/indexeddb/IDBObjectStore/index">apis/indexeddb/IDBObjectStore/index</a></td>
	<td class="Summary">Returns an IDBIndex representing an index that is part of the object store.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBObjectStore/indexNames" title="apis/indexeddb/IDBObjectStore/indexNames">apis/indexeddb/IDBObjectStore/indexNames</a></td>
	<td class="Summary">Provides a list of the names of indexes on objects in this object store.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBObjectStore/keyPath" title="apis/indexeddb/IDBObjectStore/keyPath">apis/indexeddb/IDBObjectStore/keyPath</a></td>
	<td class="Summary">Provides the key path of this object store.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBObjectStore/name" title="apis/indexeddb/IDBObjectStore/name">apis/indexeddb/IDBObjectStore/name</a></td>
	<td class="Summary">Provides the name of this object store.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBObjectStore/openCursor" title="apis/indexeddb/IDBObjectStore/openCursor">apis/indexeddb/IDBObjectStore/openCursor</a></td>
	<td class="Summary">Creates a cursor.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBObjectStore/put" title="apis/indexeddb/IDBObjectStore/put">apis/indexeddb/IDBObjectStore/put</a></td>
	<td class="Summary">Creates a structured clone of the value parameter.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBObjectStore/transaction" title="apis/indexeddb/IDBObjectStore/transaction">apis/indexeddb/IDBObjectStore/transaction</a></td>
	<td class="Summary">Returns the transaction this object store belongs to.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBOpenDBRequest/onUpgradeNeeded" title="apis/indexeddb/IDBOpenDBRequest/onUpgradeNeeded">apis/indexeddb/IDBOpenDBRequest/onUpgradeNeeded</a></td>
	<td class="Summary">The event handler for the upgrade needed event.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBOpenDBRequest/onblocked" title="apis/indexeddb/IDBOpenDBRequest/onblocked">apis/indexeddb/IDBOpenDBRequest/onblocked</a></td>
	<td class="Summary">The event handler for the blocked event. This event is triggered when the upgradeneeded should be triggered because of a version change but the database is still in use (ie not closed) somewhere, even after the versionchange event was sent.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBRequest/error" title="apis/indexeddb/IDBRequest/error">apis/indexeddb/IDBRequest/error</a></td>
	<td class="Summary">The error codes returned under certain conditions.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBRequest/onerror" title="apis/indexeddb/IDBRequest/onerror">apis/indexeddb/IDBRequest/onerror</a></td>
	<td class="Summary">The event handler for the error event.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBRequest/onsuccess" title="apis/indexeddb/IDBRequest/onsuccess">apis/indexeddb/IDBRequest/onsuccess</a></td>
	<td class="Summary">The event handler for the success event.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBRequest/readyState" title="apis/indexeddb/IDBRequest/readyState">apis/indexeddb/IDBRequest/readyState</a></td>
	<td class="Summary">The state of the request. Every request starts in the pending state. The state changes to done when the request completes successfully or when an error occurs.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBRequest/result" title="apis/indexeddb/IDBRequest/result">apis/indexeddb/IDBRequest/result</a></td>
	<td class="Summary">Returns the result of the request. If the the request failed and the result is not available, the DOMException InvalidStateError exception is thrown.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBRequest/source" title="apis/indexeddb/IDBRequest/source">apis/indexeddb/IDBRequest/source</a></td>
	<td class="Summary">The source of the request, such as an Index or a ObjectStore. If no source exists (such as when calling indexedDB.open()), it returns null.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBRequest/transaction" title="apis/indexeddb/IDBRequest/transaction">apis/indexeddb/IDBRequest/transaction</a></td>
	<td class="Summary">The transaction for the request. This property can be null for certain requests, such as for request returned from IDBFactory.open (You're just connecting to a database, so there is no transaction to return).</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBTransaction/db" title="apis/indexeddb/IDBTransaction/db">apis/indexeddb/IDBTransaction/db</a></td>
	<td class="Summary">The database connection of which this transaction is a part.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBTransaction/error" title="apis/indexeddb/IDBTransaction/error">apis/indexeddb/IDBTransaction/error</a></td>
	<td class="Summary">Null if the transaction is not finished, is finished and successfully committed, or was aborted with the abort() function. Returns the same DOMError as the request object which caused the transaction to be aborted due to a failed request, or a DOMError for the transaction failure not due to a failed request (such as QuotaExceededError or UnknownError).</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBTransaction/mode" title="apis/indexeddb/IDBTransaction/mode">apis/indexeddb/IDBTransaction/mode</a></td>
	<td class="Summary">The mode for isolating access to data in the object stores that are in the scope of the transaction. For possible values, see Return Value, below. The default value is readonly.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBTransaction/objectStore" title="apis/indexeddb/IDBTransaction/objectStore">apis/indexeddb/IDBTransaction/objectStore</a></td>
	<td class="Summary">Returns an object store that has already been added to the scope of this transaction.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBTransaction/onabort" title="apis/indexeddb/IDBTransaction/onabort">apis/indexeddb/IDBTransaction/onabort</a></td>
	<td class="Summary">The event handler for the onabort event.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBTransaction/oncomplete" title="apis/indexeddb/IDBTransaction/oncomplete">apis/indexeddb/IDBTransaction/oncomplete</a></td>
	<td class="Summary">The event handler for the oncomplete event.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBTransaction/onerror" title="apis/indexeddb/IDBTransaction/onerror">apis/indexeddb/IDBTransaction/onerror</a></td>
	<td class="Summary">The event handler for the error event.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBVersionChangeEvent/newVersion" title="apis/indexeddb/IDBVersionChangeEvent/newVersion">apis/indexeddb/IDBVersionChangeEvent/newVersion</a></td>
	<td class="Summary">Returns the new version of the database, which is the version specified by the open request.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBVersionChangeEvent/oldVersion" title="apis/indexeddb/IDBVersionChangeEvent/oldVersion">apis/indexeddb/IDBVersionChangeEvent/oldVersion</a></td>
	<td class="Summary">Returns the old version of the database.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/indexeddb/IDBVersionChangeRequest/onblocked" title="apis/indexeddb/IDBVersionChangeRequest/onblocked">apis/indexeddb/IDBVersionChangeRequest/onblocked</a></td>
	<td class="Summary">The event handler for the blocked event.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/indexeddb/indexedDB/open" title="apis/indexeddb/indexedDB/open">apis/indexeddb/indexedDB/open</a></td>
	<td class="Summary">Opens a database. See <a href="/wiki/apis/indexeddb/IDBFactory/open" title="apis/indexeddb/IDBFactory/open">apis/indexeddb/IDBFactory/open</a></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStream/addtrack" title="apis/media capture and streams/MediaStream/addtrack">apis/media capture and streams/MediaStream/addtrack</a></td>
	<td class="Summary">This event is fired when a track is added to the MediaStream.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStream/ended" title="apis/media capture and streams/MediaStream/ended">apis/media capture and streams/MediaStream/ended</a></td>
	<td class="Summary">Is true if the MediaStream has finished, false otherwise.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStream/id" title="apis/media capture and streams/MediaStream/id">apis/media capture and streams/MediaStream/id</a></td>
	<td class="Summary">A globally unique identifier string, initialized when the MediaStream object is created.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStream/onaddtrack" title="apis/media capture and streams/MediaStream/onaddtrack">apis/media capture and streams/MediaStream/onaddtrack</a></td>
	<td class="Summary">Handles the addtrack event when fired on the MediaStream object.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStream/onended" title="apis/media capture and streams/MediaStream/onended">apis/media capture and streams/MediaStream/onended</a></td>
	<td class="Summary">Handles the ended event when fired on the MediaStream object.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStream/onremovetrack" title="apis/media capture and streams/MediaStream/onremovetrack">apis/media capture and streams/MediaStream/onremovetrack</a></td>
	<td class="Summary">Handles the removetrack event when fired on the MediaStream object.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStream/removetrack" title="apis/media capture and streams/MediaStream/removetrack">apis/media capture and streams/MediaStream/removetrack</a></td>
	<td class="Summary">This event is fired when a track is removed from the MediaStream.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/applyConstraints" title="apis/media capture and streams/MediaStreamTrack/applyConstraints">apis/media capture and streams/MediaStreamTrack/applyConstraints</a></td>
	<td class="Summary">Replaces all existing constraints with the provided constraints, if existing constraints exist. Otherwise, it applies the newly provided constraints to the track.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/capabilities" title="apis/media capture and streams/MediaStreamTrack/capabilities">apis/media capture and streams/MediaStreamTrack/capabilities</a></td>
	<td class="Summary">Returns a dictionary with all of the capabilities for the track type.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/clone" title="apis/media capture and streams/MediaStreamTrack/clone">apis/media capture and streams/MediaStreamTrack/clone</a></td>
	<td class="Summary">Clones the given MediaStreamTrack.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/constraints" title="apis/media capture and streams/MediaStreamTrack/constraints">apis/media capture and streams/MediaStreamTrack/constraints</a></td>
	<td class="Summary">Returns the complete constraints object associated with the track. If no mandatory constraints have been defined, the mandatory field will not be present (it will be undefined). If no optional constraints have been defined, the optional field will not be present (it will be undefined). If neither optional, nor mandatory constraints have been created, the value null is returned.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/enabled" title="apis/media capture and streams/MediaStreamTrack/enabled">apis/media capture and streams/MediaStreamTrack/enabled</a></td>
	<td class="Summary">Enables the track if the new value is true, and disable it otherwise.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/id" title="apis/media capture and streams/MediaStreamTrack/id">apis/media capture and streams/MediaStreamTrack/id</a></td>
	<td class="Summary">A globally unique identifier string, initialized when the MediaStreamTrack object is created.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/kind" title="apis/media capture and streams/MediaStreamTrack/kind">apis/media capture and streams/MediaStreamTrack/kind</a></td>
	<td class="Summary">Returns the string "audio" if the object represents an audio track or "video" if object represents a video track.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/label" title="apis/media capture and streams/MediaStreamTrack/label">apis/media capture and streams/MediaStreamTrack/label</a></td>
	<td class="Summary">Returns the label of the object’s corresponding track, if any. If the corresponding track has or had no label, it returns the empty string.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/mute" title="apis/media capture and streams/MediaStreamTrack/mute">apis/media capture and streams/MediaStreamTrack/mute</a></td>
	<td class="Summary">This event fires when the MediaStreamTrack object's source is temporarily unable to provide data.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/muted" title="apis/media capture and streams/MediaStreamTrack/muted">apis/media capture and streams/MediaStreamTrack/muted</a></td>
	<td class="Summary">Returns true if the track is muted, and false otherwise.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/onended" title="apis/media capture and streams/MediaStreamTrack/onended">apis/media capture and streams/MediaStreamTrack/onended</a></td>
	<td class="Summary">Handles the ended event when fired on the MediaStreamTrack object.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/onmute" title="apis/media capture and streams/MediaStreamTrack/onmute">apis/media capture and streams/MediaStreamTrack/onmute</a></td>
	<td class="Summary">Handles the mute event when fired on the MediaStreamTrack object.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/onoverconstrained" title="apis/media capture and streams/MediaStreamTrack/onoverconstrained">apis/media capture and streams/MediaStreamTrack/onoverconstrained</a></td>
	<td class="Summary">Handles the overcontrained event when fired on the MediaStreamTrack object.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/onstarted" title="apis/media capture and streams/MediaStreamTrack/onstarted">apis/media capture and streams/MediaStreamTrack/onstarted</a></td>
	<td class="Summary">Handles the started event when fired on the MediaStreamTrack object.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/onunmute" title="apis/media capture and streams/MediaStreamTrack/onunmute">apis/media capture and streams/MediaStreamTrack/onunmute</a></td>
	<td class="Summary">Handles the unmute event when fired on the MediaStreamTrack object.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/overconstrained" title="apis/media capture and streams/MediaStreamTrack/overconstrained">apis/media capture and streams/MediaStreamTrack/overconstrained</a></td>
	<td class="Summary">This event fires asynchronously for each affected track (when multiple tracks share the same source) after the user agent has evaluated the current constraints against a given sourceId and is not able to configure the source within the limitations established by the union of imposed constraints.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/readonly" title="apis/media capture and streams/MediaStreamTrack/readonly">apis/media capture and streams/MediaStreamTrack/readonly</a></td>
	<td class="Summary">Returns true If the track (audio or video) is backed by a read-only source such as a file, or the track source is a local microphone or camera, but is shared so that this track cannot modify any of the source's settings. Returns false otherwise.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/readyState" title="apis/media capture and streams/MediaStreamTrack/readyState">apis/media capture and streams/MediaStreamTrack/readyState</a></td>
	<td class="Summary">Returns the state of the track.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/remote" title="apis/media capture and streams/MediaStreamTrack/remote">apis/media capture and streams/MediaStreamTrack/remote</a></td>
	<td class="Summary">Returns true if the track is sourced by an RTCPeerConnection. Returns false otherwise.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/started" title="apis/media capture and streams/MediaStreamTrack/started">apis/media capture and streams/MediaStreamTrack/started</a></td>
	<td class="Summary">This event fires when the MediaStreamTrack object has just transitioned from the "new" readyState to another state.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/states" title="apis/media capture and streams/MediaStreamTrack/states">apis/media capture and streams/MediaStreamTrack/states</a></td>
	<td class="Summary">Returns an object containing all the state variables associated with the allowed constraints.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/stop" title="apis/media capture and streams/MediaStreamTrack/stop">apis/media capture and streams/MediaStreamTrack/stop</a></td>
	<td class="Summary">Permanently stop the generation of data for track's source.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/unmute" title="apis/media capture and streams/MediaStreamTrack/unmute">apis/media capture and streams/MediaStreamTrack/unmute</a></td>
	<td class="Summary">This event fires when the MediaStreamTrack object's source is live again after having been temporarily unable to provide data.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/media_capture_and_streams/ended" title="apis/media capture and streams/ended">apis/media capture and streams/ended</a></td>
	<td class="Summary">This event is fired when a MediaStream is stopped.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/network_information/Connection" title="apis/network information/Connection">apis/network information/Connection</a></td>
	<td class="Summary">Provides a handle to the device's connection information.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/network_information/Connection/bandwidth" title="apis/network information/Connection/bandwidth">apis/network information/Connection/bandwidth</a></td>
	<td class="Summary">An estimation of the current bandwidth in MB/s (Megabytes per seconds) available.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/network_information/Connection/change" title="apis/network information/Connection/change">apis/network information/Connection/change</a></td>
	<td class="Summary">Fires when the Connection changes.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/network_information/Connection/metered" title="apis/network information/Connection/metered">apis/network information/Connection/metered</a></td>
	<td class="Summary">A connection is metered when the user's connection is subject to a limitation from his Internet Service Provider strong enough to request web applications to be careful with the bandwidth usage.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/network_information/Connection/onchange" title="apis/network information/Connection/onchange">apis/network information/Connection/onchange</a></td>
	<td class="Summary">Handles the change event, fired when the Connection changes.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/network_information/NetworkInformation/connection" title="apis/network information/NetworkInformation/connection">apis/network information/NetworkInformation/connection</a></td>
	<td class="Summary">The object from which connection information is accessed.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/quota_management/StorageQuota" title="apis/quota management/StorageQuota">apis/quota management/StorageQuota</a></td>
	<td class="Summary">Provides a means to query and request storage usage and quota information.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/quota_management/queryUsageAndQuota" title="apis/quota management/queryUsageAndQuota">apis/quota management/queryUsageAndQuota</a></td>
	<td class="Summary">Queries the current usage (how much data is stored) and quota available for the requesting application.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/quota_management/requestQuota" title="apis/quota management/requestQuota">apis/quota management/requestQuota</a></td>
	<td class="Summary">Requests a new quota for the requesting application.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/web_animations/AnimationPlayer/currentTime" title="apis/web animations/AnimationPlayer/currentTime">apis/web animations/AnimationPlayer/currentTime</a></td>
	<td class="Summary">The current time of this player unless this player has a pending pause task, in which case this attribute returns null.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/web_animations/AnimationPlayer/reverse" title="apis/web animations/AnimationPlayer/reverse">apis/web animations/AnimationPlayer/reverse</a></td>
	<td class="Summary">Inverts the playback rate of this player and seeks to the start of the source content if if has finished playing in the reversed direction using the reverse a player procedure for this object.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webaudio/AudioContext/activeSourceCount" title="apis/webaudio/AudioContext/activeSourceCount">apis/webaudio/AudioContext/activeSourceCount</a></td>
	<td class="Summary">The number of <a href="/wiki/apis/webaudio/AudioBufferSourceNode" title="apis/webaudio/AudioBufferSourceNode"><b>AudioBufferSourceNode</b>s</a> that are currently playing.
<b>Out of date; removed from spec. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webaudio/AudioContext/createWaveTable" title="apis/webaudio/AudioContext/createWaveTable">apis/webaudio/AudioContext/createWaveTable</a></td>
	<td class="Summary">Creates a <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a> representing a waveform containing arbitrary harmonic content. The real and imag parameters must be of type <b>Float32Array</b> of equal lengths greater than zero and less than or equal to 4096 or an exception will be thrown. These parameters specify the Fourier coefficients of a Fourier series representing the partials of a periodic waveform. The created <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a> will be used with an <a href="/wiki/apis/webaudio/OscillatorNode" title="apis/webaudio/OscillatorNode"><b>OscillatorNode</b></a> and will represent a normalized time-domain waveform having maximum absolute peak value of 1. Another way of saying this is that the generated waveform of an <a href="/wiki/apis/webaudio/OscillatorNode" title="apis/webaudio/OscillatorNode"><b>OscillatorNode</b></a> will have maximum peak value at 0dBFS. Conveniently, this corresponds to the full-range of the signal values used by the Web Audio API. Because the <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a> will be normalized on creation, the real and imag parameters represent relative values.
<b>Out of date; removed from spec. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webaudio/AudioDestinationNode/numberOfChannels" title="apis/webaudio/AudioDestinationNode/numberOfChannels">apis/webaudio/AudioDestinationNode/numberOfChannels</a></td>
	<td class="Summary">The number of channels of the destination's input. This value will default to 2, and may be set to any non-zero value less than or equal to <a href="/wiki/apis/webaudio/AudioDestinationNode/maxChannelCount" title="apis/webaudio/AudioDestinationNode/maxChannelCount"><b>maxChannelCount</b></a>. An exception will be thrown if this value is not within the valid range.
<b>Not in spec; deletion candidate. Possibly confused with AudioBuffer/numberOfChannels. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webaudio/AudioParam/computedValue" title="apis/webaudio/AudioParam/computedValue">apis/webaudio/AudioParam/computedValue</a></td>
	<td class="Summary">The final value controlling the audio DSP, calculated at each time, which is either the value set directly to the value attribute or, if there are any scheduled parameter changes (automation events), the value as calculated from these events.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webaudio/AudioParam/maxValue" title="apis/webaudio/AudioParam/maxValue">apis/webaudio/AudioParam/maxValue</a></td>
	<td class="Summary">Nominal maximum value. The value attribute may be set higher than this value.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webaudio/AudioParam/minValue" title="apis/webaudio/AudioParam/minValue">apis/webaudio/AudioParam/minValue</a></td>
	<td class="Summary">Nominal minimum value. The value attribute may be set lower than this value.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webaudio/AudioProcessingEvent/inputBuffer" title="apis/webaudio/AudioProcessingEvent/inputBuffer">apis/webaudio/AudioProcessingEvent/inputBuffer</a></td>
	<td class="Summary">An <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> containing the input audio data. It will have a number of channels equal to the <b>numberOfInputChannels</b> parameter of the <a href="/wiki/apis/webaudio/AudioContext/createScriptProcessor" title="apis/webaudio/AudioContext/createScriptProcessor"><b>createScriptProcessor()</b></a> method. This <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> is only valid while in the scope of the <a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess"><b>onaudioprocess</b></a> function. Its values will be meaningless outside of this scope.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webaudio/AudioProcessingEvent/node" title="apis/webaudio/AudioProcessingEvent/node">apis/webaudio/AudioProcessingEvent/node</a></td>
	<td class="Summary">The <a href="/wiki/apis/webaudio/ScriptProcessorNode" title="apis/webaudio/ScriptProcessorNode"><b>ScriptProcessorNode</b></a> associated with this processing event.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webaudio/AudioProcessingEvent/outputBuffer" title="apis/webaudio/AudioProcessingEvent/outputBuffer">apis/webaudio/AudioProcessingEvent/outputBuffer</a></td>
	<td class="Summary">An <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> where the output audio data should be written. It will have a number of channels equal to the <b>numberOfOutputChannels</b> parameter of the <a href="/wiki/apis/webaudio/AudioContext/createScriptProcessor" title="apis/webaudio/AudioContext/createScriptProcessor"><b>createScriptProcessor()</b></a> method. Script code within the scope of the <a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess"><b>onaudioprocess</b></a> function is expected to modify the <b>Float32Array</b> arrays representing channel data in this <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a>. Any script modifications to this <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> outside of this scope will not produce any audible effects.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webaudio/AudioProcessingEvent/playbackTime" title="apis/webaudio/AudioProcessingEvent/playbackTime">apis/webaudio/AudioProcessingEvent/playbackTime</a></td>
	<td class="Summary">The time when the audio will be played, in the same time coordinate system as <a href="/wiki/apis/webaudio/AudioContext/currentTime" title="apis/webaudio/AudioContext/currentTime"><b>AudioContext.currentTime</b></a>. <a href="/wiki/apis/webaudio/AudioProcessingEvent/playbackTime" title="apis/webaudio/AudioProcessingEvent/playbackTime"><b>playbackTime</b></a> allows for very tight synchronization between processing directly in JavaScript with the other events in the context's rendering graph.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webaudio/OscillatorNode/playbackState" title="apis/webaudio/OscillatorNode/playbackState">apis/webaudio/OscillatorNode/playbackState</a></td>
	<td class="Summary">The playback state, initialized to UNSCHEDULED_STATE, progressing through SCHEDULED_STATE, PLAYING_STATE, and FINISHED_STATE.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webaudio/OscillatorNode/setWaveTable" title="apis/webaudio/OscillatorNode/setWaveTable">apis/webaudio/OscillatorNode/setWaveTable</a></td>
	<td class="Summary">Sets an arbitrary custom periodic waveform given a <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a>.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webaudio/ScriptProcessorNode/bufferSize" title="apis/webaudio/ScriptProcessorNode/bufferSize">apis/webaudio/ScriptProcessorNode/bufferSize</a></td>
	<td class="Summary">The size of the buffer (in sample-frames) which needs to be processed each time <a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess"><b>onaudioprocess</b></a> is called. Legal values are 256, 512, 1024, 2048, 4096, 8192, and 16384.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess">apis/webaudio/ScriptProcessorNode/onaudioprocess</a></td>
	<td class="Summary">An event listener which is called periodically for audio processing. An event of type <a href="/wiki/apis/webaudio/AudioProcessingEvent" title="apis/webaudio/AudioProcessingEvent"><b>AudioProcessingEvent</b></a> will be passed to the event handler.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/LocalMediaStream/stop" title="apis/webrtc/LocalMediaStream/stop">apis/webrtc/LocalMediaStream/stop</a></td>
	<td class="Summary">Permanently halts the generation of data for the tracks' sources and removes the references to the sources.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStream/audioTracks" title="apis/webrtc/MediaStream/audioTracks">apis/webrtc/MediaStream/audioTracks</a></td>
	<td class="Summary">The MediaStreamTrackList object representing the audio tracks.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStream/ended" title="apis/webrtc/MediaStream/ended">apis/webrtc/MediaStream/ended</a></td>
	<td class="Summary">True if the ended event has fired on the MediaStream object.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStream/label" title="apis/webrtc/MediaStream/label">apis/webrtc/MediaStream/label</a></td>
	<td class="Summary">A globally unique identifier (GUID) of 36 characters that describes the media stream.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStream/onended" title="apis/webrtc/MediaStream/onended">apis/webrtc/MediaStream/onended</a></td>
	<td class="Summary">Handles the ended event when fired on the MediaStream object.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStream/videoTracks" title="apis/webrtc/MediaStream/videoTracks">apis/webrtc/MediaStream/videoTracks</a></td>
	<td class="Summary">The MediaStreamTrackList object representing the video tracks.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrack" title="apis/webrtc/MediaStreamTrack">apis/webrtc/MediaStreamTrack</a></td>
	<td class="Summary">A MediaStreamTrack is one of two kinds, audio or video, and represents the media source, such as a camera.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrack/enabled" title="apis/webrtc/MediaStreamTrack/enabled">apis/webrtc/MediaStreamTrack/enabled</a></td>
	<td class="Summary">True if the track is still associated with its source.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrack/ended" title="apis/webrtc/MediaStreamTrack/ended">apis/webrtc/MediaStreamTrack/ended</a></td>
	<td class="Summary">The MediaStreamTrack object's source will not provide data; this may be caused by the following:
<ul><li> the user has revoked permissions on the application</li>
<li> the source device has been disconnected</li>
<li> the remote peer has stopped sending data</li>
<li> the stop() method was invoked</li></ul></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrack/kind" title="apis/webrtc/MediaStreamTrack/kind">apis/webrtc/MediaStreamTrack/kind</a></td>
	<td class="Summary">The value, either <b>audio</b> or <b>video</b> for the source of the track.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrack/label" title="apis/webrtc/MediaStreamTrack/label">apis/webrtc/MediaStreamTrack/label</a></td>
	<td class="Summary">A user agent-assigned string that identifies the track source, as in "internal microphone."</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrack/muted" title="apis/webrtc/MediaStreamTrack/muted">apis/webrtc/MediaStreamTrack/muted</a></td>
	<td class="Summary">The MediaStreamTrack object's source is temporarily unable to provide data.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrack/onended" title="apis/webrtc/MediaStreamTrack/onended">apis/webrtc/MediaStreamTrack/onended</a></td>
	<td class="Summary">Handles the ended event when fired on the MediaStream object.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrack/onmute" title="apis/webrtc/MediaStreamTrack/onmute">apis/webrtc/MediaStreamTrack/onmute</a></td>
	<td class="Summary">Handles the muted event when fired on the MediaStream object.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrack/readyState" title="apis/webrtc/MediaStreamTrack/readyState">apis/webrtc/MediaStreamTrack/readyState</a></td>
	<td class="Summary">The track's ready state; values.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrack/unmuted" title="apis/webrtc/MediaStreamTrack/unmuted">apis/webrtc/MediaStreamTrack/unmuted</a></td>
	<td class="Summary">The MediaStreamTrack object's source has resumed providing data.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrackList" title="apis/webrtc/MediaStreamTrackList">apis/webrtc/MediaStreamTrackList</a></td>
	<td class="Summary">A MediaStream has two MediaStreamTrackList objects, one for the video tracks and one for the audio tracks.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrackList/add" title="apis/webrtc/MediaStreamTrackList/add">apis/webrtc/MediaStreamTrackList/add</a></td>
	<td class="Summary">Adds a MediaStreamTrack to this track list.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrackList/addtrack" title="apis/webrtc/MediaStreamTrackList/addtrack">apis/webrtc/MediaStreamTrackList/addtrack</a></td>
	<td class="Summary">A MediaStreamTrack has been added to the list.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrackList/item" title="apis/webrtc/MediaStreamTrackList/item">apis/webrtc/MediaStreamTrackList/item</a></td>
	<td class="Summary">Returns the MediaStreamTrack at the specified index value.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrackList/length" title="apis/webrtc/MediaStreamTrackList/length">apis/webrtc/MediaStreamTrackList/length</a></td>
	<td class="Summary">The number of tracks in the list.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrackList/onaddtrack" title="apis/webrtc/MediaStreamTrackList/onaddtrack">apis/webrtc/MediaStreamTrackList/onaddtrack</a></td>
	<td class="Summary">Handles the addtrack event.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrackList/onremovetrack" title="apis/webrtc/MediaStreamTrackList/onremovetrack">apis/webrtc/MediaStreamTrackList/onremovetrack</a></td>
	<td class="Summary">Handles the removetrack event.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrackList/remove" title="apis/webrtc/MediaStreamTrackList/remove">apis/webrtc/MediaStreamTrackList/remove</a></td>
	<td class="Summary">Removes a MediaStreamTrack from this track list.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/MediaStreamTrackList/removetrack" title="apis/webrtc/MediaStreamTrackList/removetrack">apis/webrtc/MediaStreamTrackList/removetrack</a></td>
	<td class="Summary">A MediaStreamTrack has been removed from the list.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCDataChannel/binaryType" title="apis/webrtc/RTCDataChannel/binaryType">apis/webrtc/RTCDataChannel/binaryType</a></td>
	<td class="Summary">Returns the value to which it was last set; on creation, must be initialized to the string "blob".</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCDataChannel/bufferedAmount" title="apis/webrtc/RTCDataChannel/bufferedAmount">apis/webrtc/RTCDataChannel/bufferedAmount</a></td>
	<td class="Summary">Returns the number of bytes of application data that have been queued using send() but that (as of the last time the event loop started executing a task) have not yet been transmitted to the network.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCDataChannel/close" title="apis/webrtc/RTCDataChannel/close">apis/webrtc/RTCDataChannel/close</a></td>
	<td class="Summary">Closes the RTCDataChannel.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCDataChannel/label" title="apis/webrtc/RTCDataChannel/label">apis/webrtc/RTCDataChannel/label</a></td>
	<td class="Summary">A unique identifier that can be used to distinguish this RTCDataChannel object from other RTCDataChannel objects.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCDataChannel/onclose" title="apis/webrtc/RTCDataChannel/onclose">apis/webrtc/RTCDataChannel/onclose</a></td>
	<td class="Summary">An event listener to be called when an RTCDataChannel is closed.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCDataChannel/onerror" title="apis/webrtc/RTCDataChannel/onerror">apis/webrtc/RTCDataChannel/onerror</a></td>
	<td class="Summary">An event listener to be called when an error occurs.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCDataChannel/onmessage" title="apis/webrtc/RTCDataChannel/onmessage">apis/webrtc/RTCDataChannel/onmessage</a></td>
	<td class="Summary">An event listener to be called when a message is received.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCDataChannel/onopen" title="apis/webrtc/RTCDataChannel/onopen">apis/webrtc/RTCDataChannel/onopen</a></td>
	<td class="Summary">An event listener to be called when an RTCDataChannel is opened.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCDataChannel/readyState" title="apis/webrtc/RTCDataChannel/readyState">apis/webrtc/RTCDataChannel/readyState</a></td>
	<td class="Summary">Represents the state of the RTCDataChannel object.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCDataChannel/reliable" title="apis/webrtc/RTCDataChannel/reliable">apis/webrtc/RTCDataChannel/reliable</a></td>
	<td class="Summary">Returns true if the RTCDataChannel is reliable, and false otherwise.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCDataChannel/send" title="apis/webrtc/RTCDataChannel/send">apis/webrtc/RTCDataChannel/send</a></td>
	<td class="Summary">Sends a message (<i>data</i>) on the RTCDataChannel’s underlying data transport.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCIceCandidate" title="apis/webrtc/RTCIceCandidate">apis/webrtc/RTCIceCandidate</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection" title="apis/webrtc/RTCPeerConnection">apis/webrtc/RTCPeerConnection</a></td>
	<td class="Summary">Provides for the connection between remote peers, the transmission of locally generated MediaStream data and arbitrary data between peers.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/addIceCandidate" title="apis/webrtc/RTCPeerConnection/addIceCandidate">apis/webrtc/RTCPeerConnection/addIceCandidate</a></td>
	<td class="Summary">Provides a remote candidate to the ICE agent.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/close" title="apis/webrtc/RTCPeerConnection/close">apis/webrtc/RTCPeerConnection/close</a></td>
	<td class="Summary">Closes a peer connection, stops all active ICE processing and any active streaming, and releases any relevant resources such as TURN permissions.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/createAnswer" title="apis/webrtc/RTCPeerConnection/createAnswer">apis/webrtc/RTCPeerConnection/createAnswer</a></td>
	<td class="Summary">Creates a session description compatible with the remote configuration.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/createOffer" title="apis/webrtc/RTCPeerConnection/createOffer">apis/webrtc/RTCPeerConnection/createOffer</a></td>
	<td class="Summary">Creates a session description compatible with the local configuration.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/getIdentityAssertion" title="apis/webrtc/RTCPeerConnection/getIdentityAssertion">apis/webrtc/RTCPeerConnection/getIdentityAssertion</a></td>
	<td class="Summary">Provides an identity assertion.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/getStats" title="apis/webrtc/RTCPeerConnection/getStats">apis/webrtc/RTCPeerConnection/getStats</a></td>
	<td class="Summary">Retrieves status information for a given <a href="/wiki/apis/webrtc/MediaStreamTrack" title="apis/webrtc/MediaStreamTrack">MediaStreamTrack</a>.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/iceGatheringState" title="apis/webrtc/RTCPeerConnection/iceGatheringState">apis/webrtc/RTCPeerConnection/iceGatheringState</a></td>
	<td class="Summary">Returns the gathering state of the ICE agent.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/iceState" title="apis/webrtc/RTCPeerConnection/iceState">apis/webrtc/RTCPeerConnection/iceState</a></td>
	<td class="Summary">Returns the ICE state of the ICE agent.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/icecandidate" title="apis/webrtc/RTCPeerConnection/icecandidate">apis/webrtc/RTCPeerConnection/icecandidate</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/icechange" title="apis/webrtc/RTCPeerConnection/icechange">apis/webrtc/RTCPeerConnection/icechange</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/identityresult" title="apis/webrtc/RTCPeerConnection/identityresult">apis/webrtc/RTCPeerConnection/identityresult</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/localDescription" title="apis/webrtc/RTCPeerConnection/localDescription">apis/webrtc/RTCPeerConnection/localDescription</a></td>
	<td class="Summary">Returns the <a href="/wiki/apis/webrtc/RTCSessionDescription" title="apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> most recently passed to the <a href="/wiki/apis/webrtc/RTCPeerConnection/setLocalDescription" title="apis/webrtc/RTCPeerConnection/setLocalDescription">setLocalDescription()</a> method along with any local candidate descriptions generated since the method was called.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/localStreams" title="apis/webrtc/RTCPeerConnection/localStreams">apis/webrtc/RTCPeerConnection/localStreams</a></td>
	<td class="Summary">Returns an array of <a href="/wiki/apis/webrtc/MediaStream" title="apis/webrtc/MediaStream">MediaStream</a> objects added to the connection with <a href="/wiki/apis/webrtc/RTCPeerConnection/addStream" title="apis/webrtc/RTCPeerConnection/addStream">addStream()</a>.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/negotiationneeded" title="apis/webrtc/RTCPeerConnection/negotiationneeded">apis/webrtc/RTCPeerConnection/negotiationneeded</a></td>
	<td class="Summary">The browser anticipates a session negotiation is required.
It is triggered whenever <a href="/wiki/apis/webrtc/RTCPeerConnection/addStream" title="apis/webrtc/RTCPeerConnection/addStream">addStream</a>, <a href="/wiki/apis/webrtc/RTCPeerConnection/removeStream" title="apis/webrtc/RTCPeerConnection/removeStream">removeStream</a> or <a href="/wiki/apis/webrtc/RTCPeerConnection/setIdentityProvider" title="apis/webrtc/RTCPeerConnection/setIdentityProvider">setIdentityProvider</a> methods were called successfully and <a href="/wiki/apis/webrtc/RTCPeerConnection" title="apis/webrtc/RTCPeerConnection">RTCPeerConnection</a> signalingState is <code>stable</code> .</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/onaddstream" title="apis/webrtc/RTCPeerConnection/onaddstream">apis/webrtc/RTCPeerConnection/onaddstream</a></td>
	<td class="Summary">Handles the <a href="/w/index.php?title=apis/webrtc/RTCPeerConnection/addstream&amp;action=edit&amp;redlink=1" class="new" title="apis/webrtc/RTCPeerConnection/addstream (page does not exist)">addstream</a> event fired when <a href="/wiki/apis/webrtc/RTCPeerConnection/setRemoteDescription" title="apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a> is called.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/ondatachannel" title="apis/webrtc/RTCPeerConnection/ondatachannel">apis/webrtc/RTCPeerConnection/ondatachannel</a></td>
	<td class="Summary">Handles the <b>datachannel</b> event.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/ongatheringchange" title="apis/webrtc/RTCPeerConnection/ongatheringchange">apis/webrtc/RTCPeerConnection/ongatheringchange</a></td>
	<td class="Summary">Handles the <b>gatheringchange</b> event for a change to the <a href="/wiki/apis/webrtc/RTCPeerConnection/iceGatheringState" title="apis/webrtc/RTCPeerConnection/iceGatheringState">iceGatheringState</a> property.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/onicecandidate" title="apis/webrtc/RTCPeerConnection/onicecandidate">apis/webrtc/RTCPeerConnection/onicecandidate</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/icechange" title="apis/webrtc/RTCPeerConnection/icechange">icechange</a> event for a change to the <a href="/wiki/apis/webrtc/RTCPeerConnection/iceState" title="apis/webrtc/RTCPeerConnection/iceState">apis/webrtc/RTCPeerConnection/iceState</a> property. It is called any time there is a new ICE candidate added to a previous offer or answer.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/onicechange" title="apis/webrtc/RTCPeerConnection/onicechange">apis/webrtc/RTCPeerConnection/onicechange</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/icechange" title="apis/webrtc/RTCPeerConnection/icechange">icechange</a> event. It is called any time the <a href="/wiki/apis/webrtc/RTCPeerConnection/iceState" title="apis/webrtc/RTCPeerConnection/iceState">iceState</a>  changes.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/onidentityresult" title="apis/webrtc/RTCPeerConnection/onidentityresult">apis/webrtc/RTCPeerConnection/onidentityresult</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/identityresult" title="apis/webrtc/RTCPeerConnection/identityresult">identityresult</a> event for the success or failure of an identity verification.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/onnegotiationneeded" title="apis/webrtc/RTCPeerConnection/onnegotiationneeded">apis/webrtc/RTCPeerConnection/onnegotiationneeded</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/negotiationneeded" title="apis/webrtc/RTCPeerConnection/negotiationneeded">negotiationneeded</a> event.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/onopen" title="apis/webrtc/RTCPeerConnection/onopen">apis/webrtc/RTCPeerConnection/onopen</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/open" title="apis/webrtc/RTCPeerConnection/open">open</a> event.
Testing.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/onremovestream" title="apis/webrtc/RTCPeerConnection/onremovestream">apis/webrtc/RTCPeerConnection/onremovestream</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/removeStream" title="apis/webrtc/RTCPeerConnection/removeStream">removeStream</a> event for when <a href="/wiki/apis/webrtc/RTCPeerConnection/setRemoteDescription" title="apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a> is called to remove a <a href="/wiki/apis/webrtc/MediaStream" title="apis/webrtc/MediaStream">MediaStream</a> object on the remote peer.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/onstatechange" title="apis/webrtc/RTCPeerConnection/onstatechange">apis/webrtc/RTCPeerConnection/onstatechange</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/statechange" title="apis/webrtc/RTCPeerConnection/statechange">statechange</a> event for when the <a href="/wiki/apis/webrtc/RTCPeerConnection/readyState" title="apis/webrtc/RTCPeerConnection/readyState">readyState</a> property is changed, i.e. with a call to <a href="/wiki/apis/webrtc/RTCPeerConnection/setLocalDescription" title="apis/webrtc/RTCPeerConnection/setLocalDescription">setLocalDescription()</a> or <a href="/wiki/apis/webrtc/RTCPeerConnection/setRemoteDescription" title="apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a>. The event does not fire when a new RTCPeerConnection object is created.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/open" title="apis/webrtc/RTCPeerConnection/open">apis/webrtc/RTCPeerConnection/open</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/readyState" title="apis/webrtc/RTCPeerConnection/readyState">apis/webrtc/RTCPeerConnection/readyState</a></td>
	<td class="Summary">Returns the ready state of the peer connection.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/remoteDescription" title="apis/webrtc/RTCPeerConnection/remoteDescription">apis/webrtc/RTCPeerConnection/remoteDescription</a></td>
	<td class="Summary">Returns the <a href="/wiki/apis/webrtc/RTCSessionDescription" title="apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> most recently passed to the <a href="/wiki/apis/webrtc/RTCPeerConnection/setRemoteDescription" title="apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a> method along with any remote candidate descriptions supplied with <a href="/wiki/apis/webrtc/RTCPeerConnection/addIceCandidate" title="apis/webrtc/RTCPeerConnection/addIceCandidate">addIceCandidate()</a>. Returns null if the remote description has not been set.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/remoteStreams" title="apis/webrtc/RTCPeerConnection/remoteStreams">apis/webrtc/RTCPeerConnection/remoteStreams</a></td>
	<td class="Summary">Returns an array of <a href="/wiki/apis/webrtc/MediaStream" title="apis/webrtc/MediaStream">MediaStream</a> objects added to the connection by the remote peer. This array is updated when the <a href="/wiki/apis/webrtc/RTCPeerConnection/onaddstream" title="apis/webrtc/RTCPeerConnection/onaddstream">addstream</a> and <a href="/wiki/apis/webrtc/RTCPeerConnection/removeStream" title="apis/webrtc/RTCPeerConnection/removeStream">removestream</a> events are fired.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/removeStream" title="apis/webrtc/RTCPeerConnection/removeStream">apis/webrtc/RTCPeerConnection/removeStream</a></td>
	<td class="Summary">Removes the given stream from the <a href="/wiki/apis/webrtc/RTCPeerConnection/localStreams" title="apis/webrtc/RTCPeerConnection/localStreams">localStreams</a> array in the RTCPeerConnection and fires the <a href="/wiki/apis/webrtc/RTCPeerConnection/negotiationneeded" title="apis/webrtc/RTCPeerConnection/negotiationneeded">negotiationneeded</a> event.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/setIdentityProvider" title="apis/webrtc/RTCPeerConnection/setIdentityProvider">apis/webrtc/RTCPeerConnection/setIdentityProvider</a></td>
	<td class="Summary">Sets the identity provider. Not required if the browser is already configured for an identity provider.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/setLocalDescription" title="apis/webrtc/RTCPeerConnection/setLocalDescription">apis/webrtc/RTCPeerConnection/setLocalDescription</a></td>
	<td class="Summary">Applies the supplied <a href="/wiki/apis/webrtc/RTCSessionDescription" title="apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> to the local description.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/setRemoteDescription" title="apis/webrtc/RTCPeerConnection/setRemoteDescription">apis/webrtc/RTCPeerConnection/setRemoteDescription</a></td>
	<td class="Summary">Applies the supplied <a href="/wiki/apis/webrtc/RTCSessionDescription" title="apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> to the remote description.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/statechange" title="apis/webrtc/RTCPeerConnection/statechange">apis/webrtc/RTCPeerConnection/statechange</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCPeerConnection/updateIce" title="apis/webrtc/RTCPeerConnection/updateIce">apis/webrtc/RTCPeerConnection/updateIce</a></td>
	<td class="Summary">Updates the ICE agent process that gathers local candidates and remote candidates.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCSessionDescription/sdp" title="apis/webrtc/RTCSessionDescription/sdp">apis/webrtc/RTCSessionDescription/sdp</a></td>
	<td class="Summary">The string representation of the SDP object.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/webrtc/RTCSessionDescription/type" title="apis/webrtc/RTCSessionDescription/type">apis/webrtc/RTCSessionDescription/type</a></td>
	<td class="Summary">The type of SDP object this RTCSessionDescription represents.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/websocket/CloseEvent/code" title="apis/websocket/CloseEvent/code">apis/websocket/CloseEvent/code</a></td>
	<td class="Summary">The WebSocket connection close code provided by the server.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/websocket/CloseEvent/reason" title="apis/websocket/CloseEvent/reason">apis/websocket/CloseEvent/reason</a></td>
	<td class="Summary">Indicates the reason the server closed the WebSocket connection.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/websocket/WebSocket/close" title="apis/websocket/WebSocket/close">apis/websocket/WebSocket/close</a></td>
	<td class="Summary">Closes the WebSocket connection or connection attempt, if any.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/websocket/WebSocket/extensions" title="apis/websocket/WebSocket/extensions">apis/websocket/WebSocket/extensions</a></td>
	<td class="Summary">The extensions selected by the server.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/websocket/WebSocket/protocol" title="apis/websocket/WebSocket/protocol">apis/websocket/WebSocket/protocol</a></td>
	<td class="Summary">Indicates the name of the sub-protocol the server selected.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/workers/Worker/onerror" title="apis/workers/Worker/onerror">apis/workers/Worker/onerror</a></td>
	<td class="Summary">An event listener to be called when an error occurs.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/workers/Worker/onmessage" title="apis/workers/Worker/onmessage">apis/workers/Worker/onmessage</a></td>
	<td class="Summary">An event listener to be called when a message is received from the worker.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/workers/Worker/postMessage" title="apis/workers/Worker/postMessage">apis/workers/Worker/postMessage</a></td>
	<td class="Summary">Posts a message to the worker with which the object is associated.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/workers/Worker/terminate" title="apis/workers/Worker/terminate">apis/workers/Worker/terminate</a></td>
	<td class="Summary">Immediately terminates the worker with which the object is associated.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/workers/WorkerGlobalScope/close" title="apis/workers/WorkerGlobalScope/close">apis/workers/WorkerGlobalScope/close</a></td>
	<td class="Summary">Discards any pending tasks and immediately closes the worker.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/workers/WorkerGlobalScope/importScripts" title="apis/workers/WorkerGlobalScope/importScripts">apis/workers/WorkerGlobalScope/importScripts</a></td>
	<td class="Summary">Fetches one or more script resources, identified by absolute URLs.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/workers/WorkerGlobalScope/location" title="apis/workers/WorkerGlobalScope/location">apis/workers/WorkerGlobalScope/location</a></td>
	<td class="Summary">Returns the WorkerLocation object created for the WorkerGlobalScope object when the worker was created.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/workers/WorkerGlobalScope/navigator" title="apis/workers/WorkerGlobalScope/navigator">apis/workers/WorkerGlobalScope/navigator</a></td>
	<td class="Summary">Returns an instance of the WorkerNavigator interface, which represents the identity and state of the user agent (the client).</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/workers/WorkerGlobalScope/onerror" title="apis/workers/WorkerGlobalScope/onerror">apis/workers/WorkerGlobalScope/onerror</a></td>
	<td class="Summary">An event listener to be called when an error occurs.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/workers/WorkerGlobalScope/onoffline" title="apis/workers/WorkerGlobalScope/onoffline">apis/workers/WorkerGlobalScope/onoffline</a></td>
	<td class="Summary">An event listener to be called when the worker goes offline.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/workers/WorkerGlobalScope/ononline" title="apis/workers/WorkerGlobalScope/ononline">apis/workers/WorkerGlobalScope/ononline</a></td>
	<td class="Summary">An event listener to be called when the worker goes online.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/workers/WorkerGlobalScope/self" title="apis/workers/WorkerGlobalScope/self">apis/workers/WorkerGlobalScope/self</a></td>
	<td class="Summary">Returns the WorkerGlobalScope object.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/workers/WorkerLocation/href" title="apis/workers/WorkerLocation/href">apis/workers/WorkerLocation/href</a></td>
	<td class="Summary">Returns the absolute URL that the object represents.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/xhr/XMLHttpRequest/abort-event" title="apis/xhr/XMLHttpRequest/abort-event">apis/xhr/XMLHttpRequest/abort-event</a></td>
	<td class="Summary">When the request has been aborted. For instance, by invoking the abort() method.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/xhr/XMLHttpRequest/error" title="apis/xhr/XMLHttpRequest/error">apis/xhr/XMLHttpRequest/error</a></td>
	<td class="Summary">When the request has failed.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/xhr/XMLHttpRequest/getResponseHeader" title="apis/xhr/XMLHttpRequest/getResponseHeader">apis/xhr/XMLHttpRequest/getResponseHeader</a></td>
	<td class="Summary">Returns the string containing the text of the specified header, or null if the response has not been received or the header does not exist.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/xhr/XMLHttpRequest/load" title="apis/xhr/XMLHttpRequest/load">apis/xhr/XMLHttpRequest/load</a></td>
	<td class="Summary">When the request has successfully completed.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/xhr/XMLHttpRequest/loadend" title="apis/xhr/XMLHttpRequest/loadend">apis/xhr/XMLHttpRequest/loadend</a></td>
	<td class="Summary">When the request has completed (either in success or failure).</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/xhr/XMLHttpRequest/loadstart" title="apis/xhr/XMLHttpRequest/loadstart">apis/xhr/XMLHttpRequest/loadstart</a></td>
	<td class="Summary">When the request starts.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/xhr/XMLHttpRequest/progress" title="apis/xhr/XMLHttpRequest/progress">apis/xhr/XMLHttpRequest/progress</a></td>
	<td class="Summary">While sending and loading data.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/xhr/XMLHttpRequest/setRequestHeader" title="apis/xhr/XMLHttpRequest/setRequestHeader">apis/xhr/XMLHttpRequest/setRequestHeader</a></td>
	<td class="Summary">Sets the value of an XMLHttpRequest header.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/apis/xhr/XMLHttpRequest/status" title="apis/xhr/XMLHttpRequest/status">apis/xhr/XMLHttpRequest/status</a></td>
	<td class="Summary">Returns the HTTP result code (status) of the response to the request.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/apis/xhr/XMLHttpRequest/timeout-event" title="apis/xhr/XMLHttpRequest/timeout-event">apis/xhr/XMLHttpRequest/timeout-event</a></td>
	<td class="Summary">When the author specified timeout has passed before the request could complete.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/Element/change" title="dom/Element/change">dom/Element/change</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/Element/cuechange" title="dom/Element/cuechange">dom/Element/cuechange</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/Element/emptied" title="dom/Element/emptied">dom/Element/emptied</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/Element/ended" title="dom/Element/ended">dom/Element/ended</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/Element/loadeddata" title="dom/Element/loadeddata">dom/Element/loadeddata</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/Element/loadedmetadata" title="dom/Element/loadedmetadata">dom/Element/loadedmetadata</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/Element/loadstart" title="dom/Element/loadstart">dom/Element/loadstart</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/Element/media" title="dom/Element/media">dom/Element/media</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/Element/pause" title="dom/Element/pause">dom/Element/pause</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/Element/play" title="dom/Element/play">dom/Element/play</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/Element/playing" title="dom/Element/playing">dom/Element/playing</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/Element/seeked" title="dom/Element/seeked">dom/Element/seeked</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/Element/seeking" title="dom/Element/seeking">dom/Element/seeking</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/Element/stalled" title="dom/Element/stalled">dom/Element/stalled</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/Element/suspend" title="dom/Element/suspend">dom/Element/suspend</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/Element/waiting" title="dom/Element/waiting">dom/Element/waiting</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/autobuffer" title="dom/HTMLMediaElement/autobuffer">dom/HTMLMediaElement/autobuffer</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/autoplay" title="dom/HTMLMediaElement/autoplay">dom/HTMLMediaElement/autoplay</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/buffered" title="dom/HTMLMediaElement/buffered">dom/HTMLMediaElement/buffered</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/canPlayType" title="dom/HTMLMediaElement/canPlayType">dom/HTMLMediaElement/canPlayType</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/canplay" title="dom/HTMLMediaElement/canplay">dom/HTMLMediaElement/canplay</a></td>
	<td class="Summary">Fires whenever enough data is available to determine whether a media is playable.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/canplaythrough" title="dom/HTMLMediaElement/canplaythrough">dom/HTMLMediaElement/canplaythrough</a></td>
	<td class="Summary">Fires when enough data is available to determine whether a media is playable at a normal rate without interruptions.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/controls" title="dom/HTMLMediaElement/controls">dom/HTMLMediaElement/controls</a></td>
	<td class="Summary">Controls attribute used within a Audio element or Video element displays the default media controls defined by the web browser being used to open HTML document or view of a Web Application.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/currentSrc" title="dom/HTMLMediaElement/currentSrc">dom/HTMLMediaElement/currentSrc</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/currentTime" title="dom/HTMLMediaElement/currentTime">dom/HTMLMediaElement/currentTime</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/defaultPlaybackRate" title="dom/HTMLMediaElement/defaultPlaybackRate">dom/HTMLMediaElement/defaultPlaybackRate</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/duration" title="dom/HTMLMediaElement/duration">dom/HTMLMediaElement/duration</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/ended" title="dom/HTMLMediaElement/ended">dom/HTMLMediaElement/ended</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/error" title="dom/HTMLMediaElement/error">dom/HTMLMediaElement/error</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/load" title="dom/HTMLMediaElement/load">dom/HTMLMediaElement/load</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/loop" title="dom/HTMLMediaElement/loop">dom/HTMLMediaElement/loop</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/muted" title="dom/HTMLMediaElement/muted">dom/HTMLMediaElement/muted</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/networkState" title="dom/HTMLMediaElement/networkState">dom/HTMLMediaElement/networkState</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/pause" title="dom/HTMLMediaElement/pause">dom/HTMLMediaElement/pause</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/paused" title="dom/HTMLMediaElement/paused">dom/HTMLMediaElement/paused</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/playbackRate" title="dom/HTMLMediaElement/playbackRate">dom/HTMLMediaElement/playbackRate</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/played" title="dom/HTMLMediaElement/played">dom/HTMLMediaElement/played</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/preload" title="dom/HTMLMediaElement/preload">dom/HTMLMediaElement/preload</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/progress" title="dom/HTMLMediaElement/progress">dom/HTMLMediaElement/progress</a></td>
	<td class="Summary">Fires to indicate progress while downloading media data.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/seekable" title="dom/HTMLMediaElement/seekable">dom/HTMLMediaElement/seekable</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/seeking" title="dom/HTMLMediaElement/seeking">dom/HTMLMediaElement/seeking</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/src" title="dom/HTMLMediaElement/src">dom/HTMLMediaElement/src</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/textTracks" title="dom/HTMLMediaElement/textTracks">dom/HTMLMediaElement/textTracks</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLMediaElement/volume" title="dom/HTMLMediaElement/volume">dom/HTMLMediaElement/volume</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLMediaError/code" title="dom/HTMLMediaError/code">dom/HTMLMediaError/code</a></td>
	<td class="Summary">Returns the current <b>HTMLMediaError</b> code or null if no error has occurred.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLTrackElement/default" title="dom/HTMLTrackElement/default">dom/HTMLTrackElement/default</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLTrackElement/kind" title="dom/HTMLTrackElement/kind">dom/HTMLTrackElement/kind</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLTrackElement/label" title="dom/HTMLTrackElement/label">dom/HTMLTrackElement/label</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLTrackElement/srclang" title="dom/HTMLTrackElement/srclang">dom/HTMLTrackElement/srclang</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLTrackElement/track" title="dom/HTMLTrackElement/track">dom/HTMLTrackElement/track</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLVideoElement/height" title="dom/HTMLVideoElement/height">dom/HTMLVideoElement/height</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLVideoElement/initialTime" title="dom/HTMLVideoElement/initialTime">dom/HTMLVideoElement/initialTime</a></td>
	<td class="Summary">Earliest point in seconds where the playback can (should) start playing</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLVideoElement/poster" title="dom/HTMLVideoElement/poster">dom/HTMLVideoElement/poster</a></td>
	<td class="Summary">Valid URL to an image ressource that will be displayed until the first frame of the video is available or will be displayed if no valid video ressource is available at all.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLVideoElement/videoHeight" title="dom/HTMLVideoElement/videoHeight">dom/HTMLVideoElement/videoHeight</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/HTMLVideoElement/videoWidth" title="dom/HTMLVideoElement/videoWidth">dom/HTMLVideoElement/videoWidth</a></td>
	<td></td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/HTMLVideoElement/width" title="dom/HTMLVideoElement/width">dom/HTMLVideoElement/width</a></td>
	<td></td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/shadowdom/ShadowRoot/activeElement" title="dom/shadowdom/ShadowRoot/activeElement">dom/shadowdom/ShadowRoot/activeElement</a></td>
	<td class="Summary">Represents the currently focused element in the shadow tree.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/shadowdom/ShadowRoot/addStyleSheet" title="dom/shadowdom/ShadowRoot/addStyleSheet">dom/shadowdom/ShadowRoot/addStyleSheet</a></td>
	<td class="Summary">Adds a new style sheet to shadow root style sheets.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/shadowdom/ShadowRoot/applyAuthorStyles" title="dom/shadowdom/ShadowRoot/applyAuthorStyles">dom/shadowdom/ShadowRoot/applyAuthorStyles</a></td>
	<td class="Summary">Indicates whether the rules in author styles associated with the element's document apply to the shadow tree. If false (default value), the author styles are not applied to the shadow tree. If true, the author styles are applied.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/shadowdom/ShadowRoot/elementFromPoint" title="dom/shadowdom/ShadowRoot/elementFromPoint">dom/shadowdom/ShadowRoot/elementFromPoint</a></td>
	<td class="Summary">Returns an element at specified coordinates.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/shadowdom/ShadowRoot/getSelection" title="dom/shadowdom/ShadowRoot/getSelection">dom/shadowdom/ShadowRoot/getSelection</a></td>
	<td class="Summary">Returns the current selection in this ShadowRoot's shadow tree.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/shadowdom/ShadowRoot/innerHTML" title="dom/shadowdom/ShadowRoot/innerHTML">dom/shadowdom/ShadowRoot/innerHTML</a></td>
	<td class="Summary">Represents the markup of the ShadowRoot's contents.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/shadowdom/ShadowRoot/removeStyleSheet" title="dom/shadowdom/ShadowRoot/removeStyleSheet">dom/shadowdom/ShadowRoot/removeStyleSheet</a></td>
	<td class="Summary">Removes a style sheet from the ShadowRoot.</td>
</tr>
<tr class="row-even">
	<td class="Page"><a href="/wiki/dom/shadowdom/ShadowRoot/resetStyleInheritance" title="dom/shadowdom/ShadowRoot/resetStyleInheritance">dom/shadowdom/ShadowRoot/resetStyleInheritance</a></td>
	<td class="Summary">Indicates whether or not the inheritable CSS properties are set to the initial value at the shadow boundary. If false (default value), the properties continue to inherit. If true, the properties are set to initial value.</td>
</tr>
<tr class="row-odd">
	<td class="Page"><a href="/wiki/dom/shadowdom/ShadowRoot/styleSheets" title="dom/shadowdom/ShadowRoot/styleSheets">dom/shadowdom/ShadowRoot/styleSheets</a></td>
	<td class="Summary">Represents the shadow root style sheets.</td>
</tr></tbody><tfoot></tfoot></table>
<p><br>
</p>
<h3><span class="mw-headline" id="Review_content">Review content</span></h3>
<p>(0 results)
</p><p>These pages need to be reviewed by a community member familiar with the API and its usage in JavaScript. Where you find errors, please correct them; when you're finished, please remove the "Needs Review" flag.<br><br>
The following criteria are applied:
</p>
<ul><li> Topics: API</li>
<li> High-level issues: Needs Review</li></ul>
<p>Nothing found!</p>

<h2><span class="mw-headline" id="DOM_content">DOM content</span></h2>
<p>Content identified here was originally considered part of the API project, but these APIs are actually DOM APIs, and should be considered in the scope of the DOM project (yet to be started).
</p>
<table class="sortable jquery-tablesorter">
<thead><tr>
<th class="headerSort" tabindex="0" role="columnheader button" title="Sort ascending"> Priority
</th>
<th class="headerSort" tabindex="0" role="columnheader button" title="Sort ascending"> API Name
</th>
<th class="headerSort" tabindex="0" role="columnheader button" title="Sort ascending"> Source
</th>
<th class="headerSort" tabindex="0" role="columnheader button" title="Sort ascending"> Description
</th></tr></thead><tbody>
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
</td></tr></tbody><tfoot></tfoot></table>

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
<p>The methodology for creating API pages is described in <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a>.</p>
