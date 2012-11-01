This article offers a methodology for adding new pages to Web Platform Docs. It provides a process for adding several new pages -  as a branch - to the wiki. The discussion cites as an example the creation of  the [[/apis/webrtc/ | WebRTC API]] pages.

=Landing page=

The landing page is the top-level page that introduces the subject, in this example the WebRTC API. Most of the time, this page is not the proper name of an API or other element. Rather, it is a catch-all description for a group of APIs. In this example, WebRTC is a catch-all for the MediaStream, PeerConnection, and DataChannel APIs. To make matters worse, these are catch-alls themselves. The MediaStream API is actually composed of the MediaStream, LocalMediaStream, MediaStreamTrack, and MediaStreamTrackList objects. These are the actual APIs, the named objects that have methods and properties and which the developer uses in her application.

We want to associate all of the objects and their members properly by organizing the content hierarchically with the objects as parents and their members as child pages. It serves no useful purpose to put those objects under the landing pages - the result is an artificial representation and long URLs that leave all the important bits hidden in the browser's navigation field.

So, instead of '''apis/webrtc/mediastream/LocalMediaStream''' the URL of the page should read, '''apis/LocalMediaStream'''.

The landing pages should be at the same level in the structure as the API objects. So, '''apis/webrtc''' and '''apis/LocalMediaStream'''.

Note that landing pages, not being proper names of API objects, do not have camel-casing in URLs. So, '''apis/webrtc''' not '''apis/WebRTC'''.

You really only need one landing page. It's enough to just have '''apis/webrtc''' - you don't need '''apis/mediastream''' (as a landing page, different from the '''apis/MediaStream''' page which represents the actual API object), '''apis/peerconnection''', or '''apis/datachannel'''. All of these sub landing pages should just be represented as headings in the main landing page, not pages in their own right.

The landing page then lists the APIs as links - under headings, if necessary - like this:
<nowiki>
<title>WebRTC API</title>
</nowiki>
<nowiki><br /></nowiki>
<nowiki>
   <h1>MediaStream API</h1>
</nowiki>
<nowiki>
   <a href...>MediaStream</a>
</nowiki>
<nowiki>
   <a href...>LocalMediaStream</a>
</nowiki>
<nowiki>
   <a href...>
</nowiki>
<nowiki>
   <a href...>MediaStreamTrack</a>
</nowiki>