---
title: WPD:Infrastructure/analysis/Things to ensure is not changed
---
<h1><span class="mw-headline" id="Things_to_ensure_is_not_changed">Things to ensure is not changed</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>Infrastructure choices that should be remembered and not changed categorized by the target technology.
</p>
<h2><span class="mw-headline" id="Softwares">Softwares</span></h2>
<h3><span class="mw-headline" id="MediaWiki">MediaWiki</span></h3>
<h4><span class="mw-headline" id="robots.txt_and_the_redirects">robots.txt and the redirects</span></h4>
<p>Web server redirects must ensure that the <a rel="nofollow" class="external free" href="http://docs.webplatform.org/robots.txt">http://docs.webplatform.org/robots.txt</a> address <b>do not</b> redirect to <a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/robots.txt">http://docs.webplatform.org/wiki/robots.txt</a> otherwise it changes the context and makes crawling all kinds of things that shouldn't be and might overload server capacity.
</p>
<!-- 
NewPP limit report
CPU time usage: 0.009 seconds
Real time usage: 0.009 seconds
Preprocessor visited node count: 18/1000000
Preprocessor generated node count: 24/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:9501-0!*!*!!*!*!*!esi=1 and timestamp 20150730213639 and revision id 40901
 -->
