---
title: WPD:Translations
---
<h1><span class="mw-headline" id="Creating_translations_on_WebPlatform.org">Creating translations on WebPlatform.org</span></h1>
<p>Web Platform Docs was originally using <a class="external text" href="http://www.mediawiki.org/wiki/Languages">MediaWiki features</a> for translated versions of the content.
</p><p>Specifically we use the <a class="external text" href="http://www.mediawiki.org/wiki/Template:Languages">{{Languages}} template</a>, which creates a link to all translations of a page.
</p>
<h2><span class="mw-headline" id="Translating_content_instructions">Translating content instructions</span></h2>
<p>WebPlatform.org has a MediaWiki extension installed that allows us to create translations of any pages we like. to do this, you simply need to:
</p>
<ul><li> Make sure you <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/WPD:Editors_Guide/step_1_register_for_a_wiki_account">have a WebPlatform.org account</a>, and are logged in.</li>
<li> Find the language code of the language you want to translate into, for example "pt" for Portuguese, "pt-br" for Brazilian Portuguese. A search on a search engine will usually find what you are looking for, if you don't know that language code already!</li>
<li> Find a page you want to translate. Let's use <a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/Main_Page">http://docs.webplatform.org/wiki/Main_Page</a> as an example, as it already has a good number of translations available!</li>
<li> To translate this page into your chosen language, you need to create your translated page at the same URL as the original, but with a subdirectory added on the end, of your language code. So for example <a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/Main_Page/pt">http://docs.webplatform.org/wiki/Main_Page/pt</a>.</li>
<li> Create your new page using the [<a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/WPD:New_Page%7CNew">Page</a>] tool. Choose an appropriate template to create the page in. For this one, I used the "Other/Basic" form, entering "Main_Page/pt" into the text field and pressing the "Create Basic Page" button (if you are translating a tutorial you'd use "Tutorial", "CSS Property" for a CSS property page, etc.) You need to make sure that everything after "wiki/" in the URL slug is entered into the form field, with a slash and your language code after it. So if you were creating a Japanese translation of the page at <a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/css/properties/background-image">http://docs.webplatform.org/wiki/css/properties/background-image</a>, you'd need to use the CSS Property form, and make sure you enter "css/properties/background-image/ja" into it.</li>
<li> Add your translation text into the new page you have created.</li>
<li> You also need to add a &#123;&#123;Languages&#125;&#125; tag into both your translation page and the original English page (if it does not include one yet) and save it.</li>
<li> If you've put the translated page into the right place and added the &#123;&#123;Languages&#125;&#125; tags correctly, a link to the available translations should appear in a special banner at the top of the pages, as seen in the image below.</li>
<li> Find a reviewer for your translation; this may be the  <a href="/w/index.php?title=WPD:translations/translation_lead&amp;action=edit&amp;redlink=1" class="new" title="WPD:translations/translation lead (page does not exist)">translation lead</a></li></ul>
<div class="center"><div class="floatnone"><a href="/wiki/File:translation1.jpg" class="image" title="A WebPlatform.org page showing that a Portuguese translation is available."><img alt="A WebPlatform.org page showing that a Portuguese translation is available." src="//static.webplatform.org/w/public/d/d3/translation1.jpg" width="600" height="234" /></a></div></div>
<p>PLEASE NOTE: If you want to use a language variant, for example "pt-br" for Brazilian Portuguese (see image below), rather than just "pt" for Portuguese, you need to <strong>make everything lower case</strong>. "pt-BR" won't work.</p>
<div class="center"><div class="floatnone"><a href="/wiki/File:translation2.jpg" class="image" title="A WebPlatform.org page showing that a Brazilian Portuguese translation is available."><img alt="A WebPlatform.org page showing that a Brazilian Portuguese translation is available." src="//static.webplatform.org/w/public/a/af/translation2.jpg" width="600" height="226" /></a></div></div>
<p><br />
</p>
<h2><span class="mw-headline" id="Mechanism">Mechanism</span></h2>
<p>This site will be using the MediaWiki convention of treating non-English articles (whether translations or original material) as <b>subpages</b> of the main article (which is assumed to be English). For example, the URL for the article on the CSS property <code>border-radius</code>, would be nested like so:
</p>
<ul><li> docs/webplatform.org/wiki/css/properties/border-radius </li></ul>
<p><i>docs</i> is the subdomain, <i>wiki</i> is the subdirectory root, <i>css</i> is a subpage of <i>docs</i>, <i>properties</i> is a subpage of <i>css</i>, and <i>border-radius</i> is a subpage of <i>properties</i>.
</p><p>Translations of this article would be subpages of the article itself. For example:
</p>
<ul><li> <b>Chinese:</b> docs/webplatform.org/wiki/css/properties/border-radius/<b>zh</b> </li>
<li> <b>French:</b> docs/webplatform.org/wiki/css/properties/border-radius/<b>fr</b> </li>
<li> <b>Hindi:</b> docs/webplatform.org/wiki/css/properties/border-radius/<b>hi</b> </li>
<li> <b>Iranian Persian:</b> docs/webplatform.org/wiki/css/properties/border-radius/<b>pes</b> </li>
<li> <b>Swahili:</b> docs/webplatform.org/wiki/css/properties/border-radius/<b>sw</b></li></ul>
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

<!-- 
NewPP limit report
CPU time usage: 0.061 seconds
Real time usage: 1.241 seconds
Preprocessor visited node count: 48/1000000
Preprocessor generated node count: 76/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:6698-0!*!0!!*!5!*!esi=1 and timestamp 20150731180914 and revision id 101739
 -->
