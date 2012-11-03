{{Page_Title|Creating/editing reference articles}}
{{Flags}}
{{Summary_Section|This article provides a guide to editing and creating reference articles. Following the steps below should give good results, but if you have any questions, feel free to share them on the mailing list or IRC or Q&A (see our [[WPD:Help|help page]] for more details.)}}
{{Basic Page}}
==1. What type of reference — make a choice!==

First you need to choose what type of reference you are creating or editing. The [[WPD:New_Page|new page tool]] has many different reference article types for you to choose from:

* [[WPD:New_Page#API_Listing|API listing]]: For pages that primarily list APIs, like css/properties.
* [[WPD:New_Page#API_Object|API object]]: If you're documenting an API, like <code>document</code>. Generally all pages in this type have a URL that contains <code>apis</code>, and has method and property pages that are sub-pages.
* [[WPD:New_Page#API_Object_Method|API object method]]: If you're documenting a ''method'' of an API, like <code>appendChild</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object.
* [[WPD:New_Page#API_Object_Property|API object property]]: If you're documenting a ''property'' of an API, like <code>childNodes</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object.
* [[WPD:New_Page#Constant|Constant]]: For pages that document a constant (for CSS, JavaScript, etc).
* [[WPD:New_Page#CSS_At_Rule|CSS at-rule]]: For pages that document a CSS At Rule (like @keyframes).
* [[WPD:New_Page#CSS_Function|CSS function]]: For pages that document a CSS function (like calc).
* [[WPD:New_Page#CSS_Keyword|CSS keyword]]: For pages that document a CSS keyword (like <code>inherit</code>).
* [[WPD:New_Page#CSS_Media_Feature|CSS media feature]]: For pages that document a CSS media feature.

* [[WPD:New_Page#CSS_Property|CSS property]]: For pages that document a CSS property, like <code>font-size</code>. Generally, all pages that have a URL that begins with <code>/css/properties/</code> should live here.
* [[WPD:New_Page#CSS_Selector|CSS selector]]: For pages that document a CSS selector (like the descendant selector). The URL should be a descriptive name since most of the selectors are illegal characters for MediaWiki URLs.
* [[WPD:New_Page#Data_Type|Data type]]: For pages that document a data type (for CSS, JavaScript, etc).
* [[WPD:New_Page#Event|Event]]: For pages that document a DOM event, like <code>click</code>
* [[WPD:New_Page#JavaScript_Operator|JavaScript operator]]: For pages that document a JavaScript operator, for example <code>+</code> or <code>.</code>. These normally live at URLs that begin with <code>js/operators/</code>. Note that you must use a readable long-form name as many of the actual values are illegal in URLs.
* [[WPD:New_Page#JavaScript_Statement|JavaScript statement]]: For pages that document a JavaScript statement, for example <code>for</code>, or <code>var</code>. Normally their URLs begin with <code>js/statements/</code>
* [[WPD:New_Page#Markup_Attribute|Markup attribute]]: For pages that document a Markup attribute (of HTML, SVG, MathML or XML), for example <code>class</code> or <code>href</code>. These normally live at URLs with a prefix of <code>{xml,html,mathml,svg}/attributes/</code>.
* [[WPD:New_Page#Markup_Element|Markup element]]: For pages that document a Markup Element (of HTML, SVG, MathML, or XML). For example, <code>canvas</code>, <code>div</code>, <code>circle</code>. These articles normally live at URLs with a prefix of <code>{xml,svg,html,mathml}/elements/</code>.
* [[WPD:New_Page#Markup_Structure|Markup structure]]: For pages that document a Markup structure (of HTML, SVG, or other types). For example, <code>CDATA</code>.
* [[WPD:New_Page#Regex_Metacharacter|Regex Metacharacter]]: For pages that document a regex metacharacter, like <code>*</code> or <code>.</code>. Make sure to use a descriptive name, not the literal character (as those are often illegal page names).

If you are not sure where to put your chosen subject, take your best guess; then afterwards send a mail to the webplatform public mailing list so someone else can check it.

==2. Create a new article page (if needed)== 

To enter your chosen page name, use lower case only, and use spaces in between the words, not hyphens or anything else.

Media Wiki doesn't allow most special characters in URLs, so you will need to write descriptions in many cases, rather than using actual characters. Also try to cut down on unnecessary words in URLs, if possible. So for example:

* '''regex dot''' rather than '''. regex metacharacter'''
* '''media at rule''' rather than '''@media'''
* '''javascript assignment operator''' rather than '''javascript ='''
* '''css child selector''' rather than '''css >'''

Generally reference article URLs are harder to cut down than tutorial article URLs, and you need to work more on making them descriptive enough to be meaningful, but do what you can.

Media wiki will resolve the spaces in URLs to underscores, so for example '''js/operators/javascript assignment operator''' will be created as 

http://docs.webplatform.org/wiki/js/operators/javascript_assignment_operator

While '''css/properties/text-align''' will be created as

http://docs.webplatform.org/wiki/css/properties/text-align

Press the relevant '''Create…''' button to create your new article.

==3. Make sure the article is (going to go) in the right location==

You can find a guide to the site structure at [[WPD:Content/Topic_Hierarchy|Topic Hierarchy]]. All articles should fit into this somewhere. If you have any issues with this structure, please tell us!

'''FOR EXISTING ARTICLES''' if you think an existing article wrongly placed, flag it with the '''Move candidate''' flag, and write an editorial note to suggest where to move it to.


==4. Make sure the fields in the edit form are filled in correctly==

The different types of reference article will have slightly different forms, and we don't have space to list them all here. What I will do is provide some examples that should help you go in the right direction.

<p class="note">TODO: ADD LINKS TO DECENT REFERENCES</p>

In general, you should find some decent already existing material about the thing you are documenting, to look up missing details. The [[http://w3.org|main W3C site]] has a lot of material to help you! You can all use search engines, I'm sure! 

You should also write a couple of examples demonstrating usage of the subject being discussed, as most reference pages have space for adding some examples.

===Example: an HTML markup element reference page===

Let's look at an example article, [[html/elements/p|The paragraph (p) element]]. In its edit form, you have the following fields:

* '''Page title''': Enter a properly capitalised title for your article. By default, only the URL slug will be used, for example '''html javascript sortable table'''. This makes for a good URL slug, but not a very good article title; in the example we've used '''The paragraph (p) element'''.
* '''Standardization status''': Choose what the subject's standardization status is. If you are not sure, search for W3 specs mentioning the article, to see what they say. In our example's case, &lt;p&gt; has been in a finished W3C recommendation since about HTML 2.0, so no question really. When the subject is mentioned in multiple specs, you should look for the status of the oldest spec it is featured in. For example, HTML5 mentions &lt;p&gt;, but it is not finished, so not a good measure to go off.
* '''API Name''' NOT SURE ABOUT THIS
* '''Top level summary''': contains a brief summary that says what the subject does.
* '''DOM interface''': In here, fill in '''dom/<name of interface>''', and it should create a link to the page that covers the DOM interface for the element. 
* '''Main Content''': This is where the main content of the article goes: this usually contains further information about the feature that might be useful; in our case information on block/inline and closing tag. Copy these and fill them in for future HTML element references
* '''Examples section''': This shouldn't be suppressed; you should fill in at least one or two examples to show usage of the subject, as appropriate.
* '''Usage/Notes/Import notes''': ??? Ignore these if you are not sure, which I'm not.
* '''Related specifications''': A place to provide link to the most recent specifications that cover the subject. In our example, we have included the links to the relevant pages of HTML5 and HTML4.01. Including links to older specs would not really be worth it. 
* '''Compatibility section''': This is where you record the browser compatibility for the features covered by your article. They are fairly self-explanatory when you try to use them.
* '''Topic clusters''': check the boxes that most relate to your article - do you want your article to be placed with a specific topics cluster?
* '''Manual links''': Here, include internal links to other articles that are related to this one. Where do you want your readers to go for more information? What should they read to learn more about how to use the subject, or find more examples?
* '''External links''': the same purpose as manual links, but this is specifically for external links.
* '''Manual sections'': this is for any other sections you want to add that are not covered by the other sections in the form. For example I have included exercise questions in a lot of my articles, but you could think about including other things as well.
* '''Topics''': check any topic boxes that related to technologies the article covers. Our '''Creating a sortable table using HTML and JavaScript''' example would definitely go under HTML and JavaScript.
* '''External attribution''': if the article actually comes from another site, provide details here. You should make sure not to use content which isn't licensed for such reuse.

'''FOR EXISTING ARTICLES''' Feel free to move stuff around to the right places, when fixing up an existing article.

==5. Ask for an editor/proofer!== 

When you have written a new article, let us know about it, via the mailing list. It is also a good idea to ask for a proof reader to come on board to look over your work for you, and correct any errors. We all make mistakes!

==6. Record your progress in working on the article==

When you are working on fixing up an article, it is a good idea to write who you are and what stage you have got to in the Editorial note box near the top of the edit form, so that others don't decided to take on the same work and start repeating what you have done.

When you have finished working on an article, leave a record of what you have done (very brief note) and say what else needs to be done. The flags can also help with this.
{{Notes_Section}}
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}