---
title: WPD:Content/Import Guide/H5R
---
<p>These instructions are specific to importing content from <a rel="nofollow" class="external text" href="http://www.html5rocks.com/">HTML5Rocks!</a>
</p>
<h2><span class="mw-headline" id="Initial_conversion">Initial conversion</span></h2>
<p>Here's what you do to get the content into wiki format.
</p>
<ol><li>From the <a rel="nofollow" class="external text" href="https://docs.google.com/a/google.com/spreadsheet/ccc?key=0AkRs-89PKiZpdHBqN2poNnJjV1c0N1FCYlN3ZUtpZ3c&amp;pli=1#gid=0">Content Batches spreadsheet</a>, copy the WPD URL for the article you intend to create.</li>
<li>In a new window, open the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/WPD:New_Page">WPD:New_Page</a> page.</li>
<li>Scroll down to the page type for the article (e.g., Tutorial).</li>
<li>In the text field, paste the WPD URL, and click Create Tutorial Page.</li>
<li>From the Content Batches spreadsheet, open the original HTML5Rocks! article using the Existing URL.</li>
<li>Open the <a rel="nofollow" class="external text" href="http://toolserver.org/~diberri/cgi-bin/html2wiki/index.cgi">html-to-wiki converter</a> page.</li>
<li> Open the original HTML5Rocks! article by adding the <code>?ModPagespeed=off</code> parameter to the URL.</li>
<li>Next, do one of the following:
<ul><li>In the original article, View Source, select all content, and copy; in the converter, choose the "Raw HTML" radio button, and paste the source into the HTML Source box.</li>
<li>In the original article, copy the full HTML5Rocks! URL (with the <code>?ModPagespeed=off</code>); in the converter, choose the "Fetch from URL" radio button, and paste the original URL into the text field.</li></ul></li>
<li>Under Options, choose "MediaWiki" from the dropdown as the output type. </li>
<li>Check "Escape HTML entities".</li>
<li>Click "Convert HTML to wiki markup". The converted markup appears in the MediaWiki markup box at the top of the page.</li>
<li>In the MediaWiki markup box, select all text, and copy.</li>
<li>In the new WPD page, past the new wiki code into the Content field, and click Save page.</li></ol>
<p>That gets the main content into a new page.
</p><p><i>Note:</i> If the above converter won't load (we've been getting a 503 Bad Gateway error lately), try <a rel="nofollow" class="external text" href="http://labs.seapine.com/htmltowiki.cgi">this one</a>. It's copy-and-paste only, but if it works, it works.
</p>
<h2><span class="mw-headline" id="Clean_up">Clean up</span></h2>
<p>There will be a lot of cruft - stuff that you'll delete or otherwise fix.
</p>
<ol><li>In the new WPD page, click the EDIT button.</li>
<li>In the Content field, remove everything up to the title - usually an H1 marked with a single '='. You'll remove it later as well, but save it for now.</li>
<li>Remove everything between the title and the "by" line; again, you'll remove it later, but you need the data for the moment. Same for "publish date".</li>
<li>Keep the Supported Browsers information (again, temporarily) but remove everything between the last browser "supported" or "unsupported" (i.e., "Your browser may ..." and so on) and the first subheading of the article (probably marked with ==s), including Table of Contents information.</li>
<li>Scroll down to the last line of article content, and remove everything after it, including the page content license blather, the page comments, JavaScript references, etc.</li>
<li>Remove any double line breaks except those meant to start a new paragraph.</li>
<li>Save the article and have a look.</li></ol>
<p><br />
</p>
<h2><span class="mw-headline" id=".3Ch2.3Es_with_IDs">&lt;h2&gt;s with IDs</span></h2>
<p>The converter should change HTML &lt;h2&gt; headings to double-equals wiki headings. However, many of our articles "deep link" to specific heading points in other articles. Those targets have IDs, and the IDs must be preserved for the links to continue to work. So after conversion, review the original article's source code for h2s with IDs. If you find any, change the converted double-equals headings <i>back</i> to standard HTML syntax and include the original ID. Thus: 
</p>
<pre>
==Introduction==
</pre>
<p>becomes
</p>
<pre>
&lt;h2 id=&quot;toc-intro&quot;&gt;Introduction&lt;/h2&gt;
</pre>
<p>as it appeared in the original article.
</p>
<h2><span class="mw-headline" id="Fix_broken_links">Fix broken links</span></h2>
<p>Check the content for links. They should be of the form: 
</p>
<pre>[http://www.google.com Google]</pre>
<p>Make sure that all URLs are fully qualified. External URLs will already be fully qualified, but links back to existing HTML5Rocks! articles will probably not be, and they won't work from the new WPD domain. That is:
</p>
<pre>
Original link:
[/tutorials/casestudies/onslaught/ Onslaught]

Corrected link:
[http://www.html5rocks.com/tutorials/casestudies/onslaught/ Onslaught]
</pre>
<h2><span class="mw-headline" id="iframe_content">iframe content</span></h2>
<p>Some of the articles we're migrating may have content that appears in an iframe. WikiMedia does not support iframes, so the best we can do is create a link to the content. In HTML5Rocks! usually the iframe has both code and layout from the playground. If the iframe contains a code sample, cut and paste the code sample into the article and put it in a <code>&lt;pre&gt;...&lt;/pre&gt;</code> block. If the iframe contains a sample page (that runs some wiz-bang doohicky), create a link to the page and tell the user what's happening, something like this:
</p>
<pre>
You can see a live demo of this game  [http://www.html5rocks.com/tutorials/casestudies/onslaught/ here].
</pre> 
<p>See the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/tutorials/audio_tag">audio tag</a> WPD article for examples of this workaround. 
</p>
<h2><span class="mw-headline" id="Images">Images</span></h2>
<p>Images: To get any images from the original article into your new version, you must save the images locally, fix the image references in your new code, and then upload them to your more-or-less finished product. 
</p><p>One good way to do this, especially if there are loads of images, is to go to the original article page and select <code>File &gt; Save as... &gt; Web page, complete</code> (or your browser's equivalent). This will save a copy of the page you are on, with all the images and other assets associated with a page saved along with it, in a subfolder, in one go.
</p><p>If there are only a few images, you can right-click on each one and save them locally with a name of your choosing. Either way, you have to get the article's images onto your local drive.
</p><p>Next, for each image, you need to create (or correct) the wiki markup tag that signifies you want to insert an image, in this format:
</p>
<pre>
[[Image:filename.jpg|alt text]]
</pre>
<p>Use the file name and extension for the image as saved to your local drive. When you next save the page, the image code will appear as a red (i.e., broken) link. Click on this link to go to an admin page where you can choose to upload the image you want to appear there. Select the image and let the page load a preview; this will also check that the image type matches the file extension, which is handy. Then click Upload, which actually uploads the file.
</p><p>After the file is uploaded, click the link at the bottom of the upload page to return to your original article. The image should appear in place of the red link. Repeat for each image.
</p>
<h2><span class="mw-headline" id="Filling_in_the_boxes">Filling in the boxes</span></h2>
<p>The next piece of work is to fill in the meta data and other form content for the article.
</p><p><b>Note:</b> The wiki layout puts the checkbox to the left of the label.
</p>
<ol><li>Edit the article.</li>
<li>At the top, always check High-level issues: Needs flags.</li>
<li>Check other flags that apply.</li>
<li>Fill in a short Summary. Be mindful of SEO.</li>
<li>At the bottom, in the Topics section, check all that apply.</li>
<li>Under External Attribution, check whichever applies (HTML5Rocks! in this case), and provide the original link in the text box. <b>Important:</b> If the H5R URL contains "en/" in the path, remove it. That is, if the original article URL is <code><a rel="nofollow" class="external free" href="http://www.html5rocks.com/en/tutorials/eventsource/basics/">http://www.html5rocks.com/en/tutorials/eventsource/basics/</a></code>, change it to <code><a rel="nofollow" class="external free" href="http://www.html5rocks.com/tutorials/eventsource/basics/">http://www.html5rocks.com/tutorials/eventsource/basics/</a></code>.</li></ol>
<h2><span class="mw-headline" id="Author_and_publish_date">Author and publish date</span></h2>
<p>Enter the original author's name, their profile link, and the publish (and update) date(s) in the form fields. Delete the original info from the content box.
</p>
<h2><span class="mw-headline" id="Compatibility_table">Compatibility table</span></h2>
<p>In the Content field, move all the Supported Browser content down to the end of the content to make it easier to reference when you are filling out the compatibility table. Do not make manual tables; use the compatibility table buttons in the form. You can use the original author's info as reference, but it may be out of date. Always get the latest information from <a rel="nofollow" class="external text" href="http://caniuse.com/">caniuse.com</a>.
</p><p>When you have the compatibility tables filled out, delete the original supported browsers info from the content box.
</p>
<h2><span class="mw-headline" id="Housekeeping">Housekeeping</span></h2>
<p>When you've finished an article, fill in the Status column of the spreadsheet: provide a status and your initials (i.e. Done - sr). Other people may be converting some articles in the same list, so always check the status column before you begin.
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:1765-0!*!*!!*!*!*!esi=1 and timestamp 20150731182655 and revision id 7039
 -->
