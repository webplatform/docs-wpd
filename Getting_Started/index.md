=Contributing content to WPD =

Anyone can contribute to WPD. To get started, you'll first need to [http://docs.webplatform.org/w/index.php?title=Special:UserLogin&type=signup register] and verify your email address. There are many ways to contribute that take varying amounts of time and expertise. Often it's best to start with the simplest, fastest tasks and progress upwards from there as you gain expertise and experience. You can make meaningful contributions whether you have [[#5-minute tasks|five minutes]], [[#half-hour tasks|half an hour]], or [[#half-day tasks|half a day]]. 

The community is friendly and welcoming to newcomers; if you ever have any questions, [[WPD:Help|just ask]]!

[[File:get_start.png]]

== Creating a new page ==

Great, you have an idea for a new page you want to create, and you've determined the canonical URL where the content should live. For details on how to choose your page's URL, see [[WPD:Architecture|the architecture page]]. The next step is to use the New Page form to create your page from the proper template, and at the proper URL.

'''Steps for creating a new page'''

# Go to the [[WPD:New_Page|New Page]] page. 
# On that page identify the form to create the proper template (see [[#Choosing a content template]]).
# In the form's text field enter the URL for the new page in the text field, and click Create Page. 

For example, if you were creating a tutorial about a racing game, the URL might be '''/tutorials/racing_game'''.

=== Choosing a content template===

The [[WPD:New_Page|New Page]] page contains a form for each type of content you can create on the site. Each form consists of a text field where you enter the new page's URL and a button to create the page.

* If you are creating a tutorial, use the [[WPD:New_Page#Tutorial|Tutorial template]].
* If you want to describe a concept or feature, use the [[WPD:New_Page#Concept|Concept template]].
* If you are creating a reference page, the template you select is determined by the kind of API you are documenting.
** 
** 

The forms are listed in decreasing order of specificity. Identify the most specific form below that fits the type of content you'd like to create. For example

==Editing an existing page==

Editing an existing page is as easy as clicking the Edit button at the top of the page. 

==Content types and URLs==

WPD supports three basic types of content:

* '''Reference material''' -- JavaScript APIs, HTML and CSS reference). 
* '''Tutorials''' -- Step-by-step instructions for building a sample application or demonstrating a feature. 
* '''Concepts''' -- Provides an overview of a feature or API.

Each of these types content types has a unique URL name space--that is, where the page "lives". Figure out where the page should live. Consult the architecture page for an overview of the URL structure of the site.

http://docs.webplatform.org/wiki/concepts/internet_and_web/the_history_of_the_web

http://docs.webplatform.org/wiki/tutorials/

==Types of tasks==

There are many ways to contribute that take varying amounts of time and expertise. Often it's best to start with the simplest, fastest tasks and progress upwards from there as you gain expertise and experience. You can make meaningful contributions whether you have five minutes, half an hour, or half a day. 

===5-minute tasks===

* '''Correct grammar and spelling mistakes''' Pages with the [[Special:SearchByProperty/Content-20quality-20flag/Grammar-2FSpelling|grammar flag checked]] need some attention to fix grammar and spelling mistakes. Often these changes require no knowledge of MediaWiki or web development domain expertise to help with, which makes them great starter issues to focus on. See [[WPD:Flags/Content_Grammar_Spelling|for more information]].
* '''Filling in missing compatibility information''' Some pages have compatibility tables with missing cells, which you can find on [http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace= this list]. Generally the information can be verified by comparing a couple of other sources  (such as http://caniuse.com/) and then inputting the values in the form. 
* '''Data not semantic''' it is a bad practice to use include code examples that are not semantic, for example which use presentational IDs (e.g. red-box; editors-note would be better) or use presentational elements (such as &lt;center&gt; or &lt;font&gt;) or which just use inappropriate tag structures (for example &lt;br&gt;&lt;br&gt; to create line breaks between paragraphs). Please fix such instances! 
* '''Biased content''' WPD is supposed to be a vendor neutral documentation site, so efforts need to be made to remove biased information. For example, have you found a section that talks about a feature as if it is only usable in Firefox or Chrome, or a section of code that could work across all browsers, but won't because it only uses one or two browsers' vendor prefixes? Please ammend these accordingly, or at least check the '''Biased voice''' flag in the edit form
* '''Setting appropriate flags''' If you press the edit button at the top of an article, you can check the different flag checkboxes at the top of the edit form to indicate what tasks need to be done on that article.
* '''Fixing broken links''' Broken links are fairly easy to spot on WPD - they should be highlighted in a [[albatross/my broken link example|bold red colour]]. Please repair any you find, or at least check the '''Broken Links''' flag.
* '''Add more useful links''' Feel free to add useful, relevant links to external resources to show more examples to illustrate a technique or technology.
* '''Add the correct code syntax coloring to code blocks''' See [[WPD:Style_Manual#Code_syntax_highlight_coloring|our code coloring guide]] for details of how.

===Half-hour tasks===
* '''New examples''' It is always useful to add more examples to illustrate techniques or show good use of technologies. Look for articles where the examples are thin on the group.
* '''Incomplete API documentation''' Some reference articles or incomplete or need documentation fleshing out.
* '''Merge duplicate articles''' Every so often there will be pages that substantially duplicate content and should be merged into one. For example, an article that originally came from MSDN might have lots of overlapping content with another article that came from HTML5Rocks. Look for articles on [[Special:SearchByProperty/High-2Dlevel-20issue/Merge-20Candidate|this list]], then look in the editorial note at the top to find the other article they've been proposed to merge into. Often it just requires looking carefully through both articles to maintain the best of both without duplication. See [[WPD:Flags/Merge_Candidate]] for more information.
* '''Fill in stubs''' There are a number of pages that are just stubs - article titles and locations with no content, usually as a result of someone thinking that it'd be a good idea to have an article on X or Y, but not having time right now, so setting a placeholder for later. Filling these in would be greatly appreciated.
* '''Fill in exercise questions''' Some articles have exercise questions listed at the bottom of them - you can fill in useful exercise questions, in the '''Manual sections: (raw other sections, including headers)''' box of the '''See also section''' in the edit form for tutorials, guides, etc.
* '''Add screenshots or supporting information''' many articles have broken screenshot links, or notes such as '''Note: add screenshot to show what this should look like.''' in them. Please help out by adding needed screenshots, or further examples or supporting information to illustrate techniques.
* '''Clean up imported content''' Some content that came from other sources originally needs help to clean it up, ensure it is complete, make sure it is associated with the correct other pages when applicable, and generally bring it up to snuff. You can find out more specifics by reading about the [[WPD:Flags/Unreviewed_Import|Unreviewed Import]] flag.

===Half-day tasks===
* '''Merge articles''' Some articles are marked with the '''Merge candidate'' flag, meaning that they should be merged with other articles, perhaps because they duplicate information, or because they would work better as single entity.
* '''Split articles''' - this is the same as above, except in the opposite direction.
* '''[[WPD:New_Page|Write new articles]]''' It is always great to see people writing new content. To find out what needs to be written, see the suggestion board. IF you are not sure if something needs to be written, ask about it first, at our [[http://talk.webplatform.org/forums/|Forums]] or in our IRC channel (irc.freenode.org, port 6667, room webplatform). If you haven't got time to write a complete article, it is still worth creating a new page with the beginnings of a new article on it.
* '''Suggest new topics for inclusion''' If you have a good idea for an article that could be included but don't have the time or skills to write it yourself, it is still worth putting the idea forward. You can do this in a variety of ways, for example my e-mailing ideas to XXXXXXXXXXXX, writing then down on the suggestion board at XXXXXXXXXXXX, and XXXXXXXXXXXXX.
* '''Improve internal documentation''' If it took you time to figure out how to do something, consider writing up a guide so people who others can follow in your footsteps later.
* '''Rewriting CC-BY-SA content''' While we have content on the site that is licensed under CC-BY-SA, ideally we would prefer to rewrite it so that it is more distributable and reusable. If you see articles licensed like this, feel free to rewrite the content.

==The basics==
===The technology===

===The norms===
The WPD community is guided by a series of foundational norms that we call the [[WPD:Pillars|WPD Pillars]]. The Pillars document is a list of guiding principles that informs the more mundane norms and processes that govern the day-to-day operations of the site. You should read them carefully, but what's most important to know is that WPD is founded on the idea that we should assume good faith cooperation and that we prefer norms over rules. These norms and rules are documented within the wiki itself, in the WPD namespace (to keep it separate from documentation content). You can find the more mundane norms listed at [[WPD:Policy]].

===Flags and editorial notes===
WPD uses a system of flags and editorial notes to keep track of areas where improvements are required. [[link to flags]]

==References==

Here are some references to help you:

* [[WPD:Manual_Of_Style|Style Guide]]
* [http://www.mediawiki.org/wiki/Help:Formatting MediaWiki Formatting]
* [[WPD:Manual_Of_Style/Gotchas|Wiki Syntax Errors (Gotchas)]]
* [[WPD:Implementation_Patterns|Template and Form Implementation]]
* [[WPD:FAQ|General FAQ]]

Remember, if at any point you're unsure, ask the [[WPD:Help|IRC channel or the e-mail list]]. We love helping new editors get the hang of things!


==Bugs!==

See [[WPD:Filing|Filing bugs]]