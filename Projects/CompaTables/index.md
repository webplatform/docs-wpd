= Compatibility Tables ("CompaTables") =

== Summary ==
This document is to define how WebPlatform produce browser compatibility support table in multiple formats; published and within WebPlatform Docs. This document describes the actual implementation status and related conversation describing its status. 

It is expected that the project produce multiple modules, such as: scraping, aggragating, normalizing, publishing and generating HTML blocks and also within our own pages.

To read more about the plans and objectives you can see in the [[#Resources]], read relevant [[#Mail threads]], or follow those links below:
* [[WPD:Compatibility_Info]]
* [[WPD:Compatibility_Info/Phase_1]]
* [[WPD:Compatibility_Info/Phase_2]]

== Agenda ==

# Goals and getting to know the desired outcome
# Analyze what's to be done to push to the production wiki
# Determine and analyze what features are ready, what is missing to make our first release into the production wiki.
# Validate to adjust notes published in both [[WPD:Compatibility_Info/Phase_1]], and [[WPD:Compatibility_Info/Phase_2]]

== Upcoming features ==

'''mdn-compat-importer''':
* Scrape content from MDN, not complete; blocker [https://github.com/webplatform/mdn-compat-importer/issues/3 see issue #3]
* Process and normalize data (living implementation)

'''CompaTables MediaWiki Extension''':
* Generated HTML to leverage ESI tags to help with caching (Varnish)
* Relies on Memcached to save/purge/re-use chunks of HTML
* Reads date of data JSON file, invalidate Memcached version if mismatch
* Allow manage markup-free for various ways to display the information (e.g. in format=table, the version number be in a dd tag, while in format=list it can be in a span tag)
* Support alternate URL for table itself on a page, example:
** [http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&format=table Table in a standard view]
** [http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&format=table&foresi=1 Table alone (used for ESI, see in URL '&foresi=1')]
* Purging a particular table [http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&format=table&action=purge see in URL note '&action=purge']
* Should not break current ESI support feature



== Related ==

=== Published data  ===

* Generated from [https://github.com/webplatform/mdn-compat-importer  MDN Compat Importer], published at [http://docs.webplatform.org/compat/compat-mdn.json compat/compat-mdn.json]
* Directly from caniuse, [http://docs.webplatform.org/compat/data.json data.json]

=== Code repositories ===
* [https://github.com/webplatform/mdn-compat-importer  MDN Compat Importer], by [[User:frozenice]] and [[User:renoirb]]
* [https://github.com/webplatform/mediawiki WebPlatform mediawiki repository], in '''extensions/CompaTables''', by ''[http://www.mediawiki.org/wiki/User:Aaron_Schulz Aaron Schulz]'', [[User:shepazu]] and [[User:Renoirb]]
* [http://webplatform.github.io/browser-compat-model/ Data Model for User Agent Testing], by [[User:Ronaldmansveld]]


=== See also ===
* [https://github.com/dontcallmedom/canmymobilebrowser Can My Mobile Browser] by Dominique Hazael-Massieux, [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0024.html in April 2013, Re: Automatic Data CanIUse Prototype] in file [https://github.com/dontcallmedom/canmymobilebrowser/blob/master/build.py build.py] (yet to be documented)

=== Testing the Compatable feature our pages ===
* [[WPD:Compatibility_Info/Test]]
* On the test wiki at [http://docs.webplatform.org/test/Tests/Compatibility_table_and_caching test/Tests/Compatibility_table_and_caching], bleeding edge version and integration testing


== Resources ==
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


=== Misc. assets ===
* [https://github.com/alrra/browser-logos/ Collection of web browser logos]