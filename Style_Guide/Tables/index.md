---
title: WPD:Style Guide/Tables
---
<h2><span class="mw-headline" id="Syntax">Syntax</span></h2>
<p>For consistency and compatibility of tables, please use the following table syntax styles. These rules are required to ensure that tables print correctly in all contexts, including when they are part of a form field.
</p>
<h3><span class="mw-headline" id="Normal_pages">Normal pages</span></h3>
<pre>
{|
! head 1
! head 2
! head 3
|-
| column a1
| column a2
| column a3
|-
| column b1
| column b2
| column b3
|}
</pre>
<p>This results in the following table:
</p>
<table>
<tr>
<th> head 1
</th>
<th> head 2
</th>
<th> head 3
</th></tr>
<tr>
<td> column a1
</td>
<td> column a2
</td>
<td> column a3
</td></tr>
<tr>
<td> column b1
</td>
<td> column b2
</td>
<td> column b3
</td></tr></table>
<h3><span class="mw-headline" id="Form-based_pages">Form-based pages</span></h3>
<p>Tables in a template or form-based page must use the <a href="/wiki/WPD:Manual_Of_Style/Gotchas#The_dreaded_pipe_character" title="WPD:Manual Of Style/Gotchas" class="mw-redirect">"pipe hack"</a> instead of the <code>|</code> character:
</p>
<pre>
{{!}}
</pre>
<p>Thus, the same table in a form would use the following (ugly) syntax:
</p>
<pre>
{{{!}}
! head 1
! head 2
! head 3
{{!}}-
{{!}} column a1
{{!}} column a2
{{!}} column a3
{{!}}-
{{!}} column b1
{{!}} column b2
{{!}} column b3
{{!}}}
</pre>
<h3><span class="mw-headline" id="Do_not_do_this.21">Do not do this!</span></h3>
<p>Do not use the single-line row syntax.
</p>
<pre>
{|
| head 1   &#160;!! column 2 &#160;!! column 3
|-
| column a1 || column a2 || column a3
|-
| column b1 || column b2 || column b3
|}
</pre>
<h2><span class="mw-headline" id="Sortable_tables">Sortable tables</span></h2>
<p>MediaWiki has the ability to create <a class="external text" href="http://www.mediawiki.org/wiki/Help:Sorting">sortable tables</a>, simply by adding the class <code>sortable</code>:
</p>
<pre>
{| class=&quot;sortable&quot;
! head 1
! head 2
! head 3
|-
| apple a1
| peach a2
| blueberry a3
|-
| ape b1
| dog b2
| fish b3
|}
</pre>
<p>This results in the following table:
</p>
<table class="sortable">
<tr>
<th> head 1
</th>
<th> head 2
</th>
<th> head 3
</th></tr>
<tr>
<td> apple 1
</td>
<td> peach 2
</td>
<td> blueberry 3
</td></tr>
<tr>
<td> ape 1
</td>
<td> dog 2
</td>
<td> zebra 3
</td></tr></table>
<p><br />
</p>
<h2><span class="mw-headline" id="Other.2C_less_styled_variant">Other, less styled variant</span></h2>
<p>This variant has been found by mix-matching class names. Consider this as a hack if you really need to put data in a table without being forced to use first row as the table heading cell.
</p>
<pre>
{| class=&quot;mw-datatable os-suggest-results filehistory&quot;
|+Unstyled table, and showing table caption cell syntax
|-
|Column one
|Column two
|Column three
|-
|'''Column one and row one'''
|Column two:
* Lists
* works
* that way
|Column three
|-
|'''Column one and row two'''
|Column two, row two
|Column three, row two
|}
</pre>
<p>This results in the following table:
</p>
<table class="mw-datatable os-suggest-results filehistory">
<caption>Unstyled table, and showing table caption cell syntax
</caption>
<tr>
<td>Column one
</td>
<td>Column two
</td>
<td>Column three
</td></tr>
<tr>
<td><b>Column one and row one</b>
</td>
<td>Column two:
<ul><li> Lists</li>
<li> works</li>
<li> that way</li></ul>
</td>
<td>Column three
</td></tr>
<tr>
<td><b>Column one and row two</b>
</td>
<td>Column two, row two
</td>
<td>Column three, row two
</td></tr></table>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:569-0!*!0!!*!*!*!esi=1 and timestamp 20150731182151 and revision id 38396
 -->
