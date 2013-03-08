== Summary ==

WebPlatform.org documents are attracting attention from a lot of web developers who read and write in many different languages as well as English. Many of them are willing to translate the documents into their native languages and associate them with the original ones written in English.

Currently we have a problem on writing translations. There is no rule for creating translation articles yet.

== Potential solutions ==

As preceding examples in translations, [http://meta.wikimedia.org/wiki/Complete_list_of_Wikimedia_projects MediaWikis running on Wikimedia Project servers] have two different manners for creating articles in different language and associating it with ones in the other languages.

=== Different host for each language ===

In [http://en.wikipedia.org/ Wikipedia], [http://en.wiktionary.org/ Wiktionary], [http://en.wikiversity.org/ Wikiversity], etc., different hosts are prepared for each languages; as for Wikipedia, http://en.wikipedia.org/ for English, http://es.wikipedia.org/ for Spanish, http://ko.wikipedia.org/ for Korean, etc.

As for WebPlatform.org, there is a proposal like <code>{lang}.docs.webplatform.org</code> or <code>docs-{lang}.webplatform.org</code> [http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0113.html].

In this manner, different article names are allowed in different languages. (e.g. 'beginners' for English, '初心者' for Japanese)

This solution requires configuration and additional mechanism for [http://www.mediawiki.org/wiki/Manual:Interwiki interwiki], which provides a method for hyperlinking between different Wikis. MediaWiki in every language host requires configurations of interwiki to the other language hosts.

By default, all translators have to make interwiki manually to the corresponding articles in the other languages. MediaWiki itself does not have any functionalities to make such interwiki automatically. In Wikipedia, [http://meta.wikimedia.org/wiki/Interwiki_bot interwiki bots] managed by volunteers are patrolling to find the articles which are hyperlinked from the ones in the other languages and make mutual interwiki hyperlinks automatically. For more convenience, [http://www.wikidata.org/wiki/Wikidata:Main_Page Wikidata] provides a tool to create interwiki hyperlinks to all existing translations at once [http://meta.wikimedia.org/wiki/Interwiki_bot].

=== Using language code suffix and <nowiki>{{Languages}}</nowiki> template ===

[http://www.mediawiki.org/ MediaWiki web site] etc.  have a simple rule of translations. Translated articles can be created as the subpage of their original English article. For instance, the article <code>article/name/fr</code> describes a French translation of <code>article/name</code> in English.

In this solution, we can add the list of all translations in a MediaWiki source code simply by using [http://www.mediawiki.org/wiki/Template:Languages <nowiki>{{Languages}}</nowiki> template]. This requires no additional configuration in MediaWiki (LocalSettings.php, etc.).

This solution is found to have a problem that several language codes conflict with some of HTML elements [http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0051.html]. To avoid such conflicts, alternative suffix rules are proposed; <code>article/name/lang-{lang}</code>[http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0076.html], <code>article/name/lang:{lang}</code>[http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0077.html], etc.