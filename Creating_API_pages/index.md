This article provides a methodology for adding new API documentation pages to Web Platform Docs. It provides a process for adding several new pages -  as a branch - to the wiki. The discussion cites as an example the creation of  the [[apis/webrtc|WebRTC API]] pages.

=Listing page=

The listing page is the top-level page that introduces the subject, in this example the WebRTC API. It uses the common API listing name to identify the subject.

Most of the time, the API listing is not the proper name of an API or other element. Rather, it is a catch-all description for a group of APIs. In this example, WebRTC is a catch-all for the MediaStream, PeerConnection, and DataChannel APIs. In fact, these are catch-alls themselves. The MediaStream API is actually composed of the MediaStream, LocalMediaStream, MediaStreamTrack, and MediaStreamTrackList objects. These are the actual APIs, the named objects that have methods and properties and which the developer uses in her application.

We use the API listings as reference pages for all of the associated API objects and their members. The listing page is the parent page of the API objects. It is a reference page that associates the common name of the API (WebRTC) with its actual components (MediaStream, LocalMediaStream, etc.).

So, the listing page for the WebRTC API is '''apis/webrtc'''.

Note that the API listings, not being proper names of API objects, do not have camel-casing in URLs. So, '''apis/webrtc''' not '''apis/WebRTC'''. But MediaStream is an API object, so '''apis/webrtc/MediaStream'''. See [[WPD:Manual_Of_Style#URLs|URLs]] in the [[WPD:Manual_Of_Style|Manual of Style]] for more about URLs.

You really only need one listing page. It's enough to just have '''apis/webrtc''' - you don't need '''apis/webrtc/peerconnection''', '''apis/webrtc/datachannel''', nor '''apis/webrtc/mediastream''' (as a listing page, different from the '''apis/webrtc/MediaStream''' page which represents the actual API object - more on that below). All of these sub listing pages should just be represented as headings in the content of the main listing page, not as pages in their own right, as shown below. But don't leave these names out; they are valuable as keywords, and as long as they're included as sub headings, search engines can find them.

If you have only one API object and there is no other catch-all description for the API, you still have to create the listing page. So if the API name is '''MyAPI''' the URLs for the listing page and the object page are, '''apis/myapi''' and '''apis/myapi/MyAPI''', respectively.

Doing this allows for changes in the specification as the API is being developed. Often an API in development goes through lots of changes. Decoupling the API listing and the API objects in this fashion allows the names to change to protect the innocent.

The organization of the '''apis''' namespace, therefore, is as follows:

:apis
:apis/<apilist>
:apis/<apilist>/<apiObject>/<event>
:apis/<apilist>/<apiObject>/<method>
:apis/<apilist>/<apiObject>/<property>

See [[Creating the API Object Method, Property, and Event pages]] for an example.

==Creating the listing page==
The [[apis/webrtc]] listing page was created as follows.
# Navigate to [[WPD:New_Page]].
# Under the '''API Lising''' page type, enter '''apis/foo'''.
#: Where '''foo''' is the name of the listing page, all lower case (as in webrtc). See the [[WPD:Manual_Of_Style|Manual of Style]] for more information about titles and headings.
# Click the '''Create API Listing Page''' button.
# Fill out the '''Main content''' with the sub headings and names of the API objects - you can come back and create the links to them later.
&nbsp;

=Stubbing out the pages=

The best way to work on all of this is to first draw out the architecture as a hierarchy of stub pages. This allows other writers to help out and it provides you with the ability to create the links you need between pages as you fill them in.

==Creating the API Object page==
The first page to create, after the listing page, is that for the first API object; in this example, [[apis/webrtc/MediaStream]].
# Navigate to [[WPD:New_Page]].
# Under the '''API Object''' page type, enter '''apis/foo/barFly'''.
#: Where '''foo''' is the name of the API listing (webrtc), and '''barFly''' is the name of the API object in its native case (as in MediaStream). See the [[WPD:Manual_Of_Style|Manual of Style]] for more information about titles and headings.
# Click the '''Create API Object Page''' button.
# Mark the page as a stub.

==Creating the API Object Method, Property, and Event pages==
The API Object page lists all of the members (properties, methods, and events) for the object in tables that summarize these members. Each member's information is held in a separate page, the pertinent sections of which are drawn into the summary tables. You have to create a page for each member using [[WPD:New_Page]].

The WPD:New_Page page describes how to create the URL for each page. For example, the [[apis/webrtc/MediaStreamTrackList|MediaStreamTrackList]] object has the following members, shown with their full paths:
* Methods
** [[apis/webrtc/MediaStreamTrackList/add]]
** [[apis/webrtc/MediaStreamTrackList/item]]
** [[apis/webrtc/MediaStreamTrackList/remove]]
* Properties
** [[apis/webrtc/MediaStreamTrackList/length]]
** [[apis/webrtc/MediaStreamTrackList/onaddtrack]]
** [[apis/webrtc/MediaStreamTrackList/onremovetrack]]
* Events
** [[apis/webrtc/MediaStreamTrackList/addtrack]]
** [[apis/webrtc/MediaStreamTrackList/removetrack]]

When you create the page, you specify the full path - per the above - in the New_Page page.

'''Note:''' While we are reasonably confident that there will be no collisions, for example a property and an event of the same name, we are resolved to deal with these by inserting identifying labels, for example:

* apis/myapi/myAPI/void-property
* apis/myapi/myAPI/void-method

Such identifiers, however, are the exception, not the rule.

{{TODO|The form input fields in the New_Page page need to be wider to display longer paths.}}

The [[apis/webrtc/MediaStreamTrackList]] page displays each of these methods, properties, and events in tables generated for each member where the member has specified the MediaStreamTrackList object in the '''Applies to''' field in the '''Basic property configuration''' form. All you have to do to generate the tables is to specify the parent API object for the member in that form.

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
Describe the MediaStream API. Provide links to the appropriate API objects, in this example: LocalMediaStream, </nowiki>
 <nowiki>MediaStream, MediaStreamTrack, and MediaStreamTrackList.
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

{{TODO|The API_Listing template needs to include the Compatibility Section and import compat tables. Note that the import compat tables does not appear to work currently.}}

==Object page content==
 
The object page is pretty straight-forward. Here you'll want to explain how to use the object and its relationship to the other objects in the API.

{{TODO|The API_Object template needs a '''Content''' section - as in the Basic_Page template.}}

For now, just use the Usage section.

{{TODO|The API_Object template needs an '''Applies to''' field to which the summary table in the API_Listing page can refer to list all of the objects in the API listing page.}}

{{TODO|In the API_Object template, '''Subclasses''' should be changed to '''Inherits from''' for greater accuracy and clarity.}}

==Object sub-page content==

This covers issues common to all sub pages of the object page, events, methods, and properties pages.

===Return value data type===

In the '''Basic property configuration''' form, for the '''Return value data type''' field you specify the data type of the object by selecting it from the drop-down menu. However, if the type is not in the list, you must edit the '''Property:Javascript_data_type''' and add the data type to the list. When you add types to the list, be sure to maintain the alphabetical order.

{{TODO|The problems with this are, 1 - keeping the list in some order that makes sense (alphabetical), and 2 - dealing with a potentially endless list of types. We need to come up with a better way of specifying the type if it is not one of the primitive types. Perhaps an additional text input field under the drop-down where you can specify the type if you choose "Other" from the drop-down.}}

==Object method page content==

Again, pretty straight-forward.

{{TODO|The API__Object_Method template needs greater clarity in using the '''Syntax''' section.}}

{{TODO|The API_Object_Method template needs a field for '''Exceptions'''.}}

==Object property page content==

Another straight-forward form.

Constants often define the possible values of an object property. See [[apis/webrtc/MediaStreamTrack/readyState|this]] for an example of how they are treated. 

{{TODO|The API__Object_Property template needs greater clarity in using the '''Syntax''' section. Need to describe event handler.}}

==Object event page content==

Again, straight-forward.

{{TODO|The Event template: it's not clear how the values in the '''Overview Table''' get populated. For APIs - as opposed to DOM events - we may need a different form/template.}}

==Referencing extra-API facilities==

Sometimes an API includes methods that are called on objects not in the API. In our WebRTC example, this is the case with [[dom/methods/getUserMedia|getUserMedia()]] which is a method of the DOM Navigator object. In WebRTC, you call getUserMedia() to get a [[apis/webrtc/LocalMediaStream|LocalMediaStream]] object for the user's audio and video data.

Strictly speaking, getUserMedia() does not belong to the WebRTC API, though it was developed to accommodate WebRTC. There is no semantic way to include getUserMedia() as a method of any object in the WebRTC API. The getUserMedia() method must be added to the wiki under [[dom/methods]] and as a member of [[dom/navigator]].
{{TODO|The ambiguity this creates and it's ramifications for our dom architecture are the subject for another day - in short, yeah, we need to fix this, too - as in dom/objects/navigator/methods/getUserMedia.}}

The best practice is to reference the extra-API facility (couldn't think of a better name) in the main content of the pertinent API listing and object pages. For the WebRTC API, the [[apis/webrtc/LocalMediaStream|LocalMediaStream]] object page must have a reference to [[dom/methods/getUserMedia|getUserMedia()]]. So should any tutorials about using the API, and these tutorials should be referenced in the API listing and object pages as well.