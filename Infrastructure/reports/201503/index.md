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


{| class="wikitable sortable" |
! Resource
! Software
! Deployment repository
! Project details page
! Location
|- 
! Home page
| [https://docpad.org/ DocPad]
| [https://github.com/webplatform/www.webplatform.org repository]
| TODO
| [http://webplatform.org/ webplatform.org/]
|-
! wiki ([[Special:Version|version]])
| [https://www.mediawiki.org/wiki/MediaWiki MediaWiki] using Wikimedia Foundation ("wmf/1.24wmfX") continuous release branches
| [https://github.com/webplatform/mediawiki repository]
| TODO
| [https://docs.webplatform.org/wiki/ docs.webplatform.org/wiki/]
|-
! IRC logger
| [http://classam.github.io/pierc/ Lumberjack (now called Pierc)]
| TODO
| TODO
| [https://www.webplatform.org/talk/chatlogs/ www.webplatform.org/talk/chatlogs/]
|-
! Analytics
| [http://piwik.org/ Piwik]
| TODO
| TODO
| [https://stats.webplatform.org/ stats.webplatform.org/]
|-
! Blog
| [http://wordpress.org/ WordPress]
| [https://github.com/webplatform/blog-service repository]
| TODO
| [https://blog.webplatform.org/ blog.webplatform.org/]
|-
! Code sandbox
| [http://dabblet.com/ Dabblet]
| [https://github.com/webplatform/dabblet repository]
| TODO
| [http://code.webplatform.org/ code.webplatform.org/]
|-
! Project management
| [http://www.thebuggenie.com/ The Bug Genie]
| [https://github.com/webplatform/thebuggenie repository]
| TODO
| [https://project.webplatform.org/ project.webplatform.org/]
|-
! Operations issue tracker
| GitHub "''webplatform/ops"'' project and [https://huboard.com/ Hubboard]
| N/A
| TODO
| [https://huboard.com/webplatform/ops/#/ ''KanBan'' dashboard], [https://webplatform.github.io/ops webplatform.github.io/ops]
|-
! Accounts
| [https://wiki.mozilla.org/Identity/Firefox_Accounts Firefox Accounts]
| TODO
| [[WPD:Projects/SSO|SSO Project page]]
| [https://accounts.webplatform.org/ accounts.webplatform.org/]
|}


== 2013 ==

* Installation of our own Analytics solution using '''Piwik''', at ''stats.webplatform.org''' 
* Only one set of Virtual Machines (VMs) exposing live site, no room to work on improvements without risks of affecting live site
* Deployment scripts were assuming exactly one deployment, making it hard to do gradual roll out
* VMs were running with two different OS versions: Ubuntu 10.04 and 12.04 
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


== 2014 ==

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

== 2015 ==

* '''March 2015'''; Finished up work planned in [[WPD:Infrastructure/reports/201410#Objectives|'''October 2014 sprint report''', according to the ''Objectives'']] ''and'' [[WPD:Infrastructure/analysis/2014-Improvements_plan|2014 '''Improvements plan''']] we set.