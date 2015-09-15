---
title: API documentation proposal
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - apis/file/MSStream
    - apis/webrtc/RTCPeerConnection/addstream
uri: 'WPD:Projects/api docs'

---
## <span>Summary</span>

Some of the most immediately useful technical content that WPD can provide is for the new JavaScript APIs recently developed (or currently being developed) for web applications. These APIs provide new functionality that make web applications as robust and high-performing as desktop or native apps. By focusing on this area of technical content, we can establish WPD as the leading provider of reference information for modern web development.

The goal for this project is to bring the API documentation up to date and to make WPD the most current source for this documentation.

This proposal outlines a strategy for building out the API documentation, considering the following:

-   The current state of the "apis" namespace and extant content
-   External content that could be imported to WPD
-   New content that will help developers use the latest features of modern browsers
-   Creating, updating, and importing content
-   Template and forms changes that need to be implemented
-   Priorities and project management
-   Additional documents

## <span>Current state of the WPD API documentation</span>

With the launch of WPD in October 2012, we received a generous donation of API documentation from Microsoft; it included some 12 APIs: appcache, audio-video (media), canvas, file, geolocation, indexeddb, timing, web-messaging, web-storage, websocket, workers, and xhr. A review of this content revealled that it needed to be reorganized and ammended extensively. While this work began, some new API documentation was developed (mostly to prove the process for creating API documentation). The findings of these efforts are summarized in [WPD:Creating\_API\_pages](/WPD:Creating_API_pages).

The following table summarizes the current state of the extant API documentation on WPD. Note that all of the extant documentation will require changes associated with new templates and forms as discussed in [Templates and forms](#Templates_and_forms), below. Another (messy) representation of this content may be found on the [apis](/apis) page.

Where the current state is described as "Content complete" the API has been described with all of the pertinent aspects of the current standard specification for that API. It is organized as the API's component model, with objects, properties (attributes), methods, and events delineated accordingly. Additionally, the following checks apply:

-   The API\_Listing page has instructions for (or a link to the page with the key method or other instructions on) how to use the API.
-   The usage of the "key" method is documented and includes example code.
-   All objects, properties, methods, and events have pages in the appropriate hierarchy.
-   All pages have a summary description.
-   All relevant information from the spec is included in the documentation.
-   A link to the specification is included.
-   All pages are marked "Needs review".
-   All pages contain compatibility information if available, or are marked "Compatibility incomplete" if not.
-   All pages have topic flags of "API" and API type, e.g., "Web Audio".

The API document may or may not include code examples, and it may or may not have been reviewed; see [On-going work](/WPD:Projects/api_docs#On-going_work).

|Priority|API Name|Handler|Current State|
|:-------|:-------|:------|:------------|
|1|[appcache](/apis/appcache)|[Dave Gash](/User:Dgash)|Content complete|
|2|[audio-video](/apis/audio-video)|[Dave Gash](/User:Dgash)|Content complete|
|3|[canvas](/apis/canvas)|[Dave Gash](/User:Dgash)|Content complete|
|4|[css-regions](/apis/css-regions)|[Mike Sierra](/User:Sierra)|Content complete|
|5|[file](/apis/file)|[Dave Gash](/User:Dgash)|Content complete|
|6|[filesystem](/apis/filesystem)|[Dave Gash](/User:Dgash)|Content complete|
|7|[geolocation](/apis/geolocation)|[Dave Gash](/User:Dgash)|Content complete|
|8|[indexeddb](/apis/indexeddb)|[Lance Leonard](/User:Lleonard)|In progress|
|9|[navigation timing](/apis/navigation_timing)|[Dave Gash](/User:Dgash)|Content complete|
|10|[user timing](/apis/user_timing)|[Dave Gash](/User:Dgash)|Content complete|
|11|[resource timing](/apis/resource_timing)|[Dave Gash](/User:Dgash)|Content complete|
|12|[webaudio](/apis/webaudio)|[Dave Gash](/User:Dgash)|Content complete|
|13|[web-messaging](/apis/web-messaging)|[Dave Gash](/User:Dgash)|Content complete|
|14|[webrtc](/apis/webrtc)|[Scott Rowe](/User:Scottrowe)|Content complete|
|15|[websocket](/apis/websocket)|[Dave Gash](/User:Dgash)|Content complete|
|16|[web-storage](/apis/web-storage)|[Dave Gash](/User:Dgash)|Content complete|
|17|[workers](/apis/workers)|[Dave Gash](/User:Dgash)|Content complete|
|18|[xhr](/apis/xhr)|[Dave Gash](/User:Dgash)|Mostly complete, needs to include CORS|
|19|[quota management](/apis/quota_management)|[Dave Gash](/User:Dgash)|Content complete|
|20|[gamepad](/apis/gamepad)|[Dave Gash](/User:Dgash)|Content complete|
|21|[canvas](/apis/canvas) WebGL|[Scott Rowe](/User:Scottrowe)|Not started ([spec](https://www.khronos.org/registry/webgl/specs/1.0/WebGL))|

## <span>On-going work</span>

Although the initial layout and development of these documents is complete, a great deal of work remains in developing code examples and reviewing the content. The following tables list the pages that need these pieces in order for the documentation to attain stardom. The lists are the results of queries for content with [flags](/WPD:Editors_Guide/step_4_review_existing_content#How_to_add_a_flag) that identify needed improvements; specifically, "Examples Needed" and "Needs Review."

### <span>Examples development</span>

(375 results)

These pages need examples to thoroughly explain the documented API artifacts and their usage. When you've completed a page's example, please remove the "Needs Examples" flag.
 The following criteria are applied:

-   Topics: API

-   Content quality flags: Examples Needed

<table>
<col width="50%" />
<col width="50%" />
<thead>
<tr class="header">
<th align="left">Page</th>
<th align="left">Summary</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><a href="/apis/MediaStream/ended">apis/MediaStream/ended</a></td>
<td align="left">All tracks of the MediaStream object have ended; the MediaStream is said to be finished.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/appcache/ApplicationCache/abort">apis/appcache/ApplicationCache/abort</a></td>
<td align="left">Cancels the application cache download process. This method is intended to be used by Web applications showing their own caching progress UI, in case the user wants to stop the update (e.g., because bandwidth is limited).</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/appcache/ApplicationCache/oncached">apis/appcache/ApplicationCache/oncached</a></td>
<td align="left">The resources listed in the manifest have been downloaded, and the application is now cached.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/appcache/ApplicationCache/onchecking">apis/appcache/ApplicationCache/onchecking</a></td>
<td align="left">The user agent is checking for an update, or attempting to download the manifest for the first time. This is always the first event in the sequence.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/appcache/ApplicationCache/ondownloading">apis/appcache/ApplicationCache/ondownloading</a></td>
<td align="left">The user agent has found an update and is fetching it, or is downloading the resources listed by the manifest for the first time.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/appcache/ApplicationCache/onerror">apis/appcache/ApplicationCache/onerror</a></td>
<td align="left">Indicates an error has occurred.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/audio-video/track">apis/audio-video/track</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/audio-video/video">apis/audio-video/video</a></td>
<td align="left">HTML Video element allows creator of a HTML document or view of a Web Application to embed a video for display when a user visits the view or opens HTML document in a web browser.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/battery_status/BatteryManager/charging">apis/battery status/BatteryManager/charging</a></td>
<td align="left">Represents if the system's battery is charging.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/battery_status/BatteryManager/chargingTime">apis/battery status/BatteryManager/chargingTime</a></td>
<td align="left">Represents the time remaining in seconds until the system's battery is fully charged.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/battery_status/BatteryManager/chargingchange">apis/battery status/BatteryManager/chargingchange</a></td>
<td align="left">Fired when the battery charging state is updated.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/battery_status/BatteryManager/chargingtimechange">apis/battery status/BatteryManager/chargingtimechange</a></td>
<td align="left">Fired when the battery charging time is updated.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/battery_status/BatteryManager/dischargingTime">apis/battery status/BatteryManager/dischargingTime</a></td>
<td align="left">Represents the time remaining in seconds until the system's battery is completely discharged and the system is about to be suspended.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/battery_status/BatteryManager/dischargingtimechange">apis/battery status/BatteryManager/dischargingtimechange</a></td>
<td align="left">Fired when the battery discharging time is updated.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/battery_status/BatteryManager/level">apis/battery status/BatteryManager/level</a></td>
<td align="left">Represents the current battery level scaled from 0 to 1.0.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/battery_status/BatteryManager/levelchange">apis/battery status/BatteryManager/levelchange</a></td>
<td align="left">Fired when the battery level is updated.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/battery_status/BatteryManager/onchargingchange">apis/battery status/BatteryManager/onchargingchange</a></td>
<td align="left">Handles the chargingchange event.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/battery_status/BatteryManager/onchargingtimechange">apis/battery status/BatteryManager/onchargingtimechange</a></td>
<td align="left">Handles the chargingtimechange event.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/battery_status/BatteryManager/ondischargingtimechange">apis/battery status/BatteryManager/ondischargingtimechange</a></td>
<td align="left">Handles the dischargingtimechange event.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/battery_status/BatteryManager/onlevelchange">apis/battery status/BatteryManager/onlevelchange</a></td>
<td align="left">Handles the levelchange event.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/canvas/CanvasRenderingContext2D/drawCustomFocusRing">apis/canvas/CanvasRenderingContext2D/drawCustomFocusRing</a></td>
<td align="left">Draw a focus ring of the appropriate style along the intended path, and sets result to <em>false</em>. <strong>Removed from spec; deletion candidate.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/canvas/CanvasRenderingContext2D/drawSystemFocusRing">apis/canvas/CanvasRenderingContext2D/drawSystemFocusRing</a></td>
<td align="left">Draws a focus ring of the appropriate style along the intended path, following platform conventions. <strong>Removed from spec; deletion candidate.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/canvas/CanvasRenderingContext2D/ellipse">apis/canvas/CanvasRenderingContext2D/ellipse</a></td>
<td align="left">Draws the specified ellipse. If the object's path has any subpaths, this method adds a straight line from the last point in the subpath to the start point of the arc. Then, it adds the start and end points of the arc to the subpath, and connects them with an arc. <strong>Experimental, subject to change or removal; deletion candidate.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/file/FileError">apis/file/FileError</a></td>
<td align="left">Represents an error that occurs while using the FileReader interface. Obsolete per latest specification. Use <a href="/dom/DOMError">DOMError</a> instead.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/file/MSStreamError">apis/file/MSStreamError</a></td>
<td align="left">The MSStreamError object reports file-related errors asynchronously. Obsolete per latest specification. Use <a href="/dom/DOMError">DOMError</a> instead.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/file/MSStreamReader">apis/file/MSStreamReader</a></td>
<td align="left">Creates random access data (Blob) from an MSStream object.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/file/MSStreamReader/onabort">apis/file/MSStreamReader/onabort</a></td>
<td align="left">Indicates that the read has been aborted (for example, by calling <strong>abort()</strong>).</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/file/MSStreamReader/readAsBlob">apis/file/MSStreamReader/readAsBlob</a></td>
<td align="left">Performs an asynchronous read of an <a href="/w/index.php?title=apis/file/MSStream&amp;action=edit&amp;redlink=1">MSStream</a> object in order to create a <a href="/apis/file/Blob">Blob</a> object.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/file/MSStreamReader/readAsText">apis/file/MSStreamReader/readAsText</a></td>
<td align="left">Returns partial Blob data representing the number of bytes currently loaded (as a fraction of the total), decoded into memory according to the encoding determination.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/file/URL/revokeObjectURL">apis/file/URL/revokeObjectURL</a></td>
<td align="left">Revokes a URL from a document and frees the object associated with that URL.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/DirectoryEntry/createReader">apis/filesystem/DirectoryEntry/createReader</a></td>
<td align="left">Creates a new DirectoryReader to read Entries from this Directory. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/DirectoryEntry/getDirectory">apis/filesystem/DirectoryEntry/getDirectory</a></td>
<td align="left">Creates or looks up a directory. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/DirectoryEntry/getFile">apis/filesystem/DirectoryEntry/getFile</a></td>
<td align="left">Creates or looks up a file. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/DirectoryEntry/removeRecursively">apis/filesystem/DirectoryEntry/removeRecursively</a></td>
<td align="left">Deletes a directory and all of its contents, if any. In the event of an error [e.g. trying to delete a directory that contains a file that cannot be removed], some of the contents of the directory may be deleted. It is an error to attempt to delete the root directory of a filesystem. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/DirectoryEntrySync/createReader">apis/filesystem/DirectoryEntrySync/createReader</a></td>
<td align="left">Creates a new DirectoryReaderSync to read EntrySyncs from this DirectorySync. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/DirectoryEntrySync/getDirectory">apis/filesystem/DirectoryEntrySync/getDirectory</a></td>
<td align="left">Creates or looks up a directory. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/DirectoryEntrySync/getFile">apis/filesystem/DirectoryEntrySync/getFile</a></td>
<td align="left">Creates or looks up a file. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/DirectoryEntrySync/removeRecursively">apis/filesystem/DirectoryEntrySync/removeRecursively</a></td>
<td align="left">Deletes a directory and all of its contents, if any. In the event of an error [e.g. trying to delete a directory that contains a file that cannot be removed], some of the contents of the directory may be deleted. It is an error to attempt to delete the root directory of a filesystem. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/DirectoryReader/readEntries">apis/filesystem/DirectoryReader/readEntries</a></td>
<td align="left">Read the next block of entries from this directory. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/DirectoryReaderSync/readEntries">apis/filesystem/DirectoryReaderSync/readEntries</a></td>
<td align="left">Read the next block of entries from this directory. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/EntriesCallback/handleEvent">apis/filesystem/EntriesCallback/handleEvent</a></td>
<td align="left">Used to supply an array of Entries as a response to a user query. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/Entry/copyTo">apis/filesystem/Entry/copyTo</a></td>
<td align="left">Copy an Entry to a different location on the file system. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/Entry/filesystem">apis/filesystem/Entry/filesystem</a></td>
<td align="left">The file system on which the Entry resides. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/Entry/fullPath">apis/filesystem/Entry/fullPath</a></td>
<td align="left">The full absolute path from the root to the Entry. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/Entry/getMetadata">apis/filesystem/Entry/getMetadata</a></td>
<td align="left">Look up metadata about this Entry. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/Entry/getParent">apis/filesystem/Entry/getParent</a></td>
<td align="left">Look up the parent DirectoryEntry containing this Entry. If this Entry is the root of its filesystem, its parent is itself. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/Entry/isDirectory">apis/filesystem/Entry/isDirectory</a></td>
<td align="left">True if the Entry is a directory. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/Entry/isFile">apis/filesystem/Entry/isFile</a></td>
<td align="left">True if the Entry is a file. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/Entry/moveTo">apis/filesystem/Entry/moveTo</a></td>
<td align="left">Move an Entry to a different location on the file system. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/Entry/name">apis/filesystem/Entry/name</a></td>
<td align="left">The name of the Entry, excluding the path leading to it. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/Entry/remove">apis/filesystem/Entry/remove</a></td>
<td align="left">Deletes a file or directory. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/Entry/toURL">apis/filesystem/Entry/toURL</a></td>
<td align="left">Returns a URL that can be used to identify this Entry. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/EntryCallback/handleEvent">apis/filesystem/EntryCallback/handleEvent</a></td>
<td align="left">Used to supply an Entry as a response to a user query. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/EntrySync/copyTo">apis/filesystem/EntrySync/copyTo</a></td>
<td align="left">Copy an EntrySync to a different location on the file system. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/EntrySync/filesystem">apis/filesystem/EntrySync/filesystem</a></td>
<td align="left">The file system on which the EntrySync resides. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/EntrySync/fullPath">apis/filesystem/EntrySync/fullPath</a></td>
<td align="left">The full absolute path from the root to the EntrySync. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/EntrySync/getMetadata">apis/filesystem/EntrySync/getMetadata</a></td>
<td align="left">Look up metadata about this EntrySync. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/EntrySync/getParent">apis/filesystem/EntrySync/getParent</a></td>
<td align="left">Look up the parent DirectoryEntrySync containing this EntrySync. If this EntrySync is the root of its filesystem, its parent is itself. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/EntrySync/isDirectory">apis/filesystem/EntrySync/isDirectory</a></td>
<td align="left">True if the EntrySync is a directory. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/EntrySync/isFile">apis/filesystem/EntrySync/isFile</a></td>
<td align="left">True if the EntrySync is a file. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/EntrySync/moveTo">apis/filesystem/EntrySync/moveTo</a></td>
<td align="left">Move an EntrySync to a different location on the file system. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/EntrySync/name">apis/filesystem/EntrySync/name</a></td>
<td align="left">The name of the EntrySync, excluding the path leading to it. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/EntrySync/remove">apis/filesystem/EntrySync/remove</a></td>
<td align="left">Deletes a file or directory. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/EntrySync/toURL">apis/filesystem/EntrySync/toURL</a></td>
<td align="left">Returns a URL that can be used to identify this EntrySync. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/ErrorCallback/handleEvent">apis/filesystem/ErrorCallback/handleEvent</a></td>
<td align="left">There was an error with the request. Details are provided by the err parameter. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/FileCallback/handleEvent">apis/filesystem/FileCallback/handleEvent</a></td>
<td align="left">Used to supply a File as a response to a user query. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/FileEntry/createWriter">apis/filesystem/FileEntry/createWriter</a></td>
<td align="left">Creates a new FileWriter associated with the file that this FileEntry represents. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/FileEntry/file">apis/filesystem/FileEntry/file</a></td>
<td align="left">Returns a File that represents the current state of the file that this FileEntry represents. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/FileEntrySync/createWriter">apis/filesystem/FileEntrySync/createWriter</a></td>
<td align="left">Creates a new FileWriterSync associated with the file that this FileEntrySync represents. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/FileEntrySync/file">apis/filesystem/FileEntrySync/file</a></td>
<td align="left">Returns a File that represents the current state of the file that this FileEntrySync represents. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/FileSystem/name">apis/filesystem/FileSystem/name</a></td>
<td align="left">The name of the file system. The specifics of naming filesystems is unspecified, but a name must be unique across the list of exposed file systems. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/FileSystem/root">apis/filesystem/FileSystem/root</a></td>
<td align="left">The root directory of the file system. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/FileSystemCallback/handleEvent">apis/filesystem/FileSystemCallback/handleEvent</a></td>
<td align="left">The file system was successfully obtained. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/FileSystemSync/name">apis/filesystem/FileSystemSync/name</a></td>
<td align="left">The name of the file system. The specifics of naming filesystems is unspecified, but a name must be unique across the list of exposed file systems. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/FileSystemSync/root">apis/filesystem/FileSystemSync/root</a></td>
<td align="left">The root directory of the file system. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/FileWriterCallback/handleEvent">apis/filesystem/FileWriterCallback/handleEvent</a></td>
<td align="left">Used to supply a FileWriter as a response to a user query. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/LocalFileSystem/requestFileSystem">apis/filesystem/LocalFileSystem/requestFileSystem</a></td>
<td align="left">Requests a file system where data should be stored. You access a sandboxed file system by requesting a LocalFileSystem object using this global method, window.requestFileSystem(). <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/LocalFileSystem/resolveLocalFileSystemURL">apis/filesystem/LocalFileSystem/resolveLocalFileSystemURL</a></td>
<td align="left">Allows the user to look up the Entry for a file or directory referred to by a local URL. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/LocalFileSystemSync/requestFileSystemSync">apis/filesystem/LocalFileSystemSync/requestFileSystemSync</a></td>
<td align="left">Requests a file system where data should be stored. You access a sandboxed file system by requesting a LocalFileSystemSync object from within a web worker using this global method, window.requestFileSystemSync(). <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/LocalFileSystemSync/resolveLocalFileSystemSyncURL">apis/filesystem/LocalFileSystemSync/resolveLocalFileSystemSyncURL</a></td>
<td align="left">Allows the user to look up the Entry for a file or directory referred to by a local URL. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/filesystem/MetadataCallback/handleEvent">apis/filesystem/MetadataCallback/handleEvent</a></td>
<td align="left">Used to supply file or directory metadata as a response to a user query. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/filesystem/VoidCallback/handleEvent">apis/filesystem/VoidCallback/handleEvent</a></td>
<td align="left">Indicates success of an asynchronous method. <strong>Out of date; feature discontinued. See <a href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/image_capture/ImageCapture/getFrame">apis/image capture/ImageCapture/getFrame</a></td>
<td align="left">Gathers data from the VideoStreamTrack into a ImageData object.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/image_capture/ImageCapture/onerror">apis/image capture/ImageCapture/onerror</a></td>
<td align="left">Register/unregister for Image Capture error events of type ImageCaptureErrorEvent.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/image_capture/ImageCapture/onframegrab">apis/image capture/ImageCapture/onframegrab</a></td>
<td align="left">Register/unregister for frame capture events of type FrameGrabEvent.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/image_capture/ImageCapture/onphoto">apis/image capture/ImageCapture/onphoto</a></td>
<td align="left">Register/unregister for photo events of type BlobEvent.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/image_capture/ImageCapture/onphotosettingschange">apis/image capture/ImageCapture/onphotosettingschange</a></td>
<td align="left">Register/unregister for photo settings change events of type SettingsChangeEvent.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/image_capture/ImageCapture/photoSettingsOptions">apis/image capture/ImageCapture/photoSettingsOptions</a></td>
<td align="left">Describes current photo settings.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/image_capture/ImageCapture/setOptions">apis/image capture/ImageCapture/setOptions</a></td>
<td align="left">Applies the settings specified by the PhotoSettings object passed by parameter.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/image_capture/ImageCapture/takePhoto">apis/image capture/ImageCapture/takePhoto</a></td>
<td align="left">Gathers data from the VideoStreamTrack into a Blob containing a single still image.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/image_capture/ImageCapture/videoStreamTrack">apis/image capture/ImageCapture/videoStreamTrack</a></td>
<td align="left">The MediaStream passed into the constructor.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBCursor/delete">apis/indexeddb/IDBCursor/delete</a></td>
<td align="left">Returns an IDBRequest object and, in a separate thread, deletes the record at the cursor's position, without changing the cursor's position. Once the record is deleted, the cursor's value is set to null.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBCursor/direction">apis/indexeddb/IDBCursor/direction</a></td>
<td align="left">Indicates the direction of travel within a cursor.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBCursor/key">apis/indexeddb/IDBCursor/key</a></td>
<td align="left">The key value for the record currently displayed by the cursor.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBCursor/primaryKey">apis/indexeddb/IDBCursor/primaryKey</a></td>
<td align="left">Returns the cursor's current effective key.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBCursor/source">apis/indexeddb/IDBCursor/source</a></td>
<td align="left">On getting, returns the IDBObjectStore or IDBIndex that the cursor is iterating. This function never returns null or throws an exception, even if the cursor is currently being iterated, has iterated past its end, or its transaction is not active.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBCursor/update">apis/indexeddb/IDBCursor/update</a></td>
<td align="left">Creates a structured clone of the value parameter.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBCursorWithValue/value">apis/indexeddb/IDBCursorWithValue/value</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBDatabase/deleteObjectStore">apis/indexeddb/IDBDatabase/deleteObjectStore</a></td>
<td align="left">Destroys an object store with the given name as well as all indexes that are referencing that object store.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBDatabase/name">apis/indexeddb/IDBDatabase/name</a></td>
<td align="left">Name of the connected database.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBDatabase/objectStoreNames">apis/indexeddb/IDBDatabase/objectStoreNames</a></td>
<td align="left">Returns a list of names of the object stores currently in the connected database.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBDatabase/setVersion">apis/indexeddb/IDBDatabase/setVersion</a></td>
<td align="left">Deletion candidate. Not in spec: <a href="http://www.w3.org/TR/IndexedDB/">http://www.w3.org/TR/IndexedDB/</a></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBDatabase/transaction">apis/indexeddb/IDBDatabase/transaction</a></td>
<td align="left">Execute the steps for creating a transaction in a sychronous fashion.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBDatabase/version">apis/indexeddb/IDBDatabase/version</a></td>
<td align="left">Returns the version of the database when this IDBDatabaseSync instance was created.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBDatabaseException">apis/indexeddb/IDBDatabaseException</a></td>
<td align="left">Not supported.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBDatabaseException/code">apis/indexeddb/IDBDatabaseException/code</a></td>
<td align="left">Not supported.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBDatabaseException/message">apis/indexeddb/IDBDatabaseException/message</a></td>
<td align="left">Not supported.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBIndex/count">apis/indexeddb/IDBIndex/count</a></td>
<td align="left">Runs the steps for asynchronously executing a request and returns the IDBRequest created by these steps.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBIndex/get">apis/indexeddb/IDBIndex/get</a></td>
<td align="left">Runs the steps for asynchronously executing a request and returns the IDBRequest created by these steps.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBIndex/keyPath">apis/indexeddb/IDBIndex/keyPath</a></td>
<td align="left">The key path of this index. If null, this index is not auto-populated.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBIndex/multiEntry">apis/indexeddb/IDBIndex/multiEntry</a></td>
<td align="left">Affects how the index behaves when the result of evaluating the index's key path yields an array. If true, there is one record in the index for each item in an array of keys. If false, then there is one record for each key that is an array.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBIndex/name">apis/indexeddb/IDBIndex/name</a></td>
<td align="left">The name of this index.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBIndex/objectStore">apis/indexeddb/IDBIndex/objectStore</a></td>
<td align="left">Returns a reference to the IDBObjectStore instance for the referenced object store in this IDBIndex's transaction.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBIndex/openCursor">apis/indexeddb/IDBIndex/openCursor</a></td>
<td align="left">Creates a cursor.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBIndex/openKeyCursor">apis/indexeddb/IDBIndex/openKeyCursor</a></td>
<td align="left">Creates a cursor.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBIndex/unique">apis/indexeddb/IDBIndex/unique</a></td>
<td align="left">Provides the unique flag of this index.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBKeyRange/lower">apis/indexeddb/IDBKeyRange/lower</a></td>
<td align="left">This value is the lower-bound of the key range.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBKeyRange/lowerBound">apis/indexeddb/IDBKeyRange/lowerBound</a></td>
<td align="left">Creates and returns a new key range with lower set to lower, lowerOpen set to open, upper set to undefined and and upperOpen set to true.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBKeyRange/lowerOpen">apis/indexeddb/IDBKeyRange/lowerOpen</a></td>
<td align="left">Returns false if the lower-bound value is included in the key range. Returns true if the lower-bound value is excluded from the key range.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBKeyRange/only">apis/indexeddb/IDBKeyRange/only</a></td>
<td align="left">Creates and returns a new key range with both lower and upper set to value and both lowerOpen and upperOpen set to false.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBKeyRange/upperBound">apis/indexeddb/IDBKeyRange/upperBound</a></td>
<td align="left">Creates and returns a new key range with lower set to undefined, lowerOpen set to true, upper set to upper and and upperOpen set to open.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBKeyRange/upperOpen">apis/indexeddb/IDBKeyRange/upperOpen</a></td>
<td align="left">Returns false if the upper-bound value is included in the key range. Returns true if the upper-bound value is excluded from the key range.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBObjectStore/autoIncrement">apis/indexeddb/IDBObjectStore/autoIncrement</a></td>
<td align="left">Provides the auto increment flag for this object store.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBObjectStore/count">apis/indexeddb/IDBObjectStore/count</a></td>
<td align="left">The count method returns the number of records in an object store.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBObjectStore/get">apis/indexeddb/IDBObjectStore/get</a></td>
<td align="left">Runs the steps for asynchronously executing a request and returns the IDBRequest created by these steps.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBObjectStore/index">apis/indexeddb/IDBObjectStore/index</a></td>
<td align="left">Returns an IDBIndex representing an index that is part of the object store.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBObjectStore/indexNames">apis/indexeddb/IDBObjectStore/indexNames</a></td>
<td align="left">Provides a list of the names of indexes on objects in this object store.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBObjectStore/keyPath">apis/indexeddb/IDBObjectStore/keyPath</a></td>
<td align="left">Provides the key path of this object store.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBObjectStore/name">apis/indexeddb/IDBObjectStore/name</a></td>
<td align="left">Provides the name of this object store.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBObjectStore/openCursor">apis/indexeddb/IDBObjectStore/openCursor</a></td>
<td align="left">Creates a cursor.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBObjectStore/put">apis/indexeddb/IDBObjectStore/put</a></td>
<td align="left">Creates a structured clone of the value parameter.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBObjectStore/transaction">apis/indexeddb/IDBObjectStore/transaction</a></td>
<td align="left">Returns the transaction this object store belongs to.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBOpenDBRequest/onUpgradeNeeded">apis/indexeddb/IDBOpenDBRequest/onUpgradeNeeded</a></td>
<td align="left">The event handler for the upgrade needed event.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBOpenDBRequest/onblocked">apis/indexeddb/IDBOpenDBRequest/onblocked</a></td>
<td align="left">The event handler for the blocked event. This event is triggered when the upgradeneeded should be triggered because of a version change but the database is still in use (ie not closed) somewhere, even after the versionchange event was sent.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBRequest/error">apis/indexeddb/IDBRequest/error</a></td>
<td align="left">The error codes returned under certain conditions.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBRequest/onerror">apis/indexeddb/IDBRequest/onerror</a></td>
<td align="left">The event handler for the error event.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBRequest/onsuccess">apis/indexeddb/IDBRequest/onsuccess</a></td>
<td align="left">The event handler for the success event.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBRequest/readyState">apis/indexeddb/IDBRequest/readyState</a></td>
<td align="left">The state of the request. Every request starts in the pending state. The state changes to done when the request completes successfully or when an error occurs.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBRequest/result">apis/indexeddb/IDBRequest/result</a></td>
<td align="left">Returns the result of the request. If the the request failed and the result is not available, the DOMException InvalidStateError exception is thrown.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBRequest/source">apis/indexeddb/IDBRequest/source</a></td>
<td align="left">The source of the request, such as an Index or a ObjectStore. If no source exists (such as when calling indexedDB.open()), it returns null.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBRequest/transaction">apis/indexeddb/IDBRequest/transaction</a></td>
<td align="left">The transaction for the request. This property can be null for certain requests, such as for request returned from IDBFactory.open (You're just connecting to a database, so there is no transaction to return).</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBTransaction/db">apis/indexeddb/IDBTransaction/db</a></td>
<td align="left">The database connection of which this transaction is a part.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBTransaction/error">apis/indexeddb/IDBTransaction/error</a></td>
<td align="left">Null if the transaction is not finished, is finished and successfully committed, or was aborted with the abort() function. Returns the same DOMError as the request object which caused the transaction to be aborted due to a failed request, or a DOMError for the transaction failure not due to a failed request (such as QuotaExceededError or UnknownError).</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBTransaction/mode">apis/indexeddb/IDBTransaction/mode</a></td>
<td align="left">The mode for isolating access to data in the object stores that are in the scope of the transaction. For possible values, see Return Value, below. The default value is readonly.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBTransaction/objectStore">apis/indexeddb/IDBTransaction/objectStore</a></td>
<td align="left">Returns an object store that has already been added to the scope of this transaction.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBTransaction/onabort">apis/indexeddb/IDBTransaction/onabort</a></td>
<td align="left">The event handler for the onabort event.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBTransaction/oncomplete">apis/indexeddb/IDBTransaction/oncomplete</a></td>
<td align="left">The event handler for the oncomplete event.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBTransaction/onerror">apis/indexeddb/IDBTransaction/onerror</a></td>
<td align="left">The event handler for the error event.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBVersionChangeEvent/newVersion">apis/indexeddb/IDBVersionChangeEvent/newVersion</a></td>
<td align="left">Returns the new version of the database, which is the version specified by the open request.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/IDBVersionChangeEvent/oldVersion">apis/indexeddb/IDBVersionChangeEvent/oldVersion</a></td>
<td align="left">Returns the old version of the database.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/indexeddb/IDBVersionChangeRequest/onblocked">apis/indexeddb/IDBVersionChangeRequest/onblocked</a></td>
<td align="left">The event handler for the blocked event.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/indexeddb/indexedDB/open">apis/indexeddb/indexedDB/open</a></td>
<td align="left">Opens a database. See <a href="/apis/indexeddb/IDBFactory/open">apis/indexeddb/IDBFactory/open</a></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStream/addtrack">apis/media capture and streams/MediaStream/addtrack</a></td>
<td align="left">This event is fired when a track is added to the MediaStream.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStream/ended">apis/media capture and streams/MediaStream/ended</a></td>
<td align="left">Is true if the MediaStream has finished, false otherwise.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStream/id">apis/media capture and streams/MediaStream/id</a></td>
<td align="left">A globally unique identifier string, initialized when the MediaStream object is created.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStream/onaddtrack">apis/media capture and streams/MediaStream/onaddtrack</a></td>
<td align="left">Handles the addtrack event when fired on the MediaStream object.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStream/onended">apis/media capture and streams/MediaStream/onended</a></td>
<td align="left">Handles the ended event when fired on the MediaStream object.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStream/onremovetrack">apis/media capture and streams/MediaStream/onremovetrack</a></td>
<td align="left">Handles the removetrack event when fired on the MediaStream object.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStream/removetrack">apis/media capture and streams/MediaStream/removetrack</a></td>
<td align="left">This event is fired when a track is removed from the MediaStream.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/applyConstraints">apis/media capture and streams/MediaStreamTrack/applyConstraints</a></td>
<td align="left">Replaces all existing constraints with the provided constraints, if existing constraints exist. Otherwise, it applies the newly provided constraints to the track.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/capabilities">apis/media capture and streams/MediaStreamTrack/capabilities</a></td>
<td align="left">Returns a dictionary with all of the capabilities for the track type.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/clone">apis/media capture and streams/MediaStreamTrack/clone</a></td>
<td align="left">Clones the given MediaStreamTrack.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/constraints">apis/media capture and streams/MediaStreamTrack/constraints</a></td>
<td align="left">Returns the complete constraints object associated with the track. If no mandatory constraints have been defined, the mandatory field will not be present (it will be undefined). If no optional constraints have been defined, the optional field will not be present (it will be undefined). If neither optional, nor mandatory constraints have been created, the value null is returned.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/enabled">apis/media capture and streams/MediaStreamTrack/enabled</a></td>
<td align="left">Enables the track if the new value is true, and disable it otherwise.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/id">apis/media capture and streams/MediaStreamTrack/id</a></td>
<td align="left">A globally unique identifier string, initialized when the MediaStreamTrack object is created.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/kind">apis/media capture and streams/MediaStreamTrack/kind</a></td>
<td align="left">Returns the string &quot;audio&quot; if the object represents an audio track or &quot;video&quot; if object represents a video track.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/label">apis/media capture and streams/MediaStreamTrack/label</a></td>
<td align="left">Returns the label of the object’s corresponding track, if any. If the corresponding track has or had no label, it returns the empty string.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/mute">apis/media capture and streams/MediaStreamTrack/mute</a></td>
<td align="left">This event fires when the MediaStreamTrack object's source is temporarily unable to provide data.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/muted">apis/media capture and streams/MediaStreamTrack/muted</a></td>
<td align="left">Returns true if the track is muted, and false otherwise.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/onended">apis/media capture and streams/MediaStreamTrack/onended</a></td>
<td align="left">Handles the ended event when fired on the MediaStreamTrack object.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/onmute">apis/media capture and streams/MediaStreamTrack/onmute</a></td>
<td align="left">Handles the mute event when fired on the MediaStreamTrack object.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/onoverconstrained">apis/media capture and streams/MediaStreamTrack/onoverconstrained</a></td>
<td align="left">Handles the overcontrained event when fired on the MediaStreamTrack object.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/onstarted">apis/media capture and streams/MediaStreamTrack/onstarted</a></td>
<td align="left">Handles the started event when fired on the MediaStreamTrack object.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/onunmute">apis/media capture and streams/MediaStreamTrack/onunmute</a></td>
<td align="left">Handles the unmute event when fired on the MediaStreamTrack object.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/overconstrained">apis/media capture and streams/MediaStreamTrack/overconstrained</a></td>
<td align="left">This event fires asynchronously for each affected track (when multiple tracks share the same source) after the user agent has evaluated the current constraints against a given sourceId and is not able to configure the source within the limitations established by the union of imposed constraints.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/readonly">apis/media capture and streams/MediaStreamTrack/readonly</a></td>
<td align="left">Returns true If the track (audio or video) is backed by a read-only source such as a file, or the track source is a local microphone or camera, but is shared so that this track cannot modify any of the source's settings. Returns false otherwise.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/readyState">apis/media capture and streams/MediaStreamTrack/readyState</a></td>
<td align="left">Returns the state of the track.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/remote">apis/media capture and streams/MediaStreamTrack/remote</a></td>
<td align="left">Returns true if the track is sourced by an RTCPeerConnection. Returns false otherwise.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/started">apis/media capture and streams/MediaStreamTrack/started</a></td>
<td align="left">This event fires when the MediaStreamTrack object has just transitioned from the &quot;new&quot; readyState to another state.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/states">apis/media capture and streams/MediaStreamTrack/states</a></td>
<td align="left">Returns an object containing all the state variables associated with the allowed constraints.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/stop">apis/media capture and streams/MediaStreamTrack/stop</a></td>
<td align="left">Permanently stop the generation of data for track's source.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/media_capture_and_streams/MediaStreamTrack/unmute">apis/media capture and streams/MediaStreamTrack/unmute</a></td>
<td align="left">This event fires when the MediaStreamTrack object's source is live again after having been temporarily unable to provide data.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/media_capture_and_streams/ended">apis/media capture and streams/ended</a></td>
<td align="left">This event is fired when a MediaStream is stopped.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/network_information/Connection">apis/network information/Connection</a></td>
<td align="left">Provides a handle to the device's connection information.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/network_information/Connection/bandwidth">apis/network information/Connection/bandwidth</a></td>
<td align="left">An estimation of the current bandwidth in MB/s (Megabytes per seconds) available.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/network_information/Connection/change">apis/network information/Connection/change</a></td>
<td align="left">Fires when the Connection changes.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/network_information/Connection/metered">apis/network information/Connection/metered</a></td>
<td align="left">A connection is metered when the user's connection is subject to a limitation from his Internet Service Provider strong enough to request web applications to be careful with the bandwidth usage.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/network_information/Connection/onchange">apis/network information/Connection/onchange</a></td>
<td align="left">Handles the change event, fired when the Connection changes.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/network_information/NetworkInformation/connection">apis/network information/NetworkInformation/connection</a></td>
<td align="left">The object from which connection information is accessed.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/quota_management/StorageQuota">apis/quota management/StorageQuota</a></td>
<td align="left">Provides a means to query and request storage usage and quota information.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/quota_management/queryUsageAndQuota">apis/quota management/queryUsageAndQuota</a></td>
<td align="left">Queries the current usage (how much data is stored) and quota available for the requesting application.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/quota_management/requestQuota">apis/quota management/requestQuota</a></td>
<td align="left">Requests a new quota for the requesting application.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/web_animations/AnimationPlayer/currentTime">apis/web animations/AnimationPlayer/currentTime</a></td>
<td align="left">The current time of this player unless this player has a pending pause task, in which case this attribute returns null.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/web_animations/AnimationPlayer/reverse">apis/web animations/AnimationPlayer/reverse</a></td>
<td align="left">Inverts the playback rate of this player and seeks to the start of the source content if if has finished playing in the reversed direction using the reverse a player procedure for this object.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webaudio/AudioContext/activeSourceCount">apis/webaudio/AudioContext/activeSourceCount</a></td>
<td align="left">The number of <a href="/apis/webaudio/AudioBufferSourceNode"><strong>AudioBufferSourceNode</strong>s</a> that are currently playing. <strong>Out of date; removed from spec. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webaudio/AudioContext/createWaveTable">apis/webaudio/AudioContext/createWaveTable</a></td>
<td align="left">Creates a <a href="/apis/webaudio/WaveTable"><strong>WaveTable</strong></a> representing a waveform containing arbitrary harmonic content. The real and imag parameters must be of type <strong>Float32Array</strong> of equal lengths greater than zero and less than or equal to 4096 or an exception will be thrown. These parameters specify the Fourier coefficients of a Fourier series representing the partials of a periodic waveform. The created <a href="/apis/webaudio/WaveTable"><strong>WaveTable</strong></a> will be used with an <a href="/apis/webaudio/OscillatorNode"><strong>OscillatorNode</strong></a> and will represent a normalized time-domain waveform having maximum absolute peak value of 1. Another way of saying this is that the generated waveform of an <a href="/apis/webaudio/OscillatorNode"><strong>OscillatorNode</strong></a> will have maximum peak value at 0dBFS. Conveniently, this corresponds to the full-range of the signal values used by the Web Audio API. Because the <a href="/apis/webaudio/WaveTable"><strong>WaveTable</strong></a> will be normalized on creation, the real and imag parameters represent relative values. <strong>Out of date; removed from spec. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webaudio/AudioDestinationNode/numberOfChannels">apis/webaudio/AudioDestinationNode/numberOfChannels</a></td>
<td align="left">The number of channels of the destination's input. This value will default to 2, and may be set to any non-zero value less than or equal to <a href="/apis/webaudio/AudioDestinationNode/maxChannelCount"><strong>maxChannelCount</strong></a>. An exception will be thrown if this value is not within the valid range. <strong>Not in spec; deletion candidate. Possibly confused with AudioBuffer/numberOfChannels. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webaudio/AudioParam/computedValue">apis/webaudio/AudioParam/computedValue</a></td>
<td align="left">The final value controlling the audio DSP, calculated at each time, which is either the value set directly to the value attribute or, if there are any scheduled parameter changes (automation events), the value as calculated from these events. <strong>Not in spec; deletion candidate. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webaudio/AudioParam/maxValue">apis/webaudio/AudioParam/maxValue</a></td>
<td align="left">Nominal maximum value. The value attribute may be set higher than this value. <strong>Not in spec; deletion candidate. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webaudio/AudioParam/minValue">apis/webaudio/AudioParam/minValue</a></td>
<td align="left">Nominal minimum value. The value attribute may be set lower than this value. <strong>Not in spec; deletion candidate. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webaudio/AudioProcessingEvent/inputBuffer">apis/webaudio/AudioProcessingEvent/inputBuffer</a></td>
<td align="left">An <a href="/apis/webaudio/AudioBuffer"><strong>AudioBuffer</strong></a> containing the input audio data. It will have a number of channels equal to the <strong>numberOfInputChannels</strong> parameter of the <a href="/apis/webaudio/AudioContext/createScriptProcessor"><strong>createScriptProcessor()</strong></a> method. This <a href="/apis/webaudio/AudioBuffer"><strong>AudioBuffer</strong></a> is only valid while in the scope of the <a href="/apis/webaudio/ScriptProcessorNode/onaudioprocess"><strong>onaudioprocess</strong></a> function. Its values will be meaningless outside of this scope. <strong>Deprecated; deletion candidate. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webaudio/AudioProcessingEvent/node">apis/webaudio/AudioProcessingEvent/node</a></td>
<td align="left">The <a href="/apis/webaudio/ScriptProcessorNode"><strong>ScriptProcessorNode</strong></a> associated with this processing event. <strong>Deprecated; deletion candidate. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webaudio/AudioProcessingEvent/outputBuffer">apis/webaudio/AudioProcessingEvent/outputBuffer</a></td>
<td align="left">An <a href="/apis/webaudio/AudioBuffer"><strong>AudioBuffer</strong></a> where the output audio data should be written. It will have a number of channels equal to the <strong>numberOfOutputChannels</strong> parameter of the <a href="/apis/webaudio/AudioContext/createScriptProcessor"><strong>createScriptProcessor()</strong></a> method. Script code within the scope of the <a href="/apis/webaudio/ScriptProcessorNode/onaudioprocess"><strong>onaudioprocess</strong></a> function is expected to modify the <strong>Float32Array</strong> arrays representing channel data in this <a href="/apis/webaudio/AudioBuffer"><strong>AudioBuffer</strong></a>. Any script modifications to this <a href="/apis/webaudio/AudioBuffer"><strong>AudioBuffer</strong></a> outside of this scope will not produce any audible effects. <strong>Deprecated; deletion candidate. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webaudio/AudioProcessingEvent/playbackTime">apis/webaudio/AudioProcessingEvent/playbackTime</a></td>
<td align="left">The time when the audio will be played, in the same time coordinate system as <a href="/apis/webaudio/AudioContext/currentTime"><strong>AudioContext.currentTime</strong></a>. <a href="/apis/webaudio/AudioProcessingEvent/playbackTime"><strong>playbackTime</strong></a> allows for very tight synchronization between processing directly in JavaScript with the other events in the context's rendering graph. <strong>Deprecated; deletion candidate. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webaudio/OscillatorNode/playbackState">apis/webaudio/OscillatorNode/playbackState</a></td>
<td align="left">The playback state, initialized to UNSCHEDULED_STATE, progressing through SCHEDULED_STATE, PLAYING_STATE, and FINISHED_STATE. <strong>Not in spec; deletion candidate. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webaudio/OscillatorNode/setWaveTable">apis/webaudio/OscillatorNode/setWaveTable</a></td>
<td align="left">Sets an arbitrary custom periodic waveform given a <a href="/apis/webaudio/WaveTable"><strong>WaveTable</strong></a>. <strong>Not in spec; deletion candidate. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webaudio/ScriptProcessorNode/bufferSize">apis/webaudio/ScriptProcessorNode/bufferSize</a></td>
<td align="left">The size of the buffer (in sample-frames) which needs to be processed each time <a href="/apis/webaudio/ScriptProcessorNode/onaudioprocess"><strong>onaudioprocess</strong></a> is called. Legal values are 256, 512, 1024, 2048, 4096, 8192, and 16384. <strong>Deprecated; deletion candidate. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webaudio/ScriptProcessorNode/onaudioprocess">apis/webaudio/ScriptProcessorNode/onaudioprocess</a></td>
<td align="left">An event listener which is called periodically for audio processing. An event of type <a href="/apis/webaudio/AudioProcessingEvent"><strong>AudioProcessingEvent</strong></a> will be passed to the event handler. <strong>Deprecated; deletion candidate. See <a href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</strong></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/LocalMediaStream/stop">apis/webrtc/LocalMediaStream/stop</a></td>
<td align="left">Permanently halts the generation of data for the tracks' sources and removes the references to the sources.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStream/audioTracks">apis/webrtc/MediaStream/audioTracks</a></td>
<td align="left">The MediaStreamTrackList object representing the audio tracks.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStream/ended">apis/webrtc/MediaStream/ended</a></td>
<td align="left">True if the ended event has fired on the MediaStream object.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStream/label">apis/webrtc/MediaStream/label</a></td>
<td align="left">A globally unique identifier (GUID) of 36 characters that describes the media stream.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStream/onended">apis/webrtc/MediaStream/onended</a></td>
<td align="left">Handles the ended event when fired on the MediaStream object.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStream/videoTracks">apis/webrtc/MediaStream/videoTracks</a></td>
<td align="left">The MediaStreamTrackList object representing the video tracks.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStreamTrack">apis/webrtc/MediaStreamTrack</a></td>
<td align="left">A MediaStreamTrack is one of two kinds, audio or video, and represents the media source, such as a camera.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStreamTrack/enabled">apis/webrtc/MediaStreamTrack/enabled</a></td>
<td align="left">True if the track is still associated with its source.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStreamTrack/ended">apis/webrtc/MediaStreamTrack/ended</a></td>
<td align="left">The MediaStreamTrack object's source will not provide data; this may be caused by the following:
<ul>
<li>the user has revoked permissions on the application</li>
<li>the source device has been disconnected</li>
<li>the remote peer has stopped sending data</li>
<li>the stop() method was invoked</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStreamTrack/kind">apis/webrtc/MediaStreamTrack/kind</a></td>
<td align="left">The value, either <strong>audio</strong> or <strong>video</strong> for the source of the track.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStreamTrack/label">apis/webrtc/MediaStreamTrack/label</a></td>
<td align="left">A user agent-assigned string that identifies the track source, as in &quot;internal microphone.&quot;</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStreamTrack/muted">apis/webrtc/MediaStreamTrack/muted</a></td>
<td align="left">The MediaStreamTrack object's source is temporarily unable to provide data.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStreamTrack/onended">apis/webrtc/MediaStreamTrack/onended</a></td>
<td align="left">Handles the ended event when fired on the MediaStream object.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStreamTrack/onmute">apis/webrtc/MediaStreamTrack/onmute</a></td>
<td align="left">Handles the muted event when fired on the MediaStream object.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStreamTrack/readyState">apis/webrtc/MediaStreamTrack/readyState</a></td>
<td align="left">The track's ready state; values.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStreamTrack/unmuted">apis/webrtc/MediaStreamTrack/unmuted</a></td>
<td align="left">The MediaStreamTrack object's source has resumed providing data.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStreamTrackList">apis/webrtc/MediaStreamTrackList</a></td>
<td align="left">A MediaStream has two MediaStreamTrackList objects, one for the video tracks and one for the audio tracks.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStreamTrackList/add">apis/webrtc/MediaStreamTrackList/add</a></td>
<td align="left">Adds a MediaStreamTrack to this track list.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStreamTrackList/addtrack">apis/webrtc/MediaStreamTrackList/addtrack</a></td>
<td align="left">A MediaStreamTrack has been added to the list.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStreamTrackList/item">apis/webrtc/MediaStreamTrackList/item</a></td>
<td align="left">Returns the MediaStreamTrack at the specified index value.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStreamTrackList/length">apis/webrtc/MediaStreamTrackList/length</a></td>
<td align="left">The number of tracks in the list.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStreamTrackList/onaddtrack">apis/webrtc/MediaStreamTrackList/onaddtrack</a></td>
<td align="left">Handles the addtrack event.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStreamTrackList/onremovetrack">apis/webrtc/MediaStreamTrackList/onremovetrack</a></td>
<td align="left">Handles the removetrack event.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/MediaStreamTrackList/remove">apis/webrtc/MediaStreamTrackList/remove</a></td>
<td align="left">Removes a MediaStreamTrack from this track list.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/MediaStreamTrackList/removetrack">apis/webrtc/MediaStreamTrackList/removetrack</a></td>
<td align="left">A MediaStreamTrack has been removed from the list.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCDataChannel/binaryType">apis/webrtc/RTCDataChannel/binaryType</a></td>
<td align="left">Returns the value to which it was last set; on creation, must be initialized to the string &quot;blob&quot;.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCDataChannel/bufferedAmount">apis/webrtc/RTCDataChannel/bufferedAmount</a></td>
<td align="left">Returns the number of bytes of application data that have been queued using send() but that (as of the last time the event loop started executing a task) have not yet been transmitted to the network.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCDataChannel/close">apis/webrtc/RTCDataChannel/close</a></td>
<td align="left">Closes the RTCDataChannel.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCDataChannel/label">apis/webrtc/RTCDataChannel/label</a></td>
<td align="left">A unique identifier that can be used to distinguish this RTCDataChannel object from other RTCDataChannel objects.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCDataChannel/onclose">apis/webrtc/RTCDataChannel/onclose</a></td>
<td align="left">An event listener to be called when an RTCDataChannel is closed.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCDataChannel/onerror">apis/webrtc/RTCDataChannel/onerror</a></td>
<td align="left">An event listener to be called when an error occurs.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCDataChannel/onmessage">apis/webrtc/RTCDataChannel/onmessage</a></td>
<td align="left">An event listener to be called when a message is received.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCDataChannel/onopen">apis/webrtc/RTCDataChannel/onopen</a></td>
<td align="left">An event listener to be called when an RTCDataChannel is opened.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCDataChannel/readyState">apis/webrtc/RTCDataChannel/readyState</a></td>
<td align="left">Represents the state of the RTCDataChannel object.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCDataChannel/reliable">apis/webrtc/RTCDataChannel/reliable</a></td>
<td align="left">Returns true if the RTCDataChannel is reliable, and false otherwise.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCDataChannel/send">apis/webrtc/RTCDataChannel/send</a></td>
<td align="left">Sends a message (<em>data</em>) on the RTCDataChannel’s underlying data transport.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCIceCandidate">apis/webrtc/RTCIceCandidate</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection">apis/webrtc/RTCPeerConnection</a></td>
<td align="left">Provides for the connection between remote peers, the transmission of locally generated MediaStream data and arbitrary data between peers.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/addIceCandidate">apis/webrtc/RTCPeerConnection/addIceCandidate</a></td>
<td align="left">Provides a remote candidate to the ICE agent.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/close">apis/webrtc/RTCPeerConnection/close</a></td>
<td align="left">Closes a peer connection, stops all active ICE processing and any active streaming, and releases any relevant resources such as TURN permissions.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/createAnswer">apis/webrtc/RTCPeerConnection/createAnswer</a></td>
<td align="left">Creates a session description compatible with the remote configuration.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/createOffer">apis/webrtc/RTCPeerConnection/createOffer</a></td>
<td align="left">Creates a session description compatible with the local configuration.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/getIdentityAssertion">apis/webrtc/RTCPeerConnection/getIdentityAssertion</a></td>
<td align="left">Provides an identity assertion.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/getStats">apis/webrtc/RTCPeerConnection/getStats</a></td>
<td align="left">Retrieves status information for a given <a href="/apis/webrtc/MediaStreamTrack">MediaStreamTrack</a>.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/iceGatheringState">apis/webrtc/RTCPeerConnection/iceGatheringState</a></td>
<td align="left">Returns the gathering state of the ICE agent.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/iceState">apis/webrtc/RTCPeerConnection/iceState</a></td>
<td align="left">Returns the ICE state of the ICE agent.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/icecandidate">apis/webrtc/RTCPeerConnection/icecandidate</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/icechange">apis/webrtc/RTCPeerConnection/icechange</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/identityresult">apis/webrtc/RTCPeerConnection/identityresult</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/localDescription">apis/webrtc/RTCPeerConnection/localDescription</a></td>
<td align="left">Returns the <a href="/apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> most recently passed to the <a href="/apis/webrtc/RTCPeerConnection/setLocalDescription">setLocalDescription()</a> method along with any local candidate descriptions generated since the method was called.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/localStreams">apis/webrtc/RTCPeerConnection/localStreams</a></td>
<td align="left">Returns an array of <a href="/apis/webrtc/MediaStream">MediaStream</a> objects added to the connection with <a href="/apis/webrtc/RTCPeerConnection/addStream">addStream()</a>.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/negotiationneeded">apis/webrtc/RTCPeerConnection/negotiationneeded</a></td>
<td align="left">The browser anticipates a session negotiation is required. It is triggered whenever <a href="/apis/webrtc/RTCPeerConnection/addStream">addStream</a>, <a href="/apis/webrtc/RTCPeerConnection/removeStream">removeStream</a> or <a href="/apis/webrtc/RTCPeerConnection/setIdentityProvider">setIdentityProvider</a> methods were called successfully and <a href="/apis/webrtc/RTCPeerConnection">RTCPeerConnection</a> signalingState is <code>stable</code> .</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/onaddstream">apis/webrtc/RTCPeerConnection/onaddstream</a></td>
<td align="left">Handles the <a href="/w/index.php?title=apis/webrtc/RTCPeerConnection/addstream&amp;action=edit&amp;redlink=1">addstream</a> event fired when <a href="/apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a> is called.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/ondatachannel">apis/webrtc/RTCPeerConnection/ondatachannel</a></td>
<td align="left">Handles the <strong>datachannel</strong> event.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/ongatheringchange">apis/webrtc/RTCPeerConnection/ongatheringchange</a></td>
<td align="left">Handles the <strong>gatheringchange</strong> event for a change to the <a href="/apis/webrtc/RTCPeerConnection/iceGatheringState">iceGatheringState</a> property.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/onicecandidate">apis/webrtc/RTCPeerConnection/onicecandidate</a></td>
<td align="left">Handles the <a href="/apis/webrtc/RTCPeerConnection/icechange">icechange</a> event for a change to the <a href="/apis/webrtc/RTCPeerConnection/iceState">apis/webrtc/RTCPeerConnection/iceState</a> property. It is called any time there is a new ICE candidate added to a previous offer or answer.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/onicechange">apis/webrtc/RTCPeerConnection/onicechange</a></td>
<td align="left">Handles the <a href="/apis/webrtc/RTCPeerConnection/icechange">icechange</a> event. It is called any time the <a href="/apis/webrtc/RTCPeerConnection/iceState">iceState</a> changes.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/onidentityresult">apis/webrtc/RTCPeerConnection/onidentityresult</a></td>
<td align="left">Handles the <a href="/apis/webrtc/RTCPeerConnection/identityresult">identityresult</a> event for the success or failure of an identity verification.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/onnegotiationneeded">apis/webrtc/RTCPeerConnection/onnegotiationneeded</a></td>
<td align="left">Handles the <a href="/apis/webrtc/RTCPeerConnection/negotiationneeded">negotiationneeded</a> event.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/onopen">apis/webrtc/RTCPeerConnection/onopen</a></td>
<td align="left">Handles the <a href="/apis/webrtc/RTCPeerConnection/open">open</a> event. Testing.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/onremovestream">apis/webrtc/RTCPeerConnection/onremovestream</a></td>
<td align="left">Handles the <a href="/apis/webrtc/RTCPeerConnection/removeStream">removeStream</a> event for when <a href="/apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a> is called to remove a <a href="/apis/webrtc/MediaStream">MediaStream</a> object on the remote peer.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/onstatechange">apis/webrtc/RTCPeerConnection/onstatechange</a></td>
<td align="left">Handles the <a href="/apis/webrtc/RTCPeerConnection/statechange">statechange</a> event for when the <a href="/apis/webrtc/RTCPeerConnection/readyState">readyState</a> property is changed, i.e. with a call to <a href="/apis/webrtc/RTCPeerConnection/setLocalDescription">setLocalDescription()</a> or <a href="/apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a>. The event does not fire when a new RTCPeerConnection object is created.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/open">apis/webrtc/RTCPeerConnection/open</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/readyState">apis/webrtc/RTCPeerConnection/readyState</a></td>
<td align="left">Returns the ready state of the peer connection.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/remoteDescription">apis/webrtc/RTCPeerConnection/remoteDescription</a></td>
<td align="left">Returns the <a href="/apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> most recently passed to the <a href="/apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a> method along with any remote candidate descriptions supplied with <a href="/apis/webrtc/RTCPeerConnection/addIceCandidate">addIceCandidate()</a>. Returns null if the remote description has not been set.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/remoteStreams">apis/webrtc/RTCPeerConnection/remoteStreams</a></td>
<td align="left">Returns an array of <a href="/apis/webrtc/MediaStream">MediaStream</a> objects added to the connection by the remote peer. This array is updated when the <a href="/apis/webrtc/RTCPeerConnection/onaddstream">addstream</a> and <a href="/apis/webrtc/RTCPeerConnection/removeStream">removestream</a> events are fired.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/removeStream">apis/webrtc/RTCPeerConnection/removeStream</a></td>
<td align="left">Removes the given stream from the <a href="/apis/webrtc/RTCPeerConnection/localStreams">localStreams</a> array in the RTCPeerConnection and fires the <a href="/apis/webrtc/RTCPeerConnection/negotiationneeded">negotiationneeded</a> event.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/setIdentityProvider">apis/webrtc/RTCPeerConnection/setIdentityProvider</a></td>
<td align="left">Sets the identity provider. Not required if the browser is already configured for an identity provider.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/setLocalDescription">apis/webrtc/RTCPeerConnection/setLocalDescription</a></td>
<td align="left">Applies the supplied <a href="/apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> to the local description.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/setRemoteDescription">apis/webrtc/RTCPeerConnection/setRemoteDescription</a></td>
<td align="left">Applies the supplied <a href="/apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> to the remote description.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/statechange">apis/webrtc/RTCPeerConnection/statechange</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCPeerConnection/updateIce">apis/webrtc/RTCPeerConnection/updateIce</a></td>
<td align="left">Updates the ICE agent process that gathers local candidates and remote candidates.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/webrtc/RTCSessionDescription/sdp">apis/webrtc/RTCSessionDescription/sdp</a></td>
<td align="left">The string representation of the SDP object.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/webrtc/RTCSessionDescription/type">apis/webrtc/RTCSessionDescription/type</a></td>
<td align="left">The type of SDP object this RTCSessionDescription represents.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/websocket/CloseEvent/code">apis/websocket/CloseEvent/code</a></td>
<td align="left">The WebSocket connection close code provided by the server.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/websocket/CloseEvent/reason">apis/websocket/CloseEvent/reason</a></td>
<td align="left">Indicates the reason the server closed the WebSocket connection.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/websocket/WebSocket/close">apis/websocket/WebSocket/close</a></td>
<td align="left">Closes the WebSocket connection or connection attempt, if any.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/websocket/WebSocket/extensions">apis/websocket/WebSocket/extensions</a></td>
<td align="left">The extensions selected by the server.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/websocket/WebSocket/protocol">apis/websocket/WebSocket/protocol</a></td>
<td align="left">Indicates the name of the sub-protocol the server selected.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/workers/Worker/onerror">apis/workers/Worker/onerror</a></td>
<td align="left">An event listener to be called when an error occurs.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/workers/Worker/onmessage">apis/workers/Worker/onmessage</a></td>
<td align="left">An event listener to be called when a message is received from the worker.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/workers/Worker/postMessage">apis/workers/Worker/postMessage</a></td>
<td align="left">Posts a message to the worker with which the object is associated.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/workers/Worker/terminate">apis/workers/Worker/terminate</a></td>
<td align="left">Immediately terminates the worker with which the object is associated.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/workers/WorkerGlobalScope/close">apis/workers/WorkerGlobalScope/close</a></td>
<td align="left">Discards any pending tasks and immediately closes the worker.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/workers/WorkerGlobalScope/importScripts">apis/workers/WorkerGlobalScope/importScripts</a></td>
<td align="left">Fetches one or more script resources, identified by absolute URLs.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/workers/WorkerGlobalScope/location">apis/workers/WorkerGlobalScope/location</a></td>
<td align="left">Returns the WorkerLocation object created for the WorkerGlobalScope object when the worker was created.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/workers/WorkerGlobalScope/navigator">apis/workers/WorkerGlobalScope/navigator</a></td>
<td align="left">Returns an instance of the WorkerNavigator interface, which represents the identity and state of the user agent (the client).</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/workers/WorkerGlobalScope/onerror">apis/workers/WorkerGlobalScope/onerror</a></td>
<td align="left">An event listener to be called when an error occurs.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/workers/WorkerGlobalScope/onoffline">apis/workers/WorkerGlobalScope/onoffline</a></td>
<td align="left">An event listener to be called when the worker goes offline.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/workers/WorkerGlobalScope/ononline">apis/workers/WorkerGlobalScope/ononline</a></td>
<td align="left">An event listener to be called when the worker goes online.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/workers/WorkerGlobalScope/self">apis/workers/WorkerGlobalScope/self</a></td>
<td align="left">Returns the WorkerGlobalScope object.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/workers/WorkerLocation/href">apis/workers/WorkerLocation/href</a></td>
<td align="left">Returns the absolute URL that the object represents.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/xhr/XMLHttpRequest/abort-event">apis/xhr/XMLHttpRequest/abort-event</a></td>
<td align="left">When the request has been aborted. For instance, by invoking the abort() method.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/xhr/XMLHttpRequest/error">apis/xhr/XMLHttpRequest/error</a></td>
<td align="left">When the request has failed.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/xhr/XMLHttpRequest/getResponseHeader">apis/xhr/XMLHttpRequest/getResponseHeader</a></td>
<td align="left">Returns the string containing the text of the specified header, or null if the response has not been received or the header does not exist.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/xhr/XMLHttpRequest/load">apis/xhr/XMLHttpRequest/load</a></td>
<td align="left">When the request has successfully completed.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/xhr/XMLHttpRequest/loadend">apis/xhr/XMLHttpRequest/loadend</a></td>
<td align="left">When the request has completed (either in success or failure).</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/xhr/XMLHttpRequest/loadstart">apis/xhr/XMLHttpRequest/loadstart</a></td>
<td align="left">When the request starts.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/xhr/XMLHttpRequest/progress">apis/xhr/XMLHttpRequest/progress</a></td>
<td align="left">While sending and loading data.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/xhr/XMLHttpRequest/setRequestHeader">apis/xhr/XMLHttpRequest/setRequestHeader</a></td>
<td align="left">Sets the value of an XMLHttpRequest header.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/apis/xhr/XMLHttpRequest/status">apis/xhr/XMLHttpRequest/status</a></td>
<td align="left">Returns the HTTP result code (status) of the response to the request.</td>
</tr>
<tr class="even">
<td align="left"><a href="/apis/xhr/XMLHttpRequest/timeout-event">apis/xhr/XMLHttpRequest/timeout-event</a></td>
<td align="left">When the author specified timeout has passed before the request could complete.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/Element/change">dom/Element/change</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/Element/cuechange">dom/Element/cuechange</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/Element/emptied">dom/Element/emptied</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/Element/ended">dom/Element/ended</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/Element/loadeddata">dom/Element/loadeddata</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/Element/loadedmetadata">dom/Element/loadedmetadata</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/Element/loadstart">dom/Element/loadstart</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/Element/media">dom/Element/media</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/Element/pause">dom/Element/pause</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/Element/play">dom/Element/play</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/Element/playing">dom/Element/playing</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/Element/seeked">dom/Element/seeked</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/Element/seeking">dom/Element/seeking</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/Element/stalled">dom/Element/stalled</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/Element/suspend">dom/Element/suspend</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/Element/waiting">dom/Element/waiting</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/autobuffer">dom/HTMLMediaElement/autobuffer</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/autoplay">dom/HTMLMediaElement/autoplay</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/buffered">dom/HTMLMediaElement/buffered</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/canPlayType">dom/HTMLMediaElement/canPlayType</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/canplay">dom/HTMLMediaElement/canplay</a></td>
<td align="left">Fires whenever enough data is available to determine whether a media is playable.</td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/canplaythrough">dom/HTMLMediaElement/canplaythrough</a></td>
<td align="left">Fires when enough data is available to determine whether a media is playable at a normal rate without interruptions.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/controls">dom/HTMLMediaElement/controls</a></td>
<td align="left">Controls attribute used within a Audio element or Video element displays the default media controls defined by the web browser being used to open HTML document or view of a Web Application.</td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/currentSrc">dom/HTMLMediaElement/currentSrc</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/currentTime">dom/HTMLMediaElement/currentTime</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/defaultPlaybackRate">dom/HTMLMediaElement/defaultPlaybackRate</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/duration">dom/HTMLMediaElement/duration</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/ended">dom/HTMLMediaElement/ended</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/error">dom/HTMLMediaElement/error</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/load">dom/HTMLMediaElement/load</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/loop">dom/HTMLMediaElement/loop</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/muted">dom/HTMLMediaElement/muted</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/networkState">dom/HTMLMediaElement/networkState</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/pause">dom/HTMLMediaElement/pause</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/paused">dom/HTMLMediaElement/paused</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/playbackRate">dom/HTMLMediaElement/playbackRate</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/played">dom/HTMLMediaElement/played</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/preload">dom/HTMLMediaElement/preload</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/progress">dom/HTMLMediaElement/progress</a></td>
<td align="left">Fires to indicate progress while downloading media data.</td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/seekable">dom/HTMLMediaElement/seekable</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/seeking">dom/HTMLMediaElement/seeking</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/src">dom/HTMLMediaElement/src</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaElement/textTracks">dom/HTMLMediaElement/textTracks</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLMediaElement/volume">dom/HTMLMediaElement/volume</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLMediaError/code">dom/HTMLMediaError/code</a></td>
<td align="left">Returns the current <strong>HTMLMediaError</strong> code or null if no error has occurred.</td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLTrackElement/default">dom/HTMLTrackElement/default</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLTrackElement/kind">dom/HTMLTrackElement/kind</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLTrackElement/label">dom/HTMLTrackElement/label</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLTrackElement/srclang">dom/HTMLTrackElement/srclang</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLTrackElement/track">dom/HTMLTrackElement/track</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLVideoElement/height">dom/HTMLVideoElement/height</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLVideoElement/initialTime">dom/HTMLVideoElement/initialTime</a></td>
<td align="left">Earliest point in seconds where the playback can (should) start playing</td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLVideoElement/poster">dom/HTMLVideoElement/poster</a></td>
<td align="left">Valid URL to an image ressource that will be displayed until the first frame of the video is available or will be displayed if no valid video ressource is available at all.</td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLVideoElement/videoHeight">dom/HTMLVideoElement/videoHeight</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/HTMLVideoElement/videoWidth">dom/HTMLVideoElement/videoWidth</a></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/HTMLVideoElement/width">dom/HTMLVideoElement/width</a></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/shadowdom/ShadowRoot/activeElement">dom/shadowdom/ShadowRoot/activeElement</a></td>
<td align="left">Represents the currently focused element in the shadow tree.</td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/shadowdom/ShadowRoot/addStyleSheet">dom/shadowdom/ShadowRoot/addStyleSheet</a></td>
<td align="left">Adds a new style sheet to shadow root style sheets.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/shadowdom/ShadowRoot/applyAuthorStyles">dom/shadowdom/ShadowRoot/applyAuthorStyles</a></td>
<td align="left">Indicates whether the rules in author styles associated with the element's document apply to the shadow tree. If false (default value), the author styles are not applied to the shadow tree. If true, the author styles are applied.</td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/shadowdom/ShadowRoot/elementFromPoint">dom/shadowdom/ShadowRoot/elementFromPoint</a></td>
<td align="left">Returns an element at specified coordinates.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/shadowdom/ShadowRoot/getSelection">dom/shadowdom/ShadowRoot/getSelection</a></td>
<td align="left">Returns the current selection in this ShadowRoot's shadow tree.</td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/shadowdom/ShadowRoot/innerHTML">dom/shadowdom/ShadowRoot/innerHTML</a></td>
<td align="left">Represents the markup of the ShadowRoot's contents.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/shadowdom/ShadowRoot/removeStyleSheet">dom/shadowdom/ShadowRoot/removeStyleSheet</a></td>
<td align="left">Removes a style sheet from the ShadowRoot.</td>
</tr>
<tr class="even">
<td align="left"><a href="/dom/shadowdom/ShadowRoot/resetStyleInheritance">dom/shadowdom/ShadowRoot/resetStyleInheritance</a></td>
<td align="left">Indicates whether or not the inheritable CSS properties are set to the initial value at the shadow boundary. If false (default value), the properties continue to inherit. If true, the properties are set to initial value.</td>
</tr>
<tr class="odd">
<td align="left"><a href="/dom/shadowdom/ShadowRoot/styleSheets">dom/shadowdom/ShadowRoot/styleSheets</a></td>
<td align="left">Represents the shadow root style sheets.</td>
</tr>
</tbody>
</table>

### <span>Review content</span>

(0 results)

These pages need to be reviewed by a community member familiar with the API and its usage in JavaScript. Where you find errors, please correct them; when you're finished, please remove the "Needs Review" flag.
 The following criteria are applied:

-   Topics: API
-   High-level issues: Needs Review

Nothing found!

## <span>DOM content</span>

Content identified here was originally considered part of the API project, but these APIs are actually DOM APIs, and should be considered in the scope of the DOM project (yet to be started).

|Priority|API Name|Source|Description|
|:-------|:-------|:-----|:----------|
|DOM|[Pointer Lock API](https://developer.mozilla.org/en-US/docs/API/Pointer_Lock_API)|MDN|Provides input methods based on the movement of the mouse over time.|
|DOM|[Battery](https://developer.mozilla.org/en-US/docs/DOM/window.navigator.battery)|MDN|Battery status.|
|DOM|[MutationObserver](https://developer.mozilla.org/en-US/docs/DOM/MutationObserver)|MDN|Observes changes to the DOM.|
|DOM|[Page Visibility](https://developer.mozilla.org/en-US/docs/DOM/Using_the_Page_Visibility_API)|MDN|Tells the application if a page is in focus.|
|DOM|[Fullscreen](https://developer.mozilla.org/en-US/docs/Using_fullscreen_mode)|MDN|Gives elements access to fullscreen presentation.|
|DOM|[Device Orientation](https://developer.mozilla.org/en-US/docs/Detecting_device_orientation)|MDN|Events that signal the device's orientation.|
|DOM|[Shadow DOM](https://dvcs.w3.org/hg/webcomponents/raw-file/tip/spec/shadow/index.html)|Dimitri's Blog|Tip of the Web Components iceberg; Scott is on the hook for this one.|

## <span>Creating, updating, and importing content</span>

Along with importing content from other sources, it is crucial that when you are working with existing content you check that content against the source specification. The document, [WPD:Creating\_API\_pages](/WPD:Creating_API_pages) has more information about editing API pages.

## <span>Templates and forms</span>

Several issues with the current design and implementation of the templates and forms for use with the API documentation are noted in the "TODO" sections of the page, [WPD:Creating\_API\_pages](/WPD:Creating_API_pages). The issues are summarized as follows:

-   The text fields in the page creation forms on the [WPD:New\_Page](/WPD:New_Page) page need to be wider to accomodate longer namespace names. [Bug 20625](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20625)
-   We need a better way to specify non-primitive (or uncommon) return types. [[Bug 20626](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20626)]
-   Exceptions need to have forms and templates designed for them so that they may be reused between object methods. [Bug 20627](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20627)
-   Constants (or enumerations) used as property and method values need to have forms and templates designed for them so that they may be reused between object properties and methods. [Bug 20628](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20628)
-   For the Syntax section in properties and methods, it is not clear that the way the form enforces the syntax works in all cases. It may be overly specific. We need a tiger team to look at this more carefully to determine if there is an issue.
-   In the Event template it is not clear how the Overview Table gets populated. Looks like the Event template has not been completed. [Bug 20629](https://www.w3.org/Bugs/Public/show_bug.cgi?id=20629)

## <span>Additional documents</span>

The methodology for creating API pages is described in [WPD:Creating\_API\_pages](/WPD:Creating_API_pages).