---
title: JavaScript project proposal
uri: 'WPD:Projects/javascript'

---
**NOTE** Project is completed, participate in improving the [javascript](/javascript) documentation!

JavaScript is a proposed Web Platform Docs project to document the implementation of the ECMAScript standard in web browsers, focusing on the language itself rather than how it is coupled inside a browser to dom objects, events, HTML5 APIs, or CSS style.

## Project characteristics

 Version
:   The version of JavaScript documented will initially be based on the ECMA-262 edition 5.1 [standard of June 2011](http://www.ecma-international.org/publications/standards/Ecma-262.htm), since it has the [greatest browser conformance](https://en.wikipedia.org/wiki/ECMAScript#Conformance_tests).

 Location
:   All JavaScript reference material will exist relative to the [javascript](/javascript) parent page.

## Page structure

An initial bulk page import is planned based on pages [donated by Microsoft](http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0238.html), and reformatted. The import work is an [ongoing subproject](http://project.webplatform.org/msdnjs). The initial page structure will be a set of top-level pages shown below, each one having second-level subpages that capture the logical structure and for efficient bread crumbs page navigation.

### Top-level pages

|Top-level page|Subpages|
|:-------------|:-------|
|Objects|336 pages: built-in objects (Array, ArrayBuffer, Boolean, etc) and other special objects (arguments, Function, Global, Object).|
|Constants|1 page listing constants found within Math, Global, and Number like (E, Infinity, MIN\_VALUE)|
|Properties|1 page listing properties found within arguments, RegExp, Function, Error, etc.|
|Functions|1 page listing functions found within Math, Global, Object, String, etc.|
|Methods|1 page listing methods found within String, Function, Enumerator, Array, etc.|
|Operators|39 pages: Addition Assignment, Addition, Assignment, Bitwise AND Assignment, etc.|
|Statements|22 pages:break, Comment, continue, do while, etc.|
|Errors|2 pages: Run time, Syntax|
|Reserved Words|1 page listing words unable to be used as identifiers.|

### Third-level subpages

Third-level subpages will exist for each property, function (not requiring an object), method (requiring an object), and constant. For example, under the Objects top-level page, we have second-level pages Array and Math. These in turn will have the following third-level subpages:

-   Array's three properties: constructor, length, and prototype.
-   Array's one function: Array.isArray.
-   Array's many methods: concat, every, filter, forEach, indexOf, join, lastIndexOf, map, pop, push, reduce, reduceRight, reverse, shift, slice, some, sort, splice, toString, unshift, and valueOf.
-   Math's constant Math.E.

Putting it all together, an example URL path for the Array constructor would then be: "Objects/Array/constructor Property". To see more examples, the current bulk import page names can be [found here](https://github.com/maxpolk/msdn-js-conversion/blob/master/round-alice/upload-mapping.wiki).

Notice the rules for third-level pages under Object:

-   property pages have a "Property" suffix, eg. Objects/Array/length **Property**
-   function pages have a "Function" suffix, eg. Objects/Array/Array.isArray **Function**
-   method pages have a "Method" suffix, eg. Objects/Array/concat **Method**
-   constant pages have a "Constant" suffix, eg. Objects/Float32Array/BYTES\_PER\_ELEMENT **Constant**

Notice the rules for second-level pages under Operators:

-   Operators are spelled out as words, eg. Operators/Addition Assignment for the `+=` operator
-   Logical or bitwise operators are capitalized, eg. Operators/Logical AND

### Path rewriting proposal

-   Rename the "Objects" level to "global" for greater accuracy and correctness -
    -   javascript/global/Array
    -   javascript/global/Object
    -   javascript/global/parseInt

-   Drop the suffixes -
    -   javascript/global/Array/length Property --\> javascript/global/Array/length
    -   javascript/global/Array/forEach Method --\> javascript/global/Array/forEach

-   Static methods should not be prefixed with their object -
    -   javascript/global/Array/Array.isArray --\> javascript/global/Array/isArray

-   Drop the Constants, Functions and Properties top levels and incorporate them into the global hierarchy or object pages instead.

-   Low priority -
    -   Move constants into the page of their parent object. So, `Infinity` will be shown as a section within the global page. It will not have its own page.
    -   Alternatively - treat constants as regular properties within the hierarchy.

## Templates and forms

Forms for all pages will be developed to allow editing with Semantic Forms rather than basic Mediawiki markup.

Two forms have been defined and are listed on the [new page tool](/WPD:New_Page), JavaScript Operator and JavaScript Statement. However, we are missing a form for JavaScript built-in objects.

Semantic query using the [semantic query interface](/Special:Ask) should work. Investigation will be made whether or not JavaScript should be supported in queries. This involves making the forms more semantic web aware, not only for the sake of page metadata like authorship and page date, but also so that assertions can be made about the parts of the language or built-in objects. Reference about the extensions:

<dl>
<dd>
<dl>
<dd>
[Semantic Forms](http://www.mediawiki.org/wiki/Extension:Semantic_Forms)

</dd>
<dd>
[Semantic MediaWiki](http://www.mediawiki.org/wiki/Extension:Semantic_MediaWiki)

</dd>
</dl>
</dd>
</dl>
## On-going work

The latest round of converted files is located [here](https://github.com/maxpolk/msdn-js-conversion/tree/master/round-alice) as .wiki files, one of which is the mapping file upload-mapping.wiki.

Work has already begun importing MSDN JS pages:

-   Search discussion in the mailing list [[1]](http://lists.w3.org/Archives/Public/public-webplatform/)
-   Discussed in [Webplatform meetings](/WPD:Community/Meetings/General)
-   Project tasks and bugs reported in the [MSDN conversion issue tracking](http://project.webplatform.org/msdnjs)
-   Guidelines [Guidelines](/WPD:Content/Reference_articles)
-   Have this proposal reviewed and approved

Unfinished work or work not yet started:

-   Create or update forms.
-   Create a [new page tool](/WPD:New_Page) for JavaScript
-   Update the article [reference page](/WPD:Content/Reference_articles) to fix the reference to the new page tool and update page location from old values like "js/operators"
-   Format information during the MSDN JS import to conform to the form templates
