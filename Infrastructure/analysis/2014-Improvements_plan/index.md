= Sept.-Dec. 2014 Improvement plans =

Infrastructure improvement plans, what’s planned and the big picture.


== Goal ==

The goal of this sprint is to have a separation between ''development'' (e.g. a local Vagrant VM, or code checkout), ''staging'' (i.e. a full deployment) and ''production'' (i.e. the live site) so we can test our changes in an environment without impacting the live "production" site.


=== Expected outcome ===

* Before deploying to production, every components MUST be running fine on ''webplatformSTAGING.org''
* Deploy automatically on git push (GitHub hooks) on master branch and/or a release tag (TBD)
* Self-contained environment at every level; e.g, ''staging'' MUST NOT use any resources from ''production''
* Full clone of the site for each components; e.g. '''blog.webplatform.org''' (production), '''blog.webplatformSTAGING.org''' (staging).
* Harmonize configuration settings across the softwares, automate them based on known data facts, do not rely on internal DNS
* Remove anything that isn’t used anymore, and simplify system as much as possible

=== Tasks summary ===

* Publish to the public all our deployment scripts, with correct author attribution, without passwords nor private data
* Set in place a system that will update code automatically when a contributor push on watched Git repos
* Salt reactor pull, and run scripts (bower, grunt, composer, etc) and makes a zip archive, deploy archive
* Salt reactor launch rsync when changes are detected
* Ensure all components works on BOTH '''webplatform.org''' AND '''webplatformSTAGING.org''' top level domains, ''without configuration switches''
* Ensure all VM are on Ubuntu 14.04 LTS
* Make sure every components are working as it should


== Tasks ==

=== Done ===

What has been done and is deployable on staging at this moment.

* Decommissioned global system features (will improve system and refactor after the rest is ready):
** Disabled centralized log
** Disabled Ganglia graphs

* Decommissioned VM types:
** storage (we rely on DreamObjects instead of our own)
** monitor (we will refactor the monitoring and log management in the next steps)

* Homepage:
** Can be configured (switch <code>@site.tld</code> in ''docpad.js'') to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding.
** Supports SSL
** Fastly forces SSL
** Upgraded version (DocPad)

* MediaWiki
** Enabled back planned for deprecation extension [http://www.mediawiki.org/wiki/Extension:SocialProfile SocialProfile Extension], see [https://github.com/webplatform/mediawiki/issues/19 issue #19]. Disabled explicitly uploads, serve an empty 1x1 gif.
** Ability to disable completely Piwik tracking
** Upgraded version
** Supports SSL
** Fastly forces SSL
** Improved deployment using git
** Deployment to exclusively use git submodules (until composer is supported)
** Can be configured (switch <code>siteTopLevelDomain</code>, in ''LocalSettings.php'') to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding
** Improved configuration system to use Salt stack provided values (no manual edition anymore)
** Made an extension that contains all copy-pasted micro-extensions, and theme
** Migrated all images and fonts to use www.webplatform.org instead (eventually CSS/JS will also be removed)
** Have Salt Stack generate config automatically: database, sessions

* MediaWiki Compatibility tables extension
** When access <code>Special:Compatables?topic=css...&action=purge</code> it also purges keystore copy
** Big memory usage was caused by ''data.json'' being called more than once at EVERY requests (MW arch problem, error somewhere?) — fixed by saving generated HTML AND ''data.json'' in configurable Keystore

* Blog
** Upgraded version (WordPress)
** Improved deployment using git
** Reworked skin (see [https://github.com/webplatform/webplatform-wordpress-theme WebPlatform WordPress theme repo]) to manage theme and plugin configuration through Git. See article: [http://blog.g-design.net/post/60019471157/managing-and-deploying-wordpress-with-git Managing and deploying WordPress with Git].

* Piwik
** Upgraded version
** Improved deployment using git
** Reworked skin, forked project and changed theme to match our site theme (there are no real template system nor theme support)

* Improve error pages
** When backend server crash, before Fastly marks the backend "unhealthy", send link to status page (see [http://www.webplatformstaging.org/errors/503.html static version])

* '''Upgrade to latest Ubuntu 14.04 LTS version''', and their configured services for each VM types;
** notes
** bots
** db
** app
** blog
** project
** memcache
** backup
** elasticsearch
** piwik

* New VM types
** postgres
** redis

* Ways to define role of a VM type
** Use of Salt mine to store static data such as internal IP addresse for automatic configuration generation
** Parse the VM name and make it as a role (e.g. ''redis-jobs1'', has roles: [redis, jobs]) so we can target secondary service allocation based on the role and not exclusively on the hostname


=== To do ===

What’s missing to complete this sprint.

* '''Upgrade to latest Ubuntu 14.04 LTS version''', and their configured services:
** account
** webat
** mail

* Blog:
** Skin can be configured (switch <code>TBD</code>) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding
** Support SSL (almost done)
** Fastly to force SSL
** Have Salt Stack generate config automatically: database, sessions

* NGINX:
** Make sure that every vhosts has appropriate 5xx error page messages

* Apache:
** Make sure that every vhosts has appropriate 5xx error page messages

* BugGenie:
** Skin can be configured (switch <code>TBD</code>) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding
** Support SSL (almost done)
** Fastly to force SSL
** Have Salt Stack generate config automatically: database, sessions

* Piwik
** Have Salt Stack generate config automatically: database, sessions
** Support SSL
** Figure out whether to use NGINX or Fastly

* Database cluster, VM types [db, postgres]: 
** Migrate all databases into new cluster using MariaDB 10.1
** Setup replication
** Ensure every components gets the list of IP addresses of the database servers through Salt stack

* On postgresql VM type:
** Make backup works like MySQL

* On every VM types; Make X service to rely on local VM type instance instead of an hardcoded setting pointing to production:
** emails
** Accounts system

* Create new VM types:
** Discourse forum using Docker, but to use postgres server VM
** postgresql


* Figure out which '''Keystore mechanism''' (Redis, or Memcache, or Redis + Memcache) to use:
** Must support SSL between web app and clients (and authentication?)
** Each web app runtime origin VM types (e.g. app, project, etc) should have ONE '''Keystore broker client''' (e.g. Nutcracker, MCRouter)
** Be consistent on the keystore system to use per use-case
** Most popular use-case  (i.e. will be used most) will use default port number
** Use-case 1: Session storage (most popular)
** Use-case 3: Message queue for logs to pass through LogStash (second popular)
** Use-case 2: MediaWiki Jobs
** Use-case 4: Keystore (e.g. various components in MediaWiki, etc)

* On every PHP VM types; [app, project, blog, notes, piwik, webat], ensure:
** MCRouter forwards to Memcache [roles:session, roles:keystore] clusters
** Monit watches local MCRouter
** MediaWiki config points to local MCRouter ports
** MediaWiki config points to role:jobs redis cluster
** Ensure Redis is used everywhere for session handling through local nutcracker Redis port
** Set <code>session.save_handler</code> correctly and consistently

* Automatic deployment
** Create typical deployment package (i.e. commands to run to get all dependencies, make a zip file, unpack on every servers)

* Improve centralized logging
** LogStash to process logs
** Log rotation, and create archive files every year to prevent disk filling

* Improve system stats
** Graphana to get system metrics
** Attempt to merge data from ganglia into Graphana so we do not lose previous data

* Set in place Monit to ensure+enforce critical services are up
** ensure MySQL servers are up on db VM types
** ensure MySQL server are accessible on app*, project*, blog*, piwik* nodes
** ensure Apache HTTP server up on app*, project*, blog*, notes*, piwik*, webat* nodes
** ensure local redis, memcache ports is up and nutcracker is running on app*, project*, blog*, piwik* nodes 
** ensure NGINX HTTP server is up on accounts* nodes
** ensure ElasticSearch is up on elastic* nodes
** ensure memcached is up on memcache* nodes
** ensure redis is up on redis* nodes



== Next ==

What should be done once the previous requisites are met.

* WebPlatform Accounts
** Create shared component (i.e. using composer) 
** Factor out specific to MediaWiki as an extension, use new shared PHP component 

* MediaWiki:
** document how to upgrade version
** delete unused css/js/misc assets moved to www.webplatform.org

* On [db, postgres] VM types:
** Send backups to DreamObjects after a month, purge local copy

* Setup alerts (aremysitesup is insufficient)
* Rework Varnish files: compression is not working from Fastly, fix ESI
* Make Fastly VCL to point to salt master with basic "server maintenance in progress" page if origin is unresponsive
* '''Upgrade to latest Ubuntu 14.04 LTS version''', and their configured services for each VM types;
** source

* Improve Fastly service configs:
** ''www.webplatform.org'' fastly service to be completely cookie less, hold DreamObject images (instead of static.webplatform.org)
** Deprecate ''static.webplatform.org'' fastly service
** Each services to use consistent ''static error pages''
** Each services to use to a minimum Fastly web UI and instead use source-controlled VCL files
** See if Fastly VCL supports to include secondary VCL to hold private data

* Improve ''static error pages'' when communication problem (other "guru meditation" left)
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