Gotchas, gaaks, traps, pratfalls, syntax errors - every language is full of them, and MediaWiki markup is no exception. This article lists those that we've discovered as we build this site and work with content. Wherever possible, a work-around is provided.

==The dreaded pipe character==

'''What happens'''

The content you've entered in the '''Content''' text field contains a pipe character ('''<nowiki>|</nowiki>'''). When you click '''Save page''' all of the text including and following the pipe character disappears.

A pipe character in a Semantic MediaWiki form gets interpreted as a parameter separator for the template call. When you edit a page via '''Edit with Form''' (&action=formedit) everything you enter in the '''Content''' text field is contained in a form that calls a template to render the content. So the rendering engine hits the pipe and stops generating the form (unless the characters following the pipe happen to match a named parameter, but hey, what are the chances?). 

'''What to do'''

Yes, you can get your content back. It's still there. Deep breath.
# In the URL for the page, replace '''&action=formedit''' with '''&action=edit'''.
# Find the offending pipe character, '''<nowiki>|</nowiki>'''.
# Replace the pipe character with '''<nowiki>{{!}}</nowiki>''' or .

'''<nowiki>{{!}}</nowiki>''' is a transclusion of a template named '''<nowiki>!</nowiki>''' which contains a single pipe character. Luckily, the rendering engine evaluatates template transclusions after producing the form, so the pipe character does not get interpreted as a parameter separator.

===Tables with pipe characters===

To create tables, you have to avoid pipes completely. See [[WPD:Manual_Of_Style/Tables|Tables]] for details. 

===Pre sections with pipe characters===

It's even worse to use pipes in an explicit <nowiki><pre></nowiki> section. The rendering engine isignores everything in a <nowiki><pre></nowiki> section and reproduces it as is. Here's an example:

<code>
<nowiki>
<pre>if (moodQuery==checkin.mood&#l24;&#l24;moodQuery) handler(checkin);</pre>
</nowiki>
</code>

This code renders as follows.

<pre>
if (moodQuery==checkin.mood&#124;&#124;moodQuery) handler(checkin);
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

==Spaces in template calls==

This applies only if you are editing the templates and forms used to build this wiki. MediaWiki is very weird about spaces. In particular, a line that starts with a single space is interpreted as a pre-formatted line of characters, and a group of such lines are then formatted as a <nowiki><pre></nowiki> block in the HTML output. This can bite you in template calls where you might have added spaces for readability. Most of the times they get trimmed off, but sometimes they don't. In general '''do not use spaces''' around parameter values. Most of the times everything will work fine, but some times it will break without warning. See the [[Template:External_Attribution_Block|External Attribution Block template]] for an example.

= HTML code =

Because HTML markup is interpreted by MediaWiki, you must enclose code examples that contain HTML markup in a <code><nowiki>&lt;syntaxhighlight&gt;</nowiki></code> block. To mention HTML elements in an inline context (in text rather than an example block), use the <code>&amp;lt;</code> and <code>&amp;gt;</code> character entities to represent the left and right angle brackets around the name. 

To refer to a <code>&lt;script&gt;</code> element, use the following:

 &amp;lt;script&amp;gt;

Otherwise, the element is interpreted, and halts processing of the page.