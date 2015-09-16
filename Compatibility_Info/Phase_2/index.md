---
title: Phase 2
uri: 'WPD:Compatibility Info/Phase 2'

---
## Phase 1: *Integrate MDN data*

-   **Timeline:** April–May 2013
-   **Status:** in progress, partial completion

This second phase of automated data compatibility tables is to integrate the data from [Mozilla Developer Network (MDN)](https://developer.mozilla.org/).

MDN does not have a test-based methodology for its compatibility tables, which are reported manually by their contributors, but it does have wide coverage and a meaningful granularity of features. We can use these results as a stop-gap measure to fill in information where other data sources don't supply information. These non-test-based results will bear an indicator that they are not verified, and we will provide a way to allow contributors to submit tests and results for verification.

This data will be obtained from MDN only a single time, since it is temporary.

## Methodology

1.  Obtain permission from Mozilla to reuse this data *(done)*
2.  Identify a list of pages to copy the data from
3.  Create a script to access and save the compatibility data from each page via the MDN API *(partially done)*
4.  Run the script on a low-traffic day and time, to decrease the impact on MDN
5.  Convert the data into JSON format
6.  Upload the data file to a dedicated data directory: <http://docs.webplatform.org/compat/mdn/data.json>
7.  Develop a merge script to integrate the MDN data with other sources, preferentially selecting the other sources where they contain test-backed data
    -   Indicate in the JSON schema which results are test-driven and which are not

8.  Output markup to allow us to style non-test-driven data, and prompt users to contribute test (long-term)

## Results

The results will be a table showing the compatibility tables for the feature indicated in the **feature** attribute; for example, the CSS property *border-radius*: \<compatability topic="css" type="property" feature="border-radius"\>test\</compatability\>
