The compatibility tables on each reference page are meant to show how well each User Agent (desktop browser, mobile browser, authoring tool, etc.) supports that feature (also known as conformance). To be maximally help users, this information should be '''understandable''', '''data-driven''', '''accurate''', '''complete''', '''up-to-date''', '''detailed''', and '''comprehensive'''. 

==Automatic results==
Currently, most sites that report compatibility information rely on humans to input and update the current status of a feature in a browser, often based on very limited tests. This information is often out-of-date, and not comprehensive across User Agent and platforms. In an environment when more users are using a wide variety of devices to access web pages and webapps, this is not as helpful to developers as it could be.

Manual results are also subject to subjective opinions and even outright abuse in reporting compatibility; testing is not immune from marketing goals.

As much as possible, compatibility data should be automatically generated based on objective and verifiable criteria, not manually edited. This means that it should be based on representative tests.

==Data sources==
Given the requirement for data-driven, test-based compatibility results, we need to select appropriate sources for this information.

===QuirksMode===
QuirksMode, maintained by Peter-Paul Koch (PPK), has detailed and comprehensive test results for a variety of browsers, including mobile browsers.

===CanIUse===
CanIUse.com, maintained by Alexis Deveria, has data on a broad number of features, and excellent reporting and ability to drill down into details. 

===W3C Tests===
W3C working groups produce test suites and implementation reports associated with specific specifications.

Using this as a data source has the advantage that it will be kept up to date by the standardization process itself, and will also help provide incentive to browser vendors and others to provide tests to the Working Groups, because the results will be highly visible; this also takes advantage of the fact that we are encouraging implementers to make their unit tests and build tests in a way that can be contributed to W3C.

===Test the Web Forward===
This is a effort driven by Adobe and others to crowdsource the testing effort, to get developers directly involved in helping write tests. Their tests are meant to be made available through W3C's test suites.

===Others===
There are many other sources of good data on the web, some specialized and some with a different focus. We welcome data from these sources as they are identified.

==Drilling down into data==
Ideally, the depth of detail would allow developers to drill down from a high-level overview into individual criteria for conformance, including conformance on different devices and operating systems, combinations of the feature with other related features, and even access to the specific tests and their reported results.

Direct access to tests can be useful in a variety of ways, including:
* Verifying support on your own browser and platform or choice, especially for project testing and debugging 
* Using the test as a simple code example of a specific aspect of a feature
* Reviewing the test itself to make sure that an error didn't slip in

==Requirements==
In order to process, itegrate, and present the data, agreed convention are needed to categorize the information so it can be applied appropriately.

For example, W3C test suites and implementation reports are focused not on conformance, but on verification that all features of a specification are viable; the typical criterion for inclusion of a feature in a W3C Recommendation is that there are at least two independent implementations for that feature. This leads to tests that overlap but are not identical to the needs of developers. 

===Priority===
W3C tests are all treated with equal importance; a test for a primary use case has no more weight than a test for an edge case. The implementation report does not differentiate on which features are the most important for a general overview on browser support.

Information should be added to these tests to allow users to assess broad compatibility, with details available for drill-down. For example, tests could be marked '''critical''', '''important''', and '''edge-case''' (or given a simple numeric ranking).

===Overview===
Sometimes it's not easy to tell precisely what a test file is testing. Each test should include a human-understandable description of what is being tested, and what the pass criteria are.

===Uniform format and criteria===
Tests from all sources should have agreed-upon sets of formats, testing styles, and pass criteria

===Uniform reporting===
Tests from all sources should have a single convention for reporting for '''pass''', '''fail''', and '''uncertain''' results, and for identifying the name and version of the user agent and the platform.

==API==
To integrate the data, there should be an API that allows us to import the data from all of our sources regularly.

To be useful to other projects, this API should also allow anyone to query our compatibility data; we can use this API ourselves for generating the compatibility tables on the reference pages of WebPlatform.org.