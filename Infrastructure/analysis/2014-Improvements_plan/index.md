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
* Improve error pages
** When backend server crash, before Fastly marks the backend "unhealthy", send link to status page (see [http://www.webplatformstaging.org/errors/503.html static version])
** Make Fastly redirect to a static page on salt-master when no IP responds, message: "server maintenance in progress"


== To do ==

Objective;

* Deploy automatically on git push (GitHub hooks) on master branch
* System listens to given git repos, send event to salt reactor
* Salt reactor pull, and run scripts (bower, grunt, composer, etc) and makes a zip archive
* Salt reactor launch rsync when changes are detected
* Ensure all components works on '''webplatformSTAGING.org''' AND '''webplatform.org''' top level domains, without configuration switch
* Ensure all VM are on Ubuntu 14.04 LTS


=== Tasks details ===
* Nutcracker Redis port forward on different ports, depending of its purpose
** Session storage, use default port; TCP 6379, forward to redis-sessions*
** Job queue, use default port +1; TCP 6380, forward to redis-jobs*
* For every PHP nodes (app*, project*, blog*, notes*, piwik*, webat*)
** Ensure Nutcracker forwards both Redis and Memcached ports to the memcache*, redis* nodes
** Ensure Redis is used everywhere for session handling through local nutcracker Redis port
** Redis, test <code>session.save_handler</code>
<syntaxHighlight>
      session.save_handler = redis
      session.save_path = "tcp://localhost:6379"
</syntaxHighlight>
** Ensure Memcached is used everywhere for page cache
** Ensure redis-jobs* is used for jobs
* MediaWiki:
** Hardcoded method in template to redirect to preferred top level domain name. See <code>WebPlatformTemplate::getTld()</code>
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
* Make fastly VCL to point to salt master with basic "server mainteannce in progress" page if origin is unresponsive

== Next ==

* Rebuild VMs to new Ubuntu version (no config refactor yet):
** account
** webat
** mail
** source
* Improve error pages
** Create human comprehensible explanation messages for each of them
** See [http://docs.fastly.com/guides/backend-servers/503-error-explanations Fastly specific errors documentation]
** See sample [http://www.webplatformstaging.org/errors/503.html 503 error page static version]
** Commited into GitHub www.webplatform.org project in [https://github.com/webplatform/www.webplatform.org/tree/master/src/documents/errors src/documents/errors]
** Find how to configure Fastly for each of them (i.e. When Fastly is about to serve white page error, replace with ours)
** Make static html page for each of them, commit into www.webplatform.org github repo
** 503 Connection Refused,
** 503 Network Unreachable; In case of a network outage between Fastly and DreamHost/iWeb networks
** 503 Backend.max_conn Reached; When ALL backends cannot meet the demand
** 503 Backend Is Unhealthy; When the only backend server isn’t "healthy"
** 503 No Healthy Backends; When no backend server are’t "healthy"
** 503 All Backends Failed or Unhealthy; When ALL backends aren’t "healthy"
** 503 Backend Read Error; When backend server takes too long to respond
** 503 Backend Write Error; 
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