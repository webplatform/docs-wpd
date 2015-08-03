---
title: WPD:Projects/DOM API docs
---
<h1><span class="mw-headline" id="DOM_API_documentation">DOM API documentation</span></h1>
<p>This is the project page for the DOM API documentation on WPD.
</p>
<h2><span class="mw-headline" id="Purpose">Purpose</span></h2>
<p>The purpose of this documentation is to describe the Document Object Model for developers of applications that work with DOM artifacts. It is not an architectural study of the DOM, nor is it intended to support the development of the DOM itself.
</p>
<h2><span class="mw-headline" id="Scope">Scope</span></h2>
<p>This documentation will cover the programatic artifacts that provide an interface to the DOM, the APIs. This document does not cover the HTML elements or CSS artifacts that otherwise are considered part of the DOM. Nor does this project deal with the SVG or MathML content in WPD.
</p>
<h2><span class="mw-headline" id="Tasks">Tasks</span></h2>
<p>The two primary tasks of this project are as follows:
</p>
<ul><li> Reorganize the DOM API documentation in a coherent structure that supports short, predictable URLs.</li>
<li> Remove and replace proprietary content with standard content.</li>
<li> Fill in the pages with information currently missing.</li></ul>
<h2><span class="mw-headline" id="Reorganization">Reorganization</span></h2>
<p>First, we have to reorganize our current content.
</p>
<h3><span class="mw-headline" id="Current_organization_variants">Current organization variants</span></h3>
<p>Most of the problems with the way the content is currently organized boil down to the use of "interstials" - either as unnecessary namespace delineations or artificial subtree designations.
</p>
<h4><span class="mw-headline" id="Optimum_scheme">Optimum scheme</span></h4>
<p>Some of the <a href="/wiki/dom" title="dom">DOM</a> pages follow the very plain, short, and predictable delineation that we consider optimum:
</p>
<ul><li> dom/&lt;object&gt;/&lt;member&gt;</li></ul>
<p>Where &lt;member&gt; may be a property, event, or method. For example,  <a href="/wiki/dom/Element/error" title="dom/Element/error">dom/Element/error</a>.
</p>
<h4><span class="mw-headline" id="Weird_subtrees">Weird subtrees</span></h4>
<p>Some pages are designated as subtrees of the dom/apis. These are:
</p>
<ul><li> <a href="/w/index.php?title=dom/apis/audio-video&amp;action=edit&amp;redlink=1" class="new" title="dom/apis/audio-video (page does not exist)">dom/apis/audio-video</a></li>
<li> <a href="/w/index.php?title=dom/traversal&amp;action=edit&amp;redlink=1" class="new" title="dom/traversal (page does not exist)">dom/traversal</a></li></ul>
<p>These subtree designations appear to be completely artificial, unlike the use of such designations in the <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">API Project</a>, where API_Listing pages described the common name of the API. Here, with no common API names required to distinguish the pages, these interstitials are unnecessary. The member pages of these dom "subtrees" invariably refer to their parent objects - HTMLElement, etc. - via the "Applies to" template (though these are not shown in the URL presently).
</p>
<h4><span class="mw-headline" id="Interstitials">Interstitials</span></h4>
<p>Other pages are using "interstitials" to describe the namespace type, such as the "apis" interstitial, as follows:
</p>
<ul><li> dom/apis/&lt;object&gt;/&lt;member&gt;</li></ul>
<p>For example, <a href="/w/index.php?title=dom/apis/document/getElementById&amp;action=edit&amp;redlink=1" class="new" title="dom/apis/document/getElementById (page does not exist)">dom/apis/document/getElementById</a>. Note the object name, "document" is not capitalized, which violates our rules of capitalization. 
</p><p>Interstitials usually follow the "dom" namespace identifier, and are used to delineate objects and members:
</p>
<ul><li> dom/objects/&lt;object&gt; </li>
<li> dom/events/&lt;event&gt;</li>
<li> dom/methods/&lt;method&gt;</li>
<li> dom/properties/&lt;property&gt;</li></ul>
<p>For example <a href="/w/index.php?title=dom/events/abort&amp;action=edit&amp;redlink=1" class="new" title="dom/events/abort (page does not exist)">dom/events/abort</a> or <a href="/w/index.php?title=dom/methods/moveTo&amp;action=edit&amp;redlink=1" class="new" title="dom/methods/moveTo (page does not exist)">dom/methods/moveTo</a>. For members, these lack any description of the objects that encapsulate them in the URL, though the reference to the parent object is maintained in the content via the "Applies to" template.
</p><p>Also, within named subtrees of the dom/apis, interstitials are used to distinguish methods, properties, and events. For example, <a href="/w/index.php?title=dom/apis/audio-video/properties/type&amp;action=edit&amp;redlink=1" class="new" title="dom/apis/audio-video/properties/type (page does not exist)">dom/apis/audio-video/properties/type</a>.
</p><p>In the <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">API Project</a> we decided to eliminate these member interstitials as being unnecessary. We can follow the same reasoning for the DOM APIs.
</p><p>Some pages have no interstitials at all.
</p>
<ul><li> dom/&lt;member&gt;</li></ul>
<p>For example, <a href="/w/index.php?title=dom/gotpointercapture&amp;action=edit&amp;redlink=1" class="new" title="dom/gotpointercapture (page does not exist)">dom/gotpointercapture</a>.
</p>
<h4><span class="mw-headline" id="Inheritance_not_in_the_URLs">Inheritance not  in the URLs</span></h4>
<p>Inheritance is not described in the URLs of the pages. Most pages follow this organization:
</p>
<ul><li> dom/&lt;object&gt;</li></ul>
<p>For example, <a href="/wiki/dom/HTMLTrackElement" title="dom/HTMLTrackElement">dom/HTMLTrackElement</a> <i>not</i> <a href="/w/index.php?title=dom/EventTarget/Node/Element/HTMLElement/HTMLTrackElement&amp;action=edit&amp;redlink=1" class="new" title="dom/EventTarget/Node/Element/HTMLElement/HTMLTrackElement (page does not exist)">dom/EventTarget/Node/Element/HTMLElement/HTMLTrackElement</a>. This is a good thing. As you can see, describing the inheritance model would make the URLs unnecessarily long without providing any useful information to the user.
</p>
<h3><span class="mw-headline" id="Organization_solution">Organization solution</span></h3>
<p>Proposed is the abolition of all "interstitials" and the assignment of all members to their encapsulating objects in the URLs. Even the "apis" interstitial is unnecessary (see below). To that, we would have the following first-tier designations.
</p>
<ul><li> <b>dom</b> - a listing page with all DOM objects and their summaries.</li></ul>
<p>Beneath that are the DOM objects; these are of two types, <b>events</b> and <b>event targets</b>.  
</p>
<h4><span class="mw-headline" id="Events">Events</span></h4>
<p>All of the event types are currently organized under dom/objects, i.e. dom/objects/PointerEvent and the actual events are organized under dom/events, i.e dom/events/pointerdown.
</p><p>Events logically belong under their event types (i.e. dom/PointerEvent/pointerdown or dom/Event/error). The events in <a href="/wiki/dom/PointerEvent" title="dom/PointerEvent">dom/PointerEvent</a> are organized thus, and we want to describe all events this way - under their event types in the URLs. There are two fields in the Event template that capture the parent object of specific events, the Interface= field and the Event_applies_to= field, as shown in the example below:
</p><p>
{{Event
|Interface=dom/objects/FocusEvent
|Target=dom/Element
|Default_action=
|Content=
|Event_applies_to=dom/objects/FocusEvent
|Synchronous=No
|Bubbles=No
|Cancelable=No
}}

</p><p>The trouble is that, as in the above example, the values of the Interface= and Event_applies_to fields need to be corrected. In the above example, the field should read, Interface=dom/FocusEvent. This is the case with all of the events, their event types are all organized under the interstitial, "objects."
</p><p>So, the first task is to re-organize the event types directly under dom, i.e. dom/PointerEvent. Event type pages need to be moved out of dom/objects/ and into dom/ - for example, dom/FocusEvent. This move needs to be performed manually for all of the pages currently under <a href="/w/index.php?title=dom/objects&amp;action=edit&amp;redlink=1" class="new" title="dom/objects (page does not exist)">dom/objects</a>.
</p><p>Then, we need to edit the event pages Event_applies_to= field to point to the event type, for example,  Event_applies_to=dom/UIEvent. While we're at it, do the same for the Interface= field, i.e. Interface=dom/UIEvent. Although the Interface= field appears to be unused, it should be updated for consistency.
</p><p>Making these changes will cause changes to the event target pages like dom/Element. In most cases, the event pages currently specify Event_applies_to=&lt;event target page&gt;, i.e. Event_applies_to=dom/Element. This produces a list of events on the event target page. When we change the value to Event_applies_to=&lt;event type&gt;, i.e. Event_applies_to=dom/PointerEvent, the list appears on the event type page, as it should, instead.
</p><p>To produce a list on the event target pages, the API_Object template needs to be updated to generate the list based on the Target=dom/Element value. See <a rel="nofollow" class="external text" href="http://project.webplatform.org/tmpl/issues/14">this issue</a> for details.
</p><p>Eventually we need to add a field to the Event form to display the event type (see <a rel="nofollow" class="external text" href="http://project.webplatform.org/tmpl/issues/7">this issue</a>).
</p><p>We also considered organizing events  under their targets (i.e. dom/Element/pointerdown), but found namespace collisions (dom/Element/error property collides with dom/Element/error event). Besides, events properly belong to event types, not targets, in the DOM.
</p>
<h4><span class="mw-headline" id="Event_targets">Event targets</span></h4>
<p>Event targets are such objects as Document, Element, etc.
</p><p>Inheritance should not be described in the URL. Rather, all DOM objects, regardless of their "level" in the DOM, should reside on one level of the WPD URL structure. This provides for short URLs. So, we would have the following:
</p>
<ul><li> dom/HTMLTrackElement (<i>not</i> dom/EventTarget/Node/Element/HTMLElement/HTMLTrackElement)</li>
<li> dom/Navigator</li>
<li> dom/Window</li>
<li> dom/Node</li>
<li> dom/Document</li>
<li> dom/Element</li>
<li> dom/HTMLElement</li>
<li> dom/HTMLMenuElement</li></ul>
<p>etc.
</p><p>Going further into the namespace, all members would be organized under their parent objects. To wit:
</p>
<ul><li> current: <a href="/w/index.php?title=dom/apis/document/getElementById&amp;action=edit&amp;redlink=1" class="new" title="dom/apis/document/getElementById (page does not exist)">dom/apis/document/getElementById</a>            proposed: <a href="/wiki/dom/Document/getElementById" title="dom/Document/getElementById">dom/Document/getElementById</a></li>
<li> current: <a href="/w/index.php?title=dom/traversal/methods/RangeException&amp;action=edit&amp;redlink=1" class="new" title="dom/traversal/methods/RangeException (page does not exist)">dom/traversal/methods/RangeException</a>       proposed: <a href="/wiki/dom/Element/RangeException" title="dom/Element/RangeException">dom/Element/RangeException</a></li></ul>
<p>This follows the methodology in the <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">API Project</a>, except that API_Listing pages are not required to describe interstitials (other than the "dom" listing page), because there is no danger of namespace conflicts that would require the use of such interstitials.
</p><p>An "apis" interstitial is unnecessary. The DOM itself includes CSS, CSSOM, HTML Elements, SVG, etc., and we have already broken out the content into these top-level buckets. We don't have "dom/css/cssom" or "dom/svg." We are designating this bucket as the "dom" to mean the objects and interfaces used to program against the DOM. That these are understood to be the APIs, using "apis" as an interstitial (as in "dom/apis") is redundant.
</p><p>We propose to reorganize the DOM pages (estimated at roughly 1,129 pages) according to the guidelines above. Under these guidelines, all DOM pages would follow the URL structure, "dom/&lt;object&gt;/&lt;member&gt;" where &lt;member&gt; may be a property or method, or event.
</p>
<h3><span class="mw-headline" id="Reorganization_procedure">Reorganization procedure</span></h3>
<p>There are 1129 pages in the dom namespace.  
</p>
<ul><li> 137 in a dom/&lt;object&gt;/&lt;member&gt; pattern already (some of which may not need to move)</li>
<li> 119 in dom/events </li>
<li> 49 in dom/objects</li>
<li> 77 in dom/apis</li>
<li> 101 in dom/traversal</li>
<li> 257 in dom/methods</li>
<li> 336 in dom/properties </li></ul>
<p>This leaves 53 pages that don't fit into any of these categories. Also, there are an additional 20 or so pages that may belong in the dom namespace and which currently reside in the apis namespace. These include the <a href="/wiki/apis/audio-video" title="apis/audio-video">audio-video APIs</a>, which need to be reviewed for members that may need to be moved into the dom namespace.
</p><p>For the dom/objects pages, simply move dom/objects/* to dom/* - removing the "objects" interstitial.
</p><p>For the dom/apis pages, most of these are part of the audio-video API, for example <a href="/w/index.php?title=dom/apis/audio-video/events/play&amp;action=edit&amp;redlink=1" class="new" title="dom/apis/audio-video/events/play (page does not exist)">dom/apis/audio-video/events/play</a>. Each of the pages in this namespace needs to be be organized under its parent DOM object - HTMLMediaElement, for example. Also, review the <a href="/wiki/apis/audio-video" title="apis/audio-video">audio-video APIs</a> for possible moves to the dom namespace. The rest, like <a href="/w/index.php?title=dom/apis/document/getElementById&amp;action=edit&amp;redlink=1" class="new" title="dom/apis/document/getElementById (page does not exist)">dom/apis/document/getElementById</a> can be moved according to the methodology outline here.
</p><p>The dom/traversal pages also need to be moved under their parent objects. For example <a href="/w/index.php?title=dom/traversal/methods/cloneContents&amp;action=edit&amp;redlink=1" class="new" title="dom/traversal/methods/cloneContents (page does not exist)">dom/traversal/methods/cloneContents</a> may need to move to dom/&lt;parentDOMobject&gt;/Range. Much of the work will be in figuring out to which DOM objects these traversal members belong. If the parent DOM object can't be determined, the traversal API might belong in the <a href="/wiki/apis" title="apis">apis</a> namespace. Luckily, there are no event pages under dom/traversal.
</p>
<h4><span class="mw-headline" id="Script">Script</span></h4>
<p>It may be possible to do some of this moving with a script. People in the community might be able to lend a hand. [<a rel="nofollow" class="external autonumber" href="http://docs.webplatform.org/wiki/User:Frozenice%7CFrozenice">[1]</a> (David Kirstein) is very knowledgeable about MediaWiki and Semantic MediaWiki, and he may be able to help automate this process.
</p><p>From a first-impression, it seemed the script could apply the following process to the dom pages.
</p>
<ul><li> If the page is of the API_Object_Method or API_Object_Property template type
<ul><li> If the page's <b>Applies to</b> field is set (Method_applies_to= , Property_applies_to=)
<ul><li> If the <b>Applies to</b> location is valid (exists)
<ul><li> If there is no existing page in the location specified by the <b>Applies to</b> field, move the page under the location specified in that field</li>
<li> Else if there is an existing page in the location specified by the <b>Applies to</b> field, move the page under <b>&lt;Applies-to_field&gt;/duplicates</b> </li>
<li> Else if there is an existing page in the location specified by <b>&lt;Applies-to_field&gt;/duplicates</b> move the page under <b>&lt;Applies-to_field&gt;/duplicates/duplicates</b> (and so on)</li></ul></li></ul></li>
<li> For each page that links to this page
<ul><li> Update the link to point to the page's new location.</li></ul></li></ul></li>
<li> Otherwise, leave the page where it is</li></ul>
<h4><span class="mw-headline" id="Manual_moving">Manual moving</span></h4>
<p>Before moving a page, take note of the new URL, and update the links in all pages that link to the moved page. Leave no redirect.
</p>
<h4><span class="mw-headline" id="Changing_Inbound_Links">Changing Inbound Links</span></h4>
<p>For each page that links to the page in question, all the links on that page to the new location. All the pages that link to the target page can be found consistently with the <a href="/wiki/Special:WhatLinksHere" title="Special:WhatLinksHere">Special:WhatLinksHere</a> page. For example:
</p>
<pre><a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/Special:WhatLinksHere/dom/apis/audio-video/events/play">http://docs.webplatform.org/wiki/Special:WhatLinksHere/dom/apis/audio-video/events/play</a>
</pre>
<p>We should leave no redirects, since page-level redirects, as opposed to server-level redirects, harm SEO.
</p>
<h2><span class="mw-headline" id="Amending_the_content">Amending the content</span></h2>
<p>We'll deal with this after we get reorganized. To be continued...
</p>
<h2><span class="mw-headline" id="Unresolved_issues">Unresolved issues</span></h2>
<p>Need to identify the event type (i.e. KeyboardEvent) in the Event template, Overview table. (<a rel="nofollow" class="external text" href="http://project.webplatform.org/tmpl/issues/7">bug</a>)
</p>
<!-- 
NewPP limit report
CPU time usage: 0.107 seconds
Real time usage: 0.157 seconds
Preprocessor visited node count: 83/1000000
Preprocessor generated node count: 100/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:7926-0!*!0!!*!*!*!esi=1 and timestamp 20150731111105 and revision id 40386
 -->
