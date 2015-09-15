---
title: Import Guide
summary: 'This is a guide to importing articles form other sources into WPD, including converting HTML to Wiki markup, how to fill in the page type forms, and more.'
tags:
  - Basic
  - Pages
uri: 'WPD:Content/Import Guide'

---
## <span>Summary</span>

This is a guide to importing articles form other sources into WPD, including converting HTML to Wiki markup, how to fill in the page type forms, and more.

**Note:** if you are importing content from HTML5Rocks! see [this guide](/WPD:Content/Import_Guide/H5R) for additional information.

## <span>Preparation</span>

### <span>1. Open up the pages you need to do this work:</span>

-   [Alex's content batch tracking spreadsheet](https://docs.google.com/a/chromium.org/spreadsheet/ccc?key=0AkRs-89PKiZpdHBqN2poNnJjV1c0N1FCYlN3ZUtpZ3c#gid=0)
-   The [Content requirements](http://webplatform.org/docs/WPD:Content_Requirements)
-   The [Site architecture document](http://webplatform.org/docs/WPD:Architecture)
-   The [New page creator tool](http://webplatform.org/docs/WPD:New_Page)

### <span>2. Choose a batch to work on</span>

Mark it as being in progress in Alex's spread

### <span>3. Choose an article to work on</span>

From the batch you have chosen.

Go to the relevant tab on Alex's spread for the batch you are working on. For your current article, do the following:

-   fill in the article name and existing URL.
-   fill in a new article name for your article, for the article as it will appear on WPD. This will generally be very similar to the name of the article as it appears on the [content requirements](http://webplatform.org/docs/WPD:Content_Requirements), but it might differ a bit. Read the [article titling guide](http://webplatform.org/docs/WPD:Manual_Of_Style#Descriptive_Titles_Manual_Of_Style.2C_Descriptive_Titles) to get more of a clue about this.
-   Choose a page category for your page, and fill it in. Page categories are generally the same as page types (see the [New page tool](http://webplatform.org/docs/WPD:New_Page)), but you should fill in a more specific page category identifier, as several different ones might fit into a single page type. For example, it would include things like DOM Interface (as opposed to API\_Object being the page type). The point of this column is to enumerate how many import scripts we would need based on how many categories of things to import there are from your content.
-   Choose a page type for your page to be based on, at the [New page tool](http://webplatform.org/docs/WPD:New_Page), and fill it in.

## <span>Implementation</span>

### <span>Fill in your chosen page title</span>

in the text field in the relevant page type section at the [New page tool](http://webplatform.org/docs/WPD:New_Page). You should basically replace "foo" in each case with your page title.

### <span>Press the "Create…" button for your page type</span>

This will take you to the form editing page for your new page.

### <span>record your page URL</span>

Immediately go to the bottom on the page and press "Save". Grab the Page URL and fill it in, in the "WPD URL" field of Alex's spreadsheet. It may seem tedious having to fill in all this information in Alex's spreadsheet, but it will make a lot of things way easier later on, if we have it to hand.

### <span>Start filling in the form</span>

Press the edit button, and start filling in the form.

[THESE INSTRUCTIONS WILL DIFFER FROM PAGE TO PAGE - THE CURRENT ONES ARE ONLY FOR TUTORIALS. WE'LL HAVE TO ADD MORE AS WE TACKLE DIFFERENT PAGE TYPES.]

#### <span>Main content</span>

First of all, tackle the main content box - this is where the bulk of your article content goes:

1.  Take a copy of the HTML you want to convert - this is best done like so, from the different sources:

    -   MDN - sign in to MDN, press the edit button, press the Source button on the editing interface, and copy and paste the contents of the `<body></body>` tags into a blank text file. Pro tip from Janet: adding
        `?raw&macros` to an MDN URL gives you the article content without the skin, but after evaluating templates; view the source of this to get the raw HTML.

    -   Opera web standards curriculum - this material is already in Wiki markup, so you've got a much easier job here!

    -   foo

2.  Check that the HTML validates: Go to <http://html5.validator.nu/>, select "text field" from the drop down select list, paste your body content in between the `<body></body>` tags, and press "Validate". If it comes up with errors, keeping fixing and rechecking until no more errors come up.

3.  Go to [this tool](http://toolserver.org/~diberri/cgi-bin/html2wiki/) or [this tool](http://labs.seapine.com/htmltowiki.cgi). Use either tool to convert your HTML into wikimarkup, and grab a copy of the result.

4.  Try pasting it into your page's content field and pressing "Save". It'll probably look terrible at the moment. You'll need to:

    -   **Remove excess whitespace**. Because of the way Wiki markup works, you'll need to put only a single line between paragraphs, and remove whitespace from the beginning of lines.

    -   **Get tables to render**. Because of a bug in the way media wiki tables are handled in semantic media wiki forms, you need to write your table syntax using the pipe hack. See <http://webplatform.org/docs/WPD:Manual_Of_Style/Tables> for more details.

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

    -   Foo

#### <span>flags/issues</span>

Check any boxes for issues that you know apply to the current article, and enter any editorial notes you want to add at this stage. [I REALLY WOULDN'T OBSESS OVER THESE RIGHT NOW - BETTER TO GET THE ARTICLES ON THE SITE FIRST, AND THEN WORRY ABOUT THESE LATER IF YOU ARE NOT SURE WHAT TO PUT]

#### <span>Summary</span>

Fill in a short top level summary to say what the article covers.

#### <span>Next and previous pages</span>

You probably won't be able to fill in next and previous pages at first. Leave this blank for now, and come back when you've filled in a whole series, or batch.

#### <span>Browser compatibility</span>

In the compatibility section, fill in information on what browser support there is for the technology features discussed in the tutorial. If the article does not discuss specific technology features, check the "Not required" checkbox.

To add a section detailing support for a single technology feature on desktop of mobile browsers, click the relevant "Add another button" and fill in the big box that appears - these are pretty intuitive. You can have multiple ones for multiple technology features.

[THE RENDERING OF THE COMPATIBILITY TABLES IS CURRENTLY A BIT BROKEN.]

The "Compatibility note" section is for you to add support information about a browser that doesn't appear in the list.

#### <span>See also section: references and further reading</span>

In the "See also" section, include any further information and links to other resources that you deem relevant.

Click a topic cluster if you want your article to be part of a specific topic cluster.

Put any internal links you want included on the page for further reading in the "Manual links" field, and external further reading in the "External links" field.

You need to include the links in bullet form, like this:

-   [Google](http://www.google.com)
-   [Mozilla](http://www.mozilla.org)
-   [Opera](http://www.opera.com)

[THERE ARE ONLY TWO TOPIC CLUSTERS LISTED INSIDE THE CSS TUTORIAL TYPE, AND LOADS MORE I COULD FORSEE BEING NEEDED. WHAT DO WE DO HERE IF WE WANT MORE? ALSO, I'M ASSUMING MANUAL LINKS? IS FOR OTHER PAGES ON WPD, IN WHICH CASE IT SHOULD BE CHANGED TO "INTERNAL LINKS" PERHAPS? THIS ISN'T VERY CLEAR.]

If you want to put any extra text and headings below the reference links in the "Manual sections" field, you'll need to start the headings at heading level three for them to appear underneath the "See also" heading. You can start them at page 2 if you want to include more sections at the bottom unrelated to "See also", but I'm not sure why you'd want to do that.

#### <span>Page topics</span>

The "Topics" section allows you to put the current article into a high level topic, such as Accessibility, or CSS. You can choose multiple topics for each article. These will appear at the very bottom of the page.

#### <span>Attribution</span>

The "External attribution" section is for you to fill in extra licensing information about the article. It should be licensed as CC-BY, in which case you can do nothing.

If it is instead licensed as CC-BY-SA, check the top checkbox. You may also need to fill in one of the other checkboxes instead, provide an external link and the summary at the bottom, to say what the content has come from and how it is licensed, as appropriate. If the content's license is incompatible with WPD, it will be removed.

[SOME MORE DETAILS WILL PROBABLY BE NEEDED HERE, BUT NOT SURE WHAT TO PUT AS YET.]

## <span>Tracking progress</span>

In the "overview" tab of Alex's tracking spread, you should update the status of each task for your batch as you complete them - these are the dreaded red boxes. The less red you see, the better! You will generally only change the status of these boxes twice - once to "In progress" when you start progress on a batch, and once when to "Done" you complete processing all articles in a batch (as you tend to do all the tasks concurrently.)

If you can't complete a batch, set your boxes to "Blocked" and report to the list why they are blocked.

