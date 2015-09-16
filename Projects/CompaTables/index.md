---
title: Compatibility Tables ("CompaTables")
uri: 'WPD:Projects/CompaTables'

---
## Summary

This document is to define how WebPlatform produce browser compatibility support table in multiple formats; published and within WebPlatform Docs. This document describes the actual implementation status and related conversation describing its status.

It is expected that the project produce multiple modules, such as: scraping, aggragating, normalizing, publishing and generating HTML blocks and also within our own pages.

To read more about the plans and objectives you can see in the [\#Resources](#Resources), read relevant [\#Mail threads](#Mail_threads), or follow those links below:

-   [WPD:Compatibility\_Info](/WPD:Compatibility_Info)
-   [WPD:Compatibility\_Info/Phase\_1](/WPD:Compatibility_Info/Phase_1)
-   [WPD:Compatibility\_Info/Phase\_2](/WPD:Compatibility_Info/Phase_2)
-   [WPD:Infrastructure/Components/CompaTables](/WPD:Infrastructure/Components/CompaTables)

## Past sprints

-   **Mar. 2014** [WPD:Projects/CompaTables/201403-sprint\#Work done](/WPD:Projects/CompaTables/201403-sprint#Work_done)
-   **Aug. 2014**; Imported all content from MDN, published on github [**webplatform/compatibility-data**](https://github.com/webplatform/compatibility-data)
-   **Sept. 2014**
    -   Compatibility HTML table rendering extension deployed ([see code in **webplatform/mediawiki/../Compatables** MediaWiki extension](https://github.com/webplatform/mediawiki/tree/master/extensions/Compatables))
    -   MediaWiki template we are using within our content is [*Template:Compatibility*](http://docs.webplatform.org/wiki/Template:Compatibility)
    -   Notes on where we installed the template calls in [WPD:Projects/CompaTables/Adding\_to\_our\_content](/WPD:Projects/CompaTables/Adding_to_our_content)

### To fix or improve

-   See [WPD:Projects/CompaTables/201403-sprint\#To fix or improve](/WPD:Projects/CompaTables/201403-sprint#To_fix_or_improve)

## Related

### Published data

-   Generated from [MDN Compat Importer](https://github.com/webplatform/mdn-compat-importer)
-   Data is available as [**webplatform/compatibility-data** on GitHub](https://github.com/webplatform/compatibility-data)
    -   Available as [compat/data.json](http://docs.webplatform.org/compat/data.json),
    -   Also available in "human-friendly" format as [compat/data-human.json](http://docs.webplatform.org/compat/data-human.json)

### Code repositories

-   [Compatibility data](https://github.com/webplatform/compatibility-data)
-   [MDN Compat Importer](https://github.com/webplatform/mdn-compat-importer), by [User:frozenice](/User:Frozenice) and [User:renoirb](/User:Renoirb)
-   [WebPlatform mediawiki repository](https://github.com/webplatform/mediawiki), in **extensions/CompaTables**, by *[Aaron Schulz](http://www.mediawiki.org/wiki/User:Aaron_Schulz)*, [User:shepazu](/User:Shepazu) and [User:Renoirb](/User:Renoirb)
-   [Data Model for User Agent Testing](http://webplatform.github.io/browser-compat-model/), by [User:Ronaldmansveld](/User:Ronaldmansveld) and [Tobie Langel](http://blog.tobie.me/)

### See also

-   [Can My Mobile Browser](https://github.com/dontcallmedom/canmymobilebrowser) by Dominique Hazael-Massieux, [in April 2013, Re: Automatic Data CanIUse Prototype](http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0024.html) in file [build.py](https://github.com/dontcallmedom/canmymobilebrowser/blob/master/build.py) (yet to be documented)
-   Query the *data.json* file through the command line [WPD:Projects/CompaTables/Reading\_the\_data.json\_file](/WPD:Projects/CompaTables/Reading_the_data.json_file)

### Testing the Compatable feature our pages

-   [WPD:Compatibility\_Info/Test](/WPD:Compatibility_Info/Test)
-   On the test wiki at [test/Tests/Compatibility\_table\_and\_caching](http://docs.webplatform.org/test/Tests/Compatibility_table_and_caching), bleeding edge version and integration testing

## Resources

-   [*public-webplatform-tests* dedicated mailing list](http://lists.w3.org/Archives/Public/public-webplatform-tests/)
-   [Test the Web Forward](http://testthewebforward.org/)
-   [W3C browser test suites](https://github.com/w3c/web-platform-tests)
-   [W3C Mobile "web app state"](http://www.w3.org/Mobile/mobile-web-app-state/) maintained by Dominique Hazael-Massieux

### Mail threads

-   [WebPlatform Browser Support Info](http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0027.html)
    -   [WebPlatform Browser Support Info](http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0029.html)
-   [Oct. 17 2013, WebPlatform Browser Support Info](http://lists.w3.org/Archives/Public/public-webplatform-tests/2013OctDec/0000.html)
-   [March 2013, Re: Automatic Data CanIUse Prototype](http://lists.w3.org/Archives/Public/public-webplatform/2013Mar/0345.html)
    -   [April 2013, Re: Automatic Data CanIUse Prototype](http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0016.html)
    -   [April 2013, Re: Automatic Data CanIUse Prototype](http://lists.w3.org/Archives/Public/public-webplatform/2013Apr/0024.html) answer by Dominique Hazael-Massieux
-   [Jan 2014, Converting MDN Compat Data to JSON](http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0017.html)
    -   [Jan 2014, Re: Converting MDN Compat Data to JSON](http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0030.html)
-   [Jan. 27 2014, MDN Compat data project w/ Jeremie Patronnier](http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0136.html)
    -   [Jan. 30 2014](http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0165.html)
    -   [Jan. 27 2014, by Janet](http://lists.w3.org/Archives/Public/public-webplatform/2014Jan/0130.html)
-   [Feb. 07 2014, Compat Table Progress](http://lists.w3.org/Archives/Public/public-webplatform/2014Feb/0051.html)
-   [May 21 2014, Compat Table Data from MDN](http://lists.w3.org/Archives/Public/public-webplatform-tests/2014AprJun/0000.html)
-   [Sept. 13 2014, Upcoming compatibility table update](http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0041.html) (i.e. displaying the compatibility data from within the wiki)
    -   [(continued)](http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0044.html)
    -   [(continued)](http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0045.html)
    -   [(continued)](http://lists.w3.org/Archives/Public/public-webplatform/2014Sep/0050.html)

### Prefixes, potential resources

-   <http://www.w3.org/TR/CSS21/syndata.html#vendor-keyword-history>
-   <http://peter.sh/experiments/vendor-prefixed-css-property-overview/>
-   <https://github.com/ai/autoprefixer>
    -   <https://github.com/ai/autoprefixer/tree/master/lib/hacks>
    -   <https://github.com/ai/autoprefixer/blob/master/updaters/prefixes.coffee>
    -   <https://github.com/ai/autoprefixer/blob/master/updaters/browsers.coffee>

### Misc. assets

-   [Collection of web browser logos](https://github.com/alrra/browser-logos/)
