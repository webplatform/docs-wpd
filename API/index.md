==API Documentation==
* [http://docs.webplatform.org/w/api.php http://docs.webplatform.org/w/api.php]
* [http://www.mediawiki.org/wiki/API:Query http://www.mediawiki.org/wiki/API:Query]
* [http://semantic-mediawiki.org/wiki/Ask_API http://semantic-mediawiki.org/wiki/Ask_API]

==API Examples==
Summary and possible values (without their description) for a single page, here [[css/properties/display]]:
* <nowiki>http://docs.webplatform.org/w/api.php?action=ask&query=[[css/properties/display]]|?Summary|?Possible_value</nowiki>

The same for a list of pages, here by [[:Category:CSS_Properties]]:
* <nowiki>http://docs.webplatform.org/w/api.php?action=ask&query=[[Category:CSS_Properties]]|?Summary|?Possible_value</nowiki>

Possible values with description:
* <nowiki>http://docs.webplatform.org/w/api.php?action=ask&query=[[Value_for_property::css/properties/display]]|?Property_value_description</nowiki>

Return the value description of a DOM method:
* <nowiki>http://docs.webplatform.org/w/api.php?action=ask&query=[[dom/methods/appendChild]]|?Return_value_description</nowiki>

==Discovering properties==
When making queries to the API, you need to specify which properties to display. A useful tool for discovering the available properties can be found here:
http://docs.webplatform.org/wiki/Special:Browse

For example, you can find the properties available on the Document interface at http://docs.webplatform.org/wiki/Special:Browse/dom-2Fdocument

==Applications==
* [http://blog.brackets.io/2013/05/01/web-platform-docs-in-brackets/ Brackets integration]: prepackaged inline CSS properties documentation, extracted from the API
* [http://webplatform.frozenice.de/pageinfo.html WPD page info] by [[User:Frozenice|Frozenice]]: explore the internals of a WPD page
* [http://webster.io/ Webster]: A quick reference for the web platform API.