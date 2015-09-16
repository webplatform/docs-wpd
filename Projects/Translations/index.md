---
title: translations
uri: 'WPD:Projects/translations'

---
## Summary

WebPlatform.org documents are attracting attention from a lot of web developers who read and write in many different languages as well as English. Many of them are willing to translate the documents into their native languages and associate them with the original ones written in English.

Currently we have a problem on writing translations. There is no rule for creating translation articles yet.

## Potential solutions

As preceding examples in translations, [MediaWikis running on Wikimedia Project servers](http://meta.wikimedia.org/wiki/Complete_list_of_Wikimedia_projects) have two different manners for creating articles in different language and associating it with ones in the other languages.

### Different host for each language

In [Wikipedia](http://en.wikipedia.org/), [Wiktionary](http://en.wiktionary.org/), [Wikiversity](http://en.wikiversity.org/), etc., different host is prepared for each language; as for Wikipedia, <http://en.wikipedia.org/> for English, <http://es.wikipedia.org/> for Spanish, <http://ko.wikipedia.org/> for Korean, etc.

As for WebPlatform.org, there is a proposal like `{lang}.docs.webplatform.org` or `docs-{lang}.webplatform.org` [[1]](http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0113.html).

In this manner, different article names are allowed in different languages. (e.g. 'beginners' for English, '初心者' for Japanese)

This solution requires configuration and additional mechanism for [interwiki](http://www.mediawiki.org/wiki/Manual:Interwiki), which provides a method for hyperlinking between different Wikis. MediaWiki in every language host requires configurations of interwiki to the other language hosts.

By default, all translators have to make interwiki manually to the corresponding articles in the other languages. MediaWiki itself does not have any functionalities to make such interwiki automatically. In Wikipedia, [interwiki bots](http://meta.wikimedia.org/wiki/Interwiki_bot) managed by volunteers are patrolling to find the articles which are hyperlinked from the ones in the other languages and make mutual interwiki hyperlinks automatically. For more convenience, [Wikidata](http://www.wikidata.org/wiki/Wikidata:Main_Page) provides a tool to create interwiki hyperlinks to all existing translations at once [[2]](http://meta.wikimedia.org/wiki/Interwiki_bot).

### Using language code suffix and {{Languages}} template

[MediaWiki web site](http://www.mediawiki.org/) etc. have a simple rule of translations. Translated articles can be created as the subpage of their original English article. For instance, the article `article/name/fr` describes a French translation of `article/name` in English.

In this solution, we can add the list of all translations simply by putting [{{Languages}} template](http://www.mediawiki.org/wiki/Template:Languages) in a MediaWiki source code. This requires no additional configuration in MediaWiki (LocalSettings.php, etc.).

This solution is found to have a problem that several language codes conflict with the names of some HTML elements [[3]](http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0051.html). To avoid such conflicts, alternative suffix rules are proposed; `article/name/lang-{lang}`[[4]](http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0076.html), `article/name/lang:{lang}`[[5]](http://lists.w3.org/Archives/Public/public-webplatform/2012Dec/0077.html), etc.
