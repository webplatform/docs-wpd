---
title: WPD:Infrastructure/reports/201503
---
<h1><span class="mw-headline" id="March_2015_Infrastructure_change_log_since_2013">March 2015 Infrastructure change log since 2013</span></h1>
<p>List of high level Infrastructure changes we’ve worked on in the last two years.
</p><p>Should cover;
</p>
<ul><li> Which individual software we run, pieces involved, what needs each piece fulfills</li>
<li> Software we got rid of (e.g. web based IRC client, GlusterFS, etc)</li>
<li> New components</li>
<li> We weren't assured of long term free hosting form HP, thankfully DreamHost took charge of us</li>
<li> Automation improvements</li>
<li> Overview of lessons learned, and wins</li></ul>
<p>On a related note, there are also notes in <a href="/wiki/WPD:Infrastructure/reports/201410" title="WPD:Infrastructure/reports/201410">the 201410 report published last year</a> and in the <a href="/wiki/WPD:Infrastructure/analysis/2014-Improvements_plan" title="WPD:Infrastructure/analysis/2014-Improvements plan"><b>2014 Improvement plan</b> page</a>.
</p>
<h2><span class="mw-headline" id="Software_we_currently_use">Software we currently use</span></h2>
<h3><span class="mw-headline" id="Web_applications_we_host">Web applications we host</span></h3>
<table class="wikitable sortable">
<tr>
<th> Resource
</th>
<th> Software
</th>
<th> Deployment repository
</th>
<th> Location
</th></tr>
<tr>
<th> Home page
</th>
<td> <a rel="nofollow" class="external text" href="https://docpad.org/">DocPad</a>
</td>
<td> <a rel="nofollow" class="external text" href="https://github.com/webplatform/www.webplatform.org">repository</a>
</td>
<td> <a rel="nofollow" class="external text" href="http://webplatform.org/">webplatform.org/</a>
</td></tr>
<tr>
<th> wiki (<a href="/wiki/Special:Version" title="Special:Version">version</a>)
</th>
<td> <a class="external text" href="https://www.mediawiki.org/wiki/MediaWiki">MediaWiki</a> using Wikimedia Foundation ("wmf/1.24wmfX") continuous release branches
</td>
<td> <a rel="nofollow" class="external text" href="https://github.com/webplatform/mediawiki">repository</a>
</td>
<td> <a rel="nofollow" class="external text" href="https://docs.webplatform.org/wiki/">docs.webplatform.org/wiki/</a>
</td></tr>
<tr>
<th> IRC logger
</th>
<td> <a rel="nofollow" class="external text" href="http://classam.github.io/pierc/">Lumberjack (now called Pierc)</a>
</td>
<td> TODO
</td>
<td> <a rel="nofollow" class="external text" href="https://www.webplatform.org/talk/chatlogs/">www.webplatform.org/talk/chatlogs/</a>
</td></tr>
<tr>
<th> Analytics
</th>
<td> <a rel="nofollow" class="external text" href="http://piwik.org/">Piwik</a>
</td>
<td> TODO
</td>
<td> <a rel="nofollow" class="external text" href="https://stats.webplatform.org/">stats.webplatform.org/</a>
</td></tr>
<tr>
<th> Blog
</th>
<td> <a rel="nofollow" class="external text" href="http://wordpress.org/">WordPress</a>
</td>
<td> <a rel="nofollow" class="external text" href="https://github.com/webplatform/blog-service">repository</a>
</td>
<td> <a rel="nofollow" class="external text" href="https://blog.webplatform.org/">blog.webplatform.org/</a>
</td></tr>
<tr>
<th> Code sandbox
</th>
<td> <a rel="nofollow" class="external text" href="http://dabblet.com/">Dabblet</a>
</td>
<td> <a rel="nofollow" class="external text" href="https://github.com/webplatform/dabblet">repository</a>
</td>
<td> <a rel="nofollow" class="external text" href="http://code.webplatform.org/">code.webplatform.org/</a>
</td></tr>
<tr>
<th> Project management
</th>
<td> <a rel="nofollow" class="external text" href="http://www.thebuggenie.com/">The Bug Genie</a>
</td>
<td> <a rel="nofollow" class="external text" href="https://github.com/webplatform/thebuggenie">repository</a>
</td>
<td> <a rel="nofollow" class="external text" href="https://project.webplatform.org/">project.webplatform.org/</a>
</td></tr>
<tr>
<th> Accounts
</th>
<td> <a rel="nofollow" class="external text" href="https://wiki.mozilla.org/Identity/Firefox_Accounts">Firefox Accounts</a>
</td>
<td> see <a href="/wiki/WPD:Projects/SSO" title="WPD:Projects/SSO">SSO Project page</a>
</td>
<td> <a rel="nofollow" class="external text" href="https://accounts.webplatform.org/">accounts.webplatform.org/</a>
</td></tr>
<tr>
<th> Hypothes.is
</th>
<td> <a rel="nofollow" class="external text" href="https://www.hypothes.is/">Hypothes.is</a>
</td>
<td> TODO
</td>
<td> <a rel="nofollow" class="external text" href="https://notes.webplatform.org/">notes.webplatform.org/</a>
</td></tr>
<tr>
<th> Discuss
</th>
<td> <a rel="nofollow" class="external text" href="http://www.discourse.org/">Discourse</a>
</td>
<td> TODO
</td>
<td> <a rel="nofollow" class="external text" href="https://discuss.webplatform.org/">discuss.webplatform.org/</a>
</td></tr></table>
<h3><span class="mw-headline" id="Web_application_that_we_rely_on">Web application that we rely on</span></h3>
<table class="wikitable sortable">
<tr>
<th> Resource
</th>
<th> Software
</th>
<th> Location
</th>
<th> Usage
</th></tr>
<tr>
<th> Operations issue tracker
</th>
<td> GitHub "<i>webplatform/ops"</i> project and <a rel="nofollow" class="external text" href="https://huboard.com/">Hubboard</a>
</td>
<td> <a rel="nofollow" class="external text" href="https://huboard.com/webplatform/ops/#/"><i>KanBan</i> dashboard</a>, <a rel="nofollow" class="external text" href="https://webplatform.github.io/ops">webplatform.github.io/ops</a>
</td>
<td> A Dashboard utility to visualize in columns what’s next, what´s in progress, and what’s done.
</td></tr>
<tr>
<th> WebPlatformDocs GitHub account
</th>
<td> GitHub
</td>
<td> <a rel="nofollow" class="external text" href="https://gist.github.com/WebPlatformDocs">gist.github.com/WebPlatformDocs</a>, <a rel="nofollow" class="external text" href="https://github.com/WebPlatformDocs">github.com/WebPlatformDocs</a>
</td>
<td> Store all <i>code.webplatform.org</i> gists in GitHub. This account was created before GitHub introduced "organizations".
</td></tr>
<tr>
<th> WebPlatform GitHub organization
</th>
<td> GitHub
</td>
<td> <a rel="nofollow" class="external text" href="https://github.com/WebPlatform">github.com/WebPlatform</a>
</td>
<td> An organization in which we store all repositories
</td></tr></table>
<h3><span class="mw-headline" id="Misc.">Misc.</span></h3>
<dl><dt>Ubuntu</dt>
<dd> We were originally running on two different versions of Ubuntu 10.04 and 12.04. While both are "Long Term Support" we weren’t running on the same version for every servers, and also had no automatic install of security updates. Since mid-2014 all servers uses the same version — Ubuntu 14.04 LTS — and automatic security updates</dd>
<dt>Memcached</dt>
<dd> A "key store" system that many web applications relies to keep the HTML that it generated, speeding up the page render. </dd>
<dt>Redis <i>(new since 2014)</i></dt>
<dd> Another "key store" system similar to Memcached, but in use for storing session data so we can balance web application backend load across multiple web servers. Benefit of Redis over Memcached is that we can easily make Redis calls through SSL/TLS and require clients to authenticates. Also, we can configure MediaWiki to store async jobs over to Redis instead of a MySQL table. MediaWiki operations team lead said that tables is fine for heavy load. Unless we get wikipedia.org type of load.</dd>
<dt>ElasticSearch <i>(new since 2014)</i></dt>
<dd> A "REST" web application on which we can index documents, and use as a search engine. We store annotations in it, and so we could configure MediaWiki so we improve search capabilities.</dd>
<dt>MariaDB <i>(new since 2014)</i></dt>
<dd> A drop-in replacement to MySQL, in use by most of the infrastructure. We could also configure it to use <i>Galera</i> so we could send writes to any node in the cluster. Might be a next step.</dd>
<dt>Monit <i>(new since 2014)</i></dt>
<dd> A system that is made to help ensure vital services are up.</dd>
<dt>NGINX <i>(new since 2014)</i></dt>
<dd> A Web Server and Proxy software. We will eventually use NGINX instead of apache in a near future</dd>
<dt>Apache</dt>
<dd> The original web server software. Only MediaWiki has an hard requirement to it, until we change our configuration or that Semantic MediaWiki  (<i>"SMW"'</i>) requirement changes. At this time, SMW requires PHP to be run through <b>mpm-prefork</b> which is, in contrast to multi-threaded servers, is asking to always keep up a set of processes to answer HTTP requests. It is said in SMW mailing list, this hard requirement might change soon.</dd>
<dt>php-fpm <i>(new since 2014)</i></dt>
<dd> A PHP execution environment that NGINX connects to to server dynamic pages. Currently in use with Piwik, other PHP web applications (except MediaWiki) could be migrated to it soon enough. Unless we could run everything that runs in <i>php5-fpm</i> to HHVM (see below) instead.</dd></dl>
<p><br />
</p>
<h3><span class="mw-headline" id="Software_we_are_currently_evaluating_to_use">Software we are currently evaluating to use</span></h3>
<dl><dt><a rel="nofollow" class="external text" href="https://github.com/twitter/twemproxy">Nutcracker</a></dt>
<dd> A "key store" proxy system that we could install on each app server making a local copy and balancing the load accross both Redis and Memcached.</dd>
<dt><a rel="nofollow" class="external text" href="http://hhvm.com/">HHVM</a></dt>
<dd> A complete rewrite of the PHP execution environment with known improvements compared to php-fpm. We might migrate all compatible PHP web applications to this runtime environment.</dd>
<dt><a rel="nofollow" class="external text" href="http://logstash.net/">LogStash</a></dt>
<dd> A centralized log manager. It harmonizes, archives and process any log messages we send to it. Serves as an easy to use log search engine</dd>
<dt> <a rel="nofollow" class="external text" href="http://phabricator.org/">Phabricator</a></dt>
<dd> A web application made to help organize software projects. It features an IRC bot from which we could monitor more than one IRC chat room (our chat bot is not maintained and doesn’t scale well). Also, we could Phabricator as a place to: store sensitive documents, mirror GIT/SVN/Mercurial repositories we rely on, host temporary Git/Mercurial stashes so we don’t risk losing them around, code "pastebin" so we don’t need to rely on GitHub gists, etc. See <a rel="nofollow" class="external text" href="http://phabricator.org/applications/">Phabricator applications list for more details</a></dd>
<dt> <a rel="nofollow" class="external text" href="https://www.docker.com/">Docker</a></dt>
<dd> A system that allows us to create "executable" packages called "containers" out of any software or web application. At a first look, it looks like a VM, but its a very thin one that only does one job and removes the need to upgrade operating system packages and allow to roll back from any previous builds that had been made</dd>
<dt> <a rel="nofollow" class="external text" href="http://deis.io/">Deis</a></dt>
<dd> An "orchestration" system that automates the cycle of building Docker containers. It automates handling of subsystems such as load balancing, remove the need to hardcode web application related deployment scripts, archiving, etc. With this, we could build on push anything that has a "<i>Dockerfile</i>" at the root of the project.  </dd>
<dt>CoreOS</dt>
<dd> A thin Linux distribution that has Docker preinstalled and a few other orchestration utilities to provide auto-discoverability and automatic scaling.</dd></dl>
<p><br />
</p>
<h3><span class="mw-headline" id="Conventions_in_place">Conventions in place</span></h3>
<p>Idea is that any service use default configuration as if its local, use of equivalent service to delegate/proxy to specialized set of servers
</p>
<dl><dt>What’s common on any VMs</dt>
<dd> Refer to <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM" title="WPD:Infrastructure/architecture/Base configuration of a VM">architecture documentation at  <b>Base configuration of a VM</b></a> </dd>
<dt>email</dt>
<dd> Each server uses <i>localhost</i> as their email server gateway, but the local email server then uses a specialized VM only for sending emails</dd>
<dt>memcached (still in evaluation)</dt>
<dd> Each application server (i.e. a server that runs a web application backend technology such as <i>PHP</i> or <i>Python</i>) acts as if <i>Memcached</i> is local, but in fact a service called <i>Nutcracker</i> (a.k.a. TwEmProxy) is configured to talk to more than one Memcached servers serving the purpose of keeping a local copy of the data.</dd>
<dt>secrets, passwords ("accounts" pillars)</dt>
<dd> Are stored in a separate set of (salt) pillars in <i>/srv/private/pillar/accounts/production.sls</i> and (will be) hosted in a private Git repository at W3C. In there, we keep all API secrets, tokens, and passwords we need. Every configuration and services pulls information from there. To adjust, edit and commit the file then run a "highstate".  (staging is at  '<i>/srv/private/pillar/accounts/staging.sls</i>)</dd>
<dt>Deployment sensible variables... ("infra" pillars)</dt>
<dd> Are stored in a centralized (salt) pillars in <i>/srv/pillar/infra/production.sls</i>. In there, we list private IP addresses of database servers, ElasticSearch, etc. Every configuration file and states relies on it. To adjust, edit and commit the file, then run a "highstate". (staging is at  '<i>/srv/private/pillars/accounts/staging.sls</i>)</dd>
<dt>ssh access</dt>
<dd> The only way to work on any is to pass through the salt master as a "jump box", see <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM#Accessing_a_VM_using_SSH" title="WPD:Infrastructure/architecture/Base configuration of a VM">Accessing a VM using SSH</a></dd>
<dt>which level a VM is in?</dt>
<dd>The "level" grain exists to tell which configuration file to use in both <i>/srv/pillar/infra/$level.sls</i> AND in <i>/srv/private/pillars/accounts/$level.sls</i>. To get which level, you can ask from the terminal <code>salt \* grains.get level</code>. Refer to <a href="/wiki/WPD:Infrastructure/architecture/Roles_and_environment_level" title="WPD:Infrastructure/architecture/Roles and environment level">architecture documentation at <b>Roles and Environment level</b></a></dd></dl>
<p><br />
</p>
<h3><span class="mw-headline" id="Lessons_learned">Lessons learned</span></h3>
<dl><dt>Varnish</dt>
<dd> Refer to <a href="/wiki/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish#Caveats" title="WPD:Infrastructure/architecture/Things to consider when we expose service via Fastly and Varnish"><b>Caveats</b> in Things to consider when we expose service via Fastly and Varnish</a></dd>
<dt>Use IP address instead of names, in web application configuration files</dt>
<dd> Name resolution can be costly. I learned that it speeds page render time when I explicitly set Database, Redis, Memcached, ElasticSearch IPs instead of names that we’d put in <i>/etc/hosts</i>. Since we now manage every configuration file through salt since late 2014, we can now update easily this information automatically</dd>
<dt>To support multiple runtime backends ...</dt>
<dd> Its much easier to configure a public Front-end server to use directly a private-access-only backend that handles when to serve static files it already hosts and which files should pass through FastCGI, etc. Front-end nodes wouldn’t need to duplicate that part, but be responsible to balance the load and take care of both static files and in-memory page cache. Much like Varnish does.</dd></dl>
<p><br /> 
</p>
<h2><span class="mw-headline" id="Work_done_per_year">Work done per year</span></h2>
<h3><span class="mw-headline" id="2013">2013</span></h3>
<ul><li> <i>Started working on WebPlatform on July 2013</i></li>
<li> Setup analytics solution w/ <b>Piwik</b>, at <b>stats.webplatform.org</b></li>
<li> Only one set of Virtual Machines (VMs) exposing live site, no room to work on improvements without risks of affecting live site</li>
<li> Deployment scripts were assuming exactly one deployment, making it hard to do gradual roll out</li>
<li> In configuration files, every IP Addresses were scattered around and I had to search around to adjust changes so that the servers would get the information updated</li>
<li> VMs were running with two different OS versions: Ubuntu 10.04 and 12.04, no automatic installation of security patches</li>
<li> Setup of a private OpenStack at DreamHost ("DHO"; DreamHost OpenStack) cluster from a 4 blades server, server was lent by DreamHost</li>
<li> Server migration from HP Cloud into DHO <a href="/wiki/WPD:Infrastructure/analysis/2013-Migrating_to_a_new_cloud_provider" title="WPD:Infrastructure/analysis/2013-Migrating to a new cloud provider">2013 Migrating to a new Cloud Provider</a></li>
<li> Work on MySQL cluster so we could have off-site hot backup (i.e. database replication on a remote site, with logs transferred through SSL)</li>
<li> Multiple outages due to a bug in MediaWiki+Semantic MediaWiki affecting the rest of the infrastructure</li>
<li> Complete rework of MediaWiki installation. Originally it was a clone with bits and pieces pasted without source control to a scripted setup exclusively based on source controlled repositories</li>
<li> Work with Doug to create a new Compatibility data JSON schema</li>
<li> Sprint on extracting compatibility data from MDN into new Compatibility JSON schema</li>
<li> Sprint on Compatibility tables extension
<ul><li> see <a href="/wiki/WPD:Projects/CompaTables/201403-sprint" title="WPD:Projects/CompaTables/201403-sprint">201403 sprint notes</a></li>
<li> serve a copy of the generated HTML</li>
<li> flush the generated HTML copy when JSON source is updated</li>
<li> Alternate views and new supported actions:
<ol><li> single table view: <a rel="nofollow" class="external text" href="https://docs.webplatform.org/wiki/Special:Compatables?feature=border-radius&amp;format=table&amp;topic=css"><code>GET /wiki/Special:Compatables?feature=border-radius&amp;format=table&amp;topic=css</code></a></li>
<li>single table view, "naked" alternate <a rel="nofollow" class="external text" href="https://docs.webplatform.org/wiki/Special:Compatables?feature=border-radius&amp;format=table&amp;topic=css&amp;foresi=1"><code>GET /wiki/Special:Compatables?feature=border-radius&amp;format=table&amp;topic=css&amp;foresi=1</code></a></li>
<li>manual table flush <a rel="nofollow" class="external text" href="https://docs.webplatform.org/wiki/Special:Compatables?feature=border-radius&amp;format=table&amp;topic=css&amp;action=purge"><code>GET /wiki/Special:Compatables?feature=border-radius&amp;format=table&amp;topic=css&amp;action=purge</code></a></li></ol></li>
<li> Work on Semantic MediaWiki template <a rel="nofollow" class="external text" href="https://docs.webplatform.org/wiki/Template:Compatibility">Template:Compatibility</a> to allow embed in content pages</li>
<li> Creation of a GitHub repository to host compatibility data <a rel="nofollow" class="external text" href="https://github.com/webplatform/compatibility-data%7Con">GitHub <i>webplatform/compatibility-data</i></a></li>
<li>  Originally it was regenerating the HTML for EVERY page load based on a previous JSON source</li></ul></li>
<li> Removed requirement of shared storage across VMs (GlusterFS) and switched to use external DreamObjects storage (Swift) at DreamHost </li>
<li> Set in place image storage pulling files directly from DreamObjects</li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="2014">2014</span></h3>
<ul><li> Upgraded all VMs to use only Ubuntu 14.04</li>
<li> Pages are now served under SSL</li>
<li> Most of the work mentioned below until 2015 is also noted in <a href="/wiki/WPD:Infrastructure/analysis/2014-Improvements_plan" title="WPD:Infrastructure/analysis/2014-Improvements plan">2014 Improvements plan</a></li>
<li> Refactor of the homepage
<ul><li> Originally from a set of PHP files to DocPad and other <i>NodeJS</i> based scripts to make the homepage completely static </li>
<li> see <a href="/wiki/WPD:Projects/Homepage" title="WPD:Projects/Homepage">in Projects/Homepage page</a></li></ul></li>
<li> Setup of our own email exit relay so that every server uses it instead of a paid external provider</li>
<li> Deployed notes.webplatform.org w/ Hypothes.is</li>
<li> Worked on implementing "SSO" based on a shared session token key, a "profile" server would be used as a source of truth, client web app (i.e. MediaWiki) would either create a user based on the details, or start a session</li>
<li> Upgraded MySQL server version, migrated to MariaDB (Open Source version fork from the original author of MySQL)</li>
<li> Creation of an account management service
<ul><li> Based on Mozilla Firefox Accounts ("FxA")</li>
<li> Created our own fork, changed branding</li>
<li> Implemented Proof of concept of SSO using FxA for MediaWiki</li>
<li> see <a href="/wiki/WPD:Projects/SSO" title="WPD:Projects/SSO">SSO Project page</a></li></ul></li>
<li> Rework of how we deploy which now reads from a specifically crafted git repository and pull any plugins/extensions and gets configuration automatically applied
<ul><li> Piwik (stats.webplatform.org), </li>
<li> WordPress (blog.webplatform.org)</li>
<li> MediaWiki (docs.webplatform.org)</li>
<li> The IRC bot, </li>
<li> BugGenie (project.webplatform.org)</li>
<li> Annotation service (notes.webplatform.org)</li>
<li> Accounts service (accounts.webplatform.org), many repos refer to notes at <a href="/wiki/WPD:Projects/SSO" title="WPD:Projects/SSO">SSO Project page</a></li>
<li> Homepage (www.webplatform.org)</li></ul></li>
<li> Purchase of an EV SSL certificate with mention of "World Wide Web Consortium" to give a hint of the site maintainers</li>
<li> Purchase of an alternate domain name to replicate in full (!!) the server setup allowing us to test in isolation every components of the site</li>
<li> Reviewed every blog posts, and imported any images we were linking outside of our site </li>
<li> "Inventory" system that keeps in memory the internal IP addresses of each infrastructure services: MySQL, Redis, Memcache, etc.</li>
<li> Generates automatically configuration file with credentials based on the servers that are up at that moment, IP address, Passwords, Private keys, etc</li>
<li> Capability to update passwords/private keys across all web applications from one "private" configuration file</li>
<li> Setup of a "private" configuration system stored in a git repo, see <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/145">webplatform/ops#145</a></b></li>
<li> We will eventually publish all our deployment scripts to the public, except the "private" data files. Ref <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/48">webplatform/ops#48</a></b></li>
<li> Setup an NFS mount point so that ElasticSearch instances can do backups. Reviewed idea of not using inter instance storage, at least limit it only in the case of of backups... until we can store ElasticSearch snapshots through Swift/DreamObjects too, see <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/120">webplatform/ops#120</a></b></li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="2015">2015</span></h3>
<ul><li> Renamed <b>deployment.webplatform.org</b> into <b>salt.webplatform.org</b>
<ul><li> Old <b>deployment</b> —in DHO cluster— was left to run everything in production, as long as it wasn’t ready to be moved to the new environment in DreamCompute</li>
<li> Created <b>salt.webplatform.org</b> —in DreamCompute cluster— so that we could create a complete deployment of every compoenents without affecting production</li>
<li> Used both environments simultaneously and could do gradual roll out of every components. Once a roll out was made, I stopped the old version in DHO cluster.</li></ul></li>
<li> Set in place conventions to remove need to change configurations across environments, see <a href="#Conventions_in_place">#Conventions in place</a></li>
<li> Work done on "hardening" security on servers
<ul><li> Set in place automatic installation of security updates</li>
<li> The main deployment server ("salt.webplatform.org", a.k.a salt) is the only IP address we can connect through SSH, only way to access another server using salt as a proxy. Benefit is that to remove access to a user, we can remove his access on salt, everything else becomes inaccessible</li></ul></li>
<li> <b>March 2015</b>; Finished up work planned in <a href="/wiki/WPD:Infrastructure/reports/201410#Objectives" title="WPD:Infrastructure/reports/201410"><b>October 2014 sprint report</b>, according to the <i>Objectives</i></a> <i>and</i> <a href="/wiki/WPD:Infrastructure/analysis/2014-Improvements_plan" title="WPD:Infrastructure/analysis/2014-Improvements plan">2014 <b>Improvements plan</b></a> we set. Except for "automated deployment at Git push", something that’ll be done in a future sprint.</li>
<li> Created bootstrap scripts so we can rebuild "from scratch" —at ANY time— a new salt master (what’s taking care of orchestrating deployment).</li>
<li> Improved infrastructure maintenance documentation
<ul><li> <a href="/wiki/WPD:Infrastructure/architecture" title="WPD:Infrastructure/architecture">Architecture design</a>
<ul><li> <a href="/wiki/WPD:Infrastructure/architecture/VM_roles" title="WPD:Infrastructure/architecture/VM roles">What roles each server fulfills and how to leverage it</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/The_salt_master" title="WPD:Infrastructure/architecture/The salt master">How the <b>Salt Master</b> is designed</a></li></ul></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Deploying_code_changes" title="WPD:Infrastructure/procedures/Deploying code changes">How we deploy code</a></li></ul></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Replacing_a_VM" title="WPD:Infrastructure/procedures/Replacing a VM">How to replace any VM</a> (without downtime)</li>
<li> How caching is configured
<ul><li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration" title="WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration">How to maintain Varnish/Fastly caching configuration</a>, </li>
<li> Documented what should be taken into account when working on the configuration in <a href="/wiki/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish" title="WPD:Infrastructure/architecture/Things to consider when we expose service via Fastly and Varnish"><b>Things to consider when we work on Varnish configuration</b></a></li></ul></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Managing_MySQL_replication" title="WPD:Infrastructure/procedures/Managing MySQL replication">How to manage MySQL/MariaDB replication</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it" title="WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it">How to change database configuration and ensure every affected web application gets the new passswords</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">How to maintain our new ElasticSearch cluster</a>, including notes on how automatic backups are made</li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_email_services" title="WPD:Infrastructure/procedures/Maintaining email services">How to <b>Maintain email services</b></a></li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Soon.3F">Soon?</span></h2>
<p>Some notes that were gathered around that aren’t been tried yet.
</p>
<ul><li> Improve stats:
<ul><li> <b>Purpose</b>: Get system health data as graph, over time </li>
<li> Some candidates
<ul><li> <a rel="nofollow" class="external text" href="http://grafana.org">Graphana</a>?</li>
<li> <a rel="nofollow" class="external text" href="http://sensuapp.org">Sensu</a>?</li>
<li> <a rel="nofollow" class="external text" href="http://riemann.io/">Riemann</a></li>
<li> collectd</li>
<li> fluentd </li>
<li> <a rel="nofollow" class="external text" href="https://github.com/python-diamond/Diamond">Diamond</a>?</li></ul></li>
<li> Get page load stats (i.e. what <a rel="nofollow" class="external text" href="http://www.soasta.com/">SOASTA</a> does, but use open-source version; <a rel="nofollow" class="external text" href="http://www.lognormal.com/boomerang/doc/">Boomerang</a>), see <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/143">webplatform/ops#143</a></b></li>
<li> Attempt to merge data from ganglia into Graphana so we do not lose previous data</li></ul></li></ul>
<ul><li> Improve toolkit
<ul><li> Ability to debug a-la-firebug communication between backends w/ <a rel="nofollow" class="external text" href="https://blog.twitter.com/2012/distributed-systems-tracing-with-zipkin">Zipkin</a>, see <a rel="nofollow" class="external text" href="http://research.google.com/pubs/pub36356.html">paper about <i>distributed systems tracing</i></a></li>
<li> Ability to snapshot a server state for future investigation? Ref; <a rel="nofollow" class="external free" href="http://www.sysdig.org/">http://www.sysdig.org/</a></li>
<li> More food for thoughts ... <a rel="nofollow" class="external text" href="http://metrics20.org/">Metrics 2.0</a></li></ul></li></ul>
<ul><li> Get system metrics
<ul><li> Leverage Monit system, push to <a rel="nofollow" class="external text" href="http://hekad.readthedocs.org">Heka</a>? (<a rel="nofollow" class="external text" href="https://github.com/renoirb/mmonit-mock-listener">see this sandbox</a>), or <a rel="nofollow" class="external text" href="https://github.com/lunich/monitrb">use an existing one in <i>Ruby</i> that stores in MongoDB</a></li>
<li> Use NGINX status, ref <a rel="nofollow" class="external text" href="https://www.scalyr.com/community/guides/how-to-monitor-nginx-the-essential-guide">How to monitor NGINX, the essential guide</a></li>
<li> Gather ElasticSearch metrics, see <a rel="nofollow" class="external text" href="https://github.com/abronner/elasticsearch-monitoring">this repo</a></li>
<li> Get Inspiration from <a rel="nofollow" class="external text" href="http://www.lowlevelmanager.com/2014/07/monitorama-conference.html">some notes from <i>Monitorama</i> conference</a> </li></ul></li></ul>
<ul><li> Centralized logging:
<ul><li> <b>Purpose</b>: Aggregate and harmonize all log messages to see what happened (or happens)</li>
<li> LogStash to process logs (and emails? see <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/127">webplatform/ops#127</a></b>)</li>
<li> Log rotation, and create archive files every year to prevent disk filling</li>
<li> Network traffic review tool <a rel="nofollow" class="external text" href="http://www.haka-security.org/hakabana.html">HaKabana</a>; "Visualize Haka traffic in real-time using Kibana and Elasticsearch.", see <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/142">webplatform/ops#142</a></b></li></ul></li></ul>
<p><br />
</p>
<ul><li> Accounts web app:
<ul><li> PHP relying client; Create shared component compatible with Composer</li>
<li> Factor out specific to MediaWiki as an extension, use new shared PHP component</li></ul></li></ul>
<ul><li> Automatic deployment:
<ul><li> <b>Purpose</b>: Ease to have contributors to see their work online</li>
<li> Create typical deployment package (i.e. commands to run to get all dependencies, make a zip file, unpack on every servers)</li>
<li> Homepage, see: <a rel="nofollow" class="external text" href="http://project.webplatform.org/infrastructure/issues/99">Story 99; Automating deployment of Home page</a></li>
<li> Project, see: <a rel="nofollow" class="external text" href="http://project.webplatform.org/infrastructure/issues/81">Story 81; Automating deployment of Project Management tool</a> (postpone?)</li>
<li> Wiki, see: <a rel="nofollow" class="external text" href="http://project.webplatform.org/infrastructure/issues/79">Story 79; Automating deployment of Wiki</a></li>
<li> Blog, see: <a rel="nofollow" class="external text" href="http://project.webplatform.org/infrastructure/issues/80">Story 80; Automating deployment of Blog</a></li>
<li> Mis. requirements:
<ul><li> Handle dependencies, look at <a rel="nofollow" class="external text" href="https://gradle.org/">Graddle would do?</a></li>
<li> Make all web apps deployed through Docker?</li>
<li> Figure out how we could test</li></ul></li></ul></li></ul>
<ul><li> Set in place deployment tests;
<ul><li> Cover all edge-cases a backend served by Varnish must have</li>
<li> Cover all edge-cases a request served by Varnish should have</li>
<li> Think of Behat/ReSpec for a server. See <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/144">webplatform/ops#144</a></b></li></ul></li></ul>
<ul><li> Monitoring and alerts
<ul><li> Leverage LogStash as a Monitoring solution? Ref <a rel="nofollow" class="external text" href="http://www.nuxeo.com/blog/monitoring-nuxeo/">Monitoring at Nuxeo</a></li>
<li> Document expectations and endpoints along with links to documentation for each service</li>
<li> Use deployment tests as monitoring? ref <a rel="nofollow" class="external text" href="http://riltsken.github.io/devops/infrastructure/monitoring/2014/04/19/making-runbooks-more-useful-by-exposing-them-through-monitoring.html">making "run books" more useful by exposing through monitoring</a></li>
<li> etc...</li></ul></li></ul>
<ul><li> Helpers
<ul><li> Make server SSH MOTD point out links to maintenance documentation, <a rel="nofollow" class="external text" href="http://riltsken.github.io/devops/infrastructure/2014/03/16/how-server-message-of-the-day-improved-our-devops-team.html">inspired by this <i>blog post</i></a></li></ul></li></ul>
<ul><li> Dashboard and status
<ul><li> <a rel="nofollow" class="external text" href="https://shopify.github.io/dashing">Dashing</a>?</li>
<li> <a rel="nofollow" class="external text" href="https://github.com/cachethq">Cachet</a></li></ul></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:58636-0!*!0!!*!*!*!esi=1 and timestamp 20150731185936 and revision id 101374
 -->
