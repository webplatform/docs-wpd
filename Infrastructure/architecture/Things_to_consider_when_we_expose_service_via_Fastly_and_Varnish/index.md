{{:WPD:Infrastructure/architecture}}
= Things to consider when we expose service via Fastly and Varnish =

INCOMPLETE

== Mind map ==

* Check for specific headers the backend sends
** Vary
** Cache-Control
** Set-Cookie
** Expires
* Cases when Varnish don’t cache a response
** Client request has a Cookie header
** Backend response has a Set-Cookie header
** Backend response has a Cache-Control: with  private and/or max-age=0 and/or s-max-age=0
* Common problems found in web apps preventing varnish to cache
** Images, JavaScript, CSS 
*** Don’t need Cookie header
***Enforce Cache-Control public with some duration
** MediaWiki:
*** Sends Cache-Control: private too often
*** Expires is in the past in every situations
*** Vary is set with both Cookie and Accept-Encoding. While Cookie is useful if we have no Varnish cache, it doesn’t help us in our context
*** How can we fix MediaWiki behavior  to improve caching in Varnish:
***# Remove backend Cache-Control if `req.http.Cookie !~ "_session="` was sent in request
***# Remove backend Expires header if  `req.http.Cookie !~ "_session="` was sent in request
* Ensure backend has a purging mechanism on page save.
** e.g. after saving /wiki/beginners, send  `http PURGE /wiki/beginners` 
* Ensure static assets (or anything else) isn’t cached until "end of time", when we update content we would be forced to purge every time
* Varnish matches headers explicitly, which means that order and cASING matters
** Space matters: Vary: Accept-Encoding,Cookie  !== Vary: Cookie, Accept-Encoding
**; Order matters: Accept-Encoding: gzip,deflate !== Accept-Encoding: deflate, gzip
**; Casing matters: Accept-Encoding: gzip !== accept-encoding: gzip
* Specific to Fastly
** While Varnish would be OK pass along an Accept-Encoding: gzip, get and cache a Content-Encoding: gzip, Fastly don't. Instead let Fastly get it non compressed, and he’ll compress to the client if the client asks for it. In both cases, only one copy is required for both use cases. #TODO: Validate
** If a backend uses ESI, make sure backend ALWAYS fetches contents non encoded
* Consider which views in web app really needs different render than a cached version
** MediaWiki
***; <code>GET /wiki/Special …</code>: Special pages (using rewrite)
***; <code>GET /w/index.php?title=Special</code>: Special pages (explicit link, without rewrite)
***; <code>GET /w/index.php? … &action=edit …</code>: Edit a page

== Reference == 

* https://www.mnot.net/cache_docs/
* http://www.fastly.com/blog/best-practices-for-using-the-vary-header/
* https://www.varnish-cache.org/docs/trunk/users-guide/increasing-your-hitrate.html#the-role-of-http-headers
* https://www.varnish-cache.org/trac/wiki/VCLExampleLongerCaching
* http://stackoverflow.com/questions/10284813/howto-control-varnish-and-a-browser-using-cache-control-max-age-header-in-a-rai

=== Reference to review ===
==== MediaWiki ====
* [http://www.mediawiki.org/wiki/Manual:Varnish_caching MediaWiki Varnish Caching]
* [http://labs.creativecommons.org/2011/03/18/caching-mediawiki-with-varnish/ Caching mediawiki with varnish]
* [https://www.varnish-cache.org/lists/pipermail/varnish-misc/2012-January/021574.html Default VCL for MediaWiki]

==== Varnish in general ====
* [http://kly.no/varnish/regex.txt Regular expression Cheat sheet]
* [https://www.varnish-cache.org/docs/2.1/genindex.html Varnish documentation]
** [https://www.varnish-cache.org/docs/2.1/tutorial/vcl.html Varnish configuration language]
** [https://www.varnish-cache.org/docs/2.1/tutorial/cookies.html Varnish tutorial cookies]
* [https://www.varnish-software.com/static/book/Tuning.html?highlight=timeout Varnish book about tuning]

==== ESI ====
* [https://www.varnish-cache.org/trac/wiki/ESIfeatures Varnish ESI features]
* [https://www.varnish-cache.org/docs/2.1/tutorial/esi.html Varnish 2.1 ESI doc]

==== Misc. ====
* [http://kly.no/posts/2010_01_08__Hitpass_objects_and_Varnish__.rst Varnish caching, definition of HIT, PASS and other caching lingo]
* [http://docs.fastly.com/guides/21847086 Fastly: Caching tutorials]
** [http://docs.fastly.com/guides/21835572/21744408 Fastly: Removing headers from backend response]
** [http://docs.fastly.com/guides/21835572/23999817 Fastly: Adding and modifying headers]
** [http://docs.fastly.com/guides/21847086/22257776 How to serve stale content in case of origin becoming unavailable]
* [http://docs.fastly.com/guides/21847086/26628787 Fastly tutorial: Cache control]