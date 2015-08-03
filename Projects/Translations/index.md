---
title: WPD:Projects/translations
---
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>WebPlatform.org documents are attracting attention from a lot of web developers who read and write in many different languages as well as English. Many of them are willing to translate the documents into their native languages and associate them with the original ones written in English.
</p><p>Currently we have a problem on writing translations. There is no rule for creating translation articles yet.
</p>
<h2><span class="mw-headline" id="Potential_solutions">Potential solutions</span></h2>
<p>As preceding examples in translations, <a rel="nofollow" class="external text" href="http://meta.wikimedia.org/wiki/Complete_list_of_Wikimedia_projects">MediaWikis running on Wikimedia Project servers</a> have two different manners for creating articles in different language and associating it with ones in the other languages.
</p>
<h3><span class="mw-headline" id="Different_host_for_each_language">Different host for each language</span></h3>
<p>In <a rel="nofollow" class="external text" href="http://en.wikipedia.org/">Wikipedia</a>, <a rel="nofollow" class="external text" href="http://en.wiktionary.org/">Wiktionary</a>, <a rel="nofollow" class="external text" href="http://en.wikiversity.org/">Wikiversity</a>, etc., different host is prepared for each language; as for Wikipedia, <a rel="nofollow" class="external free" href="http://en.wikipedia.org/">http://en.wikipedia.org/</a> for English, <a rel="nofollow" class="external free" href="http://es.wikipedia.org/">http://es.wikipedia.org/</a> for Spanish, <a rel="nofollow" class="external free" href="http://ko.wikipedia.org/">http://ko.wikipedia.org/</a> for Korean, etc.
</p><p>As for WebPlatform.org, there is a proposal like <code>{lang}.docs.webplatform.org</code> or <code>docs-{lang}.webplatform.org</code> <a rel="nofollow" class="external autonumber" href="http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0113.html">[1]</a>.
</p><p>In this manner, different article names are allowed in different languages. (e.g. 'beginners' for English, '初心者' for Japanese)
</p><p>This solution requires configuration and additional mechanism for <a class="external text" href="http://www.mediawiki.org/wiki/Manual:Interwiki">interwiki</a>, which provides a method for hyperlinking between different Wikis. MediaWiki in every language host requires configurations of interwiki to the other language hosts.
</p><p>By default, all translators have to make interwiki manually to the corresponding articles in the other languages. MediaWiki itself does not have any functionalities to make such interwiki automatically. In Wikipedia, <a rel="nofollow" class="external text" href="http://meta.wikimedia.org/wiki/Interwiki_bot">interwiki bots</a> managed by volunteers are patrolling to find the articles which are hyperlinked from the ones in the other languages and make mutual interwiki hyperlinks automatically. For more convenience, <a rel="nofollow" class="external text" href="http://www.wikidata.org/wiki/Wikidata:Main_Page">Wikidata</a> provides a tool to create interwiki hyperlinks to all existing translations at once <a rel="nofollow" class="external autonumber" href="http://meta.wikimedia.org/wiki/Interwiki_bot">[2]</a>.
</p>
<h3><span class="mw-headline" id="Using_language_code_suffix_and_.7B.7BLanguages.7D.7D_template">Using language code suffix and {{Languages}} template</span></h3>
<p><a class="external text" href="http://www.mediawiki.org/">MediaWiki web site</a> etc.  have a simple rule of translations. Translated articles can be created as the subpage of their original English article. For instance, the article <code>article/name/fr</code> describes a French translation of <code>article/name</code> in English.
</p><p>In this solution, we can add the list of all translations simply by putting <a class="external text" href="http://www.mediawiki.org/wiki/Template:Languages">{{Languages}} template</a>  in a MediaWiki source code. This requires no additional configuration in MediaWiki (LocalSettings.php, etc.).
</p><p>This solution is found to have a problem that several language codes conflict with the names of some HTML elements <a rel="nofollow" class="external autonumber" href="http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0051.html">[3]</a>. To avoid such conflicts, alternative suffix rules are proposed; <code>article/name/lang-{lang}</code><a rel="nofollow" class="external autonumber" href="http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0076.html">[4]</a>, <code>article/name/lang:{lang}</code><a rel="nofollow" class="external autonumber" href="http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0077.html">[5]</a>, etc.
</p>
<!-- 
NewPP limit report
CPU time usage: 0.017 seconds
Real time usage: 0.018 seconds
Preprocessor visited node count: 20/1000000
Preprocessor generated node count: 60/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 3/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:7818-0!*!*!!*!*!*!esi=1 and timestamp 20150731174533 and revision id 29274
 -->
