{{Page_Title|Step 5: Update existing content}}
{{Flags
|Checked_Out=No
}}
{{Summary_Section|This is Step 5 of the [[WPD:Editors_Guide|Editor's Guide]].}}
{{Basic Page}}
==Step 5. Update existing content==
===Become familiar with MediaWiki syntax conventions===

Review the syntax to [http://www.mediawiki.org/wiki/Help:Formatting format pages in the wiki].

Also see the [http://en.wikipedia.org/wiki/Wikipedia:Cheatsheet MediaWiki syntax cheat sheet] from Wikipedia.

For help with  specific coding issues, see:
* [[WPD:Style_Guide/Tables| Formatting tables]]
* [[WPD:Style_Guide/Lists| Formatting lists]] 
* [[WPD:Style_Guide/Gotchas|Common gotchas for editors]]

Check out the [[WPD:Manual_Of_Style/Sample_best_practices| Samples best practices page]] to see guidelines when authoring pages with code examples.

** [COMMENT:] Need to create a NEW Page for this Editor's Guide that contains a list of all valid tags and macros for WebPlatform.org. For example, using the tag &#60;subpages /&#62; to display a list of sub pages. Or find the link, if this page exists already.

===Follow the WebPlatform style guide===
WebPlatform.org is intended to be a repository of high quality, reliable, and accessible information. For an article to be considered high quality, it should adhere to the conventions outlined in this Editor's Guide. Articles that do not sufficiently adhere to the guidelines will be tagged with the relevant markers, and they may be deleted over time if they are not improved.

* WebPlatform.org uses the [http://styleguide.yahoo.com/ Yahoo Style Guide].

===Ensure articles have descriptive article titles===
After clicking the Edit button to access the editing interface, verify that there is a descriptive title in the Custom Page Title field. If not, enter a descriptive title that matches the content on the page. It is fine if the custom page title is different from the URL (it probably will be). 

See [[WPD:Getting_Started#Improve_titles|Improve titles]] for a list of articles that have the "Undescriptive Title" flag set.

Article types should be consistently titled, each according to its content's primary information type. Pages should use a consistent titling scheme so that the author can accurately position the content in the information hierarchy and visitors can infer the content type from the custom title without having to read the entire page.

Follow these title conventions for specific article types:
* Use gerunds (words ending in the -ing suffix) for articles with tutorial, task, procedure, and process content.
** Examples: 
*** Using the <audio> tag
*** Drawing on the canvas
*** Styling UI elements with CSS
*** Interpreting getLocation() data 
* Use nouns and noun phrases for articles with reference, syntactical, validity, and similar content, as well as concept, guide, and overview content. 
** Examples: 
*** <audio> tag attributes
*** Valid .moveTo() values
*** Introduction to Flexbox
*** The history of the Web

Use capitals sparingly. Capitalize only the first word (using sentence case). However, in situations when the title includes an abbreviation, a proper name, or camel case, the title should use the normal capitalization, like this:
*Style manual
*The CSS layout model
*Unicode characters in JavaScript files
*Resolving issues in Internet Explorer

===Enter helpful article summaries===
All articles should include a brief summary in the article summary field. The contents of this field should not exceed one paragraph and should succinctly describe the contents of the page (for API pages, describe the behavior and function of the specific API section). This summary text is automatically included in other pages that link to this page. Sometimes you can summarize an article based on its extant content; otherwise you may need to do some research.  

See [[WPD:Getting_Started#Fill_in_missing_summaries|Fill in missing summaries]] for a list of articles with the "Needs Summary" flag set.

===Update section headings to be descriptive and strong ===
Generally, follow the same guidelines for section headings as outlined for article titles. Make your section headings brief but meaningful. Use sentence case. The goal is to help the reader understand what is in the section without having to read the section. However, you can draw the reader into a section by making the section title enticing. Examples: 
*Web standards rock 
*Develop well-formed pages 
*Leveraging localStorage
*Populating attributes dynamically

See the [[WPD:Manual_Of_Style/Section_Guidelines | Section guidelines page]], which outlines the guidelines for specific sections of pages.

===Avoid using contractions===
* Please do not use contractions. For example, use the phrase: do not, instead of writing: don't. This ensures that pages can be translated accurately. It also makes pages easier to read if English is not a reader's primary language.

===Use standard US English spellings===
WebPlatform.org uses the general US English classification. Standardizing this type of spelling is useful because English words that appear in code syntax are also spelled in US English. Consistently spelling words in both syntax and other wording helps reduce confusion. When updating pages, ensure the content uses the US English spellings of words, like this:
*Color
*Customize
*Inquiry
Edit UK spellings that you find for colour, customise, enquiry, and other spelling variations.

If you are not sure of the correct spelling, use an online dictionary of American English such as [http://www.merriam-webster.com/ Merriam-Webster]. 

===Standardize common terms===
* Use ''Internet'' when it is a proper noun, such as: The Internet is a global system of interconnected computer networks. Otherwise, use lowercase, like this: Leverage internet marketing to drive site traffic.
* Use ''Web'' when it is a proper noun, such as: Surfing the Web. Otherwise, use lowercase, like this: CSS is a web-related topic.
* Spell ''website'' as one word, not ''web site''. Strictly speaking, it is a two word, adjective-noun combination, but the common use today (including the listing in the AP Stylebook) combines the words into a single noun.

===Use the appropriate syntax highlighting when displaying code===
WebPlatform uses the [http://www.mediawiki.org/wiki/Syntaxhighlight SyntaxHighlight] GeSHi extension for syntax highlighting. Use the following guidelines when authoring articles for this wiki:

*Use <code>&lt;syntaxhighlight&gt;</code> only for stand-alone code blocks; for inline terms use the <code>&lt;code&gt;</code> tag (as used in this list item).
*Specify the language for each code block in the opening tag: <code>&lt;syntaxhighlight lang="''language''"&gt;</code>. You can find a full list of supported languages in the  [http://www.mediawiki.org/wiki/Syntaxhighlight Syntaxhighlight documentation]. 
*The most common language notations you will use are <code>&lt;html5&gt;</code>, <code>&lt;css&gt;</code>, and <code>&lt;javascript&gt;</code>. Note that using just <code>&lt;html&gt;</code> does not work; you must use either <code>&lt;html5&gt;</code> or <code>&lt;html4strict&gt;</code> to display proper syntax highlighting.
*Prefer <code>&lt;syntaxhighlight&gt;</code> blocks to <code>&lt;pre&gt;</code> blocks, and do not use them together in any case &mdash; the SyntaxHighlight extension handles all the formatting.
*There is no need to escape entities like angle brackets inside your code block; Syntaxhighlight handles that as well.
*Lines of code can be emphasized by providing a <code>highlight=""</code> attribute.
**This highlights the third line in your code snippet:
***<code>&lt;syntaxhighlight lang="''language''" highlight="3"&gt;</code>
**This highlights a range of lines or multiple lines specified one by one:
***<code>&lt;syntaxhighlight lang="''language''" highlight="3-5"&gt;</code>
***<code>&lt;syntaxhighlight lang="''language''" highlight="1,4,8"&gt;</code>
**Multiple options can even be mixed together:
***<code>&lt;syntaxhighlight lang="''language''" highlight="1,4-6,9"&gt;</code>

===Add images to illustrate concepts===
Screenshots and illustrations greatly improve articles and pages posted on this wiki. See [[WPD:Editors_Guide/step_7_prepare_and_upload_assets_for_articles| Step 7 of the Editor's Guide]] to learn how to prepare and upload image files and other assets to complement articles. 

===Adhere to quality principles===
The book titled: [http://www.amazon.com/Developing-Quality-Technical-Information-Handbook/dp/0131477498 Developing Quality Technical Information: A Handbook for Writers and Editors] defines the characteristics of quality in technical information as:
* '''Easy to use''': Task oriented, accurate, and complete
* '''Easy to understand''': Clear, concrete, and appropriate style
* '''Easy to find''': Coherently organized, retrievable, and visually effective

The following principles guide our contributions to help achieve high quality in the information presented on this website.

===Ensure articles are vendor neutral===
Content should be vendor neutral whenever possible. Where browser implementations vary, provide compatibility information for major browsers, or describe equivalent functionality in all major browsers. For a list of articles marked with the '''Not Neutral''' flag, see [[WPD:Getting_Started#Edit_content_for_neutrality|Edit content for neutrality].

===Author content using a neutral voice===
With the exception of tutorials and guides, content should maintain a neutral voice.  Because the site is a collaborative wiki, even tutorials and guides that are first authored with a specific voice can be expected to morph over time.

===Present up-to-date information===
Content should include recent details for using the most modern browsers and the newest web technologies to help web developers build sites.

===Tag pages with all applicable tags===
Tagging pages helps users of the site find content that is relevant to them. A comprehensive and complete set of tags are important to improve discoverability of pages. When tagging, also include tags that clearly denote the content's standardization progress and implementation status.

See [[WPD:Editors_Guide/step_4_review_existing_content|Review existing content]] and [[WPD:Editors_Guide/step_6_author_or_upload_new_content#Topics_and_topic_clusters|Topics and topic clusters]] for guidance.

===Include compatibility information===
See [[WPD:Editors_Guide/step_6_author_or_upload_new_content| Step 6 of the Editor's Guide]] to learn best practices when providing compatibility information. Many existing pages are missing the compatibility details in the compatibility tables included with the templates. Researching online and updating compatibility tables, as well as flagging pages to mark issues, is a great way to get started contributing to this wiki.

'''Note:''' We anticipate automating the population of the compatibility tables in the near future, and we recommend against working on compatibility tables by hand.

===Provide complete documentation of API===
API reference pages should document the entirety of the API, as well as any quirks or edge cases that are important to know in real-world projects. For more information, see [[WPD:Creating_API_pages#Filling_in_the_pages|Creating API pages]].

===Address relevant best practices===
Address accessibility, internationalization, privacy, and security good practices in the articles you edit for this wiki.

===Include examples where appropriate===
Examples help make articles more concrete and easier to understand. For a list of articles that need examples, see [[WPD:Getting_Started#Develop_code_examples|Develop code examples]].

===Follow best practices for sample code===
It is particularly important that samples and example code follow best practices (for example, including alt text for image tags), because example code is often copied by developers. In particular, be sure that sample code does not create security vulnerabilities. See [[WPD:Manual_Of_Style/Code_sample_best_practices|Code sample best practices]]. For a list of articles where code samples may not follow best practices see [[WPD:Getting_Started#Fix_examples_not_following_best_practices|Fix examples not following best practices]]. 

===Add citations and helpful links===
Include references to applicable standards, test suites, implementation reports, live demos, and other useful resources.

===Author accessible pages===
Your content should be accessible according to WCAG 2.0 AA. If you have questions about accessibility, seek reviews from community members with more experience. Materials uploaded by agents of a browser vendor should be accessible when posted; materials uploaded by unaffiliated community members should be clearly marked if they aren’t accessible. If reasonable steps are not taken to make content accessible after a reasonable amount of time, it may be removed from the site.

===Publish content that is relevant to this wiki===
Articles that are not relevant to the site's goals (as laid out in the [[WPD:Pillars|Pillars]] document) should not be included in the site. If you are unsure, ask for advice on IRC, the mailing list, or the forum. See [[WPD:Editors_Guide/step_2_communicate_with_the_online_community| Step 2 of the Editor's Guide]] for more details.

===Omit comments and discussion===
Relevant comments and discussion about the article should occur in the associated discussion page, not in the body of the article.

===Avoid posting duplicate content===
Strive to ensure separate pages do not substantially overlap content or topics, except when necessary to improve understanding and organization. 

===Promote search engine optimization===
Use the relevant keywords for an article in the summary, and where possible and natural throughout the article. However, write for humans more than search engines; do not overload pages with keywords.

===Include all relevant sections===
* If you are editing tutorials and concept articles, follow the guidelines in the [[WPD:Content/Tutorials_and_concept_articles  | Tutorial and concept articles page]].
* If you are editing reference documentation, see the rules in the [[WPD:Content/Reference_articles | Reference articles page]].
* If you are updating API documentation, read the [[WPD:Creating_API_pages | Creating API documentation page]] to learn more.

Different types of articles have different types of sections. For an article to be considered to be high quality, it should include all applicable sections.

===Participate in the conversation about formatting and styling wiki pages===
*Note: Further style discussions are taking place in the [http://www.w3.org/community/webed/wiki/Web_Education_community_group_style_guide Web Education Community Group].
{{Notes_Section}}
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}