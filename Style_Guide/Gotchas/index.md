This page describes some intricacies of the mark-up syntax used by Semantic MediaWiki that can cause confusion for people editing WPD.

==Tables==
"Normal" MediaWiki syntax for tables does not work in Semantic MediaWiki forms. See [[/WPD:Manual_Of_Style/Tables|Tables]] for details.

==Pipe characters==
Related to the table issue, the pipe character ("|") cannot appear in text in a Semantic MediaWiki form. In place of the pipe character, you must use the sequence "{{!}}". For example:

<pre>
The logical OR operator {{!}}{{!}} returns true if either operand is true.
</pre>
'''Result:'''
<blockquote>
The logical OR operator {{!}}{{!}} returns true if either operand is true.
</blockquote>