---
title: WPD:Projects/CompaTables/201403-sprint
---
<h1><span class="mw-headline" id="Sprint_of_2014-03">Sprint of 2014-03</span></h1>
<p>Sprint report, extending documentation at <a href="/wiki/WPD:Projects/CompaTables" title="WPD:Projects/CompaTables">WPD:Projects/CompaTables</a>
</p>
<h2><span class="mw-headline" id="Work_done">Work done</span></h2>
<p><b>mdn-compat-importer</b>:
</p>
<ul><li> Process and normalize data (living implementation)</li></ul>
<p><b>CompaTables MediaWiki Extension</b>:
</p>
<ul><li> Implement mdn-compat-importer <i><a href="#Current_normalized_data">#Current normalized data</a></i> (living implementation)</li>
<li> Relies on Memcached to save/purge/re-use chunks of HTML</li>
<li> Allow manage markup-free text arrays (e.g. in format=table, the word "Unsupported" be in a dd tag, while in format=list it can be in a abbr tag)</li>
<li> Support alternate URL for table itself on its own view:
<ul><li> <a rel="nofollow" class="external text" href="http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&amp;format=table">Table in a standard view</a></li>
<li> <a rel="nofollow" class="external text" href="http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&amp;format=table&amp;foresi=1">Table alone (used for ESI, see in URL '&amp;foresi=1')</a></li></ul></li>
<li> Purging Memcached version of generated HTML views:
<ul><li> When origin JSON file date changes mismatch cached version</li>
<li> Purging a particular table directly, along with ESI purging mechanism  <a rel="nofollow" class="external text" href="http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&amp;format=table&amp;action=purge">see in URL note '&amp;action=purge'</a></li></ul></li>
<li> Should not break current ESI support feature</li>
<li> Rudimentary A11y markup (needs testing). Done according to <a rel="nofollow" class="external text" href="http://www.w3.org/TR/WCAG10-HTML-TECHS/#identifying-table-rows-columns">this WCAG1 checkpoint</a></li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="To_fix_or_improve">To fix or improve</span></h2>
<h4><span class="mw-headline" id="CompaTables_MediaWiki_Extension">CompaTables MediaWiki Extension</span></h4>
<ul><li> List view format (format=list) is not using latest <i><a href="#Current_normalized_data">#Current normalized data</a></i> </li>
<li> Table view format 
<ul><li> doesn't show prefix icons (e.g. -webkit)</li></ul></li></ul>
<h4><span class="mw-headline" id="ESI">ESI</span></h4>
<p>To use ESI, work has to be done on the servers. To summarize the findings, we cannot enable ESI tags on Fastly as it is at the moment due to a set of factors:
</p><p>Fastly's Varnish version (2.1.5) doesn't support gzip between backend and varnish; (but Varnish 3.x+ do.)
</p>
<ul><li> Between our servers ("backend") and Fastly we use currently compress with gzip</li>
<li> Fastly has plans to upgrade their varnish, but its out of our hands</li></ul>
<p>To enable;
</p>
<ul><li> Disable gzip between our backend servers and Fastly (might increase the data transfer usage, to validate with fastly)</li>
<li> Enable gzip only from Fastly to our visitors (currently gzip is in both places)</li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.018 seconds
Real time usage: 0.019 seconds
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

<!-- Saved in parser cache with key wpwiki:pcache:idhash:18463-0!*!0!!*!*!*!esi=1 and timestamp 20150731111103 and revision id 70567
 -->
