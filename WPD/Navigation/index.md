---
title: WPD:Navigation
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - border-radius
    - WebPlatform.org/docs/css/properties/border-radius
uri: 'WPD:Navigation'

---
## <span>URLs</span>

In addition to the [WebPlatform.org](http://webplatform.org) domain, we also have the domains [wpd.cc](http://wpd.cc), [WebPlatformDocs.org](http://webplatformdocs.org), and [WebPlatformDocs.com](http://webplatformdocs.com), which redirect to [WebPlatform.org/docs/](http://webplatform.org/docs/).

The [WebPlatformDocs.org](http://webplatformdocs.org) and [WebPlatformDocs.com](http://webplatformdocs.com) domains are simply there to catch typos and people who hear "Web Platform Docs" and attempt to simply type the direct URL, and to a lesser extent, to prevent typosquatting; these domains are not intended to be published or promoted at all.

### <span>Shortname: WPD</span>

The [wpd.cc](http://wpd.cc) domain, however, is meant to be part of our strategy. For link-sharing on Twitter or other character-limiting services, having a shortname like this will be useful (e.g. [wpd.cc/css/properties/border-radius](http://wpd.cc/css/properties/border-radius)); **WebPlatform.org/docs/** is 21 characters long, while **wpd.cc/** is only 7 characters long.

This URL also reinforces our **WPD** branding for usage on search engines, much like a search for "MDN border-radius" gets you more direct results.

We may choose to have a "share" link (a la Web Intents) on each page, which may use the shortname rather than the full canonical **WebPlatform.org/docs/** URL.

We should evaluate what positive or negative effects this would have on site performance and on SEO.

### <span>Internal Redirects</span>

We may wish to set up shorter redirects for our "leaf" articles, such as those for CSS properties. For example, [WebPlatform.org/docs/border-radius](/w/index.php?title=border-radius&action=edit&redlink=1) could redirect to [WebPlatform.org/docs/css/properties/border-radius](/w/index.php?title=WebPlatform.org/docs/css/properties/border-radius&action=edit&redlink=1).

This may prove convenient for link-sharing, and simply for typing directly as a URL.

There will be conflicts, such as the HTML `a` element and the SVG `a` element, or the CSS `stroke` property and the SVG `stroke` attribute, but we can either decide on one resource, or redirect to a page that transcludes all results.

As with wpd.cc, we should evaluate what positive or negative effects this would have on site performance and on SEO.

If we want to preserve some structure to our redirects, we could opt for something like one of the following "short-URL" schemes:

-   WebPlatform.org/docs/c/p/border-radius
-   WebPlatform.org/docs/css/border-radius
-   WebPlatform.org/docs/cssprops/border-radius

## <span>Site Searches</span>

Our site searches should have a progressive autosuggest/autofiltering mechanism, like [DocHub.io](http://dochub.io/). As the user types, a set of options are presented to them, based on the title of the article (which includes most or all keywords). This will satisfy most queries that a user might have if they already have an idea of what they are looking for, and bypasses the need to load a separate results page if the user is looking for a titled article.

If the user clicks on the "search" button, a traditional full-text search of article contents is performed instead. This stands a better chance of finding information from more vague clues.

There could be some refinements on the results, however.

### <span>Full-Text vs. Word-Start</span>

There might be a picker control (checkbox, options) to allow the user to specify whether they want the typed string to come only at the beginning of the word, or if the string can occur anywhere in the title article. For example, with *full-text*, the string **for** would return both **format** and **transform**, where with *word-start*, the string **for** would return only **format**, not **transform**.

### <span>Categorization</span>

Instead of requiring the user to first select a search category, as with DocHub, we might have categorized results from all topics (HTML, SVG, MathML, CSS, JavaScript, DOM, Events, and so on). For example, typing the word **for** might yield the following results:

-   CSS
    -   block formatting context
    -   page-break-before
    -   text-transform
    -   transform
    -   transform-origin
    -   transform-style
    -   Using URL values for the cursor property
    -   -moz-force-broken-image-icon
    -    :-moz-system-metric(scrollbar-end-forward)
    -    :-moz-system-metric(scrollbar-start-forward)
    -    :before | ::before
-   HTML
    -   form
-   JavaScript
    -   Array.forEach
    -   Date.toLocaleFormat
    -   for
    -   for each...in
    -   for...in
-   SVG
    -   animateTransform
    -   font-face-format
    -   foreignObject
    -   format
    -   transform
-   DOM
    -   beforeunload
    -   document.enableStyleSheetsForSet
    -   document.forms
    -   document.getBoxObjectFor
    -   element.onbeforescriptexecute
    -   form.acceptCharset
    -   form.action
    -   form.elements
    -   form.enctype
    -   form.length
    -   form.method
    -   form.name
    -   form.reset
    -   form.submit
    -   form.target
    -   range.setEndBefore
    -   range.setStartBefore
    -   window.forward
    -   window.navigator.platform
    -   window.onbeforeunload
    -   window.onmozbeforepaint
    -   FormData
    -   HTMLFormControlsCollection
    -   HTMLFormElement
    -   Node.insertBefore
    -   SVGAnimateTransformElement
    -   SVGAnimatedTransformList
    -   SVGFontFaceFormatElement
    -   SVGForeignObjectElement
    -   SVGTransform
    -   SVGTransformList
    -   SVGTransformable
    -   Using dynamic styling information
-   MathML
    -   forall

Each topic header might be collapsible or even removable from the results. This would make long results easier to view, search, and select. Alternately, the user could click upvote or downvote buttons for any given topic to set the preference to move those results up or down in future results.

### <span>Toggling Topics</span>

There might be a picker control (checkbox, options, selectbox) to allow the user to specify beforehand with topics (e.g. HTML, SVG, MathML, CSS, JavaScript, DOM, Events) they want to confine the search to. Given the value of page space and the clutter risk, however, the collapsible or removable results might be more effective as a UI. We might consider allowing users to set an persistent search preference to confine or order the results, but that doesn't seem like an important feature.

## <span>Categories</span>

Semantic MediaWiki has the ability to collect links to pages based on categories or tags, and we should expose that as widely as possible.

For example, there should be a page with all articles including CSS properties, with a link to that page from each CSS property page. In addition, we might have finer-grained categories; for example, all article on the CSS property *font*, such as *font-size*, *font-weight*, etc. would be linked under the "Related Articles" section on each *font*-related property article.

## <span>Breadcrumbs</span>

Because we are using a topical hierarchical site structure, with subpages of topics, we will have breadcrumbs at the top of the page to allow the user to return to the next-higher level of abstraction. (Note: these will be hierarchical breadcrumbs, not path-followed breadcrumbs.)

Users may wish to step from the current item to a sibling item under the same category (e.g. move from the HTML element *video* to the HTML element *audio*), without having to go back up to the page of all HTML elements. To enable this, we could have dropdown menus available on mouseover of each breadcrumb item, like this the [xbreadcrumbs](http://www.ajaxblender.com/script-sources/xbreadcrumbs/demo/index.html) JS library.

For example, if the user were on a page about *border-radius*, the breadcrumbs would look like this:

    Home > CSS > Properties > border-radius

Mousing over 'Properties' would bring up a menu of all the CSS properties (or a more manageable set, like a list of alphabetical ranges, like 'a-d', 'e-h', ..., 'w-z', or 'actual value to display', ... 'white-space to z-index').

Mousing over 'CSS' would bring up a menu with 'Properties', 'Selectors', and 'Data Types' (for example).

Mousing over 'Home' would bring up a menu with 'HTML', 'CSS', 'SVG', 'DOM', 'ARIA', 'Javascript', 'MathML', and so on.

Clicking on any of the top-level breadcrumbs would take the user to that hierarchical page, while clicking on the menu item would jump the user directly to that content page.