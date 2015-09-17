---
title: 'Creating translations on WebPlatform.org'
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - 'WPD:translations/translation lead'
uri: 'WPD:Translations'

---
Web Platform Docs was originally using [MediaWiki features](http://www.mediawiki.org/wiki/Languages) for translated versions of the content.

Specifically we use the [{{Languages}} template](http://www.mediawiki.org/wiki/Template:Languages), which creates a link to all translations of a page.

## Translating content instructions

WebPlatform.org has a MediaWiki extension installed that allows us to create translations of any pages we like. to do this, you simply need to:

-   Make sure you [have a WebPlatform.org account](http://docs.webplatform.org/wiki/WPD:Editors_Guide/step_1_register_for_a_wiki_account), and are logged in.
-   Find the language code of the language you want to translate into, for example "pt" for Portuguese, "pt-br" for Brazilian Portuguese. A search on a search engine will usually find what you are looking for, if you don't know that language code already!
-   Find a page you want to translate. Let's use <http://docs.webplatform.org/wiki/Main_Page> as an example, as it already has a good number of translations available!
-   To translate this page into your chosen language, you need to create your translated page at the same URL as the original, but with a subdirectory added on the end, of your language code. So for example <http://docs.webplatform.org/wiki/Main_Page/pt>.
-   Create your new page using the [[Page](http://docs.webplatform.org/wiki/WPD:New_Page%7CNew)] tool. Choose an appropriate template to create the page in. For this one, I used the "Other/Basic" form, entering "Main\_Page/pt" into the text field and pressing the "Create Basic Page" button (if you are translating a tutorial you'd use "Tutorial", "CSS Property" for a CSS property page, etc.) You need to make sure that everything after "wiki/" in the URL slug is entered into the form field, with a slash and your language code after it. So if you were creating a Japanese translation of the page at <http://docs.webplatform.org/wiki/css/properties/background-image>, you'd need to use the CSS Property form, and make sure you enter "css/properties/background-image/ja" into it.
-   Add your translation text into the new page you have created.
-   You also need to add a {{Languages}} tag into both your translation page and the original English page (if it does not include one yet) and save it.
-   If you've put the translated page into the right place and added the {{Languages}} tags correctly, a link to the available translations should appear in a special banner at the top of the pages, as seen in the image below.
-   Find a reviewer for your translation; this may be the [translation lead](/w/index.php?title=WPD:translations/translation_lead&action=edit&redlink=1)

![A WebPlatform.org page showing that a Portuguese translation is available.](/WPD/assets/public/d/d3/translation1.jpg)

PLEASE NOTE: If you want to use a language variant, for example "pt-br" for Brazilian Portuguese (see image below), rather than just "pt" for Portuguese, you need to **make everything lower case**. "pt-BR" won't work.

![A WebPlatform.org page showing that a Brazilian Portuguese translation is available.](/WPD/assets/public/a/af/translation2.jpg)

## Mechanism

This site will be using the MediaWiki convention of treating non-English articles (whether translations or original material) as **subpages** of the main article (which is assumed to be English). For example, the URL for the article on the CSS property `border-radius`, would be nested like so:

-   docs/webplatform.org/wiki/css/properties/border-radius

*docs* is the subdomain, *wiki* is the subdirectory root, *css* is a subpage of *docs*, *properties* is a subpage of *css*, and *border-radius* is a subpage of *properties*.

Translations of this article would be subpages of the article itself. For example:

-   **Chinese:** docs/webplatform.org/wiki/css/properties/border-radius/**zh**
-   **French:** docs/webplatform.org/wiki/css/properties/border-radius/**fr**
-   **Hindi:** docs/webplatform.org/wiki/css/properties/border-radius/**hi**
-   **Iranian Persian:** docs/webplatform.org/wiki/css/properties/border-radius/**pes**
-   **Swahili:** docs/webplatform.org/wiki/css/properties/border-radius/**sw**

This mechanism applies not only to the final "leaf" node articles, those at the end of the information hierarchy chain, but also to each level above that, the organizational or aggregation articles; each level has its own potential translation, like so:

-   docs/webplatform.org/wiki/**fr**
-   docs/webplatform.org/wiki/css/**fr**
-   docs/webplatform.org/wiki/css/properties/**fr**
-   docs/webplatform.org/wiki/css/properties/border-radius/**fr**

This allows each language to reuse the same underlying information hierarchy and automatic semantic and structural mechanisms of the wiki system.

### Details

For more details, see [multilanguage support](/WPD:Multilanguage_Support).

### Example

As an example, see the [languages test page](/WPD:Languages).

### Bugs

-   Currently, the displayed title of a translated article will be incorrect
-   Languages template is not included by default
-   Languages template displays in body, not header
-   No option to create blank translation page for an article
-   No ability to report how "fresh" a translation is
-   No mechanism to review translated articles
-   No "*auto-translate'* option
-   No **side-by-side** source-target page view

## Making translations

If you are interested in providing translations for WPD, please follow the following steps:

-   Make sure that the page you are translating has the {{Languages}} template
-   Create a new page with the proper language subtag as a child of the translated page (e.g., docs/webplatform.org/wiki/css/properties/border-radius/**fr**), by altering the URL
-   Please use the appropriate templates for the translated page (the same templates as the source page)
-   Coordinate with other translators (especially the '*translation lead*)

### Translation leads

A '*translation lead* is the main coordinator for translations into any language. Some of their duties include:

-   Coordinating between translators
-   Tracking who is providing a translation for each page, to prevent conflicts
-   Recruiting translation volunteers
-   Making sure each page has a translator
-   Organize translation sprints
