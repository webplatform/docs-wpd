---
title: Gotchas
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - first-line
uri: 'WPD:Style Guide/Gotchas'

---
Gotchas, gaaks, traps, pratfalls, syntax errors - every language is full of them, and MediaWiki markup is no exception. This article lists those that we've discovered as we build this site and work with content. Wherever possible, a work-around is provided.

# <span>The dreaded pipe character</span>

> "You wanna come over? It's pipe night!" -Kramer on *Seinfeld*

**What happens**

The content you've entered in the **Content** text field contains a pipe character (**|**). When you click **Save page** all of the text including and following the pipe character disappears.

A pipe character in a Semantic MediaWiki form gets interpreted as a parameter separator for the template call. When you edit a page via **Edit** (&action=formedit in the URL) everything you enter in the **Content** text field is contained in a form that calls a template to render the content. So the rendering engine hits the pipe and stops generating the form (unless the characters following the pipe happen to match a named parameter, but hey, what are the chances?).

<dl>
<dd>
**Note:** The pipe character works just fine in internal links, like [[WPD:Style\_Manual**|**Style manual]] and in subsequent template calls, as in {{template**|**parameter}}. This is just a bug in the situations described below.

</dd>
</dl>
**What to do**

Yes, you can get your content back. It's still there. Deep breath.

1.  From the **Edit** menu, select **Edit Source**.
    -   Alternatively, in the URL for the page you can replace **&action=formedit** with **&action=edit**.

2.  Find the offending pipe character, **|**.
3.  Replace the pipe character with **{{!}}** or **&\#124;**.

**{{!}}** is a transclusion of a template named **!** which contains a single pipe character. Luckily, the rendering engine evaluatates template transclusions after producing the form, so the pipe character does not get interpreted as a parameter separator. The &\#124; escape is even stronger because only the browser will render the pipe character from it.

## <span>Tables with pipe characters</span>

To create tables, you have to avoid pipes completely. See [Tables](/WPD:Manual_Of_Style/Tables) for details.

## <span>Pre sections with pipe characters</span>

It's even worse to use pipes in an explicit \<pre\> section. The rendering engine is supposed to ignore everything in a \<pre\> section and reproduce it as is. But no. For this you have to use the **&\#124;** Here's an example:

`  <pre>if (moodQuery==checkin.mood&#124;&#124;moodQuery) handler(checkin);</pre> `

This code renders as follows.

    if (moodQuery==checkin.mood||moodQuery) handler(checkin);

In lines of code designated by a leading single space (implicit pre-formatted sections, let's call 'em), you may use the {{!}} template. Here's an example:

`    if (moodQuery==checkin.mood{{!}}{{!}}moodQuery) handler(checkin); `

(With a leading space), this code renders as follows.

    if (moodQuery==checkin.mood||moodQuery) handler(checkin);

And just to beat this topic to death, pipes in \<code\>-encoded text must also be substituted with the {{!}} template. The rendering engine treats such sections only for style considerations (with CSS), it still evaluates the characters.

## <span>Parser functions with pipe characters</span>

But wait, there's more! However, you don't have to worry about this unless you're editing the templates and forms used to build the wiki itself. You won't encounter parser functions, typically, in your day-to-day content editing.

Parser functions also gaak when they encounter pipes. So, when you combine a parser function like \#if with a table, you have to use the {{!}} template instead of pipes for the table.

Here's the normal \#if syntax:

``` html
{{#if: condition | value | else-value}}
```

 Here's the normal syntax for a table:

``` html
{| class="wikitable"
! Header-value 1
! Header-value-2
|-
| Row-value 1
| Row-value-2
|}
```

 The problem is that in the \#if block, every pipe character the rendering engine encounters will be interpreted literally. So if you try to include pipe characters for the table syntax as part of the value or else-value, it just won't work. Here's an example where we use the {{!}} template hack:

``` html
{{#if: {{{Specifications|}}} |
==Related Specifications==
{{{!}} class="wikitable"
! Specification
! Status
! Related Changes
{{!}}-
{{{Specifications|}}}
{{!}}} | }}
```

# <span>Escaping characters</span>

If you include certain characters in your article, like the pipe character, the Semantic MediaWiki will interpret these as part of the template processing instructions and the result is usually a break in the rendering at the point where the character appears. See [The dreaded pipe character](#The_dreaded_pipe_character) above. For these characters, use their HTML entity tags, shown in this table.

|Character|Description|HTML Entity|
|:--------|:----------|:----------|
|[|Left square bracket|&\#91;|
|]|Right square bracket|&\#93;|
|{|Left curly bracket|&\#123;|
|}|Right curly bracket|&\#125;|
|||Pipe|&\#124;|
|'|Apostrophe|&\#124;|

# <span>Unclosed brackets</span>

When you include either curly or straight brackets in your article, the wiki will choke if you don't pair a left bracket with a matching right bracket. The form will stop rendering and you'll see an error message like this:

![open bracket.png](/assets/public/2/28/open_bracket.png)

If the text incudes a single bracket that should not be paired, as when the text describes a bracket character as part of a code example, use an HTML entity instead of the keyboard character. See [Escaping characters](#Escaping_characters) for more information.

# <span>URL containing special characters in notes or other tags</span>

Certain links contain special characters, such as the equal sign (=) in a link to a YouTube video (for example, <http://www.youtube.com/watch?v=me3BviH3nZc>). When these links are inside other wiki references, such as the Note tag, the special character needs to be escaped. Two ways to do so are:

-   Replace every = with =, as in:

``` html
{{Note|[http://www.youtube.com/watch?v{{=}}me3BviH3nZc Watch Erik's entire WebGL video tutorial] for free on YouTube. Over 2 and a half hours of WebGL tuition! }}
```

 OR

-   Prefix the note-text with 1=, as in:

``` html
{{Note|1=[http://www.youtube.com/watch?v=me3BviH3nZc Watch Erik's entire WebGL video tutorial] for free on YouTube. Over 2 and a half hours of WebGL tuition! }}
```

# <span>Spaces in template calls</span>

This applies only if you are editing the templates and forms used to build this wiki. MediaWiki is very weird about spaces. In particular, a line that starts with a single space is interpreted as a pre-formatted line of characters, and a group of such lines are then formatted as a \<pre\> block in the HTML output. This can bite you in template calls where you might have added spaces for readability. Most of the times they get trimmed off, but sometimes they don't. In general **do not use spaces** around parameter values. Most of the times everything will work fine, but some times it will break without warning. See the [External Attribution Block template](/Template:External_Attribution_Block) for an example.

# <span>HTML code</span>

Because HTML markup is interpreted by MediaWiki, you must enclose code examples that contain HTML markup in a `<syntaxhighlight>` block. See [Code syntax highlighting](/WPD:Style_Manual#Code_syntax_highlighting) in the style manual for details on using this tag.

To mention HTML elements in an inline context (in text rather than an example block), use the `&lt;` and `&gt;` character entities to represent the left and right angle brackets around the name.

To refer to a `<script>` element, use the following:

    &lt;script&gt;

Otherwise, the element is interpreted, and halts processing of the page.

# <span>Leading colon in page name</span>

Pages with a leading colon in their name (e.g. [first-line](/Special:FormEdit/Method/first-line?redlink=1)) will display their h1 title incorrectly, because the first colon will be interpreted as starting a dl list.

To work around this, use an HTML escape of ":" (i.e. &\#58;) in the "custom title" field.