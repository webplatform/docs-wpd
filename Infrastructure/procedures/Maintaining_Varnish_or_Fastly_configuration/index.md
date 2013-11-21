== Summary ==
This page is about keeping notes on current Varnish configuration fils and notes to help maintaining an appropriate caching strategy. 

== Details to remember ==
An important detail to remember is that Fastly is using Varnish 2.1.4, do not support pipe, ban, nor purging with ACL. 

Also, they provide a feature called 'Shield' that is basically an ad-hoc backend that keeps a local copy of what gets cached and is served instead of using the backend, this is what makes it be also act like a CDN.

A recommended way to work is to follow '''[https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL-  How do I mix and match Fastly VCL with custom VCL]'''

== Links ==
* [http://www.mediawiki.org/wiki/Manual:Varnish_caching MediaWiki Varnish Caching]
* [http://labs.creativecommons.org/2011/03/18/caching-mediawiki-with-varnish/ Caching mediawiki with varnish]
* [https://www.varnish-cache.org/lists/pipermail/varnish-misc/2012-January/021574.html Default VCL for MediaWiki]
* [https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL- Fastly: How to mix and match Fastly VCL with custom VCL (Varnish configuration file)]
* [http://kly.no/posts/2010_01_08__Hitpass_objects_and_Varnish__.rst Varnish caching, definition of HIT, PASS and other caching lingo]
* [http://docs.fastly.com/guides/21847086 Fastly: Caching tutorials]
** [http://docs.fastly.com/guides/21835572/21744408 Fastly: Removing headers from backend response]
** [http://docs.fastly.com/guides/21835572/23999817 Fastly: Adding and modifying headers]
** [http://docs.fastly.com/guides/21847086/22257776 How to serve stale content in case of origin becoming unavailable]
* [http://docs.fastly.com/guides/21847086/26628787 Fastly tutorial: Cache control]
* [https://www.varnish-cache.org/docs/2.1/genindex.html Varnish documentation]
** [https://www.varnish-cache.org/docs/2.1/tutorial/vcl.html Varnish configuration language]
** [https://www.varnish-cache.org/docs/2.1/tutorial/cookies.html Varnish tutorial cookies]
* [https://www.varnish-software.com/static/book/Tuning.html?highlight=timeout Varnish book about tuning]

== Attached documents ==
* [https://gist.github.com/renoirb/7586240 20131121.vcl]