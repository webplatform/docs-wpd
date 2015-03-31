= March 2015 Infrastructure change log since 2013 =

List of high level Infrastructure changes we’ve worked on in the last two years.

Should cover;
* Which individual software we run, pieces involved, what needs each piece fulfills
* Software we got rid of (e.g. web based IRC client, GlusterFS, etc)
* New components
* We weren't assured of long term free hosting form HP, thankfully DreamHost took charge of us
* Automation improvements
* Overview of lessons learned, and wins

On a related note, there are also notes in [[WPD:Infrastructure/reports/201410|the 201410 report published last year]] and in the [[WPD:Infrastructure/analysis/2014-Improvements_plan|'''2014 Improvement plan''' page]].

== Software we currently use ==

=== Web applications we host ===

{| class="wikitable sortable" |
! Resource
! Software
! Deployment repository
! Location
|- 
! Home page
| [https://docpad.org/ DocPad]
| [https://github.com/webplatform/www.webplatform.org repository]
| [http://webplatform.org/ webplatform.org/]
|-
! wiki ([[Special:Version|version]])
| [https://www.mediawiki.org/wiki/MediaWiki MediaWiki] using Wikimedia Foundation ("wmf/1.24wmfX") continuous release branches
| [https://github.com/webplatform/mediawiki repository]
| [https://docs.webplatform.org/wiki/ docs.webplatform.org/wiki/]
|-
! IRC logger
| [http://classam.github.io/pierc/ Lumberjack (now called Pierc)]
| TODO
| [https://www.webplatform.org/talk/chatlogs/ www.webplatform.org/talk/chatlogs/]
|-
! Analytics
| [http://piwik.org/ Piwik]
| TODO
| [https://stats.webplatform.org/ stats.webplatform.org/]
|-
! Blog
| [http://wordpress.org/ WordPress]
| [https://github.com/webplatform/blog-service repository]
| [https://blog.webplatform.org/ blog.webplatform.org/]
|-
! Code sandbox
| [http://dabblet.com/ Dabblet]
| [https://github.com/webplatform/dabblet repository]
| [http://code.webplatform.org/ code.webplatform.org/]
|-
! Project management
| [http://www.thebuggenie.com/ The Bug Genie]
| [https://github.com/webplatform/thebuggenie repository]
| [https://project.webplatform.org/ project.webplatform.org/]
|-
! Accounts
| [https://wiki.mozilla.org/Identity/Firefox_Accounts Firefox Accounts]
| see [[WPD:Projects/SSO|SSO Project page]]
| [https://accounts.webplatform.org/ accounts.webplatform.org/]
|-
! Hypothes.is
| [https://www.hypothes.is/ Hypothes.is]
| TODO
| [https://notes.webplatform.org/ notes.webplatform.org/]
|-
! Discuss
| [http://www.discourse.org/ Discourse]
| TODO
| [https://discuss.webplatform.org/ discuss.webplatform.org/]
|}

=== Web application that we rely on ===

{| class="wikitable sortable" |
! Resource
! Software
! Location
! Usage
|- 
! Operations issue tracker
| GitHub "''webplatform/ops"'' project and [https://huboard.com/ Hubboard]
| [https://huboard.com/webplatform/ops/#/ ''KanBan'' dashboard], [https://webplatform.github.io/ops webplatform.github.io/ops]
| A Dashboard utility to visualize in columns what’s next, what´s in progress, and what’s done.
|- 
! WebPlatformDocs GitHub account
| GitHub 
| [https://gist.github.com/WebPlatformDocs gist.github.com/WebPlatformDocs], [https://github.com/WebPlatformDocs github.com/WebPlatformDocs]
| Store all ''code.webplatform.org'' gists in GitHub. This account was created before GitHub introduced "organizations".
|- 
! WebPlatform GitHub organization
| GitHub
| [https://github.com/WebPlatform github.com/WebPlatform]
| An organization in which we store all repositories
|}

=== Misc. ===

;Ubuntu: We were originally running on two different versions of Ubuntu 10.04 and 12.04. While both are "Long Term Support" we weren’t running on the same version for every servers, and also had no automatic install of security updates. Since mid-2014 all servers uses the same version — Ubuntu 14.04 LTS — and automatic security updates
;Memcached: A "key store" system that many web applications relies to keep the HTML that it generated, speeding up the page render. 
;Redis ''(new since 2014)'': Another "key store" system similar to Memcached, but in use for storing session data so we can balance web application backend load across multiple web servers. Benefit of Redis over Memcached is that we can easily make Redis calls through SSL/TLS and require clients to authenticates. Also, we can configure MediaWiki to store async jobs over to Redis instead of a MySQL table. MediaWiki operations team lead said that tables is fine for heavy load. Unless we get wikipedia.org type of load.
;ElasticSearch ''(new since 2014)'': A "REST" web application on which we can index documents, and use as a search engine. We store annotations in it, and so we could configure MediaWiki so we improve search capabilities.
;MariaDB ''(new since 2014)'': A drop-in replacement to MySQL, in use by most of the infrastructure. We could also configure it to use ''Galera'' so we could send writes to any node in the cluster. Might be a next step.
;Monit ''(new since 2014)'': A system that is made to help ensure vital services are up.
;NGINX ''(new since 2014)'': A Web Server and Proxy software. We will eventually use NGINX instead of apache in a near future
;Apache: The original web server software. Only MediaWiki has an hard requirement to it, until we change our configuration or that Semantic MediaWiki  (''"SMW"''') requirement changes. At this time, SMW requires PHP to be run through '''mpm-prefork''' which is, in contrast to multi-threaded servers, is asking to always keep up a set of processes to answer HTTP requests. It is said in SMW mailing list, this hard requirement might change soon.
;php-fpm ''(new since 2014)'': A PHP execution environment that NGINX connects to to server dynamic pages. Currently in use with Piwik, other PHP web applications (except MediaWiki) could be migrated to it soon enough. Unless we could run everything that runs in ''php5-fpm'' to HHVM (see below) instead.



=== Software we are currently evaluating to use ===

;[https://github.com/twitter/twemproxy Nutcracker]: A "key store" proxy system that we could install on each app server making a local copy and balancing the load accross both Redis and Memcached.
;[http://hhvm.com/ HHVM]: A complete rewrite of the PHP execution environment with known improvements compared to php-fpm. We might migrate all compatible PHP web applications to this runtime environment.
;[http://logstash.net/ LogStash]: A centralized log manager. It harmonizes, archives and process any log messages we send to it. Serves as an easy to use log search engine
; [http://phabricator.org/ Phabricator]: A web application made to help organize software projects. It features an IRC bot from which we could monitor more than one IRC chat room (our chat bot is not maintained and doesn’t scale well). Also, we could Phabricator as a place to: store sensitive documents, mirror GIT/SVN/Mercurial repositories we rely on, host temporary Git/Mercurial stashes so we don’t risk losing them around, code "pastebin" so we don’t need to rely on GitHub gists, etc. See [http://phabricator.org/applications/ Phabricator applications list for more details]
; [https://www.docker.com/ Docker]: A system that allows us to create "executable" packages called "containers" out of any software or web application. At a first look, it looks like a VM, but its a very thin one that only does one job and removes the need to upgrade operating system packages and allow to roll back from any previous builds that had been made
; [http://deis.io/ Deis]: An "orchestration" system that automates the cycle of building Docker containers. It automates handling of subsystems such as load balancing, remove the need to hardcode web application related deployment scripts, archiving, etc. With this, we could build on push anything that has a "''Dockerfile''" at the root of the project.  
;CoreOS: A thin Linux distribution that has Docker preinstalled and a few other orchestration utilities to provide auto-discoverability and automatic scaling.


=== Conventions in place ===

Idea is that any service use default configuration as if its local, use of equivalent service to delegate/proxy to specialized set of servers

;What’s common on any VMs: Refer to [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM|architecture documentation at  '''Base configuration of a VM''']] 
;email: Each server uses ''localhost'' as their email server gateway, but the local email server then uses a specialized VM only for sending emails
;memcached (still in evaluation): Each application server (i.e. a server that runs a web application backend technology such as ''PHP'' or ''Python'') acts as if ''Memcached'' is local, but in fact a service called ''Nutcracker'' (a.k.a. TwEmProxy) is configured to talk to more than one Memcached servers serving the purpose of keeping a local copy of the data.
;secrets, passwords ("accounts" pillars): Are stored in a separate set of (salt) pillars in ''/srv/private/pillar/accounts/production.sls'' and (will be) hosted in a private Git repository at W3C. In there, we keep all API secrets, tokens, and passwords we need. Every configuration and services pulls information from there. To adjust, edit and commit the file then run a "highstate".  (staging is at  '''/srv/private/pillar/accounts/staging.sls'')
;Deployment sensible variables... ("infra" pillars): Are stored in a centralized (salt) pillars in ''/srv/pillar/infra/production.sls''. In there, we list private IP addresses of database servers, ElasticSearch, etc. Every configuration file and states relies on it. To adjust, edit and commit the file, then run a "highstate". (staging is at  '''/srv/private/pillars/accounts/staging.sls'')
;ssh access: The only way to work on any is to pass through the salt master as a "jump box", see [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM#Accessing_a_VM_using_SSH|Accessing a VM using SSH]]
;which level a VM is in?:The "level" grain exists to tell which configuration file to use in both ''/srv/pillar/infra/$level.sls'' AND in ''/srv/private/pillars/accounts/$level.sls''. To get which level, you can ask from the terminal <code>salt \* grains.get level</code>. Refer to [[WPD:Infrastructure/architecture/Roles_and_environment_level|architecture documentation at '''Roles and Environment level''']]


=== Lessons learned ===

;Varnish: Refer to [[WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish#Caveats|'''Caveats''' in Things to consider when we expose service via Fastly and Varnish]]
;Use IP address instead of names, in web application configuration files: Name resolution can be costly. I learned that it speeds page render time when I explicitly set Database, Redis, Memcached, ElasticSearch IPs instead of names that we’d put in ''/etc/hosts''. Since we now manage every configuration file through salt since late 2014, we can now update easily this information automatically
;To support multiple runtime backends ...: Its much easier to configure a public Front-end server to use directly a private-access-only backend that handles when to serve static files it already hosts and which files should pass through FastCGI, etc. Front-end nodes wouldn’t need to duplicate that part, but be responsible to balance the load and take care of both static files and in-memory page cache. Much like Varnish does.

 

== Work done per year ==

=== 2013 ===

* ''Started working on WebPlatform on July 2013''
* Setup analytics solution w/ '''Piwik''', at '''stats.webplatform.org'''
* Only one set of Virtual Machines (VMs) exposing live site, no room to work on improvements without risks of affecting live site
* Deployment scripts were assuming exactly one deployment, making it hard to do gradual roll out
* In configuration files, every IP Addresses were scattered around and I had to search around to adjust changes so that the servers would get the information updated
* VMs were running with two different OS versions: Ubuntu 10.04 and 12.04, no automatic installation of security patches
* Setup of a private OpenStack at DreamHost ("DHO"; DreamHost OpenStack) cluster from a 4 blades server, server was lent by DreamHost
* Server migration from HP Cloud into DHO [[WPD:Infrastructure/analysis/2013-Migrating_to_a_new_cloud_provider|2013 Migrating to a new Cloud Provider]]
* Work on MySQL cluster so we could have off-site hot backup (i.e. database replication on a remote site, with logs transferred through SSL)
* Multiple outages due to a bug in MediaWiki+Semantic MediaWiki affecting the rest of the infrastructure
* Complete rework of MediaWiki installation. Originally it was a clone with bits and pieces pasted without source control to a scripted setup exclusively based on source controlled repositories
* Work with Doug to create a new Compatibility data JSON schema
* Sprint on extracting compatibility data from MDN into new Compatibility JSON schema
* Sprint on Compatibility tables extension
** see [[WPD:Projects/CompaTables/201403-sprint|201403 sprint notes]]
** serve a copy of the generated HTML
** flush the generated HTML copy when JSON source is updated
** Alternate views and new supported actions:
**# single table view: [https://docs.webplatform.org/wiki/Special:Compatables?feature=border-radius&format=table&topic=css <code>GET /wiki/Special:Compatables?feature=border-radius&format=table&topic=css</code>]
**#single table view, "naked" alternate [https://docs.webplatform.org/wiki/Special:Compatables?feature=border-radius&format=table&topic=css&foresi=1 <code>GET /wiki/Special:Compatables?feature=border-radius&format=table&topic=css&foresi=1</code>]
**#manual table flush [https://docs.webplatform.org/wiki/Special:Compatables?feature=border-radius&format=table&topic=css&action=purge <code>GET /wiki/Special:Compatables?feature=border-radius&format=table&topic=css&action=purge</code>]
** Work on Semantic MediaWiki template [https://docs.webplatform.org/wiki/Template:Compatibility <nowiki>Template:Compatibility</nowiki>] to allow embed in content pages
** Creation of a GitHub repository to host compatibility data [https://github.com/webplatform/compatibility-data|on GitHub ''webplatform/compatibility-data'']
**  Originally it was regenerating the HTML for EVERY page load based on a previous JSON source
* Removed requirement of shared storage across VMs to use external DreamObjects storage (Swift) at DreamHost 
* Set in place image storage pulling files directly from DreamObjects


=== 2014 ===

* Upgraded all VMs to use only Ubuntu 14.04
* Pages are now served under SSL
* Most of the work mentioned below until 2015 is also noted in [[WPD:Infrastructure/analysis/2014-Improvements_plan|2014 Improvements plan]]
* Refactor of the homepage
** Originally from a set of PHP files to DocPad and other ''NodeJS'' based scripts to make the homepage completely static 
** see [[WPD:Projects/Homepage|in Projects/Homepage page]]
* Setup of our own email exit relay so that every server uses it instead of a paid external provider
* Deployed notes.webplatform.org w/ Hypothes.is
* Worked on implementing "SSO" based on a shared session token key, a "profile" server would be used as a source of truth, client web app (i.e. MediaWiki) would either create a user based on the details, or start a session
* Upgraded MySQL server version, migrated to MariaDB (Open Source version fork from the original author of MySQL)
* Creation of an account management service
** Based on Mozilla Firefox Accounts ("FxA")
** Created our own fork, changed branding
** Implemented Proof of concept of SSO using FxA for MediaWiki
** see [[WPD:Projects/SSO|SSO Project page]]
* Rework of how we deploy which now reads from a specifically crafted git repository and pull any plugins/extensions and gets configuration automatically applied
** Piwik (stats.webplatform.org), 
** WordPress (blog.webplatform.org)
** MediaWiki (docs.webplatform.org)
** The IRC bot, 
** BugGenie (project.webplatform.org)
** Annotation service (notes.webplatform.org)
** Accounts service (accounts.webplatform.org), many repos refer to notes at [[WPD:Projects/SSO|SSO Project page]]
** Homepage (www.webplatform.org)
* Purchase of an EV SSL certificate with mention of "World Wide Web Consortium" to give a hint of the site maintainers
* Purchase of an alternate domain name to replicate in full (!!) the server setup allowing us to test in isolation every components of the site
* Reviewed every blog posts, and imported any images we were linking outside of our site 
* "Inventory" system that keeps in memory the internal IP addresses of each infrastructure services: MySQL, Redis, Memcache, etc.
* Generates automatically configuration file with credentials based on the servers that are up at that moment, IP address, Passwords, Private keys, etc
* Capability to update passwords/private keys across all web applications from one "private" configuration file
* Setup of a "private" configuration system stored in a git repo
* We will eventually publish all our deployment scripts to the public, except the "private" data files


=== 2015 ===

* Renamed '''deployment.webplatform.org''' into '''salt.webplatform.org'''
** Old '''deployment''' —in DHO cluster— was left to run everything in production, as long as it wasn’t ready to be moved to the new environment in DreamCompute
** Created '''salt.webplatform.org''' —in DreamCompute cluster— so that we could create a complete deployment of every compoenents without affecting production
** Used both environments simultaneously and could do gradual roll out of every components. Once a roll out was made, I stopped the old version in DHO cluster.
* Set in place conventions to remove need to change configurations across environments, see [[#Conventions in place]]
* Work done on "hardening" security on servers
** Set in place automatic installation of security updates
** The main deployment server ("salt.webplatform.org", a.k.a salt) is the only IP address we can connect through SSH, only way to access another server using salt as a proxy. Benefit is that to remove access to a user, we can remove his access on salt, everything else becomes inaccessible
* '''March 2015'''; Finished up work planned in [[WPD:Infrastructure/reports/201410#Objectives|'''October 2014 sprint report''', according to the ''Objectives'']] ''and'' [[WPD:Infrastructure/analysis/2014-Improvements_plan|2014 '''Improvements plan''']] we set. Except for "automated deployment at Git push", something that’ll be done in a future sprint.
* Created bootstrap scripts so we can rebuild "from scratch" —at ANY time— a new salt master (what’s taking care of orchestrating deployment).
* Improved infrastructure maintenance documentation
** [[WPD:Infrastructure/architecture|Architecture design]]
*** [[WPD:Infrastructure/architecture/VM_roles|What roles each server fulfills and how to leverage it]]
*** [[WPD:Infrastructure/architecture/The_salt_master|How the '''Salt Master''' is designed]]
** [[WPD:Infrastructure/procedures/Deploying_code_changes|How we deploy code]]
* [[WPD:Infrastructure/procedures/Replacing_a_VM|How to replace any VM]] (without downtime)
* How caching is configured
** [[WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration|How to maintain Varnish/Fastly caching configuration]], 
** Documented what should be taken into account when working on the configuration in [[WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish|'''Things to consider when we work on Varnish configuration''']]
* [[WPD:Infrastructure/procedures/Managing_MySQL_replication|How to manage MySQL/MariaDB replication]]
* [[WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it|How to change database configuration and ensure every affected web application gets the new passswords]]
* [[WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster|How to maintain our new ElasticSearch cluster]], including notes on how automatic backups are made
* [[WPD:Infrastructure/procedures/Maintaining_email_services|How to '''Maintain email services''']]

== Soon? ==

* Improve stats:
** '''Purpose''': Get system health data as graph, over time 
** Set in place statsd, fluentd, monit and other system health graph tools
** Get system metrics
** Candidates
*** [http://grafana.org Graphana]?
*** [http://hekad.readthedocs.org Heka] that gets updated by Monit?
*** [http://sensuapp.org Sensu]?
** Get page load stats (i.e. what SOASTA does, but use open-source version; [http://www.lognormal.com/boomerang/doc/ Boomerang]), see {{OperationsTask|143}}
** Attempt to merge data from ganglia into Graphana so we do not lose previous data
** Ability to snapshot a server state for future investigation? Ref; http://www.sysdig.org/
** More food for thoughts ... [http://metrics20.org/ Metrics 2.0]

* Centralized logging:
** '''Purpose''': Aggregate and harmonize all log messages to see what happened (or happens)
** LogStash to process logs (and emails? see {{OperationsTask|127}})
** Log rotation, and create archive files every year to prevent disk filling
** Network traffic review tool [http://www.haka-security.org/hakabana.html HaKabana]; "Visualize Haka traffic in real-time using Kibana and Elasticsearch.", see {{OperationsTask|142}}


* Accounts web app:
** PHP relying client; Create shared component compatible with Composer
** Factor out specific to MediaWiki as an extension, use new shared PHP component

* Automatic deployment:
** '''Purpose''': Ease to have contributors to see their work online
** Create typical deployment package (i.e. commands to run to get all dependencies, make a zip file, unpack on every servers)
** Homepage, see: [http://project.webplatform.org/infrastructure/issues/99 Story 99; Automating deployment of Home page]
** Project, see: [http://project.webplatform.org/infrastructure/issues/81 Story 81; Automating deployment of Project Management tool] (postpone?)
** Wiki, see: [http://project.webplatform.org/infrastructure/issues/79 Story 79; Automating deployment of Wiki]
** Blog, see: [http://project.webplatform.org/infrastructure/issues/80 Story 80; Automating deployment of Blog]

* Set in place deployment tests;
** Cover all edge-cases a backend served by Varnish must have
** Cover all edge-cases a request served by Varnish should have
** Think of Behat/ReSpec for a server. See {{OperationsTask|144}}

* Monitoring and alerts
** Document expectations and endpoints along with links to documentation for each service
** Use deployment tests as monitoring? ref [http://riltsken.github.io/devops/infrastructure/monitoring/2014/04/19/making-runbooks-more-useful-by-exposing-them-through-monitoring.html making "runbooks" more useful by exposing through monitoring]
** etc...