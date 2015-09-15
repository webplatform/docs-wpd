---
title: WPD:Translations
lang: ko
uri: 'WPD:Translations/ko'

---
현재, 웹 플랫폼 문서는 콘텐츠의 번역을 위해서 [미디어위키의 기능](http://www.mediawiki.org/wiki/Languages)을 사용하고 있습니다.

특히, [{{Languages}} 템플릿](http://www.mediawiki.org/wiki/Template:Languages)을 사용하면, 해당 문서의 모든 번역 문서에 대한 링크가 생성됩니다.

## <span>시스템시스템</span>

이 사이트는 미디어위키의 방식인, 영어가 아닌 언어로 작성된 글(번역문 또는 비영문 원문)을 영어로 작성된 메인 글의 서브페이지로 취급합니다. 예를 들어, CSS 속성인 `border-radius`의 URL은 다음과 같습니다.

-   docs/webplatform.org/wiki/css/properties/border-radius

*docs*은 서브 도메인이고, *wiki*는 root의 서브 경로입니다. *css*는 *docs*의 서브 페이지이며, *properties*는 *css* 서브 페이지입니다. 그리고 *border-radius*는 *properties*의 서브 페이지입니다.

아래의 예제처럼, 이 문서의 번역문은 이 문서의 서브 페이지가 됩니다.

-   **한국어:** docs/webplatform.org/wiki/css/properties/border-radius/**ko**
-   **중국어:** docs/webplatform.org/wiki/css/properties/border-radius/**zh**
-   **프랑스어:** docs/webplatform.org/wiki/css/properties/border-radius/**fr**
-   **힌두어:** docs/webplatform.org/wiki/css/properties/border-radius/**hi**
-   **페르시안 이란어:** docs/webplatform.org/wiki/css/properties/border-radius/**pes**
-   **스와힐리어:** docs/webplatform.org/wiki/css/properties/border-radius/**sw**

This mechanism applies not only to the final "leaf" node articles, those at the end of the information hierarchy chain, but also to each level above that, the organizational or aggregation articles; each level has its own potential translation, like so:

-   docs/webplatform.org/wiki/**fr**
-   docs/webplatform.org/wiki/css/**fr**
-   docs/webplatform.org/wiki/css/properties/**fr**
-   docs/webplatform.org/wiki/css/properties/border-radius/**fr**

This allows each language to reuse the same underlying information hierarchy and automatic semantic and structural mechanisms of the wiki system.

### <span>Details</span>

For more details, see [multilanguage support](/WPD:Multilanguage_Support).

### <span>Example</span>

As an example, see the [languages test page](/WPD:Languages).

### <span>Bugs</span>

-   Currently, the displayed title of a translated article will be incorrect
-   Languages template is not included by default
-   Languages template displays in body, not header
-   No option to create blank translation page for an article
-   No ability to report how "fresh" a translation is
-   No mechanism to review translated articles
-   No "*auto-translate'* option
-   No **side-by-side** source-target page view

## <span>Making translations</span>

If you are interested in providing translations for WPD, please follow the following steps:

-   Make sure that the page you are translating has the {{Languages}} template
-   Create a new page with the proper language subtag as a child of the translated page (e.g., docs/webplatform.org/wiki/css/properties/border-radius/**fr**), by altering the URL
-   Please use the appropriate templates for the translated page (the same templates as the source page)
-   Coordinate with other translators (especially the '*translation lead*)

### <span>Translation leads</span>

A '*translation lead* is the main coordinator for translations into any language. Some of their duties include:

-   Coordinating between translators
-   Tracking who is providing a translation for each page, to prevent conflicts
-   Recruiting translation volunteers
-   Making sure each page has a translator
-   Organize translation sprints
