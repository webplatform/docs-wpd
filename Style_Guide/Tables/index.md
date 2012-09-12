==Syntax==
For consistency and compatibility of tables, please use the following table syntax styles.

===Normal Pages===
<pre><nowiki>
{|
! head 1
! column 2
! column 3
|-
| column 1
| column 2
| column 3
|-
| column 1
| column 2
| column 3
|}
</nowiki></pre>

This results in the following table:

{|
! head 1
! head 2
! head 3
|-
| column 1
| column 2
| column 3
|-
| column 1
| column 2
| column 3
|}

===Form-Based Pages===
Tables in a template or form-based page must use the [[http://webplatform.org/docs/WPD:Implementation_Patterns#The_CSS_Property_page|"pipe hack"]] instead of the <code>|</code> character:

<pre><nowiki>
{{!}}
</nowiki></pre>

Thus, the same table in a form would use the following syntax:

<pre><nowiki>
{{{{!}}
! head 1
! head 2
! head 3
{{!}}-
{{!}} column 1
{{!}} column 2
{{!}} column 3
{{!}}-
{{!}} column 1
{{!}} column 2
{{!}} column 3
{{!}}}
</nowiki></pre>

===Do Not Do This!===
Do not use the single-line row syntax.
<pre><nowiki>
{|
| head 1   !! column 2 !! column 3
|-
| column 1 || column 2 || column 3
|-
| column 1 || column 2 || column 3
|}
</nowiki></pre>

==Sortable Tables==
MediaWiki has the ability to create sortable tables, simply by adding the class <code>wikitable sortable</code>:

<pre><nowiki>
{| class="sortable"|
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
| fish 3
|}
</nowiki></pre>

This results in the following table:

{| class="sortable"|
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