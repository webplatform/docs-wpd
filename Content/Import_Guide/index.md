---
title: WPD:Content/Import Guide
---
<h1><span class="mw-headline" id="Import_Guide">Import Guide</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>This is a guide to importing articles form other sources into WPD, including converting HTML to Wiki markup, how to fill in the page type forms, and more.
</p><p><b>Note:</b> if you are importing content from HTML5Rocks! see <a href="/wiki/WPD:Content/Import_Guide/H5R" title="WPD:Content/Import Guide/H5R">this guide</a> for additional information.
</p>
<h2><span class="mw-headline" id="Preparation">Preparation</span></h2>
<h3><span class="mw-headline" id="1._Open_up_the_pages_you_need_to_do_this_work:">1. Open up the pages you need to do this work:</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="https://docs.google.com/a/chromium.org/spreadsheet/ccc?key=0AkRs-89PKiZpdHBqN2poNnJjV1c0N1FCYlN3ZUtpZ3c#gid=0">Alex's content batch tracking spreadsheet</a></li>
<li> The <a rel="nofollow" class="external text" href="http://webplatform.org/docs/WPD:Content_Requirements">Content requirements</a></li>
<li> The <a rel="nofollow" class="external text" href="http://webplatform.org/docs/WPD:Architecture">Site architecture document</a></li>
<li> The <a rel="nofollow" class="external text" href="http://webplatform.org/docs/WPD:New_Page">New page creator tool</a></li></ul>
<h3><span class="mw-headline" id="2._Choose_a_batch_to_work_on">2. Choose a batch to work on</span></h3>
<p>Mark it as being in progress in Alex's spread
</p>
<h3><span class="mw-headline" id="3._Choose_an_article_to_work_on">3. Choose an article to work on</span></h3>
<p>From the batch you have chosen.
</p><p>Go to the relevant tab on Alex's spread for the batch you are working on. For your current article, do the following:
</p>
<ul><li> fill in the article name and existing URL.</li>
<li> fill in a new article name for your article, for the article as it will appear on WPD. This will generally be very similar to the name of the article as it appears on the <a rel="nofollow" class="external text" href="http://webplatform.org/docs/WPD:Content_Requirements">content requirements</a>, but it might differ a bit. Read the <a rel="nofollow" class="external text" href="http://webplatform.org/docs/WPD:Manual_Of_Style#Descriptive_Titles_Manual_Of_Style.2C_Descriptive_Titles">article titling guide</a> to get more of a clue about this.</li>
<li> Choose a page category for your page, and fill it in. Page categories are generally the same as page types (see the <a rel="nofollow" class="external text" href="http://webplatform.org/docs/WPD:New_Page">New page tool</a>), but you should fill in a more specific page category identifier, as several different ones might fit into a single page type. For example, it would include things like DOM Interface (as opposed to API_Object being the page type). The point of this column is to enumerate how many import scripts we would need based on how many categories of things to import there are from your content.</li>
<li> Choose a page type for your page to be based on, at the <a rel="nofollow" class="external text" href="http://webplatform.org/docs/WPD:New_Page">New page tool</a>, and fill it in.</li></ul>
<h2><span class="mw-headline" id="Implementation">Implementation</span></h2>
<h3><span class="mw-headline" id="Fill_in_your_chosen_page_title">Fill in your chosen page title</span></h3>
<p>in the text field in the relevant page type section at the <a rel="nofollow" class="external text" href="http://webplatform.org/docs/WPD:New_Page">New page tool</a>. You should basically replace "foo" in each case with your page title. 
</p>
<h3><span class="mw-headline" id="Press_the_.22Create.E2.80.A6.22_button_for_your_page_type">Press the "Create…" button for your page type</span></h3>
<p>This will take you to the form editing page for your new page.
</p>
<h3><span class="mw-headline" id="record_your_page_URL">record your page URL</span></h3>
<p>Immediately go to the bottom on the page and press "Save". Grab the Page URL and fill it in, in the "WPD URL" field of Alex's spreadsheet. It may seem tedious having to fill in all this information in Alex's spreadsheet, but it will make a lot of things way easier later on, if we have it to hand.
</p>
<h3><span class="mw-headline" id="Start_filling_in_the_form">Start filling in the form</span></h3>
<p>Press the edit button, and start filling in the form.
</p><p>[THESE INSTRUCTIONS WILL DIFFER FROM PAGE TO PAGE - THE CURRENT ONES ARE ONLY FOR TUTORIALS. WE'LL HAVE TO ADD MORE AS WE TACKLE DIFFERENT PAGE TYPES.]
</p>
<h4><span class="mw-headline" id="Main_content">Main content</span></h4>
<p>First of all, tackle the main content box - this is where the bulk of your article content goes:
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
  <li><p>Go to <a rel="nofollow" class="external text" href="http://toolserver.org/~diberri/cgi-bin/html2wiki/">this tool</a> or <a rel="nofollow" class="external text" href="http://labs.seapine.com/htmltowiki.cgi">this tool</a>. Use either tool to convert your HTML into wikimarkup, and grab a copy of the result.</p></li>
  <li><p>Try pasting it into your page's content field and pressing "Save". It'll probably look terrible at the moment. You'll need to:</p>
    <ul>
      <li><p><b>Remove excess whitespace</b>. Because of the way Wiki markup works, you'll need to put only a single line between paragraphs, and remove whitespace from the beginning of lines.</p></li>
      <li><p><b>Get tables to render</b>. Because of a bug in the way media wiki tables are handled in semantic media wiki forms, you need to write your table syntax using the pipe hack. See <a rel="nofollow" class="external free" href="http://webplatform.org/docs/WPD:Manual_Of_Style/Tables">http://webplatform.org/docs/WPD:Manual_Of_Style/Tables</a> for more details.</p></li>
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
      <li><p>Foo</p></li>
    </ul>
  </li>
</ol>
<h4><span class="mw-headline" id="flags.2Fissues">flags/issues</span></h4>
<p>Check any boxes for issues that you know apply to the current article, and enter any editorial notes you want to add at this stage. [I REALLY WOULDN'T OBSESS OVER THESE RIGHT NOW - BETTER TO GET THE ARTICLES ON THE SITE FIRST, AND THEN WORRY ABOUT THESE LATER IF YOU ARE NOT SURE WHAT TO PUT]
</p>
<h4><span class="mw-headline" id="Summary_2">Summary</span></h4>
<p>Fill in a short top level summary to say what the article covers.
</p>
<h4><span class="mw-headline" id="Next_and_previous_pages">Next and previous pages</span></h4>
<p>You probably won't be able to fill in next and previous pages at first. Leave this blank for now, and come back when you've filled in a whole series, or batch.
</p>
<h4><span class="mw-headline" id="Browser_compatibility">Browser compatibility</span></h4>
<p>In the compatibility section, fill in information on what browser support there is for the technology features discussed in the tutorial. If the article does not discuss specific technology features, check the "Not required" checkbox.
</p><p>To add a section detailing support for a single technology feature on desktop of mobile browsers, click the relevant "Add another button" and fill in the big box that appears - these are pretty intuitive. You can have multiple ones for multiple technology features.
</p><p>[THE RENDERING OF THE COMPATIBILITY TABLES IS CURRENTLY A BIT BROKEN.]
</p><p>The "Compatibility note" section is for you to add support information about a browser that doesn't appear in the list.
</p>
<h4><span class="mw-headline" id="See_also_section:_references_and_further_reading">See also section: references and further reading</span></h4>
<p>In the "See also" section, include any further information and links to other resources that you deem relevant.
</p><p>Click a topic cluster if you want your article to be part of a specific topic cluster.
</p><p>Put any internal links you want included on the page for further reading in the "Manual links" field, and external further reading in the "External links" field.
</p><p>You need to include the links in bullet form, like this:
</p>
<ul><li> <a rel="nofollow" class="external text" href="http://www.google.com">Google</a></li>
<li> <a rel="nofollow" class="external text" href="http://www.mozilla.org">Mozilla</a></li>
<li> <a rel="nofollow" class="external text" href="http://www.opera.com">Opera</a></li></ul>
<p>[THERE ARE ONLY TWO TOPIC CLUSTERS LISTED INSIDE THE CSS TUTORIAL TYPE, AND LOADS MORE I COULD FORSEE BEING NEEDED. WHAT DO WE DO HERE IF WE WANT MORE? ALSO, I'M ASSUMING MANUAL LINKS? IS FOR OTHER PAGES ON WPD, IN WHICH CASE IT SHOULD BE CHANGED TO "INTERNAL LINKS" PERHAPS? THIS ISN'T VERY CLEAR.]
</p><p>If you want to put any extra text and headings below the reference links in the "Manual sections" field, you'll need to start the headings at heading level three for them to appear underneath the "See also" heading. You can start them at page 2 if you want to include more sections at the bottom unrelated to "See also", but I'm not sure why you'd want to do that.
</p>
<h4><span class="mw-headline" id="Page_topics">Page topics</span></h4>
<p>The "Topics" section allows you to put the current article into a high level topic, such as Accessibility, or CSS. You can choose multiple topics for each article. These will appear at the very bottom of the page.
</p>
<h4><span class="mw-headline" id="Attribution">Attribution</span></h4>
<p>The "External attribution" section is for you to fill in extra licensing information about the article. It should be licensed as CC-BY, in which case you can do nothing.
</p><p>If it is instead licensed as CC-BY-SA, check the top checkbox. You may also need to fill in one of the other checkboxes instead, provide an external link and the summary at the bottom, to say what the content has come from and how it is licensed, as appropriate. If the content's license is incompatible with WPD, it will be removed.
</p><p>[SOME MORE DETAILS WILL PROBABLY BE NEEDED HERE, BUT NOT SURE WHAT TO PUT AS YET.]
</p>
<h2><span class="mw-headline" id="Tracking_progress">Tracking progress</span></h2>
<p>In the "overview" tab of Alex's tracking spread, you should update the status of each task for your batch as you complete them - these are the dreaded red boxes. The less red you see, the better! You will generally only change the status of these boxes twice - once to "In progress" when you start progress on a batch, and once when to "Done" you complete processing all articles in a batch (as you tend to do all the tasks concurrently.)
</p><p>If you can't complete a batch, set your boxes to "Blocked" and report to the list why they are blocked.
</p><p><br />
</p><p><br />
</p>
<div class="attribution">
<p><br />
</p><p><br />
</p>
</div>

<!-- 
NewPP limit report
CPU time usage: 0.078 seconds
Real time usage: 0.091 seconds
Preprocessor visited node count: 192/1000000
Preprocessor generated node count: 906/1000000
Post‐expand include size: 531/2097152 bytes
Template argument size: 468/2097152 bytes
Highest expansion depth: 5/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%   49.258      1 - -total
 25.73%   12.672      1 - Template:Page_Title
 20.07%    9.884      1 - Template:Flags
 15.45%    7.609      1 - Template:External_Attribution
 11.40%    5.616      1 - Template:Summary_Section
  8.18%    4.029      1 - Template:Notes_Section
  6.05%    2.982      1 - Template:Topics
  4.91%    2.417      1 - Template:Basic_Page
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:529-0!*!0!!*!*!*!esi=1 and timestamp 20150731050501 and revision id 26707
 -->
