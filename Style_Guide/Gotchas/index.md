Gotchas, gaaks, traps, pratfalls, syntax errors - every language is full of them, and MediaWiki markup is no exception. This article lists those that we've discovered as we build this site and work with content. Wherever possible, a work-around is provided.

==The dreaded pipe character==

'''What happens:''' The content you've entered in the '''Content''' text field contains a pipe character ('''<nowiki>|</nowiki>'''). When you click '''Save page''' all of the text including and following the pipe character disappears.

When the pipe character appears in a Semantic MediaWiki form it gets interpreted as a parameter separator for the template call. When you edit a page via '''Edit with Form''' (&action=formedit) everything you enter in the '''Content''' text field is contained in a form that calls a template to render the content. So the rendering engine hits the pipe and stops generating the form (unless the characters following the pipe happen to match a named parameter, but hey, what are the chances?). 

'''What to do:''' Yes, you can get your content back. It's still there. Deep breath.
# In the URL for the page, replace '''&action=formedit''' with '''&action=edit'''.
# Find the offending pipe character, '''<nowiki>|</nowiki>'''.
# Replace the pipe character with '''<nowiki>{{!}}</nowiki>'''.

'''<nowiki>{{!}}</nowiki>''' is a transclusion of a template named '''<nowiki>!</nowiki>''' which contains a single pipe character. Luckily, the rendering engine evaluatates template transclusions after producing the form, so the pipe character does not get interpreted as a parameter separator.

===Tables with pipe characters===

To create tables, you have to avoid pipes completely. See [[WPD:Manual_Of_Style/Tables|Tables]] for details. 

===Pre sections with pipe characters===

Related to the table issue,  For example:

<pre>
The logical OR operator {{!}}{{!}} returns true if either operand is true.
</pre>
'''Result:'''
<blockquote>
The logical OR operator {{!}}{{!}} returns true if either operand is true.
</blockquote>

{{Note|The <nowiki>{{!}}</nowiki> escape sequence does not work properly inside a <nowiki><pre></nowiki> element, when editing using a form. To edit pages that have this condition, use the Edit Source link to edit the page, being careful not to disturb any of the form-related syntax on the page.}}