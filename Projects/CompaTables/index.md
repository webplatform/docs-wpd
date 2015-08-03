---
title: WPD:Projects/CompaTables
---
<h1><span class="mw-headline" id="Compatibility_Tables_.28.22CompaTables.22.29">Compatibility Tables ("CompaTables")</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>This document is to define how WebPlatform produce browser compatibility support table in multiple formats; published and within WebPlatform Docs. This document describes the actual implementation status and related conversation describing its status. 
</p><p>It is expected that the project produce multiple modules, such as: scraping, aggragating, normalizing, publishing and generating HTML blocks and also within our own pages.
</p><p>To read more about the plans and objectives you can see in the <a href="#Resources">#Resources</a>, read relevant <a href="#Mail_threads">#Mail threads</a>, or follow those links below:
</p>
<ul><li> <a href="/wiki/WPD:Compatibility_Info" title="WPD:Compatibility Info">WPD:Compatibility_Info</a></li>
<li> <a href="/wiki/WPD:Compatibility_Info/Phase_1" title="WPD:Compatibility Info/Phase 1">WPD:Compatibility_Info/Phase_1</a></li>
<li> <a href="/wiki/WPD:Compatibility_Info/Phase_2" title="WPD:Compatibility Info/Phase 2">WPD:Compatibility_Info/Phase_2</a></li>
<li> <a href="/wiki/WPD:Infrastructure/Components/CompaTables" title="WPD:Infrastructure/Components/CompaTables">WPD:Infrastructure/Components/CompaTables</a></li></ul>
<h2><span class="mw-headline" id="Past_sprints">Past sprints</span></h2>
<ul><li> <b>Mar. 2014</b> <a href="/wiki/WPD:Projects/CompaTables/201403-sprint#Work_done" title="WPD:Projects/CompaTables/201403-sprint">WPD:Projects/CompaTables/201403-sprint#Work done</a></li>
<li> <b>Aug. 2014</b>; Imported all content from MDN, published on github <a rel="nofollow" class="external text" href="https://github.com/webplatform/compatibility-data"><b>webplatform/compatibility-data</b></a></li>
<li> <b>Sept. 2014</b>
<ul><li> Compatibility HTML table rendering extension deployed (<a rel="nofollow" class="external text" href="https://github.com/webplatform/mediawiki/tree/master/extensions/Compatables">see code in <b>webplatform/mediawiki/../Compatables</b> MediaWiki extension</a>)</li>
<li> MediaWiki template we are using within our content is <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/Template:Compatibility"><i>Template:Compatibility</i></a> </li>
<li> Notes on where we installed the template calls in <a href="/wiki/WPD:Projects/CompaTables/Adding_to_our_content" title="WPD:Projects/CompaTables/Adding to our content">WPD:Projects/CompaTables/Adding_to_our_content</a></li></ul></li></ul>
<h3><span class="mw-headline" id="To_fix_or_improve">To fix or improve</span></h3>
<ul><li> See <a href="/wiki/WPD:Projects/CompaTables/201403-sprint#To_fix_or_improve" title="WPD:Projects/CompaTables/201403-sprint">WPD:Projects/CompaTables/201403-sprint#To fix or improve</a></li></ul>
<h2><span class="mw-headline" id="Related">Related</span></h2>
<h3><span class="mw-headline" id="Published_data">Published data</span></h3>
<ul><li> Generated from <a rel="nofollow" class="external text" href="https://github.com/webplatform/mdn-compat-importer">MDN Compat Importer</a></li>
<li> Data is available as <a rel="nofollow" class="external text" href="https://github.com/webplatform/compatibility-data"><b>webplatform/compatibility-data</b> on GitHub</a>
<ul><li> Available as <a rel="nofollow" class="external text" href="http://docs.webplatform.org/compat/data.json">compat/data.json</a>, </li>
<li> Also available in "human-friendly" format as  <a rel="nofollow" class="external text" href="http://docs.webplatform.org/compat/data-human.json">compat/data-human.json</a></li></ul></li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="Code_repositories">Code repositories</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/compatibility-data">Compatibility data</a></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/mdn-compat-importer">MDN Compat Importer</a>, by <a href="/wiki/User:Frozenice" title="User:Frozenice">User:frozenice</a> and <a href="/wiki/User:Renoirb" title="User:Renoirb">User:renoirb</a></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/mediawiki">WebPlatform mediawiki repository</a>, in <b>extensions/CompaTables</b>, by <i><a class="external text" href="http://www.mediawiki.org/wiki/User:Aaron_Schulz">Aaron Schulz</a></i>, <a href="/wiki/User:Shepazu" title="User:Shepazu">User:shepazu</a> and <a href="/wiki/User:Renoirb" title="User:Renoirb">User:Renoirb</a></li>
<li> <a rel="nofollow" class="external text" href="http://webplatform.github.io/browser-compat-model/">Data Model for User Agent Testing</a>, by <a href="/wiki/User:Ronaldmansveld" title="User:Ronaldmansveld">User:Ronaldmansveld</a> and <a rel="nofollow" class="external text" href="http://blog.tobie.me/">Tobie Langel</a></li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="See_also">See also</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="https://github.com/dontcallmedom/canmymobilebrowser">Can My Mobile Browser</a> by Dominique Hazael-Massieux, <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0024.html">in April 2013, Re: Automatic Data CanIUse Prototype</a> in file <a rel="nofollow" class="external text" href="https://github.com/dontcallmedom/canmymobilebrowser/blob/master/build.py">build.py</a> (yet to be documented)</li>
<li> Query the <i>data.json</i> file through the command line <a href="/wiki/WPD:Projects/CompaTables/Reading_the_data.json_file" title="WPD:Projects/CompaTables/Reading the data.json file">WPD:Projects/CompaTables/Reading_the_data.json_file</a></li></ul>
<h3><span class="mw-headline" id="Testing_the_Compatable_feature_our_pages">Testing the Compatable feature our pages</span></h3>
<ul><li> <a href="/wiki/WPD:Compatibility_Info/Test" title="WPD:Compatibility Info/Test">WPD:Compatibility_Info/Test</a></li>
<li> On the test wiki at <a rel="nofollow" class="external text" href="http://docs.webplatform.org/test/Tests/Compatibility_table_and_caching">test/Tests/Compatibility_table_and_caching</a>, bleeding edge version and integration testing</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Resources">Resources</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform-tests/"><i>public-webplatform-tests</i> dedicated mailing list</a></li>
<li> <a rel="nofollow" class="external text" href="http://testthewebforward.org/">Test the Web Forward</a></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/w3c/web-platform-tests">W3C browser test suites</a></li>
<li> <a rel="nofollow" class="external text" href="http://www.w3.org/Mobile/mobile-web-app-state/">W3C Mobile "web app state"</a> maintained by Dominique Hazael-Massieux</li></ul>
<h3><span class="mw-headline" id="Mail_threads">Mail threads</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0027.html">WebPlatform Browser Support Info</a>
<ul><li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0029.html">WebPlatform Browser Support Info</a></li></ul></li>
<li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0000.html">Oct. 17 2013, WebPlatform Browser Support Info</a></li>
<li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2013Mar/0345.html">March 2013,  Re: Automatic Data CanIUse Prototype</a>
<ul><li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0016.html">April 2013,  Re: Automatic Data CanIUse Prototype</a></li>
<li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0024.html">April 2013, Re: Automatic Data CanIUse Prototype</a> answer by Dominique Hazael-Massieux</li></ul></li>
<li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0017.html">Jan 2014, Converting MDN Compat Data to JSON</a>
<ul><li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0030.html">Jan 2014, Re: Converting MDN Compat Data to JSON</a></li></ul></li>
<li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0136.html">Jan. 27 2014, MDN Compat data project w/ Jeremie Patronnier</a>
<ul><li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0165.html">Jan. 30 2014</a></li>
<li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0130.html">Jan. 27 2014, by Janet</a></li></ul></li>
<li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2014Feb/0051.html">Feb. 07 2014, Compat Table Progress</a></li>
<li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform-tests/2014AprJun/0000.html">May 21 2014, Compat Table Data from MDN</a></li>
<li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0041.html">Sept. 13 2014, Upcoming compatibility table update</a> (i.e. displaying the compatibility data from within the wiki)
<ul><li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0044.html">(continued)</a></li>
<li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0045.html">(continued)</a></li>
<li> <a rel="nofollow" class="external text" href="http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0050.html">(continued)</a></li></ul></li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="Prefixes.2C_potential_resources">Prefixes, potential resources</span></h3>
<ul><li> <a rel="nofollow" class="external free" href="http://www.w3.org/TR/CSS21/syndata.html#vendor-keyword-history">http://www.w3.org/TR/CSS21/syndata.html#vendor-keyword-history</a></li>
<li> <a rel="nofollow" class="external free" href="http://peter.sh/experiments/vendor-prefixed-css-property-overview/">http://peter.sh/experiments/vendor-prefixed-css-property-overview/</a></li>
<li> <a rel="nofollow" class="external free" href="https://github.com/ai/autoprefixer">https://github.com/ai/autoprefixer</a>
<ul><li>  <a rel="nofollow" class="external free" href="https://github.com/ai/autoprefixer/tree/master/lib/hacks">https://github.com/ai/autoprefixer/tree/master/lib/hacks</a></li>
<li> <a rel="nofollow" class="external free" href="https://github.com/ai/autoprefixer/blob/master/updaters/prefixes.coffee">https://github.com/ai/autoprefixer/blob/master/updaters/prefixes.coffee</a></li>
<li> <a rel="nofollow" class="external free" href="https://github.com/ai/autoprefixer/blob/master/updaters/browsers.coffee">https://github.com/ai/autoprefixer/blob/master/updaters/browsers.coffee</a></li></ul></li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="Misc._assets">Misc. assets</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="https://github.com/alrra/browser-logos/">Collection of web browser logos</a></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.038 seconds
Real time usage: 0.044 seconds
Preprocessor visited node count: 50/1000000
Preprocessor generated node count: 56/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:17689-0!*!0!!*!*!*!esi=1 and timestamp 20150731111102 and revision id 70612
 -->
