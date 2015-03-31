= Sept.-Dec. 2014 Improvement plans =

This sprint is about refactoring the server infrastructure to ease the maintenance work and automate what’s possible.

For the project summary, refer to [[WPD:Infrastructure/reports/201410|the 201410 report]]

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

* Wiki web app:
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

* Wiki Compatibility tables extension:
** When access <code>Special:Compatables?topic=css...&action=purge</code> it also purges keystore copy
** Big memory usage was caused by ''data.json'' being called more than once at EVERY requests (MW arch problem, error somewhere?) — fixed by saving generated HTML AND ''data.json'' in configurable Keystore

* Blog web app:
** Upgraded version (WordPress)
** Improved deployment using git
** Reworked skin (see [https://github.com/webplatform/webplatform-wordpress-theme WebPlatform WordPress theme repo]) to manage theme and plugin configuration through Git. See article: [http://blog.g-design.net/post/60019471157/managing-and-deploying-wordpress-with-git Managing and deploying WordPress with Git].
** Skin can be configured (switch <code>siteTopLevelDomain</code>) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding
** Have Salt Stack generate config automatically: database, sessions

* Stats web app:
** Upgraded version (Piwik)
** Improved deployment using git
** Reworked skin, forked project and changed theme to match our site theme (there are no real template system nor theme support)
** Support SSL
** Fastly to force SSL
** Config to use database table for sessions (the only one supported off-the-shelf by Piwik so far)
** Config points automatically to database and Memcached/Redis IPs

* Project web app:
** Upgraded BugGenie version (BugGenie branch-32)
** Skin can be configured (switch <code>siteTopLevelDomain</code>) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding
** Support SSL
** Fastly to force SSL
** Config points automatically to database and Memcached IPs

* Improve error pages:
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
** source
** account
** mail


* Ways to define role of a VM type
** Use of Salt mine to store static data such as internal IP addresse for automatic configuration generation
** Parse the VM name and make it as a role (e.g. ''memcache-jobs1'', has roles: [memcache, jobs]) so we can target secondary service allocation based on the role and not exclusively on the hostname

* Change Salt stack behavior:
** Create a grain to learn in which deployment level (e.g. "staging") we are in
** Create a grain to learn what are the roles the VM has (e.g. [salt])

* Service resiliency subsystem "Monit":
** '''Purpose''': Ensure critical services are up
** Ensure common service is running: salt-minion, ssh

* Key store clusters (Memcached, Redis):
** '''Purpose:''' Each cluster fills a role, depending of the life expectancy of the stored data (e.g. sessions should not be cleared, page cache might)
** Ensure only local network can connect
** Each web app runtime origin VM types should have a '''Keystore broker client''' (e.g. Nutcracker)

* Configure '''Key store broker client''' (Nutcracker):
** '''Purpose:''' Have everything locally is much quicker, this component keeps a local cache, see  [https://code.facebook.com/posts/296442737213493/introducing-mcrouter-a-memcached-protocol-router-for-scaling-memcached-deployments/ MCRouter introduction]
** Separate port number per use-case, most popular (i.e. will be used most) will use default port number
** Use-case 1: Session storage (most popular)
** Use-case 2: Keystore (e.g. various components in MediaWiki, etc)
** Set <code>session.save_handler</code> correctly and consistently

* Service resiliency subsystem "Monit":
** '''Purpose''': Ensure critical services are up
** ensure MySQL servers are up on db VM types
** ensure Apache HTTP server up on app*, project*, blog*, notes*, piwik*, webat* VM types
** ensure Nutcracker is running on app*, project*, blog*, piwik*  VM types
** ensure NGINX HTTP server is up on accounts*  VM types
** ensure ElasticSearch is up on elastic*  VM types
** ensure Memcached is up on memcache*  VM types

* NGINX:
** Make sure that every vhosts has error page; see <code>/srv/webplatform/errors</code>

** ''Setup logrotate for non typical logs'': \[mw-logs, fastly, remote logs\]

* '''Upgrade to latest Ubuntu 14.04 LTS version''', and their configured services:

* Blog web app:
** Support SSL
** Fastly to force SSL
** Config W3TotalCache to use local Nutcracker port
** Config points automatically to database IP


* Database cluster, VM types [db]: 
** Migrate all databases into new cluster using MariaDB 10.1
** Ensure every components gets the list of IP addresses of the database servers through Salt stack
** Setup replication
** Automatic backups, sends to DreamObjects bucket

* Apache:
** Make sure that every vhosts has error page; see <code>/srv/webplatform/errors</code>

* On elastic VM type:
** Automatic backups, sends to DreamObjects bucket








<!--  -----------------------------------------------------------  -->


=== To do ===

What’s missing to complete this sprint to have something better than what we have in production, but with latest version.


<!--  -----------------------------------------------------------  -->


== Next ==

What should be done once the previous requisites are met.


* '''Misc. issues''':
** ''Blog'' see [http://project.webplatform.org/infrastructure/issues/89 WordPress login problem w/ Fastly, issue 89], ensure it works w/ new theme structure. currently broken.

* Automatic deployment:
** '''Purpose''': Ease to have contributors to see their work online
** Create typical deployment package (i.e. commands to run to get all dependencies, make a zip file, unpack on every servers)
** Homepage, see: [http://project.webplatform.org/infrastructure/issues/99 Story 99; Automating deployment of Home page]
** Project, see: [http://project.webplatform.org/infrastructure/issues/81 Story 81; Automating deployment of Project Management tool] (postpone?)
** Wiki, see: [http://project.webplatform.org/infrastructure/issues/79 Story 79; Automating deployment of Wiki]
** Blog, see: [http://project.webplatform.org/infrastructure/issues/80 Story 80; Automating deployment of Blog]

* Un hardcode deployment level (e.g. "staging"):
** '''Purpose:''' Make X service to rely on local VM type instance instead of an hardcoded setting pointing to production:
** Use new ''Salt grain "salt-call grains.get level"'' instead.
** How to find <code>cd /srv/salt; grep -rli 'staging' .</code>, or with a ''#TODO'' note.
** emails
** Accounts system

* Service resiliency subsystem "Monit":
** '''Purpose''': Ensure critical services are up
** Notes to [http://mmonit.com/wiki/MMonit/Setup make monit respawn], [http://mmonit.com/wiki/Monit/FAQ Monit FAQ], [http://mmonit.com/wiki/Monit/ConfigurationExamples Configuration examples]
** ensure MySQL server are accessible on app*, project*, blog*, piwik* VM types
** ensure Apache HTTP server up on app*, project*, blog*, notes*, piwik*, webat* VM types
** ensure [ssh, salt-minion] are always running on every nodes
** ensure alert email config and destination is configured depending of staging/production
** ensure disk usage alerts are in place
** ensure resolv.conf works

* Improve system stats:
** '''Purpose''': Get system health data as graph, over time 
** Set in place statsd, fluentd, monit and other system health graph tools
** Graphana to get system metrics
** Attempt to merge data from ganglia into Graphana so we do not lose previous data

* Centralized logging:
** '''Purpose''': Aggregate and harmonize all log messages to see what happened (or happens)
** LogStash to process logs
** Log rotation, and create archive files every year to prevent disk filling
* Docker VM type:
** To host Discourse, and other things TBD such as preparing web app archives

* Discourse web app:
** Support SSL
** Config points to local MCRouter port
** Config points automatically to database IP

* NGINX:
** Move all web apps that can run properly under HHVM/php-fpm, NGINX as the frontend
** Serve as frontend to counter-balance apache2’s mod-prefork and older PHP code memory issues

* Accounts web app:
** Create shared component (i.e. using composer) 
** Factor out specific to MediaWiki as an extension, use new shared PHP component 

* Wiki web app:
** document how to upgrade version
** delete unused css/js/misc assets moved to www.webplatform.org

* On [db, postgres] VM types:
** Send backups to DreamObjects after a month, purge local copy

* Setup alerts (aremysitesup is insufficient)

* Rework Varnish files: compression is not working from Fastly, fix ESI

* Make Fastly VCL to point to salt master with basic "server maintenance in progress" page if origin is unresponsive

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