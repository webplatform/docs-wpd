---
title: 'WPD:Compatibility Info'
uri: 'WPD:Compatibility Info'

---
The compatibility tables on each reference page are meant to show how well each User Agent (desktop browser, mobile browser, authoring tool, etc.) supports that feature (also known as conformance). To be maximally help users, this information should be **understandable**, **data-driven**, **accurate**, **complete**, **up-to-date**, **detailed**, and **comprehensive**.

We plan to integrate data from multiple sources to provide up-to-date information on each feature of the Open Web Platform. This information will be displayed in what we call **Compatibility Tables**, which show the support for a feature.

![Compatibility Table.png](/WPD/assets/public/4/49/Compatibility_Table.png)

## Automatic results

Currently, most sites that report compatibility information rely on humans to input and update the current status of a feature in a browser, often based on very limited tests. This information is often out-of-date, and not comprehensive across User Agent and platforms. In an environment when more users are using a wide variety of devices to access web pages and webapps, this is not as helpful to developers as it could be.

This kind of information is best when collected directly from test data and displayed automatically, rather than entered manually by contributors, for several reasons.

Manual data can go out of date quickly, while automated data can be collected and updated regularly.

Manual results are also subject to subjective opinions and even outright abuse in reporting compatibility; testing is not immune from marketing goals. Since this information can be subject to bias or different interpretations, it benefits from objective and fair criteria that is harder to game for PR purposes.

As much as possible, compatibility data should be automatically generated based on objective and verifiable criteria, not manually edited. This means that it should be based on representative tests.

## Data sources

The sources for our compatibility tables must be data-driven, test-based, to ensure transparency and consistency. They must also be open, and available under a license compatible with WPD's license, CC-BY.

Given these requirements, we need to select appropriate sources for this information.

### CanIUse

[CanIUse.com](http://caniuse.com/), created and maintained by Alexis Deveria, has data on a broad number of features, and excellent reporting and ability to drill down into details, specifically on features that everyday developers need.

This data already has a well-structured format that will serve as a great starting point. We may use code from [Andi Smith's CanIUse widget](http://andismith.github.com/caniuse-widget/).

### QuirksMode

[QuirksMode.org](http://www.quirksmode.org/compatibility.html), created and maintained by Peter-Paul Koch (PPK), has detailed and comprehensive test results for a variety of browsers, including mobile browsers, and is mature with great historical and current data.

### MobileHTML5

[MobileHTML5.org](http://mobilehtml5.org/), created and maintained by Max Firtman (@firt), covers high-level support for a wide variety of mobile devices.

### W3C Tests

W3C working groups produce test suites and implementation reports associated with specific specifications.

Using this as a data source has the advantage that it will be kept up to date by the standardization process itself, and will also help provide incentive to browser vendors and others to provide tests to the Working Groups, because the results will be highly visible; this also takes advantage of the fact that we are encouraging implementers to make their unit tests and build tests in a way that can be contributed to W3C.

While W3C Test Suites are comprehensive for W3C specification features, they are currently not ideally suited for use in compatibility tables. This will shift over time.

### Test the Web Forward

The [Test the Web Forward](http://testthewebforward.org/) events are a successful effort to help crowdsource testing. This is a effort driven by Adobe and others to get developers directly involved in helping write tests. The resulting tests are intended to be made available through W3C's test suites.

### MDN

[Mozilla Developer Network (MDN)](https://developer.mozilla.org/) does not have a test-based methodology for its compatibility tables, which are reported manually by their contributors, but it does have wide coverage and a meaningful granularity of features. We can use these results as a stop-gap measure to fill in information where other data sources don't supply information. These non-test-based results will bear an indicator that they are not verified, and we will provide a way to allow contributors to submit tests and results for verification.

### Others

There are many other sources of good data on the web, some specialized and some with a different focus. We welcome data from other open, high-quality, test-based repositories. In the future, we may also integrate efforts and features from projects like [Browserscope](http://www.browserscope.org/). Let us know if you have other sources of data you'd like us to consider.

For example, [HTML5Test.com](http://html5test.com/) might be a good source of data.

## Drilling down into data

Ideally, the depth of detail would allow developers to drill down from a high-level overview into individual criteria for conformance, including conformance on different devices and operating systems, combinations of the feature with other related features, and even access to the specific tests and their reported results.

Direct access to tests can be useful in a variety of ways, including:

-   Verifying support on your own browser and platform or choice, especially for project testing and debugging
-   Using the test as a simple code example of a specific aspect of a feature
-   Reviewing the test itself to make sure that an error didn't slip in

## Requirements

In order to process, itegrate, and present the data, agreed convention are needed to categorize the information so it can be applied appropriately.

For example, W3C test suites and implementation reports are focused not on conformance, but on verification that all features of a specification are viable; the typical criterion for inclusion of a feature in a W3C Recommendation is that there are at least two independent implementations for that feature. This leads to tests that overlap but are not identical to the needs of developers.

### Priority

W3C tests are all treated with equal importance; a test for a primary use case has no more weight than a test for an edge case. The implementation report does not differentiate on which features are the most important for a general overview on browser support.

Information should be added to these tests to allow users to assess broad compatibility, with details available for drill-down. For example, tests could be marked **critical**, **important**, and **edge-case** (or given a simple numeric ranking).

### Overview

Sometimes it's not easy to tell precisely what a test file is testing. Each test should include a human-understandable description of what is being tested, and what the pass criteria are.

### Uniform format and criteria

Tests from all sources should have agreed-upon sets of formats, testing styles, and pass criteria

### Uniform reporting

Tests from all sources should have a single convention for reporting for **pass**, **fail**, and **uncertain** results, and for identifying the name and version of the user agent and the platform.

## API

To integrate the data, there should be an API that allows us to import the data from all of our sources regularly.

To be useful to other projects, this API should also allow anyone to query our compatibility data. Like other aspects of WPD, we will use this API ourselves for generating the compatibility tables on the reference pages of WebPlatform.org.

## Timeline

-   **[Phase 1](/WPD:Compatibility_Info/Phase_1):** integrate automated compatibility tables from CanIUse data *(March–April 2013)*
-   **[Phase 2](/WPD:Compatibility_Info/Phase_2):** integrate MDN data *(April–May 2013)*
-   **Phase 3:** normalize and integrate QuirksMode data *(April–July 2013)*
-   **Phase 4:** normalize and integrate W3C Test data *(August 2013 – March 2014)*
