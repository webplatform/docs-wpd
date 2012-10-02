These instructions are specific to importing content from HTML5Rocks!

==Initial conversion==
Here's what you do to get the content into wiki format.

#From the [https://docs.google.com/a/google.com/spreadsheet/ccc?key=0AkRs-89PKiZpdHBqN2poNnJjV1c0N1FCYlN3ZUtpZ3c&pli=1#gid=0 Content Batches spreadsheet], copy the WPD URL for the article you intend to create.
#In a new window, open the [http://docs.webplatform.org/wiki/WPD:New_Page WPD:New_Page] page.
#Scroll down to the page type for the article (e.g., Tutorial).
#In the text field, paste the WPD URL, and click Create Tutorial Page.
#From the Content Batches spreadsheet, open the original HTML5Rocks! article using the Existing URL.
#Open the [http://toolserver.org/~diberri/cgi-bin/html2wiki/index.cgi html-to-wiki converter] page.
# Open the original HTML5Rocks! article by adding the <code>?ModPagespeed=off</code> parameter to the URL.
#Next, do one of the following:
#*In the original article, View Source, select all content, and copy; in the converter, choose the "Raw HTML" radio button, and paste the source into the HTML Source box.
#*In the original article, copy the full HTML5Rocks! URL (with the <code>?ModPagespeed=off</code>); in the converter, choose the "Fetch from URL" radio button, and paste the original URL into the text field.
#Under Options, choose "MediaWiki" from the dropdown as the output type. 
#Check "Escape HTML entities".
#Click "Convert HTML to wiki markup". The converted markup appears in the MediaWiki markup box at the top of the page.
#In the MediaWiki markup box, select all text, and copy.
#In the new WPD page, past the new wiki code into the Content field, and click Save page.

That gets the main content into a new page.

==Clean up==
There will be a lot of cruft - stuff that you'll delete or otherwise fix.

#In the new WPD page, click the EDIT button.
#In the Content field, remove everything up to the title - usually an H1 marked with a single '='. You'll remove it later as well, but save it for now.
#Remove everything between the title and the "by" line; again, you'll remove it later, but you need the data for the moment. Same for "publish date".
#Keep the Supported Browsers information (again, temporarily) but remove everything between the last browser "supported" or "unsupported" (i.e., "Your browser may ..." and so on) and the first subheading of the article (probably marked with ==s), including Table of Contents information.
#Scroll down to the last line of article content, and remove everything after it, including the page content license blather, the page comments, JavaScript references, etc.
#Remove any double line breaks except those meant to start a new paragraph.
#Save the article and have a look.


==&lt;h2&gt;s with IDs==
The converter should change HTML &lt;h2&gt; headings to double-equals wiki headings. However, many of our articles "deep link" to specific heading points in other articles. Those targets have IDs, and the IDs must be preserved for the links to continue to work. So after conversion, review the original article's source code for h2s with IDs. If you find any, change the converted double-equals headings ''back'' to standard HTML syntax and include the original ID, thus: 

<pre>
==Introduction==
</pre>
becomes
<pre>
&lt;h2 id="toc-intro"&gt;Introduction&lt;/h2&gt;
</pre>
as it appeared in the original article.

==Fix broken links==
Check the content for links. They should be of the form: 
<pre>[http://www.google.com Google]</pre>

Make sure that all URLs are fully qualified. External URLs will already be fully qualified, but links back to existing HTML5Rocks! articles will probably not be, and they won't work from the new WPD domain. That is:

<pre>
Original link:
[/tutorials/casestudies/onslaught/ Onslaught]

Corrected link:
[http://www.html5rocks.com/tutorials/casestudies/onslaught/ Onslaught]
</pre>

==iframe content==
Some of the articles we're migrating may have content that appears in an iframe. WikiMedia does not support iframes, so the best we can do is create a link to the content. In HTML5Rocks! usually the iframe has both code and layout from the playground. If the iframe contains a code sample, cut and paste the code sample into the article and put it in a <code>&lt;pre&gt;...&lt;/pre&gt;</code> block. If the iframe contains a sample page (that runs some wiz-bang doohicky), create a link to the page and tell the user what's happening, something like this:

<pre>
You can see a live demo of this game  [http://www.html5rocks.com/tutorials/casestudies/onslaught/ here].
</pre> 

See the [http://docs.webplatform.org/wiki/tutorials/audio_tag audio tag] WPD article for examples of this workaround. 

==Images==
Images: To get any images from the original article into your new version, you must save the images locally, fix the image references in your new code, and then upload them to your more-or-less finished product. 

One good way to do this, especially if there are loads of images, is to go to the original article page and select <code>File &gt; Save as... &gt; Web page, complete</code> (or your browser's equivalent). This will save a copy of the page you are on, with all the images and other assets associated with a page saved along with it, in a subfolder.

If there are only a few images, you can right-click on each one and save them locally with a name of your choosing. In either case, you have to get the article's images onto your local drive.

Next, for each image you need to create a special wiki markup tag that signifies you want to insert an image:

[ [ Image:image-filename.jpg|alt text you want your image to have]]
Once you save your page, this will appear as a red (i.e. "doesn't exist yet") link. Click on this link to go to an admin page where you can choose to upload the image you want to appear there.

When you've done that, go back to the page and refresh - the image should appear in place of the red link.


==Filling in the boxes==
The next piece of work is to fill in the meta data and other form content for the article.

'''Note:''' The wiki layout puts the checkbox to the left of the label.

#Edit the article.
#At the top, always check High-level issues: Needs flags.
#Check other flags that apply.
#Fill in a short Summary. Be mindful of SEO.
#At the bottom, in the Topics section, check all that apply.
#Under External Attribution, check whichever applies (HTML5Rocks! in this case), and provide the original link in the text box. '''Important:''' If the H5R URL contains "en/" in the path, remove it. That is, if the original article URL is <code>http://www.html5rocks.com/en/tutorials/eventsource/basics/</code>, change it to <code>http://www.html5rocks.com/tutorials/eventsource/basics/</code>.

==Author and publish date==
Enter the original author's name, their profile link, and the publish (and update) date(s) in the form fields. Delete the original info from the content box.

==Compatibility table==
In the Content field, move all the Supported Browser content down to the end of the content to make it easier to reference when you are filling out the compatibility table. Do not make manual tables; use the compatibility table buttons in the form. You can use the original author's info as reference, but it may be out of date. Always get the latest information from [http://caniuse.com/ caniuse.com].

When you have the compatibility tables filled out, delete the original supported browsers info from the content box.

==Housekeeping==

When you've finished an article, fill in the Status column of the spreadsheet: provide a status and your initials (i.e. Done - sr). Other people may be converting some articles in the same list, so always check the status column before you begin.