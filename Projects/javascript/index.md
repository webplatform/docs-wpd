---
title: WPD:Projects/javascript
---
<div class="note"><b>NOTE</b> Project is completed, participate in improving the <a href="/wiki/javascript" title="javascript">javascript</a> documentation!</div>
<h1><span class="mw-headline" id="JavaScript_project_proposal">JavaScript project proposal</span></h1>
<p>JavaScript is a proposed Web Platform Docs project to document the implementation of the ECMAScript standard in web browsers, focusing on the language itself rather than how it is coupled inside a browser to dom objects, events, HTML5 APIs, or CSS style.
</p>
<h2><span class="mw-headline" id="Project_characteristics">Project characteristics</span></h2>
<dl><dt> Version</dt>
<dd> The version of JavaScript documented will initially be based on the ECMA-262 edition 5.1 <a rel="nofollow" class="external text" href="http://www.ecma-international.org/publications/standards/Ecma-262.htm">standard of June 2011</a>, since it has the <a rel="nofollow" class="external text" href="https://en.wikipedia.org/wiki/ECMAScript#Conformance_tests">greatest browser conformance</a>.</dd></dl>
<dl><dt> Location</dt>
<dd> All JavaScript reference material will exist relative to the <a href="/wiki/javascript" title="javascript">javascript</a> parent page.</dd></dl>
<h2><span class="mw-headline" id="Page_structure">Page structure</span></h2>
<p>An initial bulk page import is planned based on pages <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0238.html">donated by Microsoft</a>, and reformatted.  The import work is an <a rel="nofollow" class="external text" href="http://project.webplatform.org/msdnjs">ongoing subproject</a>.  The initial page structure will be a set of top-level pages shown below, each one having second-level subpages that capture the logical structure and for efficient bread crumbs page navigation.
</p>
<h3><span class="mw-headline" id="Top-level_pages">Top-level pages</span></h3>
<table class="wikitable">
<tr>
<th> Top-level page </th>
<th> Subpages
</th></tr>
<tr>
<td> Objects </td>
<td> 336 pages: built-in objects (Array, ArrayBuffer, Boolean, etc) and other special objects (arguments, Function, Global, Object).
</td></tr>
<tr>
<td> Constants </td>
<td> 1 page listing constants found within Math, Global, and Number like (E, Infinity, MIN_VALUE)
</td></tr>
<tr>
<td> Properties </td>
<td> 1 page listing properties found within arguments, RegExp, Function, Error, etc.
</td></tr>
<tr>
<td> Functions </td>
<td> 1 page listing functions found within Math, Global, Object, String, etc.
</td></tr>
<tr>
<td> Methods </td>
<td> 1 page listing methods found within String, Function, Enumerator, Array, etc.
</td></tr>
<tr>
<td> Operators </td>
<td> 39 pages: Addition Assignment, Addition, Assignment, Bitwise AND Assignment, etc.
</td></tr>
<tr>
<td> Statements </td>
<td> 22 pages:break, Comment, continue, do while, etc.
</td></tr>
<tr>
<td> Errors </td>
<td> 2 pages: Run time, Syntax
</td></tr>
<tr>
<td> Reserved Words </td>
<td> 1 page listing words unable to be used as identifiers.
</td></tr></table>
<h3><span class="mw-headline" id="Third-level_subpages">Third-level subpages</span></h3>
<p>Third-level subpages will exist for each property, function (not requiring an object), method (requiring an object), and constant.  For example, under the Objects top-level page, we have second-level pages Array and Math.  These in turn will have the following third-level subpages:
</p>
<ul><li> Array's three properties: constructor, length, and prototype.</li>
<li> Array's one function: Array.isArray.</li>
<li> Array's many methods: concat, every, filter, forEach, indexOf, join, lastIndexOf, map, pop, push, reduce, reduceRight, reverse, shift, slice, some, sort, splice, toString, unshift, and valueOf.</li>
<li> Math's constant Math.E.</li></ul>
<p>Putting it all together, an example URL path for the Array constructor would then be: "Objects/Array/constructor Property".  To see more examples, the current bulk import page names can be <a rel="nofollow" class="external text" href="https://github.com/maxpolk/msdn-js-conversion/blob/master/round-alice/upload-mapping.wiki">found here</a>.
</p><p>Notice the rules for third-level pages under Object:
</p>
<ul><li> property pages have a "Property" suffix, eg. Objects/Array/length <b>Property</b></li>
<li> function pages have a "Function" suffix, eg. Objects/Array/Array.isArray <b>Function</b></li>
<li> method pages have a "Method" suffix, eg. Objects/Array/concat <b>Method</b></li>
<li> constant pages have a "Constant" suffix, eg. Objects/Float32Array/BYTES_PER_ELEMENT <b>Constant</b></li></ul>
<p>Notice the rules for second-level pages under Operators:
</p>
<ul><li> Operators are spelled out as words, eg. Operators/Addition Assignment for the <code style="font-size: larger;">+=</code> operator</li>
<li> Logical or bitwise operators are capitalized, eg. Operators/Logical AND</li></ul>
<h3><span class="mw-headline" id="Path_rewriting_proposal">Path rewriting proposal</span></h3>
<ul><li> Rename the "Objects" level to "global" for greater accuracy and correctness -
<ul><li> javascript/global/Array</li>
<li> javascript/global/Object</li>
<li> javascript/global/parseInt</li></ul></li></ul>
<ul><li> Drop the suffixes -
<ul><li> javascript/global/Array/length Property --&gt; javascript/global/Array/length</li>
<li> javascript/global/Array/forEach Method --&gt; javascript/global/Array/forEach</li></ul></li></ul>
<ul><li> Static methods should not be prefixed with their object -
<ul><li> javascript/global/Array/Array.isArray --&gt; javascript/global/Array/isArray</li></ul></li></ul>
<ul><li> Drop the Constants, Functions and Properties top levels and incorporate them into the global hierarchy or object pages instead.</li></ul>
<ul><li> Low priority -
<ul><li> Move constants into the page of their parent object. So, <code>Infinity</code> will be shown as a section within the global page. It will not have its own page.</li>
<li> Alternatively - treat constants as regular properties within the hierarchy.</li></ul></li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Templates_and_forms">Templates and forms</span></h2>
<p>Forms for all pages will be developed to allow editing with Semantic Forms rather than basic Mediawiki markup.
</p><p>Two forms have been defined and are listed on the <a href="/wiki/WPD:New_Page" title="WPD:New Page">new page tool</a>, JavaScript Operator and JavaScript Statement.  However, we are missing a form for JavaScript built-in objects.
</p><p>Semantic query using the <a href="/wiki/Special:Ask" title="Special:Ask">semantic query interface</a> should work.  Investigation will be made whether or not JavaScript should be supported in queries.  This involves making the forms more semantic web aware, not only for the sake of page metadata like authorship and page date, but also so that assertions can be made about the parts of the language or built-in objects.  Reference about the extensions:
</p>
<dl><dd><dl><dd> <a class="external text" href="http://www.mediawiki.org/wiki/Extension:Semantic_Forms">Semantic Forms</a></dd>
<dd> <a class="external text" href="http://www.mediawiki.org/wiki/Extension:Semantic_MediaWiki">Semantic MediaWiki</a></dd></dl></dd></dl>
<h2><span class="mw-headline" id="On-going_work">On-going work</span></h2>
<p>The latest round of converted files is located <a rel="nofollow" class="external text" href="https://github.com/maxpolk/msdn-js-conversion/tree/master/round-alice">here</a> as .wiki files, one of which is the mapping file upload-mapping.wiki.
</p><p>Work has already begun importing MSDN JS pages:
</p>
<ul><li> Search discussion in the mailing list <a rel="nofollow" class="external autonumber" href="http://lists.w3.org/Archives/Public/public-webplatform/">[1]</a></li>
<li> Discussed in <a href="/wiki/WPD:Community/Meetings/General" title="WPD:Community/Meetings/General">Webplatform meetings</a></li>
<li> Project tasks and bugs reported in the  <a rel="nofollow" class="external text" href="http://project.webplatform.org/msdnjs">MSDN conversion issue tracking</a></li>
<li> Guidelines <a href="/wiki/WPD:Content/Reference_articles" title="WPD:Content/Reference articles">Guidelines</a></li>
<li> Have this proposal reviewed and approved</li></ul>
<p>Unfinished work or work not yet started:
</p>
<ul><li> Create or update forms.</li>
<li> Create a <a href="/wiki/WPD:New_Page" title="WPD:New Page">new page tool</a> for JavaScript</li>
<li> Update the article <a href="/wiki/WPD:Content/Reference_articles" title="WPD:Content/Reference articles">reference page</a> to fix the reference to the new page tool and update page location from old values like "js/operators"</li>
<li> Format information during the MSDN JS import to conform to the form templates</li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.029 seconds
Real time usage: 0.032 seconds
Preprocessor visited node count: 33/1000000
Preprocessor generated node count: 40/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:9301-0!*!0!!*!*!*!esi=1 and timestamp 20150731111136 and revision id 46055
 -->
