---
title: Most Wanted Tasks
notes:
  - "\nDeletion Candidate:   Outdated. We shouldn't be maintaining static lists like this with the new project management system in place.\n\n"
summary: 'A quick list of things that could be done around the site.'
tags:
  - Basic
  - Pages
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - 'WPD:Touch Pages'
uri: 'WPD:Most Wanted Tasks'

---
## Summary

A quick list of things that could be done around the site.

Here is a great quick list of specific things that could be done around the site. They are organized by the timeframe into which they fit according to the [Getting Started Guide](/WPD:Getting_Started). If you see something you want to take up, just do it and then please be neat and remove it from the list once you are finished.

Working on the Web Platform DocSprint in Mountain View (12/12/12)? Use this tracking spreadsheet: <http://goo.gl/NHJYT>

Thanks in advance for any task completed!

### Five-minute tasks

-   Import an article or two worth of compatibility information from CoreMob's published compatibility table: <https://docs.google.com/spreadsheet/ccc?key=0AuIhlK0fCwP4dEFPR1pUWHk1QVczcV9xbFAtX19CMXc#gid=0>

### Half-hour tasks

-   Help improve the JavaScript libraries page [bug 19834](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19834)

-   Help create the pages for server-side languages [bug 19391](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19391). Please remember that we are **not** fully documenting languages and that the content should not be opinionated.

-   Remove HTML4-specific content from some tutorials [bug 19719](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19719)

-   Clean the HTML tutorials [bug 19720](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19720)

### Half-day tasks

-   Help improve HTML attribute pages [bug 19500](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19500)

-   Help import some that failed during the initial import [bug 19314](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19314)

Note: These tasks are under half day tasks, but individual edits would be **far** faster. Don't think you need to take on everything. Just one or two edits in these areas is much appreciated.

-   Review merges from meta:html into html/elements [bug 19265](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19265)

-   Look for duplicate pages that are in the root page.

-   Put every page into a category except for the main page. Review the [Uncategorized Pages](/Special:UncategorizedPages) to see where this is needed.

-   Fix [lonely pages](http://docs.webplatform.org/w/index.php?title=Special:LonelyPages&limit=500&offset=0). These are typically the pages that need the most work at this time.

-   Move capitalized page paths that aren't following the style guide. Check [Category:CSS](/Category:CSS) for this.

-   Expand Topics on almost every page. Every page should have multiple topics.

### Brainstorming

-   Let's find a way to display CSS properties better [bug 19835](https://www.w3.org/Bugs/Public/show_bug.cgi?id=19835)

### Always going

-   Clean up pages that do not have needed templates.

## Other tasks to choose from

## Specific call to action: help clean up HTML element references

I would like to call upon anyone interested to help start going through the HTML element reference pages and surrounding structures. I have written a detailed reference to creating/editing reference articles, which will help. See [Reference articles](/WPD:Content/Reference_articles).

### Things that need to be done

-   All HTML element reference pages (except the ones mentioned below). See <http://docs.webplatform.org/wiki/html/elements> for a list!
-   Adding a table into the main content of each article to say what attributes they can take. See <http://docs.webplatform.org/wiki/html/attributes> for the list of links you can choose from!
-   Linking up each HTML element page to its relevant DOM Interface. See <http://docs.webplatform.org/wiki/dom> for the full list.

### Things already done

-   Changed link to HTML elements page on [main HTML page](/html) from <http://docs.webplatform.org/wiki/HTML/Elements> to <http://docs.webplatform.org/wiki/html/elements>.
-   Kept list of subpages at <http://docs.webplatform.org/wiki/html/elements>, but moved useful content from <http://docs.webplatform.org/wiki/HTML/Elements> on to it.
-   Updated all the links to individual pages on <http://docs.webplatform.org/wiki/html/elements> to be correct - all lower case, and changed Meta:HTML to html in URLs still pointing to the meta namespace.
-   The [Paragraph element](/html/elements/p) page has been pretty much completed: you can use this for a reference when completing other reference pages.
-   Help [Touch Pages](/w/index.php?title=WPD:Touch_Pages&action=edit&redlink=1) -- This is done 11/2/2012 EPG

### Pages being worked on

-   [Blockquote](/html/elements/blockquote) worked on by [Michelle Carlough](/User:Michistar)

-   [ul](/html/elements/ul) worked on by [Michelle Carlough](/User:Michistar)

#### Completed pages

-   [The paragraph element](/html/elements/p)

### [fr0zenice's](/User:Frozenice) notes on updating the paragraph element page

-   check what the editor before me had done: <http://docs.webplatform.org/w/index.php?title=html%2Felements%2Fp&diff=13355&oldid=9438>
    -   summary, remarks and some other stuff as it seems
-   I'm assuming the article has a formedit compatible template
    -   I used only the formedit, I think, as there was no need to fix anything in the raw source
-   remove extra brackets around links, external links use single square brackets and a space as seperator for the displayed title
    -   in this case the only one was the MSDN Link right at the bottom, maybe note that this field automatically wraps it's text in single square brackets
    -   there might also be erroneous links in the other fields, seen some in other articles

(Import Notes only stuff from here on, that means the text that's in that field in formedit, not raw stuff via edit source)

-   fixing anchor-links
    -   "[\#events Events]" -\> "[[\#Events|Events]]"
    -   this requires a heading like "====Events===="
-   collapsing multiple spaces / formatting line-breaks
    -   there were several places where 2-3 spaces were used instead of one, could be due to the import
    -   some table cells had more than one line, I formatted them like this: "Gets the namespace defined for the element.\<br\>This property is not supported for Metro style apps using JavaScript."
    -   that is totally open for discussion, of course, but the way it was took too much space, in my opinion
-   fixing tables (the largest part)
    -   "|" needs to be replaced with "{{!}}" where appropriate, that means:
    -   the start and end tag of a table become "{{{!}} ... {{!}}}" instead of "{| ... |}"
    -   row breaks become "{{!}}-" instead of "|-"
    -   cells become "{{!}} text" instead of "| text"
    -   pipes DO NOT need replacing in link-markups in tables, e.g. this is fine: "{{!}}Sets an [[dom/attributes|'''attribute''']] object node as part of the object."

## Specific call to action: help clean up DOM interface references

See <http://docs.webplatform.org/wiki/dom>

TO BE WRITTEN!

## Specific call to action: help clean up HTML attribute references

See <http://docs.webplatform.org/wiki/html/attributes>

TO BE WRITTEN!

## Specific call to action: help clean up tutorials/concepts!

I would like to call upon anyone who wants to help to start going through tutorials/concept articles, checking syntax, spelling, and grammar; making sure links and images work; and making improvements as you see fit.

You can find a detailed guide to handling tutorials and concept articles at [Tutorials and concept articles](/WPD:Content/Tutorials_and_concept_articles). Follow the different steps on this page, and make sure everything looks ok, to go through a tutorial/concept successfully. Let [[Chris Mills know](mailto:cmills@opera.com)] if you have any problems, want your work checked, or have any suggestions about improving the process.

## Notes

Things should be placed at a conservative "best-guess" time-frame and try to fit in with what is specified on the Getting Started Guide.

