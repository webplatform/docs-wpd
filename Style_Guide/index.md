=WPD style guide=
WebPlatform Docs (WPD) is intended to be a repository of high quality, reliable, and accessible information. For an article to be considered high quality, it should adhere to certain guidelines as posted here. Articles that do not sufficiently adhere to the guidelines should be tagged with the relevant markers, and may be deleted if they are not improved.

<!--You might also be interested in the [[WPD:Manual_Of_Style/Section_Guidelines | Section guidelines]] page, which outlines the guidelines for specific sections of pages.-->

==URLs==
When creating an article from the [http://docs.webplatform.org/wiki/WPD:New_Page new page page], bear in mind that what you enter in the path text box will be the URL for the new page, and that the URL need not be the visible page title. That is, a page whose URL is "eventsource_basics" can have an internal title of "Streaming updates with server-sent events". So keep URLs short, descriptive, and unique.

A couple of guidelines:
*Do not capitalize unless absolutely vital for syntax correctness. Thus, for an article about user media, you might enter "usermedia"; for an article specifically about the getUserMedia method, you might instead enter "getUserMedia".
*Use blanks, not underscores, to separate words, as underscores are generated when the page is created. Thus for an article about the HTLM5 audio tag, you might enter "audio tag"; the generated URL would be "audio_tag".
*Do not use other punctuation, such as dashes or parentheses, in a URL. Just don't.
*Do not use articles (the, a, an) in titles unless absolutely necessary.

==Article titles==
In the "Custom page title" form field, enter a descriptive title if it's different from the URL (it probably will be). 

For clarity in both creating and reading, article types should be consistently titled, each according to its content's primary information type. Most content can be assigned one of three information types: '''task''', '''concept''', or '''reference'''. Each article type should use a consistent titling scheme so that (a) the author can accurately place it in the information hierarchy and (b) the reader can infer its content type from the title without further reading.

Please follow the following title conventions for at least these specific article types:
* '''Gerunds''' for articles with tutorial, task, procedure, process, and similar content
** Examples: "Using the <audio> tag", "Drawing on the canvas", "Interpreting getLocation() data" 
* '''Nouns''' and '''Noun phrases''' for articles with reference, syntactical, validity, and similar content, and also for articles with concept, guide, and overview content. 
** Examples: "<audio> tag attributes", "Valid .moveTo() values", "Latitude and longitude notation", "Introduction to Flexbox", "The history of the Web", "Information architecture basics"

Use capitals sparingly. Capitalize only the first word ("sentence case"); however, where the title includes an abbreviation, a proper name, or camel case, keep the capitalization for those. Some correct examples:
*Style manual
*The CSS layout model
*Unicode characters in JavaScript files
*Specifying fonts

==Section headings==
Generally, follow the same guidelines as for article titles. Make your section headings brief but meaningful. Again, you want the reader to know what's in the section without having to read the section. However, you may want to draw the reader into a section by making the section title enticing, something like "Web standards rock" or "What is localStorage?"

==Grammar and spelling conventions==
We follow the [http://styleguide.yahoo.com/ Yahoo style guide] for language styles. Refer to it when you have a spelling, gramatical, or other language query.

== Common usages ==
* Use ''Internet'' when used as a proper noun, e.g., '''The Internet'''. Otherwise, use lower case, e.g., '''Do you think internet marketing is a real degree?'''
* Use ''Web'' when used as a proper noun, e.g., '''The Web'''. Otherwise, use lower case, e.g., '''I think CSS is a web-related topic.'''
* Use ''website'', not ''web site''. Strictly speaking, it's an adjective-noun combination, but common use today (including recent inclusion in the AP Stylebook) is to combine them into a single noun.

=Code syntax highlight coloring=

WPD uses the SyntaxHighlight GeSHi extension for syntax highlighting. You can find more detailed usage instructions at http://www.mediawiki.org/wiki/Syntaxhighlight. The following points should help you do what you need to do most of the time.

<ol>
<li><p>We don't want code terms inside paragraphs colored, just code blocks.</p></li>
<li><p>You have to enclose each code block in <code>&lt;syntaxhighlight lang="language"&gt; ... &lt;/syntaxhighlight&gt;</code>, where "language" is the type of language you are highlighting.</p></li>
<li><p>The type of language has to be one of the supported languages (http://www.mediawiki.org/wiki/Syntaxhighlight#Supported_languages), so <code>html5</code>, <code>css</code> and <code>javascript</code> are the most common we'll use. Note that just <code>html</code> doesn't work. It has to be <code>html5</code> or <code>html4strict</code>.</p></li>
<li><p>If your code block is inside <code>&lt;pre&gt;&lt;/pre&gt;</code> tags already, remove those - the SyntaxHighlight extension creates those for you.</p></li>
<li><p>If you are escaping things like angle brackets inside your code block, you'll need to put them back in as <, >, etc. Syntaxhighlight seems to escape them for you.</p></li>
</ol>

=Quality principles=
[http://www.amazon.com/Developing-Quality-Technical-Information-Handbook/dp/0131477498 Developing Quality Technical Information: A Handbook for Writers and Editors] defines the characteristics of quality in technical information as:
* '''easy to use''': task oriented, accurate, complete
* '''easy to understand''': clear, concrete, appropriate style
* '''easy to find''': coherently organized, retrievable, visually effective

The following principles are chosen help achieve high quality in the information presented on this website.

==Free of spam==
Spam makes it hard for readers of the site to find what they’re looking for, and should be removed as soon as possible.

==Vendor neutral==
Content should be vendor neutral whenever possible. Where browser implementations vary, provide compatibility information for major browsers, or describe equivalent functionality in major browsers.

==Neutral voice==
With the exception of tutorials and guides, content should maintain a neutral voice.  Because the site is a collaborative wiki, even tutorials and guides that begin with a specific voice can be expected to morph over time.

==Up to date==
Content should include any new details that may be useful for web developers.

==Tagged with all applicable tags==
Tags help users of the site find content that is relevant to them, which means that having comprehensive and complete tagging is important. This includes tags that clearly denote its standardization progress and implementation status.

==Include compatibility information==
See [[Template:Style Compatibility Issue|Compatibility]] &lt;Sub-Page&gt; for a description of the best practices for formatting compatibility information.

==Complete documentation of API==
API reference pages should document the entirety of the API, as well as any quirks or edge cases that are important to know in practice.  Relevant standards should be

==Address relevant best practices==
Authors are encouraged to address accessibility, internationalization, privacy, and security good practices.

==Include examples where appropriate==
Examples help make APIs more concrete and easier to understand.

==Follow all best practices for sample code==
It is particularly important that samples and example code follow best practices (for instance, accessibility best practices regarding the use of alt text for image tags within samples), because example code is often copied by developers. Therefore, in particular, be sure that sample code does not create security vulnerabilities.

==Include citations and helpful links==
Include references to applicable standards, test suites, implementation reports, and other useful resources.

==Accessible==
The content should be accessible according to WCAG 2.0 AA. Where there are questions about accessibility, contributors should seek review from community members with more experience. Materials uploaded by agents of a browser vendor should be accessible when posted; materials uploaded by unaffiliated community members should be clearly marked if they aren’t accessible. If reasonable steps are not taken to make such material accessible after a reasonable amount of time, it may be removed from the site.

==Relevant to the site==
Articles that are not relevant to the site's goals (as laid out in the [[WPD:Pillars|Pillars]]) should not be included in the site.

==Leave comments and discussion out==
Relevant comments and discussion about the page should occur in the associated discussion page.

==Doesn't needlessly duplicate content==
Separate pages shouldn't substantially overlap content or topics except when necessary to improve understanding and organization. 

==Search engine optimization==
Use the relevant keywords for an article in the summary, and where possible and natural throughout the article. However, write for humans more than search engines, so don't overload on keywords.

==Includes all relevant sections==
Different [[WPD:Manual Of Style/Article Types|types of articles]] have different types of sections. For an article to be considered to be high quality, it should have all applicable sections.

==Sections Follow Style Guidelines==
Different sections have [[WPD:Manual Of Style/Section Guidelines|different style guidelines]]. Each section of the article should follow all of the applicable style guidelines.

''Note: Further manual of style discussions are taking place in the [http://www.w3.org/community/webed/wiki/Web_Education_community_group_style_guide Web Education Community Group].''

==Use accepted wikitext syntax conventions==
WebPlatform Docs uses Semantic MediaWiki as its underlying engine, and has adopted certain conventions in the syntax, which everyone should use when editing pages:

* [[WPD:Manual_Of_Style/Tables|Tables]]
* [[WPD:Manual_Of_Style/Links|Links]]
* [[WPD:Manual_Of_Style/Code Examples|Code Examples]]
* [[WPD:Manual_Of_Style/Gotchas|Common Gotchas for WPD editors]]