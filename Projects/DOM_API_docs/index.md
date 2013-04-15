=DOM API documentation=

This is the project page for the DOM API documentation on WPD.

==Purpose==

The purpose of this documentation is to describe the Document Object Model for developers using JavaScript to build applications that work with DOM artifacts. It is not an architectural study of the DOM, nor is it intended to support the development of the DOM itself.

==Scope==

This documentation will cover the DOM artifacts relevant to their use in JavaScript. This document does not cover the HTML elements or CSS artifacts that otherwise are considered part of the DOM. Nor does this project deal with the SVG or MathML content in WPD.

==Tasks==

The two primary tasks of this project are as follows:
* Reorganize the DOM API documentation in a coherent structure that supports short, predictable URLs.
* Fill in the pages with information currently missing.

==Reorganization==

Consider the current state of the [[dom|DOM]] pages. Some follow the very plain, short, and predictable delineation that we consider optimum:
* dom/<object>/<member>
Where <member> may be a property or method. For example,  [[dom/Element/error]].

Some pages are designated as subtrees of the dom/apis. These are:
* [[dom/apis/audio-video]]
* [[dom/traversal]]
These subtree designations appear to be completely artificial, unlike the use of such designations in the [[WPD:Creating_API_pages|API Project]], where API_Listing pages described the common name of the API. The member pages of these dom "subtrees" invariably refer to their parent objects, though these are not shown in the URL.

Other pages are using "interstitials" to describe the namespace type, such as:
* dom/apis/<object>/<member>
For example, [[dom/apis/document/getElementById]]. Note the object name, "document" is not capitalized, which violates our rules of capitalization. 

Interstitials are used to delineate objects and members:
* dom/objects/<object> 
* dom/events/<event>
* dom/methods/<method>
* dom/properties/<property>
For example [[dom/events/abort]] or [[dom/methods/moveTo]]. For members, these lack any description of the objects that encapsulate them in the URL, though usually the reference to the parent object is maintained in the content.

Also, within named subtrees of the dom/apis, interstitials are used to distinguish methods and properties as well as events. For example, [[dom/apis/audio-video/properties/type]].

Some pages have no interstitials at all.
* dom/<member>

For example, [[dom/gotpointercapture]].

Inheritance is not described in the URLs of the pages. Most pages follow this organization:
* dom/<object>
For example, [[dom/HTMLTrackElement]] ''not'' [[dom/EventTarget/Node/Element/HTMLElement/HTMLTrackElement]].