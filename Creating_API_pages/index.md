This article offers a methodology for adding new API documentation pages to Web Platform Docs. It provides a process for adding several new pages -  as a branch - to the wiki. The discussion cites as an example the creation of  the [[apis/webrtc|WebRTC API]] pages.

{{TODO|Once the final methodology is in place, and the fixes cited by the TODOs are in, remove all the TODOs like this one.}}

{{Author_note|These will be removed, too, once the final methodology is agreed upon. You can ignore them if you don't want to listen to me rattle on.}}

=The  Problem=

{{TODO|This "Problem" section will be removed from the final, user-facing page.}}

The way our '''apis''' namespace is drawn out leaves us short of accomplishing the goals we had for the URL architecture. We wanted URLs that delineated the hierarchies inherent with the coding artifacts in the documentation, for the purpose of storing the content in a predictable, logical fashion, and for the purpose of providing the user with equally predictable, logical navigation.

The scheme in place currently, however, omits some key elements needed to achieve those objectives, and results in ambiguous or conflicting delineations.

For the purposes of comparison, this article will cite examples from the [[apis/indexedDB]] namespace. Other APIs in the '''apis''' namespace currently follow the same structure.

==No differentiation between objects and listings==

Our WPD:New_Page page provides for the creation of API Listing pages that can describe the API and list all of the API objects in it. The listing page can distinguish the common name of the API (IndexedDB) from its member objects (IDBFactory, IDBCursor, etc.) With the current structure of the '''apis''' namespace, there is a problem with differentiation between API listings and API objects.

Sometimes this is a problem with the case of the URL artifact. For example, the API listing should be '''indexeddb''' instead of '''indexedDB''' where the camel casing implies an object. (All lower case implies a listing - see [[WPD:Manual_Of_Style#URLs|URLs]] in the Manual of Style.)

Sometimes it is a problem with a missing '''objects''' namespace artifact identifier - but not always - as in [[apis/timing/objects/performance]]. Most of the APIs appear to missing this identifier - at least if you look at the [[apis]] page. For example, [[apis/indexedDB/IDBFactory]] would be better understood as '''apis/indexedDB/objects/IDBFactory'''.

We need to consistently distinguish API objects the same way we distinguish events, methods, and properties, by placing the '''objects''' identifier between the API listing and API object, as in [[apis/webrtc/objects/MediaStream]]. Below in this document is shown how API listing pages can be used to solve these problems.

== Delineation is inaccurate ==

By saying, '''apis/indexedDB/methods/openKeyCursor''' the URL is implying that the openKeyCursor method belongs to an object called indexedDB. It does not. Rather it belongs to the IDBIndex object. All of the properties, methods, and events of ''every api'' are collocated likewise under one namespace artifact. In the case of IndexedDB, they read as follows:

* apis/indexedDB/events
* apis/indexedDB/methods
* apis/indexedDB/properties

Instead, these should be assigned to their respective API objects, as in '''apis/indexeddb/objects/indexedDB/methods/open'''. Notice how this both properly associates the '''open''' method with the '''indexedDB''' object ''and'' differentiates the '''indexeddb''' API listing from the '''indexedDB''' object.

While the templates do provide for an association between the event, method, or property with its parent object via the '''Applies to''' field, this is not implemented consistently. For many object members the '''Applies to''' field doesn't work properly. For example, [[apis/indexedDB/properties/direction]]. Although the '''Applies to''' field does specify '''apis/indexedDB/IDBCursor''' the reference does not appear in the generated page. Therefore, the user has no idea how to use this particular property, given the documentation.

If the '''direction''' page had as its URL, '''apis/indexeddb/objects/IDBCursor/properties/direction''' the developer would know at a glance to which object this property belongs.

==Dublicate names in conflict==

Consider the following two pages. They both describe different properties of the same name for different objects.
* [[apis/webrtc/objects/MediaStream/properties/label]]
* [[apis/webrtc/objects/MediaStreamTrack/properties/label]]

No, these aren't the same, but under the current architecture, one of 'em's gotta go. You can't have two pages with the same name:
* apis/webrtc/properties/label

Somehow this fundamental principle of namespace architecture got missed in our '''apis'''.

==Template and form fixes needed==

To fill out the '''apis''' for better usability, we'll need to make some minor modifications to the templates and forms that comprise the pages.  These are cited as TODOs in the following sections, where the methodology for creating API pages is proposed as a solution to the problems cited here.

{{Author_note|Keep in mind that while the rest of this document is a proposed solution, it is ultimately intended to become a guide for users creating new pages. That means there will be a lot of "well, duh" moments for you as an expert on this wiki. Bear with us.}}

=Listing page=

The listing page is the top-level page that introduces the subject, in this example the WebRTC API. It uses the common API listing name to identify the subject.

Most of the time, the API listing is not the proper name of an API or other element. Rather, it is a catch-all description for a group of APIs. In this example, WebRTC is a catch-all for the MediaStream, PeerConnection, and DataChannel APIs. In fact, these are catch-alls themselves. The MediaStream API is actually composed of the MediaStream, LocalMediaStream, MediaStreamTrack, and MediaStreamTrackList objects. These are the actual APIs, the named objects that have methods and properties and which the developer uses in her application.

We use the API listings as reference pages for all of the associated API objects and their members. The listing page is the parent page of the API objects. It is a reference page that associates the common name of the API (WebRTC) with its actual components (MediaStream, LocalMediaStream, etc.).

So, the listing page for the WebRTC API is '''apis/webrtc'''.

Note that the API listings, not being proper names of API objects, do not have camel-casing in URLs. So, '''apis/webrtc''' not '''apis/WebRTC'''. But MediaStream is an API object, so '''apis/webrtc/objects/MediaStream'''. See [[WPD:Manual_Of_Style#URLs|URLs]] in the [[WPD:Manual_Of_Style|Manual of Style]] for more about URLs.

You really only need one listing page. It's enough to just have '''apis/webrtc''' - you don't need '''apis/webrtc/mediastream''' (as a listing page, different from the '''apis/webrtc/objects/MediaStream''' page which represents the actual API object), '''apis/webrtc/peerconnection''', nor '''apis/webrtc/datachannel'''. All of these sub listing pages should just be represented as headings in the content of the main listing page, not as pages in their own right, as shown below. But don't leave them out; as long as they're included as sub headings, search engines can find them.

If you have only one API object and there is no other catch-all description for the API, you still have to create the listing page. So if the API name is '''MyAPI''' the URLs for the listing page and the object are, '''apis/myapi''' and '''apis/myapi/objects/MyAPI''', respectively.

Doing this allows for changes in the specification as the API is being developed. Often an API in development goes through lots of changes. Decoupling the API listing and the API objects in this fashion allows the names to change to protect the innocent.

{{Author_note|I'm not a big fan of the long, verbose URLs. But we've got to dance with the date we brought, and this is the only way currently that we have for organizing our content - through the URLs. The scheme above provides for disambiguation within the constraints of our current structure and methodology. Long term, I'd like to see us move away from rigid URL-dependence and toward flexible, keyword-based, multi-faceted, seach-served content. These URLs provide a path toward that future whereby they get converted into metadata via some automated process.}}

==Creating the listing page==
The [[apis/webrtc]] listing page was created as follows.
# Navigate to [[WPD:New_Page]].
# Under the '''API Lising''' page type, enter '''apis/foo'''.
#: Where '''foo''' is the name of the listing page, all lower case (webrtc). See the [[WPD:Manual_Of_Style|Manual of Style]] for more information about titles and headings.
# Click the '''Create API Listing Page''' button.
# Fill out the '''Main content''' with the sub headings and names of the API objects - you can come back and create the links to them later.
&nbsp;

=Stubbing out the pages=

The best way to work on all of this is to first draw out the architecture as a hierarchy of stub pages. This allows other writers to help out and it provides you with the ability to create the links you need between pages as you fill them out.

==Creating the API Object page==
The first page to create, after the listing page, is that for the first API object; in this example, [[apis/webrtc/objects/MediaStream]].
# Navigate to [[WPD:New_Page]].
# Under the '''API Object''' page type, enter '''apis/foo/objects/barFly'''.
#: Where '''foo''' is the name of the API listing (webrtc), and '''barFly''' is the name of the API object in its native case (MediaStream). See the [[WPD:Manual_Of_Style|Manual of Style]] for more information about titles and headings.
# Click the '''Create API Object Page''' button.
# Mark the page as a stub.

==Creating the API Object Method, Property, and Event pages==
The API Object page lists all of the members (properties, methods, and events) for the object in tables that summarize these members. Each member's information is held in a separate page, the pertinent sections of which are drawn into the summary tables. You have to create a page for each member using [[WPD:New_Page]].

The WPD:New_Page page describes how to create the URL for each page. For example, the [[apis/webrtc/objects/MediaStreamTrackList|MediaStreamTrackList]] object has the following members, shown with their full paths:
* Methods
** [[apis/webrtc/objects/MediaStreamTrackList/methods/add]]
** [[apis/webrtc/objects/MediaStreamTrackList/methods/item]]
** [[apis/webrtc/objects/MediaStreamTrackList/methods/remove]]
* Properties
** [[apis/webrtc/objects/MediaStreamTrackList/properties/length]]
** [[apis/webrtc/objects/MediaStreamTrackList/properties/onaddtrack]]
** [[apis/webrtc/objects/MediaStreamTrackList/properties/onremovetrack]]
* Events
** [[apis/webrtc/objects/MediaStreamTrackList/events/addtrack]]
** [[apis/webrtc/objects/MediaStreamTrackList/events/removetrack]]

When you create the page, you specify the full path - per the above - in the New_Page page.

{{TODO|The form input fields in the New_Page page need to be wider to display longer paths.}}

The [[apis/webrtc/objects/MediaStreamTrackList]] page displays each of these methods, properties, and events in tables generated for each member where the member has specified the MediaStreamTrackList object in the '''Applies to''' field in the '''Basic property configuration''' form. All you have to do to generate the tables is to specify the parent API object for the member in that form.

When you are stubbing out the pages, if you do nothing else in the member pages, you must specify the parent API object in the '''Applies to''' field.

Oh, that and mark them as stubs, of course!

=Filling in the pages=

Once you've got the pages all in place, you can go back and start filling them in. Most of the time, how to do this is obvious. But where it may be unclear, this section attempts to clarify.

==Object listing page content==

The API listing page provides a broad description of the API. If there are further sub divisions of the API, include them as sub headings. This preserves the API's design - as it is described on w3.org - and allows the content to respond to search effectively. The main content field for the WebRTC API page (apis/webrtc) would look like the following:

 <nowiki>
<title>WebRTC API</title>
...
Describe the WebRTC API.
=MediaStream API=
Describe the MediaStream API. Provide links to the appropriate API objects, in this example:
=PeerConnection API=
 Describe the PeerConnection API.
=DataChannel API=
    etc.</nowiki>

This is just an outline. Here's the [[apis/webrtc|actual content of the apis/webrtc page]].

The listing page's main content should provide both an elaborate description of the APIs and links to other conceptual or tutorial pages.

{{TODO|The API_Listing template needs a '''Content''' section - as in the Basic_Page template.}}

It also will have a summary table of the API objects included in the API. These are generated when each object's '''Applies to''' field specifies the API listing to which it belongs.

{{TODO|The API_Listing template needs an '''API Name/Summary''' table to list all of the API objects. Move the '''Subpages''' table to the bottom of the template.}}

The listing page should also include compatibility tables for each of the API objects.

{{TODO|The API_Listing template needs to include the Compatibility Section and import compat tables. Note that the import compat tables does not appear to work currently. See below}}

==Object page content==
 
The object page is pretty straight-forward. Here you'll want to explain how to use the object and its relationship to the other objects in the API.

{{TODO|The API_Object template needs an '''Applies to''' field to which the summary table in the API_Listing page can refer to list all of the objects in the API listing page.}}

{{TODO|The API_Object_* templates '''Applies to''' field ghost text needs to be updated for this new URL structure.}}

{{TODO|In the API_Object template, '''Subclasses''' should be changed to '''Inherits from''' for greater accuracy and clarity.}}

==Object method page content==

Again, pretty straight-forward.

{{TODO|The API__Object_Method template needs greater clarity in using the '''Syntax''' section.}}

[[TODO|The API_Object_Method template needs a field for '''Exceptions'''.}}

==Object property page content==

Another straight-forward form.

{{TODO|'''Bug''' The API_Object_Property page does not display the parent object, i.e. "Property of X object."}}

{{TODO|The API__Object_Property template needs greater clarity in using the '''Syntax''' section. Need to describe event handler.}}

==Object event page content==

Again, straight-forward.

{{TODO|The Event template: it's not clear how the values in the '''Overview Table''' get populated.

==Intermediate pages==

By virtue of the URL architecture we impose, there will be empty pages created as you assign the member pages to their URLs. This is the case with the '''objects''', '''properties''', '''methods''', and '''events''' intermediate pages in the '''apis''' namespace.

You need to fill in these pages to avoid confusing the reader and to provide for navigation.

===Filling with a redirect===

The easiest way to deal with empty intermediate pages is to redirect them back to the API object page, as we do on the [[apis/webrtc/objects/MediaStream/properties]] page. This page has only the following line to redirect the page back to the Properties section of the API object page:
 <nowiki>
#REDIRECT [[apis/webrtc/objects/MediaStream#Properties]]</nowiki>

This has the advantage of providing not only the list of properties, but all of the information about the API without you having to rewrite it.

If you ever have to remove the redirect, navigate to the page with '''&redirect=no''' appended to the URL. For example, <nowiki>http://docs.webplatform.org/wiki/apis/webrtc/objects/MediaStream/properties&redirect=no</nowiki>. You can then edit the page as needed.

===Filling with a query===

To fill in the page, you could also plug in a Semantic MediaWiki query, as we do with the '''apis''' page, like this:
 <nowiki>
{{API_Listing
|Query=[[Category:API_Objects]]
|Use_page_title=No
|List_all_subpages=Yes
}}</nowiki>

You could do this on a '''properties''' page with the query reading as follows:
 <nowiki>
Query=[[Category:API_Object_Properties]]</nowiki>

But the disadvantage of doing it this way is that you don't get anything but a table of links. You still have to write some adorning text to explain the page and so forth.

==Referencing extra-API facilities==

Sometimes an API includes methods that are called on objects not in the API. In our WebRTC example, this is the case with [[dom/methods/getUserMedia|getUserMedia()]] which is a method of the DOM Navigator object. In WebRTC, you call getUserMedia() to get a [[apis/webrtc/objects/LocalMediaStream|LocalMediaStream]] object for the user's audio and video data.

Strictly speaking, getUserMedia() does not belong to the WebRTC API, though it was developed to accommodate WebRTC. There is no semantic way to include getUserMedia() as a method of any object in the WebRTC API. The getUserMedia() method must be added to the wiki under [[dom/methods]] and as a member of [[dom/navigator]].
{{TODO|The ambiguity this creates and it's ramifications for our dom architecture are the subject for another day - in short, yeah, we need to fix this, too - as in dom/objects/navigator/methods/getUserMedia.}}

The best practice is to reference the extra-API facility (couldn't think of a better name) in the main content of the pertinent API listing and object pages. For the WebRTC API, the [[apis/webrtc/objects/LocalMediaStream|LocalMediaStream]] object page must have a reference to [[dom/methods/getUserMedia|getUserMedia()]]. So should any tutorials about using the API, and these tutorials should be referenced in the API listing and object pages as well.