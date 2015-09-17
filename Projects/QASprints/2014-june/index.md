---
title: 'Quality Assurance & Readiness Review (aka QA Sprint), June 2014'
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - 'WPD:Projects/QASprints/2014-june/WPD:Editors Guide/step 2 communicate with the online community/ko'
uri: 'WPD:Projects/QASprints/2014-june'

---
## Overview

As part of the progression of Webplatform.org to Beta stage (see the [Project Status](/WPD:Project_Status) or [Beta requirements](/WPD:Projects/Beta_Requirements) pages), we need to assign [readiness state properties](/Property:State) to every reference article. Once individual articles have markers of their quality, we can remove the "Web Platform Docs is in alpha" warning from every page.

As this will require a manual review of every page by experienced contributors, this is also a good time to do other quick and simple clean-up and quality assurance (QA) tasks that can only be done manually.

## UPDATE

We're in the final stretch, and to make sure everything gets done, I've broken the remaining articles into the bite-size lists, available on a separate sign-up page:

[<span style="font-size:larger;font-weight:bold">Sign up here</span>](/WPD:Projects/QASprints/2014-june/Sign-up)

**If you can work on a batch of articles, edit the sign-up page to put your name above the article list** (in the place that currently says "Your name here"). Please don't sign up until you're ready to sit down and start working! That way, whoever has the time can get the work done.

There are 80 batches, each with about 15-20 articles; I tried to split them at logical topic changes. The more you can do the better, but even if you only do one batch that's a big help. If you haven't already been working on the QA review, scroll down this page for information on what to do.

## Progress

Current Article Count:

-   Needs Review: 108 articles
-   Readiness Assessed: 4359 articles

(You can see the counts by readiness state, with links to all articles given that state, on the [Property:State](/Property:State) page.)

## Review Tasks

The following is a list of tasks which have been suggested for this review.

1.  Assign a readiness state. [More about readiness states](/WPD:Content/Readiness_Markers)
2.  ~~Add any details about readiness/what is required to the editorial notes box.~~
3.  For DOM method pages, assign index values to the parameter entries in order to get the correct syntax to display, as [described in this email post](http://lists.w3.org/Archives/Public/public-webplatform/2014May/0026.html).
4.  For pages without a default form, ensure that they have the basic `{{Page Title}}` template to make them searchable by name and path.
5.  ~~Confirm that the new compatibility tables are pulling in the correct data (Doug Schepers is going to give us more information about this once the import from MDN happens later this week).~~
6.  For almost-done pages, check that the W3C status icon is correct.
7.  ~~Ensure that every page has a summary section.~~

## Checklist

We have a lot of pages to get through, so this checklist has been designed to make the assessment quick and consistent. Follow the decision tree until you reach a readiness state. For some pages there are extra to-do lists, given below.

### Decision Tree for all pages

1.  Does the page have an editing form?
     NO
    :   -   follow basic templates to-do list.
        -   Readiness = NOT READY.

2.  **Is there a title at the top of the page?**
     NO
    :   -   follow basic templates to-do list, using the "Edit Source" button to get to the template code.
        -   continue with rest of checklist

3.  Is the page in a language other than English?
     YES
    :   leave Readiness = UNREVIEWED

4.  Is the page an obvious mistake or deletion candidate?
     YES
    :   -   add an explanation to the Details field (the text box under the Readiness State selector in the form), if it isn't already there
        -   delete all content from the page if it is particularly objectionable (It would be preferable if you don't delete the page even if you have permission, as this will throw off the search listings used to assign articles)
        -   Readiness = NOT READY

5.  Is this a DOM method page?
     YES
    :   -   follow DOM method to-do list.
        -   continue with the checklist.

6.  Is there substantial content on the page?
     *For REFERENCE DOCS:*
    :   Are there fewer than 3 of the following sections?
        -   Summary
        -   Values for info tables / syntax (if relevant)
        -   Written description / notes
        -   Examples
        -   Specifications
        -   Compatibility

     *For TUTORIAL/CONCEPT pages:*
    :   Is this obviously a stub page without much content?
     YES
    :   Readiness = NOT READY

7.  Is there a good summary?
     NO
    :   Readiness = IN PROGRESS

8.  Is there obvious bias towards one software (IE, Firefox)?
     YES
    :   Readiness = IN PROGRESS

9.  Is there any major content quality problem (spelling/grammar/formatting)?
     YES
    :   Readiness = IN PROGRESS

10. Is there still a lot of work to do?
     *For REFERENCE DOCS:*
    :   How many of the sections from (3) are missing?
     2-3 sections missing
    :   Readiness = IN PROGRESS
     1 section missing
    :   Readiness = ALMOST READY
     All sections included
    :   continue to next step
     *For TUTORIALS/CONCEPT pages:*
    :   Are there signs that this is half-done?
     YES
    :   Readiness = IN PROGRESS
     NO
    :   continue to next step

11. Is there a circular W3C icon on the page?
     YES
    :   Follow the Standardization Status to-do list.

12. Are there any other problems you can see at a glance?
    -   Could there obviously be better/more detailed explanations?
    -   Do you have any concerns about whether the content is accurate and up-to-date?

     YES
    :   Readiness = ALMOST READY
     NO, everything looks good
    :   Readiness = READY TO USE

### DOM Method To-Do List

1.  Does the syntax block have the words "see parameter list" insted of parameters?
     YES
    :   Open the editing form, and assign consecutive integer values (0,1,2,3...) to the "Argument Index" field for each parameter (in the order they are given in the page)

2.  Continue with the readiness checklist

### Standardization Status To-Do List

1.  In the edit form, ensure that the value for Standardization Status matches the most recent value in the Specifications table.
2.  Continue with the readiness checklist

### Basic Templates To-Do List

For pages that don't currently have a page template/default form (the "Edit" button opens a text box):

1.  Make sure that the first line in the code is the `{{Page Title}}` template.
2.  If the page currently has an h1 heading (surrounded by one '=' on either side), add it as a parameter to the template, like `{{Page Title | Text to use as title}}`; delete it from the main text and don't include the \`=\` in the template parameter value.
3.  Manually add the line `|State=Not Ready` to the `{{Flags}}` template (or one of the other state values, although I'm fairly certain any pages that don't have default forms will be "Not Ready").
    -   If the flags template isn't there, add it as `{{Flags|State=Not Ready}}`.
    -   If there is a Flags template, be sure not to delete any existing parameters.

The bare minimum will look like

       {{Page Title}}
       {{Flags|State=Not Ready}}

An example with a custom title and existing flag information will look like

       {{Page Title|multiply()}}
       {{Flags
       |State=Not Ready
       |High-level issues=Needs Topics, Missing Relevant Sections, Data Not Semantic, Unreviewed Import
       |Content=Incomplete, Not Neutral, Compatibility Incomplete, Examples Best Practices, Cleanup
       }}

## List of Volunteers

**Thanks for everyone who volunteered.** If anyone else wants to help, get in touch with one of the people on the list and ask them if they need help on their assigned articles.

~~**Please add your name to this list if you're willing to contribute.** The amount of work that can be done will depend on the number of people we have. There are 4400+ articles to review, it would be nice to have 20+ people tackling them; more people means fewer articles each. However, we are not trying to solicit brand new contributors for this, like in a DocSprint. Participants must be familiar with the mediawiki structure and understand the content quality expectations.~~

If you indicate topic areas you are comfortable with, I'll try to make most of your assigned articles in that domain, but there will be some overlap and I'm assigning things alphabetically (by file path) since that's how search results are ordered.

1.  shepazu (SVG, etc)
2.  renoirb
3.  jensimmons (CSS & HTML)
4.  julee
5.  eliot (Javascript)
6.  AmeliaBR (SVG, whatever's needed)
7.  eliezerb
8.  garbee
9.  frozenice (HTML & DOM)
10. Michaela (CSS & HTML)
11. Paulv
12. emerson (HTML/CSS/DOM)
13. brianjhong (HTML & CSS)
14. Rob\^\_\^ (any)
15. Hiroki
16. Roberto
17. caraya (late addition, may be able to help out with other people's article blocks)

## Article Blocks

<ins> See the update above for information about the new article blocks, or go to the [sign-up page](/WPD:Projects/QASprints/2014-june/Sign-up) to claim your block.</ins>

The following articles have been assigned to each volunteer by breaking the alphabetical search results into blocks of 275 articles each:

<dl>
<dt>
renoirb

-   [/WPD:Editors Guide/step 2 communicate with the online community/ko](/w/index.php?title=WPD:Projects/QASprints/2014-june/WPD:Editors_Guide/step_2_communicate_with_the_online_community/ko&action=edit&redlink=1) to [apis/filesystem/Entry/isDirectory](/apis/filesystem/Entry/isDirectory)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=0&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 235

</dt>
</dl>
<dl>
<dt>
garbee

-   [apis/filesystem/Entry/isFile](/apis/filesystem/Entry/isFile) to [apis/navigation timing/PerformanceTiming/domainLookupStart](/apis/navigation_timing/PerformanceTiming/domainLookupStart)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=275&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 288

</dt>
</dl>
<dl>
<dt>
eliot <ins>and Dave Gash</ins>

-   [apis/navigation timing/PerformanceTiming/fetchStart](/apis/navigation_timing/PerformanceTiming/fetchStart) to [apis/webrtc/RTCPeerConnection/icechange](/apis/webrtc/RTCPeerConnection/icechange)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=550&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 328

</dt>
</dl>
<dl>
<dt>
Paulv

-   [apis/webrtc/RTCPeerConnection/identityresult](/apis/webrtc/RTCPeerConnection/identityresult) to [concepts/ux/user experience design](/concepts/ux/user_experience_design)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=825&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 261

</dt>
</dl>
<dl>
<dt>
brianjhong

-   [concepts/ux/what does a good web page need](/concepts/ux/what_does_a_good_web_page_need) to [css/functions/translateY()](/css/functions/translateY())
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=1100&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 268

</dt>
</dl>
<dl>
<dt>
Michaela

-   [css/functions/translateZ()](/css/functions/translateZ()) to [css/properties/min-height](/css/properties/min-height)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=1375&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 278

</dt>
</dl>
<dl>
<dt>
jensimmons

-   [css/properties/min-width](/css/properties/min-width) to [dom/Document/close](/dom/Document/close)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=1650&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 257

</dt>
</dl>
<dl>
<dt>
emerson

-   [dom/Document/cookie](/dom/Document/cookie) to [dom/HTMLElement/clientLeft](/dom/HTMLElement/clientLeft)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=1925&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 271

</dt>
</dl>
<dl>
<dt>
~~frozenice~~ ~~*needs a volunteer*~~ AmeliaBR

-   [dom/HTMLElement/clientTop](/dom/HTMLElement/clientTop) to [dom/MouseEvent/layerX](/dom/MouseEvent/layerX)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=2200&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 269

</dt>
</dl>
<dl>
<dt>
Rob\^\_\^

-   [dom/MouseEvent/layerY](/dom/MouseEvent/layerY) to [dom/constants/DOM exception error codes](/dom/constants/DOM_exception_error_codes)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=2475&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 268

</dt>
</dl>
<dl>
<dt>
julee

-   [dom/constants/HTTP response headers](/dom/constants/HTTP_response_headers) to [html/attributes/valueType](/html/attributes/valueType)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=2751&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 255

</dt>
</dl>
<dl>
<dt>
Hiroki

-   [html/attributes/vcard name](/html/attributes/vcard_name) to [javascript/Date/constructor](/javascript/Date/constructor)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=3025&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 291

</dt>
</dl>
<dl>
<dt>
Roberto

-   [javascript/Date/getDate](/javascript/Date/getDate) to [javascript/operators/logical and](/javascript/operators/logical_and)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=3300&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 287

</dt>
</dl>
<dl>
<dt>
Eliezerb

-   [javascript/operators/logical not](/javascript/operators/logical_not) to [svg/methods/inverse](/svg/methods/inverse)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=3575&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 261

</dt>
</dl>
<dl>
<dt>
AmeliaBR

-   [svg/methods/item](/svg/methods/item) to [svg/properties/type (SVGTransform)](/svg/properties/type_(SVGTransform))
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=3850&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 275

</dt>
</dl>
<dl>
<dt>
shepazu

-   [svg/properties/unitType](/svg/properties/unitType) to [tutorials/workers basics](/tutorials/workers_basics)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=4125&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 245

</dt>
</dl>
<dl>
<dt>
caraya

-   [tutorials/working with objects in JavaScript](/tutorials/working_with_objects_in_JavaScript) to [xslt](/xslt)
-   [search page](//docs.webplatformstaging.org/w/index.php?title=Special:Ask&q=%5B%5BState%3A%3A%2B%5D%5D&offset=4400&limit=275&po=%3FState+%0A%3FState+Details)
-   \# completed: 11

</dt>
</dl>

## Plan of Attack

If you need help, [ask on IRC](/WPD:Community#Chat_with_us_on_IRC). If you can't complete your assigned tasks, send a note to the email list clearly indicating what range of articles still needs to be done, so that other people can take over.

## Timeline

-   ~~Comments and volunteers ASAP~~
-   Articles to be assigned Thursday June 12, 2014
-   Work completed ~~by July 1~~<ins> as soon as possible</ins>
