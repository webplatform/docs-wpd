---
title: WPD:Infrastructure/analysis/2014-Improvements plan
---
<h1><span class="mw-headline" id="Sept.-Dec._2014_Improvement_plans">Sept.-Dec. 2014 Improvement plans</span></h1>
<p>This sprint is about refactoring the server infrastructure to ease the maintenance work and automate what’s possible.
</p><p>For the project summary, refer to <a href="/wiki/WPD:Infrastructure/reports/201410" title="WPD:Infrastructure/reports/201410">the 201410 report</a>
</p>
<h2><span class="mw-headline" id="Tasks">Tasks</span></h2>
<h3><span class="mw-headline" id="Done">Done</span></h3>
<p>What has been done and is deployable on staging at this moment.
</p>
<ul><li> Decommissioned global system features (will improve system and refactor after the rest is ready):
<ul><li> Disabled centralized log</li>
<li> Disabled Ganglia graphs</li></ul></li></ul>
<ul><li> Decommissioned VM types:
<ul><li> storage (we rely on DreamObjects instead of our own)</li>
<li> monitor (we will refactor the monitoring and log management in the next steps)</li></ul></li></ul>
<ul><li> Homepage:
<ul><li> Can be configured (switch <code>@site.tld</code> in <i>docpad.js</i>) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding.</li>
<li> Supports SSL</li>
<li> Fastly forces SSL</li>
<li> Upgraded version (DocPad)</li></ul></li></ul>
<ul><li> Wiki web app:
<ul><li> Enabled back planned for deprecation extension <a class="external text" href="http://www.mediawiki.org/wiki/Extension:SocialProfile">SocialProfile Extension</a>, see <a rel="nofollow" class="external text" href="https://github.com/webplatform/mediawiki/issues/19">issue #19</a>. Disabled explicitly uploads, serve an empty 1x1 gif.</li>
<li> Ability to disable completely Piwik tracking</li>
<li> Upgraded version</li>
<li> Supports SSL</li>
<li> Fastly forces SSL</li>
<li> Improved deployment using git</li>
<li> Deployment to exclusively use git submodules (until composer is supported)</li>
<li> Can be configured (switch <code>siteTopLevelDomain</code>, in <i>LocalSettings.php</i>) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding</li>
<li> Improved configuration system to use Salt stack provided values (no manual edition anymore)</li>
<li> Made an extension that contains all copy-pasted micro-extensions, and theme</li>
<li> Migrated all images and fonts to use www.webplatform.org instead (eventually CSS/JS will also be removed)</li>
<li> Have Salt Stack generate config automatically: database, sessions</li></ul></li></ul>
<ul><li> Wiki Compatibility tables extension:
<ul><li> When access <code>Special:Compatables?topic=css...&amp;action=purge</code> it also purges keystore copy</li>
<li> Big memory usage was caused by <i>data.json</i> being called more than once at EVERY requests (MW arch problem, error somewhere?) — fixed by saving generated HTML AND <i>data.json</i> in configurable Keystore</li></ul></li></ul>
<ul><li> Blog web app:
<ul><li> Upgraded version (WordPress)</li>
<li> Improved deployment using git</li>
<li> Reworked skin (see <a rel="nofollow" class="external text" href="https://github.com/webplatform/webplatform-wordpress-theme">WebPlatform WordPress theme repo</a>) to manage theme and plugin configuration through Git. See article: <a rel="nofollow" class="external text" href="http://blog.g-design.net/post/60019471157/managing-and-deploying-wordpress-with-git">Managing and deploying WordPress with Git</a>.</li>
<li> Skin can be configured (switch <code>siteTopLevelDomain</code>) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding</li>
<li> Have Salt Stack generate config automatically: database, sessions</li></ul></li></ul>
<ul><li> Stats web app:
<ul><li> Upgraded version (Piwik)</li>
<li> Improved deployment using git</li>
<li> Reworked skin, forked project and changed theme to match our site theme (there are no real template system nor theme support)</li>
<li> Support SSL</li>
<li> Fastly to force SSL</li>
<li> Config to use database table for sessions (the only one supported off-the-shelf by Piwik so far)</li>
<li> Config points automatically to database and Memcached/Redis IPs</li></ul></li></ul>
<ul><li> Project web app:
<ul><li> Upgraded BugGenie version (BugGenie branch-32)</li>
<li> Skin can be configured (switch <code>siteTopLevelDomain</code>) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding</li>
<li> Support SSL</li>
<li> Fastly to force SSL</li>
<li> Config points automatically to database and Memcached IPs</li></ul></li></ul>
<ul><li> Improve error pages:
<ul><li> When backend server crash, before Fastly marks the backend "unhealthy", send link to status page (see <a rel="nofollow" class="external text" href="http://www.webplatformstaging.org/errors/503.html">static version</a>)</li></ul></li></ul>
<ul><li> <b>Upgrade to latest Ubuntu 14.04 LTS version</b>, and their configured services for each VM types;
<ul><li> notes</li>
<li> bots</li>
<li> db</li>
<li> app</li>
<li> blog</li>
<li> project</li>
<li> memcache</li>
<li> backup</li>
<li> elasticsearch</li>
<li> piwik</li>
<li> source</li>
<li> account</li>
<li> mail</li></ul></li></ul>
<p><br />
</p>
<ul><li> Ways to define role of a VM type
<ul><li> Use of Salt mine to store static data such as internal IP addresse for automatic configuration generation</li>
<li> Parse the VM name and make it as a role (e.g. <i>memcache-jobs1</i>, has roles: [memcache, jobs]) so we can target secondary service allocation based on the role and not exclusively on the hostname</li></ul></li></ul>
<ul><li> Change Salt stack behavior:
<ul><li> Create a grain to learn in which deployment level (e.g. "staging") we are in</li>
<li> Create a grain to learn what are the roles the VM has (e.g. [salt])</li></ul></li></ul>
<ul><li> Service resiliency subsystem "Monit" XXX:
<ul><li> <b>Purpose</b>: Ensure critical services are up</li>
<li> Ensure common service is running: salt-minion, ssh</li>
<li> <b>Purpose</b>: Ensure critical services are up</li>
<li> ensure MySQL servers are up on db VM types</li>
<li> ensure Apache HTTP server up on app*, project*, blog*, notes*, piwik*, webat* VM types</li>
<li> ensure Nutcracker is running on app*, project*, blog*, piwik*  VM types</li>
<li> ensure NGINX HTTP server is up on accounts*  VM types</li>
<li> ensure ElasticSearch is up on elastic*  VM types</li>
<li> ensure Memcached is up on memcache*  VM types</li>
<li> ensure alert email config and destination is configured depending of staging/production</li>
<li> ensure disk usage alerts are in place</li></ul></li></ul>
<p><br />
</p>
<ul><li> Key store clusters (Memcached, Redis):
<ul><li> <b>Purpose:</b> Each cluster fills a role, depending of the life expectancy of the stored data (e.g. sessions should not be cleared, page cache might)</li>
<li> Ensure only local network can connect</li>
<li> Each web app runtime origin VM types should have a <b>Keystore broker client</b> (e.g. Nutcracker)</li></ul></li></ul>
<ul><li> Configure <b>Key store broker client</b> (Nutcracker):
<ul><li> <b>Purpose:</b> Have everything locally is much quicker, this component keeps a local cache, see  <a rel="nofollow" class="external text" href="https://code.facebook.com/posts/296442737213493/introducing-mcrouter-a-memcached-protocol-router-for-scaling-memcached-deployments/">MCRouter introduction</a></li>
<li> Separate port number per use-case, most popular (i.e. will be used most) will use default port number</li>
<li> Use-case 1: Session storage (most popular)</li>
<li> Use-case 2: Keystore (e.g. various components in MediaWiki, etc)</li>
<li> Set <code>session.save_handler</code> correctly and consistently</li></ul></li></ul>
<ul><li> NGINX:
<ul><li> Make sure that every vhosts has error page; see <code>/srv/webplatform/errors</code></li></ul></li></ul>
<ul><li><ul><li> <i>Setup logrotate for non typical logs</i>: \[mw-logs, fastly, remote logs\]</li></ul></li></ul>
<ul><li> <b>Upgrade to latest Ubuntu 14.04 LTS version</b>, and their configured services:</li></ul>
<ul><li> Blog web app:
<ul><li> Support SSL</li>
<li> Fastly to force SSL</li>
<li> Config W3TotalCache to use local Nutcracker port</li>
<li> Config points automatically to database IP</li></ul></li></ul>
<p><br />
</p>
<ul><li> Database cluster, VM types [db]: 
<ul><li> Migrate all databases into new cluster using MariaDB 10.1</li>
<li> Ensure every components gets the list of IP addresses of the database servers through Salt stack</li>
<li> Setup replication</li>
<li> Automatic backups, sends to DreamObjects bucket</li></ul></li></ul>
<ul><li> Apache:
<ul><li> Make sure that every vhosts has error page; see <code>/srv/webplatform/errors</code></li></ul></li></ul>
<ul><li> On elastic VM type:
<ul><li> Automatic backups, sends to DreamObjects bucket</li></ul></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:30827-0!*!0!!*!*!*!esi=1 and timestamp 20150731185555 and revision id 101355
 -->
