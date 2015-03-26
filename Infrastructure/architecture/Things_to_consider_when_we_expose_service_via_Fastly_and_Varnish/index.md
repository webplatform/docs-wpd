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

* http://www.fastly.com/blog/best-practices-for-using-the-vary-header/
* https://www.varnish-cache.org/docs/trunk/users-guide/increasing-your-hitrate.html#the-role-of-http-headers
* https://www.varnish-cache.org/trac/wiki/VCLExampleLongerCaching
* http://stackoverflow.com/questions/10284813/howto-control-varnish-and-a-browser-using-cache-control-max-age-header-in-a-rai