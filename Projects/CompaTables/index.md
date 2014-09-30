= Compatibility Tables ("CompaTables") =

== Summary ==
This document is to define how WebPlatform produce browser compatibility support table in multiple formats; published and within WebPlatform Docs. This document describes the actual implementation status and related conversation describing its status. 

It is expected that the project produce multiple modules, such as: scraping, aggragating, normalizing, publishing and generating HTML blocks and also within our own pages.

To read more about the plans and objectives you can see in the [[#Resources]], read relevant [[#Mail threads]], or follow those links below:
* [[WPD:Compatibility_Info]]
* [[WPD:Compatibility_Info/Phase_1]]
* [[WPD:Compatibility_Info/Phase_2]]
* [[WPD:Infrastructure/Components/CompaTables]]

== Past sprints ==
* Sprint 2014-03, see [[WPD:Projects/CompaTables/201403-sprint#Work done]]
* Aug. 2014; Imported all content from MDN, published on github [https://github.com/webplatform/compatibility-data '''webplatform/compatibility-data''']
* Sept. 2014
** Compatibility HTML table rendering extension deployed ([https://github.com/webplatform/mediawiki/tree/master/extensions/Compatables see code in '''webplatform/mediawiki/../Compatables''' MediaWiki extension])
** MediaWiki template we are using within our content is [http://docs.webplatform.org/wiki/Template:Compatibility ''Template:Compatibility''] 
** Notes on where we installed the template calls in [[WPD:Projects/CompaTables/Adding_to_our_content]]

=== To fix or improve ===
* See [[WPD:Projects/CompaTables/201403-sprint#To fix or improve]]

== Related ==

=== Published data  ===
* Generated from [https://github.com/webplatform/mdn-compat-importer  MDN Compat Importer]
* Data is available as [https://github.com/webplatform/compatibility-data '''webplatform/compatibility-data''' on GitHub]
** Available as [http://docs.webplatform.org/compat/data.json compat/data.json], 
** Also available in "human-friendly" format as  [http://docs.webplatform.org/compat/data-human.json compat/data-human.json]


=== Code repositories ===
* [https://github.com/webplatform/compatibility-data Compatibility data]
* [https://github.com/webplatform/mdn-compat-importer  MDN Compat Importer], by [[User:frozenice]] and [[User:renoirb]]
* [https://github.com/webplatform/mediawiki WebPlatform mediawiki repository], in '''extensions/CompaTables''', by ''[http://www.mediawiki.org/wiki/User:Aaron_Schulz Aaron Schulz]'', [[User:shepazu]] and [[User:Renoirb]]
* [http://webplatform.github.io/browser-compat-model/ Data Model for User Agent Testing], by [[User:Ronaldmansveld]] and [http://blog.tobie.me/ Tobie Langel]


=== See also ===
* [https://github.com/dontcallmedom/canmymobilebrowser Can My Mobile Browser] by Dominique Hazael-Massieux, [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0024.html in April 2013, Re: Automatic Data CanIUse Prototype] in file [https://github.com/dontcallmedom/canmymobilebrowser/blob/master/build.py build.py] (yet to be documented)
* Query the ''data.json'' file through the command line [[WPD:Projects/CompaTables/Reading_the_data.json_file]]

=== Testing the Compatable feature our pages ===
* [[WPD:Compatibility_Info/Test]]
* On the test wiki at [http://docs.webplatform.org/test/Tests/Compatibility_table_and_caching test/Tests/Compatibility_table_and_caching], bleeding edge version and integration testing


== Resources ==
* [http://lists.w3.org/Archives/Public/public-webplatform-tests/ ''public-webplatform-tests'' dedicated mailing list]
* [http://testthewebforward.org/ Test the Web Forward]
* [https://github.com/w3c/web-platform-tests W3C browser test suites]
* [http://www.w3.org/Mobile/mobile-web-app-state/ W3C Mobile "web app state"] maintained by Dominique Hazael-Massieux

=== Mail threads ===

* [http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0027.html WebPlatform Browser Support Info]
** [http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0029.html WebPlatform Browser Support Info]
* [http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0000.html Oct. 17 2013, WebPlatform Browser Support Info]
* [http://lists.w3.org/Archives/Public/public-webplatform/2013Mar/0345.html March 2013,  Re: Automatic Data CanIUse Prototype]
** [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0016.html April 2013,  Re: Automatic Data CanIUse Prototype]
** [http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0024.html April 2013, Re: Automatic Data CanIUse Prototype] answer by Dominique Hazael-Massieux
* [http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0017.html Jan 2014, Converting MDN Compat Data to JSON]
** [http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0030.html Jan 2014, Re: Converting MDN Compat Data to JSON]
* [http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0136.html Jan. 27 2014, MDN Compat data project w/ Jeremie Patronnier]
** [http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0165.html Jan. 30 2014]
** [http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0130.html Jan. 27 2014, by Janet]
* [http://lists.w3.org/Archives/Public/public-webplatform/2014Feb/0051.html Feb. 07 2014, Compat Table Progress]
* [http://lists.w3.org/Archives/Public/public-webplatform-tests/2014AprJun/0000.html May 21 2014, Compat Table Data from MDN]
* [http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0041.html Sept. 13 2014, Upcoming compatibility table update] (i.e. displaying the compatibility data from within the wiki)
** [http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0044.html (continued)]
** [http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0045.html (continued)]
** [http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0050.html (continued)]


=== Prefixes, potential resources ===
* http://www.w3.org/TR/CSS21/syndata.html#vendor-keyword-history
* http://peter.sh/experiments/vendor-prefixed-css-property-overview/
* https://github.com/ai/autoprefixer
**  https://github.com/ai/autoprefixer/tree/master/lib/hacks
** https://github.com/ai/autoprefixer/blob/master/updaters/prefixes.coffee
** https://github.com/ai/autoprefixer/blob/master/updaters/browsers.coffee


=== Misc. assets ===
* [https://github.com/alrra/browser-logos/ Collection of web browser logos]