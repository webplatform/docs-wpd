= Sept.-Dec. 2014 Improvement plans =

Infrastructure improvements that we can make to improve the site reliability

== Improving state, and done ==

* Installed MediaWiki latest version
* Successfully separated the components to put git clones together
* Isolated all minor customizations (and skin) into one extension
* Created a separate database server, only MW is using it (the heaviest)
* Compatibility tables are deployed
  * When access Special:Compatables?topic=css...&action=purge it also
purges memcache/redis
  * Big memory usage was caused by data.json being called more than once
at EVERY requests (MW arch problem, error somewhere?) — fixed by caching
it in memcached/redis



== Improving state, left to do ==

* Finish up how to make better database cluster
* Migrate all databases to new cluster


== Next ==

* Hide Compatibility table when in form (show message or not?)
* Have SSL working on wiki, blog, www. Partially done.
* Figure out which subdomains we want EV
* Set better alerts
* Set in place logging management
* Set in place Monit to ensure+enforce critical services are up
* Error pages when communication problem (other "guru meditation" left)
* Rework Varnish files: compression is not working from fastly, fix ESI
* Set in place Redis instead of MediaWiki
  * Find how to tweak memory usage to optimize resources 
  * Will also be used by: Blog, MediaWiki, Logging management, etc.
  * Configure TwMemProxy (Nutcracker [3])
* Set in place ElasticSearch, many benefits
  * besides notes, will be used by monitoring
  * found a MW extension to query it
  * Compatibility data; Find way to import source file and expose it as an API


== Also ==

* Talk with NewRelic and SOASTA —met at velocity— if they can sponsor us
free server usage monitoring
* Talked w/ NGINX a senior contributor:
** Site load w/ MediaWiki; set it in between Varnish and Apache helps
with load
** Will start thread to get integration patterns
* MediaWiki has also some improvements:
** The slowest component being the "Parser", they are now recommending
** Templates managed by Lua (a language)
** Use new Template parser web service [http://www.mediawiki.org/wiki/Lua_scripting Lua, Scibunto], Parsoid. [http://blog.wikimedia.org/2013/03/04/parsoid-how-wikipedia-catches-up-with-the-web See this post]