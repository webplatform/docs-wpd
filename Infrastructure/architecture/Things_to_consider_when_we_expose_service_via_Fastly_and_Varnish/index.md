---
title: 'Things to consider when we expose service via Fastly and Varnish'
uri: 'WPD:Infrastructure/architecture/Things to consider when we expose service via Fastly and Varnish'

---
### [WebPlatform server Infrastructure architecture menu](/WPD:Infrastructure/architecture)

-   [Base configuration of a VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM)
-   [Reports to review status](/WPD:Infrastructure/architecture/Reports_to_review_status)
-   [Roles and environment level](/WPD:Infrastructure/architecture/Roles_and_environment_level)
-   [SSL certificates](/WPD:Infrastructure/architecture/SSL_certificates)
-   [The salt master](/WPD:Infrastructure/architecture/The_salt_master)
-   **Things to consider when we expose service via Fastly and Varnish**
-   [Useful commands](/WPD:Infrastructure/architecture/Useful_commands)
-   [VM roles](/WPD:Infrastructure/architecture/VM_roles)

**See also**

-   [Deploying code changes](/WPD:Infrastructure/procedures/Deploying_code_changes)
-   [Replacing a VM](/WPD:Infrastructure/procedures/Replacing_a_VM)
-   [Maintaining Fastly configuration](/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration)
-   [Managing MySQL replication](/WPD:Infrastructure/procedures/Managing_MySQL_replication)
-   [Create new database credentials and configure a web application to use it](/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it)
-   [Maintaining ElasticSearch cluster](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster)
-   [Maintaining email services](/WPD:Infrastructure/procedures/Maintaining_email_services)

Not finished, see also [our GitHub **webplatform/varnish-configs** project](http://github.com/webplatform/varnish-configs)

## Mind map

-   Check for specific headers the backend sends
    -   Vary
    -   Cache-Control
    -   Set-Cookie
    -   Expires
-   Cases when Varnish don’t cache a response
    -   Client request has a Cookie header
    -   Backend response has a Set-Cookie header
    -   Backend response has a Cache-Control: with private and/or max-age=0 and/or s-max-age=0
-   Common problems found in web apps preventing varnish to cache
    -   Images, JavaScript, CSS
        -   Don’t need Cookie header
        -   Enforce Cache-Control public with some duration
    -   MediaWiki:
        -   Sends Cache-Control: private too often
        -   Expires is in the past in every situations
        -   Vary is set with both Cookie and Accept-Encoding. While Cookie is useful if we have no Varnish cache, it doesn’t help us in our context
        -   How can we fix MediaWiki behavior to improve caching in Varnish:
            1.  Remove backend Cache-Control if \`req.http.Cookie !\~ "\_session="\` was sent in request
            2.  Remove backend Expires header if \`req.http.Cookie !\~ "\_session="\` was sent in request
-   Ensure backend has a purging mechanism on page save.
    -   e.g. after saving /wiki/beginners, send \`http PURGE /wiki/beginners\`
-   Ensure static assets (or anything else) isn’t cached until "end of time", when we update content we would be forced to purge every time
-   Varnish matches headers explicitly, which means that order and cASING matters
    -   Space matters: Vary: Accept-Encoding,Cookie  !== Vary: Cookie, Accept-Encoding
         Order matters
        :   Accept-Encoding: gzip,deflate !== Accept-Encoding: deflate, gzip
         Casing matters
        :   Accept-Encoding: gzip !== accept-encoding: gzip
-   Specific to Fastly
    -   While Varnish would be OK pass along an Accept-Encoding: gzip, get and cache a Content-Encoding: gzip, Fastly don't. Instead let Fastly get it non compressed, and he’ll compress to the client if the client asks for it. In both cases, only one copy is required for both use cases. \#TODO: Validate
    -   If a backend uses ESI, make sure backend ALWAYS fetches contents non encoded
-   Consider which views in web app really needs different render than a cached version
    -   MediaWiki
        -    `GET /wiki/Special …`
            :   Special pages (using rewrite)
             `GET /w/index.php?title=Special`
            :   Special pages (explicit link, without rewrite)
             `GET /w/index.php? … &action=edit …`
            :   Edit a page

## Caveats

remove "Cookie" from backend’s Vary response header
:   Vary header can create non-required alternate versions of a page render. Since Varnish already handles a request with a cookie, it doesn’t need to "vary on cookie". Only valid "Vary" we need for now is "Vary: Content-Encoding". If we were serving same page, but with different languages we could add also add "Accept-Language"
make sure "Vary" and "Accept-Encoding" possible values are harmonized
:   Anything in Varnish is very explicit. If a condition reads directly an arbitrary "Accept-Encoding" request parameter without filtering it could make un needed different versions.
do some headers cleaning if a web application breaks caching
:   What is called *Cache "HIT ratio"* is a metric used in HTTP caching to tell how many times it didn’t serve a cached request. Caching is prevent if one or more of the following exists in the backend response sent back to Varnish: Authorization, Set-Cookie, Cache-Control that contains *max-age=0* or similar and Vary with "cookie". If a given page has NO possible changes whatsoever between a request with cookies or not, it is therefore safe to remove those headers.
remove non needed cookies from a request to a backend that doesn’t need them
:   Its important it is to configure Varnish to clean cookies it sends to our backend servers. Otherwise we do not have cache at all. The cleaning must be done for each backend because, for example, WordPress cookies wouldn’t be the same as MediaWiki’s. In order to not lose the subtleties, we published all Varnish VCLs into GitHub at [webplatform/varnish-configs](https://github.com/webplatform/varnish-configs).

## Reference

-   <https://www.mnot.net/cache_docs/>
-   <http://www.fastly.com/blog/best-practices-for-using-the-vary-header/>
-   <https://www.varnish-cache.org/docs/trunk/users-guide/increasing-your-hitrate.html#the-role-of-http-headers>
-   <https://www.varnish-cache.org/trac/wiki/VCLExampleLongerCaching>
-   <http://stackoverflow.com/questions/10284813/howto-control-varnish-and-a-browser-using-cache-control-max-age-header-in-a-rai>

### See also in our pages

-   [analysis; 2015, How MediaWiki backend sees requests with and without *Fastly* in front](/WPD:Infrastructure/analysis/2015-How_MediaWiki_backend_sees_requests_with_or_without_Fastly_in_front)

### Reference to review

-   <https://www.mobify.com/blog/beginners-guide-to-http-cache-headers/>

#### MediaWiki

-   [MediaWiki Varnish Caching](http://www.mediawiki.org/wiki/Manual:Varnish_caching)
-   [Caching mediawiki with varnish](http://labs.creativecommons.org/2011/03/18/caching-mediawiki-with-varnish/)
-   [Default VCL for MediaWiki](https://www.varnish-cache.org/lists/pipermail/varnish-misc/2012-January/021574.html)

#### Varnish in general

-   [Regular expression Cheat sheet](http://kly.no/varnish/regex.txt)
-   [Varnish documentation](https://www.varnish-cache.org/docs/2.1/genindex.html)
    -   [Varnish configuration language](https://www.varnish-cache.org/docs/2.1/tutorial/vcl.html)
    -   [Varnish tutorial cookies](https://www.varnish-cache.org/docs/2.1/tutorial/cookies.html)
-   [Varnish book about tuning](https://www.varnish-software.com/static/book/Tuning.html?highlight=timeout)

#### ESI

-   [Varnish ESI features](https://www.varnish-cache.org/trac/wiki/ESIfeatures)
-   [Varnish 2.1 ESI doc](https://www.varnish-cache.org/docs/2.1/tutorial/esi.html)

#### Misc.

-   [Varnish caching, definition of HIT, PASS and other caching lingo](http://kly.no/posts/2010_01_08__Hitpass_objects_and_Varnish__.rst)
-   [Fastly: Caching tutorials](http://docs.fastly.com/guides/21847086)
    -   [Fastly: Removing headers from backend response](http://docs.fastly.com/guides/21835572/21744408)
    -   [Fastly: Adding and modifying headers](http://docs.fastly.com/guides/21835572/23999817)
    -   [How to serve stale content in case of origin becoming unavailable](http://docs.fastly.com/guides/21847086/22257776)
-   [Fastly tutorial: Cache control](http://docs.fastly.com/guides/21847086/26628787)
