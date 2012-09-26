Gotchas, gaaks, traps, pratfalls, syntax errors - every language is full of them, and MediaWiki markup is no exception. This article lists those that we've discovered as we build this site and work with content. Wherever possible, a work-around is provided.

==The dreaded pipe character==

'''What happens'''
The content you've entered in the '''Content''' text field contains a pipe character ('''<nowiki>|</nowiki>'''). When you click '''Save page''' all of the text including and following the pipe character disappears.

When the pipe character appears in a Semantic MediaWiki form it gets interpreted as a parameter separator for the template call. When you edit a page via '''Edit with Form''' (&action=formedit) everything you enter in the '''Content''' text field is contained in a form that calls a template to render the content. So the rendering engine hits the pipe and stops generating the form (unless the characters following the pipe happen to match a named parameter, but hey, what are the chances?). 

'''What to do'''
Yes, you can get your content back. It's still there. Deep breath.
# In the URL for the page, replace '''&action=formedit''' with '''&action=edit'''.
# Find the offending pipe character, '''<nowiki>|</nowiki>'''.
# Replace the pipe character with '''<nowiki>{{!}}</nowiki>'''.

'''<nowiki>{{!}}</nowiki>''' is a transclusion of a template named '''<nowiki>!</nowiki>''' which contains a single pipe character. Luckily, the rendering engine evaluatates template transclusions after producing the form, so the pipe character does not get interpreted as a parameter separator.

===Tables with pipe characters===

To create tables, you have to avoid pipes completely. See [[WPD:Manual_Of_Style/Tables|Tables]] for details. 

===Pre sections with pipe characters===

It's okay to use pipes in an explicit <nowiki><pre></nowiki> section. The rendering engine ignores verything in a <nowiki><pre></nowiki> section and reproduces it as is. Here's an example:

<code>
<nowiki>
<pre>
if (moodQuery==checkin.mood||moodQuery) handler(checkin);
</pre>
</nowiki>
</code>

This code renders as follows.

<pre>
if (moodQuery==checkin.mood||moodQuery) handler(checkin);
</pre>

But in lines of code designated by a leading single space (implicit pre-formatted sections, let's call 'em), you have to use the <nowiki>{{!}}</nowiki> template. Here's an example:

<code>
&nbsp;<nowiki>
 if (moodQuery==checkin.mood{{!}}{{!}}moodQuery) handler(checkin);
</nowiki>
</code>

(With a leading space), this code renders as follows.

 if (moodQuery==checkin.mood{{!}}{{!}}moodQuery) handler(checkin);

And just to beat this topic to death, pipes in <nowiki><code></nowiki>-encoded text must also be substituted with the <nowiki>{{!}}</nowiki> template. The rendering engine treats such sections only for style considerations (with CSS), it still evaluates the characters.

===Parser functions with pipe characters===

But wait, there's more! However, you don't have to worry about this unless you're editing the templates and forms used to build the wiki itself. You won't encounter parser functions, typically, in your day-to-day content editing.

Parser functions also gaak when they encounter pipes. So, when you combine a parser function like <nowiki>#if</nowiki> with a table, you have to use the <nowiki>{{!}}</nowiki> template instead of pipes for the table.

Here's the normal #if syntax:

<syntaxhighlight>
{{#if: condition | value | else-value}}
</syntaxhighlight>

Here's normal syntax for a table: 

<syntaxhighlight>
{| class="wikitable"
! Header-value 1 !! Header-value-2
|-
| Row-value 1 || Row-value-2
|}
</syntaxhighlight>

The problem is that in the #if block, every pipe character the rendering engine encounters will be interpreted literally. So if you try to include pipe characters for the table syntax as part of the value or else-value, it just won't work. Here's an example where we use the <nowiki>{{!}}</nowiki> template hack:

<syntaxhighlight>
{{#if: {{{Specifications|}}} | 
==Related Specifications==
{{{!}} class="wikitable"
{{!}}-
! Specification !! Status !! Related Changes
{{{Specifications|}}}
{{!}}} | }}
</syntaxhighlight>