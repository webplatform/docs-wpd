=API documentation proposal=

==Summary==

Some of the most immediately useful technical content that WPD can provide is for the new JavaScript APIs recently developed (or currently being developed) for web applications. These APIs provide new functionality that make web applications as robust and high-performing as desktop or native apps. By focusing on this area of technical content, we can establish WPD as the leading provider of reference information for modern web development.

The goal for this project is to bring the API documentation up to date and to make WPD the most current source for this documentation.

This proposal outlines a strategy for building out the API documentation, considering the following:

* The current state of the "apis" namespace and extant content
* External content that could be imported to WPD
* New content that will help developers use the latest features of modern browsers
* Creating, updating, and importing content
* Template and forms changes that need to be implemented
* Priorities and project management
* Additional documents

==Current state of the WPD API documentation==

With the launch of WPD in October 2012, we received a generous donation of API documentation from Microsoft; it included some 12 APIs: appcache, audio-video (media), canvas, file, geolocation, indexeddb, timing, web-messaging, web-storage, websocket, workers, and xhr. A review of this content revealled that it needed to be reorganized and ammended extensively. While this work began, some new API documentation was developed (mostly to prove the process for creating API documentation). The findings of these efforts are summarized in [[WPD:Creating_API_pages]].

The following table summarizes the current state of the extant API documentation on WPD. Note that all of the extant documentation will require changes associated with new templates and forms as discussed in [[#Templates_and_forms|Templates and forms]], below. Another (messy) representation of this content may be found on the [[apis|apis]] page.

{| class="sortable"
! Priority
! API Name
! Handler
! Current State
|-
| 1
| [[apis/appcache|appcache]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 2
| [[apis/audio-video|audio-video]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 3
| [[apis/canvas|canvas]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 4
| [[apis/css-regions|css-regions]]
| [[User:Sierra|Mike Sierra]]
| Content complete
|-
| 5
| [[apis/file|file]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 6
| [[apis/filesystem|filesystem]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 7
| [[apis/geolocation|geolocation]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 8
| [[apis/indexeddb|indexeddb]]
| [[User:Lleonard|Lance Leonard]]
| In progress
|-
| 9
| [[apis/navigation_timing|navigation timing]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 10
| [[apis/user_timing|user timing]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 11
| [[apis/resource_timing|resource timing]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 12
| [[apis/webaudio|webaudio]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 13
| [[apis/web-messaging|web-messaging]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 14
| [[apis/webrtc|webrtc]]
| [[User:Scottrowe|Scott Rowe]]
| In progress
|-
| 15
| [[apis/websocket|websocket]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 16
| [[apis/web-storage|web-storage]]
| [[User:Dgash|Dave Gash]]
| Content complete
|-
| 17
| [[apis/workers|workers]]
| [[User:Dgash|Dave Gash]]
| In progress
|-
| 18
| [[apis/xhr|xhr]]
| [[User:Dgash|Dave Gash]]
| Mostly complete, needs to include CORS
|}

==External content for import==

Much of the extant API content (above) needs to be filled in or otherwise amended. Doing this work from scratch, going back to the specs, and building out a completely new reference would take far more time and effort than importing content already developed by the stewards or other sources. Importing external content into WPD would help us realize our goal to make WPD the largest single source of reference material for developers.

For the API documentation, the following list identifies key APIs in modern web development; these are both the most used and the newest (bleeding-edge) APIs currently documented by other sources. The list considers the API, its source, purpose, and whose permission we need to import the content into WPD. These are prioritized in terms of both how how important they are to developers and how easy it might be to obtain permission to import them into WPD.

{{TODO|Need to put in place an automated process that provides for the obtaining of permission to import and the provision for pointers to the imported content from the source (indicating that this is the new location of the doc for on-going maintenance) for MDN.}}

Also, very often the API documentation from other sources includes tutorial and conceptual content that also needs to be imported into the likewise appropriate namespace on WPD. Sometimes an API's documentation is actually a tutorial - when the API is brief, for instance.

And just in case you're wondering, content identified as authored by Google or "mostly Googlers" is considered easiest to import because no explicit approval is required from Google authors to import the content.

{| class="sortable"
! Priority
! API Name
! Source
! Description
! Authors
|-
| 
| [https://developer.mozilla.org/en-US/docs/API/Pointer_Lock_API Pointer Lock API]
| MDN
| Provides input methods based on the movement of the mouse over time.
| Mostly Googlers, see history
|-
| 
| [https://developer.mozilla.org/en-US/docs/DOM/window.navigator.battery Battery]
| MDN
| Battery status.
| Many, see history
|-
| 
| [https://developer.mozilla.org/en-US/docs/DOM/MutationObserver MutationObserver]
| MDN
| Observes changes to the DOM.
| Many, see history
|-
| 
| [https://developer.mozilla.org/en-US/docs/DOM/Using_the_Page_Visibility_API Page Visibility]
| MDN
| Tells the application if a page is in focus.
| Many, see history
|-
| 
| [https://developer.mozilla.org/en-US/docs/Using_fullscreen_mode Fullscreen]
| MDN
| Gives elements access to fullscreen presentation.
| Many, see history
|-
| 
| [https://developer.mozilla.org/en-US/docs/Detecting_device_orientation Device Orientation]
| MDN
| Events that signal the device's orientation.
| Many, see history
|-
| 
| 
| 
| 
| 
|}

==New APIs==

The following table lists APIs either in development that have not been documented and which will be important to developers in the near future.

{| class="sortable"
! Priority
! API Name
! Description
! SMEs
|-
| 1
| [https://dvcs.w3.org/hg/webcomponents/raw-file/tip/spec/shadow/index.html Shadow DOM]
| Tip of the Web Components iceberg; Scott is on the hook for this one.
| Dimitri Glazkov, Google
|-
| 2
| [https://dvcs.w3.org/hg/quota/raw-file/tip/Overview.html Quota Management]
| Manage usage and availability of a user's local storage (appcache, file, indexeddb, websql).
| Kinuko Yasuda, Google
|-
| 3
| 
| 
|
|}

==Creating, updating, and importing content==

Along with importing content from other sources, it is crucial that when you are working with existing content you check that content against the source specification. The document, [[WPD:Creating_API_pages]] has more information about editing API pages. 

==Templates and forms==

Several issues with the current design and implementation of the templates and forms for use with the API documentation are noted in the "TODO" sections of the page, [[WPD:Creating_API_pages]]. The issues are summarized as follows:

* The text fields in the page creation forms on the [[WPD:New_Page]] page need to be wider to accomodate longer namespace names. [https://www.w3.org/Bugs/Public/show_bug.cgi?id=20625 Bug 20625]
* We need a better way to specify non-primitive (or uncommon) return types. [[https://www.w3.org/Bugs/Public/show_bug.cgi?id=20626 Bug 20626]]
* Exceptions need to have forms and templates designed for them so that they may be reused between object methods. [https://www.w3.org/Bugs/Public/show_bug.cgi?id=20627 Bug 20627]
* Constants (or enumerations) used as property and method values need to have forms and templates designed for them so that they may be reused between object properties and methods. [https://www.w3.org/Bugs/Public/show_bug.cgi?id=20628 Bug 20628]
* For the Syntax section in properties and methods, it is not clear that the way the form enforces the syntax works in all cases. It may be overly specific. We need a tiger team to look at this more carefully to determine if there is an issue.
* In the Event template it is not clear how the Overview Table gets populated. Looks like the Event template has not been completed. [https://www.w3.org/Bugs/Public/show_bug.cgi?id=20629 Bug 20629]

==Priorities and project management==

This section describes the tasks and assignments needed to complete the work in this proposal. It will be developed further as the community comments on the proposal and contributors are assigned specific tasks.

===Tasks===

{| class="sortable"
! Priority
! Task
! Description
! Assigned to
! State
|-
| 0
| Obtain permissions to import articles from MDN
| Begin contacting authors for permission
| Scottrowe, Jswisher
| Not started
|-
| 0
| Assign template & form bugs
| Some discussion and design work with the Template Corps is required.
| Scottrowe
| Not started
|}

==Additional documents==

The methodology for creating API pages is described in [[WPD:Creating_API_pages]].