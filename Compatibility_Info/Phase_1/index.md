---
title: Phase 1
uri: 'WPD:Compatibility Info/Phase 1'

---
## <span>Phase 1: *Integrate automated compatibility tables from CanIUse data*</span>

-   **Timeline:** March–April ~~2013~~ 2014
-   **Status:** in progress, partial completion

This first phase of automated data compatibility tables is to integrate the data from [CanIUse.com](http://caniuse.com/), a popular data-driven compatibility site.

## <span>Methodology</span>

1.  Set up a cron job to pull the data from Alexis Deveria's [CanIUse GitHub repo](https://github.com/Fyrd/caniuse) (<https://raw.github.com/Fyrd/caniuse/master/data.json>) on a weekly basis
2.  We saved the data in our own mirror at <http://docs.webplatform.org/compat/caniuse/data.json>
3.  We copied the data.json file to our shared data directory: <http://docs.webplatform.org/compat/data.json>
    -   Currently, only CanIUse data is integrated into the shared data directory, but in later phases, we will integrate multiple sources of data, including QuirksMode and W3C Test Suites

4.  We created a MediaWiki extension, [CompaTables](/WPD:Infrastructure/Extensions/CompaTables) to automatically display the data as a table
    1.  Created a specific tag element that serves as placeholder for the table in the content. To use, add in a Wiki page using the following syntax:

``` html
<compatability feature="border-radius" format="table"></compatability>
```

1.  1.  format can be either: 'table', or 'list'
    2.  When this element is used in an article, we pull the data from the local repository, extract the data for the keyword indicated in the **feature** attribute, and format in into a table showing the first version supported for each browser

## <span>Results</span>

The results are a table showing the compatibility tables for the feature indicated in the **feature** attribute; for example, the CSS property *border-radius*: \<compatability topic="css" type="property" feature="border-radius"\>test\</compatability\>

## <span>Data Comparison</span>

There are substantial differences between the manual data currently available on many articles on WPD and the data available from CanIUse.

See the existing table on the [border-radius article](/css/properties/border-radius#Compatibility): ![compat-table border-radius.png](/WPD/assets/public/f/f2/compat-table_border-radius.png)

## <span>Caching</span>

Generated HTML has three layers of caching:

1.  Inside a wiki page behind Varnish,
2.  Generates ESI tag for varnish (in progress)
3.  Cache generated HTML inside Memcached, invalidate cache if source JSON file is changed

![CompaTables to use ESI and Memcached.png](/WPD/assets/thumb/7/7b/CompaTables_to_use_ESI_and_Memcached.png/300px-CompaTables_to_use_ESI_and_Memcached.png)

### <span>Feature Coverage</span>

The CanIUse data only focuses on newer features, not features that are consistently well-supported, so not every article has analogous information available.

### <span>Feature Granularity</span>

The manual data has a finer degree of granularity for some features, including different values for certain properties and specific methods of an API. For example, with the CSS property *border-radius*, while the CanIUse data currently only includes results for general support, the manual data includes results for the following granular values:

-   Basic Support
-   Percentages
-   Elliptical borders
-   4 values for 4 corners

### <span>Result Details and Consistency</span>

The manual data is missing detailed information on when a given browser first started supporting a particular feature, indicating only **“Supported”** in some fields, while the CanIUse data more consistently reports the version.

There are discrepancies between reported results in the manual data and the CanIUse data; these will need to be researched and accurate, test-driven results should be used.

### <span>Prefixes and Polyfills</span>

The CanIUse data has information on the following states of support:

-   Supported
-   Partial support
-   Supported but requires prefix
-   Unsupported, but has polyfill
-   Unsupported
-   Unknown

The manual data also includes this information, but inconsistently.

### <span>Classifications and Naming Conventions</span>

The CanIUse data has its own set of idiosyncratic classifications and naming conventions for features. These are intuitive and valid taxonomies, but unifying based on a systematic convention may improve interoperability with other data sets.

### <span>Notes</span>

Both the manual and CanIUse data supply extra notes about support, but each has different information.

## <span>Next Steps</span>

Next steps for phase 1 are:

-   add data to fill in features missing from CanIUse, with test coverage where possible
-   ~~improve the reporting of partial support, prefixes, and polyfills based on CanIUse data~~
-   categorize and align data targets for optimal coverage
-   improve table style, possibly with icons
