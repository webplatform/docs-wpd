---
title: WPD:API
---
<h2><span class="mw-headline" id="API_Documentation">API Documentation</span></h2>
<ul><li> <a rel="nofollow" class="external free" href="http://docs.webplatform.org/w/api.php">http://docs.webplatform.org/w/api.php</a></li>
<li> <a class="external free" href="http://www.mediawiki.org/wiki/API:Query">http://www.mediawiki.org/wiki/API:Query</a></li>
<li> <a rel="nofollow" class="external free" href="http://semantic-mediawiki.org/wiki/Ask_API">http://semantic-mediawiki.org/wiki/Ask_API</a></li></ul>
<p>The API supports a variety of formats, for example, add format=json or format=xml as a parameter. For quick debugging you can use format=jsonfm or format=xmlfm, this will format the output for legibility.
</p>
<h2><span class="mw-headline" id="API_Examples">API Examples</span></h2>
<p>Summary and possible values (without their description) for a single page, here <a href="/wiki/css/properties/display" title="css/properties/display">css/properties/display</a>:
</p>
<ul><li> http://docs.webplatform.org/w/api.php?action=ask&amp;query=[[css/properties/display]]|?Summary|?Possible_value</li></ul>
<p>The same for a list of pages, here by <a href="/wiki/Category:CSS_Properties" title="Category:CSS Properties">Category:CSS_Properties</a>:
</p>
<ul><li> http://docs.webplatform.org/w/api.php?action=ask&amp;query=[[Category:CSS_Properties]]|?Summary|?Possible_value</li></ul>
<p>Possible values with description:
</p>
<ul><li> http://docs.webplatform.org/w/api.php?action=ask&amp;query=[[Value_for_property::css/properties/display]]|?Property_value_description</li></ul>
<p>Return the value description of a DOM method:
</p>
<ul><li> http://docs.webplatform.org/w/api.php?action=ask&amp;query=[[dom/methods/appendChild]]|?Return_value_description</li></ul>
<h2><span class="mw-headline" id="Discovering_properties">Discovering properties</span></h2>
<p>When making queries to the API, you need to specify which properties to display. A useful tool for discovering the available properties can be found here:
<a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/Special:Browse">http://docs.webplatform.org/wiki/Special:Browse</a>
</p><p>For example, you can find the properties available on the Document interface at <a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/Special:Browse/dom-2Fdocument">http://docs.webplatform.org/wiki/Special:Browse/dom-2Fdocument</a>
</p>
<h2><span class="mw-headline" id="Applications">Applications</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="http://blog.brackets.io/2013/05/01/web-platform-docs-in-brackets/">Brackets integration</a>: prepackaged inline CSS properties documentation, extracted from the API</li>
<li> <a rel="nofollow" class="external text" href="http://webplatform.frozenice.de/pageinfo.html">WPD page info</a> by <a href="/wiki/User:Frozenice" title="User:Frozenice">Frozenice</a>: explore the internals of a WPD page</li>
<li> <a rel="nofollow" class="external text" href="http://webster.io/">Webster</a>: A quick reference for the web platform API.</li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.013 seconds
Real time usage: 0.014 seconds
Preprocessor visited node count: 50/1000000
Preprocessor generated node count: 100/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:8297-0!*!0!!*!*!*!esi=1 and timestamp 20150731003231 and revision id 44171
 -->
