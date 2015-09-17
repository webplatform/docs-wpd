---
title: 'Technical Requirements'
uri: 'WPD:Site/Technical Requirements'

---
## A Note on Priorities

Each feature should be marked with a priority, to help determine which features are needed when evaluating a CMS.

-   **1:** Must have
-   **2:** Should have
-   **3:** Nice to have

### Anti-features

If there is a feature that the CMS should not have, that should also be noted, for example:

    Should not require users to learn a new, unfamiliar markdown syntax (1)

Note, though, that most of these could be stated as "positive requirements":

    If uses markdown syntax, should use a familiar syntax such as MediaWiki's (1)

## Core Features

-   Accessible:
    -   [WCAG 2.0](http://www.w3.org/TR/WCAG/) (content aspect)
        -   Level A **(1)**
        -   Level AA **(2)**
    -   [ATAG 2.0](http://www.w3.org/TR/ATAG20/) (authoring tool aspect)
        -   Level A **(1)**
        -   Level AA **(2)**
-   Internationalizable
    -   easy to add translations or localizations **(1)**
    -   easy to find available translations and navigate to them **(1)**
-   clean semantic underlying code, as much as possible **(2)**
-   relatively easy and systemic method for porting well-formed content from multiple origins **(2)**
    -   *Note:* This is most important for the launch, less so for continued growth, so the way to do this doesn't have to be exposed to the general public... could be a bespoke workflow
-   Must work equally well across browsers
    -   viewing pages must work in all versions of browsers **(1)**
    -   editing pages must work in all modern browsers **(1)**
-   Customizable UI
-   Mobile-friendly output **(2)**

## Permissions and Profiles

-   Editable by anyone with account **(1)**
    -   Should track content contributions **(1)**
    -   Should have profile pages **(1)**
    -   Should allow login through OAuth via other identity providers (including W3C) **(2)**
-   Some pages can be "locked" **(1)** or have curated changes only **(2)**

## Navigation and Categorization

-   Tagging:
    -   must support the annotation or tagging of content to include it in different structures, rather than organizing it in rigid categories **(1)**
    -   tagging system also needs to support a smart referencing system, to generate most of the references to display/make available within each article. For example: An article on responsive design using media queries and viewport, which also makes use of HTML5 \<video\> and CSS transitions, should have links to those article automatically generated. **(2)**
-   Customizable sidebar / TOC **(1)**
-   URIs should be consistent, predictable, and unchanging **(1)**
-   Should allow multiple ways to find and navigate through content, including:
    -   sequential stepping through related pages **(1)**
    -   links to related topics **(1)**
    -   autocomplete search bar (a la DocHub) **(2)**
    -   drill-downs from general topics to more specific, based on categories **(2)**

## Editing

-   Should have WYSIWYG editing **(2)**
-   Custom markup and other code that the WYSIWYG doesn't do, for example being able to create a custom CSS layout for a particular article if needed. **(1)**
    -   CHRIS - Ideally it should be possible to apply custom scripts and stylesheets to pages, although I do accept that in reality this is probably too much of a security hole to have without any limit.
    -   Specific preferences for generated markup **(2)**
-   Template system for different kinds of content (reference pages for elements, attributes, CSS properties, events, APIs, etc.) **(2)**

## Code and Examples

-   Should be possible for the CMS to handle HTML5 as the standard language for all pages **(1)**
-   embedding of code examples **(1)**
-   code and example highlighting **(1)**
    -   start from numbers other than 1, to allow continuations of snippets **(2)**
-   Embedding live demos like Canvas, SVG, HTML5 \<video\>, etc? **(1)**

## Content Management

-   Include a "last updated" field in each article's footer **(1)**
-   Public view of "stale" articles that haven't been updated in a while, and may need review **(2)**

## Advanced Features

-   transclusion of content snippets **(2)**
    -   *The ability to define snippets of content to include directly in other pages. In practice this often allows tagging to work well, and makes changes to some kinds of formatting or content easier to accomplish.*
    -   *komoroske: I'd argue that this is a priority 1 feature. Without this feature it's extremely difficult to implement consistent information architecture of pages.*
-   Videos **(1)**
    -   Captioning **(1)**
    -   Served from same server (e.g. not YouTube / Vimeo) **(3)**
        -   *komoroske: Serving video also comes with potentially large bandwidth costs, which can be sidestepped by using YouTube/Vimeo*
-   Per-page scripts **(2)**

## Extra Site Features

-   Executable code example editor (e.g. JSFiddle, JSBin, Dabblet) **(1)**
    -   Should be able to open all examples in editor **(2)**
-   [Pastebin](http://en.wikipedia.org/wiki/Pastebin): may be same as code editor **(2)**
-   Blog **(2)**
-   Forums **(2)**
-   Surveys **(3)**

## APIs

-   Extractable pages for use remotely **(2)**
    -   Structured sections of page for customized extraction **(2)**
-   Allow automated input of browser support based on tests or other external data **(2)**

## Metrics

-   Feedback / rating for each article **(2)**
-   Tracking searches and result selection **(3)**
-   Usage data per site and per page **(2)**
-   Tracking should only be in aggregate, not per user **(1)**

## Scaling

-   Serving infrastructure can theoretically handle 10 million page views a month without problems **(1)**
-   Serving infrastructure can easily scale to handle arbitrary load as the site gains in popularity **(2)**
-   Serving cost scales smoothly with amount of traffic; no price cliffs **(2)**
-   Cost structure allows 10 million page views for less than \$10,000/mo **(2)**
    -   *komoroske: I just picked an arbitrary number here. Just trying to express it should be reasonably cheap.*

## Support

-   Support infrastructure to have site back up within an hour if any outages occur at any time **(1)**
-   Support infrastructure in place to implement scaling as load increases over time **(2)**
-   Support infrastructure to provide advice on configuring the site to run smoothly **(2)**
-   Support infrastructure to consult and/or implement site upgrades over time **(3)**
