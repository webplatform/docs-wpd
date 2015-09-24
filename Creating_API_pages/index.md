---
title: 'Creating API documentation guide'
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - dom/apis/document/getElementById
    - dom/methods/getUserMedia
    - dom/methods
uri: 'WPD:Creating API pages'
---

This article explains how to add new API documentation pages to Web Platform Docs. It provides a process for adding several new pages - as a branch - to the wiki. The discussion cites as an example the creation of the [WebRTC API](/apis/webrtc) pages.

These instructions support the work outlined in the [API doc proposal](/WPD:Proposals/api_docs).

## Listing page

The listing page is the top-level page that introduces the subject, in this example the WebRTC API. It uses the common API listing name to identify the subject.

Most of the time, the API listing is not the proper name of an API or other element. Rather, it is a catch-all description for a group of APIs. In this example, WebRTC is a catch-all for the MediaStream, PeerConnection, and DataChannel APIs. In fact, these are catch-alls themselves. The MediaStream API is actually composed of the MediaStream, LocalMediaStream, MediaStreamTrack, and MediaStreamTrackList objects. These are the actual APIs, the named objects that have methods and properties and which the developer uses in her application.

We use the API listings as reference pages for all of the associated API objects and their members. The listing page is the parent page of the API objects. It is a reference page that associates the common name of the API (WebRTC) with its actual components (MediaStream, LocalMediaStream, etc.).

So, the listing page for the WebRTC API is **apis/webrtc**.

Note that the API listings, not being proper names of API objects, do not have camel-casing in URLs. So, **apis/webrtc** not **apis/WebRTC**. But MediaStream is an API object, so **apis/webrtc/MediaStream**. See [URLs](/WPD:Manual_Of_Style#URLs) in the [Manual of Style](/WPD:Manual_Of_Style) for more about URLs.

You really only need one listing page. It's enough to just have **apis/webrtc** - you don't need **apis/webrtc/peerconnection**, **apis/webrtc/datachannel**, nor **apis/webrtc/mediastream** (as a listing page, different from the **apis/webrtc/MediaStream** page which represents the actual API object - more on that below). All of these sub listing pages should just be represented as headings in the content of the main listing page, not as pages in their own right, as shown below. But don't leave these names out; they are valuable as keywords, and as long as they're included as sub headings, search engines can find them.

If you have only one API object and there is no other catch-all description for the API, you still have to create the listing page. So if the API name is **MyAPI** the URLs for the listing page and the object page are, **apis/myapi** and **apis/myapi/MyAPI**, respectively.

Doing this allows for changes in the specification as the API is being developed. Often an API in development goes through lots of changes. Decoupling the API listing and the API objects in this fashion allows the names to change to protect the innocent.

The organization of the **apis** namespace, therefore, is as follows:

<dl>
<dd>
apis
</dd>
<dd>
apis/\<apilist\>
</dd>
<dd>
apis/\<apilist\>/\<apiObject\>/\<event\>
</dd>
<dd>
apis/\<apilist\>/\<apiObject\>/\<method\>
</dd>
<dd>
apis/\<apilist\>/\<apiObject\>/\<property\>
</dd>
</dl>

See [Property and Event Pages section below](#Creating_the_API_Object_Method.2C_Property.2C_and_Event_pages) for an example.

### Creating the listing page

The [apis/webrtc](/apis/webrtc) listing page was created as follows.

1.  Navigate to [WPD:New\_Page](/WPD:New_Page).
2.  Under the **API Lising** page type, enter **apis/foo**.
    <dl>
    <dd>
    Where **foo** is the name of the listing page, all lower case (as in webrtc). See the [Manual of Style](/WPD:Manual_Of_Style) for more information about titles and headings.
    </dd>
3.  Click the **Create API Listing Page** button.
4.  Fill out the **Main content** with the sub headings and names of the API objects - you can come back and create the links to them later.

 

## Stubbing out the pages

The best way to work on all of this is to first draw out the architecture as a hierarchy of stub pages. This allows other writers to help out and it provides you with the ability to create the links you need between pages as you fill them in.

### Creating the API Object page

The first page to create, after the listing page, is that for the first API object; in this example, [apis/webrtc/MediaStream](/apis/webrtc/MediaStream).

1.  Navigate to [New_Page](/WPD/New_Page).
2.  Under the **API Object** page type, enter **apis/foo/barFly**.
    <dl>
    <dd>
    Where **foo** is the name of the API listing (webrtc), and **barFly** is the name of the API object in its native case (as in MediaStream). See the [Manual of Style](/WPD:Manual_Of_Style) for more information about titles and headings.
    </dd>
3.  Click the **Create API Object Page** button.
4.  Mark the page as a stub.

 

### Creating the API Object Method, Property, and Event pages

The API Object page lists all of the members (properties, methods, and events) for the object in tables that summarize these members. Each member's information is held in a separate page, the pertinent sections of which are drawn into the summary tables. You have to create a page for each member using [WPD:New\_Page](/WPD:New_Page).

The WPD:New\_Page page describes how to create the URL for each page. For example, the [MediaStreamTrackList](/apis/webrtc/MediaStreamTrackList) object has the following members, shown with their full paths:

-   Methods
    -   [apis/webrtc/MediaStreamTrackList/add](/apis/webrtc/MediaStreamTrackList/add)
    -   [apis/webrtc/MediaStreamTrackList/item](/apis/webrtc/MediaStreamTrackList/item)
    -   [apis/webrtc/MediaStreamTrackList/remove](/apis/webrtc/MediaStreamTrackList/remove)
-   Properties
    -   [apis/webrtc/MediaStreamTrackList/length](/apis/webrtc/MediaStreamTrackList/length)
    -   [apis/webrtc/MediaStreamTrackList/onaddtrack](/apis/webrtc/MediaStreamTrackList/onaddtrack)
    -   [apis/webrtc/MediaStreamTrackList/onremovetrack](/apis/webrtc/MediaStreamTrackList/onremovetrack)
-   Events
    -   [apis/webrtc/MediaStreamTrackList/addtrack](/apis/webrtc/MediaStreamTrackList/addtrack)
    -   [apis/webrtc/MediaStreamTrackList/removetrack](/apis/webrtc/MediaStreamTrackList/removetrack)

When you create the page, you specify the full path - per the above - in the New\_Page page.

**Note:** While we are reasonably confident that there will be no collisions, for example a property and an event of the same name, we are resolved to deal with these by inserting identifying labels, for example:

-   apis/myapi/myAPI/void-property
-   apis/myapi/myAPI/void-method

Such identifiers, however, are the exception, not the rule.

**TODO**: The form input fields in the New\_Page page need to be wider to display longer paths.

The [apis/webrtc/MediaStreamTrackList](/apis/webrtc/MediaStreamTrackList) page displays each of these methods, properties, and events in tables generated for each member where the member has specified the MediaStreamTrackList object in the **Applies to** field in the **Basic property configuration** form. All you have to do to generate the tables is to specify the parent API object for the member in that form.

When you are stubbing out the pages, if you do nothing else in the member pages, you must specify the parent API object in the **Applies to** field.

Oh, that and mark them as stubs, of course!

## Filling in the pages

Once you've got the pages all in place, you can go back and start filling them in. Most of the time, how to do this is obvious. But where it may be unclear, this section attempts to clarify.

Always refer to the most current specification for the API as you develop the content. The specifications are usually found on [w3.org](http://www.w3.org) or [whatwg.org](http://www.whatwg.org/).

### Flags

All pages in the apis tree need to be identified as "API" topics, along with their individual API name topic (see[Topics](#Topics), below. When you finish creating an API page, also mark the "Needs Review" flag.

### Object listing page content

The listing page describes the API and its objects.

#### Summary and object table

After the Top-Level Summary section, in which you briefly describe the API, edit the Basic Listing Configuration to display a summary table of the API objects included in the listing.

In the Query field, include a query that selects for the topic and the API\_Objects categories. For example, the WebRTC listing page query looks like this:

<dl>
<dd>
[[Category:WebRTC]][[Category:API\_Objects]]

</dd>
</dl>
Note, you may have to create the topic category for your API listing. How to do this is described in [WPD:Topics](/WPD:Topics).

Also, **do not check** the **Use page title** or **Print all subpages** boxes.

#### Topics

The API is an API so check that one. You'll also need a category for your API's content. For example, if you're documenting the WebRTC API, you'll need to categorize this page as a "WebRTC" page - by checking the box if it exists or by creating a new topic category, then checking the box. See [WPD:Topics](/WPD:Topics) for more about creating new topics.

#### Topic clusters

The only articles that should appear in the summary table (described previously) are API\_Object pages. If you want to generate a list of related topics (or articles), the place to do that is in the **See also** section, in the **Topic clusters**. You'll want to check the boxes appropriate to your API, and, in related articles that belong in the same topic cluster, be sure the appropriate boxes are checked there. See [Topics and topic clusters](/WPD:Editors_Guide/step_6_author_or_upload_new_content#Topics_and_topic_clusters)

#### Main Content section

The API listing page provides a broad description of the API. If there are further sub divisions of the API, include them as sub headings. This preserves the API's design - as it is described on w3.org - and allows the content to respond to search effectively. The main content field for the WebRTC API page (apis/webrtc) would look like the following:

    <title>WebRTC API</title>
    ...
    Describe the WebRTC API.
    ## MediaStream API
    Describe the MediaStream API. Provide links to the appropriate API objects, in this example: LocalMediaStream,
    MediaStream, MediaStreamTrack, and MediaStreamTrackList.
    ## PeerConnection API
    Describe the PeerConnection API.
    ## DataChannel API
    etc.

This is just an outline. Here's the [actual content of the apis/webrtc page](/apis/webrtc).

The listing page's main content should provide both an elaborate description of the APIs and links to other conceptual or tutorial pages.

### Object page content

The object page is pretty straight-forward. Here you'll want to explain how to use the object and its relationship to the other objects in the API.

Object pages do not need to be included in **topic clusters** - leave that to the API\_Listing pages. But the object page must be included in at least one **topic** - that for the API name (common name) itself, for example, WebRTC is the topic for the WebRTC API.

### Examples

Object pages and object member pages (sub pages) should have examples. API\_Listing pages should not. Anything so elaborate as to involve all of the objects of a typical API should be described in a tutorial or conceptual article.

Oh, and don't forget to wrap your code samples in Markdown code fences `\`\`\``. You can also optionally declare if its *JavaScript* using `js`, HTML `html`, XML `xml` and other supported languages by [Highlight.js](https://highlightjs.org)

see [syntax highlighting](/WPD:Style_Manual#Code_syntax_highlighting).

### Object sub-page content

This covers issues common to all sub pages of the object page, events, methods, and properties pages.

#### Return value data type

In the **Basic property configuration** form, for the **Return value data type** field you specify the data type of the object by selecting it from the drop-down menu. However, if the type is not in the list, you must edit the **Property:Javascript\_data\_type** and add the data type to the list. When you add types to the list, be sure to maintain the alphabetical order.

**TODO**: The problems with this are, 1 - keeping the list in some order that makes sense (alphabetical), and 2 - dealing with a potentially endless list of types. We need to come up with a better way of specifying the type if it is not one of the primitive types. Perhaps an additional text input field under the drop-down where you can specify the type if you choose "Other" from the drop-down.

#### Exceptions, constants and enumerations need forms and templates

We need to be able to refer to constants and enumerations as content chunks (like methods and properties) so they may be reused across object methods and properties. For now, enumerations and constants are defined in the return values of properties and methods without the ability to reuse them.

**TODO**: Create Object\_Exceptions templates, forms, etc. - very large effort

**TODO**: Create Object\_Constants templates, forms, etc. - very large effort

### Object method page content

Again, pretty straight-forward.

**TODO**: The API\_\_Object\_Method template needs greater clarity in using the **Syntax** section.

**TODO**: The API\_Object\_Method template needs to handle **Exceptions**.

For now, treat exceptions within the summary section of the event that throws the exception. Use a link to any existing exception pages - i.e. DOM execeptions.

**TODO**: The API\_Object\_Method template needs to handle constants and enumerations

### Object property page content

Another straight-forward form.

Constants often define the possible values of an object property. See [this](/apis/webrtc/MediaStreamTrack/readyState) for an example of how they are treated.

Event handlers, as they are typically treated in a specification's IDL, are properties and should be treated as such in your documentation. Within the summary section for the property, be sure to link to the extant page for the corresponding event, i.e. DOM events.

**TODO**: The API\_\_Object\_Property template needs greater clarity in using the **Syntax** section.

### Object event page content

Again, straight-forward.

**TODO**: The Event template: it's not clear how the values in the **Overview Table** get populated. For APIs - as opposed to DOM events - we may need a different form/template.

### Referencing extra-API facilities

Sometimes an API includes methods that are called on objects not in the API. In our WebRTC example, this is the case with [getUserMedia()](/w/index.php?title=dom/methods/getUserMedia&action=edit&redlink=1) which is a method of the DOM Navigator object. In WebRTC, you call getUserMedia() to get a [LocalMediaStream](/apis/webrtc/LocalMediaStream) object for the user's audio and video data.

Strictly speaking, getUserMedia() does not belong to the WebRTC API, though it was developed to accommodate WebRTC. There is no semantic way to include getUserMedia() as a method of any object in the WebRTC API. The getUserMedia() method must be added to the wiki under [dom/methods](/w/index.php?title=dom/methods&action=edit&redlink=1) and as a member of [dom/Navigator](/dom/Navigator).

The best practice is to reference the extra-API facility (couldn't think of a better name) in the main content of the pertinent API listing and object pages. For the WebRTC API, the [LocalMediaStream](/apis/webrtc/LocalMediaStream) object page must have a reference to [getUserMedia()](/w/index.php?title=dom/methods/getUserMedia&action=edit&redlink=1). So should any tutorials about using the API, and these tutorials should be referenced in the API listing and object pages as well.

## Importing and updating content

Whenever you work on content in this wiki, you should be checking the documentation against the latest standards-track specifications, either provided by WATWG or the W3C. This is particularly important with the API documentation because most of the API specifications still have Working Draft status, and they are updated frequently. Usually the Editors' Draft version of a specification lists the latest changes, and earlier drafts of the specification are provided for reference. Discussion threads are also cited frequently, and may be a source of recent change information. Also, many of the authors review their work in blog posts or sites dedicated specifically to the feature being implemented.

### Converting HTML content

To convert HTML to MediaWiki markup for importing (pasting) into WPD pages, follow these steps.

1.  Take a copy of the HTML you want to convert - this is best done like so, from the different sources:

    -   MDN - sign in to MDN, press the edit button, press the Source button on the editing interface, and copy and paste the contents of the `<body></body>` tags into a blank text file. Pro tip from Janet: adding
        `?raw&macros` to an MDN URL gives you the article content without the skin, but after evaluating templates; view the source of this to get the raw HTML.

    -   Opera web standards curriculum - this material is already in Wiki markup, so you've got a much easier job here!

    -   foo

2.  Check that the HTML validates: Go to <http://html5.validator.nu/>, select "text field" from the drop down select list, paste your body content in between the `<body></body>` tags, and press "Validate". If it comes up with errors, keeping fixing and rechecking until no more errors come up.

3.  Go to [this tool](http://toolserver.org/~diberri/cgi-bin/html2wiki/) or [this tool](http://labs.seapine.com/htmltowiki.cgi). Use either tool to convert your HTML into wikimarkup, and grab a copy of the result. You can also use [Pandoc](http://johnmacfarlane.net/pandoc/README.html) for conversion from HTML and a wide variety of other formats.

4.  Try pasting it into your page's content field and pressing "Save". It'll probably look terrible at the moment. You'll need to:

    -   **Remove excess whitespace**. Because of the way Wiki markup works, you'll need to put only a single line between paragraphs, and remove whitespace from the beginning of lines.

    -   **Get tables to render**. Tables in MediaWiki rely on the pipe character to delineate the columns and rows. Because of a bug in the way pipe characters are handled in semantic media wiki forms, you need to write your table syntax using the pipe hack. See <http://webplatform.org/docs/WPD:Manual_Of_Style/Tables> for more details.

    -   **Replace vertical bars**. Media wiki's handling of the vertical bar character ( | ) is problematic. To be safe, use the "pipe hack" mentioned above to replace all vertical bars—not only in tables, but in code blocks and regular text throughout the article.

    -   **Tidy up code blocks**. Code samples should be wrapped in \<pre\>\</pre\> tags, and you should use two spaces for each level of indent. The opening and closing tags should go on the same lines as the first and last lines of code, respectively. For example:

            This
              is a
              code
            Sample

    -   **Images**: To add images back into your article when you are importing it, first of all save a copy of them all locally. A good way to do this if there are loads of images is to go to the page where your article originally came from, then select File \> Save as... \> HTML file with Images.This should save a copy of the page you are on, with all the images and other assets associated with a page saved along with it, in a folder.

        Next, for each image you need to create a special wiki markup tag that signifies you want to insert an image:

            [ [ Image:image-filename.jpg|alt text you want your image to have]]

        Once you save your page, this will appear as a red (i.e. "doesn't exist yet") link. Click on this link to go to an admin page where you can choose to upload the image you want to appear there.

        When you've done that, go back to the page and refresh - the image should appear in place of the red link. The wiki markup you entered above should be rendered in the final HTML:

            <img src="image-filename.jpg" alt="alt text you want your image to have">

        Media wiki may have also tagged some icky presentational HTML crap onto the end of this like, like `border="0"`, but hey, it works, and no kittens are going to die.

    -   **Executable code samples** (THERE DOESN'T SEEM TO BE ANY WAY YET TO INCLUDE EXECUTABLE CODE EXAMPLE ON THE SITE, BUT I ASSUME THIS IS BEING WORKED ON)

    -   **HTML lists**: Dealing with HTML lists is absolutely fine for simple lists where you've just a simple list of bullets (items created using asterisks — \*) or numbers (items created using hashes/pounds — \#), but for any kind of complex nested lists, I would advise you to just use HTML instead, otherwise you'll go through far too much pain trying to make the list render correctly and consistently. For some more complex list examples that I've already dealt with, see the [HTML lists](/guides/html_lists) guide.

## More

To update extant API\_Listing pages to use the new Template:Concept\_Listing go [here](/WPD:Creating_API_pages/updating_template_changes).
