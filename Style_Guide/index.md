---
title: WPD:Style Guide
---
<h1><span class="mw-headline" id="WPD_style_guide">WPD style guide</span></h1>
<p>WebPlatform Docs (WPD) is intended to be a repository of high quality, reliable, and accessible information. For an article to be considered high quality, it should adhere to certain guidelines as posted here. Articles that do not sufficiently adhere to the guidelines should be tagged with the relevant markers, and may be deleted if they are not improved.
</p><p><br />
</p>
<h2><span class="mw-headline" id="URLs">URLs</span></h2>
<p>The first thing you need to do when adding new content is to decide the URL. Consult the <a href="/wiki/WPD:Content/Topic_Hierarchy" title="WPD:Content/Topic Hierarchy" class="mw-redirect"> Topic hierarchy</a> page to understand how content is organized and where your new page should live.
</p><p>Next, go to the <a href="/wiki/WPD:New_Page" title="WPD:New Page"> New Page</a> page to create your new page using one of the defined content page templates. When creating an article from the New Page page, bear in mind that what you enter in the path text box will be the URL for the new page, and that the URL need not be the visible page title. That is, a page whose URL is "eventsource_basics" can have an internal title of "Streaming updates with server-sent events". So keep URLs short, descriptive, and unique.
</p><p>A few guidelines:
</p>
<ul><li>Do not capitalize unless absolutely vital for syntax correctness. Thus, for an article about user media, you might enter "usermedia"; for an article specifically about the getUserMedia method, you might instead enter "getUserMedia".</li>
<li>Use blanks, not underscores, to separate words, as underscores are generated when the page is created. Thus for an article about the HTML5 audio tag, you might enter "audio tag"; the generated URL would be "audio_tag".</li>
<li>Do not use other punctuation, such as dashes or parentheses, in a URL. Really, don't.</li>
<li>Do not use articles (the, a, an) in URLs unless absolutely necessary.</li></ul>
<h2><span class="mw-headline" id="Article_titles">Article titles</span></h2>
<p>In the "Custom page title" form field, enter a descriptive title if it is different from the URL (it probably will be). 
</p><p>For clarity in both creating and reading, article types should be consistently titled, each according to its content's primary information type. Each article type should use a consistent titling scheme so that (a) the author can accurately place it in the information hierarchy and (b) the reader can infer its content type from the title without further reading.
</p><p>Please follow the following title conventions for at least these specific article types:
</p>
<ul><li> <b>Gerunds</b> for articles with tutorial, task, procedure, process, and similar content
<ul><li> Examples: "Using the &lt;audio&gt; tag", "Drawing on the canvas", "Interpreting getLocation() data" </li></ul></li>
<li> <b>Nouns</b> and <b>Noun phrases</b> for articles with reference, syntactical, validity, and similar content, and also for articles with concept, guide, and overview content. 
<ul><li> Examples: "&lt;audio&gt; tag attributes", "Valid .moveTo() values", "Latitude and longitude notation", "Introduction to Flexbox", "The history of the Web", "Information architecture basics"</li></ul></li></ul>
<p>Use capitals sparingly. Capitalize only the first word (sentence case); however, where the title includes an abbreviation, a proper name, or camel case, keep the capitalization. Some correct examples:
</p>
<ul><li>Style manual</li>
<li>The CSS layout model</li>
<li>Unicode characters in JavaScript files</li>
<li>Specifying fonts</li></ul>
<h2><span class="mw-headline" id="Article_summaries">Article summaries</span></h2>
<p>All articles should fill in the article summary field. The contents of this field should be no more than a paragraph long and succinctly describe the contents of the page (for API pages, generally what this piece of the API accomplishes). This summary will be automatically included in other pages that link to this page.
</p>
<h2><span class="mw-headline" id="Section_headings">Section headings</span></h2>
<p>Generally, follow the same guidelines as for article titles. Make your section headings brief but meaningful. Use sentence case. Again, you want the reader to know what is in the section without having to read the section. However, you may want to draw the reader into a section by making the section title enticing, something like "Web standards rock!" or "What is localStorage?"
</p>
<h2><span class="mw-headline" id="Grammar_and_spelling_conventions">Grammar and spelling conventions</span></h2>
<p>We follow the <a rel="nofollow" class="external text" href="http://styleguide.yahoo.com/">Yahoo style guide</a> for language styles. Refer to it when you have a spelling, gramatical, or other language query. Here are a few quick tips:
</p>
<ul><li> Please do not use contractions. For example say "I am" compared to "I'm".  This makes translation better and makes good legibility.</li></ul>
<h2><span class="mw-headline" id="Common_terms">Common terms</span></h2>
<ul><li> Use <i>Internet</i> when it is a proper noun, e.g., <b>The Internet</b>. Otherwise, use lower case, e.g., <b>Do you think internet marketing is a real degree?</b></li>
<li> Use <i>Web</i> when it is a proper noun, e.g., <b>The Web</b>. Otherwise, use lower case, e.g., <b>I think CSS is a web-related topic.</b></li>
<li> Use <i>website</i>, not <i>web site</i>. Strictly speaking, it is a two-word, adjective-noun combination, but common use today (including recent inclusion in the AP Stylebook) is to combine them into a single noun.</li></ul>
<h2><span class="mw-headline" id="Code_syntax_highlighting">Code syntax highlighting</span></h2>
<p>WPD uses the <a class="external text" href="http://www.mediawiki.org/wiki/Syntaxhighlight">SyntaxHighlight</a> GeSHi extension for syntax highlighting. Use the following guidelines for WPD articles.
</p>
<ul><li>Use <code>&lt;syntaxhighlight&gt;</code> only for standalone code blocks; for inline terms use the <code>&lt;code&gt;</code> tag (as used in this list item).</li>
<li>Specify the language for each code block in the opening tag: <code>&lt;syntaxhighlight lang="<i>language</i>"&gt;</code>. You can find a full list of supported languages in the  <a class="external text" href="http://www.mediawiki.org/wiki/Syntaxhighlight">Syntaxhighlight documentation</a>. </li>
<li><code>html5</code>, <code>css</code>, and <code>javascript</code> are the most common language notations you'll use. Note that using just <code>html</code> does not work; you must use either <code>html5</code> or <code>html4strict</code> to get proper highlighting.</li>
<li>Prefer <code>&lt;syntaxhighlight&gt;</code> blocks to <code>&lt;pre&gt;</code> blocks, and do not use them together in any case &#8212; the SyntaxHighlight extension handles all the formatting.</li>
<li>There is no need to escape entities like angle brackets inside your code block; Syntaxhighlight takes care of that as well.</li>
<li>Lines of code can be emphasized by providing a <code>highlight=""</code> attribute:
<ul><li><code>&lt;syntaxhighlight lang="<i>language</i>" highlight="3"&gt;</code><br />This highlights the third line in your code snippet.</li>
<li><code>&lt;syntaxhighlight lang="<i>language</i>" highlight="3-5"&gt;</code><br /><code>&lt;syntaxhighlight lang="<i>language</i>" highlight="1,4,8"&gt;</code><br />This highlights a range of lines or multiple lines specified one by one.</li>
<li><code>&lt;syntaxhighlight lang="<i>language</i>" highlight="1,4-6,9"&gt;</code><br />Multiple options can even be mixed together.</li></ul></li></ul>
<h2><span class="mw-headline" id="Images">Images</span></h2>
<p>When adding images to an article, you should think carefully about how big the image needs to be (e.g. 300 x 150), as well as how heavy the image is (e.g. file size in KB), and what the file name is. Also consider the accessibility of your images by adding alt text to describe them.
</p>
<ul>
  <li><p>Images should only be as large as required to display the content to be portrayed. To fit inside the content column on WPD, you should make them no larger than about 650 pixels wide. If an image absolutely needs to be much larger than this, you should display a thumbnail and then link it to a full size image somewhere else.</p></li>
  <li><p>Please do not try to load images of several MB to WPD! If an image is really large in file size you should shrink it down first. If the image is something not very detailed like a line drawing, save it as a PNG 8 (most graphics packages have this option in their export settings.) If it is a lot more detailed, such as a browser screenshot or photograph, use a JPEG — 70% quality is sufficient for web use. You might also want to consider using a compression application like [<a rel="nofollow" class="external text" href="http://pmt.sourceforge.net/pngcrush/">PNG Crush</a>].</p></li>
  <li><p>Images should be given an appropriate semantic filename, for example <b>box-shadow-output.jpg</b>, not <b>my-great-image.jpg</b> or <b>454654756-awesome.jpg</b>.</p></li>
  <li><p>To add alt text to images in Media Wiki, you use the option alt=my alt text. For example:</p>
<pre>[[Image:cssbasic.png|alt=Screenshot of the Opera browser showing an applied inline style sheet]]</pre>
<p>Maps to</p>
<pre>&lt;img src=&quot;cssbasic.png alt=&quot;Screenshot of the Opera browser showing an applied inline style sheet&quot;&gt;</pre>
</li>
</ul>
<h2><span class="mw-headline" id="Quality_principles">Quality principles</span></h2>
<p><a rel="nofollow" class="external text" href="http://www.amazon.com/Developing-Quality-Technical-Information-Handbook/dp/0131477498">Developing Quality Technical Information: A Handbook for Writers and Editors</a> defines the characteristics of quality in technical information as:
</p>
<ul><li> <b>easy to use</b>: task-oriented, accurate, complete</li>
<li> <b>easy to understand</b>: clear, concrete, appropriate style</li>
<li> <b>easy to find</b>: coherently organized, retrievable, visually effective</li></ul>
<p>The following principles are chosen to help achieve high quality in the information presented on this website.
</p>
<h3><span class="mw-headline" id="Free_of_spam">Free of spam</span></h3>
<p>Spam makes it hard for readers to find what they are looking for, and should be removed as soon as possible.
</p>
<h3><span class="mw-headline" id="Vendor_neutral">Vendor neutral</span></h3>
<p>Content should be vendor neutral whenever possible. Where browser implementations vary, provide compatibility information for major browsers, or describe equivalent functionality in major browsers.
</p>
<h3><span class="mw-headline" id="Neutral_voice">Neutral voice</span></h3>
<p>With the exception of tutorials and guides, content should maintain a neutral voice.  Because the site is a collaborative wiki, even tutorials and guides that begin with a specific voice can be expected to morph over time.
</p>
<h3><span class="mw-headline" id="Up_to_date">Up to date</span></h3>
<p>Content should include any new details that may be useful for web developers.
</p>
<h3><span class="mw-headline" id="Tagged_with_all_applicable_tags">Tagged with all applicable tags</span></h3>
<p>Tags help users of the site find content that is relevant to them, which means that having comprehensive and complete tagging is important. This includes tags that clearly denote its standardization progress and implementation status.
</p>
<h3><span class="mw-headline" id="Include_compatibility_information">Include compatibility information</span></h3>
<p>See <a href="/wiki/Template:Style_Compatibility_Issue" title="Template:Style Compatibility Issue">Compatibility</a> for a description of the best practices for formatting compatibility information.
</p>
<h3><span class="mw-headline" id="Complete_documentation_of_API">Complete documentation of API</span></h3>
<p>API reference pages should document the entirety of the API, as well as any quirks or edge cases that are important to know in practice.
</p>
<h3><span class="mw-headline" id="Address_relevant_best_practices">Address relevant best practices</span></h3>
<p>Authors are encouraged to address accessibility, internationalization, privacy, and security good practices.
</p>
<h3><span class="mw-headline" id="Include_examples_where_appropriate">Include examples where appropriate</span></h3>
<p>Examples help make articles more concrete and easier to understand.
</p>
<h3><span class="mw-headline" id="Follow_best_practices_for_sample_code">Follow best practices for sample code</span></h3>
<p>It is particularly important that samples and example code follow best practices (for example, including alt text for image tags), because example code is often copied by developers. In particular, be sure that sample code does not create security vulnerabilities.
</p>
<h3><span class="mw-headline" id="Include_citations_and_helpful_links">Include citations and helpful links</span></h3>
<p>Include references to applicable standards, test suites, implementation reports, live demos, and other useful resources.
</p>
<h3><span class="mw-headline" id="Accessible">Accessible</span></h3>
<p>Your content should be accessible according to WCAG 2.0 AA. Where there are questions about accessibility, contributors should seek reviews from community members with more experience. Materials uploaded by agents of a browser vendor should be accessible when posted; materials uploaded by unaffiliated community members should be clearly marked if they are not accessible. If reasonable steps are not taken to make content accessible after a reasonable amount of time, it may be removed from the site.
</p>
<h3><span class="mw-headline" id="Relevant_to_the_site">Relevant to the site</span></h3>
<p>Articles that are not relevant to the site's goals (as laid out in the <a href="/wiki/WPD:Pillars" title="WPD:Pillars" class="mw-redirect">Pillars</a> document) should not be included in the site.
</p>
<h3><span class="mw-headline" id="Omit_comments_and_discussion">Omit comments and discussion</span></h3>
<p>Relevant comments and discussion about the article should occur in the associated discussion page, not in the body of the article.
</p>
<h3><span class="mw-headline" id="Do_not_needlessly_duplicate_content">Do not needlessly duplicate content</span></h3>
<p>Separate pages should not substantially overlap content or topics, except when necessary to improve understanding and organization. 
</p>
<h3><span class="mw-headline" id="Search_engine_optimization">Search engine optimization</span></h3>
<p>Use the relevant keywords for an article in the summary, and where possible and natural throughout the article. However, write for humans more than search engines, so do not overload on keywords.
</p>
<h3><span class="mw-headline" id="Include_all_relevant_sections">Include all relevant sections</span></h3>
<p>Different <a href="/wiki/WPD:Manual_Of_Style/Article_Types" title="WPD:Manual Of Style/Article Types">types of articles</a> have different types of sections. For an article to be considered to be high quality, it should have all applicable sections.
</p>
<ul><li>Note: Further style discussions are taking place in the <a rel="nofollow" class="external text" href="http://www.w3.org/community/webed/wiki/Web_Education_community_group_style_guide">Web Education Community Group</a>.</li></ul>
<h3><span class="mw-headline" id="Use_accepted_wikitext_syntax_conventions">Use accepted wikitext syntax conventions</span></h3>
<p>WebPlatform Docs uses Semantic MediaWiki as its underlying engine, and has adopted certain conventions in the syntax that you should use when editing pages. This is the same wiki engine used by Wikipedia, and thus has the same basic coding characteristics. For general guidelines, see:
</p>
<ul><li> the <a rel="nofollow" class="external text" href="http://en.wikipedia.org/wiki/Wikipedia:Cheatsheet">Wikipedia Cheatsheet</a> or</li>
<li> the <a class="external text" href="http://www.mediawiki.org/wiki/Help:Formatting">MediaWiki formatting guide</a></li></ul>
<p>For help with some specific WPD coding issues, see:
</p>
<ul><li> <a href="/wiki/WPD:Style_Guide/Tables" title="WPD:Style Guide/Tables">Tables</a></li>
<li> <a href="/wiki/WPD:Style_Guide/Lists" title="WPD:Style Guide/Lists">Lists</a> </li>
<li> <a href="/wiki/WPD:Style_Guide/Gotchas" title="WPD:Style Guide/Gotchas">Common Gotchas for WPD editors</a></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.045 seconds
Real time usage: 0.047 seconds
Preprocessor visited node count: 130/1000000
Preprocessor generated node count: 160/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:14-0!*!0!!*!*!*!esi=1 and timestamp 20150731111049 and revision id 30135
 -->
