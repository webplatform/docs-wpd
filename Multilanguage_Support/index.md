==Design Goals==
* The default language of the site should be English
* There should be a single 
* Translations should be a "first-class citizen" of the site
* It should be easy to discover which translations of a page are available
* Users should be able to choose a language of preference
** When navigating to an article, if there is a translated version of that article available in the user's language of choice, that version of the article should be presented
** Regardless of language preference, users should be able to navigate easily to the English-language version of an article (and possibly directly to other available translations)
** Automatic language negotiation should not be based on the location of the user (e.g. when a German who hasn't set their language preference travels to France, the English-language version of pages should be served)
* We should have an infrastructure that encourages and makes it easy for people to provide translations
* For each article, we should allow an translation into an unlimited number of languages, but there should only be a single canonical translation of any given article into a particular language (e.g. there should be 1-to-1 translations)
* Contributors should be able to create original content in other languages, which may be translated into English or other languages
* There should be a way to tell if the original version of an article has changed since the translation was made
* Translations should use standard BCP 47 [http://www.w3.org/International/articles/language-tags/ primary language tags] (e.g. ''zh'' for Mandarin Chinese), though in rare cases extended language subtags may also be used (e.g. ''zh-hans'' for Simplified Chinese, or ''az-Latn'' for Azerbaijani written in Latin script rather than Arabic)
* We should consider whether language tags should appear by default in the URL, or if the language tag should only appear in the URL to force the user to a specific language version of an article

==Mechanism==
This site will be using the MediaWiki convention of treating non-English articles (whether translations or original material) as '''subpages''' of the main article (which is assumed to be English). For example, the URL for the article on the CSS property <code>border-radius</code>, would be nested like so:
* webplatform.org/docs/css/properties/border-radius 

''docs'' is the wiki root, ''css'' is a subpage of ''docs'', ''properties'' is a subpage of ''css'', and ''border-radius'' is a subpage of ''properties''.

Translations of this article would be subpages of the article itself. For example:
* '''Chinese:''' webplatform.org/docs/css/properties/border-radius/'''zh''' 
* '''French:''' webplatform.org/docs/css/properties/border-radius/'''fr''' 
* '''Hindi:''' webplatform.org/docs/css/properties/border-radius/'''hi''' 
* '''Iranian Persian:''' webplatform.org/docs/css/properties/border-radius/'''pes''' 
* '''Swahili:''' webplatform.org/docs/css/properties/border-radius/'''sw'''

This mechanism applies not only to the final "leaf" node articles, those at the end of the information hierarchy chain, but also to each level above that, the organizational or aggregation articles; each level has its own potential translation, like so:
* webplatform.org/docs/'''fr''' 
* webplatform.org/docs/css/'''fr''' 
* webplatform.org/docs/css/properties/'''fr''' 
* webplatform.org/docs/css/properties/border-radius/'''fr''' 

This allows each language to reuse the same underlying information hierarchy and automatic semantic and structural mechanisms of the wiki system.

==User Experience==
===Readers===
language picker (not flags), showing all available translations for each page; once language picked, becomes default until another language is picked

can always return to main article (English-language version)

can pick any translation from any article or from another translation page

Is language tag always in URL?

====Search and Categories====
By default, only the English-language versions of article should show up in search results or category pages

===Translators===
If translation not available, can select language to translate into

====Translation Teams====
Team leaders, merit-based

====Template Translations====
For different Semantic Forms, should localize forms... is this possible?


==Automatic Translation==
The [http://www.mediawiki.org/wiki/Extension:Live_Translate Live Translate extension] allows the user translate an article via Google's or Microsoft's machine-translation services. In light of the highly technical nature of our content, with Web development and design jargon, this is likely to produce adequate translations.  However, we could install the extension, to make it available to readers for pages that haven't yet been localized, or for translators to use as a first-pass solution that they later rework.

==Notes==
'''Richard Ishida:'''
* language tags should only appear in urls when you want to force the user to a specific language version of a page
** ie. in the general case, use example.org/html/elements/video and NOT example.org/html/elements/video/fr or some such
* there should be a mechanism for users to be directed by default to the language version of a page that corresponds to their browser language preferences
* there should be an additional mechanism for someone to specify that they want to visit this site in a language that is different from their browser preference
* there should be links on each page to the same page in all existing translations

(See [https://www.w3.org/2012/05/22-webdoc-minutes.html 22 May 2012] teleconference for more details.)