<div class='note'>'''NOTE''' Project is completed, participate in improving the [[javascript]] documentation!</div>

=JavaScript project proposal=
JavaScript is a proposed Web Platform Docs project to document the implementation of the ECMAScript standard in web browsers, focusing on the language itself rather than how it is coupled inside a browser to dom objects, events, HTML5 APIs, or CSS style.

==Project characteristics==
; Version: The version of JavaScript documented will initially be based on the ECMA-262 edition 5.1 [http://www.ecma-international.org/publications/standards/Ecma-262.htm standard of June 2011], since it has the [https://en.wikipedia.org/wiki/ECMAScript#Conformance_tests greatest browser conformance].

; Location: All JavaScript reference material will exist relative to the [[javascript]] parent page.

==Page structure==
An initial bulk page import is planned based on pages [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0238.html donated by Microsoft], and reformatted.  The import work is an [http://project.webplatform.org/msdnjs ongoing subproject].  The initial page structure will be a set of top-level pages shown below, each one having second-level subpages that capture the logical structure and for efficient bread crumbs page navigation.

===Top-level pages===

{| class="wikitable"
! Top-level page !! Subpages
|-
| Objects || 336 pages: built-in objects (Array, ArrayBuffer, Boolean, etc) and other special objects (arguments, Function, Global, Object).
|-
| Constants || 1 page listing constants found within Math, Global, and Number like (E, Infinity, MIN_VALUE)
|-
| Properties || 1 page listing properties found within arguments, RegExp, Function, Error, etc.
|-
| Functions || 1 page listing functions found within Math, Global, Object, String, etc.
|-
| Methods || 1 page listing methods found within String, Function, Enumerator, Array, etc.
|-
| Operators || 39 pages: Addition Assignment, Addition, Assignment, Bitwise AND Assignment, etc.
|-
| Statements || 22 pages:break, Comment, continue, do while, etc.
|-
| Errors || 2 pages: Run time, Syntax
|-
| Reserved Words || 1 page listing words unable to be used as identifiers.
|}

===Third-level subpages===
Third-level subpages will exist for each property, function (not requiring an object), method (requiring an object), and constant.  For example, under the Objects top-level page, we have second-level pages Array and Math.  These in turn will have the following third-level subpages:
* Array's three properties: constructor, length, and prototype.
* Array's one function: Array.isArray.
* Array's many methods: concat, every, filter, forEach, indexOf, join, lastIndexOf, map, pop, push, reduce, reduceRight, reverse, shift, slice, some, sort, splice, toString, unshift, and valueOf.
* Math's constant Math.E.

Putting it all together, an example URL path for the Array constructor would then be: "Objects/Array/constructor Property".  To see more examples, the current bulk import page names can be [https://github.com/maxpolk/msdn-js-conversion/blob/master/round-alice/upload-mapping.wiki found here].

Notice the rules for third-level pages under Object:
* property pages have a "Property" suffix, eg. Objects/Array/length '''Property'''
* function pages have a "Function" suffix, eg. Objects/Array/Array.isArray '''Function'''
* method pages have a "Method" suffix, eg. Objects/Array/concat '''Method'''
* constant pages have a "Constant" suffix, eg. Objects/Float32Array/BYTES_PER_ELEMENT '''Constant'''

Notice the rules for second-level pages under Operators:
* Operators are spelled out as words, eg. Operators/Addition Assignment for the <code style="font-size: larger;">+=</code> operator
* Logical or bitwise operators are capitalized, eg. Operators/Logical AND

===Path rewriting proposal===
* Rename the "Objects" level to "global" for greater accuracy and correctness -
** javascript/global/Array
** javascript/global/Object
** javascript/global/parseInt

* Drop the suffixes -
** javascript/global/Array/length Property --> javascript/global/Array/length
** javascript/global/Array/forEach Method --> javascript/global/Array/forEach

* Static methods should not be prefixed with their object -
** javascript/global/Array/Array.isArray --> javascript/global/Array/isArray

* Drop the Constants, Functions and Properties top levels and incorporate them into the global hierarchy or object pages instead.

* Low priority -
** Move constants into the page of their parent object. So, <code>Infinity</code> will be shown as a section within the global page. It will not have its own page.
** Alternatively - treat constants as regular properties within the hierarchy.


==Templates and forms==
Forms for all pages will be developed to allow editing with Semantic Forms rather than basic Mediawiki markup.

Two forms have been defined and are listed on the [[WPD:New_Page|new page tool]], JavaScript Operator and JavaScript Statement.  However, we are missing a form for JavaScript built-in objects.

Semantic query using the [[Special:Ask|semantic query interface]] should work.  Investigation will be made whether or not JavaScript should be supported in queries.  This involves making the forms more semantic web aware, not only for the sake of page metadata like authorship and page date, but also so that assertions can be made about the parts of the language or built-in objects.  Reference about the extensions:
:: [http://www.mediawiki.org/wiki/Extension:Semantic_Forms Semantic Forms]
:: [http://www.mediawiki.org/wiki/Extension:Semantic_MediaWiki Semantic MediaWiki]

==On-going work==
The latest round of converted files is located [https://github.com/maxpolk/msdn-js-conversion/tree/master/round-alice here] as .wiki files, one of which is the mapping file upload-mapping.wiki.

Work has already begun importing MSDN JS pages:
* Search discussion in the mailing list [http://lists.w3.org/Archives/Public/public-webplatform/]
* Discussed in [[WPD:Community/Meetings/General|Webplatform meetings]]
* Project tasks and bugs reported in the  [http://project.webplatform.org/msdnjs MSDN conversion issue tracking]
* Guidelines [[WPD:Content/Reference_articles|Guidelines]]
* Have this proposal reviewed and approved

Unfinished work or work not yet started:
* Create or update forms.
* Create a [[WPD:New_Page|new page tool]] for JavaScript
* Update the article [[WPD:Content/Reference_articles|reference page]] to fix the reference to the new page tool and update page location from old values like "js/operators"
* Format information during the MSDN JS import to conform to the form templates