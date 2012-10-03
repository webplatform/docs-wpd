This website, Web Platform Docs is written, edited, and organized by an active community&mdash;many of them volunteers.

It's incredibly easy to get started, and you can make meaningful contributions whether you have five minutes, half an hour, or half a day. The community is friendly and welcoming to any newcomers. If you ever have any questions, just ask!

==Getting started==

Web Platform Docs (we call it WPD) is an open wiki that anyone may edit. All you need to do is get a username, verify your e-mail address, and you're set!

To get a username, click '''Login''' on any page and follow the instructions to create an account.

==Finding help==

WPD is an active and welcoming community. We'll help you get started, and there's no such thing as a dumb question.

'''public-webplatform@w3.org''' is the mailing list we use to coordinate on larger issues, like article organization, changes to common templates or forms, or setting new norms. It's also where we announce things like upcoming hackathons (which everyone is welcome to join). You can join at  http://lists.w3.org/Archives/Public/public-webplatform/. You do '''not''' need a W3C account to join or send messages.

You can find us on '''IRC''' (essentially a special chat room) at '''irc.freenode.org''' at '''#webplatform'''. IRC is the best place to ask simple questions like "why can I not get this formatting to look right" or "do we have a template I can use to do X?". Generally folks are around to answer any questions you might have. If you're new to IRC, check out [http://richard.esplins.org/siwi/2011/07/08/getting-started-freenode-irc/ this great getting started guide].

Remember: all of WPD is a wiki. If you ever find content that's not quite up to snuff (including pages like this one that help you get started), please help improve them! If everyone leaves a page in just a little bit better shape than the way they found it, WPD will become more and more useful.

==The basics==

===The technology===
Web Platform Docs is built on MediaWiki (the same system Wikipedia is built on) and the Semantic Media Wiki and Semantic Forms extensions. These extensions allow us to create structured forms for most pages, which means that often making substantive contributions to pages is as simple as filling in a form field! This means that you don't have to learn MediaWiki's somewhat arcane syntax to be helpful. Editing a page is as simple as hitting the '''Edit''' button at the top of any page.

===The norms===
The WPD community is guided by a series of foundational norms that we call the [[WPD:Pillars|Pillars]]. The Pillars document is a list of abstract guiding principles that informs the more mundane norms and processes that govern the day-to-day operations of the site. You should read them carefully, but what's most important to know is that WPD is founded on the idea that we should assume good faith cooperation and prefer norms over rules. These norms and rules are documented within the wiki itself, in the WPD namespace (to keep it separate from documentation content). You can find the more mundane norms listed at [[WPD:Policy]].

===Flags and editorial notes===
WPD uses a system of flags and editorial notes to keep track of areas where improvements are required. 

Flags are high-level labels on a page the help us find pages that require some class of work, like new examples or grammar help. They display at the top of the page in a prominent way for logged-in users, but also show for logged-out users. Most content pages have a space for them, and when you go to edit a form you'll find that they're shown as a long list of checkboxes. Most flags are toggled by hand, although some are set automatically by some templates. You can find more about each flag at [[WPD:Flags]], including guidelines on what they mean, when they should be used, and perhaps most importantly, when they can be ''removed'' from content. 

Editorial notes, by default, don't show up for users who are not logged-in. They are meant to allow editors to leave tactical notes to one another about specific work that needs to be done to improve the page. They often go hand-in-hand with flags. For example, the page might be flagged with "Examples do not follow best practices", and within the page the examples an editorial note might show up next to the specific example that needs work describing precisely which best practices it doesn't follow.  Each of the sub-pages of [[WPD:Flags]] describes which Editorial notes to use in conjunction with which flags and why. Most editorial notes are simple "sub-classes" of the basic [[Template:Editorial|editorial note template]].

Editors can provide a lot of value by merely making sure that pages have the correct flags and editorial notes set. This makes it so that other editors can easily come along and find and accomplish specific improvements, focusing their attention on the spots that need the most help.

==Contributing==
There are many ways to contribute that take varying amounts of time and expertise. Often it's best to start with the simplest, fastest tasks and progress upwards from there as you gain expertise and experience.

Here are some references to help you:
* [[WPD:Manual_Of_Style|Style Guide]]
* [http://www.mediawiki.org/wiki/Help:Formatting MediaWiki Formatting]
* [[WPD:Manual_Of_Style/Gotchas|Wiki Syntax Errors (Gotchas)]]
* [[WPD:Implementation_Patterns|Template and Form Implementation]]
* [[WPD:FAQ|General FAQ]]

Remember, if at any point you're unsure, ask the IRC channel or the e-mail list. We love helping new editors get the hang of things!

===5-minute tasks===
* '''Correct grammar and spelling mistakes''' Pages with the [[Special:SearchByProperty/Content-20quality-20flag/Grammar-2FSpelling|grammar flag checked]] need some attention to fix grammar and spelling mistakes. Often these changes require no knowledge of MediaWiki or web development domain expertise to help with, which makes them great starter issues to focus on. See [[WPD:Flags/Content_Grammar_Spelling|for more information]].
* '''Filling in missing compatibility information''' Some pages have compatibility tables with missing cells, which you can find on [http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace= this list]. Generally the information can be verified by comparing a couple of other sources  (such as http://caniuse.com/) and then inputting the values in the form. 
* '''Data not semantic''' it is a bad practice to use include code examples that are not semantic, for example which use presentational IDs (e.g. red-box; editors-note would be better) or use presentational elements (such as &lt;center&gt; or &lt;font&gt;) or which just use inappropriate tag structures (for example &lt;br&gt;&lt;br&gt; to create line breaks between paragraphs). Please fix such instances! 
* '''Biased content''' WPD is supposed to be a vendor neutral documentation site, so efforts need to be made to remove biased information. For example, have you found a section that talks about a feature as if it is only usable in Firefox or Chrome, or a section of code that could work across all browsers, but won't because it only uses one or two browsers' vendor prefixes? Please ammend these accordingly, or at least check the '''Biased voice''' flag in the edit form
* '''Setting appropriate flags''' If you press the edit button at the top of an article, you can check the different flag checkboxes at the top of the edit form to indicate what tasks need to be done on that article.
* '''Fixing broken links''' Broken links are fairly easy to spot on WPD - they should be highlighted in a [[albatross/my broken link example|bold red colour]]. Please repair any you find, or at least check the '''Broken Links''' flag.
* '''Add more useful links''' Feel free to add useful, relevant links to external resources to show more examples to illustrate a technique or technology.
* '''Add the correct code syntax coloring to code blocks''' See http://docs.webplatform.org/wiki/WPD:Style_Manual#Code_syntax_highlight_coloring for details of how.

===Half-hour tasks===
* '''New examples''' It is always useful to add more examples to illustrate techniques or show good use of technologies. Look for articles where the examples are thin on the group.
* '''Incomplete API documentation''' Some reference articles or incomplete or need documentation fleshing out.
* '''Merge duplicate articles''' Every so often there will be pages that substantially duplicate content and should be merged into one. For example, an article that originally came from MSDN might have lots of overlapping content with another article that came from HTML5Rocks. Look for articles on [[Special:SearchByProperty/High-2Dlevel-20issue/Merge-20Candidate|this list]], then look in the editorial note at the top to find the other article they've been proposed to merge into. Often it just requires looking carefully through both articles to maintain the best of both without duplication. See [[WPD:Flags/Merge_Candidate]] for more information.
* '''Fill in stubs''' There are a number of pages that are just stubs - article titles and locations with no content, usually as a result of someone thinking that it'd be a good idea to have an article on X or Y, but not having time right now, so setting a placeholder for later. Filling these in would be greatly appreciated.
* '''Fill in exercise questions''' Some articles have exercise questions listed at the bottom of them - you can fill in useful exercise questions, in the '''Manual sections: (raw other sections, including headers)''' box of the '''See also section''' in the edit form for tutorials, guides, etc.
* '''Add screenshots or supporting information''' many articles have broken screenshot links, or notes such as '''Note: add screenshot to show what this should look like.''' in them. Please help out by adding needed screenshots, or further examples or supporting information to illustrate techniques.

===Half-day tasks===
* '''Merge articles''' Some articles are marked with the '''Merge candidate'' flag, meaning that they should be merged with other articles, perhaps because they duplicate information, or because they would work better as single entity.
* '''Split articles''' - this is the same as above, except in the opposite direction.
* '''[[WPD:New_Page|Write new articles]]''' It is always great to see people writing new content. To find out what needs to be written, see the suggestion board. IF you are not sure if something needs to be written, ask about it first, at our [[http://talk.webplatform.org/forums/|Forums]] or in our IRC channel (irc.freenode.org, port 6667, room webplatform). If you haven't got time to write a complete article, it is still worth creating a new page with the beginnings of a new article on it.
* '''Suggest new topics for inclusion''' If you have a good idea for an article that could be included but don't have the time or skills to write it yourself, it is still worth putting the idea forward. You can do this in a variety of ways, for example my e-mailing ideas to XXXXXXXXXXXX, writing then down on the suggestion board at XXXXXXXXXXXX, and XXXXXXXXXXXXX.
* '''Improve internal documentation''' If it took you time to figure out how to do something, consider writing up a guide so people who others can follow in your footsteps later.
* '''Rewriting CC-BY-SA content''' While we have content on the site that is licensed under CC-BY-SA, ideally we would prefer to rewrite it so that it is more distributable and reusable. If you see articles licensed like this, feel free to rewrite the content. 

==Bugs!==

===Functional bugs===

If you find a bug on the site, please file a bug at [https://www.w3.org/Bugs/Public/enter_bug.cgi?product=webplatform.org Web Platform Docs Bugs]. We're using this bug tracker for two types of bugs:
* Site functionality bugs - errors, UI issues.
* Multiple page content problems - when an issue is related to entire groups of pages (otherwise, when an issue is related to a specific page, use the page flags).

For more guidance about filing the types of bugs, see the [[WPD:Bugzilla_Guidelines|Bugzilla Guidelines]].

===Content bugs===

If you find that content in an article is wrong or missing, consider adding a comment directly on the wiki page. To add a comment, hover over the relevant heading and an "Add comment" element appears. Select it to add your comment in the dialog box.

{{TODO | Fill in the more tactical guides for how to do some of the things on this list.}}