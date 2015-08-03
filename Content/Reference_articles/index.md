---
title: WPD:Content/Reference articles
---
<h1><span class="mw-headline" id="Creating.2Fediting_reference_articles">Creating/editing reference articles</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>This article provides a guide to editing and creating reference articles. Following the steps below should give good results, but if you have any questions, feel free to share them on the mailing list or IRC or Q&amp;A (see our <a href="/wiki/WPD:Help" title="WPD:Help">help page</a> for more details.)
</p>
<h2><span class="mw-headline" id="1._What_type_of_reference_.E2.80.94_make_a_choice.21">1. What type of reference — make a choice!</span></h2>
<p>First you need to choose what type of reference you are creating or editing. The <a href="/wiki/WPD:New_Page" title="WPD:New Page">new page tool</a> has many different reference article types for you to choose from:
</p>
<ul><li> <a href="/wiki/WPD:New_Page#API_Listing" title="WPD:New Page">API listing</a>: For pages that primarily list APIs, like css/properties.</li>
<li> <a href="/wiki/WPD:New_Page#API_Object" title="WPD:New Page">API object</a>: If you're documenting an API, like <code>document</code>. Generally all pages in this type have a URL that contains <code>apis</code>, and has method and property pages that are sub-pages.</li>
<li> <a href="/wiki/WPD:New_Page#API_Object_Method" title="WPD:New Page">API object method</a>: If you're documenting a <i>method</i> of an API, like <code>appendChild</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object.</li>
<li> <a href="/wiki/WPD:New_Page#API_Object_Property" title="WPD:New Page">API object property</a>: If you're documenting a <i>property</i> of an API, like <code>childNodes</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object.</li>
<li> <a href="/wiki/WPD:New_Page#Constant" title="WPD:New Page">Constant</a>: For pages that document a constant (for CSS, JavaScript, etc).</li>
<li> <a href="/wiki/WPD:New_Page#CSS_At_Rule" title="WPD:New Page">CSS at-rule</a>: For pages that document a CSS At Rule (like @keyframes).</li>
<li> <a href="/wiki/WPD:New_Page#CSS_Function" title="WPD:New Page">CSS function</a>: For pages that document a CSS function (like calc).</li>
<li> <a href="/wiki/WPD:New_Page#CSS_Keyword" title="WPD:New Page">CSS keyword</a>: For pages that document a CSS keyword (like <code>inherit</code>).</li>
<li> <a href="/wiki/WPD:New_Page#CSS_Media_Feature" title="WPD:New Page">CSS media feature</a>: For pages that document a CSS media feature.</li></ul>
<ul><li> <a href="/wiki/WPD:New_Page#CSS_Property" title="WPD:New Page">CSS property</a>: For pages that document a CSS property, like <code>font-size</code>. Generally, all pages that have a URL that begins with <code>/css/properties/</code> should live here.</li>
<li> <a href="/wiki/WPD:New_Page#CSS_Selector" title="WPD:New Page">CSS selector</a>: For pages that document a CSS selector (like the descendant selector). The URL should be a descriptive name since most of the selectors are illegal characters for MediaWiki URLs.</li>
<li> <a href="/wiki/WPD:New_Page#Data_Type" title="WPD:New Page">Data type</a>: For pages that document a data type (for CSS, JavaScript, etc).</li>
<li> <a href="/wiki/WPD:New_Page#Event" title="WPD:New Page">Event</a>: For pages that document a DOM event, like <code>click</code></li>
<li> <a href="/wiki/WPD:New_Page#JavaScript_Operator" title="WPD:New Page">JavaScript operator</a>: For pages that document a JavaScript operator, for example <code>+</code> or <code>.</code>. These normally live at URLs that begin with <code>js/operators/</code>. Note that you must use a readable long-form name as many of the actual values are illegal in URLs.</li>
<li> <a href="/wiki/WPD:New_Page#JavaScript_Statement" title="WPD:New Page">JavaScript statement</a>: For pages that document a JavaScript statement, for example <code>for</code>, or <code>var</code>. Normally their URLs begin with <code>js/statements/</code></li>
<li> <a href="/wiki/WPD:New_Page#Markup_Attribute" title="WPD:New Page">Markup attribute</a>: For pages that document a Markup attribute (of HTML, SVG, MathML or XML), for example <code>class</code> or <code>href</code>. These normally live at URLs with a prefix of <code>{xml,html,mathml,svg}/attributes/</code>.</li>
<li> <a href="/wiki/WPD:New_Page#Markup_Element" title="WPD:New Page">Markup element</a>: For pages that document a Markup Element (of HTML, SVG, MathML, or XML). For example, <code>canvas</code>, <code>div</code>, <code>circle</code>. These articles normally live at URLs with a prefix of <code>{xml,svg,html,mathml}/elements/</code>.</li>
<li> <a href="/wiki/WPD:New_Page#Markup_Structure" title="WPD:New Page">Markup structure</a>: For pages that document a Markup structure (of HTML, SVG, or other types). For example, <code>CDATA</code>.</li>
<li> <a href="/wiki/WPD:New_Page#Regex_Metacharacter" title="WPD:New Page">Regex metacharacter</a>: For pages that document a regex metacharacter, like <code>*</code> or <code>.</code>. Make sure to use a descriptive name, not the literal character (as those are often illegal page names).</li></ul>
<p>If you are not sure where to put your chosen subject, take your best guess; then afterwards send a mail to the webplatform public mailing list so someone else can check it.
</p>
<h2><span class="mw-headline" id="2._Create_a_new_article_page_.28if_needed.29">2. Create a new article page (if needed)</span></h2>
<p>To enter your chosen page name, use lower case only, and use spaces in between the words, not hyphens or anything else.
</p><p>Media Wiki doesn't allow most special characters in URLs, so you will need to write descriptions in many cases, rather than using actual characters. Also try to cut down on unnecessary words in URLs, if possible. So for example:
</p>
<ul><li> <b>regex dot</b> rather than <b>. regex metacharacter</b></li>
<li> <b>media at rule</b> rather than <b>@media</b></li>
<li> <b>javascript assignment operator</b> rather than <b>javascript =</b></li>
<li> <b>css child selector</b> rather than <b>css &gt;</b></li></ul>
<p>Generally reference article URLs are harder to cut down than tutorial article URLs, and you need to work more on making them descriptive enough to be meaningful, but do what you can.
</p><p>Media wiki will resolve the spaces in URLs to underscores, so for example <b>js/operators/javascript assignment operator</b> will be created as 
</p><p><a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/js/operators/javascript_assignment_operator">http://docs.webplatform.org/wiki/js/operators/javascript_assignment_operator</a>
</p><p>While <b>css/properties/text-align</b> will be created as
</p><p><a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/css/properties/text-align">http://docs.webplatform.org/wiki/css/properties/text-align</a>
</p><p>Press the relevant <b>Create…</b> button to create your new article.
</p>
<h2><span class="mw-headline" id="3._Make_sure_the_article_is_.28going_to_go.29_in_the_right_location">3. Make sure the article is (going to go) in the right location</span></h2>
<p>You can find a guide to the site structure at <a href="/wiki/WPD:Content/Topic_Hierarchy" title="WPD:Content/Topic Hierarchy" class="mw-redirect">Topic Hierarchy</a>. All articles should fit into this somewhere. If you have any issues with this structure, please tell us!
</p><p><b>FOR EXISTING ARTICLES</b> if you think an existing article wrongly placed, flag it with the <b>Move candidate</b> flag, and write an editorial note to suggest where to move it to.
</p><p><br />
</p>
<h2><span class="mw-headline" id="4._Make_sure_the_fields_in_the_edit_form_are_filled_in_correctly">4. Make sure the fields in the edit form are filled in correctly</span></h2>
<p>The different types of reference article will have slightly different forms, and we don't have space to list them all here. What I will do is provide some examples that should help you go in the right direction.
</p>
<p class="note">TODO: ADD LINKS TO DECENT REFERENCES</p>
<p>In general, you should find some decent already existing material about the thing you are documenting, to look up missing details. The [<a rel="nofollow" class="external text" href="http://w3.org%7Cmain">W3C site</a>] has a lot of material to help you! You can all use search engines, I'm sure! 
</p><p>You should also write a couple of examples demonstrating usage of the subject being discussed, as most reference pages have space for adding some examples.
</p>
<h3><span class="mw-headline" id="Example:_an_HTML_markup_element_reference_page">Example: an HTML markup element reference page</span></h3>
<p>Let's look at an example article, <a href="/wiki/html/elements/p" title="html/elements/p">The paragraph (p) element</a>. In its edit form, you have the following fields:
</p>
<ul><li> <b>Page title</b>: Enter a properly capitalised title for your article. By default, only the URL slug will be used, for example <b>html javascript sortable table</b>. This makes for a good URL slug, but not a very good article title; in the example we've used <b>The paragraph (p) element</b>.</li>
<li> <b>Standardization status</b>: Choose what the subject's standardization status is. If you are not sure, search for W3 specs mentioning the article, to see what they say. In our example's case, &lt;p&gt; has been in a finished W3C recommendation since about HTML 2.0, so no question really. When the subject is mentioned in multiple specs, you should look for the status of the oldest spec it is featured in. For example, HTML5 mentions &lt;p&gt;, but it is not finished, so not a good measure to go off.</li>
<li> <b>API name</b> NOT SURE ABOUT THIS</li>
<li> <b>Top level summary</b>: contains a brief summary that says what the subject does.</li>
<li> <b>DOM interface</b>: In here, fill in <b>dom/&lt;name of interface&gt;</b>, and it should create a link to the page that covers the DOM interface for the element. </li>
<li> <b>Main content</b>: This is where the main content of the article goes: this usually contains further information about the feature that might be useful; in our case information on block/inline and closing tag. Copy these and fill them in for future HTML element references</li>
<li> <b>Examples section</b>: This shouldn't be suppressed; you should fill in at least one or two examples to show usage of the subject, as appropriate.</li>
<li> <b>Usage/Notes/Import notes</b>:&#160;??? Ignore these if you are not sure, which I'm not.</li>
<li> <b>Related specifications</b>: A place to provide link to the most recent specifications that cover the subject. In our example, we have included the links to the relevant pages of HTML5 and HTML4.01. Including links to older specs would not really be worth it. </li>
<li> <b>Compatibility section</b>: This is where you record the browser compatibility for the features covered by your article. They are fairly self-explanatory when you try to use them.</li>
<li> <b>Topic clusters</b>: check the boxes that most relate to your article - do you want your article to be placed with a specific topics cluster?</li>
<li> <b>Manual links</b>: Here, include internal links to other articles that are related to this one. Where do you want your readers to go for more information? What should they read to learn more about how to use the subject, or find more examples?</li>
<li> <b>External links</b>: the same purpose as manual links, but this is specifically for external links.</li>
<li> '<i>Manual sections</i>: this is for any other sections you want to add that are not covered by the other sections in the form. For example I have included exercise questions in a lot of my articles, but you could think about including other things as well.</li>
<li> <b>Topics</b>: check any topic boxes that related to technologies the article covers. Our <b>Creating a sortable table using HTML and JavaScript</b> example would definitely go under HTML and JavaScript.</li>
<li> <b>External attribution</b>: if the article actually comes from another site, provide details here. You should make sure not to use content which isn't licensed for such reuse.</li></ul>
<p><b>FOR EXISTING ARTICLES</b> Feel free to move stuff around to the right places, when fixing up an existing article.
</p>
<h2><span class="mw-headline" id="5._Ask_for_an_editor.2Fproofer.21">5. Ask for an editor/proofer!</span></h2>
<p>When you have written a new article, let us know about it, via the mailing list. It is also a good idea to ask for a proof reader to come on board to look over your work for you, and correct any errors. We all make mistakes!
</p>
<h2><span class="mw-headline" id="6._Record_your_progress_in_working_on_the_article">6. Record your progress in working on the article</span></h2>
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

<!-- 
NewPP limit report
CPU time usage: 0.073 seconds
Real time usage: 0.088 seconds
Preprocessor visited node count: 114/1000000
Preprocessor generated node count: 806/1000000
Post‐expand include size: 740/2097152 bytes
Template argument size: 906/2097152 bytes
Highest expansion depth: 4/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%   47.782      1 - -total
 25.22%   12.051      1 - Template:Page_Title
 19.74%    9.431      1 - Template:Flags
 16.61%    7.935      1 - Template:External_Attribution
 11.96%    5.716      1 - Template:Summary_Section
  8.39%    4.008      1 - Template:Notes_Section
  6.74%    3.221      1 - Template:Basic_Page
  6.48%    3.095      1 - Template:Topics
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:6102-0!*!0!!*!*!*!esi=1 and timestamp 20150731111713 and revision id 16036
 -->
