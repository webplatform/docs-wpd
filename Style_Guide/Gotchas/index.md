---
title: WPD:Style Guide/Gotchas
---
<h1><span class="mw-headline" id="Gotchas">Gotchas</span></h1>
<p>Gotchas, gaaks, traps, pratfalls, syntax errors - every language is full of them, and MediaWiki markup is no exception. This article lists those that we've discovered as we build this site and work with content. Wherever possible, a work-around is provided.
</p>
<h1><span class="mw-headline" id="The_dreaded_pipe_character">The dreaded pipe character</span></h1>
<blockquote>"You wanna come over? It's pipe night!"
-Kramer on <i>Seinfeld</i></blockquote>
<p><b>What happens</b>
</p><p>The content you've entered in the <b>Content</b> text field contains a pipe character (<b>|</b>). When you click <b>Save page</b> all of the text including and following the pipe character disappears.
</p><p>A pipe character in a Semantic MediaWiki form gets interpreted as a parameter separator for the template call. When you edit a page via <b>Edit</b> (&amp;action=formedit in the URL) everything you enter in the <b>Content</b> text field is contained in a form that calls a template to render the content. So the rendering engine hits the pipe and stops generating the form (unless the characters following the pipe happen to match a named parameter, but hey, what are the chances?).
</p>
<dl><dd><b>Note:</b> The pipe character works just fine in internal links, like [[WPD:Style_Manual<b>&#124;</b>Style manual]] and in subsequent template calls, as in {{template<b>&#124;</b>parameter}}. This is just a bug in the situations described below.</dd></dl>
<p><b>What to do</b>
</p><p>Yes, you can get your content back. It's still there. Deep breath.
</p>
<ol><li> From the <b>Edit</b> menu, select <b>Edit Source</b>.
<ul><li> Alternatively, in the URL for the page you can replace <b>&amp;action=formedit</b> with <b>&amp;action=edit</b>.</li></ul></li>
<li> Find the offending pipe character, <b>|</b>.</li>
<li> Replace the pipe character with <b>{{!}}</b> or <b>&amp;#124;</b>.</li></ol>
<p><b>{{!}}</b> is a transclusion of a template named <b>!</b> which contains a single pipe character. Luckily, the rendering engine evaluatates template transclusions after producing the form, so the pipe character does not get interpreted as a parameter separator. The &amp;#124; escape is even stronger because only the browser will render the pipe character from it.
</p>
<h2><span class="mw-headline" id="Tables_with_pipe_characters">Tables with pipe characters</span></h2>
<p>To create tables, you have to avoid pipes completely. See <a href="/wiki/WPD:Manual_Of_Style/Tables" title="WPD:Manual Of Style/Tables" class="mw-redirect">Tables</a> for details. 
</p>
<h2><span class="mw-headline" id="Pre_sections_with_pipe_characters">Pre sections with pipe characters</span></h2>
<p>It's even worse to use pipes in an explicit &lt;pre&gt; section. The rendering engine is supposed to ignore everything in a &lt;pre&gt; section and reproduce it as is.  But no.  For this you have to use the <b>&amp;#124;</b>  Here's an example:
</p><p><code>

&lt;pre&gt;if (moodQuery==checkin.mood&amp;#124;&amp;#124;moodQuery) handler(checkin);&lt;/pre&gt;

</code>
</p><p>This code renders as follows.
</p>
<pre>
if (moodQuery==checkin.mood&#124;&#124;moodQuery) handler(checkin);
</pre>
<p>In lines of code designated by a leading single space (implicit pre-formatted sections, let's call 'em), you may use the {{!}} template. Here's an example:
</p><p><code>
&#160;
 if (moodQuery==checkin.mood{{!}}{{!}}moodQuery) handler(checkin);

</code>
</p><p>(With a leading space), this code renders as follows.
</p>
<pre>if (moodQuery==checkin.mood||moodQuery) handler(checkin);
</pre>
<p>And just to beat this topic to death, pipes in &lt;code&gt;-encoded text must also be substituted with the {{!}} template. The rendering engine treats such sections only for style considerations (with CSS), it still evaluates the characters.
</p>
<h2><span class="mw-headline" id="Parser_functions_with_pipe_characters">Parser functions with pipe characters</span></h2>
<p>But wait, there's more! However, you don't have to worry about this unless you're editing the templates and forms used to build the wiki itself. You won't encounter parser functions, typically, in your day-to-day content editing.
</p><p>Parser functions also gaak when they encounter pipes. So, when you combine a parser function like #if with a table, you have to use the {{!}} template instead of pipes for the table.
</p><p>Here's the normal #if syntax:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{#if: condition | value | else-value}}</pre></div></div>
<p>Here's the normal syntax for a table: 
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{| class=&quot;wikitable&quot;
! Header-value 1
! Header-value-2
|-
| Row-value 1
| Row-value-2
|}</pre></div></div>
<p>The problem is that in the #if block, every pipe character the rendering engine encounters will be interpreted literally. So if you try to include pipe characters for the table syntax as part of the value or else-value, it just won't work. Here's an example where we use the {{!}} template hack:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{#if: {{{Specifications|}}} | 
==Related Specifications==
{{{!}} class=&quot;wikitable&quot;
! Specification
! Status
! Related Changes
{{!}}-
{{{Specifications|}}}
{{!}}} | }}</pre></div></div>
<h1><span class="mw-headline" id="Escaping_characters">Escaping characters</span></h1>
<p>If you include certain characters in your article, like the pipe character, the Semantic MediaWiki will interpret these as part of the template processing instructions and the result is usually a break in the rendering at the point where the character appears. See <a href="#The_dreaded_pipe_character">The dreaded pipe character</a> above. For these characters, use their HTML entity tags, shown in this table.
</p>
<table class="wikitable">

<tr>
<th> Character </th>
<th> Description </th>
<th> HTML Entity
</th></tr>
<tr>
<td> &#91; </td>
<td> Left square bracket </td>
<td> &amp;#91;
</td></tr>
<tr>
<td> &#93; </td>
<td> Right square bracket </td>
<td> &amp;#93;
</td></tr>
<tr>
<td> &#123; </td>
<td> Left curly bracket </td>
<td> &amp;#123;
</td></tr>
<tr>
<td> &#125; </td>
<td> Right curly bracket </td>
<td> &amp;#125;
</td></tr>
<tr>
<td> &#124; </td>
<td> Pipe </td>
<td> &amp;#124;
</td></tr>
<tr>
<td> &#39; </td>
<td> Apostrophe </td>
<td> &amp;#124;
</td></tr></table>
<h1><span class="mw-headline" id="Unclosed_brackets">Unclosed brackets</span></h1>
<p>When you include either curly or straight brackets in your article, the wiki will choke if you don't pair a left bracket with a matching right bracket. The form will stop rendering and you'll see an error message like this:
</p><p><a href="/wiki/File:open_bracket.png" class="image"><img alt="open bracket.png" src="//static.webplatform.org/w/public/2/28/open_bracket.png" width="1144" height="85" /></a>
</p><p>If the text incudes a single bracket that should not be paired, as when the text describes a bracket character as part of a code example, use an HTML entity instead of the keyboard character. See <a href="#Escaping_characters">Escaping characters</a> for more information.
</p>
<h1><span class="mw-headline" id="URL_containing_special_characters_in_notes_or_other_tags">URL containing special characters in notes or other tags</span></h1>
<p>Certain links contain special characters, such as the equal sign (=) in a link to a YouTube video (for example, <a rel="nofollow" class="external free" href="http://www.youtube.com/watch?v=me3BviH3nZc">http://www.youtube.com/watch?v=me3BviH3nZc</a>). When these links are inside other wiki references, such as the Note tag, the special character needs to be escaped. Two ways to do so are:
</p>
<ul><li> Replace every = with =, as in:</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{Note|[http://www.youtube.com/watch?v{{=}}me3BviH3nZc Watch Erik's entire WebGL video tutorial] for free on YouTube. Over 2 and a half hours of WebGL tuition! }}</pre></div></div>
<p>OR
</p>
<ul><li> Prefix the note-text with 1=, as in:</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{Note|1=[http://www.youtube.com/watch?v=me3BviH3nZc Watch Erik's entire WebGL video tutorial] for free on YouTube. Over 2 and a half hours of WebGL tuition! }}</pre></div></div>
<p><br />
</p>
<h1><span class="mw-headline" id="Spaces_in_template_calls">Spaces in template calls</span></h1>
<p>This applies only if you are editing the templates and forms used to build this wiki. MediaWiki is very weird about spaces. In particular, a line that starts with a single space is interpreted as a pre-formatted line of characters, and a group of such lines are then formatted as a &lt;pre&gt; block in the HTML output. This can bite you in template calls where you might have added spaces for readability. Most of the times they get trimmed off, but sometimes they don't. In general <b>do not use spaces</b> around parameter values. Most of the times everything will work fine, but some times it will break without warning. See the <a href="/wiki/Template:External_Attribution_Block" title="Template:External Attribution Block">External Attribution Block template</a> for an example.
</p>
<h1><span class="mw-headline" id="HTML_code">HTML code</span></h1>
<p>Because HTML markup is interpreted by MediaWiki, you must enclose code examples that contain HTML markup in a <code>&lt;syntaxhighlight&gt;</code> block. See <a href="/wiki/WPD:Style_Manual#Code_syntax_highlighting" title="WPD:Style Manual" class="mw-redirect">Code syntax highlighting</a> in the style manual for details on using this tag.
</p><p>To mention HTML elements in an inline context (in text rather than an example block), use the <code>&amp;lt;</code> and <code>&amp;gt;</code> character entities to represent the left and right angle brackets around the name. 
</p><p>To refer to a <code>&lt;script&gt;</code> element, use the following:
</p>
<pre>&amp;lt;script&amp;gt;
</pre>
<p>Otherwise, the element is interpreted, and halts processing of the page.
</p>
<h1><span class="mw-headline" id="Leading_colon_in_page_name">Leading colon in page name</span></h1>
<p>Pages with a leading colon in their name (e.g. <a href="/wiki/Special:FormEdit/Method/first-line?redlink=1" class="new" title="first-line (page does not exist)">first-line</a>) will display their h1 title incorrectly, because the first colon will be interpreted as starting a dl list.
</p><p>To work around this, use an HTML escape of ":" (i.e. &amp;#58;) in the "custom title" field.
</p>
<!-- 
NewPP limit report
CPU time usage: 0.129 seconds
Real time usage: 1.336 seconds
Preprocessor visited node count: 303/1000000
Preprocessor generated node count: 737/1000000
Post‐expand include size: 40/2097152 bytes
Template argument size: 21/2097152 bytes
Highest expansion depth: 4/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%   37.095      1 - -total
 38.00%   14.095      1 - Template:Page_Title
  7.52%    2.790      1 - Template:=
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:1005-0!*!0!!*!5!*!esi=1 and timestamp 20150731030751 and revision id 66154
 -->
