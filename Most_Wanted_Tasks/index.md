{{Page_Title}}
{{Flags}}
{{Summary_Section|A quick list of things that could be done around the site.}}
{{Basic Page}}
Here is just a quick list of specific things that could be done around the site.  They are organized by the time that they fit into from the [[WPD:Getting_Started | Getting Started Guide]].  If you see something you want to take up, just do it and then please be neat and remove it from the list once you are finished.

Thanks in advance for any tasks completed!  

==Specific call to action: help clean up HTML element references==

I would like to call upon anyone interested to help start going through the HTML element reference pages, and surrounding structures. I have written a detailed reference to creating/editing reference articles, which will help — see [[WPD:Content/Reference_articles|Reference articles]].

===Things already done===

* Changed link to HTML elements page on [[html|main HTML page]] from http://docs.webplatform.org/wiki/HTML/Elements to http://docs.webplatform.org/wiki/html/elements.
* Kept list of subpages at http://docs.webplatform.org/wiki/html/elements, but moved useful content from http://docs.webplatform.org/wiki/HTML/Elements on to it.
* Updated all the links to individual pages on http://docs.webplatform.org/wiki/html/elements to be correct - all lower case, and changed Meta:HTML to html in URLs still pointing to the meta namespace.
* The [[html/elements/p|Paragraph element]] page has been pretty much completed: you can use this for a reference when completing other reference pages.

===Things that need to be done===

* All other HTML element reference pages - see http://docs.webplatform.org/wiki/html/elements for a list!
* Adding a table into the main content of each article to say what attributes they can take. See http://docs.webplatform.org/wiki/html/attributes for the list of links you can choose from!
* Linking up each HTML element page to it's relevant DOM Interface. See http://docs.webplatform.org/wiki/dom for the full list.


===Pages being worked on===

* [[html/elements/blockquote|Blockquote]] worked on by [[User:Michistar|Michelle Carlough]]

* [[html/elements/ul|ul]] worked on by [[User:Michistar|Michelle Carlough]]

====Completed Pages====

* [[html/elements/p|The paragraph element]]


===[[User:Frozenice|fr0zenice's]] notes on updating the paragraph element page===

* check what the editor before me had done: http://docs.webplatform.org/w/index.php?title=html%2Felements%2Fp&diff=13355&oldid=9438
** summary, remarks and some other stuff as it seems
* I'm assuming the article has a formedit compatible template
** I used only the formedit, I think, as there was no need to fix anything in the raw source
* remove extra brackets around links, external links use single square brackets and a space as seperator for the displayed title
** in this case the only one was the MSDN Link right at the bottom, maybe note that this field automatically wraps it's text in single square brackets
** there might also be erroneous links in the other fields, seen some in other articles
[Import Notes only stuff from here on, that means the text that's in that field in formedit, not raw stuff via edit source]
* fixing anchor-links
** "[#events Events]" -> "[[#Events|Events]]"
** this requires a heading like "====Events===="
* collapsing multiple spaces / formatting line-breaks
** there were several places where 2-3 spaces were used instead of one, could be due to the import
** some table cells had more than one line, I formatted them like this: "Gets the namespace defined for the element.<br>This property is not supported for Metro style apps using JavaScript."
** that is totally open for discussion, of course, but the way it was took too much space, in my opinion
* fixing tables (the largest part)
** "|" needs to be replaced with "{{!}}" where appropriate, that means:
** the start and end tag of a table become "{{{!}} ... {{!}}}" instead of "{| ... |}"
** row breaks become "{{!}}-" instead of "|-"
** cells become "{{!}} text" instead of "| text"
** pipes DO NOT need replacing in link-markups in tables, e.g. this is fine: "{{!}}Sets an [[dom/attributes|'''attribute''']] object node as part of the object."

==Specific call to action: help clean up DOM interface references==

See http://docs.webplatform.org/wiki/dom

<p class="note">TO BE WRITTEN!</p>

==Specific call to action: help clean up HTML attribute references==

See http://docs.webplatform.org/wiki/html/attributes

<p class="note">TO BE WRITTEN!</p>

==Specific call to action: help clean up tutorials/concepts!==

I would like to call upon anyone who wants to help to start going through tutorials/concept articles, checking syntax, spelling and grammar, making sure links and images work, and making improvements as you see fit.

You can find a detailed guide to handling tutorials and concept articles at [[WPD:Content/Tutorials_and_concept_articles|Tutorials and concept articles]]. Follow the different steps on this page, and make sure everything looks ok, to go through a tutorial/concept successfully. Let [[mailto:cmills@opera.com Chris Mills know]] if you have any problems, want your work checked, or have any suggestions about improving the process.

To get started, choose a concept or tutorial article you want to help improve, and link to it in the subsection below so that others know you are working on it. Also put a note to say you are working on it in the editorial notes form field for that article. Good luck!

===Articles being worked on===

General Concepts:

HTML:

* [[guides/html_text|HTML Text]] worked on by [[User:Garbee|Jonathan Garbee]]

CSS:

* [[tutorials/learning what css is|What is CSS?]] worked on by [[User:Cmills|Chris Mills]]
* [[tutorials/learning why we use css|Why use CSS?]] worked on by [[User:Cmills|Chris Mills]]
* [[guides/getting started with css|Getting started with CSS]] worked on by [[User:Cmills|Chris Mills]]
* [[tutorials/css_text_quick_start|CSS Text Quick Start]] worked on by [[User:Michistar|Michelle Carlough]]
* [[guides/advanced_css_text_styling|Advanced CSS Text Styling]] worked on by [[User:Michistar|Michelle Carlough]]

JavaScript:

* [[concepts/programming/drawing_images_onto_canvas|Drawing images onto canvas]] worked on by [[User:Asbjornenge|Asbjorn Enge]]

SVG:

== Other tasks to choose from ==

===5 Minute Tasks===


===Half Hour Tasks===


===Half Day Tasks===

* Help close [https://www.w3.org/Bugs/Public/show_bug.cgi?id=19500 bug 19500]

* Help close [https://www.w3.org/Bugs/Public/show_bug.cgi?id=19373 bug 19373] -could be much faster if you are experienced in MediaWiki's syntax.  As in like a 5 minute task.

* Help close [https://www.w3.org/Bugs/Public/show_bug.cgi?id=19314 bug 19314]

Note:  These tasks are under half day tasks, but individual edits would be *far* faster.  Don't think you need to take on everything.  Just one or two edits in these areas is much appreciated.

* Look for duplicate pages that are in the root page.

* Put every page into a category except for the main page.  See the [[Special:UncategorizedPages|Uncategorized Pages]] to see where this is needed.

* Fix [http://docs.webplatform.org/w/index.php?title=Special:LonelyPages&limit=500&offset=0 Lonely Pages].   These are typically the pages that need the most work at this time.

* Move capitalized page paths that aren't following the style guide, check [[:Category:CSS]] for this

* Expand Topics on almost every page, every page should have multiple topics


====Always going====

* Clean up pages that do not have needed templates
{{Notes_Section
|Notes=Things should be placed at a conservative "best-guess" time-frame and try to fit in with what is specified on the Getting Started Guide.
}}
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}