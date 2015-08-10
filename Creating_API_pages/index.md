---
title: WPD:Creating API pages
path: Creating_API_pages

---
<h1><span class="mw-headline" id="Creating_API_documentation_guide">Creating API documentation guide</span></h1>
<p>This article explains how to add new API documentation pages to Web Platform Docs. It provides a process for adding several new pages -  as a branch - to the wiki. The discussion cites as an example the creation of  the <a href="/wiki/apis/webrtc" title="apis/webrtc">WebRTC API</a> pages.
</p><p>These instructions support the work outlined in the <a href="/wiki/WPD:Proposals/api_docs" title="WPD:Proposals/api docs" class="mw-redirect">API doc proposal</a>.
</p>
<h2><span class="mw-headline" id="Listing_page">Listing page</span></h2>
<p>The listing page is the top-level page that introduces the subject, in this example the WebRTC API. It uses the common API listing name to identify the subject.
</p><p>Most of the time, the API listing is not the proper name of an API or other element. Rather, it is a catch-all description for a group of APIs. In this example, WebRTC is a catch-all for the MediaStream, PeerConnection, and DataChannel APIs. In fact, these are catch-alls themselves. The MediaStream API is actually composed of the MediaStream, LocalMediaStream, MediaStreamTrack, and MediaStreamTrackList objects. These are the actual APIs, the named objects that have methods and properties and which the developer uses in her application.
</p><p>We use the API listings as reference pages for all of the associated API objects and their members. The listing page is the parent page of the API objects. It is a reference page that associates the common name of the API (WebRTC) with its actual components (MediaStream, LocalMediaStream, etc.).
</p><p>So, the listing page for the WebRTC API is <b>apis/webrtc</b>.
</p><p>Note that the API listings, not being proper names of API objects, do not have camel-casing in URLs. So, <b>apis/webrtc</b> not <b>apis/WebRTC</b>. But MediaStream is an API object, so <b>apis/webrtc/MediaStream</b>. See <a href="/wiki/WPD:Manual_Of_Style#URLs" title="WPD:Manual Of Style" class="mw-redirect">URLs</a> in the <a href="/wiki/WPD:Manual_Of_Style" title="WPD:Manual Of Style" class="mw-redirect">Manual of Style</a> for more about URLs.
</p><p>You really only need one listing page. It's enough to just have <b>apis/webrtc</b> - you don't need <b>apis/webrtc/peerconnection</b>, <b>apis/webrtc/datachannel</b>, nor <b>apis/webrtc/mediastream</b> (as a listing page, different from the <b>apis/webrtc/MediaStream</b> page which represents the actual API object - more on that below). All of these sub listing pages should just be represented as headings in the content of the main listing page, not as pages in their own right, as shown below. But don't leave these names out; they are valuable as keywords, and as long as they're included as sub headings, search engines can find them.
</p><p>If you have only one API object and there is no other catch-all description for the API, you still have to create the listing page. So if the API name is <b>MyAPI</b> the URLs for the listing page and the object page are, <b>apis/myapi</b> and <b>apis/myapi/MyAPI</b>, respectively.
</p><p>Doing this allows for changes in the specification as the API is being developed. Often an API in development goes through lots of changes. Decoupling the API listing and the API objects in this fashion allows the names to change to protect the innocent.
</p><p>The organization of the <b>apis</b> namespace, therefore, is as follows:
</p>
<dl><dd>apis</dd>
<dd>apis/&lt;apilist&gt;</dd>
<dd>apis/&lt;apilist&gt;/&lt;apiObject&gt;/&lt;event&gt;</dd>
<dd>apis/&lt;apilist&gt;/&lt;apiObject&gt;/&lt;method&gt;</dd>
<dd>apis/&lt;apilist&gt;/&lt;apiObject&gt;/&lt;property&gt;</dd></dl>
<p>See <a href="#Creating_the_API_Object_Method.2C_Property.2C_and_Event_pages">below</a> for an example.
</p>
<h3><span class="mw-headline" id="Creating_the_listing_page">Creating the listing page</span></h3>
<p>The <a href="/wiki/apis/webrtc" title="apis/webrtc">apis/webrtc</a> listing page was created as follows.
</p>
<ol><li> Navigate to <a href="/wiki/WPD:New_Page" title="WPD:New Page">WPD:New_Page</a>.</li>
<li> Under the <b>API Lising</b> page type, enter <b>apis/foo</b>.
<dl><dd> Where <b>foo</b> is the name of the listing page, all lower case (as in webrtc). See the <a href="/wiki/WPD:Manual_Of_Style" title="WPD:Manual Of Style" class="mw-redirect">Manual of Style</a> for more information about titles and headings.</dd></dl></li>
<li> Click the <b>Create API Listing Page</b> button.</li>
<li> Fill out the <b>Main content</b> with the sub headings and names of the API objects - you can come back and create the links to them later.</li></ol>
<p>&#160;
</p>
<h2><span class="mw-headline" id="Stubbing_out_the_pages">Stubbing out the pages</span></h2>
<p>The best way to work on all of this is to first draw out the architecture as a hierarchy of stub pages. This allows other writers to help out and it provides you with the ability to create the links you need between pages as you fill them in.
</p>
<h3><span class="mw-headline" id="Creating_the_API_Object_page">Creating the API Object page</span></h3>
<p>The first page to create, after the listing page, is that for the first API object; in this example, <a href="/wiki/apis/webrtc/MediaStream" title="apis/webrtc/MediaStream">apis/webrtc/MediaStream</a>.
</p>
<ol><li> Navigate to <a href="/wiki/WPD:New_Page" title="WPD:New Page">WPD:New_Page</a>.</li>
<li> Under the <b>API Object</b> page type, enter <b>apis/foo/barFly</b>.
<dl><dd> Where <b>foo</b> is the name of the API listing (webrtc), and <b>barFly</b> is the name of the API object in its native case (as in MediaStream). See the <a href="/wiki/WPD:Manual_Of_Style" title="WPD:Manual Of Style" class="mw-redirect">Manual of Style</a> for more information about titles and headings.</dd></dl></li>
<li> Click the <b>Create API Object Page</b> button.</li>
<li> Mark the page as a stub.</li></ol>
<p>&#160;
</p>
<h3><span class="mw-headline" id="Creating_the_API_Object_Method.2C_Property.2C_and_Event_pages">Creating the API Object Method, Property, and Event pages</span></h3>
<p>The API Object page lists all of the members (properties, methods, and events) for the object in tables that summarize these members. Each member's information is held in a separate page, the pertinent sections of which are drawn into the summary tables. You have to create a page for each member using <a href="/wiki/WPD:New_Page" title="WPD:New Page">WPD:New_Page</a>.
</p><p>The WPD:New_Page page describes how to create the URL for each page. For example, the <a href="/wiki/apis/webrtc/MediaStreamTrackList" title="apis/webrtc/MediaStreamTrackList">MediaStreamTrackList</a> object has the following members, shown with their full paths:
</p>
<ul><li> Methods
<ul><li> <a href="/wiki/apis/webrtc/MediaStreamTrackList/add" title="apis/webrtc/MediaStreamTrackList/add">apis/webrtc/MediaStreamTrackList/add</a></li>
<li> <a href="/wiki/apis/webrtc/MediaStreamTrackList/item" title="apis/webrtc/MediaStreamTrackList/item">apis/webrtc/MediaStreamTrackList/item</a></li>
<li> <a href="/wiki/apis/webrtc/MediaStreamTrackList/remove" title="apis/webrtc/MediaStreamTrackList/remove">apis/webrtc/MediaStreamTrackList/remove</a></li></ul></li>
<li> Properties
<ul><li> <a href="/wiki/apis/webrtc/MediaStreamTrackList/length" title="apis/webrtc/MediaStreamTrackList/length">apis/webrtc/MediaStreamTrackList/length</a></li>
<li> <a href="/wiki/apis/webrtc/MediaStreamTrackList/onaddtrack" title="apis/webrtc/MediaStreamTrackList/onaddtrack">apis/webrtc/MediaStreamTrackList/onaddtrack</a></li>
<li> <a href="/wiki/apis/webrtc/MediaStreamTrackList/onremovetrack" title="apis/webrtc/MediaStreamTrackList/onremovetrack">apis/webrtc/MediaStreamTrackList/onremovetrack</a></li></ul></li>
<li> Events
<ul><li> <a href="/wiki/apis/webrtc/MediaStreamTrackList/addtrack" title="apis/webrtc/MediaStreamTrackList/addtrack">apis/webrtc/MediaStreamTrackList/addtrack</a></li>
<li> <a href="/wiki/apis/webrtc/MediaStreamTrackList/removetrack" title="apis/webrtc/MediaStreamTrackList/removetrack">apis/webrtc/MediaStreamTrackList/removetrack</a></li></ul></li></ul>
<p>When you create the page, you specify the full path - per the above - in the New_Page page.
</p><p><b>Note:</b> While we are reasonably confident that there will be no collisions, for example a property and an event of the same name, we are resolved to deal with these by inserting identifying labels, for example:
</p>
<ul><li> apis/myapi/myAPI/void-property</li>
<li> apis/myapi/myAPI/void-method</li></ul>
<p>Such identifiers, however, are the exception, not the rule.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>: The form input fields in the New_Page page need to be wider to display longer paths.
</p>
</div>
<p>The <a href="/wiki/apis/webrtc/MediaStreamTrackList" title="apis/webrtc/MediaStreamTrackList">apis/webrtc/MediaStreamTrackList</a> page displays each of these methods, properties, and events in tables generated for each member where the member has specified the MediaStreamTrackList object in the <b>Applies to</b> field in the <b>Basic property configuration</b> form. All you have to do to generate the tables is to specify the parent API object for the member in that form.
</p><p>When you are stubbing out the pages, if you do nothing else in the member pages, you must specify the parent API object in the <b>Applies to</b> field.
</p><p>Oh, that and mark them as stubs, of course!
</p>
<h2><span class="mw-headline" id="Filling_in_the_pages">Filling in the pages</span></h2>
<p>Once you've got the pages all in place, you can go back and start filling them in. Most of the time, how to do this is obvious. But where it may be unclear, this section attempts to clarify.
</p><p>Always refer to the most current specification for the API as you develop the content. The specifications are usually found on <a rel="nofollow" class="external text" href="http://www.w3.org">w3.org</a> or <a rel="nofollow" class="external text" href="http://www.whatwg.org/">whatwg.org</a>.
</p>
<h3><span class="mw-headline" id="Flags">Flags</span></h3>
<p>All pages in the apis tree need to be identified as "API" topics, along with their individual API name topic (see<a href="#Topics">Topics</a>, below. When you finish creating an API page, also mark the "Needs Review" flag.
</p>
<h3><span class="mw-headline" id="Object_listing_page_content">Object listing page content</span></h3>
<p>The listing page describes the API and its objects.
</p>
<h4><span class="mw-headline" id="Summary_and_object_table">Summary and object table</span></h4>
<p>After the Top-Level Summary section, in which you briefly describe the API, edit the Basic Listing Configuration to display a summary table of the API objects included in the listing.
</p><p>In the Query field, include a query that selects for the topic and the API_Objects categories. For example, the WebRTC listing page query looks like this:
</p>
<dl><dd> [[Category:WebRTC]][[Category:API_Objects]]</dd></dl>
<p>Note, you may have to create the topic category for your API listing. How to do this is described in <a href="/wiki/WPD:Topics" title="WPD:Topics" class="mw-redirect">WPD:Topics</a>.
</p><p>Also, <b>do not check</b> the <b>Use page title</b> or <b>Print all subpages</b> boxes.
</p>
<h4><span class="mw-headline" id="Topics">Topics</span></h4>
<p>The API is an API so check that one. You'll also need a category for your API's content. For example, if you're documenting the WebRTC API, you'll need to categorize this page as a "WebRTC" page - by checking the box if it exists or by creating a new topic category, then checking the box. See <a href="/wiki/WPD:Topics" title="WPD:Topics" class="mw-redirect">WPD:Topics</a> for more about creating new topics.
</p>
<h4><span class="mw-headline" id="Topic_clusters">Topic clusters</span></h4>
<p>The only articles that should appear in the summary table (described previously) are API_Object pages. If you want to generate a list of related topics (or articles), the place to do that is in the <b>See also</b> section, in the <b>Topic clusters</b>. You'll want to check the boxes appropriate to your API, and, in related articles that belong in the same topic cluster, be sure the appropriate boxes are checked there. See <a href="/wiki/WPD:Editors_Guide/step_6_author_or_upload_new_content#Topics_and_topic_clusters" title="WPD:Editors Guide/step 6 author or upload new content">Topics and topic clusters</a>
</p>
<h4><span class="mw-headline" id="Main_Content_section">Main Content section</span></h4>
<p>The API listing page provides a broad description of the API. If there are further sub divisions of the API, include them as sub headings. This preserves the API's design - as it is described on w3.org - and allows the content to respond to search effectively. The main content field for the WebRTC API page (apis/webrtc) would look like the following:
</p>
<pre>
&lt;title&gt;WebRTC API&lt;/title&gt;
...
Describe the WebRTC API.
==MediaStream API==
Describe the MediaStream API. Provide links to the appropriate API objects, in this example: LocalMediaStream, 
MediaStream, MediaStreamTrack, and MediaStreamTrackList.
==PeerConnection API==
 Describe the PeerConnection API.
==DataChannel API==
    etc.
</pre>
<p>This is just an outline. Here's the <a href="/wiki/apis/webrtc" title="apis/webrtc">actual content of the apis/webrtc page</a>.
</p><p>The listing page's main content should provide both an elaborate description of the APIs and links to other conceptual or tutorial pages.
</p>
<h3><span class="mw-headline" id="Object_page_content">Object page content</span></h3>
<p>The object page is pretty straight-forward. Here you'll want to explain how to use the object and its relationship to the other objects in the API.
</p><p>Object pages do not need to be included in <b>topic clusters</b> - leave that to the API_Listing pages. But the object page must be included in at least one <b>topic</b> - that for the API name (common name) itself, for example, WebRTC is the topic for the WebRTC API.
</p>
<h3><span class="mw-headline" id="Examples">Examples</span></h3>
<p>Object pages and object member pages (sub pages) should have examples. API_Listing pages should not. Anything so elaborate as to involve all of the objects of a typical API should be described in a tutorial or conceptual article.
</p><p>Oh, and don't forget to wrap your HTML code examples in &lt;nowiki&gt; or &lt;syntaxhighlight&gt; tags (see <a href="/wiki/WPD:Style_Manual#Code_syntax_highlighting" title="WPD:Style Manual" class="mw-redirect">syntax highlighting</a>. Just look how ridiculous our <a href="/w/index.php?title=dom/apis/document/getElementById&amp;action=edit&amp;redlink=1" class="new" title="dom/apis/document/getElementById (page does not exist)">getElementById</a> doc looks with the &lt;syntaxhighlight&gt; tags removed. Try it.
</p>
<h3><span class="mw-headline" id="Object_sub-page_content">Object sub-page content</span></h3>
<p>This covers issues common to all sub pages of the object page, events, methods, and properties pages.
</p>
<h4><span class="mw-headline" id="Return_value_data_type">Return value data type</span></h4>
<p>In the <b>Basic property configuration</b> form, for the <b>Return value data type</b> field you specify the data type of the object by selecting it from the drop-down menu. However, if the type is not in the list, you must edit the <b>Property:Javascript_data_type</b> and add the data type to the list. When you add types to the list, be sure to maintain the alphabetical order.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>: The problems with this are, 1 - keeping the list in some order that makes sense (alphabetical), and 2 - dealing with a potentially endless list of types. We need to come up with a better way of specifying the type if it is not one of the primitive types. Perhaps an additional text input field under the drop-down where you can specify the type if you choose "Other" from the drop-down.
</p>
</div>
<h4><span class="mw-headline" id="Exceptions.2C_constants_and_enumerations_need_forms_and_templates">Exceptions, constants and enumerations need forms and templates</span></h4>
<p>We need to be able to refer to constants and enumerations as content chunks (like methods and properties) so they may be reused across object methods and properties. For now, enumerations and constants are defined in the return values of properties and methods without the ability to reuse them.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>: Create Object_Exceptions templates, forms, etc. - very large effort
</p>
</div>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>: Create Object_Constants templates, forms, etc. - very large effort
</p>
</div>
<h3><span class="mw-headline" id="Object_method_page_content">Object method page content</span></h3>
<p>Again, pretty straight-forward.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>: The API__Object_Method template needs greater clarity in using the <b>Syntax</b> section.
</p>
</div>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>: The API_Object_Method template needs to handle <b>Exceptions</b>.
</p>
</div>
<p>For now, treat exceptions within the summary section of the event that throws the exception. Use a link to any existing exception pages - i.e. DOM execeptions.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>: The API_Object_Method template needs to handle constants and enumerations
</p>
</div>
<h3><span class="mw-headline" id="Object_property_page_content">Object property page content</span></h3>
<p>Another straight-forward form.
</p><p>Constants often define the possible values of an object property. See <a href="/wiki/apis/webrtc/MediaStreamTrack/readyState" title="apis/webrtc/MediaStreamTrack/readyState">this</a> for an example of how they are treated. 
</p><p>Event handlers, as they are typically treated in a specification's IDL, are properties and should be treated as such in your documentation. Within the summary section for the property, be sure to link to the extant page for the corresponding event, i.e. DOM events.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>: The API__Object_Property template needs greater clarity in using the <b>Syntax</b> section.
</p>
</div>
<h3><span class="mw-headline" id="Object_event_page_content">Object event page content</span></h3>
<p>Again, straight-forward.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>: The Event template: it's not clear how the values in the <b>Overview Table</b> get populated. For APIs - as opposed to DOM events - we may need a different form/template.
</p>
</div>
<h3><span class="mw-headline" id="Referencing_extra-API_facilities">Referencing extra-API facilities</span></h3>
<p>Sometimes an API includes methods that are called on objects not in the API. In our WebRTC example, this is the case with <a href="/w/index.php?title=dom/methods/getUserMedia&amp;action=edit&amp;redlink=1" class="new" title="dom/methods/getUserMedia (page does not exist)">getUserMedia()</a> which is a method of the DOM Navigator object. In WebRTC, you call getUserMedia() to get a <a href="/wiki/apis/webrtc/LocalMediaStream" title="apis/webrtc/LocalMediaStream">LocalMediaStream</a> object for the user's audio and video data.
</p><p>Strictly speaking, getUserMedia() does not belong to the WebRTC API, though it was developed to accommodate WebRTC. There is no semantic way to include getUserMedia() as a method of any object in the WebRTC API. The getUserMedia() method must be added to the wiki under <a href="/w/index.php?title=dom/methods&amp;action=edit&amp;redlink=1" class="new" title="dom/methods (page does not exist)">dom/methods</a> and as a member of <a href="/wiki/dom/Navigator" title="dom/Navigator">dom/Navigator</a>.
</p><p>The best practice is to reference the extra-API facility (couldn't think of a better name) in the main content of the pertinent API listing and object pages. For the WebRTC API, the <a href="/wiki/apis/webrtc/LocalMediaStream" title="apis/webrtc/LocalMediaStream">LocalMediaStream</a> object page must have a reference to <a href="/w/index.php?title=dom/methods/getUserMedia&amp;action=edit&amp;redlink=1" class="new" title="dom/methods/getUserMedia (page does not exist)">getUserMedia()</a>. So should any tutorials about using the API, and these tutorials should be referenced in the API listing and object pages as well.
</p>
<h2><span class="mw-headline" id="Importing_and_updating_content">Importing and updating content</span></h2>
<p>Whenever you work on content in this wiki, you should be checking the documentation against the latest standards-track specifications, either provided by WATWG or the W3C. This is particularly important with the API documentation because most of the API specifications still have Working Draft status, and they are updated frequently. Usually the Editors' Draft version of a specification lists the latest changes, and earlier drafts of the specification are provided for reference. Discussion threads are also cited frequently, and may be a source of recent change information. Also, many of the authors review their work in blog posts or sites dedicated specifically to the feature being implemented.
</p>
<h3><span class="mw-headline" id="Converting_HTML_content">Converting HTML content</span></h3>
<p>To convert HTML to MediaWiki markup for importing (pasting) into WPD pages, follow these steps.
</p>
<ol>
  <li><p>Take a copy of the HTML you want to convert - this is best done like so, from the different sources:</p>
    <ul>
      <li><p>MDN - sign in to MDN, press the edit button, press the Source button on the editing interface, and copy and paste the contents of the <code>&lt;body&gt;&lt;/body&gt;</code> tags into a blank text file. Pro tip from Janet: adding <br /><code>?raw&amp;macros</code> to an MDN URL gives you the article content without the skin, but after evaluating templates; view the source of this to get the raw HTML.</p></li>
      <li><p>Opera web standards curriculum - this material is already in Wiki markup, so you've got a much easier job here!</p></li>
      <li><p>foo</p></li>
    </ul>
  </li>
  <li><p>Check that the HTML validates: Go to <a rel="nofollow" class="external free" href="http://html5.validator.nu/">http://html5.validator.nu/</a>, select "text field" from the drop down select list, paste your body content in between the <code>&lt;body&gt;&lt;/body&gt;</code> tags, and press "Validate". If it comes up with errors, keeping fixing and rechecking until no more errors come up.</p></li>
  <li><p>Go to <a rel="nofollow" class="external text" href="http://toolserver.org/~diberri/cgi-bin/html2wiki/">this tool</a> or <a rel="nofollow" class="external text" href="http://labs.seapine.com/htmltowiki.cgi">this tool</a>. Use either tool to convert your HTML into wikimarkup, and grab a copy of the result. You can also use <a rel="nofollow" class="external text" href="http://johnmacfarlane.net/pandoc/README.html">Pandoc</a> for conversion from HTML and a wide variety of other formats.</p></li>
  <li><p>Try pasting it into your page's content field and pressing "Save". It'll probably look terrible at the moment. You'll need to:</p>
    <ul>
      <li><p><b>Remove excess whitespace</b>. Because of the way Wiki markup works, you'll need to put only a single line between paragraphs, and remove whitespace from the beginning of lines.</p></li>
      <li><p><b>Get tables to render</b>. Tables in MediaWiki rely on the pipe character to delineate the columns and rows. Because of a bug in the way pipe characters are handled in semantic media wiki forms, you need to write your table syntax using the pipe hack. See <a rel="nofollow" class="external free" href="http://webplatform.org/docs/WPD:Manual_Of_Style/Tables">http://webplatform.org/docs/WPD:Manual_Of_Style/Tables</a> for more details.</p></li>
      <li><p><b>Replace vertical bars</b>. Media wiki's handling of the vertical bar character ( | ) is problematic. To be safe, use the "pipe hack" mentioned above to replace all vertical bars&#8212;not only in tables, but in code blocks and regular text throughout the article.</p></li>
      <li><p><b>Tidy up code blocks</b>. Code samples should be wrapped in &lt;pre&gt;&lt;/pre&gt; tags, and you should use two spaces for each level of indent. The opening and closing tags should go on the same lines as the first and last lines of code, respectively. For example:</p>
<pre>This
  is a
  code
Sample</pre>
      </li>
      <li><p><b>Images</b>: To add images back into your article when you are importing it, first of all save a copy of them all locally. A good way to do this if there are loads of images is to go to the page where your article originally came from, then select File &gt; Save as... &gt; HTML file with Images.This should save a copy of the page you are on, with all the images and other assets associated with a page saved along with it, in a folder.</p>
      <p>Next, for each image you need to create a special wiki markup tag that signifies you want to insert an image:</p>
<pre>&#91; &#91; Image:image-filename.jpg|alt text you want your image to have&#93;&#93;</pre>
<p>Once you save your page, this will appear as a red (i.e. "doesn't exist yet") link. Click on this link to go to an admin page where you can choose to upload the image you want to appear there. </p>
<p>When you've done that, go back to the page and refresh - the image should appear in place of the red link. The wiki markup you entered above should be rendered in the final HTML:</p>
<pre>&lt;img src=&quot;image-filename.jpg&quot; alt=&quot;alt text you want your image to have&quot;&gt;</pre>
<p>Media wiki may have also tagged some icky presentational HTML crap onto the end of this like, like <code>border="0"</code>, but hey, it works, and no kittens are going to die.</p>
      </li>
      <li><p><b>Executable code samples</b> (THERE DOESN'T SEEM TO BE ANY WAY YET TO INCLUDE EXECUTABLE CODE EXAMPLE ON THE SITE, BUT I ASSUME THIS IS BEING WORKED ON)</p></li>
      <li><p><b>HTML lists</b>: Dealing with HTML lists is absolutely fine for simple lists where you've just a simple list of bullets (items created using asterisks — &#42;) or numbers (items created using hashes/pounds — &#35;), but for any kind of complex nested lists, I would advise you to just use HTML instead, otherwise you'll go through far too much pain trying to make the list render correctly and consistently. For some more complex list examples that I've already dealt with, see the <a href="/wiki/guides/html_lists" title="guides/html lists">HTML lists</a> guide.</p>
    </ul>
  </li>
</ol>
<h2><span class="mw-headline" id="More">More</span></h2>
<p>To update extant API_Listing pages to use the new Template:Concept_Listing go <a href="/wiki/WPD:Creating_API_pages/updating_template_changes" title="WPD:Creating API pages/updating template changes">here</a>.
</p>
<!-- 
NewPP limit report
CPU time usage: 0.102 seconds
Real time usage: 0.121 seconds
Preprocessor visited node count: 245/1000000
Preprocessor generated node count: 478/1000000
Post‐expand include size: 2429/2097152 bytes
Template argument size: 1087/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%   11.120      1 - -total
 62.16%    6.912      9 - Template:TODO
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:6298-0!*!0!!*!*!*!esi=1 and timestamp 20150809225543 and revision id 71239
 -->
