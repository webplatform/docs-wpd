These are instructions specific to importing content from HTML5Rocks!

=Initial conversion=

Here's what you do to get the content into wiki format.

#From the Content Batches spreadsheet, copy the WPD URL.
#In a new window, open WPD:New_Page.
#Scroll down to the Tutorial page type.
#In the text field, paste the WPD URL, and click Create Tutorial Page.
#From the Content Batches spreadsheet, open the Existing URL of the article.
#View Source, select all content, and copy.
#Open the html-to-wiki converter.
#In the Input field, paste in the HTML from the article, select HTML to Wikipedia and click Convert Input.
#In the Conversion output, select all text, and copy.
#In the new WPD page, in the Content field, paste the text, and click Save page.

=Clean up=

There will be a lot of cruft - stuff that you'll delete or otherwise fix.

#In the new WPD page, click the EDIT button.
#In the Content field, remove everything up to the title - usually an H1 marked with a single '='.
#Remove everything between the title and the "by" line; we'll keep the "by" line.
#Remove everything up to the "Published" text, remove any cruft around the text (including the spaces before), but leave the "Published XXXX" in place.
#Keep the Supported Browsers information - for now - but remove everything between the last browser "supported" or "unsupported" - i.e. "Your browser may ..." and so on up to the first subheading of the article; this includes Table of Contents.
#Scroll down to the last line of article content, and remove everything after it - including the page content license blather, the page comments JavaScript references, etc.
#Remove any double line breaks - make them single line breaks.
#Save the article and have a look.

=Fix broken links=
You'd think that the converter would be able to create simple links of the format, "[URL title]" but this is apparently not so (I think this a bug). Until we can get the converter to work, we'll have to go back and fix each link. These appear in red when the page is in read mode. Note that the links also come in with double brackets [[ ... ]] - these should be single brackets [ ... ].

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