---
title: 'WPD:Semantic Forms'
uri: 'WPD:Semantic Forms'

---
### What are Semantic Forms?

Semantic Forms is a extension for MediaWiki that relies on Semantic MediaWiki to create form edits and define forms (which I will describe later). They appear over most pages on this wiki.

### Why isn't my page showing Semantic Forms?

Semantic Forms requires special Categories, defined by forms, that are used to query Semantics MediaWiki to allow the forms to exist. These Categories are written in the same style as typical MediaWiki syntax, such as [[Category:Markup Elements]].

The Categories must belong to one of the Forms, below is a compiled list of every form.

-   API Listings
-   API Objects
-   API Object Method
-   API Object Property
-   Basic Pages
-   CSS At Rule
-   CSS Functions
-   CSS Keywords
-   CSS Media Features
-   CSS Property
-   CSS Selector
-   Concept Pages
-   Constants
-   Data Type Pages
-   Events
-   Examples
-   Glossary
-   Glossary Items
-   Guides
-   JavaScript Operators
-   JavaScript Statements
-   Markup Attributes
-   Markup Elements
-   Markup Structures
-   Regex Metacharacters
-   Tutorials
-   data types
-   javascript global object
-   javascript methods

## That Special Dance

Here I will provide you simple step-by-step directions for allowing forms to exist on pages that do not have them.

1.  Identify if the page is missing the forms, you can view this by hovering over the edit button, if you only see "Edit" and not "Edit Source" then you know something is wrong.
2.  Push "Edit" and scroll down to the bottom of the page.
3.  Decide what Form the page fits under, most pages are going to fall under "Markup Elements" if you feel unsure, someone can correct it later, do not be afraid to add it even if you are unsure of the Form it belongs to.
4.  Add [[Category:FORMHERE]] on the last line of the page.
5.  Save the page, your Form might not show up instantly so try refreshing a few times if you don't see it right away.

*If it's still not showing up, nag someone on IRC to check it over for you.*
