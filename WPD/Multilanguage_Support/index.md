---
title: WPD:Multilanguage Support
uri: 'WPD:Multilanguage Support'

---
## <span>Design Goals</span>

-   The default language of the site should be English
-   There should be a single site hierarcy
-   Translations should be a "first-class citizen" of the site
-   It should be easy to discover which translations of a page are available
-   Users should be able to choose a language of preference
    -   When navigating to an article, if there is a translated version of that article available in the user's language of choice, that version of the article should be presented
    -   Regardless of language preference, users should be able to navigate easily to the English-language version of an article (and possibly directly to other available translations)
    -   Automatic language negotiation should not be based on the location of the user (e.g. when a German who hasn't set their language preference travels to France, the English-language version of pages should be served)
-   We should have an infrastructure that encourages and makes it easy for people to provide translations
-   For each article, we should allow an translation into an unlimited number of languages, but there should only be a single canonical translation of any given article into a particular language (e.g. there should be 1-to-1 translations)
-   Contributors should be able to create original content in other languages, which may be translated into English or other languages
-   There should be a way to tell if the original version of an article has changed since the translation was made
-   Translations should use standard BCP 47 [primary language tags](http://www.w3.org/International/articles/language-tags/) (e.g. *zh* for Mandarin Chinese), though in rare cases extended language subtags may also be used (e.g. *zh-hans* for Simplified Chinese, or *az-Latn* for Azerbaijani written in Latin script rather than Arabic)
-   We should consider whether language tags should appear by default in the URL, or if the language tag should only appear in the URL to force the user to a specific language version of an article

## <span>Mechanism</span>

This site will be using the MediaWiki convention of treating non-English articles (whether translations or original material) as **subpages** of the main article (which is assumed to be English). For example, the URL for the article on the CSS property `border-radius`, would be nested like so:

-   webplatform.org/docs/css/properties/border-radius

*docs* is the wiki root, *css* is a subpage of *docs*, *properties* is a subpage of *css*, and *border-radius* is a subpage of *properties*.

Translations of this article would be subpages of the article itself. For example:

-   **Chinese:** webplatform.org/docs/css/properties/border-radius/**zh**
-   **French:** webplatform.org/docs/css/properties/border-radius/**fr**
-   **Hindi:** webplatform.org/docs/css/properties/border-radius/**hi**
-   **Iranian Persian:** webplatform.org/docs/css/properties/border-radius/**pes**
-   **Swahili:** webplatform.org/docs/css/properties/border-radius/**sw**

This mechanism applies not only to the final "leaf" node articles, those at the end of the information hierarchy chain, but also to each level above that, the organizational or aggregation articles; each level has its own potential translation, like so:

-   webplatform.org/docs/**fr**
-   webplatform.org/docs/css/**fr**
-   webplatform.org/docs/css/properties/**fr**
-   webplatform.org/docs/css/properties/border-radius/**fr**

This allows each language to reuse the same underlying information hierarchy and automatic semantic and structural mechanisms of the wiki system.

## <span>User Experience</span>

### <span>Readers</span>

Each article will feature a language picker (not flags, which are controversial), showing all available translations for that article. If the user picks a particular language, that is saved as a preference, and that language becomes that user's default until they actively pick another language.

From any given translated page, the user can always return to the main (English-language version) article; the user should also be able to select any other translation of that same main article, from whatever translation they happen to be on (including the English-language version).

**Open Question:** Is it okay for the language tag to always appear in the URL? This may be a technical problem with MediaWiki, or may be solved by server-based content-negotiation.

#### <span>Search and Categories</span>

By default, only the English-language versions of article should show up in search results or category pages. Users can select the languages they wish to receive search results in.

### <span>Translators</span>

We intend to provide infrastructure, resources, and rewards for translators to localize our articles. Many details of this still need to be discussed and decided.

For each article, if there is not translation available, the user can select a language to translate into, and a subpage for that language will be created; optionally, a stub may be created from an automatic translation service, with the article automatically flagged as a stub.

#### <span>Translation Teams</span>

Once the site becomes known, we should actively recruit local Web developers to create translations for their language area. Some of these might come from W3C Members or W3C Offices, or from local offices of the Stewards; others may come from various Web developer communities.

Organizationally, we could pick "Translation Team Leads" on a merit or reputation basis. In turn, these Team Leads will help coordination the localization efforts, coordinating with the WebPlatform leads and admins.

### <span>Rewards</span>

**Community Service:** The simplest reward is providing a framework in which high-quality content and multiple translations can exist and thrive. This reward may be altruistic or enlightened self-interest.

**Attribution:** Since all translations will be marked with the contributor's username, and linked to their profile, they will get some degree of credibility and recognition from their contribution.

**Authority:** People who prove their expertise and willingness to help may be candidates for becoming Team Leads, or site admins.

**Badges:** People should get special badges for a certain number of translations (or quantity of translation), for organizing localization sprints, and so on. They can display these badges on their user profile, or on their own site.

#### <span>Template Translations</span>

Since the different Semantic Forms contain English-language terms for their output, we should localize these forms, if that's possible.

## <span>Automatic Translation</span>

The [Live Translate extension](http://www.mediawiki.org/wiki/Extension:Live_Translate) allows the user translate an article via Google's or Microsoft's machine-translation services. In light of the highly technical nature of our content, with Web development and design jargon, this is likely to produce adequate translations. However, we could install the extension, to make it available to readers for pages that haven't yet been localized, or for translators to use as a first-pass solution that they later rework.

## <span>Notes</span>

**Richard Ishida:**

-   language tags should only appear in urls when you want to force the user to a specific language version of a page
    -   ie. in the general case, use example.org/html/elements/video and NOT example.org/html/elements/video/fr or some such
-   there should be a mechanism for users to be directed by default to the language version of a page that corresponds to their browser language preferences
-   there should be an additional mechanism for someone to specify that they want to visit this site in a language that is different from their browser preference
-   there should be links on each page to the same page in all existing translations

(See [22 May 2012](https://www.w3.org/2012/05/22-webdoc-minutes.html) teleconference for more details.)