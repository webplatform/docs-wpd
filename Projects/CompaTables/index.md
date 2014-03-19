<div class='note'>'''NOTE''' Project is ongoing</div>

= Compatibility Tables ("CompaTables") =

== Abstract ==

This document is to define how WebPlatform will publish browser compatibility to support of a given feature for the web developers. WebPlatform Docs should eventually be able to aggregate and publish support information based on multiple data sources, including interpretation of test results provided by ''W3C's Test Suites for Web Platform specifications''.

=== Goals overview ===
[http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0000.html Excerpt from "Oct 2013, WebPlatform Browser Support Info"], by [[User:Shepazu|Shepazu]]

<blockquote>
Current Goals:
* create unified data model (probably JSON)
* integrate data from different sites into that data store
* provide an API for that data
* create a scalable extension for WebPlatform.org to show compat data on 
our pages
* find the right level of granularity to display results in different 
contexts (e.g., quicklook, detailed tables of current information, drill 
down view into different data sources)
* help automate QuirksMode's infrastructure

Non-goals for WebPlatform.org:
* testing user's browsers
* collecting stats on browser usage for compat (uselessly skewed on a 
site aimed at web developers)

Possible future goals:
* report browser statistics (from best source... Akamai? netstats?)
* report results for game consoles, set-top boxes, TVs, etc.
</blockquote>


== Related ==
To get up to speed on other traces of the project.

=== Code repositories ===
* [https://github.com/webplatform/mdn-compat-importer  MDN Compat Importer], by [[User:frozenice]] and [[User:renoirb]]
* [https://github.com/webplatform/mediawiki WebPlatform mediawiki repository]], in '''extensions/CompaTables''', by ''[http://www.mediawiki.org/wiki/User:Aaron_Schulz Aaron Schulz]'', [[User:shepazu]] and [[User:Renoirb]]
* [http://webplatform.github.io/browser-compat-model/ Data Model for User Agent Testing], by [[User:Ronaldmansveld]]


==== See also ====
* [https://github.com/dontcallmedom/canmymobilebrowser Can My Mobile Browser] by Dominique Hazael-Massieux, [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0024.html in April 2013, Re: Automatic Data CanIUse Prototype] in file [https://github.com/dontcallmedom/canmymobilebrowser/blob/master/build.py build.py] (yet to be documented)


=== Other related documents ===
* [[WPD:Compatibility_Info]]
* [[WPD:Compatibility_Info/Phase_1]]
* [[WPD:Compatibility_Info/Phase_2]]


=== Testing the Compatable feature our pages ===
* [[WPD:Compatibility_Info/Test]]
* On the test wiki at [http://docs.webplatform.org/test/Tests/Compatibility_table_and_caching test/Tests/Compatibility_table_and_caching], bleeding edge version and integration testing


=== Resources ===
* [http://lists.w3.org/Archives/Public/public-webplatform-tests/ ''public-webplatform-tests'' dedicated mailing list]
* [http://testthewebforward.org/ Test the Web Forward]
* [https://github.com/w3c/web-platform-tests W3C browser test suites]
* [http://www.w3.org/Mobile/mobile-web-app-state/ W3C Mobile "web app state"] maintained by Dominique Hazael-Massieux


=== Mail threads ===
* [http://lists.w3.org/Archives/Public/public-webplatform/2014Feb/0051.html Feb 2014, Compat Table Progress]
* [http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0165.html Jan 2014, Converting MDN Compat Data to JSON]
* [http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0017.html Jan 2014, Converting MDN Compat Data to JSON]
** [http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0030.html Jan 2014, Re: Converting MDN Compat Data to JSON]
* [http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0027.html WebPlatform Browser Support Info]
** [http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0029.html WebPlatform Browser Support Info]
* [http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0000.html Oct 2013, WebPlatform Browser Support Info]
* [http://lists.w3.org/Archives/Public/public-webplatform/2013Mar/0345.html March 2013,  Re: Automatic Data CanIUse Prototype]
** [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0016.html April 2013,  Re: Automatic Data CanIUse Prototype]
** [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0024.html April 2013, Re: Automatic Data CanIUse Prototype] answer by Dominique Hazael-Massieux


== Misc. assets ==
* [https://github.com/alrra/browser-logos/ Collection of web browser logos]