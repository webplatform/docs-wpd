---
title: WPD:Compatibility Info
---
<p>The compatibility tables on each reference page are meant to show how well each User Agent (desktop browser, mobile browser, authoring tool, etc.) supports that feature (also known as conformance). To be maximally help users, this information should be <b>understandable</b>, <b>data-driven</b>, <b>accurate</b>, <b>complete</b>, <b>up-to-date</b>, <b>detailed</b>, and <b>comprehensive</b>. 
</p><p>We plan to integrate data from multiple sources to provide up-to-date information on each feature of the Open Web Platform. This information will be displayed in what we call <b>Compatibility Tables</b>, which show the support for a feature.
</p><p><a href="/wiki/File:Compatibility_Table.png" class="image"><img alt="Compatibility Table.png" src="//static.webplatform.org/w/public/4/49/Compatibility_Table.png" width="927" height="82" /></a>
</p>
<h2><span class="mw-headline" id="Automatic_results">Automatic results</span></h2>
<p>Currently, most sites that report compatibility information rely on humans to input and update the current status of a feature in a browser, often based on very limited tests. This information is often out-of-date, and not comprehensive across User Agent and platforms. In an environment when more users are using a wide variety of devices to access web pages and webapps, this is not as helpful to developers as it could be.
</p><p>This kind of information is best when collected directly from test data and displayed automatically, rather than entered manually by contributors, for several reasons. 
</p><p>Manual data can go out of date quickly, while automated data can be collected and updated regularly.
</p><p>Manual results are also subject to subjective opinions and even outright abuse in reporting compatibility; testing is not immune from marketing goals. Since this information can be subject to bias or different interpretations, it benefits from objective and fair criteria that is harder to game for PR purposes.
</p><p>As much as possible, compatibility data should be automatically generated based on objective and verifiable criteria, not manually edited. This means that it should be based on representative tests.
</p>
<h2><span class="mw-headline" id="Data_sources">Data sources</span></h2>
<p>The sources for our compatibility tables must be data-driven, test-based, to ensure transparency and consistency. They must also be open, and available under a license compatible with WPD's license, CC-BY.
</p><p>Given these requirements, we need to select appropriate sources for this information.
</p>
<h3><span class="mw-headline" id="CanIUse">CanIUse</span></h3>
<p><a rel="nofollow" class="external text" href="http://caniuse.com/">CanIUse.com</a>, created and maintained by Alexis Deveria, has data on a broad number of features, and excellent reporting and ability to drill down into details, specifically on features that everyday developers need.
</p><p>This data already has a well-structured format that will serve as a great starting point. We may use code from <a rel="nofollow" class="external text" href="http://andismith.github.com/caniuse-widget/">Andi Smith's CanIUse widget</a>.
</p>
<h3><span class="mw-headline" id="QuirksMode">QuirksMode</span></h3>
<p><a rel="nofollow" class="external text" href="http://www.quirksmode.org/compatibility.html">QuirksMode.org</a>, created and maintained by Peter-Paul Koch (PPK), has detailed and comprehensive test results for a variety of browsers, including mobile browsers, and is mature with great historical and current data.
</p>
<h3><span class="mw-headline" id="MobileHTML5">MobileHTML5</span></h3>
<p><a rel="nofollow" class="external text" href="http://mobilehtml5.org/">MobileHTML5.org</a>, created and maintained by Max Firtman (@firt), covers high-level support for a wide variety of mobile devices. 
</p>
<h3><span class="mw-headline" id="W3C_Tests">W3C Tests</span></h3>
<p>W3C working groups produce test suites and implementation reports associated with specific specifications.
</p><p>Using this as a data source has the advantage that it will be kept up to date by the standardization process itself, and will also help provide incentive to browser vendors and others to provide tests to the Working Groups, because the results will be highly visible; this also takes advantage of the fact that we are encouraging implementers to make their unit tests and build tests in a way that can be contributed to W3C.
</p><p>While W3C Test Suites are comprehensive for W3C specification features, they are currently not ideally suited for use in compatibility tables. This will shift over time.
</p>
<h3><span class="mw-headline" id="Test_the_Web_Forward">Test the Web Forward</span></h3>
<p>The <a rel="nofollow" class="external text" href="http://testthewebforward.org/">Test the Web Forward</a> events are a successful effort to help crowdsource testing. This is a effort driven by Adobe and others to get developers directly involved in helping write tests. The resulting tests are intended to be made available through W3C's test suites.
</p>
<h3><span class="mw-headline" id="MDN">MDN</span></h3>
<p><a rel="nofollow" class="external text" href="https://developer.mozilla.org/">Mozilla Developer Network (MDN)</a> does not have a test-based methodology for its compatibility tables, which are reported manually by their contributors, but it does have wide coverage and a meaningful granularity of features. We can use these results as a stop-gap measure to fill in information where other data sources don't supply information. These non-test-based results will bear an indicator that they are not verified, and we will provide a way to allow contributors to submit tests and results for verification.
</p>
<h3><span class="mw-headline" id="Others">Others</span></h3>
<p>There are many other sources of good data on the web, some specialized and some with a different focus. We welcome data from other open, high-quality, test-based repositories. In the future, we may also integrate efforts and features from projects like <a rel="nofollow" class="external text" href="http://www.browserscope.org/">Browserscope</a>. Let us know if you have other sources of data you'd like us to consider.
</p><p>For example, <a rel="nofollow" class="external text" href="http://html5test.com/">HTML5Test.com</a> might be a good source of data.
</p>
<h2><span class="mw-headline" id="Drilling_down_into_data">Drilling down into data</span></h2>
<p>Ideally, the depth of detail would allow developers to drill down from a high-level overview into individual criteria for conformance, including conformance on different devices and operating systems, combinations of the feature with other related features, and even access to the specific tests and their reported results.
</p><p>Direct access to tests can be useful in a variety of ways, including:
</p>
<ul><li> Verifying support on your own browser and platform or choice, especially for project testing and debugging </li>
<li> Using the test as a simple code example of a specific aspect of a feature</li>
<li> Reviewing the test itself to make sure that an error didn't slip in</li></ul>
<h2><span class="mw-headline" id="Requirements">Requirements</span></h2>
<p>In order to process, itegrate, and present the data, agreed convention are needed to categorize the information so it can be applied appropriately.
</p><p>For example, W3C test suites and implementation reports are focused not on conformance, but on verification that all features of a specification are viable; the typical criterion for inclusion of a feature in a W3C Recommendation is that there are at least two independent implementations for that feature. This leads to tests that overlap but are not identical to the needs of developers. 
</p>
<h3><span class="mw-headline" id="Priority">Priority</span></h3>
<p>W3C tests are all treated with equal importance; a test for a primary use case has no more weight than a test for an edge case. The implementation report does not differentiate on which features are the most important for a general overview on browser support.
</p><p>Information should be added to these tests to allow users to assess broad compatibility, with details available for drill-down. For example, tests could be marked <b>critical</b>, <b>important</b>, and <b>edge-case</b> (or given a simple numeric ranking).
</p>
<h3><span class="mw-headline" id="Overview">Overview</span></h3>
<p>Sometimes it's not easy to tell precisely what a test file is testing. Each test should include a human-understandable description of what is being tested, and what the pass criteria are.
</p>
<h3><span class="mw-headline" id="Uniform_format_and_criteria">Uniform format and criteria</span></h3>
<p>Tests from all sources should have agreed-upon sets of formats, testing styles, and pass criteria
</p>
<h3><span class="mw-headline" id="Uniform_reporting">Uniform reporting</span></h3>
<p>Tests from all sources should have a single convention for reporting for <b>pass</b>, <b>fail</b>, and <b>uncertain</b> results, and for identifying the name and version of the user agent and the platform.
</p>
<h2><span class="mw-headline" id="API">API</span></h2>
<p>To integrate the data, there should be an API that allows us to import the data from all of our sources regularly.
</p><p>To be useful to other projects, this API should also allow anyone to query our compatibility data. Like other aspects of WPD, we will use this API ourselves for generating the compatibility tables on the reference pages of WebPlatform.org.
</p>
<h2><span class="mw-headline" id="Timeline">Timeline</span></h2>
<ul><li> <b><a href="/wiki/WPD:Compatibility_Info/Phase_1" title="WPD:Compatibility Info/Phase 1">Phase 1</a>:</b> integrate automated compatibility tables from CanIUse data <i>(March–April 2013)</i></li>
<li> <b><a href="/wiki/WPD:Compatibility_Info/Phase_2" title="WPD:Compatibility Info/Phase 2">Phase 2</a>:</b> integrate MDN data <i>(April–May 2013)</i></li>
<li> <b>Phase 3:</b> normalize and integrate QuirksMode data <i>(April–July 2013)</i></li>
<li> <b>Phase 4:</b> normalize and integrate W3C Test data <i>(August 2013 – March 2014)</i></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:7357-0!*!0!!*!5!*!esi=1 and timestamp 20150731183606 and revision id 31366
 -->
