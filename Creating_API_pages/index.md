This article offers a methodology for adding new pages to Web Platform Docs. It provides a process for adding several new pages -  as a branch - to the wiki. The discussion cites as an example the creation of  the [[apis/webrtc|WebRTC API]] pages.

=Listing page=

The listing page is the top-level page that introduces the subject, in this example the WebRTC API. Most of the time, this page is not the proper name of an API or other element. Rather, it is a catch-all description for a group of APIs. In this example, WebRTC is a catch-all for the MediaStream, PeerConnection, and DataChannel APIs. To make matters worse, these are catch-alls themselves. The MediaStream API is actually composed of the MediaStream, LocalMediaStream, MediaStreamTrack, and MediaStreamTrackList objects. These are the actual APIs, the named objects that have methods and properties and which the developer uses in her application.

We want to associate all of the objects and their members properly by organizing the content hierarchically with the objects as parents and their members as child pages. It serves no useful purpose to put those objects under the listing pages - the result is an artificial representation and long URLs that leave all the important bits hidden at the end of the browser's navigation field. In other words, the listing page is not the parent page of the API objects. Rather, it is a reference page that associates the common name of the API (WebRTC) with its actual components (MediaStream, LocalMediaStream, etc.).

So, instead of '''apis/webrtc/mediastream/LocalMediaStream''' the URL of the page should read, '''apis/LocalMediaStream'''.

The listing page should be at the same level in the structure as the API objects. So, '''apis/webrtc''' and '''apis/LocalMediaStream'''.

Note that the API listings, not being proper names of API objects, do not have camel-casing in URLs. So, '''apis/webrtc''' not '''apis/WebRTC'''. But MediaStream is an API object, so '''apis/MediaStream''' (it is also the name of the API listing that is represented in all lower case). See [[WPD:Manual_Of_Style#URLs|URLs]] in the [[WPD:Manual_Of_Style|Manual of Style]].

You really only need one listing page. It's enough to just have '''apis/webrtc''' - you don't need '''apis/mediastream''' (as a listing page, different from the '''apis/MediaStream''' page which represents the actual API object), '''apis/peerconnection''', nor '''apis/datachannel'''. All of these sub listing pages should just be represented as headings in the main listing page, not as pages in their own right, like this:
 <nowiki>
<title>WebRTC API</title>
...
Some nice things about the API.
=MediaStream API=
More niceties.
        [[apis/MediaStream|MediaStream]]
        [[apis/LocalMediaStream|LocalMediaStream]]
        [[apis/MediaStreamTrack|MediaStreamTrack]]
        [[apis/MediaStreamTrackList|MediaStreamTrackList]]
=PeerConnection API=
 More niceties.
        [[apis/RTCPeerConnection|RTCPeerConnection]]
    etc.</nowiki>
The listing page then lists the APIs as links - under headings, if necessary - along with all the verbiage about the API. But of course, you have to first create all those pages before you can link to them.

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
The first page to create, after the listing page, is that for the first API object; in this example, [[apis/MediaStream]].
# Navigate to [[WPD:New_Page]].
# Under the '''API Object''' page type, enter '''apis/Foo'''.
#: Where '''Foo''' is the name of the API object, in its native case. See the [[WPD:Manual_Of_Style|Manual of Style]] for more information about titles and headings.
# Click the '''Create API Object Page''' button.
# Mark the page as a stub.

==Creating the API Object Method, Property, and Event pages==
The API Object page lists all of the members (properties, methods, and events) for the object in tables that summarize the members as represented their own pages. You have to create a page for each member using the [[WPD:New_Page]].