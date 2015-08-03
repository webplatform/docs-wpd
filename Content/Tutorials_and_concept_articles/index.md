---
title: WPD:Content/Tutorials and concept articles
---
<h1><span class="mw-headline" id="Creating.2Fediting_tutorials_and_concept_articles">Creating/editing tutorials and concept articles</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>This article provides a guide to editing and creating concept articles and tutorial articles. Following the steps below should give good results, but if you have any questions, feel free to share them on the mailing list or IRC or Q&amp;A (see our <a href="/wiki/WPD:Help" title="WPD:Help">help page</a> for more details.)
</p>
<h2><span class="mw-headline" id="1._Tutorial_or_concept_.E2.80.94_make_a_choice.21">1. Tutorial or concept — make a choice!</span></h2>
<p>First you need to choose whether a concept or tutorial article would be best for what you want to write. Both are informative articles that teach the reader something, but there is a difference in style
</p>
<ul><li> Concept articles teach the reader what something is, or how something works, in a clear series-of-facts manner. They don't require the reader to do anything except read through the document and take in the facts presented. A good example might be <b>Introduction to CSS element selectors</b>.</li>
<li> Tutorial articles also teach the reader how to do something, but do so in a much more applied way, which involves getting the reader to follow step by step instructions to get to a tangible result. A good example might be <b>Using element selectors to select paragraph elements</b></li></ul>
<p>If you are not sure which to choose, have a think about what subject or subjects you want to cover. If you are covering one subject and it isn't too much of an applied learning experience (maybe it is just an overview of what something is, rather than an in-depth treatment of how to do something specific with it), then a concept article is probably good, especially if it is pretty esoteric stuff (like how HTTP works). If you are showing how to do something specific then a tutorial is probably best, especially if you are showing how to marry two technologies together to do something (<b>Creating a sortable table using HTML and JavaScript</b>, for example).
</p><p><b>FOR EXISTING ARTICLES</b> if you think an existing article is in the wrong camp entirely, flag it with the <b>Move candidate</b> flag, and write an editorial note to suggest where to move it to.
</p>
<h2><span class="mw-headline" id="2._Make_sure_the_subject_matter_or_concept_works_for_a_single_article">2. Make sure the subject matter or concept works for a single article</span></h2>
<p>Have a look at what you want to cover. Does it work in a single article, or do you need to add more? Do you need to split it up into multiple articles? Generally you want to aim for an amount of information that is easily digestible by an average person in one evening's reading, say 2-3 hours. If it is any larger then the average person will not bother to read it.
</p><p><b>jQuery</b> is probably way to much to cover in a single article. <b>Ajax with jQuery</b> is probably still too much to cover in one article. <b>The basics of jQuery Ajax</b> is probably about right, then you probably want to follow that with a number of articles to describe more advanced features, and applied examples.
</p><p><b>FOR EXISTING ARTICLES</b> if you think an existing article is badly scoped, flag it with the <b>Merge candidate</b> or <b>Split candidate</b> flag, as appropriate, and write an editorial note to suggest what it should be merged with or split into.
</p>
<h2><span class="mw-headline" id="3._Make_sure_the_article_is_.28going_to_go.29_in_the_right_location">3. Make sure the article is (going to go) in the right location</span></h2>
<p>You can find a guide to the site structure at <a href="/wiki/WPD:Content/Topic_Hierarchy" title="WPD:Content/Topic Hierarchy" class="mw-redirect">Topic Hierarchy</a>. All articles should fit into this somewhere. If you have any issues with this structure, please tell us!
</p><p>concept articles need to go underneath <b>concepts</b>. If you think there are going to be a lot of similar concept articles, and you can't see a suitable subdirectory created already, then it might be an idea to create a new sub-directory for them to go into, for example concepts/css or concepts/jquery.
</p><p>Note: a while ago we agree to move all <b>guides</b> to <b>concepts</b>, and stop using <b>guides</b>, as it was a bit pointless having both.
</p><p>tutorial articles go underneath <b>tutorials</b>. If at all possible, just leave your article under tutorials, rather than creating subdirectories. The reason for this is that a lot of tutorials will cover multiple subjects, so to put them inside one single technology wouldn't make sense. Would <b>Creating a sortable table using HTML and JavaScript</b> go under tutorials/html or tutorials/javascript? It is more sensible to leave it under tutorials/, and then give it a Topic setting of both HTML and JavaScript, and use a script to place it automatically under both <a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/html/tutorials">http://docs.webplatform.org/wiki/html/tutorials</a> and <a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/javascript/tutorials">http://docs.webplatform.org/wiki/javascript/tutorials</a>.
</p><p>That is the eventual idea anyhow!
</p><p><b>FOR EXISTING ARTICLES</b> if you think an existing article wrongly placed, flag it with the <b>Move candidate</b> flag, and write an editorial note to suggest where to move it to.
</p>
<h2><span class="mw-headline" id="4._Create_a_new_page_.28if_needed.29">4. Create a new page (if needed)</span></h2>
<p>To create a new page, use our <a href="/wiki/WPD:New_Page" title="WPD:New Page">new page tool</a>. For concepts, use the <a href="/wiki/WPD:New_Page#Concept" title="WPD:New Page">concept</a> form, and for tutorials use the <a href="/wiki/WPD:New_Page#Tutorial" title="WPD:New Page">tutorial</a> form. You need to make sure the concept/ or tutorial/ bit is kept at the front of the entry in the form field. To enter your chosen page name, use lower case only, and use spaces in between the words, not hyphens or anything else. Media wiki will resolve these to underscores.
</p><p>When choosing a URL slug for your article, cut it down as much as possible, including only the most important words. If your tutorial was called <b>Creating a sortable table using HTML and JavaScript</b>, you could quite happily have a URL of <b>tutorials/html javascript sortable table</b>, which would be created as 
</p><p><a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/tutorials/html_javascript_sortable_table">http://docs.webplatform.org/wiki/tutorials/html_javascript_sortable_table</a>.
</p><p>Press the relevant <b>Create…</b> button to create your new article.
</p>
<h2><span class="mw-headline" id="5._Make_sure_the_article_structure_works">5. Make sure the article structure works</span></h2>
<p>An article should have the following
</p>
<ul><li> <b>Brief summary</b>: Says exactly what the article will cover, in a couple of sentences. Basically like an abstract.</li>
<li> <b>Introduction</b>: Briefly set the scene for the article. Say what you will cover in more detail, what the problem is, if we've covered a specific problem and how to solve it.</li>
<li> <b>Essential background information</b>: this can include installation instructions, brief history, a comment on what the technology feature is for, and why it solves the problem we outlined earlier, or is a better approach than the old method of solving the problem.</li>
<li> <b>The meat of the article</b>: For a concept, this can include a run down of the main features of the technology, or the main principles of making the technique work. For a tutorial, this should also include a step by step guide to implementing a solution to the problem, or an example that demonstrates use of the core features we are talking about.</li>
<li> <b>Further supporting information</b>: this can include caveats and things to watch out for, related links to more information, how to make it work in IE6, or other things that aren't central but are very useful.</li>
<li> <b>Conclusion</b>: Make any concluding points at the end of the article.</li>
<li> <b>Browser support</b>: Make a note of browser support for the feature or features covered in the article, even if it is just links to the relevant page on caniuse.com</li>
<li><b>Code examples</b>: we aren't 100% sure where to include these yet, but even so, create a code example or two to show the point of the article in action, if applicable.</li></ul>
<h2><span class="mw-headline" id="6._Make_sure_the_fields_in_the_edit_form_are_filled_in_correctly">6. Make sure the fields in the edit form are filled in correctly</span></h2>
<p>In the article edit form, there are several form fields to fill in to create your article. Let's go through all of these now
</p>
<ul><li> <b>Page title</b>: Enter a properly capitalised title for your article. By default, only the URL slug will be used, for example <b>html javascript sortable table</b>. This makes for a good URL slug, but not a very good article title, so enter <b>Creating a sortable table using HTML and JavaScript</b> in the Page title field.</li>
<li> <b>High level issues, content, editorial notes</b>: Checking the checkboxes creates the flags that I mentioned above. Content and notes allows you to enter more details about what is currently wrong with the article. When going through articles, please check flags and enter more details to let the eventual editors deal with the article as effectively as possible.</li>
<li> <b>Byline</b>: allows you to include your name, website address, and a publication date, if you want to be credited as the sole author of the text.</li>
<li> <b>Top level summary</b>: this is where the brief summary goes - it says concisely what will be covered in the article.</li>
<li> <b>Next/Previous page</b>: In a tutorial series, this is where to list the previous and next page in the series, to create a linear navigation between series members. We haven't really used this much so far.</li>
<li> <b>Content</b>. This is where the main content of the article goes, everything from the introduction to the conclusion/end.</li>
<li> <b>Usage/Notes/Import notes</b>:&#160;??? Ignore these if you are not sure, which I'm not.</li>
<li> <b>Compatibility section</b>: This is where you record the browser compatibility for the features covered by your article. They are fairly self-explanatory when you try to use them.</li>
<li> <b>Topic clusters</b>: check the boxes that most relate to your article - do you want your article to be placed with a specific topics cluster? For <b>Creating a sortable table using HTML and JavaScript</b>, HTML might be appropriate, but I'm not sure what else is. </li>
<li> <b>Manual links</b>: Here, include internal links to other articles that are related to this one. Where do you want your readers to go for more information? What should they read next after this article?</li>
<li> <b>External links</b>: the same purpose as manual links, but this is specifically for external links.</li>
<li> '<i>Manual sections</i>: this is for any other sections you want to add that are not covered by the other sections in the form. For example I have included exercise questions in a lot of my articles, but you could think about including other things as well.</li>
<li> <b>Topics</b>: check any topic boxes that related to technologies the article covers. Our <b>Creating a sortable table using HTML and JavaScript</b> example would definitely go under HTML and JavaScript.</li>
<li> <b>External attribution</b>: if the article actually comes from another site, provide details here. You should make sure not to use content which isn't licensed for such reuse.</li></ul>
<p><b>FOR EXISTING ARTICLES</b> Feel free to move stuff around to the right places, when fixing up an existing article.
</p>
<h2><span class="mw-headline" id="7._Try_to_get_formatting_and_language_done_as_well_as_possible">7. Try to get formatting and language done as well as possible</span></h2>
<p>You shouldn't let language and formatting perfection get in the way of writing a useful article, but we do urge you to try to get the language and formatting done to as good as degree as you can when submitting a new article of cleaning up an existing one. To find out more details, read our <a href="/wiki/WPD:Manual_Of_Style" title="WPD:Manual Of Style" class="mw-redirect">Manual of style</a> for lots of information on style of language, titles, etc.
</p><p>For syntax help, look at the [<a class="external text" href="http://www.mediawiki.org/wiki/Help:Formatting">Media Wiki formatting guide</a>]. If you encounter a weird problem when trying to get some syntax to work, see if you can find an answer in our <a href="/wiki/WPD:Manual_Of_Style/Gotchas" title="WPD:Manual Of Style/Gotchas" class="mw-redirect">Gotchas page</a>.
</p>
<h2><span class="mw-headline" id="8._Other_adjustments_to_be_made">8. Other adjustments to be made</span></h2>
<p>The following is a list of other things that need to be checked through before the article is deemed complete.
</p>
<ul><li> <b>Make sure images are all present</b>: If you see red links that are supposed to point to images, then try to find a suitable image (or make one yourself if you are able) to upload for this purpose. If the article comes from another location, then you can probably find it by going to that link.</li>
<li> <b>Make sure images have alt text</b>: Very important for accessibility; to add alt text to an image, you use this syntax: &#91;&#91;image:image-name.jpg|alt=alt text for my image&#93;&#93;  </li>
<li> <b>Make sure links work</b>: You can spot dead links a mile off, as they are bright red, but you should also check that the other links present go to the right places.</li>
<li> <b>Remove obvious biased or out of place language</b>: For example, if the article is talking about a feature only in the context of working in WebKit and includes WebKit-specific code, you should update the language and code to remove this bias. If there is language that says something like "To find more out about this subject, consult these other articles on MDN", then link to WPD articles instead, and update it.</li>
<li> <b>Give the article a general update</b>: Have a read through and think about whether it is up-to-date, or whether any of the text, code examples, etc. need updating. Write new text and code examples to suit.  </li></ul>
<h2><span class="mw-headline" id="9._Ask_for_an_editor.2Fproofer.21">9. Ask for an editor/proofer!</span></h2>
<p>When you have written a new article, let us know about it, via the mailing list. It is also a good idea to ask for a proof reader to come on board to look over your work for you, and correct any errors. We all make mistakes!
</p>
<h2><span class="mw-headline" id="10._Record_your_progress_in_working_on_the_article">10. Record your progress in working on the article</span></h2>
<p>When you are working on fixing up an article, it is a good idea to write who you are and what stage you have got to in the Editorial note box near the top of the edit form, so that others don't decided to take on the same work and start repeating what you have done.
</p><p>When you have finished working on an article, leave a record of what you have done (very brief note) and say what else needs to be done. The flags can also help with this.
</p><p><br />
</p><p><br />
</p>
<div class="attribution">
<p><br />
</p><p><br />
</p>
</div>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:6069-0!*!0!!*!*!*!esi=1 and timestamp 20150731182858 and revision id 14342
 -->
