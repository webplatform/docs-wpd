{{Flags}}
{{Basic Page}}
This is a guide to importing articles form other sources into WPD, including converting HTML to Wiki markup, how to fill in the page type forms, and more.

== Preparation ==

===1. Open up the pages you need to do this work:===

* [https://docs.google.com/a/chromium.org/spreadsheet/ccc?key=0AkRs-89PKiZpdHBqN2poNnJjV1c0N1FCYlN3ZUtpZ3c#gid=0 Alex's content batch tracking spreadsheet]
* The [http://webplatform.org/docs/WPD:Content_Requirements Content requirements]
* The [http://webplatform.org/docs/WPD:Architecture Site architecture document]
* The [http://webplatform.org/docs/WPD:New_Page New page creator tool]

===2. Choose a batch to work on===

Mark it as being in progress in Alex's spread

===3. Choose an article to work on===

From the batch you have chosen.

Go to the relevant tab on Alex's spread for the batch you are working on. For your current article, do the following:
* fill in the article name and existing URL.
* fill in a new article name for your article, for the article as it will appear on WPD. This will generally be very similar to the name of the article as it appears on the [http://webplatform.org/docs/WPD:Content_Requirements content requirements], but it might differ a bit. Read the [http://webplatform.org/docs/WPD:Manual_Of_Style#Descriptive_Titles_Manual_Of_Style.2C_Descriptive_Titles article titling guide] to get more of a clue about this.
* Choose a page category for your page, and fill it in. Page categories are generally the same as page types (see the [http://webplatform.org/docs/WPD:New_Page New page tool]), but you should fill in a more specific page category identifier, as several different ones might fit into a single page type. For example, it would include things like DOM Interface (as opposed to API_Object being the page type). The point of this column is to enumerate how many import scripts we would need based on how many categories of things to import there are from your content.
* Choose a page type for your page to be based on, at the [http://webplatform.org/docs/WPD:New_Page New page tool], and fill it in.

[ALEX - I CREATED A NEW "WPD NAME" COLUMN IN THE BATCH TABS ON YOUR SPREADSHEET, AS IT IS EASIER TO AKE A NOTE OF THE NAME YOU ARE GOING TO USE FIRST, AND THEN FILL IN THE URL WHEN THE NEW PAGE TOOL CREATES IT FOR YOU, WHIHC WON'T BE UNTIL SLIGHTLY LATER]

== Implementation ==

=== Fill in your chosen page title===

in the text field in the relevant page type section at the [http://webplatform.org/docs/WPD:New_Page New page tool]. You should basically replace "foo" in each case with your page title. 

===Press the "Create…" button for your page type===

This will take you to the form editing page for your new page.

===record your page URL===

Immediately go to the bottom on the page and press "Save". Grab the Page URL and fill it in, in the "WPD URL" field of Alex's spreadsheet. It may seem tedious having to fill in all this information in Alex's spreadsheet, but it will make a lot of things way easier later on, if we have it to hand.

===Start filling in the form===

Press the edit button, and start filling in the form.

[THESE INSTRUCTIONS WILL DIFFER FROM PAGE TO PAGE - THE CURRENT ONES ARE ONLY FOR TUTORIALS. WE'LL HAVE TO ADD MORE AS WE TACKLE DIFFERENT PAGE TYPES.]

====Main content====

First of all, tackle the main content box - this is where the bulk of your article content goes:

* Take a copy of the HTML you want to convert - this is best done like so, from the different sources:
** MDN - sign in to MDN, press the edit button, press the Source button on the editing interface, and copy and paste the contents of the <body></body> tags into a blank text file.
** Opera web standards curriculum - this material is already in Wiki markup, so you've got a much easier job here!
** foo
* Check that the HTML validates: Go to http://html5.validator.nu/, select "text field" from the drop down select list, paste your body content in between the <body></body> tags, and press "Validate". If it comes up with errors, keeping fixing and rechecking until no more errors come up.
* Go to http://w-i-k-i.appspot.com/. Choose "HTML to Wikipedia" from the drop down box at the bottom of the page. Paste your valid HTML into it, and press the "Convert input" button. Grab a copy of the result.
* Try pasting it into your page's content field and pressing "Save". It'll probably look terrible at the moment. You'll need to:
** Remove excess whitespace. Because of the way Wiki markup works, you'll need to put only a single line between paragraphs, and remove whitespace from the beginning of lines.
** Get tables to render [AT THE MOMENT THEY WON'T RENDER AT ALL, AND I REALLY DON'T KNOW WHY. ANY THOUGHTS?]
** Tidy up code blocks. Code samples should be wrapped in &lt;pre&gt;&lt;/pre&gt; tags, and you should use two spaces for each level of indent. The opening and closing tags should go on the same lines as the first and last lines of code, respectively. For example:
<pre>This
  is a
  code
Sample</pre>
** Images: To add images back into your article when you are importing it, first of all save a copy of them all locally. A good way to do this if there are loads of images is to go to the page where your article originally came from, then select File &gt; Save as... &gt; HTML file with Images.This should save a copy of the page you are on, with all the images and other assets associated with a page saved along with it, in a folder.

:: Next, for each image you need to create a special wiki markup tag that signifies you want to insert an image:

<pre>&#91; &#91; Image:image-filename.jpg|alt text you want your image to have&#93;&#93;</pre>

:: Once you save your page, this will appear as a red (i.e. "doesn't exist yet") link. Click on this link to go to an admin page where you can choose to upload the image you want to appear there. 

:: When you've done that, go back to the page and refresh - the image should appear in place of the red link. The wiki markup you entered above should be rendered in the final HTML:

<pre>&lt;img src="image-filename.jpg" alt="alt text you want your image to have"&gt;</pre>

:: Media wiki may have also tagged some icky presentational HTML crap onto the end of this like, like <code>border="0"</code>, but hey, it works, and no kittens are going to die.

** Executable code samples (I'M YET TO GET TO AN EXECUTABLE CODE SAMPLE)
** Foo

====flags/issues====

Check any boxes for issues that you know apply to the current article, and enter any editorial notes you want to add at this stage. [I REALLY WOULDN'T OBSESS OVER THESE RIGHT NOW - BETTER TO GET THE ARTICLES ON THE SITE FIRST, AND THEN WORRY ABOUT THESE LATER IF YOU ARE NOT SURE WHAT TO PUT]

====Summary====

Fill in a short top level summary to say what the article covers.

====Next and previous pages====

You probably won't be able to fill in next and previous pages at first. Leave this blank for now, and come back when you've filled in a whole series, or batch.

====Browser compatibility====

In the compatibility section, fill in information on what browser support there is for the technology features discussed in the tutorial. If the article does not discuss specific technology features, check the "Not required" checkbox.

To add a section detailing support for a single technology feature on desktop of mobile browsers, click the relevant "Add another button" and fill in the big box that appears - these are pretty intuitive. You can have multiple ones for multiple technology features.

[THE RENDERING OF THE COMPATIBILITY TABLES IS CURRENTLY A BIT BROKEN.]

The "Compatibility note" section is for you to add support information about a browser that doesn't appear in the list.

====See also section: references and further reading====

In the "See also" section, include any further information and links to other resources that you deem relevant.

Click a topic cluster if you want your article to be part of a specific topic cluster.

Put any internal links you want included on the page for further reading in the "Manual links" field, and external further reading in the "External links" field.

You need to include the links in bullet form, like this:

* [http://www.google.com Google]
* [http://www.mozilla.org Mozilla]
* [http://www.opera.com Opera]

[THERE ARE ONLY TWO TOPIC CLUSTERS LISTED INSIDE THE CSS TUTORIAL TYPE, AND LOADS MORE I COULD FORSEE BEING NEEDED. WHAT DO WE DO HERE IF WE WANT MORE? ALSO, I'M ASSUMING MANUAL LINKS? IS FOR OTHER PAGES ON WPD, IN WHICH CASE IT SHOULD BE CHANGED TO "INTERNAL LINKS" PERHAPS? THIS ISN'T VERY CLEAR.]

If you want to put any extra text and headings below the reference links in the "Manual sections" field, you'll need to start the headings at heading level three for them to appear underneath the "See also" heading. You can start them at page 2 if you want to include more sections at the bottom unrelated to "See also", but I'm not sure why you'd want to do that.

====Page topics====

The "Topics" section allows you to put the current article into a high level topic, such as Accessibility, or CSS. You can choose multiple topics for each article. These will appear at the very bottom of the page.

====Attribution====

The "External attribution" section is for you to fill in extra licensing information about the article. It should be licensed as CC-BY, in which case you can do nothing.

If it is instead licensed as CC-BY-SA, check the top checkbox. You may also need to fill in one of the other checkboxes instead, provide an external link and the summary at the bottom, to say what the content has come from and how it is licensed, as appropriate. If the content's license is incompatible with WPD, it will be removed.

[SOME MORE DETAILS WILL PROBABLY BE NEEDED HERE, BUT NOT SURE WHAT TO PUT AS YET.]

== Tracking progress ==

In the "overview" tab of Alex's tracking spread, you should update the status of each task for your batch as you complete them - these are the dreaded red boxes. The less red you see, the better! You will generally only change the status of these boxes twice - once to "In progress" when you start progress on a batch, and once when to "Done" you complete processing all articles in a batch (as you tend to do all the tasks concurrently.)

If you can't complete a batch, set your boxes to "Blocked" and report to the list why they are blocked.
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}