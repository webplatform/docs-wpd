---
title: WPD:Compatibility Info/Phase 1
path: Compatibility_Info/Phase_1

---
<h2><span class="mw-headline" id="Phase_1:_Integrate_automated_compatibility_tables_from_CanIUse_data">Phase 1: <i>Integrate automated compatibility tables from CanIUse data</span></h2></i>
<ul><li> <b>Timeline:</b> March–April <strike>2013</strike> 2014</li>
<li> <b>Status:</b> in progress, partial completion</li></ul>
<p>This first phase of automated data compatibility tables is to integrate the data from <a rel="nofollow" class="external text" href="http://caniuse.com/">CanIUse.com</a>, a popular data-driven compatibility site.
</p>
<h2><span class="mw-headline" id="Methodology">Methodology</span></h2>
<ol><li> Set up a cron job to pull the data from Alexis Deveria's <a rel="nofollow" class="external text" href="https://github.com/Fyrd/caniuse">CanIUse GitHub repo</a> (<a rel="nofollow" class="external free" href="https://raw.github.com/Fyrd/caniuse/master/data.json">https://raw.github.com/Fyrd/caniuse/master/data.json</a>) on a weekly basis</li>
<li> We saved the data in our own mirror at <a rel="nofollow" class="external free" href="http://docs.webplatform.org/compat/caniuse/data.json">http://docs.webplatform.org/compat/caniuse/data.json</a></li>
<li> We copied the data.json file to our shared data directory: <a rel="nofollow" class="external free" href="http://docs.webplatform.org/compat/data.json">http://docs.webplatform.org/compat/data.json</a>
<ul><li> Currently, only CanIUse data is integrated into the shared data directory, but in later phases, we will integrate multiple sources of data, including QuirksMode and W3C Test Suites </li></ul></li>
<li> We created a MediaWiki extension, <a href="/wiki/WPD:Infrastructure/Extensions/CompaTables" title="WPD:Infrastructure/Extensions/CompaTables" class="mw-redirect">CompaTables</a> to automatically display the data as a table
<ol><li> Created a specific tag element that serves as placeholder for the table in the content. To use, add in a Wiki page using the following syntax: </li></ol></li></ol>
<pre class="language-html5" data-lang="html5">
<compatability feature="border-radius" format="table"></compatability>
</pre>
<ol><li><ol><li> format can be either: 'table', or 'list'</li>
<li> When this element is used in an article, we pull the data from the local repository, extract the data for the keyword indicated in the <b>feature</b> attribute, and format in into a table showing the first version supported for each browser </li></ol></li></ol>
<h2><span class="mw-headline" id="Results">Results</span></h2>
<p>The results are a table showing the compatibility tables for the feature indicated in the <b>feature</b> attribute; for example, the CSS property <i>border-radius</i>:
&lt;compatability topic="css" type="property" feature="border-radius"&gt;test&lt;/compatability&gt;
</p>
<h2><span class="mw-headline" id="Data_Comparison">Data Comparison</span></h2>
<p>There are substantial differences between the manual data currently available on many articles on WPD and the data available from CanIUse.
</p><p>See the existing table on the <a href="/wiki/css/properties/border-radius#Compatibility" title="css/properties/border-radius">border-radius article</a>:
<a href="/wiki/File:compat-table_border-radius.png" class="image"><img alt="compat-table border-radius.png" src="//static.webplatform.org/w/public/f/f2/compat-table_border-radius.png" width="842" height="765" /></a>
</p>
<h2><span class="mw-headline" id="Caching">Caching</span></h2>
<p>Generated HTML has three layers of caching: 
</p>
<ol><li> Inside a wiki page behind Varnish, </li>
<li> Generates ESI tag for varnish (in progress)</li>
<li> Cache generated HTML inside Memcached, invalidate cache if source JSON file is changed</li></ol>
<p><a href="/wiki/File:CompaTables_to_use_ESI_and_Memcached.png" class="image"><img alt="CompaTables to use ESI and Memcached.png" src="//static.webplatform.org/w/thumb/7/7b/CompaTables_to_use_ESI_and_Memcached.png/300px-CompaTables_to_use_ESI_and_Memcached.png" width="300" height="148" srcset="//static.webplatform.org/w/thumb/7/7b/CompaTables_to_use_ESI_and_Memcached.png/450px-CompaTables_to_use_ESI_and_Memcached.png 1.5x, //static.webplatform.org/w/thumb/7/7b/CompaTables_to_use_ESI_and_Memcached.png/600px-CompaTables_to_use_ESI_and_Memcached.png 2x" /></a>
</p>
<h3><span class="mw-headline" id="Feature_Coverage">Feature Coverage</span></h3>
<p>The CanIUse data only focuses on newer features, not features that are consistently well-supported, so not every article has analogous information available.
</p>
<h3><span class="mw-headline" id="Feature_Granularity">Feature Granularity</span></h3>
<p>The manual data has a finer degree of granularity for some features, including different values for certain properties and specific methods of an API. For example, with the CSS property <i>border-radius</i>, while the CanIUse data currently only includes results for general support, the manual data includes results for the following granular values:
</p>
<ul><li> Basic Support</li>
<li> Percentages</li>
<li> Elliptical borders</li>
<li> 4 values for 4 corners</li></ul>
<h3><span class="mw-headline" id="Result_Details_and_Consistency">Result Details and Consistency</span></h3>
<p>The manual data is missing detailed information on when a given browser first started supporting a particular feature, indicating only <b>“Supported”</b> in some fields, while the CanIUse data more consistently reports the version.
</p><p>There are discrepancies between reported results in the manual data and the CanIUse data; these will need to be researched and accurate, test-driven results should be used.
</p>
<h3><span class="mw-headline" id="Prefixes_and_Polyfills">Prefixes and Polyfills</span></h3>
<p>The CanIUse data has information on the following states of support:
</p>
<ul><li> Supported</li>
<li> Partial support</li>
<li> Supported but requires prefix </li>
<li> Unsupported, but has polyfill</li>
<li> Unsupported</li>
<li> Unknown</li></ul>
<p>The manual data also includes this information, but inconsistently.
</p>
<h3><span class="mw-headline" id="Classifications_and_Naming_Conventions">Classifications and Naming Conventions</span></h3>
<p>The CanIUse data has its own set of idiosyncratic classifications and naming conventions for features. These are intuitive and valid taxonomies, but unifying based on a systematic convention may improve interoperability with other data sets.
</p>
<h3><span class="mw-headline" id="Notes">Notes</span></h3>
<p>Both the manual and CanIUse data supply extra notes about support, but each has different information.
</p>
<h2><span class="mw-headline" id="Next_Steps">Next Steps</span></h2>
<p>Next steps for phase 1 are:
</p>
<ul><li> add data to fill in features missing from CanIUse, with test coverage where possible</li>
<li> <strike>improve the reporting of partial support, prefixes, and polyfills based on CanIUse data</strike></li>
<li> categorize and align data targets for optimal coverage</li>
<li> improve table style, possibly with icons</li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:8030-0!*!0!!*!5!*!esi=1 and timestamp 20150810200014 and revision id 48931
 -->
