These instructions are specific to importing content from HTML5Rocks!

==Initial conversion==
Here's what you do to get the content into wiki format.

#From the [https://docs.google.com/a/google.com/spreadsheet/ccc?key=0AkRs-89PKiZpdHBqN2poNnJjV1c0N1FCYlN3ZUtpZ3c&pli=1#gid=0 Content Batches spreadsheet], copy the WPD URL for the article you intend to create.
#In a new window, open the [http://docs.webplatform.org/wiki/WPD:New_Page WPD:New_Page] page.
#Scroll down to the page type for the article (e.g., Tutorial).
#In the text field, paste the WPD URL, and click Create Tutorial Page.
#From the Content Batches spreadsheet, open the original HTML5Rocks! article using the Existing URL.
#Open the [http://toolserver.org/~diberri/cgi-bin/html2wiki/index.cgi html-to-wiki converter] page.
#Do one of the following:
#*In the original article, View Source, select all content, and copy; in the converter, choose the "Raw HTML" radio button, and paste the source into the HTML Source box.
#*In the original article, copy the full HTML5Rocks! URL; in the converter, choose the "Fetch from URL" radio button, and paste the original URL into the text field.
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

=I-framed content=
Some of the articles we're migrating may have content that appears in an i-frame. WikiMedia does not support iframes, so the best we can do is create a link to the content. In HTML5Rocks! usually the iframe has both code and layout from the playground. If the iframe contains a code sample, cut and paste the code sample into the article. If the iframe contains a sample page (that runs some wiz-bang doohicky), create a link to the page. 

See [[tutorials/audio_tag|audio tag]] for an example. 

=Filling in the boxes=

The next piece of work is to fill in all the meta data and other form content for the article.

'''Note:''' The wiki layout puts the checkbox to the left of the label.

#Edit the article.
#Always check High-level issues: Needs flags.
#Check other flags that apply.
#Fill in a short Summary. Be mindful of SEO.
#In the Topics section, check all that apply.
#Under External Attribution, check that which applies (MDN, HTML5Rocks!), and provide the link.

=Compatibility table=
In the Content field, move all the Supported Browser content down to the end of the content to make it easier to reference when you are filling out the compatibility table. You can use this info to start the tables, but you must also get more specific information from caniuse.com.

Once you have the compatibility table filled out, delete the Supported browsers content.

=Housekeeping=

When you've finished an article, fill in the Status column of the spreadsheet: provide a status and your initials (i.e. Done - sr). I'll be spot-converting some articles in the list, so check the status column before you begin.