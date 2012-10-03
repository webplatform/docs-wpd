For an article to be considered high quality, it should adhere to all of the following guidelines. Those that do not should be tagged with the relevant banners, and may be deleted.

You might also be interested in the [[WPD:Manual_Of_Style/Section_Guidelines | Section guidelines]] page, which outlines the guidelines for specific sections of pages.

=Capitalization=
Use capitals sparingly. Where the instance includes an abbreviation, a proper name, or camel case, keep the capitalization for those.

;Page titles
: Capitalize only the first word.
: Example: '''Style manual''' (in other words, don't use this page as an example).
: Example: '''The CSS layout model'''. 
;Section headings
: Capitalize only the first word.
: Example: '''Titles and headings''' (see below).
: Example: '''Unicode characters in JavaScript files'''.
: Example: '''Action: specifying fonts'''.
;URLs
: Do not capitalize unless completely vital for syntax correctness.
: Example: '''tutorials/audio_tag''' (the underscore is generated for you &mdash; you would enter '''tutorials/audio tag''').
: Example: '''tutorials/using_getUserMedia''' (the underscore is generated for you &mdash; you would enter '''tutorials/using getUserMedia''').

=Titles and headings=

==Choose descriptive titles==
Choose useful titles (e.g., the name of a feature being documented).

Titles are part of the URL structure, and so should follow certain rules:
* Titles should be as short as possible. Leave out any articles that aren't completely necessary (e.g., ''the'', ''an'', ''a'')
* Only capitalize when absolutely necessary, such as for technical terms, like ''getElementById''
* Use minimal punctuation; for methods, do not use parens (''( )'') 
* Separate words with a space ('' ''), which MediaWiki will convert to an underscore (''_''); only use hyphens or dashes (''–'') when they are part of a word
* When creating a subpage, avoid duplicating the parent title in the current title if at all possible, especially for long words.

In the case where these rules make it difficult to make a descriptive coherent title, such as for a tutorial, the ''title'' field should be a minimally reduced version, and the real title should be given as a subtitle.

==Article naming conventions==
For clarity in both creating and reading, article types should be consistently titled at the primary heading level, each according to its content's primary information type. Most content can be assigned one of three information types: '''task''', '''concept''', or '''reference'''. Each article type should use a consistent titling scheme so that the author can accurately place it in the information hierarchy and so that the reader can infer its content type from the title without further reading.

Please follow the following title conventions for specific article types:
* '''Gerunds''' for articles with tutorial, task, procedure, process, and similar content
** Examples: "Using the <audio> tag", "Drawing on the canvas", "Using getLocation data" 
* '''Nouns''' and '''Noun phrases''' for articles with reference, syntactical, validity, and similar content, and articles with concept, guide, background or overview content. Essentially, concept/guide articles are a reference of sorts, although more introductory and less terse.
** Reference examples: "<audio> tag attributes", "Valid .moveTo values", "Latitude and longitude notation"
** Examples: "Introduction to Flexbox", "The history of the Web", "Information architecture"

==Section headings==
As much as possible, use short sentences for heading titles, with minimal punctuation and articles, but the rules for titles do not necessarily apply to section headings. Avoid asking questions in section headings.

==Title casing==

You should capitalise the first word of each title, but not every word. So '''Web standards rock''', but not '''Web Standards Rock'''

=Grammar and spelling conventions=
We follow the [http://styleguide.yahoo.com/ Yahoo style guide] for language styles. Refer to it when you have a spelling, gramatical, or other language query.

== Common usages ==

* ''Internet'', not ''internet'', when used as a proper noun, e.g. '''The Internet'''. Otherwise, use lower case, e.g. '''Do you think internet marketing is a real degree?'''
* ''Web'', not ''web'', when used as a proper noun, e.g. '''The Web'''. Otherwise, use lower case, e.g. '''I think CSS is a web-related topic'''
* ''website'', not ''web site''

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
It is particularly important that samples and example code follow best practices (for instance, accessibility best practices regarding the use of alt text for image tags within samples), because example code is often copied by developers.

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