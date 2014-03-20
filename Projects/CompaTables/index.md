= Compatibility Tables ("CompaTables") =

== Summary ==
This document is to define how WebPlatform produce browser compatibility support table in multiple formats; published and within WebPlatform Docs. This document describes the actual implementation status and related conversation describing its status. 

It is expected that the project produce multiple modules, such as: scraping, aggragating, normalizing, publishing and generating HTML blocks and also within our own pages.

To read more about the plans and objectives you can see in the [[#Resources]], read relevant [[#Mail threads]], or follow those links below:
* [[WPD:Compatibility_Info]]
* [[WPD:Compatibility_Info/Phase_1]]
* [[WPD:Compatibility_Info/Phase_2]]

== Agenda ==

# Analyze [[#Work done]] and [[#To fix or improve]]
# '''Next milestone'''; determine what is ready, and missing to make our first release into the production wiki.
# Validate to adjust status on [[WPD:Compatibility_Info/Phase_1]], and [[WPD:Compatibility_Info/Phase_2]]
# Technical chat: '''What's to be done''' and who can do what

=== Work done ===

'''mdn-compat-importer''':
* Process and normalize data (living implementation)

'''CompaTables MediaWiki Extension''':
* Implement mdn-compat-importer ''[[#Current normalized data|]]'' (living implementation)
* Relies on Memcached to save/purge/re-use chunks of HTML
* Allow manage markup-free text arrays (e.g. in format=table, the word "Unsupported" be in a dd tag, while in format=list it can be in a abbr tag)
* Support alternate URL for table itself on its own view:
** [http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&format=table Table in a standard view]
** [http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&format=table&foresi=1 Table alone (used for ESI, see in URL '&foresi=1')]
* Purging Memcached version of generated HTML views:
** When origin JSON file date changes mismatch cached version
** Purging a particular table directly, along with ESI purging mechanism  [http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&format=table&action=purge see in URL note '&action=purge']
* Should not break current ESI support feature
* Rudimentary A11y markup (needs testing). Done according to [http://www.w3.org/TR/WCAG10-HTML-TECHS/#identifying-table-rows-columns this WCAG1 checkpoint]

=== To fix or improve ===
==== Figure out where ====
* How we want to display the available prefixes? [[#Prefixes, potential resources]]

==== mdn-compat-importer ====
* Scrape content from MDN, not complete; blocker [https://github.com/webplatform/mdn-compat-importer/issues/3 see issue #3]
* Ensure browser are sorted in alphebetical order and ensure features are matching accordingly

==== CompaTables MediaWiki Extension ====
* List view format (format=list) is not using latest ''[[#Current normalized data|]]'' 
* Table view format 
** doesn't show prefix icons (e.g. -webkit)

==== ESI ====
To use ESI, work has to be done on the servers. To summarize the findings, we cannot enable ESI tags on Fastly as it is at the moment due to a set of factors:

Fastly's Varnish version (2.1.5) doesn't support gzip between backend and varnish; (but Varnish 3.x+ do.)
* Between our servers ("backend") and Fastly we use currently compress with gzip
* Varnish has plans to upgrade their varnish, but its out of our hands

To enable;
* Disable gzip between our backend servers and Fastly (might increase the data transfer usage, to validate with fastly)
* Enable gzip only from Fastly to our visitors (currently gzip is in both places)


== Related ==

=== Published data  ===
==== Current normalized data ====
* Generated from [https://github.com/webplatform/mdn-compat-importer  MDN Compat Importer], published at [http://docs.webplatform.org/compat/compat-mdn.json compat/compat-mdn.json]

==== Original data format ====
* Directly from caniuse, [http://docs.webplatform.org/compat/data.json data.json]

=== Code repositories ===
* [https://github.com/webplatform/mdn-compat-importer  MDN Compat Importer], by [[User:frozenice]] and [[User:renoirb]]
* [https://github.com/webplatform/mediawiki WebPlatform mediawiki repository], in '''extensions/CompaTables''', by ''[http://www.mediawiki.org/wiki/User:Aaron_Schulz Aaron Schulz]'', [[User:shepazu]] and [[User:Renoirb]]
* [http://webplatform.github.io/browser-compat-model/ Data Model for User Agent Testing], by [[User:Ronaldmansveld]] and [http://blog.tobie.me/ Tobie Langel]


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


=== Prefixes, potential resources ===
* http://www.w3.org/TR/CSS21/syndata.html#vendor-keyword-history
* http://peter.sh/experiments/vendor-prefixed-css-property-overview/
* https://github.com/ai/autoprefixer
**  https://github.com/ai/autoprefixer/tree/master/lib/hacks
** https://github.com/ai/autoprefixer/blob/master/updaters/prefixes.coffee
** https://github.com/ai/autoprefixer/blob/master/updaters/browsers.coffee


=== Misc. assets ===
* [https://github.com/alrra/browser-logos/ Collection of web browser logos]