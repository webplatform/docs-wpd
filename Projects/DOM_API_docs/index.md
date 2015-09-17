---
title: 'DOM API documentation'
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - dom/apis/audio-video
    - dom/traversal
    - dom/apis/document/getElementById
    - dom/events/abort
    - dom/methods/moveTo
    - dom/apis/audio-video/properties/type
    - dom/gotpointercapture
    - dom/EventTarget/Node/Element/HTMLElement/HTMLTrackElement
    - dom/objects
    - dom/traversal/methods/RangeException
    - dom/apis/audio-video/events/play
    - dom/traversal/methods/cloneContents
uri: 'WPD:Projects/DOM API docs'

---
This is the project page for the DOM API documentation on WPD.

## Purpose

The purpose of this documentation is to describe the Document Object Model for developers of applications that work with DOM artifacts. It is not an architectural study of the DOM, nor is it intended to support the development of the DOM itself.

## Scope

This documentation will cover the programatic artifacts that provide an interface to the DOM, the APIs. This document does not cover the HTML elements or CSS artifacts that otherwise are considered part of the DOM. Nor does this project deal with the SVG or MathML content in WPD.

## Tasks

The two primary tasks of this project are as follows:

-   Reorganize the DOM API documentation in a coherent structure that supports short, predictable URLs.
-   Remove and replace proprietary content with standard content.
-   Fill in the pages with information currently missing.

## Reorganization

First, we have to reorganize our current content.

### Current organization variants

Most of the problems with the way the content is currently organized boil down to the use of "interstials" - either as unnecessary namespace delineations or artificial subtree designations.

#### Optimum scheme

Some of the [DOM](/dom) pages follow the very plain, short, and predictable delineation that we consider optimum:

-   dom/\<object\>/\<member\>

Where \<member\> may be a property, event, or method. For example, [dom/Element/error](/dom/Element/error).

#### Weird subtrees

Some pages are designated as subtrees of the dom/apis. These are:

-   [dom/apis/audio-video](/w/index.php?title=dom/apis/audio-video&action=edit&redlink=1)
-   [dom/traversal](/w/index.php?title=dom/traversal&action=edit&redlink=1)

These subtree designations appear to be completely artificial, unlike the use of such designations in the [API Project](/WPD:Creating_API_pages), where API\_Listing pages described the common name of the API. Here, with no common API names required to distinguish the pages, these interstitials are unnecessary. The member pages of these dom "subtrees" invariably refer to their parent objects - HTMLElement, etc. - via the "Applies to" template (though these are not shown in the URL presently).

#### Interstitials

Other pages are using "interstitials" to describe the namespace type, such as the "apis" interstitial, as follows:

-   dom/apis/\<object\>/\<member\>

For example, [dom/apis/document/getElementById](/w/index.php?title=dom/apis/document/getElementById&action=edit&redlink=1). Note the object name, "document" is not capitalized, which violates our rules of capitalization.

Interstitials usually follow the "dom" namespace identifier, and are used to delineate objects and members:

-   dom/objects/\<object\>
-   dom/events/\<event\>
-   dom/methods/\<method\>
-   dom/properties/\<property\>

For example [dom/events/abort](/w/index.php?title=dom/events/abort&action=edit&redlink=1) or [dom/methods/moveTo](/w/index.php?title=dom/methods/moveTo&action=edit&redlink=1). For members, these lack any description of the objects that encapsulate them in the URL, though the reference to the parent object is maintained in the content via the "Applies to" template.

Also, within named subtrees of the dom/apis, interstitials are used to distinguish methods, properties, and events. For example, [dom/apis/audio-video/properties/type](/w/index.php?title=dom/apis/audio-video/properties/type&action=edit&redlink=1).

In the [API Project](/WPD:Creating_API_pages) we decided to eliminate these member interstitials as being unnecessary. We can follow the same reasoning for the DOM APIs.

Some pages have no interstitials at all.

-   dom/\<member\>

For example, [dom/gotpointercapture](/w/index.php?title=dom/gotpointercapture&action=edit&redlink=1).

#### Inheritance not in the URLs

Inheritance is not described in the URLs of the pages. Most pages follow this organization:

-   dom/\<object\>

For example, [dom/HTMLTrackElement](/dom/HTMLTrackElement) *not* [dom/EventTarget/Node/Element/HTMLElement/HTMLTrackElement](/w/index.php?title=dom/EventTarget/Node/Element/HTMLElement/HTMLTrackElement&action=edit&redlink=1). This is a good thing. As you can see, describing the inheritance model would make the URLs unnecessarily long without providing any useful information to the user.

### Organization solution

Proposed is the abolition of all "interstitials" and the assignment of all members to their encapsulating objects in the URLs. Even the "apis" interstitial is unnecessary (see below). To that, we would have the following first-tier designations.

-   **dom** - a listing page with all DOM objects and their summaries.

Beneath that are the DOM objects; these are of two types, **events** and **event targets**.

#### Events

All of the event types are currently organized under dom/objects, i.e. dom/objects/PointerEvent and the actual events are organized under dom/events, i.e dom/events/pointerdown.

Events logically belong under their event types (i.e. dom/PointerEvent/pointerdown or dom/Event/error). The events in [dom/PointerEvent](/dom/PointerEvent) are organized thus, and we want to describe all events this way - under their event types in the URLs. There are two fields in the Event template that capture the parent object of specific events, the Interface= field and the Event\_applies\_to= field, as shown in the example below:

{{Event |Interface=dom/objects/FocusEvent |Target=dom/Element |Default\_action= |Content= |Event\_applies\_to=dom/objects/FocusEvent |Synchronous=No |Bubbles=No |Cancelable=No }}

The trouble is that, as in the above example, the values of the Interface= and Event\_applies\_to fields need to be corrected. In the above example, the field should read, Interface=dom/FocusEvent. This is the case with all of the events, their event types are all organized under the interstitial, "objects."

So, the first task is to re-organize the event types directly under dom, i.e. dom/PointerEvent. Event type pages need to be moved out of dom/objects/ and into dom/ - for example, dom/FocusEvent. This move needs to be performed manually for all of the pages currently under [dom/objects](/w/index.php?title=dom/objects&action=edit&redlink=1).

Then, we need to edit the event pages Event\_applies\_to= field to point to the event type, for example, Event\_applies\_to=dom/UIEvent. While we're at it, do the same for the Interface= field, i.e. Interface=dom/UIEvent. Although the Interface= field appears to be unused, it should be updated for consistency.

Making these changes will cause changes to the event target pages like dom/Element. In most cases, the event pages currently specify Event\_applies\_to=\<event target page\>, i.e. Event\_applies\_to=dom/Element. This produces a list of events on the event target page. When we change the value to Event\_applies\_to=\<event type\>, i.e. Event\_applies\_to=dom/PointerEvent, the list appears on the event type page, as it should, instead.

To produce a list on the event target pages, the API\_Object template needs to be updated to generate the list based on the Target=dom/Element value. See [this issue](http://project.webplatform.org/tmpl/issues/14) for details.

Eventually we need to add a field to the Event form to display the event type (see [this issue](http://project.webplatform.org/tmpl/issues/7)).

We also considered organizing events under their targets (i.e. dom/Element/pointerdown), but found namespace collisions (dom/Element/error property collides with dom/Element/error event). Besides, events properly belong to event types, not targets, in the DOM.

#### Event targets

Event targets are such objects as Document, Element, etc.

Inheritance should not be described in the URL. Rather, all DOM objects, regardless of their "level" in the DOM, should reside on one level of the WPD URL structure. This provides for short URLs. So, we would have the following:

-   dom/HTMLTrackElement (*not* dom/EventTarget/Node/Element/HTMLElement/HTMLTrackElement)
-   dom/Navigator
-   dom/Window
-   dom/Node
-   dom/Document
-   dom/Element
-   dom/HTMLElement
-   dom/HTMLMenuElement

etc.

Going further into the namespace, all members would be organized under their parent objects. To wit:

-   current: [dom/apis/document/getElementById](/w/index.php?title=dom/apis/document/getElementById&action=edit&redlink=1) proposed: [dom/Document/getElementById](/dom/Document/getElementById)
-   current: [dom/traversal/methods/RangeException](/w/index.php?title=dom/traversal/methods/RangeException&action=edit&redlink=1) proposed: [dom/Element/RangeException](/dom/Element/RangeException)

This follows the methodology in the [API Project](/WPD:Creating_API_pages), except that API\_Listing pages are not required to describe interstitials (other than the "dom" listing page), because there is no danger of namespace conflicts that would require the use of such interstitials.

An "apis" interstitial is unnecessary. The DOM itself includes CSS, CSSOM, HTML Elements, SVG, etc., and we have already broken out the content into these top-level buckets. We don't have "dom/css/cssom" or "dom/svg." We are designating this bucket as the "dom" to mean the objects and interfaces used to program against the DOM. That these are understood to be the APIs, using "apis" as an interstitial (as in "dom/apis") is redundant.

We propose to reorganize the DOM pages (estimated at roughly 1,129 pages) according to the guidelines above. Under these guidelines, all DOM pages would follow the URL structure, "dom/\<object\>/\<member\>" where \<member\> may be a property or method, or event.

### Reorganization procedure

There are 1129 pages in the dom namespace.

-   137 in a dom/\<object\>/\<member\> pattern already (some of which may not need to move)
-   119 in dom/events
-   49 in dom/objects
-   77 in dom/apis
-   101 in dom/traversal
-   257 in dom/methods
-   336 in dom/properties

This leaves 53 pages that don't fit into any of these categories. Also, there are an additional 20 or so pages that may belong in the dom namespace and which currently reside in the apis namespace. These include the [audio-video APIs](/apis/audio-video), which need to be reviewed for members that may need to be moved into the dom namespace.

For the dom/objects pages, simply move dom/objects/\* to dom/\* - removing the "objects" interstitial.

For the dom/apis pages, most of these are part of the audio-video API, for example [dom/apis/audio-video/events/play](/w/index.php?title=dom/apis/audio-video/events/play&action=edit&redlink=1). Each of the pages in this namespace needs to be be organized under its parent DOM object - HTMLMediaElement, for example. Also, review the [audio-video APIs](/apis/audio-video) for possible moves to the dom namespace. The rest, like [dom/apis/document/getElementById](/w/index.php?title=dom/apis/document/getElementById&action=edit&redlink=1) can be moved according to the methodology outline here.

The dom/traversal pages also need to be moved under their parent objects. For example [dom/traversal/methods/cloneContents](/w/index.php?title=dom/traversal/methods/cloneContents&action=edit&redlink=1) may need to move to dom/\<parentDOMobject\>/Range. Much of the work will be in figuring out to which DOM objects these traversal members belong. If the parent DOM object can't be determined, the traversal API might belong in the [apis](/apis) namespace. Luckily, there are no event pages under dom/traversal.

#### Script

It may be possible to do some of this moving with a script. People in the community might be able to lend a hand. [[[1]](http://docs.webplatform.org/wiki/User:Frozenice%7CFrozenice) (David Kirstein) is very knowledgeable about MediaWiki and Semantic MediaWiki, and he may be able to help automate this process.

From a first-impression, it seemed the script could apply the following process to the dom pages.

-   If the page is of the API\_Object\_Method or API\_Object\_Property template type
    -   If the page's **Applies to** field is set (Method\_applies\_to= , Property\_applies\_to=)
        -   If the **Applies to** location is valid (exists)
            -   If there is no existing page in the location specified by the **Applies to** field, move the page under the location specified in that field
            -   Else if there is an existing page in the location specified by the **Applies to** field, move the page under **\<Applies-to\_field\>/duplicates**
            -   Else if there is an existing page in the location specified by **\<Applies-to\_field\>/duplicates** move the page under **\<Applies-to\_field\>/duplicates/duplicates** (and so on)
    -   For each page that links to this page
        -   Update the link to point to the page's new location.
-   Otherwise, leave the page where it is

#### Manual moving

Before moving a page, take note of the new URL, and update the links in all pages that link to the moved page. Leave no redirect.

#### Changing Inbound Links

For each page that links to the page in question, all the links on that page to the new location. All the pages that link to the target page can be found consistently with the [Special:WhatLinksHere](/Special:WhatLinksHere) page. For example:

    http://docs.webplatform.org/wiki/Special:WhatLinksHere/dom/apis/audio-video/events/play

We should leave no redirects, since page-level redirects, as opposed to server-level redirects, harm SEO.

## Amending the content

We'll deal with this after we get reorganized. To be continued...

## Unresolved issues

Need to identify the event type (i.e. KeyboardEvent) in the Event template, Overview table. ([bug](http://project.webplatform.org/tmpl/issues/7))
