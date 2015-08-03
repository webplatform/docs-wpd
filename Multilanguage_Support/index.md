---
title: WPD:Multilanguage Support
---
<h2><span class="mw-headline" id="Design_Goals">Design Goals</span></h2>
<ul><li> The default language of the site should be English</li>
<li> There should be a single site hierarcy</li>
<li> Translations should be a "first-class citizen" of the site</li>
<li> It should be easy to discover which translations of a page are available</li>
<li> Users should be able to choose a language of preference
<ul><li> When navigating to an article, if there is a translated version of that article available in the user's language of choice, that version of the article should be presented</li>
<li> Regardless of language preference, users should be able to navigate easily to the English-language version of an article (and possibly directly to other available translations)</li>
<li> Automatic language negotiation should not be based on the location of the user (e.g. when a German who hasn't set their language preference travels to France, the English-language version of pages should be served)</li></ul></li>
<li> We should have an infrastructure that encourages and makes it easy for people to provide translations</li>
<li> For each article, we should allow an translation into an unlimited number of languages, but there should only be a single canonical translation of any given article into a particular language (e.g. there should be 1-to-1 translations)</li>
<li> Contributors should be able to create original content in other languages, which may be translated into English or other languages</li>
<li> There should be a way to tell if the original version of an article has changed since the translation was made</li>
<li> Translations should use standard BCP 47 <a rel="nofollow" class="external text" href="http://www.w3.org/International/articles/language-tags/">primary language tags</a> (e.g. <i>zh</i> for Mandarin Chinese), though in rare cases extended language subtags may also be used (e.g. <i>zh-hans</i> for Simplified Chinese, or <i>az-Latn</i> for Azerbaijani written in Latin script rather than Arabic)</li>
<li> We should consider whether language tags should appear by default in the URL, or if the language tag should only appear in the URL to force the user to a specific language version of an article</li></ul>
<h2><span class="mw-headline" id="Mechanism">Mechanism</span></h2>
<p>This site will be using the MediaWiki convention of treating non-English articles (whether translations or original material) as <b>subpages</b> of the main article (which is assumed to be English). For example, the URL for the article on the CSS property <code>border-radius</code>, would be nested like so:
</p>
<ul><li> webplatform.org/docs/css/properties/border-radius </li></ul>
<p><i>docs</i> is the wiki root, <i>css</i> is a subpage of <i>docs</i>, <i>properties</i> is a subpage of <i>css</i>, and <i>border-radius</i> is a subpage of <i>properties</i>.
</p><p>Translations of this article would be subpages of the article itself. For example:
</p>
<ul><li> <b>Chinese:</b> webplatform.org/docs/css/properties/border-radius/<b>zh</b> </li>
<li> <b>French:</b> webplatform.org/docs/css/properties/border-radius/<b>fr</b> </li>
<li> <b>Hindi:</b> webplatform.org/docs/css/properties/border-radius/<b>hi</b> </li>
<li> <b>Iranian Persian:</b> webplatform.org/docs/css/properties/border-radius/<b>pes</b> </li>
<li> <b>Swahili:</b> webplatform.org/docs/css/properties/border-radius/<b>sw</b></li></ul>
<p>This mechanism applies not only to the final "leaf" node articles, those at the end of the information hierarchy chain, but also to each level above that, the organizational or aggregation articles; each level has its own potential translation, like so:
</p>
<ul><li> webplatform.org/docs/<b>fr</b> </li>
<li> webplatform.org/docs/css/<b>fr</b> </li>
<li> webplatform.org/docs/css/properties/<b>fr</b> </li>
<li> webplatform.org/docs/css/properties/border-radius/<b>fr</b> </li></ul>
<p>This allows each language to reuse the same underlying information hierarchy and automatic semantic and structural mechanisms of the wiki system.
</p>
<h2><span class="mw-headline" id="User_Experience">User Experience</span></h2>
<h3><span class="mw-headline" id="Readers">Readers</span></h3>
<p>Each article will feature a language picker (not flags, which are controversial), showing all available translations for that article. If the user picks a particular language, that is saved as a preference, and that language becomes that user's default until they actively pick another language.
</p><p>From any given translated page, the user can always return to the main (English-language version) article; the user should also be able to select any other translation of that same main article, from whatever translation they happen to be on (including the English-language version).
</p><p><b>Open Question:</b> Is it okay for the language tag to always appear in the URL? This may be a technical problem with MediaWiki, or may be solved by server-based content-negotiation.
</p>
<h4><span class="mw-headline" id="Search_and_Categories">Search and Categories</span></h4>
<p>By default, only the English-language versions of article should show up in search results or category pages. Users can select the languages they wish to receive search results in.
</p>
<h3><span class="mw-headline" id="Translators">Translators</span></h3>
<p>We intend to provide infrastructure, resources, and rewards for translators to localize our articles. Many details of this still need to be discussed and decided.
</p><p>For each article, if there is not translation available, the user can select a language to translate into, and a subpage for that language will be created; optionally, a stub may be created from an automatic translation service, with the article automatically flagged as a stub.
</p>
<h4><span class="mw-headline" id="Translation_Teams">Translation Teams</span></h4>
<p>Once the site becomes known, we should actively recruit local Web developers to create translations for their language area. Some of these might come from W3C Members or W3C Offices, or from local offices of the Stewards; others may come from various Web developer communities.
</p><p>Organizationally, we could pick "Translation Team Leads" on a merit or reputation basis. In turn, these Team Leads will help coordination the localization efforts, coordinating with the WebPlatform leads and admins.
</p>
<h3><span class="mw-headline" id="Rewards">Rewards</span></h3>
<p><b>Community Service:</b> The simplest reward is providing a framework in which high-quality content and multiple translations can exist and thrive. This reward may be altruistic or enlightened self-interest.
</p><p><b>Attribution:</b> Since all translations will be marked with the contributor's username, and linked to their profile, they will get some degree of credibility and recognition from their contribution.
</p><p><b>Authority:</b> People who prove their expertise and willingness to help may be candidates for becoming Team Leads, or site admins.
</p><p><b>Badges:</b> People should get special badges for a certain number of translations (or quantity of translation), for organizing localization sprints, and so on. They can display these badges on their user profile, or on their own site.
</p>
<h4><span class="mw-headline" id="Template_Translations">Template Translations</span></h4>
<p>Since the different Semantic Forms contain English-language terms for their output, we should localize these forms, if that's possible.
</p>
<h2><span class="mw-headline" id="Automatic_Translation">Automatic Translation</span></h2>
<p>The <a class="external text" href="http://www.mediawiki.org/wiki/Extension:Live_Translate">Live Translate extension</a> allows the user translate an article via Google's or Microsoft's machine-translation services. In light of the highly technical nature of our content, with Web development and design jargon, this is likely to produce adequate translations.  However, we could install the extension, to make it available to readers for pages that haven't yet been localized, or for translators to use as a first-pass solution that they later rework.
</p>
<h2><span class="mw-headline" id="Notes">Notes</span></h2>
<p><b>Richard Ishida:</b>
</p>
<ul><li> language tags should only appear in urls when you want to force the user to a specific language version of a page
<ul><li> ie. in the general case, use example.org/html/elements/video and NOT example.org/html/elements/video/fr or some such</li></ul></li>
<li> there should be a mechanism for users to be directed by default to the language version of a page that corresponds to their browser language preferences</li>
<li> there should be an additional mechanism for someone to specify that they want to visit this site in a language that is different from their browser preference</li>
<li> there should be links on each page to the same page in all existing translations</li></ul>
<p>(See <a rel="nofollow" class="external text" href="https://www.w3.org/2012/05/22-webdoc-minutes.html">22 May 2012</a> teleconference for more details.)
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:83-0!*!*!!*!*!*!esi=1 and timestamp 20150731181229 and revision id 219
 -->
