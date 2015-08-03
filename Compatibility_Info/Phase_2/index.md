---
title: WPD:Compatibility Info/Phase 2
---
<h2><span class="mw-headline" id="Phase_1:_Integrate_MDN_data">Phase 1: <i>Integrate MDN data</span></h2></i>
<ul><li> <b>Timeline:</b> April–May 2013</li>
<li> <b>Status:</b> in progress, partial completion</li></ul>
<p>This second phase of automated data compatibility tables is to integrate the data from <a rel="nofollow" class="external text" href="https://developer.mozilla.org/">Mozilla Developer Network (MDN)</a>.
</p><p>MDN does not have a test-based methodology for its compatibility tables, which are reported manually by their contributors, but it does have wide coverage and a meaningful granularity of features. We can use these results as a stop-gap measure to fill in information where other data sources don't supply information. These non-test-based results will bear an indicator that they are not verified, and we will provide a way to allow contributors to submit tests and results for verification.
</p><p>This data will be obtained from MDN only a single time, since it is temporary.
</p>
<h2><span class="mw-headline" id="Methodology">Methodology</span></h2>
<ol><li> Obtain permission from Mozilla to reuse this data <i>(done)</i></li>
<li> Identify a list of pages to copy the data from </li>
<li> Create a script to access and save the compatibility data from each page via the MDN API <i>(partially done)</i></li>
<li> Run the script on a low-traffic day and time, to decrease the impact on MDN</li>
<li> Convert the data into JSON format</li>
<li> Upload the data file to a dedicated data directory: <a rel="nofollow" class="external free" href="http://docs.webplatform.org/compat/mdn/data.json">http://docs.webplatform.org/compat/mdn/data.json</a></li>
<li> Develop a merge script to integrate the MDN data with other sources, preferentially selecting the other sources where they contain test-backed data
<ul><li> Indicate in the JSON schema which results are test-driven and which are not</li></ul></li>
<li> Output markup to allow us to style non-test-driven data, and prompt users to contribute test (long-term)</li></ol>
<h2><span class="mw-headline" id="Results">Results</span></h2>
<p>The results will be a table showing the compatibility tables for the feature indicated in the <b>feature</b> attribute; for example, the CSS property <i>border-radius</i>:
&lt;compatability topic="css" type="property" feature="border-radius"&gt;test&lt;/compatability&gt;
</p>
<!-- 
NewPP limit report
CPU time usage: 0.012 seconds
Real time usage: 0.013 seconds
Preprocessor visited node count: 10/1000000
Preprocessor generated node count: 16/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:8276-0!*!*!!*!*!*!esi=1 and timestamp 20150731025524 and revision id 31369
 -->
