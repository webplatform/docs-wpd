{{Page_Title|Step 5: 기존에 작성된 콘텐츠를 수정하기}}
{{Flags
|Checked_Out=Yes
}}
{{Summary_Section|이것은 [[WPD:Editors_Guide|편집자 가이드]] Step 5입니다.}}
{{Basic Page}}
==Step 5. 기존에 작성된 콘텐츠를 수정하기==
===미디어위키 문법 배우기===

[http://www.mediawiki.org/wiki/Help:위키의 페이지 포맷에 대한] 문법을 검토해 주세요.

위키피디아의 [http://en.wikipedia.org/wiki/Wikipedia:Cheatsheet 미디어 위키 문법 치트 시트]도 확인해 주세요.

특정 코딩 이슈에 도움을 위한 항목은 아래와 같습니다:
* [[WPD:Style_Guide/Tables|표 형식]]
* [[WPD:Style_Guide/Lists|목록 형식]] 
* [[WPD:Style_Guide/Gotchas|편집자에게 많이 발생하는 문제점]]

코드 예제와 함께 작성하는 경우 [[WPD:Manual_Of_Style/Sample_best_practices| 예제 모범 사례 페이지]]를 확인 해 주세요.

** [COMMENT:] WebPlatform.org에서 모든 유효한 태그와 매크로 목록을 포함하는 편집자 가이드를 위한  새 페이지를 만드는 것이 필요합니다. 예를 들어 하위 페이지 목록을 보여주기 위해 &#60;subpages /&#62; 태그를 사용하는 것 입니다. 또는 이 페이지가 이미 존재하는 경우 해당 링크를 찾는 것입니다.

===스타일 가이드라인을 따르기===
WebPlatform.org는 고품질, 높은 신뢰도 , 접근 가능한 정보의 레파지토리가 되는 것을 의도하고 있습니다. 고품질로 작성 되기 위한 글은 편집자 가이드의 규칙을 준수해야 합니다. 충분하게 지침을 준수하지 않는 글은 관련 마커로 태그 될 것이며 개선되비 못할 경우 시간이 지남에 따라 삭제 될 것입니다.

* WebPlatform.org는  [http://styleguide.yahoo.com/ Yahoo 스타일 가이드]를 사용합니다..

===글에는 설명 글 제목이 있는지 확인해 주세요.===
편집 인터페이스로 진입하기 위해 Edit버튼을 클릭한 후에는 페이지 제목 필드에 설명 글 제목을 확인해 주세요. 없는 경우 페이지의 내용과 일치하는 설명 제목을 입력해 주세요. 사용자 정의 페이지 제목이 URL과 다른 경우는 괜찮습니다.

"Undescriptive Title" 플래그가 지정된 글 목록을 위해[[WPD:Getting_Started#Improve_titles|제목 개선하기]]를 확인해 주세요.

글 타입은 각각의 콘텐츠 주요 정보 타입에 따라 일관된 제목이 주어져야 한다. 저자가 정확하게 정보 계층 구조에 콘텐트를 배치하고 방문자가 전체페이지를 읽을 필요없이 사용자 지정 제목에서 콘텐트 타입을 유츄할 수 있도록 페이지에 일관된 제목 스키마를 사용해야 합니다.

특정 글 타입을 위해 제목 컨벤션을 따라 주세요.
* 튜토리얼, 작업, 절차, 프로세스 컨텐트 글을 위해 동명사(-ing 로 끝나는 단어)를 사용해 주세요.
** 예제:: 
*** Using the <audio> tag (<audio> 태그 사용하기)
*** Drawing on the canvas (canvas에 그리기)
*** Styling UI elements with CSS (CSS를 이용하여 UI element 스타일링하기)
*** Interpreting getLocation() data (getLocation() 데이터 해석하기)
* 참고, 문법, 유효성 그리고 비슷한 콘텐트 뿐만 아니라 컨셉트, 가이드, 콘텐트 오버뷰 글에는 명사/명사구를 사용해 주세요.
** 예제: 
*** <audio> tag attributes (<audio> 태그 속성)
*** Valid .moveTo() values (moveTo() 값 유효성)
*** Introduction to Flexbox (Flexbox 소개)
*** The history of the Web (Web의 역사)

대문자는 제한적으로 사용하세요. 대문자는 단어의 첫글자에만 사용하세요.(문장의 경우) 그러나 제목이 약어, 적절한 이름 또는 camel case("CamelCase" 같이 띄어쓰기 없이 단어의 시작을 대문자로 하는것) 를 포함 하고 있는 경우라면 제목은 아래와 같이 대문자가 사용되어야 한다.:
*Style manual
*The CSS layout model
*Unicode characters in JavaScript files
*Resolving issues in Internet Explorer

===도움이 되는 문서 요약을 입력하기===
모든 문서는 문서 요약 필드에 간단한 요약을 포함 해야만 합니다. 이필드의 콘텐츠는 한 단락을 초과하지 말아야 하며 페이지의 콘텐츠를 간결하게 설명해야 합니다. (API 페이지의 경우 특정 API섹션의 동작 및 기능을 설명합니다.) 이 요약 텍스트는 이 페이지가 다른 페이지에 링크되는 경우 자동적으로 포함됩니다. 때때로 여러분은 현존하는 콘텐츠에 기초한 글을 요약 할수 있습니다. 그렇지 않으면 여러분은 몇가지 연구를 해야할 필요가 있습니다.  

"Needs Summary" 플래그가 지정된 글들의 목록을 위해 [[WPD:Getting_Started#Fill_in_missing_summaries|누락된 요약 채우기]]를 확인하세요.

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
*The most common language notations you will use are <code>html5</code>, <code>css</code>, and <code>javascript</code>. Note that using just <code>html</code> does not work; you must use either <code>html5</code> or <code>html4strict</code> to display proper syntax highlighting.
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