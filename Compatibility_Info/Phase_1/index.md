==Phase 1: ''Integrate automated compatibility tables from CanIUse data==
* '''Timeline:''' March–April <strike>2013</strike> 2014
* '''Status:''' in progress, partial completion

This first phase of automated data compatibility tables is to integrate the data from [http://caniuse.com/ CanIUse.com], a popular data-driven compatibility site.

==Methodology==
# Set up a cron job to pull the data from Alexis Deveria's [https://github.com/Fyrd/caniuse CanIUse GitHub repo] (https://raw.github.com/Fyrd/caniuse/master/data.json) on a weekly basis
# We saved the data in our own mirror at http://docs.webplatform.org/compat/caniuse/data.json
# We copied the data.json file to our shared data directory: http://docs.webplatform.org/compat/data.json
#* Currently, only CanIUse data is integrated into the shared data directory, but in later phases, we will integrate multiple sources of data, including QuirksMode and W3C Test Suites 
# We created a MediaWiki extension, [[WPD:Infrastructure/Extensions/CompaTables|CompaTables]] to automatically display the data as a table
## We registered a '''magic"" keyword element as a MediaWiki extension. To use, add in a Wiki page a snippte with the following syntax: <syntaxhighlight><compatability feature="border-radius" format="table"></compatability>
</syntaxhighlight>
## format can be either: 'table', or 'list'
## When this element is used in an article, we pull the data from the local repository, extract the data for the keyword indicated in the '''feature''' attribute, and format in into a table showing the first version supported for each browser 

==Results==
The results are a table showing the compatibility tables for the feature indicated in the '''feature''' attribute; for example, the CSS property ''border-radius'':
<compatability topic="css" type="property" feature="border-radius">test</compatability>

==Data Comparison==
There are substantial differences between the manual data currently available on many articles on WPD and the data available from CanIUse.

See the existing table on the [[css/properties/border-radius#Compatibility|border-radius article]]:
[[File:compat-table_border-radius.png]]

==Caching==
Generated HTML has three layers of caching: 
# Inside a wiki page behind Varnish, 
# Generates ESI tag for varnish (in progress)
# Cache generated HTML inside Memcached, invalidate cache if source JSON file is changed
[[File:CompaTables_to_use_ESI_and_Memcached.png|300px]]

===Feature Coverage===
The CanIUse data only focuses on newer features, not features that are consistently well-supported, so not every article has analogous information available.

===Feature Granularity===
The manual data has a finer degree of granularity for some features, including different values for certain properties and specific methods of an API. For example, with the CSS property ''border-radius'', while the CanIUse data currently only includes results for general support, the manual data includes results for the following granular values:
* Basic Support
* Percentages
* Elliptical borders
* 4 values for 4 corners

===Result Details and Consistency===
The manual data is missing detailed information on when a given browser first started supporting a particular feature, indicating only '''“Supported”''' in some fields, while the CanIUse data more consistently reports the version.

There are discrepancies between reported results in the manual data and the CanIUse data; these will need to be researched and accurate, test-driven results should be used.
 
===Prefixes and Polyfills===
The CanIUse data has information on the following states of support:
* Supported
* Partial support
* Supported but requires prefix 
* Unsupported, but has polyfill
* Unsupported
* Unknown

The manual data also includes this information, but inconsistently.

===Classifications and Naming Conventions===
The CanIUse data has its own set of idiosyncratic classifications and naming conventions for features. These are intuitive and valid taxonomies, but unifying based on a systematic convention may improve interoperability with other data sets.

===Notes===
Both the manual and CanIUse data supply extra notes about support, but each has different information.

==Next Steps==
Next steps for phase 1 are:
* add data to fill in features missing from CanIUse, with test coverage where possible
* <strike>improve the reporting of partial support, prefixes, and polyfills based on CanIUse data</strike>
* categorize and align data targets for optimal coverage
* improve table style, possibly with icons