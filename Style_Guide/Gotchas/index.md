Gotchas, gaaks, traps, pratfalls - every language is full of them, and MediaWiki markdown is no exception. This article lists those that we've discovered as we build this site and work with content. Wherever possible, a work-around is provided.

==The Dreaded pipe character==

""What happens:"" The content you've entered in the text field contains a pipe character. When you click Save page all of the text including and following the pipe character disappears.

This can happen in the following cases:

===Tables with pipe characters===

This page describes some intricacies of the mark-up syntax used by Semantic MediaWiki that can cause confusion for people editing WPD.

==Tables==
"Normal" MediaWiki syntax for tables does not work in Semantic MediaWiki forms. See [[WPD:Manual_Of_Style/Tables|Tables]] for details.

==Pipe characters==
Related to the table issue, the pipe character ("|") cannot appear in text in a Semantic MediaWiki form. In place of the pipe character, you must use the sequence "{{!}}". For example:

<pre>
The logical OR operator {{!}}{{!}} returns true if either operand is true.
</pre>
'''Result:'''
<blockquote>
The logical OR operator {{!}}{{!}} returns true if either operand is true.
</blockquote>

{{Note|The <nowiki>{{!}}</nowiki> escape sequence does not work properly inside a <nowiki><pre></nowiki> element, when editing using a form. To edit pages that have this condition, use the Edit Source link to edit the page, being careful not to disturb any of the form-related syntax on the page.}}