{{Page_Title}}
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

To enter your chosen page name, use lower case only, and use spaces in between the words, not hyphens or anything else. Media wiki will resolve these to underscores.

When choosing a URL slug for your article, cut it down as much as possible, including only the most important words. If your tutorial was called '''Creating a sortable table using HTML and JavaScript''', you could quite happily have a URL of '''tutorials/html javascript sortable table''', which would be created as 

http://docs.webplatform.org/wiki/tutorials/html_javascript_sortable_table.

Press the relevant '''Create…''' button to create your new article.

==2. Make sure the subject matter or concept works for a single article==

Have a look at what you want to cover. Does it work in a single article, or do you need to add more? Do you need to split it up into multiple articles? Generally you want to aim for an amount of information that is easily digestible by an average person in one evening's reading, say 2-3 hours. If it is any larger then the average person will not bother to read it.

'''jQuery''' is probably way to much to cover in a single article. '''Ajax with jQuery''' is probably still too much to cover in one article. '''The basics of jQuery Ajax''' is probably about right, then you probably want to follow that with a number of articles to describe more advanced features, and applied examples.

'''FOR EXISTING ARTICLES''' if you think an existing article is badly scoped, flag it with the '''Merge candidate''' or '''Split candidate''' flag, as appropriate, and write an editorial note to suggest what it should be merged with or split into.

==3. Make sure the article is (going to go) in the right location==

You can find a guide to the site structure at [[WPD:Content/Topic_Hierarchy|Topic Hierarchy]]. All articles should fit into this somewhere. If you have any issues with this structure, please tell us!

concept articles need to go underneath '''concepts'''. If you think there are going to be a lot of similar concept articles, and you can't see a suitable subdirectory created already, then it might be an idea to create a new sub-directory for them to go into, for example concepts/css or concepts/jquery.

Note: a while ago we agree to move all '''guides''' to '''concepts''', and stop using '''guides''', as it was a bit pointless having both.

tutorial articles go underneath '''tutorials'''. If at all possible, just leave your article under tutorials, rather than creating subdirectories. The reason for this is that a lot of tutorials will cover multiple subjects, so to put them inside one single technology wouldn't make sense. Would '''Creating a sortable table using HTML and JavaScript''' go under tutorials/html or tutorials/javascript? It is more sensible to leave it under tutorials/, and then give it a Topic setting of both HTML and JavaScript, and use a script to place it automatically under both http://docs.webplatform.org/wiki/html/tutorials and http://docs.webplatform.org/wiki/javascript/tutorials.

That is the eventual idea anyhow!

'''FOR EXISTING ARTICLES''' if you think an existing article wrongly placed, flag it with the '''Move candidate''' flag, and write an editorial note to suggest where to move it to.


==5. Make sure the article structure works==

An article should have the following

* '''Brief summary''': Says exactly what the article will cover, in a couple of sentences. Basically like an abstract.
* '''Introduction''': Briefly set the scene for the article. Say what you will cover in more detail, what the problem is, if we've covered a specific problem and how to solve it.
* '''Essential background information''': this can include installation instructions, brief history, a comment on what the technology feature is for, and why it solves the problem we outlined earlier, or is a better approach than the old method of solving the problem.
* '''The meat of the article''': For a concept, this can include a run down of the main features of the technology, or the main principles of making the technique work. For a tutorial, this should also include a step by step guide to implementing a solution to the problem, or an example that demonstrates use of the core features we are talking about.
* '''Further supporting information''': this can include caveats and things to watch out for, related links to more information, how to make it work in IE6, or other things that aren't central but are very useful.
* '''Conclusion''': Make any concluding points at the end of the article.
* '''Browser support''': Make a note of browser support for the feature or features covered in the article, even if it is just links to the relevant page on caniuse.com
*'''Code examples''': we aren't 100% sure where to include these yet, but even so, create a code example or two to show the point of the article in action, if applicable.

==6. Make sure the fields in the edit form are filled in correctly==

In the article edit form, there are several form fields to fill in to create your article. Let's go through all of these now

* '''Page title''': Enter a properly capitalised title for your article. By default, only the URL slug will be used, for example '''html javascript sortable table'''. This makes for a good URL slug, but not a very good article title, so enter '''Creating a sortable table using HTML and JavaScript''' in the Page title field.
* '''High level issues, content, editorial notes''': Checking the checkboxes creates the flags that I mentioned above. Content and notes allows you to enter more details about what is currently wrong with the article. When going through articles, please check flags and enter more details to let the eventual editors deal with the article as effectively as possible.
* '''Byline''': allows you to include your name, website address, and a publication date, if you want to be credited as the sole author of the text.
* '''Top level summary''': this is where the brief summary goes - it says concisely what will be covered in the article.
* '''Next/Previous page''': In a tutorial series, this is where to list the previous and next page in the series, to create a linear navigation between series members. We haven't really used this much so far.
* '''Content'''. This is where the main content of the article goes, everything from the introduction to the conclusion/end.
* '''Usage/Notes/Import notes''': ??? Ignore these if you are not sure, which I'm not.
* '''Compatibility section''': This is where you record the browser compatibility for the features covered by your article. They are fairly self-explanatory when you try to use them.
* '''Topic clusters''': check the boxes that most relate to your article - do you want your article to be placed with a specific topics cluster? For '''Creating a sortable table using HTML and JavaScript''', HTML might be appropriate, but I'm not sure what else is. 
* '''Manual links''': Here, include internal links to other articles that are related to this one. Where do you want your readers to go for more information? What should they read next after this article?
* '''External links''': the same purpose as manual links, but this is specifically for external links.
* '''Manual sections'': this is for any other sections you want to add that are not covered by the other sections in the form. For example I have included exercise questions in a lot of my articles, but you could think about including other things as well.
* '''Topics''': check any topic boxes that related to technologies the article covers. Our '''Creating a sortable table using HTML and JavaScript''' example would definitely go under HTML and JavaScript.
* '''External attribution''': if the article actually comes from another site, provide details here. You should make sure not to use content which isn't licensed for such reuse.

'''FOR EXISTING ARTICLES''' Feel free to move stuff around to the right places, when fixing up an existing article.

==7. Try to get formatting and language done as well as possible==

You shouldn't let language and formatting perfection get in the way of writing a useful article, but we do urge you to try to get the language and formatting done to as good as degree as you can when submitting a new article of cleaning up an existing one. To find out more details, read our [[WPD:Manual_Of_Style|Manual of style]] for lots of information on style of language, titles, etc.

For syntax help, look at the [[http://www.mediawiki.org/wiki/Help:Formatting Media Wiki formatting guide]]. If you encounter a weird problem when trying to get some syntax to work, see if you can find an answer in our [[WPD:Manual_Of_Style/Gotchas|Gotchas page]].

==8. Other adjustments to be made==

The following is a list of other things that need to be checked through before the article is deemed complete.

* '''Make sure images are all present''': If you see red links that are supposed to point to images, then try to find a suitable image (or make one yourself if you are able) to upload for this purpose. If the article comes from another location, then you can probably find it by going to that link.
* '''Make sure images have alt text''': Very important for accessibility; to add alt text to an image, you use this syntax: &#91;&#91;image:image-name.jpg|alt=alt text for my image&#93;&#93;  
* '''Make sure links work''': You can spot dead links a mile off, as they are bright red, but you should also check that the other links present go to the right places.
* '''Remove obvious biased or out of place language''': For example, if the article is talking about a feature only in the context of working in WebKit and includes WebKit-specific code, you should update the language and code to remove this bias. If there is language that says something like "To find more out about this subject, consult these other articles on MDN", then link to WPD articles instead, and update it.
* '''Give the article a general update''': Have a read through and think about whether it is up-to-date, or whether any of the text, code examples, etc. need updating. Write new text and code examples to suit.  

==9. Ask for an editor/proofer!== 

When you have written a new article, let us know about it, via the mailing list. It is also a good idea to ask for a proof reader to come on board to look over your work for you, and correct any errors. We all make mistakes!

==10. Record your progress in working on the article==

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