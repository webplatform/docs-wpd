---
title: WPD:API
uri: 'WPD:API'

---
## <span>API Documentation</span>

-   <http://docs.webplatform.org/w/api.php>
-   <http://www.mediawiki.org/wiki/API:Query>
-   <http://semantic-mediawiki.org/wiki/Ask_API>

The API supports a variety of formats, for example, add format=json or format=xml as a parameter. For quick debugging you can use format=jsonfm or format=xmlfm, this will format the output for legibility.

## <span>API Examples</span>

Summary and possible values (without their description) for a single page, here [css/properties/display](/css/properties/display):

-   http://docs.webplatform.org/w/api.php?action=ask&query=[[css/properties/display]]|?Summary|?Possible\_value

The same for a list of pages, here by [Category:CSS\_Properties](/Category:CSS_Properties):

-   http://docs.webplatform.org/w/api.php?action=ask&query=[[Category:CSS\_Properties]]|?Summary|?Possible\_value

Possible values with description:

-   http://docs.webplatform.org/w/api.php?action=ask&query=[[Value\_for\_property::css/properties/display]]|?Property\_value\_description

Return the value description of a DOM method:

-   http://docs.webplatform.org/w/api.php?action=ask&query=[[dom/methods/appendChild]]|?Return\_value\_description

## <span>Discovering properties</span>

When making queries to the API, you need to specify which properties to display. A useful tool for discovering the available properties can be found here: <http://docs.webplatform.org/wiki/Special:Browse>

For example, you can find the properties available on the Document interface at <http://docs.webplatform.org/wiki/Special:Browse/dom-2Fdocument>

## <span>Applications</span>

-   [Brackets integration](http://blog.brackets.io/2013/05/01/web-platform-docs-in-brackets/): prepackaged inline CSS properties documentation, extracted from the API
-   [WPD page info](http://webplatform.frozenice.de/pageinfo.html) by [Frozenice](/User:Frozenice): explore the internals of a WPD page
-   [Webster](http://webster.io/): A quick reference for the web platform API.
