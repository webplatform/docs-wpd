---
title: 'Content List'
uri: 'WPD:Content/Content List'

---
This is a list of all the existing content that has been donated to the webplatform.org project. I (CHRIS MILLS) have broken it into **batches**, of roughly the same size. For each batch, we need someone to take ownership of it, and then:

**See <https://docs.google.com/a/chromium.org/spreadsheet/ccc?key=0AkRs-89PKiZpdHBqN2poNnJjV1c0N1FCYlN3ZUtpZ3c#gid=0> for our work tracking sheet**

1.  As you do these steps, update them to make them more concrete so people who follow in your footsteps won't have to figure it all out from scratch.
2.  Make sure your pages are covered by the existing [page types](/WPD:Architecture#Page_Types) and doesn't require new ones. If you find ones you need, e-mail the list and propose it.
3.  Check the content structure for the subject you are currently dealing with. For anything that doesn't make sense, or needs adding, modifying or deleting, make changes as necessary.
4.  Fit existing articles into the content structure as well as you can and document your work. **TODO: where should you do this?**
5.  Think through the best migration strategy. Assume that writing each import script will take \~5 hours and need to be tweaked for every small difference it encounters. Is it faster to do your batch by hand or with an import script? That is, how diverse/messy is your content?
6.  Look at the list of page types [WPD:New\_Page](/WPD:New_Page) and figure out which page types will be appropriate for each article. Then, for each applicable page type, look at the template. What additional fields should be there? Look at [Template:CSS\_Property](/Template:CSS_Property) and others for inspiration.

**First week: stop here**

1.  Check that all the existing articles listed have been imported into the Wiki. Most of these will be done automatically using a batch import, but you may need to import some of them manually.
2.  Create new pages/stubs for articles that are yet to be written.
3.  Make sure all articles have the correct URLs and tags.
4.  Go through the list of items that must be added to each article before publishing (NEEDS FINISHING) and make sure they are added:
    1.  browser compatibility
    2.  flags
    3.  license
    4.   ??

5.  also need to proof/edit articles at some point

## Tutorials

### ARTICLE BATCH 1

**OWNER: CHRIS MILLS**

**Notes: There is some good material in this section, but a lot of it probably needs to be rejigged or trimmed, and a lot needs to be added. I don't think this section is as high a priority as the raw technology stuff, but we should still add stubs and leave it for the community to pick up, in the immediacy?**

-   Introductory text. We've already got [[Introduction to the Web Standards Curriculum](http://www.w3.org/community/webed/wiki/Introduction_to_the_Web_Standards_Curriculum)] (Opera), but this is hardly ideal, as it is specific for the web standards curriculum.

#### Introduction to the world of web standards

-   [The history of the Internet and the web, and the evolution of web standards](http://www.w3.org/community/webed/wiki/The_history_of_the_Web) (Opera)
-   [How does the Internet work](http://www.w3.org/community/webed/wiki/How_does_the_Internet_work)? (Opera)
-   [The web standards model - HTML CSS and JavaScript](http://www.w3.org/community/webed/wiki/The_web_standards_model_-_HTML_CSS_and_JavaScript) (Opera)

#### Web Design Concepts

-   Introduction to planning a web site
-   Scoping and user research
-   [Information Architecture - planning out a web site](http://www.w3.org/community/webed/wiki/Information_Architecture_-_planning_out_a_web_site) (Opera)
-   [What does a good web page need?](http://www.w3.org/community/webed/wiki/What_does_a_good_web_page_need) (Opera)
-   [Colour Theory](http://www.w3.org/community/webed/wiki/Colour_theory) (Opera)
-   [Building up a site wireframe](http://www.w3.org/community/webed/wiki/Building_up_a_site_wireframe) (Opera)
-   [Colour schemes and design mockups](http://www.w3.org/community/webed/wiki/Colour_schemes_and_design_mockups) (Opera)
-   [Typography on the Web](http://www.w3.org/community/webed/wiki/Typography_on_the_Web) (Opera)
-   Colour schemes and design theory
-   Mockups and prototypes
-   User experience design

### ARTICLE BATCH 2

**OWNER: CHRIS MILLS**

#### HTML beginnings

-   [The basics of HTML](http://www.w3.org/community/webed/wiki/The_basics_of_HTML) (Opera)
-   [Doctypes and markup styles](http://www.w3.org/community/webed/wiki/Doctypes_and_markup_styles) (Opera)
-   [The HTML \<head\> element](http://www.w3.org/community/webed/wiki/The_HTML_head_element) (Opera)
-   [More about the document \<head\>](http://www.w3.org/community/webed/wiki/More_about_the_document_head) (Opera)

#### The HTML body

-   [Marking up textual content in HTML](http://www.w3.org/community/webed/wiki/Marking_up_textual_content_in_HTML) (Opera)
-   [HTML Lists](http://www.w3.org/community/webed/wiki/HTML_lists) (Opera)
-   [Images in HTML](http://www.w3.org/community/webed/wiki/Images_in_HTML) (Opera)
-   [HTML links — let's build a web!](http://www.w3.org/community/webed/wiki/HTML_links_-_lets_build_a_web) (Opera)
-   [HTML tables](http://www.w3.org/community/webed/wiki/HTML_tables) (Opera)
-   [HTML forms - the basics](http://www.w3.org/community/webed/wiki/HTML_forms_-_the_basics) (Opera)
-   [HTML5 form additions](http://www.w3.org/community/webed/wiki/HTML5_form_additions) (Opera)
-   [HTML structural elements](http://www.w3.org/community/webed/wiki/HTML_structural_elements) (Opera)
-   [Lesser - known semantic elements](http://www.w3.org/community/webed/wiki/Lesser_-_known_semantic_elements) (Opera)
-   [Creating multiple pages with navigation menus](http://www.w3.org/community/webed/wiki/Creating_multiple_pages_with_navigation_menus) (Opera)
-   [Validating your HTML](http://www.w3.org/community/webed/wiki/Validating_your_HTML) (Opera)

### ARTICLE BATCH 3

**OWNER: Eliot**

**Notes: Someone with a good knowledge of accessibility should handle this section, preferably someone from WAI, like Shawn. The WAI should at least be consulted, as I believe they have done some work on working out a11y content for webplatform.org already.**

#### Accessibility

We've already got

1.  [Accessibility basics](http://www.w3.org/wiki/Accessibility_basics) (Opera)
2.  [Accessibility testing](http://www.w3.org/wiki/Accessibility_testing) (Opera)

But I THINK THIS NEEDS TO BE EXPANDED OUT TO SEVERAL ARTICLES, TO COVER DIFFERENT ASPECTS, SOMETHING LIKE:

1.  WRITING A PLAN FOR A11Y TESTING, INCLUDING USE OF REAL USER TESTING, CONFORMANCE CRITERIA, AUTOMATED TOOLS, AND GOOD OLD COMMON SENSE
2.  THE LEGAL SIDE OF THINGS, EXPLAINED IN DETAIL
3.  DECIPHERING WCAG, AND OTHER CONFORMANCE CRITERIA SUCH AS SECTION 508
4.  ACCESSIBILITY TOOLS, WHAT TO USE AND WHAT TO AVOID. HOW FAR WILL THESE GET YOU?
5.  REAL A11Y TESTING WITH REAL PEOPLE, HOW TO PUT TOGETHER FOCUS GROUPS, WHAT TO LOOK FOR HERE
6.  COMMON SENSE - SOLUTIONS FOR COMMON ACCESSIBILITY ISSUES - A ROADMAP FOR FIXING ISSUES. START WITH SEMANTIC HTML, THEN GO TO VIDEO AND AUDIO CONTENT, JAVASCRIPT, AJAX, ALTERNATIVES. }

#### Accessibility sources

-   [Accessibility](http://www.w3.org/WAI/yourWAI) (W3C)

### ARTICLE BATCH 4

**OWNER: CHRIS MILLS (Lea to help)**

#### CSS

-   [What is CSS](https://developer.mozilla.org/en/CSS/Getting_Started/What_is_CSS) (Mozilla)
-   [Why use CSS](https://developer.mozilla.org/en/CSS/Getting_Started/Why_use_CSS) (Mozilla)
-   [CSS basics](http://www.w3.org/community/webed/wiki/CSS_basics) (Opera)
-   [Selectors](https://developer.mozilla.org/en/CSS/Getting_Started/Selectors) (Mozilla)
-   [Advanced CSS selectors](http://www.w3.org/community/webed/wiki/Advanced_CSS_selectors) (Opera)
-   [Inheritance and cascade](http://www.w3.org/community/webed/wiki/Inheritance_and_cascade) (Opera)
-   [Cascading and inheritance](https://developer.mozilla.org/en/CSS/Getting_Started/Cascading_and_inheritance) (Mozilla)
-   [CSS text styling part 1](http://www.w3.org/community/webed/wiki/CSS_text_styling_part_1) (Opera)
-   [Text styles](https://developer.mozilla.org/en/CSS/Getting_Started/Text_styles) (Mozilla)
-   [Readable CSS](https://developer.mozilla.org/en/CSS/Getting_Started/Readable_CSS) (Mozilla)
-   CSS text styling, part 2: cover the nu school CSS3 stuff, like text-shadow, web fonts, hyphens, font-features, etc.
-   [The CSS layout model - boxes, borders, margins, padding](http://www.w3.org/community/webed/wiki/The_CSS_layout_model_-_boxes_borders_margins_padding) (Opera)
-   [Boxes](https://developer.mozilla.org/en/CSS/Getting_Started/Boxes) (Mozilla)
-   [Layout](https://developer.mozilla.org/en/CSS/Getting_Started/Layout) (Mozilla)
-   [Content](https://developer.mozilla.org/en/CSS/Getting_Started/Content) (Mozilla)
-   [CSS background images](http://www.w3.org/community/webed/wiki/CSS_background_images) - add multiple background images (Opera)
-   [Color](https://developer.mozilla.org/en/CSS/Getting_Started/Color) (Mozilla)
-   CSS gradients
-   Border-image
-   box-shadow

### ARTICLE BATCH 5

**OWNER: CHRIS MILLS (Lea to help)**

Notes: the owner of this batch should checkout the Adobe <http://beta.theexpressiveweb.com/> resource, to see what tutorials we can use from there. They are willing to donate those to the project/

#### CSS

-   [Styling lists and links](http://www.w3.org/community/webed/wiki/Styling_lists_and_links) (Opera)
-   [Lists](https://developer.mozilla.org/en/CSS/Getting_Started/Lists) (Mozilla)
-   [Styling tables](http://www.w3.org/community/webed/wiki/Styling_tables) (Opera)
-   [Tables](https://developer.mozilla.org/en/CSS/Getting_Started/Tables) (Mozilla)
-   [Styling forms](http://www.w3.org/community/webed/wiki/Styling_forms) (Opera)
-   [Floats and clearing](http://www.w3.org/community/webed/wiki/Floats_and_clearing) (Opera)
-   [CSS static and relative positioning](http://www.w3.org/community/webed/wiki/CSS_static_and_relative_positioning) (Opera)
-   [CSS absolute and fixed positioning](http://www.w3.org/community/webed/wiki/CSS_absolute_and_fixed_positioning) (Opera)
-   New CSS layout tools - flexbox, multi-col, background-clip, etc.
-   [Debugging CSS](http://www.w3.org/community/webed/wiki/index.php?title=Debugging_CSS) (Opera)
-   [CSS shorthand reference](http://www.w3.org/community/webed/wiki/CSS_shorthand_reference) (Opera)
-   [Media](https://developer.mozilla.org/en/CSS/Getting_Started/Media) (Mozilla)
-   [JavaScript and CSS](https://developer.mozilla.org/en/CSS/Getting_Started/JavaScript) (Mozilla)
-   [SVG and CSS](https://developer.mozilla.org/en/CSS/Getting_Started/SVG_graphics) (Mozilla)
-   [CSS and XML data](https://developer.mozilla.org/en/CSS/Getting_Started/XML_data) (Mozilla)

1.  NEW CHAPTER - CSS3 TRANSFORMS
2.  NEW CHAPTER - CSS3 TRANSITIONS
3.  NEW CHAPTER - CSS3 ANIMATIONS
4.  NEW CHAPTER - MEDIA QUERIES
5.  NEW CHAPTER - VIEWPORT
6.  NEW CHAPTER - CREATING AN ADAPTIVE DESIGN, USING MEDIA QUERIES, VIEWPORT, MULTI-COL, ETC.
7.  NEW CHAPTER - OBJECT FIT/OBJECT POSITION
8.  NEW CHAPTER - OPTIMIZING CSS (INCLUDE IDEAS FOR OPTIMIZING FOR MOBILE ETC.)
9.  NEW CHAPTER - State in CSS (Lea)

#### Sources

Adobe are willing to donate the great tutorials available at <http://beta.theexpressiveweb.com/>.

### ARTICLE BATCH 6

**OWNER: PAUL IRISH**

**Notes: This batch may seem like a lot, but it is in fact not that big - many of these are just stubs.**

#### JavaScript

The following is a list of proposed topics: there is still much that can be added here, but we wanted to get the initial idea posted and will continue to add/update.

1.  Hello world! in JavaScript
2.  Variables ([Values, variables, and literals](https://developer.mozilla.org/en/JavaScript/Guide/Values%2C_Variables%2C_and_Literals) - Mozilla)
    1.  Defining variables
    2.  Variable scope
    3.  Don’t pollute the global object
    4.  The single var ‘pattern’

3.  Basic operations
    1.  JavaScript data types
        1.  Floats and Integers
        2.  Booleans
        3.  Strings
        4.  Arrays
        5.  Objects ([Working with objects](https://developer.mozilla.org/en/JavaScript/Guide/Working_with_Objects) - Mozilla; [Objects in JavaScript](http://www.w3.org/wiki/Objects_in_JavaScript) - Opera - duplicate of batch 8)
        6.  [Predefined core objects](https://developer.mozilla.org/en/JavaScript/Guide/Predefined_Core_Objects) - Mozilla

    2.  [Statements](https://developer.mozilla.org/en/JavaScript/Guide/Statements) - Mozilla
    3.  Operators ([Expressions and operators](https://developer.mozilla.org/en/JavaScript/Guide/Expressions_and_Operators) - Mozilla)
    4.  Conditions
    5.  Loops

4.  Functions ([Functions](https://developer.mozilla.org/en/JavaScript/Guide/Functions) - Mozilla; [JavaScript functions](http://www.w3.org/wiki/JavaScript_functions) - Opera - duplicate of batch 8)
    1.  Declaring functions
    2.  Functions as Objects
    3.  Anonymous functions
    4.  Recursion
    5.  Context
    6.  The callback pattern

5.  Animation
    1.  Animation loops with setInterval
    2.  Other...
    3.  could use some of [JavaScript animation](http://www.w3.org/wiki/JavaScript_animation) (Opera)

6.  [Objects in JavaScript](http://www.w3.org/wiki/Objects_in_JavaScript) (Opera) - duplicate of batch 8
7.  [Details of the JavaScript object model](https://developer.mozilla.org/en/JavaScript/Guide/Details_of_the_Object_Model) (Mozilla)
8.  [Iterators and generators](https://developer.mozilla.org/en/JavaScript/Guide/Iterators_and_Generators) (Mozilla)
9.  [Traversing the DOM](http://www.w3.org/wiki/Traversing_the_DOM) (Opera) - duplicate of batch 8
10. [Creating and modifying HTML](http://www.w3.org/wiki/Creating_and_modifying_HTML) (Opera) - duplicate of batch 8
11. [Dynamic style - manipulating CSS with JavaScript](http://www.w3.org/wiki/Dynamic_style_-_manipulating_CSS_with_JavaScript) (Opera) - duplicate of batch 8
12. [Handling events with JavaScript](http://www.w3.org/wiki/Handling_events_with_JavaScript) (Opera) - duplicate of batch 8
    1.  Probably needs expanding

### ARTICLE BATCH 7

**OWNER: ELIOT GRAFF (maybe break off the Canvas pieces)**

**Notes: This batch may seem like a lot, but it is in fact not that big - many of these are just stubs.**

#### JavaScript

1.  User interaction
    1.  Clicking buttons
    2.  Interacting with mouse movements
    3.  Keyboard controls
    4.  touch events/gestures

2.  Tool Chest
    1.  Testing and Debugging
        1.  Tools for testing and debugging
        2.  Unit testing with QUnit
        3.  Cross browser JavaScript (Ouch ;))

    2.  Code Quality
        1.  JSLint and JSHint

    3.  Production ready
        1.  Google Closure Compiler

3.  Closures ([Closures](https://developer.mozilla.org/en/JavaScript/Guide/Closures) - Mozilla)
4.  JavaScript Libraries
    1.  jQuery
    2.  jQuery UI
    3.  Modernizr
    4.  Yepnope

5.  JavaScript Polyfils
    1.  When to use and when not to

6.  JavaScript on the Server
    1.  Nodejs - There is a lot to discuss here, we can break this down as we progress

7.  JavaScript for Mobile
    1.  The frameworks
    2.  Considerations for mobile JavaScript (This can have many ‘subdivisions’)
    3.  Best practices when writing for mobile

8.  JavaScript Gotcha’s
    1.  Why eval() is evil
    2.  Use === not ==
    3.  Don’t forget the ;
    4.  The problem with using typeof for testing for null
    5.  Avoid built in Object wrappers for primitives (This of course is for the most part)

9.  APIs
    1.  The basics of using an API
    2.  HTML5 APIs
        1.  MEDIA API
        2.  GEOLOCATION (YEAH, NOT HTML5, BUT HEY)
        3.  WEB WORKERS
        4.  WEB SOCKETS
        5.  APPCACHE
        6.  WEBSQL/INDEXEDDB
        7.  WEB STORAGE
        8.  CANVAS (SHOULD PROBABLY HAVE ITS OWN SECTION ENTIRELY)

[Canvas tutorial](https://developer.mozilla.org/en/Canvas_tutorial) (Mozilla)

1.  [Basic usage](https://developer.mozilla.org/en/Canvas_tutorial/Basic_usage)
2.  [Drawing shapes](https://developer.mozilla.org/en/Canvas_tutorial%3ADrawing_shapes)
3.  [Using images](https://developer.mozilla.org/en/Canvas_tutorial%3AUsing_images)
4.  [Applying styles and colors](https://developer.mozilla.org/en/Canvas_tutorial%3AApplying_styles_and_colors)
5.  [Transformations](https://developer.mozilla.org/en/Canvas_tutorial%3ATransformations)
6.  [Compositing](https://developer.mozilla.org/en/Canvas_tutorial%3ACompositing)
7.  [Basic animations](https://developer.mozilla.org/en/Canvas_tutorial%3ABasic_animations)
8.  [Optimizing canvas](https://developer.mozilla.org/en/Canvas_tutorial/Optimizing_canvas) (incomplete)

1.  1.  1.  HTML5 HISTORY API
        2.  DATASETS

2.  Sidebar: A Short History of JavaScript

1.  1.  Popular 3rd party APIs
        1.  Google Maps
        2.  Twitter
        3.  Flickr

2.  ECMAScript 5
    1.  Browser support
    2.  Cover additions...

### ARTICLE BATCH 8

**OWNER: CHRIS MILLS (to likely find someone from Opera)**

**Notes: Most of these will have been added in as part of one of the previous JS batches, but just give this a quick check to see if anything has been missed.**

#### JavaScript

Opera has the following available:

1.  [Programming - the real basics!](http://www.w3.org/wiki/Programming_-_the_real_basics) (Opera)
2.  [What can you do with JavaScript?](http://www.w3.org/wiki/What_can_you_do_with_JavaScript) (Opera)
3.  [Your first look at JavaScript](http://www.w3.org/wiki/Your_first_look_at_JavaScript) (Opera)
4.  [JavaScript best practices](http://www.w3.org/wiki/JavaScript_best_practices) (Opera)
5.  [The principles of unobtrusive JavaScript](http://www.w3.org/wiki/The_principles_of_unobtrusive_JavaScript) (Opera)
6.  [JavaScript functions](http://www.w3.org/wiki/JavaScript_functions) (Opera)
7.  [Objects in JavaScript](http://www.w3.org/wiki/Objects_in_JavaScript) (Opera)
8.  [Traversing the DOM](http://www.w3.org/wiki/Traversing_the_DOM) (Opera)
9.  [Creating and modifying HTML](http://www.w3.org/wiki/Creating_and_modifying_HTML) (Opera)
10. [Dynamic style - manipulating CSS with JavaScript](http://www.w3.org/wiki/Dynamic_style_-_manipulating_CSS_with_JavaScript) (Opera)
11. [Handling events with JavaScript](http://www.w3.org/wiki/Handling_events_with_JavaScript) (Opera)
12. [JavaScript animation](http://www.w3.org/wiki/JavaScript_animation) (Opera)
13. [Graceful degredation versus progressive enhancement](http://www.w3.org/wiki/Graceful_degredation_versus_progressive_enhancement) (Opera)
14. NEW CHAPTER - OPTIMIZING JAVASCRIPT (INCLUDE IDEAS FOR OPTIMIZING FOR MOBILE ETC.)
15. NEW CHAPTER - TOUCH EVENTS. THESE DEFINITELY NEED COVERAGE, AS THEY ARE GETTING VERY BIG THESE DAYS. TOUCH DEVICES ARE IMPORTANT.

### ARTICLE BATCH 9

**OWNER: JANET SWISHER**

**Notes: Some of these will have been added in as part of one of the previous JS batches, but give this a check to see if some of these have been missed, and think about where they might go in the JavaScript article structure.**

These are available from Mozilla:

-   [JavaScript Guide](https://developer.mozilla.org/en/JavaScript/Guide) (16 pages)
    -   [About this guide](https://developer.mozilla.org/en/JavaScript/Guide/About)
    -   [JavaScript overview](https://developer.mozilla.org/en/JavaScript/Guide/JavaScript_Overview)
    -   [Values, variables, and literals](https://developer.mozilla.org/en/JavaScript/Guide/Values%2C_Variables%2C_and_Literals)
    -   [Expressions and operators](https://developer.mozilla.org/en/JavaScript/Guide/Expressions_and_Operators)
    -   [Regular expressions](https://developer.mozilla.org/en/JavaScript/Guide/Regular_Expressions)
    -   [Statements](https://developer.mozilla.org/en/JavaScript/Guide/Statements)
    -   [Functions](https://developer.mozilla.org/en/JavaScript/Guide/Functions)
    -   [Working with objects](https://developer.mozilla.org/en/JavaScript/Guide/Working_with_Objects)
    -   [Predefined core objects](https://developer.mozilla.org/en/JavaScript/Guide/Predefined_Core_Objects)
    -   [Details of the object model](https://developer.mozilla.org/en/JavaScript/Guide/Details_of_the_Object_Model)
    -   [Inheritance revisited](https://developer.mozilla.org/en/JavaScript/Guide/Inheritance_Revisited)
    -   [Iterators and generators](https://developer.mozilla.org/en/JavaScript/Guide/Iterators_and_Generators)
    -   [Closures](https://developer.mozilla.org/en/JavaScript/Guide/Closures)
    -   [LiveConnect overview](https://developer.mozilla.org/en/JavaScript/Guide/LiveConnect_Overview)
    -   [Processing XML with E4X](https://developer.mozilla.org/En/E4X/Processing_XML_with_E4X)
-   [Getting started with JavaScript](https://developer.mozilla.org/en/JavaScript/Getting_Started) (1 page)
-   [A re-introduction to JavaScript](https://developer.mozilla.org/en/JavaScript/A_re-introduction_to_JavaScript) (1 page)
-   [Introduction to object-oriented JavaScript](https://developer.mozilla.org/en/Introduction_to_Object-Oriented_JavaScript) (1 page)

### ARTICLE BATCH 10

**OWNER: TOBIE LANGEL**

#### Facebook HTML5 API content

-   [HTML5 Showcase](https://developers.facebook.com/html5/showcase/)
-   [Building Web Apps](https://developers.facebook.com/html5/build/richui/)
-   [Building HTML5 Games](https://developers.facebook.com/html5/build/games/)
-   [Additional HTML5 Features](https://developers.facebook.com/html5/build/features/)
-   [Audio and Video](https://developers.facebook.com/html5/build/features/media/)
-   [Forms](https://developers.facebook.com/html5/build/features/forms/)
-   [Geolocation](https://developers.facebook.com/html5/build/features/location/)
-   [Make it Work Offline](https://developers.facebook.com/html5/build/features/offline/)
-   [Optimize for Mobile](https://developers.facebook.com/html5/build/features/mobile/)
-   [Testing Web Apps](https://developers.facebook.com/html5/test/)
-   [Distributing Web Apps](https://developers.facebook.com/html5/distribution/)

### ARTICLE BATCH 11

**OWNER: SCOTT ROWE**

#### Google HTML5 API content

*Donated from <http://www.html5rocks.com/en/tutorials/>*

-   [Quick Guide to Implementing the HTML5 Audio Tag](http://www.html5rocks.com/en/tutorials/audio/quick/)
-   [A Simple TODO list using HTML5 WebDatabases](http://www.html5rocks.com/en/tutorials/webdatabase/todo/)
-   [Using the Notifications API](http://www.html5rocks.com/en/tutorials/notifications/quick/)
-   [A Simple Trip Meter using the Geolocation API](http://www.html5rocks.com/en/tutorials/geolocation/trip_meter/)
-   [Best Practices for a Faster Web App with HTML5](http://www.html5rocks.com/en/tutorials/speed/quick/)
-   [Introduction to Chrome Developer Tools, Part One](http://www.html5rocks.com/en/tutorials/developertools/part1/) - Chrome only
-   [A Beginner's Guide to Using the Application Cache](http://www.html5rocks.com/en/tutorials/appcache/beginner/)
-   [Reading files in JavaScript using the File APIs](http://www.html5rocks.com/en/tutorials/file/dndfiles/)
-   [Practical Guide to Take Your TODO List Offline](http://www.html5rocks.com/en/tutorials/offline/takingappoffline/)
-   [The Basics of Web Workers](http://www.html5rocks.com/en/tutorials/workers/basics/)
-   [Auditing Your Web App For Speed](http://www.html5rocks.com/en/tutorials/developertools/auditpanel/)
-   ["Offline": What does it mean and why should I care?](http://www.html5rocks.com/en/tutorials/offline/whats-offline/)
-   [Quick guide to webfonts via @font-face](http://www.html5rocks.com/en/tutorials/webfonts/quick/)
-   [HTML5 Video](http://www.html5rocks.com/en/tutorials/video/basics/)
-   [3D and CSS](http://www.html5rocks.com/en/tutorials/3d/css/)
-   [Case Study: Drag and Drop Download in Chrome](http://www.html5rocks.com/en/tutorials/casestudies/box_dnd_download.html)
-   [Case Study: HTML5 in deviantART muro](http://www.html5rocks.com/en/tutorials/casestudies/html5_in_deviantart_muro.html) - Schmarketing?
-   [Native HTML5 Drag and Drop](http://www.html5rocks.com/en/tutorials/dnd/basics/)
-   [Client-Side Storage](http://www.html5rocks.com/en/tutorials/offline/storage/)
-   [Quick hits with the Flexible Box Model](http://www.html5rocks.com/en/tutorials/flexbox/quick/) - Out of date

### ARTICLE BATCH 12

**OWNER: SCOTT ROWE**

#### Google HTML5 API content (donated from <http://www.html5rocks.com/en/tutorials/>)

-   [Introducing WebSockets: Bringing Sockets to the Web](http://www.html5rocks.com/en/tutorials/websockets/basics/)
-   [Stream Updates with Server-Sent Events](http://www.html5rocks.com/en/tutorials/eventsource/basics/)
-   [Case Study: Getting Entangled with HTML5 Canvas](http://www.html5rocks.com/en/tutorials/casestudies/entanglement.html)
-   [A Simple TODO list using HTML5 IndexedDB](http://www.html5rocks.com/en/tutorials/indexeddb/todo/) - Out of date
-   [Exploring the FileSystem APIs](http://www.html5rocks.com/en/tutorials/file/filesystem/)
-   [Case Study: Page Flip Effect from 20thingsilearned.com](http://www.html5rocks.com/en/tutorials/casestudies/20things_pageflip.html)
-   [Case Study: HTML5 MathBoard](http://www.html5rocks.com/en/tutorials/casestudies/mathboard.html)
-   [No Tears Guide to HTML5 Games](http://www.html5rocks.com/en/tutorials/canvas/notearsgame/)
-   [Case Study: Onslaught! Arena](http://www.html5rocks.com/en/tutorials/casestudies/onslaught.html)
-   [Improving the Performance of your HTML5 App](http://www.html5rocks.com/en/tutorials/speed/html5/)
-   [Typographic effects in canvas](http://www.html5rocks.com/en/tutorials/canvas/texteffects/)
-   ["Mobifying" Your HTML5 Site](http://www.html5rocks.com/en/mobile/mobifying.html)
-   [Case Study: Converting Wordico from Flash to HTML5](http://www.html5rocks.com/en/tutorials/casestudies/wordico.html)
-   [Case Study: Real-time Updates in Stream Congress](http://www.html5rocks.com/tutorials/casestudies/sunlight_streamcongress.html)
-   [Multi-touch Web Development](http://www.html5rocks.com/mobile/touch.html)
-   [This End Up: Using Device Orientation](http://www.html5rocks.com/tutorials/device/orientation/)
-   [Chrome Experiments Demo Harness](http://www.html5rocks.com/tutorials/webgl/demoloop/)
-   [Image Filters with Canvas](http://www.html5rocks.com/tutorials/canvas/imagefilters/)
-   [New Tricks in XMLHttpRequest2](http://www.html5rocks.com/tutorials/file/xhr2/)
-   [Rendering HTML5 in older browsers with Google Chrome Frame](http://www.html5rocks.com/tutorials/google-chrome-frame/)

### ARTICLE BATCH 13

**OWNER: SCOTT ROWE**

#### Google HTML5 API content (donated from <http://www.html5rocks.com/en/tutorials/>)

-   [Working Off the Grid with HTML5 Offline](http://www.html5rocks.com/mobile/workingoffthegrid.html)
-   [An Introduction to Shaders](http://www.html5rocks.com/tutorials/webgl/shaders/)
-   [Getting Started with Three.js](http://www.html5rocks.com/tutorials/three/intro/)
-   [Making Forms Fabulous with HTML5](http://www.html5rocks.com/tutorials/forms/html5forms/)
-   [HTML5 vs Native: The Mobile App Debate](http://www.html5rocks.com/mobile/nativedebate.html)
-   [Feature, Browser, and Form Factor Detection: It's Good for the Environment](http://www.html5rocks.com/tutorials/detection/index.html)
-   [Simple Asset Management for HTML5 Games](http://www.html5rocks.com/tutorials/games/assetmanager/)
-   [Auto-Resizing HTML5 Games](http://www.html5rocks.com/tutorials/casestudies/gopherwoord-studios-resizing-html5-games.html)
-   [How Browsers Work: Behind the scenes of modern web browsers](http://www.html5rocks.com/tutorials/internals/howbrowserswork/)
-   [Integrating Canvas into your Web App](http://www.html5rocks.com/tutorials/canvas/integrating/)
-   [Improving HTML5 Canvas Performance](http://www.html5rocks.com/tutorials/canvas/performance/)
-   [Measuring Page Load Speed with Navigation Timing](http://www.html5rocks.com/tutorials/webperformance/basics/)
-   [Introduction to Raphaël.js](http://www.html5rocks.com/tutorials/raphael/intro/)
-   [HTML5 Techniques for Optimizing Mobile Performance](http://www.html5rocks.com/mobile/optimization-and-performance.html)
-   [Getting Started with Web Audio API](http://www.html5rocks.com/tutorials/webaudio/intro/)
-   [The Synchronous FileSystem API for Workers](http://www.html5rocks.com/tutorials/file/filesystem-sync/)
-   [Using CORS](http://www.html5rocks.com/tutorials/cors/)
-   [Migrating your WebSQL DB to IndexedDB](http://www.html5rocks.com/tutorials/webdatabase/websql-indexeddb/)
-   [Case Study: Building the Stanisław Lem Google doodle](http://www.html5rocks.com/tutorials/doodles/lem/)

### ARTICLE BATCH 14

**OWNER: WAI SETO**

**Notes: This section will be mostly stubs, and we really need someone to think carefully about what structure our mobile and device material should have.**

#### Mobile and devices

We already have

-   [Mobile 1: Introduction to mobile web](http://www.w3.org/community/webed/wiki/Introduction_to_mobile_web) (Opera)

And the following available from Nokia:

Reusable mobile templates or components

-   [Templates for smartphones](http://www.developer.nokia.com/Develop/Web/Mobile_web_browsing/Web_templates/Templates_for_smartphones/)
-   [Templates for mobile phones](http://www.developer.nokia.com/Develop/Web/Mobile_web_browsing/Web_templates/Templates_for_mobile_phones/)
-   [Mobile Web Components](http://projects.developer.nokia.com/mobile_web_components)

Mobile web development shortcuts articles

-   [Device and browser detection](http://www.developer.nokia.com/Resources/Library/Web/nokia-browsers/common-elements-of-nokia-browsers/device-and-browser-detection.html#toc_Clientsidedetection)
-   [Mobile JavaScript best practies](http://www.developer.nokia.com/Resources/Library/Web/nokia-browsers/common-elements-of-nokia-browsers/mobile-javascript-best-practices.html)

-   [Mobile-optimised CMS plug-ins](http://www.developer.nokia.com/Resources/Library/Web/nokia-browsers/common-elements-of-nokia-browsers/mobile-optimised-cms-plug-ins.html)

(Some don't seen to fit WPD anymore after revewing our content style/types)

PROPOSED STRUCTURE

1.  [[About the mobile web](http://webplatform.org/docs/concepts/About_mobile_web)] Mobile beginnings: An introduction to the mobile web (include history of mobiles, how mobile networks work, what the hardware looks like, what the software looks like)
2.  [[Learning what mobile devices look like](http://webplatform.org/docs/Learning_what_mobile_devices_look_like)] What do the devices look like? (a fairly detailed reference showing the types of devices you are likely to need to support when building cross device adaptive apps. Include data such as screen resolution, espect ratio and dpi of the different devices. This kid of reference material will be very useful to developers.)
3.  [[Learning mobile constraints and advantages](http://webplatform.org/docs/Learning_mobile_constraints_and_advantages)] Mobile constraints and advantages (what are the specific constraints you need to work around for mobile and alternative browsing devices? What are the advantages, eg the context specific technologies you can take advantage of?)
4.  [[About mobile friendly web design and development overview](http://webplatform.org/docs/concepts/About_mobile_friendly_web_design_and_development_overview)] Mobile friendly: web design and development Overview (start with a basis of semantic HTML, accessibility best practices are Making an app or site mobile friendly - do you create a different site, or do you adapt your existing site for mobile? A brief introduction to Adaptive design - graceful degradation, progressive enhancement, using media queries and viewport to adapt layout, using feature detection to server appropriate content and services, geolocation, multimedia, offline apps, don't use browser sniffing!) A lot of this will be covered elsewhere.
5.  [[Implementing mobile browser feature detection](http://webplatform.org/docs/Implementing_mobile_browser_feature_detecion)] Feature detection, polyfilling, graceful degredation, etc. An article on this would be good, maybe something which showed how to detect for all different features. Kind of like Mark Pilgrims' No bullshit guide to detecting everything. Before he took it all down.
6.  [[Testing with mobile browsers](http://webplatform.org/docs/Testing_with_mobile_browsers)] CoreMob specs, Ringmark

OTHER THINGS TO ADD ELSEWHERE IN THE MATERIAL

1.  WE SHOULD WRITE AN ARTICLE TITLED "ONE WEB, MANY DEVICES", PLACED INSIDE <http://www.w3.org/wiki/Web_Standards_Curriculum#Introduction_to_the_world_of_web_standards>
2.  WE SHOULD ALSO SAY SOMETHING ABOUT SEMANTICS AND DIVERSE DEVICES IN <http://www.w3.org/wiki/The_web_standards_model_-_HTML_CSS_and_JavaScript>

### ARTICLE BATCH 15

**OWNER: DOUG SCHEPERS (Doug to communicate with Jeremie, and SVG WG)**

#### SVG

Source of inspiration :

-   <http://www.w3.org/Graphics/SVG/IG/resources/svgprimer.html>
-   <https://developer.mozilla.org/en/SVG/Tutorial>

##### SVG BASICS

1.  *History and usage* : As for HTML, it could be good to start by giving some context: What is it, Where does it come, What is it made for, How is it different than HTML? ([Introduction](https://developer.mozilla.org/en/SVG/Tutorial/Introduction) from Mozilla)
2.  *Syntax and deployment* : This part would introduce the basic syntax, the concept of viewport and absolute positioning and finally how to embed an SVG document inside other language (basically HTML and CSS). ([Simple example, basic properties, file types](https://developer.mozilla.org/en/SVG/Tutorial/Getting_Started) from Mozilla)
3.  *Basic shapes* : This part will be dedicated to the basic shapes available in SVG ([Basic Shapes](https://developer.mozilla.org/en/SVG/Tutorial/Basic_Shapes) from Mozilla)
4.  *Position and transformation* : To go deeper inside the viewport thing and to explain the role of the transformations. ([Positions](https://developer.mozilla.org/en/SVG/Tutorial/Positions) and [Basic transformations](https://developer.mozilla.org/en/SVG/Tutorial/Basic_Transformations) from Mozilla)
5.  *Using text in SVG* ([Texts](https://developer.mozilla.org/en/SVG/Tutorial/Texts) from Mozilla)
6.  *Styling SVG* : This is where we would detailed how to use presentation attributes and their CSS counterpart.
7.  *Scripting SVG* : Where we could introduce the SVG DOM API.

#### Part 2 : SVG ADVANCED

1.  *How to build Pathes* : To dig into the syntax of the d attribute on path elements ([Paths](https://developer.mozilla.org/en/SVG/Tutorial/Paths) from Mozilla)
2.  *[Fills and strokes](https://developer.mozilla.org/en/SVG/Tutorial/Fills_and_Strokes)* (Mozilla)
3.  *Animating the web with SVG Animations* : How to use SVG Animations
4.  *SVG Filters* : This would be an introduction to filters but each filters could have it's own article (Filters a really hard things) ([Filter effects](https://developer.mozilla.org/en/SVG/Tutorial/Filter_effects) -- incomplete, from Mozilla)
5.  *[Clipping and Masking](https://developer.mozilla.org/en/SVG/Tutorial/Clipping_and_masking)* (Mozilla)
6.  *[Patterns](https://developer.mozilla.org/en/SVG/Tutorial/Patterns)* (Mozilla)
7.  *[Gradients](https://developer.mozilla.org/en/SVG/Tutorial/Gradients)* (Mozilla)
8.  *Dealing with the external* : This part would be dedicated to the foreignObject element but also to links and images elements. ([Other content in SVG](https://developer.mozilla.org/en/SVG/Tutorial/Other_content_in_SVG) from Mozilla)
9.  *[SVG fonts](https://developer.mozilla.org/en/SVG/Tutorial/SVG_Fonts)* (Mozilla)
10. *[SVG image element](https://developer.mozilla.org/en/SVG/Tutorial/SVG_Image_Tag)* (Mozilla)

#### Other content sources

Ex-Opera articles

1.  [SVG Primer](http://www.w3.org/wiki/SVG_Primer) (written by David Storey, but unused)
2.  [SVG Links](http://www.w3.org/wiki/SVG_Links) (written by David Storey, but unused)

### ARTICLE BATCH 16

**OWNER: DOUG SCHEPERS (Doug to communicate with Jeremie, and SVG WG)**

**Notes: This is basically just a list of demos, but we should go through them to see where we can use these.**

 SVG WOW (<http://svg-wow.org/>) Demos:

-   [Animated Lyrics](http://svg-wow.org//blog/2009/10/04/animated-lyrics)
-   [Chiseled](http://svg-wow.org//blog/2009/10/04/chiseled)
-   [Mustache](http://svg-wow.org//blog/2009/10/04/mustache)
-   [Photo Album](http://svg-wow.org//blog/2009/10/04/photo-album)
-   [Ripple](http://svg-wow.org//blog/2009/10/04/ripple)
-   [Twirl](http://svg-wow.org//blog/2009/10/04/twirl)
-   [Video](http://svg-wow.org//blog/2009/10/04/video)
-   [Alternate Stylesheets](http://svg-wow.org//blog/2010/08/14/alternate-stylesheets)
-   [Camera](http://svg-wow.org//blog/2010/08/14/camera)
-   [Bokeh](http://svg-wow.org//blog/2010/08/22/bokeh)
-   [Pointilizer](http://svg-wow.org//blog/2010/08/22/pointilizer)
-   [Graffitis](http://svg-wow.org//blog/2010/09/06/graffitis)
-   [picture-shuffle](http://svg-wow.org//blog/2010/09/18/picture-shuffle)
-   [Text Effects](http://svg-wow.org//blog/2010/09/25/text-effects)
-   [Gandhi Quotes](http://svg-wow.org//blog/2010/10/05/gandhi-quotes)
-   [Rotozoom video](http://svg-wow.org//blog/2011/03/28/rotozoom-video)

### ARTICLE BATCH 17

**OWNER: PETER LUBBERS**

#### Supplementary articles

-   [Getting your content online](http://www.w3.org/wiki/Getting_your_content_online) (Opera)
-   [Common HTML entities used for typography](http://www.w3.org/wiki/Common_HTML_entities_used_for_typography) (Opera)
-   [The Opera Web Standards Curriculum glossary](http://www.w3.org/wiki/The_web_standards_curriculum_glossary) (Opera) This is incomplete, and will be added to as time goes by.

### Internet Basics

-   HTTP status codes
-   MIME Types
-   TCP/IP
    -   other protocols like UDP (see <http://www.skullbox.net/tcpudp.php>)
    -   packet diagrams
    -   see <http://www.xoc.net/works/jigsaw/internetbasics.asp>
-   SPDY
-   ARD
-   NAT
-   Network topology
-   Domain names and DNS
-   How Web fits on top of Internet
-   Basic security
-   History of Internet and Web

## References

### ARTICLE BATCH 18

**OWNER: ELIOT GRAFF**

#### HTML

-   [HTML Reference](http://msdn.microsoft.com/en-US/library/ie/hh772960.aspx) (Microsoft)

-   [HTML Reference](http://www.w3.org/community/webed/wiki/HTML) (W3C)

### ARTICLE BATCH 19

**OWNER: ELIOT GRAFF**

#### CSS

-   [CSS Reference](http://msdn.microsoft.com/en-us/library/ie/ms531209(v=vs.85).aspx) (Microsoft)

### ARTICLE BATCH 20

**OWNER: ELIOT GRAFF**

#### CSS

-   [CSS Reference](http://www.w3.org/community/webed/wiki/CSS) (W3C)

### ARTICLE BATCH 21

**OWNER: ELIOT GRAFF**

#### Canvas

-   [CANVAS reference (element and 2D API)](http://msdn.microsoft.com/en-us/library/ie/hh771733(v=vs.85).aspx) (Microsoft)

### ARTICLE BATCH 22

**OWNER: ELIOT GRAFF**

#### SVG

-   [SVG reference](http://msdn.microsoft.com/en-us/library/ie/ff971903(v=vs.85).aspx) (Microsoft)

### ARTICLE BATCH 23

**OWNER: ELIOT GRAFF**

#### DOM Transversal

-   [DOM transversal reference](http://msdn.microsoft.com/en-us/library/ie/hh772120(v=vs.85).aspx) (Microsoft)

### ARTICLE BATCH 24

**OWNER: ELIOT GRAFF**

#### DOM

-   [DOM General reference](http://msdn.microsoft.com/en-us/library/ie/hh771916(v=vs.85).aspx) (Microsoft)

### ARTICLE BATCH 25

**OWNER: ELIOT GRAFF**

#### DOM Events

-   [DOM Events](http://msdn.microsoft.com/en-us/library/ie/hh771866(v=vs.85).aspx) (Microsoft)

### ARTICLE BATCH 25A

**OWNER: ELIOT GRAFF**

#### ARIA

-   [ARIA reference](http://msdn.microsoft.com/en-us/library/ie/hh801958(v=vs.85).aspx) (Microsoft)

### ARTICLE BATCH 25B

**OWNER: ELIOT GRAFF**

#### Web Apps

-   [AppCache reference](http://msdn.microsoft.com/en-us/library/ie/hh673545(v=vs.85).aspx) (Microsoft)
-   [File API reference](http://msdn.microsoft.com/en-us/library/ie/hh772315(v=vs.85).aspx) (Microsoft)
-   [Geolocation reference](http://msdn.microsoft.com/en-us/library/ie/hh772290(v=vs.85).aspx) (Microsoft)
-   [IndexedDB reference](http://msdn.microsoft.com/en-us/library/ie/hh772651(v=vs.85).aspx) (Microsoft)
-   [Messaging reference](http://msdn.microsoft.com/en-us/library/ie/hh781494(v=vs.85).aspx) (Microsoft)
-   [Timing reference](http://msdn.microsoft.com/en-us/library/ie/hh772738(v=vs.85).aspx) (Microsoft)
-   [Web workers reference](http://msdn.microsoft.com/en-us/library/ie/hh772807(v=vs.85).aspx) (Microsoft)
-   [Websocket reference](http://msdn.microsoft.com/en-us/library/ie/hh772770(v=vs.85).aspx) (Microsoft)
-   [Web Storage reference](http://msdn.microsoft.com/en-US/library/ie/hh781511.aspx) (Microsoft)
-   [XHR reference](http://msdn.microsoft.com/en-us/library/ie/hh772834(v=vs.85).aspx) (Microsoft)

### ARTICLE BATCH 25C

**OWNER: ELIOT GRAFF**

#### Media (Audio and Video)

-   [Media reference](http://msdn.microsoft.com/en-us/library/ie/hh772500(v=vs.85).aspx) (Microsoft)

## Curriculum structures

Seed content taken from [WaSP InterACT Curriculum structures](http://interact.webstandards.org/curriculum/). Most recent versions kept at [Overview of InterACT curriculum articles](http://www.w3.org/community/webed/wiki/Interact_Curriculum)

### ARTICLE BATCH 26

**OWNER: DOUG SCHEPERS**

#### Basics and "soft" skills

-   [Internet Fundamentals](http://www.w3.org/community/webed/wiki/Interact/Internet_Fundamentals)
-   [Digital Design Production](http://www.w3.org/community/webed/wiki/Interact/Digital_Design_Production)
-   [Writing for the Web](http://www.w3.org/community/webed/wiki/Interact/Writing_for_the_Web)
-   [Project Management](http://www.w3.org/community/webed/wiki/Interact/Project_Management)
-   [Professional Development](http://www.w3.org/community/webed/wiki/Interact/Professional_Development)
-   [Independent Study](http://www.w3.org/community/webed/wiki/Interact/Independent_Study)
-   [Internship](http://www.w3.org/community/webed/wiki/Interact/Internship)

### ARTICLE BATCH 27

**OWNER: DOUG SCHEPERS**

#### Web design

-   [Web Design 1](http://www.w3.org/community/webed/wiki/Interact/Web_Design_1)
-   [Web Design 2](http://www.w3.org/community/webed/wiki/Interact/Web_Design_2)
-   [Accessibility](http://www.w3.org/community/webed/wiki/Interact/Accessibility)
-   [Usability 1](http://www.w3.org/community/webed/wiki/Interact/Usability_1)
-   [Findability](http://www.w3.org/community/webed/wiki/Interact/Findability)
-   [Interaction Design 1](http://www.w3.org/community/webed/wiki/Interact/Interaction_Design_1)
-   [Prototyping](http://www.w3.org/community/webed/wiki/Interact/Prototyping)

### ARTICLE BATCH 28

**OWNER: DOUG SCHEPERS**

#### Web development

-   [DOM Scripting 1](http://www.w3.org/community/webed/wiki/Interact/DOM_Scripting_1)
-   [Server-side Scripting 1](http://www.w3.org/community/webed/wiki/Interact/Server-Side_Scripting_1)

## Miscellaneous - not sure what to do with these yet

### ARTICLE BATCH 29

**OWNER: DOM (Doug to followup with Dom)**

Notes: low priority, but it might be nice to get someone to investigate these and see what we should do with them, where we should put them, etc.

-   [Internationalization](http://www.w3.org/International/getting-started/) (W3C)
-   [Tutorials](http://www.w3.org/2002/03/tutorials) (W3C)
-   [Cheatsheet](http://www.w3.org/2009/cheatsheet/) (W3C)
-   [Podcasts and Videos](http://www.w3.org/participate/podcastsvideo) (W3C)
-   [Primers](http://www.w3.org/TR/) (W3C)
