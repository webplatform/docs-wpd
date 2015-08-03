---
title: WPD:Translations/ko
lang: ko

---
<p>현재, 웹 플랫폼 문서는 콘텐츠의 번역을 위해서 <a class="external text" href="http://www.mediawiki.org/wiki/Languages">미디어위키의 기능</a>을 사용하고 있습니다.
</p><p>특히, <a class="external text" href="http://www.mediawiki.org/wiki/Template:Languages">{{Languages}} 템플릿</a>을 사용하면, 해당 문서의 모든 번역 문서에 대한 링크가 생성됩니다.
</p>
<h2><span class="mw-headline" id=".EC.8B.9C.EC.8A.A4.ED.85.9C.EC.8B.9C.EC.8A.A4.ED.85.9C">시스템시스템</span></h2>
<p>이 사이트는 미디어위키의 방식인, 영어가 아닌 언어로 작성된 글(번역문 또는 비영문 원문)을 영어로 작성된 메인 글의 서브페이지로 취급합니다. 예를 들어, CSS 속성인 <code>border-radius</code>의 URL은 다음과 같습니다.
</p>
<ul><li> docs/webplatform.org/wiki/css/properties/border-radius </li></ul>
<p><i>docs</i>은 서브 도메인이고, <i>wiki</i>는 root의 서브 경로입니다. <i>css</i>는 <i>docs</i>의 서브 페이지이며, <i>properties</i>는 <i>css</i> 서브 페이지입니다. 그리고 <i>border-radius</i>는 <i>properties</i>의 서브 페이지입니다.
</p><p>아래의 예제처럼, 이 문서의 번역문은 이 문서의 서브 페이지가 됩니다.
</p>
<ul><li> <b>한국어:</b> docs/webplatform.org/wiki/css/properties/border-radius/<b>ko</b> </li>
<li> <b>중국어:</b> docs/webplatform.org/wiki/css/properties/border-radius/<b>zh</b> </li>
<li> <b>프랑스어:</b> docs/webplatform.org/wiki/css/properties/border-radius/<b>fr</b> </li>
<li> <b>힌두어:</b> docs/webplatform.org/wiki/css/properties/border-radius/<b>hi</b> </li>
<li> <b>페르시안 이란어:</b> docs/webplatform.org/wiki/css/properties/border-radius/<b>pes</b> </li>
<li> <b>스와힐리어:</b> docs/webplatform.org/wiki/css/properties/border-radius/<b>sw</b></li></ul>
<p>This mechanism applies not only to the final "leaf" node articles, those at the end of the information hierarchy chain, but also to each level above that, the organizational or aggregation articles; each level has its own potential translation, like so:
</p>
<ul><li> docs/webplatform.org/wiki/<b>fr</b> </li>
<li> docs/webplatform.org/wiki/css/<b>fr</b> </li>
<li> docs/webplatform.org/wiki/css/properties/<b>fr</b> </li>
<li> docs/webplatform.org/wiki/css/properties/border-radius/<b>fr</b> </li></ul>
<p>This allows each language to reuse the same underlying information hierarchy and automatic semantic and structural mechanisms of the wiki system.
</p>
<h3><span class="mw-headline" id="Details">Details</span></h3>
<p>For more details, see <a href="/wiki/WPD:Multilanguage_Support" title="WPD:Multilanguage Support">multilanguage support</a>.
</p>
<h3><span class="mw-headline" id="Example">Example</span></h3>
<p>As an example, see the <a href="/wiki/WPD:Languages" title="WPD:Languages">languages test page</a>.
</p>
<h3><span class="mw-headline" id="Bugs">Bugs</span></h3>
<ul><li> Currently, the displayed title of a translated article will be incorrect</li>
<li> Languages template is not included by default</li>
<li> Languages template displays in body, not header</li>
<li> No option to create blank translation page for an article</li>
<li> No ability to report how "fresh" a translation is</li>
<li> No mechanism to review translated articles</li>
<li> No "<i>auto-translate'</i> option</li>
<li> No <b>side-by-side</b> source-target page view</li></ul>
<h2><span class="mw-headline" id="Making_translations">Making translations</span></h2>
<p>If you are interested in providing translations for WPD, please follow the following steps:
</p>
<ul><li> Make sure that the page you are translating has the {{Languages}} template</li>
<li> Create a new page with the proper language subtag as a child of the translated page (e.g., docs/webplatform.org/wiki/css/properties/border-radius/<b>fr</b>), by altering the URL</li>
<li> Please use the appropriate templates for the translated page (the same templates as the source page)</li>
<li> Coordinate with other translators (especially the '<i>translation lead</i>)</li></ul>
<h3><span class="mw-headline" id="Translation_leads">Translation leads</span></h3>
<p>A '<i>translation lead</i> is the main coordinator for translations into any language. Some of their duties include:
</p>
<ul><li> Coordinating between translators</li>
<li> Tracking who is providing a translation for each page, to prevent conflicts</li>
<li> Recruiting translation volunteers</li>
<li> Making sure each page has a translator</li>
<li> Organize translation sprints</li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:7732-0!*!0!!*!*!*!esi=1 and timestamp 20150731183745 and revision id 27234
 -->
