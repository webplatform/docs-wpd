---
title: Step 5: Update existing content
notes:
  - 'Need to create a NEW Page for this Editor''s Guide that contains a list of all valid tags and macros for WebPlatform.org. For example, using the tag splist (et al.) to display a list of sub pages, find a link, if this page exists already.'
readiness: 'Out of Date'
summary: 'MediaWiki syntax and the Web Platform style guide.'
tags:
  - Basic
  - Pages
uri: 'WPD:Editors Guide/step 5 update existing content'

---
## Summary

MediaWiki syntax and the Web Platform style guide.

### Become familiar with MediaWiki syntax conventions

Review the syntax to [format pages in the wiki](http://www.mediawiki.org/wiki/Help:Formatting).

Also see the [MediaWiki syntax cheat sheet](http://en.wikipedia.org/wiki/Wikipedia:Cheatsheet) from Wikipedia.

For help with specific coding issues, see:

-   [Formatting tables](/WPD:Style_Guide/Tables)
-   [Formatting lists](/WPD:Style_Guide/Lists)
-   [Common gotchas for editors](/WPD:Style_Guide/Gotchas)

Check out the [Samples best practices page](/WPD:Manual_Of_Style/Sample_best_practices) to see guidelines when authoring pages with code examples.

### Follow the WebPlatform style guide

WebPlatform.org is intended to be a repository of high quality, reliable, and accessible information. For an article to be considered high quality, it should adhere to the conventions outlined in this Editor's Guide. Articles that do not sufficiently adhere to the guidelines will be tagged with the relevant markers, and they may be deleted over time if they are not improved.

### Ensure articles have descriptive article titles

After clicking the Edit button to access the editing interface, verify that there is a descriptive title in the Custom Page Title field. If not, enter a descriptive title that matches the content on the page. It is fine if the custom page title is different from the URL (it probably will be).

See [Improve titles](/WPD:Getting_Started#Improve_titles) for a list of articles that have the "Undescriptive Title" flag set.

Article types should be consistently titled, each according to its content's primary information type. Pages should use a consistent titling scheme so that the author can accurately position the content in the information hierarchy and visitors can infer the content type from the custom title without having to read the entire page.

Follow these title conventions for specific article types:

-   Use gerunds (words ending in the -ing suffix) for articles with tutorial, task, procedure, and process content.
    -   Examples:
        -   Using the `<audio>` tag
        -   Drawing on the canvas
        -   Styling UI elements with CSS
        -   Interpreting getLocation() data
-   Use nouns and noun phrases for articles with reference, syntactical, validity, and similar content, as well as concept, guide, and overview content.
    -   Examples:
        -   \<audio\> tag attributes
        -   Valid .moveTo() values
        -   Introduction to Flexbox
        -   The history of the Web

Use capitals sparingly. Capitalize only the first word (using sentence case). However, in situations when the title includes an abbreviation, a proper name, or camel case, the title should use the normal capitalization, like this:

-   Style manual
-   The CSS layout model
-   Unicode characters in JavaScript files
-   Resolving issues in Internet Explorer

### Enter helpful article summaries

All articles should include a brief summary in the article summary field. The contents of this field should not exceed one paragraph and should succinctly describe the contents of the page (for API pages, describe the behavior and function of the specific API section). This summary text is automatically included in other pages that link to this page. Sometimes you can summarize an article based on its extant content; otherwise you may need to do some research.

See [Fill in missing summaries](/WPD:Getting_Started#Fill_in_missing_summaries) for a list of articles with the "Needs Summary" flag set.

### Update section headings to be descriptive and strong

Generally, follow the same guidelines for section headings as outlined for article titles. Make your section headings brief but meaningful. Use sentence case. The goal is to help the reader understand what is in the section without having to read the section. However, you can draw the reader into a section by making the section title enticing. Examples:

-   Web standards rock
-   Develop well-formed pages
-   Leveraging localStorage
-   Populating attributes dynamically

See the [Section guidelines page](/WPD:Manual_Of_Style/Section_Guidelines), which outlines the guidelines for specific sections of pages.

### Avoid using contractions

-   Please do not use contractions. For example, use the phrase: do not, instead of writing: don't. This ensures that pages can be translated accurately. It also makes pages easier to read if English is not a reader's primary language.

### Use standard US English spellings

WebPlatform.org uses the general US English classification. Standardizing this type of spelling is useful because English words that appear in code syntax are also spelled in US English. Consistently spelling words in both syntax and other wording helps reduce confusion. When updating pages, ensure the content uses the US English spellings of words, like this:

-   Color
-   Customize
-   Inquiry

Edit UK spellings that you find for colour, customise, enquiry, and other spelling variations.

If you are not sure of the correct spelling, use an online dictionary of American English such as [Merriam-Webster](http://www.merriam-webster.com/).

### Standardize common terms

-   Use *Internet* when it is a proper noun, such as: The Internet is a global system of interconnected computer networks. Otherwise, use lowercase, like this: Leverage internet marketing to drive site traffic.
-   Use *Web* when it is a proper noun, such as: Surfing the Web. Otherwise, use lowercase, like this: CSS is a web-related topic.
-   Spell *website* as one word, not *web site*. Strictly speaking, it is a two word, adjective-noun combination, but the common use today (including the listing in the AP Stylebook) combines the words into a single noun.

### Use the appropriate syntax highlighting when displaying code

WebPlatform uses the [SyntaxHighlight](http://www.mediawiki.org/wiki/Syntaxhighlight) GeSHi extension for syntax highlighting. Use the following guidelines when authoring articles for this wiki:

-   Use `<syntaxhighlight>` only for stand-alone code blocks; for inline terms use the `<code>` tag (as used in this list item).
-   Specify the language for each code block in the opening tag: `<syntaxhighlight lang="language">`. You can find a full list of supported languages in the [Syntaxhighlight documentation](http://www.mediawiki.org/wiki/Syntaxhighlight).
-   The most common language notations you will use are `html5`, `css`, and `javascript`. Note that using just `html` does not work; you must use either `html5` or `html4strict` to display proper syntax highlighting.
-   Prefer `<syntaxhighlight>` blocks to `<pre>` blocks, and do not use them together in any case — the SyntaxHighlight extension handles all the formatting.
-   There is no need to escape entities like angle brackets inside your code block; Syntaxhighlight handles that as well.
-   Lines of code can be emphasized by providing a `highlight=""` attribute.
    -   This highlights the third line in your code snippet:
        -   `<syntaxhighlight lang="language" highlight="3">`
    -   This highlights a range of lines or multiple lines specified one by one:
        -   `<syntaxhighlight lang="language" highlight="3-5">`
        -   `<syntaxhighlight lang="language" highlight="1,4,8">`
    -   Multiple options can even be mixed together:
        -   `<syntaxhighlight lang="language" highlight="1,4-6,9">`

### Add images to illustrate concepts

Screenshots and illustrations greatly improve articles and pages posted on this wiki. See [Step 7 of the Editor's Guide](/WPD:Editors_Guide/step_7_prepare_and_upload_assets_for_articles) to learn how to prepare and upload image files and other assets to complement articles.

### Adhere to quality principles

The book titled: [Developing Quality Technical Information: A Handbook for Writers and Editors](http://www.amazon.com/Developing-Quality-Technical-Information-Handbook/dp/0131477498) defines the characteristics of quality in technical information as:

-   **Easy to use**: Task oriented, accurate, and complete
-   **Easy to understand**: Clear, concrete, and appropriate style
-   **Easy to find**: Coherently organized, retrievable, and visually effective

The following principles guide our contributions to help achieve high quality in the information presented on this website.

### Ensure articles are vendor neutral

Content should be vendor neutral whenever possible. Where browser implementations vary, provide compatibility information for major browsers, or describe equivalent functionality in all major browsers. For a list of articles marked with the **Not Neutral** flag, see [Edit content for neutrality](/WPD:Getting_Started#Edit_content_for_neutrality).

### Author content using a neutral voice

With the exception of tutorials and guides, content should maintain a neutral voice. Because the site is a collaborative wiki, even tutorials and guides that are first authored with a specific voice can be expected to morph over time.

### Present up-to-date information

Content should include recent details for using the most modern browsers and the newest web technologies to help web developers build sites.

### Tag pages with all applicable tags

Tagging pages helps users of the site find content that is relevant to them. A comprehensive and complete set of tags are important to improve discoverability of pages. When tagging, also include tags that clearly denote the content's standardization progress and implementation status.

See [Review existing content](/WPD:Editors_Guide/step_4_review_existing_content) and [Topics and topic clusters](/WPD:Editors_Guide/step_6_author_or_upload_new_content#Topics_and_topic_clusters) for guidance.

### Include compatibility information

See [Step 6 of the Editor's Guide](/WPD:Editors_Guide/step_6_author_or_upload_new_content) to learn best practices when providing compatibility information. Many existing pages are missing the compatibility details in the compatibility tables included with the templates. Researching online and updating compatibility tables, as well as flagging pages to mark issues, is a great way to get started contributing to this wiki.

**Note:** We anticipate automating the population of the compatibility tables in the near future, and we recommend against working on compatibility tables by hand.

### Provide complete documentation of API

API reference pages should document the entirety of the API, as well as any quirks or edge cases that are important to know in real-world projects. For more information, see [Creating API pages](/WPD:Creating_API_pages#Filling_in_the_pages).

### Address relevant best practices

Address accessibility, internationalization, privacy, and security good practices in the articles you edit for this wiki.

### Include examples where appropriate

Examples help make articles more concrete and easier to understand. For a list of articles that need examples, see [Develop code examples](/WPD:Getting_Started#Develop_code_examples).

### Follow best practices for sample code

It is particularly important that samples and example code follow best practices (for example, including alt text for image tags), because example code is often copied by developers. In particular, be sure that sample code does not create security vulnerabilities. See [Code sample best practices](/WPD:Manual_Of_Style/Code_sample_best_practices). For a list of articles where code samples may not follow best practices see [Fix examples not following best practices](/WPD:Getting_Started#Fix_examples_not_following_best_practices).

### Add citations and helpful links

Include references to applicable standards, test suites, implementation reports, live demos, and other useful resources.

### Author accessible pages

Your content should be accessible according to WCAG 2.0 AA. If you have questions about accessibility, seek reviews from community members with more experience. Materials uploaded by agents of a browser vendor should be accessible when posted; materials uploaded by unaffiliated community members should be clearly marked if they aren’t accessible. If reasonable steps are not taken to make content accessible after a reasonable amount of time, it may be removed from the site.

### Publish content that is relevant to this wiki

Articles that are not relevant to the site's goals (as laid out in the [Pillars](/WPD:Pillars) document) should not be included in the site. If you are unsure, ask for advice on IRC, the mailing list, or the forum. See [Step 2 of the Editor's Guide](/WPD:Editors_Guide/step_2_communicate_with_the_online_community) for more details.

### Omit comments and discussion

Relevant comments and discussion about the article should occur in the associated discussion page, not in the body of the article.

### Avoid posting duplicate content

Strive to ensure separate pages do not substantially overlap content or topics, except when necessary to improve understanding and organization.

### Promote search engine optimization

Use the relevant keywords for an article in the summary, and where possible and natural throughout the article. However, write for humans more than search engines; do not overload pages with keywords.

### Include all relevant sections

-   If you are editing tutorials and concept articles, follow the guidelines in the [Tutorial and concept articles page](/WPD:Content/Tutorials_and_concept_articles).
-   If you are editing reference documentation, see the rules in the [Reference articles page](/WPD:Content/Reference_articles).
-   If you are updating API documentation, read the [Creating API documentation page](/WPD:Creating_API_pages) to learn more.

Different types of articles have different types of sections. For an article to be considered to be high quality, it should include all applicable sections.

### Participate in the conversation about formatting and styling wiki pages

-   Note: Further style discussions are taking place in the [Web Education Community Group](http://www.w3.org/community/webed/wiki/Web_Education_community_group_style_guide).

### Blogging guidelines

To contribute to the WPD blog efforts, please see the [Blogging](/WPD:Blogging) topic.

