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

===정확히 설명될 수 있도록 섹션 제목을 업데이트 하기===
일반적으로 글의 제목에 대한 설명으로 섹션 제목에 대해 동일한 지침을 따르세요.  여러분의 섹션 제목은 짧고 의미가 있어야 합니다. 문장을 사용하게요. 목표는 독자가 섹션을 읽지 않고도 섹션 안의 내용을 이해할수 있도록 도움을 주는 것입니다. 그러나 여러분은 섹션 제목으로 유혹하여 독자를 섹션으로 끌어들일 수 있습니다.
예제: 
*Web standards rock 
*Develop well-formed pages 
*Leveraging localStorage
*Populating attributes dynamically

페이지의 특정 섹션에 대한 지침을 설명하는 [[WPD:Manual_Of_Style/Section_Guidelines | 섹션 지침 페이지]]를 확인 해 주세요.

===줄임말을 사용하지 마세요.===
* 줄임말을 사용하지 마세요. 예를 들면 don't를 사용하는 대신 do not을 사용하세요. 이것은 페이지가 정확히 번역될수 있도록 합니다. 또한 영어가 주언어가 아닌 독자들에게 읽히기 더 쉽도록 합니다.

===표준 미국식 영어 맞춤법을 사용하세요.===
WebPlatform.org는 일반 미국식 영어 분류를 사용합니다. 코드 문법에서도 미국식 영어 철자법을 사용하여 나타내기 때문에 철자 유형을 표준화 하는데 유용합니다. 문법과 다른 표현 모두에서 일관된 단어의 사용은 혼돈을 줄일 수 있습니다. 페이지를 업데이트 할때 콘텐츠가 아래와 같은 미국식 영어 철자법을 사용하였는지 확인하세요.
*Color
*Customize
*Inquiry
여러분은 colour, customise, enquiry 그리고 다른 철자법을 사용한 영국식 단어들을 찾아 수정하세요.

여러분이 올바른 철자법인지 확신할 수 없다면 [http://www.merriam-webster.com/ Merriam-Webster]와 같은 미국식 영어의 온라인 사전을 이용하세요.

===일반적인 용어를 표준화 하세요.===
* Internet은 상호 연결된 컴퓨터 네트워크의 글로벌 시스템입니다 와 같이 고유 명사로 사용된 때에는 "Internet"이라고 사용하세요. internet 마케팅은 사이트 트래픽을 유도 할 수 있습니다. 와 같은 경우에는 소문자를 사용하세요.
* Web 탐색하기 와 같이 고유명사로 사용된 경우 "Web"이라고 사용하세요. CSS는 web 관련 주제입니다와 같은 경우는 소문자를 사용하세요.
* "website"는 "web site"와 같이 쓰지 않고 한 단어("website")로 사용하세요. 엄밀하게 보면 형용사-명사의 두 단어이지만 오늘날 일반적으로 단어들이 연결되어 하나의 명사로 사용됩니다. (AP Stylebook 상의 목록에 포함되어 있습니다.)

===코드를 나타낼때 적절한 구문 강조를 사용하세요.===
WebPlatform은 구문 강조를 위해 GeSHi [http://www.mediawiki.org/wiki/Syntaxhighlight 구문강조]를 사용합니다. 이 위키의 문서 저작시 지침을 따라 사용하세요.

* <code>&lt;syntaxhighlight&gt;</code>는 인라인 문구가 <code>&lt;code&gt;</code>를 사용하기 위해 독립 실행 형 전용 코드 블록에 사용하세요. (이 문장에 사용된 것과 같이...)
* 여는 태그에서 <code>&lt;syntaxhighlight lang="''language''"&gt;</code>와 같이 각 코드 블록에 대한 언어를 지정해 주세요. 여러분은 [http://www.mediawiki.org/wiki/Syntaxhighlight 구문 강조 문서]에서 지원되는 언어의 모든 목록을 찾을 수 있습니다.
* 대부분의 일반적인 언어는 <code>html5</code>, <code>css</code>, 그리고 <code>javascript</code>와 같이 사용됩니다. <code>html</code>는 사용되지 않으며 적절한 구문 강조를 표현하기 위해 <code>html5</code> 또는  <code>html4strict</code>를 사용해야 합니다.
* <code>&lt;pre&gt;</code>블록보다 <code>&lt;syntaxhighlight&gt;</code>를 선호하세요. 어떤 경우에도 그들을 함께 사용하지 마세요. - SyntaxHighlight 확장은 모든 서식을 처리합니다.
* 코드 블록내의 괄호와 같은 요소를 회피 처리 할 필요가 없습니다. Syntaxhighlight가 잘 처리합니다.
* 코드 행은 <code>highlight=""</code> 속성을 제공하여 강조 할 수 있습니다.
** 이것은 여러분의 코드에서 세번째 라인을 강조합니다:
***<code>&lt;syntaxhighlight lang="''language''" highlight="3"&gt;</code>
** 라인 범위 지정 또는 여러 라인의 강조는 개별적 지정하여 강조합니다.:
***<code>&lt;syntaxhighlight lang="''language''" highlight="3-5"&gt;</code>
***<code>&lt;syntaxhighlight lang="''language''" highlight="1,4,8"&gt;</code>
** 여러 개의 옵션을 함께 혼합하여 사용할 수 있습니다.:
***<code>&lt;syntaxhighlight lang="''language''" highlight="1,4-6,9"&gt;</code>

===개념을 설명하기 위해 이미지를 추가하기===
스크린 샷과 이미지는 위키에 등록된 글과 페이지를 비약적으로 향상 시킵니다. 글을 보완하기 위해 이미지 파일 및 기타 리소스(assets)를  준비하고  업로드 하는 방법을 배우기 위해 [[WPD:Editors_Guide/step_7_prepare_and_upload_assets_for_articles| 편집자 가이드 Step 7]] 을 살펴보세요. 

===품질 원칙을 준수하기===
[http://www.amazon.com/Developing-Quality-Technical-Information-Handbook/dp/0131477498 고품길 기술 정보 개발 : 작가와 편집자를 위한 핸드북] 이라는 제목의 책은 다음과 같은 기술적 정보 품질의 특성을 정의합니다.:
* ""사용하기 쉽게 하세요"" : 업무 중심으로 정확하고 완벽하게.
* ""이해하기 쉽게 하세요"" : 명확하고 구체적이며 적절한 스타일.
* ""찾기 쉽게 하세요"" : 일관적인 구성, 검색 가능한 구성, 시각적인 효과 

다음과 같은 원칙이 웹사이트에서 제공되는 정보에 높은 품질을 달성 할 수 있도록 우리의 기여를 안내합니다.

===글은 벤더(vendor) 중립성을 가져야 합니다.===
콘텐트는 가능한 벤더(vendor) 중립적이어야 합니다. 브라우저 별 구현이 다를 경우 주요 브라우저에 대한 호환성 정보를 제공하거나 모든 주요 브라우저에서의 동일한 기능을 설명하세요. ""Not Neutral"" 플래그가 달린 글들의 목록을 위해 [[WPD:Getting_Started#Edit_content_for_neutrality|중립성에 대한 편집 내용]을 확인 해 주세요.

===중립적인 의견을 사용하는 작성자 콘텐트===
튜토리얼과 가이드를 제외한 콘텐트는 중립적인 의견을 유지해야 합니다. 공동 위키이기 때문에 최초 특정 의견으로 작성된 튜토리얼과 가이드라 할지라도 시간이 지남에 따라 중립적인 의견으로 변화될 것으로 예상 할 수 있습니다.

===최신의 정보를 제공===
콘텐트는 웹 개발자가 사이트를 구축하는데 도움이 되는 가장 현대적인 브라우저와 새로운 웹 기술을 사용하기 위한 최근의 세부사항을 포함해야 합니다.

===모든 적용 가능한 태그들로 페이지를 태그해 주세요.===
페이지에 태깅하는 것은 사이트의 이용자가 그들과 관련이 있는 컨텐트를 찾는데 도움을 줍니다. 포괄적이고 완전한 세트의 태그들은 페이지의 검색 기능을 향상 시키기 위해 중요합니다. 태깅을 할때는 명확하게 콘텐츠의 표준화 진행 및 구현 상태를 나타내는 태그를 포함합니다.

[[WPD:Editors_Guide/step_4_review_existing_content|기존에 작성된 콘텐츠 검토하기 ]] 와 [[WPD:Editors_Guide/step_6_author_or_upload_new_content#Topics_and_topic_clusters|토픽과 토픽 클러스터]]를 참고하세요.

===호환성 정보를 포함하세요.===
호환성 정보를 제공하는 모범 사례를 배우기 위해 [[WPD:Editors_Guide/step_6_author_or_upload_new_content| 편집자 가이드 Step 6]]을 확인 하세요. 기존의 많은 페이지들은 템플릿 상에 포함된 호환성 표의 호환성 세부사항을 누락하였습니다. 온라인을 연구하고 호환성 표를 업데이트 하는것 뿐만 아니라 이슈를 표시하기 위해 페이지에 플래그를 설정하는 것도 이 위키에 기여하기 시작하는 훌륭한 방법입니다.

'''Note:''' 우리는 가까운 장래에 호환성 표의 모집단을 자동화 할것으로 예상하며 우리는 수작업으로 호환성 표를 작업하는 것을 추천합니다.

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