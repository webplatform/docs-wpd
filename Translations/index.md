Web Platform Docs currently uses the [http://www.mediawiki.org/wiki/Languages MediaWiki features] for translated versions of the content.

Specifically we use the [http://www.mediawiki.org/wiki/Template:Languages <nowiki>{{Languages}}</nowiki> template], which creates a link to all translations of a page.

==Mechanism==
This site will be using the MediaWiki convention of treating non-English articles (whether translations or original material) as '''subpages''' of the main article (which is assumed to be English). For example, the URL for the article on the CSS property <code>border-radius</code>, would be nested like so:
* docs/webplatform.org/wiki/css/properties/border-radius 

''docs'' is the subdomain, ''wiki'' is the subdirectory root, ''css'' is a subpage of ''docs'', ''properties'' is a subpage of ''css'', and ''border-radius'' is a subpage of ''properties''.

Translations of this article would be subpages of the article itself. For example:
* '''Chinese:''' docs/webplatform.org/wiki/css/properties/border-radius/'''zh''' 
* '''French:''' docs/webplatform.org/wiki/css/properties/border-radius/'''fr''' 
* '''Hindi:''' docs/webplatform.org/wiki/css/properties/border-radius/'''hi''' 
* '''Iranian Persian:''' docs/webplatform.org/wiki/css/properties/border-radius/'''pes''' 
* '''Swahili:''' docs/webplatform.org/wiki/css/properties/border-radius/'''sw'''

This mechanism applies not only to the final "leaf" node articles, those at the end of the information hierarchy chain, but also to each level above that, the organizational or aggregation articles; each level has its own potential translation, like so:
* docs/webplatform.org/wiki/'''fr''' 
* docs/webplatform.org/wiki/css/'''fr''' 
* docs/webplatform.org/wiki/css/properties/'''fr''' 
* docs/webplatform.org/wiki/css/properties/border-radius/'''fr''' 

This allows each language to reuse the same underlying information hierarchy and automatic semantic and structural mechanisms of the wiki system.

===Details===
For more details, see [[WPD:Multilanguage_Support|multilanguage support]].

===Example===
As an example, see the [[WPD:Languages|languages test page]].

===Bugs===
* Currently, the displayed title of a translated article will be incorrect
* Languages template is not included by default
* Languages template displays in body, not header
* No option to create blank translation page for an article
* No ability to report how "fresh" a translation is
* No mechanism to review translated articles
* No "''auto-translate''' option
* No '''side-by-side''' source-target page view

==Making translations==
If you are interested in providing translations for WPD, please follow the following steps:

* Make sure that the page you are translating has the <nowiki>{{Languages}}</nowiki> template
* Create a new page with the proper language subtag as a child of the translated page (e.g., docs/webplatform.org/wiki/css/properties/border-radius/'''fr'''), by altering the URL
* Please use the appropriate templates for the translated page (the same templates as the source page)
* Coordinate with other translators (especially the '''translation lead'')

===Translation leads===
A '''translation lead'' is the main coordinator for translations into any language. Some of their duties include:
* Coordinating between translators
* Tracking who is providing a translation for each page, to prevent conflicts
* Recruiting translation volunteers
* Making sure each page has a translator
* Organize translation sprints