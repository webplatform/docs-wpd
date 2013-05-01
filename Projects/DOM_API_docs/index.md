=DOM API documentation=

This is the project page for the DOM API documentation on WPD.

==Purpose==

The purpose of this documentation is to describe the Document Object Model for developers of applications that work with DOM artifacts. It is not an architectural study of the DOM, nor is it intended to support the development of the DOM itself.

==Scope==

This documentation will cover the programatic artifacts that provide an interface to the DOM, the APIs. This document does not cover the HTML elements or CSS artifacts that otherwise are considered part of the DOM. Nor does this project deal with the SVG or MathML content in WPD.

==Tasks==

The two primary tasks of this project are as follows:
* Reorganize the DOM API documentation in a coherent structure that supports short, predictable URLs.
* Fill in the pages with information currently missing.

==Reorganization==
First, we have to reorganize our current content.

===Current organization variants===
Most of the problems with the way the content is currently organized boil down to the use of "interstials" - either as unnecessary namespace delineations or artificial subtree designations.

====Optimum scheme====
Some of the [[dom|DOM]] pages follow the very plain, short, and predictable delineation that we consider optimum:
* dom/<object>/<member>
Where <member> may be a property, event, or method. For example,  [[dom/Element/error]].

====Weird subtrees====
Some pages are designated as subtrees of the dom/apis. These are:
* [[dom/apis/audio-video]]
* [[dom/traversal]]
These subtree designations appear to be completely artificial, unlike the use of such designations in the [[WPD:Creating_API_pages|API Project]], where API_Listing pages described the common name of the API. Here, with no common API names required to distinguish the pages, these interstitials are unnecessary. The member pages of these dom "subtrees" invariably refer to their parent objects - HTMLElement, etc. - via the "Applies to" template (though these are not shown in the URL presently).

====Interstitials====
Other pages are using "interstitials" to describe the namespace type, such as the "apis" interstitial, as follows:
* dom/apis/<object>/<member>
For example, [[dom/apis/document/getElementById]]. Note the object name, "document" is not capitalized, which violates our rules of capitalization. 

Interstitials usually follow the "dom" namespace identifier, and are used to delineate objects and members:
* dom/objects/<object> 
* dom/events/<event>
* dom/methods/<method>
* dom/properties/<property>

For example [[dom/events/abort]] or [[dom/methods/moveTo]]. For members, these lack any description of the objects that encapsulate them in the URL, though the reference to the parent object is maintained in the content via the "Applies to" template.

Also, within named subtrees of the dom/apis, interstitials are used to distinguish methods, properties, and events. For example, [[dom/apis/audio-video/properties/type]].

In the [[WPD:Creating_API_pages|API Project]] we decided to eliminate these member interstitials as being unnecessary. We can follow the same reasoning for the DOM APIs.

Some pages have no interstitials at all.
* dom/<member>

For example, [[dom/gotpointercapture]].

====Inheritance not  in the URLs====
Inheritance is not described in the URLs of the pages. Most pages follow this organization:
* dom/<object>
For example, [[dom/HTMLTrackElement]] ''not'' [[dom/EventTarget/Node/Element/HTMLElement/HTMLTrackElement]]. This is a good thing. As you can see, describing the inheritance model would make the URLs unnecessarily long without providing any useful information to the user.

===Organization solution===

Proposed is the abolition of all "interstitials" and the assignment of all members to their encapsulating objects in the URLs. Even the "apis" interstitial is unnecessary (see below). To that, we would have the following first-tier designations.
* '''dom''' - a listing page with all DOM objects and their summaries.

For events we're using the '''Applies to field''' in an overloaded fashion. For methods and properties it means "belongs to" or "is a member of" whereas for events it means "targeted at".

Inheritance, however, should not be described in the URL. Rather, all DOM objects, regardless of their "level" in the DOM, should reside on one level of the WPD URL structure. This provides for short URLs. So, we would have the following:
* dom/HTMLTrackElement (''not'' dom/EventTarget/Node/Element/HTMLElement/HTMLTrackElement)
* dom/Navigator
* dom/Window
* dom/Node
* dom/Document
* dom/Element
* dom/HTMLElement
* dom/HTMLMenuElement
etc.

Going further into the namespace, all members would be organized under their parent objects. To wit:
* current: [[dom/apis/document/getElementById]]            proposed: [[dom/Document/getElementById]]
* current: [[dom/traversal/methods/RangeException]]       proposed: [[dom/Element/RangeException]]
* current: [[dom/events/mouseover]]                                 proposed: [[dom/Element/mouseover]]

This follows the methodology in the [[WPD:Creating_API_pages|API Project]], except that API_Listing pages are not required to describe interstitials (other than the "dom" listing page), because there is no danger of namespace conflicts that would require the use of such interstitials.

An "apis" interstitial is unnecessary. The DOM itself includes CSS, CSSOM, HTML Elements, SVG, etc., and we have already broken out the content into these top-level buckets. We don't have "dom/css/cssom" or "dom/svg." We are designating this bucket as the "dom" to mean the objects and interfaces used to program against the DOM. That these are understood to be the APIs, using "apis" as an interstitial (as in "dom/apis") is redundant.

We propose to reorganize the DOM pages (estimated at roughly 1200 pages) according to the guidelines above. Under these guidelines, all DOM pages would follow the URL structure, "dom/<object>/<member>" where <member> may be a property, event, or method.

===Reorganization procedure===

There are 1129 pages in the dom namespace.  
* 137 in a dom/<object>/<member> pattern already (wich do not need to move)
* 49 in dom/objects
* 77 in dom/apis
* 101 in dom/traversal
* 119 in dom/events
* 257 in dom/methods
* 336 in dom/properties 

This leaves 53 pages that don't fit into any of these categories.

The 137 pages that follow the dom/<object>/<member> pattern do not have to move. However, there are several PointerEvent types (for example [[dom/pointercancel]], where the Applies to field actually lists the event type (PointerEvent) rather than the target (Element). For these, change the '''Applies to''' field for all PointerEvent event members from "dom/PointerEvent" to "dom/Element". 

For the dom/objects pages, simply move dom/objects/* to dom/* - removing the "objects" interstitial.

For the dom/apis pages, some of these can be moved with the script because they have an '''Applies to''' field, for example [[dom/apis/audio-video/events/play]].

Apply the following process to the dom/methods, dom/properties, and dom/events pages.

* If the page is of the Event, API_Object_Method, or API_Object_Property template type, AND if the page's '''Applies to''' field is set
** If the '''Applies to''' location is valid (exists)
*** If there is no existing page in the location specified by the '''Applies to''' field, move the page under the location specified in that field
*** If there is an existing page in the location specified by the '''Applies to''' field, move the page under '''<Applies-to_field>/duplicates''' 
*** If there is an existing page in the location specified by '''<Applies-to_field>/duplicates''' move the page under '''<Applies-to_field>/duplicates/duplicates'''
* Otherwise, leave the page where it is

==Amending the content==
We'll deal with this after we get reorganized. To be continued...

Need a way to identify the event type (i.e. KeyboardEvent). ([http://project.webplatform.org/tmpl/issues/7 bug])