This article offers a methodology for adding new API documentation pages to Web Platform Docs. It provides a process for adding several new pages -  as a branch - to the wiki. The discussion cites as an example the creation of  the [[apis/webrtc|WebRTC API]] pages.

{{TODO|Once the final methodology is in place, and the fixes cited by the TODOs are in, remove all the TODOs like this one.}}

=Listing page=

The listing page is the top-level page that introduces the subject, in this example the WebRTC API. It uses the common API listing name to identify the subject.

Most of the time, the API listing is not the proper name of an API or other element. Rather, it is a catch-all description for a group of APIs. In this example, WebRTC is a catch-all for the MediaStream, PeerConnection, and DataChannel APIs. In fact, these are catch-alls themselves. The MediaStream API is actually composed of the MediaStream, LocalMediaStream, MediaStreamTrack, and MediaStreamTrackList objects. These are the actual APIs, the named objects that have methods and properties and which the developer uses in her application.

We use the API listings as reference pages for all of the associated API objects and their members. The listing page is the parent page of the API objects. It is a reference page that associates the common name of the API (WebRTC) with its actual components (MediaStream, LocalMediaStream, etc.).

So, the listing page for the WebRTC API is '''apis/webrtc'''.

Note that the API listings, not being proper names of API objects, do not have camel-casing in URLs. So, '''apis/webrtc''' not '''apis/WebRTC'''. But MediaStream is an API object, so '''apis/webrtc/objects/MediaStream'''. See [[WPD:Manual_Of_Style#URLs|URLs]] in the [[WPD:Manual_Of_Style|Manual of Style]] for more about URLs.

You really only need one listing page. It's enough to just have '''apis/webrtc''' - you don't need '''apis/webrtc/mediastream''' (as a listing page, different from the '''apis/webrtc/objects/MediaStream''' page which represents the actual API object), '''apis/webrtc/peerconnection''', nor '''apis/webrtc/datachannel'''. All of these sub listing pages should just be represented as headings in the content of the main listing page, not as pages in their own right, as shown below. But don't leave them out; as long as they're included as sub headings, search engines can find them.

If you have only one API object and there is no other catch-all description for the API, you still have to create the listing page. So if the API name is '''MyAPI''' the URLs for the listing page and the object are, '''apis/myapi''' and '''apis/myapi/objects/MyAPI''', respectively.

Doing this allows for changes in the specification as the API is being developed. Often an API in development goes through lots of changes. Decoupling the API listing and the API objects in this fashion allows the names to change to protect the innocent.

{{Author_note|I'm not a big fan of the long URLs. But we've got to dance with the date we brought, and this is the only way currently that we have for organizing our content - through the URLs. The scheme above provides for disambiguation within the constraints of our current structure and methodology.}}

==Creating the listing page==
The [[apis/webrtc]] listing page was created as follows.
# Navigate to [[WPD:New_Page]].
# Under the '''API Lising'' page type, enter '''apis/foo'''.
#: Where '''foo''' is the name of the listing page, all lower case. See the [[WPD:Manual_Of_Style|Manual of Style]] for more information about titles and headings.
# Click the '''Create API Listing Page''' button.
# Fill out the '''Main content''' with the sub headings and names of the API objects - you can come back and create the links to them later.
&nbsp;

=Stubbing out the pages=

The best way to work on all of this is to first draw out the architecture as a hierarchy of stub pages. This allows other writers to help out and it provides you with the ability to create the links you need between pages as you fill them out.

==Creating the API Object page==
The first page to create, after the listing page, is that for the first API object; in this example, [[apis/webrtc/objects/MediaStream]].
# Navigate to [[WPD:New_Page]].
# Under the '''API Object''' page type, enter '''apis/Foo/objects/bar'''.
#: Where '''Foo''' is the name of the API listing, and '''bar''' is the name of the API object in its native case. See the [[WPD:Manual_Of_Style|Manual of Style]] for more information about titles and headings.
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

The [[apis/webrtc/objects/MediaStreamTrackList]] page displays each of these methods, properties, and events in tables generated for each member where the member has specified the MediaStreamTrackList object in the '''Applies to''' field in the '''Basic property configuration''' form. All you have to do to generate the tables is to specify the parent API object for the member in that form.

When you are stubbing out the pages, if you do nothing else in the member pages, you must specify the parent API object in the '''Applies to''' field.

Oh, that and mark them as stubs, of course!

=Filling in the pages=

Once you've got the pages all in place, you can go back and start filling them in. Most of the time, how to do this is obvious. But where it may be unclear, this section attempts to clarify.

==Listing page content==

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

The listing page's main content should provide both an elaborate description of the APIs and links to other conceptual or tutorial pages.

{{TODO|The API_Listing template '''Usage''' section should be retitled as '''Overview''' and given an h1 header.}}

It also will have a summary table of the API objects included in the API. These are generated when each object's '''Applies to''' field specifies the API listing to which it belongs.

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
{{TODO|The ambiguity this creates and it's ramifications for our dom architecture are the subject for another day - in short, yeah, we need to fix that, too.}}

The best practice is to reference the extra-API facility (couldn't think of a better name) in the main content of the pertinent API listing and object pages. For the WebRTC API, the [[apis/webrtc/objects/LocalMediaStream|LocalMediaStream]] object page must have a reference to [[dom/methods/getUserMedia|getUserMedia()]]. So should any tutorials about using the API, and these tutorials should be referenced in the API listing and object pages as well.