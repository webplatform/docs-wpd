= Sept.-Dec. 2014 Improvement plans =

Infrastructure improvement plans, what’s planned and what’s done.

== Done ==

* In deployment process (will improve system and refactor after the rest is ready)
** Disabled centralized log
** Disabled Ganglia graphs
* MediaWiki
** Upgraded to a more recent version
** Improved deployment to exclusively use git submodules (until composer is supported)
** Improved configuration system to use Salt stack provided values (no manual edition anymore)
** Made an extension that contains all copy-pasted micro-extensions, and theme
* Made an extension for upcoming single sign on (Non MediaWiki specific code will be factored out as dependency. Allowing to re-use in other PHP components)
** Migrated all images and fonts to use www.webplatform.org instead (eventually CSS/JS will also be removed)
** Supports SSL
* MediaWiki Compatibility tables extension
** Last sprint version is deployed
** When access <code>Special:Compatables?topic=css...&action=purge</code> it also purges memcache/redis
** Big memory usage was caused by data.json being called more than once at EVERY requests (MW arch problem, error somewhere?) — fixed by saving generated HTML AND data.json in Memcached


== To do ==

* Mail relay
** To support webplatformstaging, only works on one domain
** Ensure every components use local mail server relative to where they are (its currently hardcoded)
* Database cluster
** Migrate all databases into new cluster using MariaDB 10.1
** Setup replication
** Ensure every components gets the list of IP addresses of the database servers through Salt stack
* Automatic deployment
** Create typical deployment package (i.e. commands to run to get all dependencies, make a zip file, unpack on every servers)
* SSL
** blog
** project

== Next ==

* Setup alerts (aremysitesup is insufficient)
* Improve centralized logging
** LogStash to process logs
** Log rotation, and create archive files every year to prevent disk filling
* Improve system stats
** Graphana to get system metrics
** Attempt to merge data from ganglia into Graphana so we do not lose previous data
* Set in place Monit to ensure+enforce critical services are up
** ensure MySQL servers are up on db* nodes
** ensure MySQL server are accessible on app*, project*, blog*, piwik* nodes
** ensure Apache HTTP server up on app*, project*, blog*, notes*, piwik*, webat* nodes
** ensure local redis, memcache ports is up and nutcracker is running on app*, project*, blog*, piwik* nodes 
** ensure NGINX HTTP server is up on accounts* nodes
** ensure ElasticSearch is up on elastic* nodes
** ensure memcached is up on memcache* nodes
** ensure redis is up on redis* nodes
* Error pages when communication problem (other "guru meditation" left)
* Rework Varnish files: compression is not working from Fastly, fix ESI