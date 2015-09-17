---
title: 'Step 5: 기존에 작성된 콘텐츠를 수정하기'
lang: ko
summary: '이것은 편집자 가이드 Step 5입니다.'
tags:
  - Basic
  - Pages
uri: 'WPD:Editors Guide/step 5 update existing content/ko'

---
## Summary

이것은 편집자 가이드 Step 5입니다.

## Step 5. 기존에 작성된 콘텐츠를 수정하기

### 미디어위키 문법 배우기

[페이지 포맷에 대한](http://www.mediawiki.org/wiki/Help:위키의) 문법을 검토해 주세요.

위키피디아의 [미디어 위키 문법 치트 시트](http://en.wikipedia.org/wiki/Wikipedia:Cheatsheet)도 확인해 주세요.

특정 코딩 이슈에 도움을 위한 항목은 아래와 같습니다:

-   [표 형식](/WPD:Style_Guide/Tables)
-   [목록 형식](/WPD:Style_Guide/Lists)
-   [편집자에게 많이 발생하는 문제점](/WPD:Style_Guide/Gotchas)

코드 예제와 함께 작성하는 경우 [예제 모범 사례 페이지](/WPD:Manual_Of_Style/Sample_best_practices)를 확인 해 주세요.

-   -   [COMMENT:] WebPlatform.org에서 모든 유효한 태그와 매크로 목록을 포함하는 편집자 가이드를 위한 새 페이지를 만드는 것이 필요합니다. 예를 들어 하위 페이지 목록을 보여주기 위해 \<subpages /\> 태그를 사용하는 것 입니다. 또는 이 페이지가 이미 존재하는 경우 해당 링크를 찾는 것입니다.

### 스타일 가이드라인을 따르기

WebPlatform.org는 고품질, 높은 신뢰도 , 접근 가능한 정보의 레파지토리가 되는 것을 의도하고 있습니다. 고품질로 작성 되기 위한 글은 편집자 가이드의 규칙을 준수해야 합니다. 충분하게 지침을 준수하지 않는 글은 관련 마커로 태그 될 것이며 개선되비 못할 경우 시간이 지남에 따라 삭제 될 것입니다.

-   WebPlatform.org는 [Yahoo 스타일 가이드](http://styleguide.yahoo.com/)를 사용합니다..

### 글에는 설명 글 제목이 있는지 확인해 주세요.

편집 인터페이스로 진입하기 위해 Edit버튼을 클릭한 후에는 페이지 제목 필드에 설명 글 제목을 확인해 주세요. 없는 경우 페이지의 내용과 일치하는 설명 제목을 입력해 주세요. 사용자 정의 페이지 제목이 URL과 다른 경우는 괜찮습니다.

"Undescriptive Title" 플래그가 지정된 글 목록을 위해[제목 개선하기](/WPD:Getting_Started#Improve_titles)를 확인해 주세요.

글 타입은 각각의 콘텐츠 주요 정보 타입에 따라 일관된 제목이 주어져야 한다. 저자가 정확하게 정보 계층 구조에 콘텐트를 배치하고 방문자가 전체페이지를 읽을 필요없이 사용자 지정 제목에서 콘텐트 타입을 유츄할 수 있도록 페이지에 일관된 제목 스키마를 사용해야 합니다.

특정 글 타입을 위해 제목 컨벤션을 따라 주세요.

-   튜토리얼, 작업, 절차, 프로세스 컨텐트 글을 위해 동명사(-ing 로 끝나는 단어)를 사용해 주세요.
    -   예제::
        -   Using the \<audio\> tag (\<audio\> 태그 사용하기)
        -   Drawing on the canvas (canvas에 그리기)
        -   Styling UI elements with CSS (CSS를 이용하여 UI element 스타일링하기)
        -   Interpreting getLocation() data (getLocation() 데이터 해석하기)
-   참고, 문법, 유효성 그리고 비슷한 콘텐트 뿐만 아니라 컨셉트, 가이드, 콘텐트 오버뷰 글에는 명사/명사구를 사용해 주세요.
    -   예제:
        -   \<audio\> tag attributes (\<audio\> 태그 속성)
        -   Valid .moveTo() values (moveTo() 값 유효성)
        -   Introduction to Flexbox (Flexbox 소개)
        -   The history of the Web (Web의 역사)

대문자는 제한적으로 사용하세요. 대문자는 단어의 첫글자에만 사용하세요.(문장의 경우) 그러나 제목이 약어, 적절한 이름 또는 camel case("CamelCase" 같이 띄어쓰기 없이 단어의 시작을 대문자로 하는것) 를 포함 하고 있는 경우라면 제목은 아래와 같이 대문자가 사용되어야 한다.:

-   Style manual
-   The CSS layout model
-   Unicode characters in JavaScript files
-   Resolving issues in Internet Explorer

### 도움이 되는 문서 요약을 입력하기

모든 문서는 문서 요약 필드에 간단한 요약을 포함 해야만 합니다. 이필드의 콘텐츠는 한 단락을 초과하지 말아야 하며 페이지의 콘텐츠를 간결하게 설명해야 합니다. (API 페이지의 경우 특정 API섹션의 동작 및 기능을 설명합니다.) 이 요약 텍스트는 이 페이지가 다른 페이지에 링크되는 경우 자동적으로 포함됩니다. 때때로 여러분은 현존하는 콘텐츠에 기초한 글을 요약 할수 있습니다. 그렇지 않으면 여러분은 몇가지 연구를 해야할 필요가 있습니다.

"Needs Summary" 플래그가 지정된 글들의 목록을 위해 [누락된 요약 채우기](/WPD:Getting_Started#Fill_in_missing_summaries)를 확인하세요.

### 정확히 설명될 수 있도록 섹션 제목을 업데이트 하기

일반적으로 글의 제목에 대한 설명으로 섹션 제목에 대해 동일한 지침을 따르세요. 여러분의 섹션 제목은 짧고 의미가 있어야 합니다. 문장을 사용하게요. 목표는 독자가 섹션을 읽지 않고도 섹션 안의 내용을 이해할수 있도록 도움을 주는 것입니다. 그러나 여러분은 섹션 제목으로 유혹하여 독자를 섹션으로 끌어들일 수 있습니다. 예제:

-   Web standards rock
-   Develop well-formed pages
-   Leveraging localStorage
-   Populating attributes dynamically

페이지의 특정 섹션에 대한 지침을 설명하는 [섹션 지침 페이지](/WPD:Manual_Of_Style/Section_Guidelines)를 확인 해 주세요.

### 줄임말을 사용하지 마세요.

-   줄임말을 사용하지 마세요. 예를 들면 don't를 사용하는 대신 do not을 사용하세요. 이것은 페이지가 정확히 번역될수 있도록 합니다. 또한 영어가 주언어가 아닌 독자들에게 읽히기 더 쉽도록 합니다.

### 표준 미국식 영어 맞춤법을 사용하세요.

WebPlatform.org는 일반 미국식 영어 분류를 사용합니다. 코드 문법에서도 미국식 영어 철자법을 사용하여 나타내기 때문에 철자 유형을 표준화 하는데 유용합니다. 문법과 다른 표현 모두에서 일관된 단어의 사용은 혼돈을 줄일 수 있습니다. 페이지를 업데이트 할때 콘텐츠가 아래와 같은 미국식 영어 철자법을 사용하였는지 확인하세요.

-   Color
-   Customize
-   Inquiry

여러분은 colour, customise, enquiry 그리고 다른 철자법을 사용한 영국식 단어들을 찾아 수정하세요.

여러분이 올바른 철자법인지 확신할 수 없다면 [Merriam-Webster](http://www.merriam-webster.com/)와 같은 미국식 영어의 온라인 사전을 이용하세요.

### 일반적인 용어를 표준화 하세요.

-   Internet은 상호 연결된 컴퓨터 네트워크의 글로벌 시스템입니다 와 같이 고유 명사로 사용된 때에는 "Internet"이라고 사용하세요. internet 마케팅은 사이트 트래픽을 유도 할 수 있습니다. 와 같은 경우에는 소문자를 사용하세요.
-   Web 탐색하기 와 같이 고유명사로 사용된 경우 "Web"이라고 사용하세요. CSS는 web 관련 주제입니다와 같은 경우는 소문자를 사용하세요.
-   "website"는 "web site"와 같이 쓰지 않고 한 단어("website")로 사용하세요. 엄밀하게 보면 형용사-명사의 두 단어이지만 오늘날 일반적으로 단어들이 연결되어 하나의 명사로 사용됩니다. (AP Stylebook 상의 목록에 포함되어 있습니다.)

### 코드를 나타낼때 적절한 구문 강조를 사용하세요.

WebPlatform은 구문 강조를 위해 GeSHi [구문강조](http://www.mediawiki.org/wiki/Syntaxhighlight)를 사용합니다. 이 위키의 문서 저작시 지침을 따라 사용하세요.

-   `<syntaxhighlight>`는 인라인 문구가 `<code>`를 사용하기 위해 독립 실행 형 전용 코드 블록에 사용하세요. (이 문장에 사용된 것과 같이...)
-   여는 태그에서 `<syntaxhighlight lang="language">`와 같이 각 코드 블록에 대한 언어를 지정해 주세요. 여러분은 [구문 강조 문서](http://www.mediawiki.org/wiki/Syntaxhighlight)에서 지원되는 언어의 모든 목록을 찾을 수 있습니다.
-   대부분의 일반적인 언어는 `html5`, `css`, 그리고 `javascript`와 같이 사용됩니다. `html`는 사용되지 않으며 적절한 구문 강조를 표현하기 위해 `html5` 또는 `html4strict`를 사용해야 합니다.
-   `<pre>`블록보다 `<syntaxhighlight>`를 선호하세요. 어떤 경우에도 그들을 함께 사용하지 마세요. - SyntaxHighlight 확장은 모든 서식을 처리합니다.
-   코드 블록내의 괄호와 같은 요소를 회피 처리 할 필요가 없습니다. Syntaxhighlight가 잘 처리합니다.
-   코드 행은 `highlight=""` 속성을 제공하여 강조 할 수 있습니다.
    -   이것은 여러분의 코드에서 세번째 라인을 강조합니다:
        -   `<syntaxhighlight lang="language" highlight="3">`
    -   라인 범위 지정 또는 여러 라인의 강조는 개별적 지정하여 강조합니다.:
        -   `<syntaxhighlight lang="language" highlight="3-5">`
        -   `<syntaxhighlight lang="language" highlight="1,4,8">`
    -   여러 개의 옵션을 함께 혼합하여 사용할 수 있습니다.:
        -   `<syntaxhighlight lang="language" highlight="1,4-6,9">`

### 개념을 설명하기 위해 이미지를 추가하기

스크린 샷과 이미지는 위키에 등록된 글과 페이지를 비약적으로 향상 시킵니다. 글을 보완하기 위해 이미지 파일 및 기타 리소스(assets)를 준비하고 업로드 하는 방법을 배우기 위해 [편집자 가이드 Step 7](/WPD:Editors_Guide/step_7_prepare_and_upload_assets_for_articles) 을 살펴보세요.

### 품질 원칙을 준수하기

[고품질 기술 정보 개발 : 작가와 편집자를 위한 핸드북](http://www.amazon.com/Developing-Quality-Technical-Information-Handbook/dp/0131477498) 이라는 제목의 책은 다음과 같은 기술적 정보 품질의 특성을 정의합니다.:

-   ""사용하기 쉽게 하세요"" : 업무 중심으로 정확하고 완벽하게.
-   ""이해하기 쉽게 하세요"" : 명확하고 구체적이며 적절한 스타일.
-   ""찾기 쉽게 하세요"" : 일관적인 구성, 검색 가능한 구성, 시각적인 효과

다음과 같은 원칙이 웹사이트에서 제공되는 정보에 높은 품질을 달성 할 수 있도록 우리의 기여를 안내합니다.

### 글은 벤더(vendor) 중립성을 가져야 합니다.

콘텐트는 가능한 벤더(vendor) 중립적이어야 합니다. 브라우저 별 구현이 다를 경우 주요 브라우저에 대한 호환성 정보를 제공하거나 모든 주요 브라우저에서의 동일한 기능을 설명하세요. ""Not Neutral"" 플래그가 달린 글들의 목록을 위해 [[WPD:Getting\_Started\#Edit\_content\_for\_neutrality|중립성에 대한 편집 내용]을 확인 해 주세요.

### 중립적인 의견을 사용하는 작성자 콘텐트

튜토리얼과 가이드를 제외한 콘텐트는 중립적인 의견을 유지해야 합니다. 공동 위키이기 때문에 최초 특정 의견으로 작성된 튜토리얼과 가이드라 할지라도 시간이 지남에 따라 중립적인 의견으로 변화될 것으로 예상 할 수 있습니다.

### 최신의 정보를 제공

콘텐트는 웹 개발자가 사이트를 구축하는데 도움이 되는 가장 현대적인 브라우저와 새로운 웹 기술을 사용하기 위한 최근의 세부사항을 포함해야 합니다.

### 모든 적용 가능한 태그들로 페이지를 태그해 주세요.

페이지에 태깅하는 것은 사이트의 이용자가 그들과 관련이 있는 컨텐트를 찾는데 도움을 줍니다. 포괄적이고 완전한 세트의 태그들은 페이지의 검색 기능을 향상 시키기 위해 중요합니다. 태깅을 할때는 명확하게 콘텐츠의 표준화 진행 및 구현 상태를 나타내는 태그를 포함합니다.

[기존에 작성된 콘텐츠 검토하기](/WPD:Editors_Guide/step_4_review_existing_content/ko) 와 [토픽과 토픽 클러스터](/WPD:Editors_Guide/step_6_author_or_upload_new_content/ko#.ED.86.A0.ED.94.BD.EA.B3.BC_.ED.86.A0.ED.94.BD_.ED.81.B4.EB.9F.AC.EC.8A.A4.ED.84.B0)를 참고하세요.

### 호환성 정보를 포함하세요.

호환성 정보를 제공하는 모범 사례를 배우기 위해 [편집자 가이드 Step 6](/WPD:Editors_Guide/step_6_author_or_upload_new_content/ko)을 확인 하세요. 기존의 많은 페이지들은 템플릿 상에 포함된 호환성 표의 호환성 세부사항을 누락하였습니다. 온라인을 연구하고 호환성 표를 업데이트 하는것 뿐만 아니라 이슈를 표시하기 위해 페이지에 플래그를 설정하는 것도 이 위키에 기여하기 시작하는 훌륭한 방법입니다.

**Note:** 우리는 가까운 장래에 호환성 표의 모집단을 자동화 할것으로 예상하며 우리는 수작업으로 호환성 표를 작업하는 것을 추천합니다.

### API의 완전한 문서를 제공하기

API 참조 페이지들은 API 전체 뿐만 아니라 실제 프로젝트에서 알아야 할 중요한 단점이나 주변 케이스들도 문서화 해야 합니다. 추가 정보는 [API 페이지 만들기](/WPD:Creating_API_pages#Filling_in_the_pages)를 확인 해 주세요.

### 관련 모범 사례를 해결하기

글에서 접근성, 국제화(다국어 처리), 개인정보보호 및 보안상의 우수 사례를 이 여러분이 위키에 작성해 주세요.

### 적절한 예제를 포함하기

예제들은 기사를 더 구체적으로 쉽게 이해할 수 있도록 도와줍니다. 예제가 필요한 글들의 목록은 [코드 예제 개발하기](/WPD:Getting_Started#Develop_code_examples)을 참고하세요.

### 샘플 코드 모범 사례를 따르기

예제 코드는 종종 개발자들에 의해 복사되기 때문에 샘플과 예제 코드들이 모범 사례를 따르는 것은 특히 중요합니다. (예를 들어 alt 텍스트가 포함된 이미지 태그들) 특히, 샘플 코드가 보안 취약성을 만들지 않는지 확인해 주세요. [코드 예제 모범 사례](/WPD:Manual_Of_Style/Code_sample_best_practices)를 확인해 주세요. 코드 예제가 모범 사례를 따르지 않는 글들의 목록은 [모범 사례를 따르지 않는 예제 수정하기](/WPD:Getting_Started#Fix_examples_not_following_best_practices)에서 확인해 주세요.

### 인용과 도움이 되는 링크 추가하기

적용가능한 표준들, 테스트 시트, 구현 레포트, 라이브 데모 그리고 유용한 리소스를 참조하는 것을 포함합니다.

### 저자가 접근가능한 페이지들

여러분의 컨텐츠는 WCAG 2.0 AA에 따라 접근 가능해야 합니다. 여러분이 접근성에 대한 문의사항이 있다면 더 많은 경험이 있는 커뮤니티 멤버들의 리뷰를 검색해 보세요. 브라우저 벤더(vendor) 에이전트(agent)에 의해 업로드된 자료들은 게시 되었을때 접근 가능해야 합니다. 관련없는 커뮤니티 멤버들에 의해 업로드된 자료들은 그들이 접근할 수 없는 경우 명확히 표시 되어야 합니다. 적절한 시간 후에 콘텐츠에 접근할수 있는 적절한 조치가 취해지지 않는 경우 이 사이트에서 삭제 될 수 있습니다.

### 이 위키와 관련된 콘텐트를 게시하기

사이트의 목표와 관련이 없는 글([Pillars](/WPD:Pillars) 문서에 열거된 내용에 따라서)은 사이트에 포함할 수 없습니다. 확실치 않다면 IRC, 메일링 리스트 또는 포럼에 조언을 구해 보세요. 더 많은 정보는 [편집자 가이드 Step 2](/WPD:Editors_Guide/step_2_communicate_with_the_online_community/ko)를 확인 하세요.

### 의견들과 토론을 생략하기

글에 대한 의견들과 토론은 글의 내용이 아닌 관련 토론 페이지에서 이루어져야 합니다.

### 중복 콘텐츠를 게시하지 마세요.

이해 및 구조를 향상시킬 필요가 있는 경우를 제외하고 서로 다른 페이지가 대부분 일치하는 콘텐츠나 주제를 가지는지 확인하는 노력을 해주세요.

### 검색 엔진 최적화를 해 주세요.

글의 요약에서 가능한 자연스럽게 글과 통하는 관련 키워드들을 사용하세요. 그러나 검색 엔진 보다는(너무 많은 키워드들을 페이지에 나열하는 것) 사람을 위해 글을 써주세요.

### 모든 관련 섹션을 포함해 주세요.

-   만약 여러분이 튜토리얼과 컨셉트 글을 작성하고 있다면 [튜토리얼과 컨셉트 글 페이지](/WPD:Content/Tutorials_and_concept_articles)의 지침을 따르세요.
-   만약 여러분이 참조 문서를 작성하고 있다면 [참조 문서 페이지](/WPD:Content/Reference_articles)의 규칙을 확인해 주세요.
-   만약 여러분이 API문서를 업데이트 한다면 [API 문서 페이지 만들기](/WPD:Creating_API_pages)를 읽어 주세요.

글의 다른 유형들은 섹션들의 다른 유형을 가집니다. 고품질로 간주되는 글의 경우 모든 적용가능한 섹션을 포함하고 있어야 합니다.

### 위키 페이지의 포맷팅과 스타일링에 대한 논의에 참여하기

-   Note: 추가적인 스타일 논의는 [Web Education Community Group](http://www.w3.org/community/webed/wiki/Web_Education_community_group_style_guide)에서 진행합니다.

