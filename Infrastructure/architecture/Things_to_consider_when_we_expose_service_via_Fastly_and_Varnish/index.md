---
title: WPD:Infrastructure/architecture/Things to consider when we expose service via Fastly and Varnish
---
<div style="float:right;width:33%;word-wrap:break-word;clear:both;">
<h3><span class="mw-headline" id="WebPlatform_server_Infrastructure_architecture_menu"><a href="/wiki/WPD:Infrastructure/architecture" title="WPD:Infrastructure/architecture">WebPlatform server Infrastructure architecture menu</a></span></h3>
<div class="subpagelist">
<ul><li> <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM" title="WPD:Infrastructure/architecture/Base configuration of a VM">Base configuration of a VM</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status" title="WPD:Infrastructure/architecture/Reports to review status">Reports to review status</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Roles_and_environment_level" title="WPD:Infrastructure/architecture/Roles and environment level">Roles and environment level</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/SSL_certificates" title="WPD:Infrastructure/architecture/SSL certificates">SSL certificates</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/The_salt_master" title="WPD:Infrastructure/architecture/The salt master">The salt master</a></li>
<li> <strong class="selflink">Things to consider when we expose service via Fastly and Varnish</strong></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Useful_commands" title="WPD:Infrastructure/architecture/Useful commands">Useful commands</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/VM_roles" title="WPD:Infrastructure/architecture/VM roles">VM roles</a></div></li></ul>
<p><b>See also</b>
</p>
<ul><li> <a href="/wiki/WPD:Infrastructure/procedures/Deploying_code_changes" title="WPD:Infrastructure/procedures/Deploying code changes">Deploying code changes</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Replacing_a_VM" title="WPD:Infrastructure/procedures/Replacing a VM">Replacing a VM</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration" title="WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration">Maintaining Fastly configuration</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Managing_MySQL_replication" title="WPD:Infrastructure/procedures/Managing MySQL replication">Managing MySQL replication</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it" title="WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it">Create new database credentials and configure a web application to use it</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">Maintaining ElasticSearch cluster</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_email_services" title="WPD:Infrastructure/procedures/Maintaining email services">Maintaining email services</a></li></ul>
</div>
<h1><span class="mw-headline" id="Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish">Things to consider when we expose service via Fastly and Varnish</span></h1>
<p>Not finished, see also <a rel="nofollow" class="external text" href="http://github.com/webplatform/varnish-configs">our GitHub <b>webplatform/varnish-configs</b> project</a>
</p>
<h2><span class="mw-headline" id="Mind_map">Mind map</span></h2>
<ul><li> Check for specific headers the backend sends
<ul><li> Vary</li>
<li> Cache-Control</li>
<li> Set-Cookie</li>
<li> Expires</li></ul></li>
<li> Cases when Varnish don’t cache a response
<ul><li> Client request has a Cookie header</li>
<li> Backend response has a Set-Cookie header</li>
<li> Backend response has a Cache-Control: with  private and/or max-age=0 and/or s-max-age=0</li></ul></li>
<li> Common problems found in web apps preventing varnish to cache
<ul><li> Images, JavaScript, CSS 
<ul><li> Don’t need Cookie header</li>
<li>Enforce Cache-Control public with some duration</li></ul></li>
<li> MediaWiki:
<ul><li> Sends Cache-Control: private too often</li>
<li> Expires is in the past in every situations</li>
<li> Vary is set with both Cookie and Accept-Encoding. While Cookie is useful if we have no Varnish cache, it doesn’t help us in our context</li>
<li> How can we fix MediaWiki behavior  to improve caching in Varnish:
<ol><li> Remove backend Cache-Control if `req.http.Cookie&#160;!~ "_session="` was sent in request</li>
<li> Remove backend Expires header if  `req.http.Cookie&#160;!~ "_session="` was sent in request</li></ol></li></ul></li></ul></li>
<li> Ensure backend has a purging mechanism on page save.
<ul><li> e.g. after saving /wiki/beginners, send  `http PURGE /wiki/beginners` </li></ul></li>
<li> Ensure static assets (or anything else) isn’t cached until "end of time", when we update content we would be forced to purge every time</li>
<li> Varnish matches headers explicitly, which means that order and cASING matters
<ul><li> Space matters: Vary: Accept-Encoding,Cookie &#160;!== Vary: Cookie, Accept-Encoding
<dl><dt> Order matters</dt>
<dd> Accept-Encoding: gzip,deflate&#160;!== Accept-Encoding: deflate, gzip</dd>
<dt> Casing matters</dt>
<dd> Accept-Encoding: gzip&#160;!== accept-encoding: gzip</dd></dl></li></ul></li>
<li> Specific to Fastly
<ul><li> While Varnish would be OK pass along an Accept-Encoding: gzip, get and cache a Content-Encoding: gzip, Fastly don't. Instead let Fastly get it non compressed, and he’ll compress to the client if the client asks for it. In both cases, only one copy is required for both use cases. #TODO: Validate</li>
<li> If a backend uses ESI, make sure backend ALWAYS fetches contents non encoded</li></ul></li>
<li> Consider which views in web app really needs different render than a cached version
<ul><li> MediaWiki
<ul><li><dl><dt> <code>GET /wiki/Special …</code></dt>
<dd> Special pages (using rewrite)</dd>
<dt> <code>GET /w/index.php?title=Special</code></dt>
<dd> Special pages (explicit link, without rewrite)</dd>
<dt> <code>GET /w/index.php? … &amp;action=edit …</code></dt>
<dd> Edit a page</dd></dl></li></ul></li></ul></li></ul>
<h2><span class="mw-headline" id="Caveats">Caveats</span></h2>
<dl><dt>remove "Cookie" from backend’s Vary response header</dt>
<dd> Vary header can create non-required alternate versions of a page render. Since Varnish already handles a request with a cookie, it doesn’t need to "vary on cookie". Only valid "Vary" we need for now is "Vary: Content-Encoding". If we were serving same page, but with different languages we could add also add "Accept-Language"</dd>
<dt>make sure "Vary" and "Accept-Encoding" possible values are harmonized</dt>
<dd> Anything in Varnish is very explicit. If a condition reads directly an arbitrary "Accept-Encoding" request parameter without filtering it could make un needed different versions. </dd>
<dt>do some headers cleaning if a web application breaks caching</dt>
<dd> What is called <i>Cache "HIT ratio"</i> is a metric used in HTTP caching to tell how many times it didn’t serve a cached request. Caching is prevent if one or more of the following exists in the backend response sent back to Varnish: Authorization, Set-Cookie, Cache-Control that contains <i>max-age=0</i> or similar and Vary with "cookie". If a given page has NO possible changes whatsoever between a request with cookies or not, it is therefore safe to remove those headers.</dd>
<dt>remove non needed cookies from a request to a backend that doesn’t need them</dt>
<dd> Its important it is to configure Varnish to clean cookies it sends to our backend servers.  Otherwise we do not have cache at all. The cleaning must be done for each backend because, for example, WordPress cookies wouldn’t be the same as MediaWiki’s.  In order to not lose the subtleties, we published all Varnish VCLs into GitHub at <a rel="nofollow" class="external text" href="https://github.com/webplatform/varnish-configs">webplatform/varnish-configs</a>.</dd></dl>
<h2><span class="mw-headline" id="Reference">Reference</span></h2>
<ul><li> <a rel="nofollow" class="external free" href="https://www.mnot.net/cache_docs/">https://www.mnot.net/cache_docs/</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.fastly.com/blog/best-practices-for-using-the-vary-header/">http://www.fastly.com/blog/best-practices-for-using-the-vary-header/</a></li>
<li> <a rel="nofollow" class="external free" href="https://www.varnish-cache.org/docs/trunk/users-guide/increasing-your-hitrate.html#the-role-of-http-headers">https://www.varnish-cache.org/docs/trunk/users-guide/increasing-your-hitrate.html#the-role-of-http-headers</a></li>
<li> <a rel="nofollow" class="external free" href="https://www.varnish-cache.org/trac/wiki/VCLExampleLongerCaching">https://www.varnish-cache.org/trac/wiki/VCLExampleLongerCaching</a></li>
<li> <a rel="nofollow" class="external free" href="http://stackoverflow.com/questions/10284813/howto-control-varnish-and-a-browser-using-cache-control-max-age-header-in-a-rai">http://stackoverflow.com/questions/10284813/howto-control-varnish-and-a-browser-using-cache-control-max-age-header-in-a-rai</a></li></ul>
<h3><span class="mw-headline" id="See_also_in_our_pages">See also in our pages</span></h3>
<ul><li> <a href="/wiki/WPD:Infrastructure/analysis/2015-How_MediaWiki_backend_sees_requests_with_or_without_Fastly_in_front" title="WPD:Infrastructure/analysis/2015-How MediaWiki backend sees requests with or without Fastly in front">analysis; 2015, How MediaWiki backend sees requests with and without <i>Fastly</i> in front</a></li></ul>
<h3><span class="mw-headline" id="Reference_to_review">Reference to review</span></h3>
<ul><li> <a rel="nofollow" class="external free" href="https://www.mobify.com/blog/beginners-guide-to-http-cache-headers/">https://www.mobify.com/blog/beginners-guide-to-http-cache-headers/</a></li></ul>
<h4><span class="mw-headline" id="MediaWiki">MediaWiki</span></h4>
<ul><li> <a class="external text" href="http://www.mediawiki.org/wiki/Manual:Varnish_caching">MediaWiki Varnish Caching</a></li>
<li> <a rel="nofollow" class="external text" href="http://labs.creativecommons.org/2011/03/18/caching-mediawiki-with-varnish/">Caching mediawiki with varnish</a></li>
<li> <a rel="nofollow" class="external text" href="https://www.varnish-cache.org/lists/pipermail/varnish-misc/2012-January/021574.html">Default VCL for MediaWiki</a></li></ul>
<h4><span class="mw-headline" id="Varnish_in_general">Varnish in general</span></h4>
<ul><li> <a rel="nofollow" class="external text" href="http://kly.no/varnish/regex.txt">Regular expression Cheat sheet</a></li>
<li> <a rel="nofollow" class="external text" href="https://www.varnish-cache.org/docs/2.1/genindex.html">Varnish documentation</a>
<ul><li> <a rel="nofollow" class="external text" href="https://www.varnish-cache.org/docs/2.1/tutorial/vcl.html">Varnish configuration language</a></li>
<li> <a rel="nofollow" class="external text" href="https://www.varnish-cache.org/docs/2.1/tutorial/cookies.html">Varnish tutorial cookies</a></li></ul></li>
<li> <a rel="nofollow" class="external text" href="https://www.varnish-software.com/static/book/Tuning.html?highlight=timeout">Varnish book about tuning</a></li></ul>
<h4><span class="mw-headline" id="ESI">ESI</span></h4>
<ul><li> <a rel="nofollow" class="external text" href="https://www.varnish-cache.org/trac/wiki/ESIfeatures">Varnish ESI features</a></li>
<li> <a rel="nofollow" class="external text" href="https://www.varnish-cache.org/docs/2.1/tutorial/esi.html">Varnish 2.1 ESI doc</a></li></ul>
<h4><span class="mw-headline" id="Misc.">Misc.</span></h4>
<ul><li> <a rel="nofollow" class="external text" href="http://kly.no/posts/2010_01_08__Hitpass_objects_and_Varnish__.rst">Varnish caching, definition of HIT, PASS and other caching lingo</a></li>
<li> <a rel="nofollow" class="external text" href="http://docs.fastly.com/guides/21847086">Fastly: Caching tutorials</a>
<ul><li> <a rel="nofollow" class="external text" href="http://docs.fastly.com/guides/21835572/21744408">Fastly: Removing headers from backend response</a></li>
<li> <a rel="nofollow" class="external text" href="http://docs.fastly.com/guides/21835572/23999817">Fastly: Adding and modifying headers</a></li>
<li> <a rel="nofollow" class="external text" href="http://docs.fastly.com/guides/21847086/22257776">How to serve stale content in case of origin becoming unavailable</a></li></ul></li>
<li> <a rel="nofollow" class="external text" href="http://docs.fastly.com/guides/21847086/26628787">Fastly tutorial: Cache control</a></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:58635-0!*!0!!*!*!*!esi=1 and timestamp 20150731185927 and revision id 101379
 -->
