---
title: WPD:Navigation
---
<h2><span class="mw-headline" id="URLs">URLs</span></h2>
<p>In addition to the <a rel="nofollow" class="external text" href="http://webplatform.org">WebPlatform.org</a> domain, we also have the domains <a rel="nofollow" class="external text" href="http://wpd.cc">wpd.cc</a>, <a rel="nofollow" class="external text" href="http://webplatformdocs.org">WebPlatformDocs.org</a>, and <a rel="nofollow" class="external text" href="http://webplatformdocs.com">WebPlatformDocs.com</a>, which redirect to <a rel="nofollow" class="external text" href="http://webplatform.org/docs/">WebPlatform.org/docs/</a>.
</p><p>The <a rel="nofollow" class="external text" href="http://webplatformdocs.org">WebPlatformDocs.org</a> and <a rel="nofollow" class="external text" href="http://webplatformdocs.com">WebPlatformDocs.com</a> domains are simply there to catch typos and people who hear "Web Platform Docs" and attempt to simply type the direct URL, and to a lesser extent, to prevent typosquatting; these domains are not intended to be published or promoted at all.
</p>
<h3><span class="mw-headline" id="Shortname:_WPD">Shortname: WPD</span></h3>
<p>The <a rel="nofollow" class="external text" href="http://wpd.cc">wpd.cc</a> domain, however, is meant to be part of our strategy. For link-sharing on Twitter or other character-limiting services, having a shortname like this will be useful (e.g. <a rel="nofollow" class="external text" href="http://wpd.cc/css/properties/border-radius">wpd.cc/css/properties/border-radius</a>); <b>WebPlatform.org/docs/</b> is 21 characters long, while <b>wpd.cc/</b> is only 7 characters long. 
</p><p>This URL also reinforces our <b>WPD</b> branding for usage on search engines, much like a search for "MDN border-radius" gets you more direct results.
</p><p>We may choose to have a "share" link (a la Web Intents) on each page, which may use the shortname rather than the full canonical <b>WebPlatform.org/docs/</b> URL. 
</p><p>We should evaluate what positive or negative effects this would have on site performance and on SEO.
</p>
<h3><span class="mw-headline" id="Internal_Redirects">Internal Redirects</span></h3>
<p>We may wish to set up shorter redirects for our "leaf" articles, such as those for CSS properties. For example, <a href="/w/index.php?title=border-radius&amp;action=edit&amp;redlink=1" class="new" title="border-radius (page does not exist)">WebPlatform.org/docs/border-radius</a> could redirect to <a href="/w/index.php?title=WebPlatform.org/docs/css/properties/border-radius&amp;action=edit&amp;redlink=1" class="new" title="WebPlatform.org/docs/css/properties/border-radius (page does not exist)">WebPlatform.org/docs/css/properties/border-radius</a>.
</p><p>This may prove convenient for link-sharing, and simply for typing directly as a URL.
</p><p>There will be conflicts, such as the HTML <code>a</code> element and the SVG <code>a</code> element, or the CSS <code>stroke</code> property and the SVG <code>stroke</code> attribute, but we can either decide on one resource, or redirect to a page that transcludes all results.
</p><p>As with wpd.cc, we should evaluate what positive or negative effects this would have on site performance and on SEO.
</p><p>If we want to preserve some structure to our redirects, we could opt for something like one of the following "short-URL" schemes:
</p>
<ul><li> WebPlatform.org/docs/c/p/border-radius</li>
<li> WebPlatform.org/docs/css/border-radius</li>
<li> WebPlatform.org/docs/cssprops/border-radius</li></ul>
<h2><span class="mw-headline" id="Site_Searches">Site Searches</span></h2>
<p>Our site searches should have a progressive autosuggest/autofiltering mechanism, like <a rel="nofollow" class="external text" href="http://dochub.io/">DocHub.io</a>. As the user types, a set of options are presented to them, based on the title of the article (which includes most or all keywords).  This will satisfy most queries that a user might have if they already have an idea of what they are looking for, and bypasses the need to load a separate results page if the user is looking for a titled article.
</p><p>If the user clicks on the "search" button, a traditional full-text search of article contents is performed instead. This stands a better chance of finding information from more vague clues.
</p><p>There could be some refinements on the results, however.
</p>
<h3><span class="mw-headline" id="Full-Text_vs._Word-Start">Full-Text vs. Word-Start</span></h3>
<p>There might be a picker control (checkbox, options) to allow the user to specify whether they want the typed string to come only at the beginning of the word, or if the string can occur anywhere in the title article.  For example, with <i>full-text</i>, the string <b>for</b> would return both <b>format</b> and <b>transform</b>, where with <i>word-start</i>, the string <b>for</b> would return only <b>format</b>, not <b>transform</b>.
</p>
<h3><span class="mw-headline" id="Categorization">Categorization</span></h3>
<p>Instead of requiring the user to first select a search category, as with DocHub, we might have categorized results from all topics (HTML, SVG, MathML, CSS, JavaScript, DOM, Events, and so on). For example, typing the word <b>for</b> might yield the following results:
</p>
<ul><li> CSS
<ul><li> block formatting context</li>
<li> page-break-before</li>
<li> text-transform</li>
<li> transform</li>
<li> transform-origin</li>
<li> transform-style</li>
<li> Using URL values for the cursor property</li>
<li> -moz-force-broken-image-icon</li>
<li>&#160;:-moz-system-metric(scrollbar-end-forward)</li>
<li>&#160;:-moz-system-metric(scrollbar-start-forward)</li>
<li>&#160;:before |&#160;::before</li></ul></li>
<li> HTML
<ul><li> form</li></ul></li>
<li> JavaScript
<ul><li> Array.forEach</li>
<li> Date.toLocaleFormat</li>
<li> for</li>
<li> for each...in</li>
<li> for...in</li></ul></li>
<li> SVG
<ul><li> animateTransform</li>
<li> font-face-format</li>
<li> foreignObject</li>
<li> format</li>
<li> transform</li></ul></li>
<li> DOM
<ul><li> beforeunload</li>
<li> document.enableStyleSheetsForSet</li>
<li> document.forms</li>
<li> document.getBoxObjectFor</li>
<li> element.onbeforescriptexecute</li>
<li> form.acceptCharset</li>
<li> form.action</li>
<li> form.elements</li>
<li> form.enctype</li>
<li> form.length</li>
<li> form.method</li>
<li> form.name</li>
<li> form.reset</li>
<li> form.submit</li>
<li> form.target</li>
<li> range.setEndBefore</li>
<li> range.setStartBefore</li>
<li> window.forward</li>
<li> window.navigator.platform</li>
<li> window.onbeforeunload</li>
<li> window.onmozbeforepaint</li>
<li> FormData</li>
<li> HTMLFormControlsCollection</li>
<li> HTMLFormElement</li>
<li> Node.insertBefore</li>
<li> SVGAnimateTransformElement</li>
<li> SVGAnimatedTransformList</li>
<li> SVGFontFaceFormatElement</li>
<li> SVGForeignObjectElement</li>
<li> SVGTransform</li>
<li> SVGTransformList</li>
<li> SVGTransformable</li>
<li> Using dynamic styling information</li></ul></li>
<li> MathML
<ul><li> forall</li></ul></li></ul>
<p>Each topic header might be collapsible or even removable from the results. This would make long results easier to view, search, and select. Alternately, the user could click upvote or downvote buttons for any given topic to set the preference to move those results up or down in future results.
</p>
<h3><span class="mw-headline" id="Toggling_Topics">Toggling Topics</span></h3>
<p>There might be a picker control (checkbox, options, selectbox) to allow the user to specify beforehand with topics (e.g. HTML, SVG, MathML, CSS, JavaScript, DOM, Events) they want to confine the search to. Given the value of page space and the clutter risk, however, the collapsible or removable results might be more effective as a UI.  We might consider allowing users to set an persistent search preference to confine or order the results, but that doesn't seem like an important feature.
</p>
<h2><span class="mw-headline" id="Categories">Categories</span></h2>
<p>Semantic MediaWiki has the ability to collect links to pages based on categories or tags, and we should expose that as widely as possible.
</p><p>For example, there should be a page with all articles including CSS properties, with a link to that page from each CSS property page. In addition, we might have finer-grained categories; for example, all article on the CSS property <i>font</i>, such as <i>font-size</i>, <i>font-weight</i>, etc. would be linked under the "Related Articles" section on each <i>font</i>-related property article.
</p>
<h2><span class="mw-headline" id="Breadcrumbs">Breadcrumbs</span></h2>
<p>Because we are using a topical hierarchical site structure, with subpages of topics, we will have breadcrumbs at the top of the page to allow the user to return to the next-higher level of abstraction. (Note: these will be hierarchical breadcrumbs, not path-followed breadcrumbs.)
</p><p>Users may wish to step from the current item to a sibling item under the same category (e.g. move from the HTML element <i>video</i> to the HTML element <i>audio</i>), without having to go back up to the page of all HTML elements. To enable this, we could have dropdown menus available on mouseover of each breadcrumb item, like this the <a rel="nofollow" class="external text" href="http://www.ajaxblender.com/script-sources/xbreadcrumbs/demo/index.html">xbreadcrumbs</a> JS library.
</p><p>For example, if the user were on a page about <i>border-radius</i>, the breadcrumbs would look like this:
</p>
<pre>Home &gt; CSS &gt; Properties &gt; border-radius
</pre>
<p>Mousing over 'Properties' would bring up a menu of all the CSS properties (or a more manageable set, like a list of alphabetical ranges, like 'a-d', 'e-h', ..., 'w-z', or 'actual value to display', ... 'white-space to z-index').
</p><p>Mousing over 'CSS' would bring up a menu with 'Properties', 'Selectors', and 'Data Types' (for example).
</p><p>Mousing over 'Home' would bring up a menu with 'HTML', 'CSS', 'SVG', 'DOM', 'ARIA', 'Javascript', 'MathML', and so on.
</p><p>Clicking on any of the top-level breadcrumbs would take the user to that hierarchical page, while clicking on the menu item would jump the user directly to that content page.
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:98-0!*!0!!*!*!*!esi=1 and timestamp 20150731181234 and revision id 217
 -->
