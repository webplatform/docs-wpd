{{Page_Title|Step 5: Update existing content}}
{{Flags}}
{{Summary_Section|This is Step 5 of the [[WPD:Editors_Guide|Editor's Guide]].}}
{{Basic Page}}

==Step 5. Update existing content==
===Become familiar with MediaWiki syntax conventions===

Review the syntax to [http://www.mediawiki.org/wiki/Help:Formatting| format pages in the wiki].

Also see the [http://en.wikipedia.org/wiki/Wikipedia:Cheatsheet MediaWiki syntax cheat sheet] from Wikipedia.

For help with  specific coding issues, see:
* [[WPD:Style_Guide/Tables| Formatting tables]]
* [[WPD:Style_Guide/Lists| Formatting lists]] 
* [[WPD:Style_Guide/Gotchas|Common gotchas for editors]]

Check out the [[WPD:Manual_Of_Style/Sample_best_practices| Samples best practices page]] to see guidelines when authoring pages with code examples.

** [COMMENT:] Create a NEW Page that explains how we use the MediaWiki syntax that contains a list of all valid tags and macros for WebPlatform.org. For example, using the tag &#60;subpages /&#62; to display list of sub pages.

===Follow the WebPlatform style guide===
WebPlatform.org is intended to be a repository of high quality, reliable, and accessible information. For an article to be considered high quality, it should adhere to certain guidelines as posted here. Articles that do not sufficiently adhere to the guidelines should be tagged with the relevant markers, and may be deleted if they are not improved.

* WebPlatform.org uses the [http://styleguide.yahoo.com/ Yahoo Style Guide] 

===Create valid URLs for new pages===
The first thing you need to do when creating new content is to choose an appropriate page URL. Consult the [[WPD:Content/Topic_Hierarchy | Topic hierarchy page]] to understand how content is organized and where your new page should be saved.

Next, go to the [[WPD:New_Page | New Page page]] to create a new page using one of the defined content page templates. When creating an article from the New Page page, bear in mind that the text you enter in the path text box will become the URL for the new page, and that the URL need not match the visible page title. For example, a page with the URL: "eventsource_basics" can have an internal title: "Streaming updates with server-sent events". The goal is to keep URLs short, descriptive, and unique.

A few guidelines:
*Do not capitalize unless absolutely vital for syntax correctness. Thus, for an article about user media, you might enter "usermedia"; for an article specifically about the getUserMedia method, you might instead enter "getUserMedia".
*Use blanks, not underscores, to separate words, as underscores are generated when the page is created. Thus for an article about the HTML5 audio tag, you might enter "audio tag"; the generated URL would be "audio_tag".
*Do not use other punctuation, such as dashes or parentheses, in a URL. Really, do not - because punctuation in URLs causes site issues.
*Do not use articles (the, a, an) in URLs unless absolutely necessary.

===Add descriptive article titles===
In the "Custom page title" form field, enter a descriptive title if it is different from the URL (it probably will be). 

For clarity in both creating and reading, article types should be consistently titled, each according to its content's primary information type. Each article type should use a consistent titling scheme so that (a) the author can accurately place it in the information hierarchy and (b) the reader can infer its content type from the title without further reading.

Please follow the following title conventions for at least these specific article types:
* '''Gerunds''' for articles with tutorial, task, procedure, process, and similar content
** Examples: "Using the <audio> tag", "Drawing on the canvas", "Interpreting getLocation() data" 
* '''Nouns''' and '''Noun phrases''' for articles with reference, syntactical, validity, and similar content, and also for articles with concept, guide, and overview content. 
** Examples: "<audio> tag attributes", "Valid .moveTo() values", "Latitude and longitude notation", "Introduction to Flexbox", "The history of the Web", "Information architecture basics"

Use capitals sparingly. Capitalize only the first word (sentence case); however, where the title includes an abbreviation, a proper name, or camel case, keep the capitalization. Some correct examples:
*Style manual
*The CSS layout model
*Unicode characters in JavaScript files
*Specifying fonts

===Enter helpful article summaries===
All articles should fill in the article summary field. The contents of this field should be no more than a paragraph long and succinctly describe the contents of the page (for API pages, generally what this piece of the API accomplishes). This summary will be automatically included in other pages that link to this page.

===Use descriptive section headings===
Generally, follow the same guidelines as for article titles. Make your section headings brief but meaningful. Use sentence case. Again, you want the reader to know what's in the section without having to read the section. However, you may want to draw the reader into a section by making the section title enticing, something like "Web standards rock" or "What is localStorage?"

See the [[WPD:Manual_Of_Style/Section_Guidelines | Section guidelines page]], which outlines the guidelines for specific sections of pages.

===Avoid using contractions===
* Please do not use contractions. For example say "I am" compared to "I'm".  This ensures that pages are translated more accurately and makes all pages easier to read.

===Standardize common terms===
* Use Internet when it is a proper noun, such as: The Internet is a global system of interconnected computer networks. Otherwise, use lower case, like this: Leverage internet marketing to drive site traffic.
* Use Web when it is a proper noun, such as, Surfing the Web. Otherwise, use lower case, like this: CSS is a web-related topic.
* Use website spelled as one word, not web site. Strictly speaking, it is a two word, adjective-noun combination, but common use today (including the listing in the AP Stylebook) is to combine the words into a single noun.

===Use the appropriate syntax highlighting when displaying code===
WebPlatform uses the [http://www.mediawiki.org/wiki/Syntaxhighlight SyntaxHighlight] GeSHi extension for syntax highlighting. Use the following guidelines when authoring articles for this wiki:

*Use <code>&lt;syntaxhighlight&gt;</code> only for stand-alone code blocks; for inline terms use the <code>&lt;code&gt;</code> tag (as used in this list item).
*Specify the language for each code block in the opening tag: <code>&lt;syntaxhighlight lang="''language''"&gt;</code>. You can find a full list of supported languages in the  [http://www.mediawiki.org/wiki/Syntaxhighlight Syntaxhighlight documentation]. 
*<code>html5</code>, <code>css</code>, and <code>javascript</code> are the most common language notations you'll use. Note that using just <code>html</code> does not work; you must use either <code>html5</code> or <code>html4strict</code> to get proper highlighting.
*Prefer <code>&lt;syntaxhighlight&gt;</code> blocks to <code>&lt;pre&gt;</code> blocks, and do not use them together in any case&mdash;the SyntaxHighlight extension handles all the formatting.
*There is no need to escape entities like angle brackets inside your code block; Syntaxhighlight takes care of that as well.
*Lines of code can be emphasized by providing a <code>highlight=""</code> attribute:
**<code>&lt;syntaxhighlight lang="''language''" highlight="3"&gt;</code><br>This highlights the third line in your code snippet.
**<code>&lt;syntaxhighlight lang="''language''" highlight="3-5"&gt;</code><br><code>&lt;syntaxhighlight lang="''language''" highlight="1,4,8"&gt;</code><br>This highlights a range of lines or multiple lines specified one by one.
**<code>&lt;syntaxhighlight lang="''language''" highlight="1,4-6,9"&gt;</code><br>Multiple options can even be mixed together.

===Add images to illustrate concepts===

Screenshots and illustrations greatly improve articles and pages posted on this wiki. See Step 7 of the Editor's Guide to learn how to prepare and upload image files and other assets. 

===Quality principles===
[http://www.amazon.com/Developing-Quality-Technical-Information-Handbook/dp/0131477498 Developing Quality Technical Information: A Handbook for Writers and Editors] defines the characteristics of quality in technical information as:
* '''Easy to use''': task oriented, accurate, complete
* '''Easy to understand''': clear, concrete, appropriate style
* '''Easy to find''': coherently organized, retrievable, visually effective

The following principles are chosen to help achieve high quality in the information presented on this website.

===Free of spam===
Spam makes it hard for readers to find what they are looking for, and should be removed as soon as possible.

===Vendor neutral===
Content should be vendor neutral whenever possible. Where browser implementations vary, provide compatibility information for major browsers, or describe equivalent functionality in major browsers.

===Neutral voice===
With the exception of tutorials and guides, content should maintain a neutral voice.  Because the site is a collaborative wiki, even tutorials and guides that begin with a specific voice can be expected to morph over time.

===Up to date===
Content should include any new details that may be useful for web developers.

===Tagged with all applicable tags===
Tags help users of the site find content that is relevant to them, which means that having comprehensive and complete tagging is important. This includes tags that clearly denote its standardization progress and implementation status.

===Include compatibility information===
See [[Template:Style Compatibility Issue|Compatibility]] for a description of the best practices for formatting compatibility information.

===Complete documentation of API===
API reference pages should document the entirety of the API, as well as any quirks or edge cases that are important to know in practice.

===Address relevant best practices===
Authors are encouraged to address accessibility, internationalization, privacy, and security good practices.

===Include examples where appropriate===
Examples help make articles more concrete and easier to understand.

===Follow best practices for sample code===
It is particularly important that samples and example code follow best practices (for example, including alt text for image tags), because example code is often copied by developers. In particular, be sure that sample code does not create security vulnerabilities.

===Include citations and helpful links===
Include references to applicable standards, test suites, implementation reports, live demos, and other useful resources.

===Accessible===
Your content should be accessible according to WCAG 2.0 AA. Where there are questions about accessibility, contributors should seek reviews from community members with more experience. Materials uploaded by agents of a browser vendor should be accessible when posted; materials uploaded by unaffiliated community members should be clearly marked if they aren’t accessible. If reasonable steps are not taken to make content accessible after a reasonable amount of time, it may be removed from the site.

===Relevant to the site===
Articles that are not relevant to the site's goals (as laid out in the [[WPD:Pillars|Pillars]] document) should not be included in the site.

===Omit comments and discussion===
Relevant comments and discussion about the article should occur in the associated discussion page, not in the body of the article.

===Avoid posting duplicate content===
Strive to ensure separate pages do not substantially overlap content or topics, except when necessary to improve understanding and organization. 

===Search engine optimization===
Use the relevant keywords for an article in the summary, and where possible and natural throughout the article. However, write for humans more than search engines; do not overload pages with keywords.

===Include all relevant sections===
Different [[WPD:Manual Of Style/Article Types|types of articles]] have different types of sections. For an article to be considered to be high quality, it should have all applicable sections.

*Note: Further style discussions are taking place in the [http://www.w3.org/community/webed/wiki/Web_Education_community_group_style_guide Web Education Community Group].