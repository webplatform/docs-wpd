==Syntax==
For consistency and compatibility of tables, please use the following table syntax styles. These rules are required to ensure that tables print correctly in all contexts, including when they are part of a form field.

===Normal pages===
<pre><nowiki>
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
</nowiki></pre>

This results in the following table:

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

===Form-based pages===
Tables in a template or form-based page must use the [[WPD:Manual_Of_Style/Gotchas#The_dreaded_pipe_character|"pipe hack"]] instead of the <code>|</code> character:

<pre><nowiki>
{{!}}
</nowiki></pre>

Thus, the same table in a form would use the following (ugly) syntax:

<pre><nowiki>
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
</nowiki></pre>

===Do not do this!===
Do not use the single-line row syntax.
<pre><nowiki>
{|
| head 1    !! column 2  !! column 3
|-
| column a1 || column a2 || column a3
|-
| column b1 || column b2 || column b3
|}
</nowiki></pre>

==Sortable tables==
MediaWiki has the ability to create [http://www.mediawiki.org/wiki/Help:Sorting sortable tables], simply by adding the class <code>sortable</code>:

<pre><nowiki>
{| class="sortable"
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
</nowiki></pre>

This results in the following table:

{| class="sortable"
! head 1
! head 2
! head 3
|-
| apple 1
| peach 2
| blueberry 3
|-
| ape 1
| dog 2
| zebra 3
|}


==Other, less styled variant==
This variant has been found by mix-matching class names. Consider this as a hack if you really need to put data in a table without being forced to use first row as the table heading cell.

<pre><nowiki>
{| class="mw-datatable os-suggest-results filehistory"
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
</nowiki></pre>

This results in the following table:

{| class="mw-datatable os-suggest-results filehistory"
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