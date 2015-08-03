---
title: WPD:Infrastructure/architecture/VM roles
---
<div style="float:right;width:33%;word-wrap:break-word;clear:both;">
<h3><span class="mw-headline" id="WebPlatform_server_Infrastructure_architecture_menu"><a href="/wiki/WPD:Infrastructure/architecture" title="WPD:Infrastructure/architecture">WebPlatform server Infrastructure architecture menu</a></span></h3>
<div class="subpagelist">
<ul><li> <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM" title="WPD:Infrastructure/architecture/Base configuration of a VM">Base configuration of a VM</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status" title="WPD:Infrastructure/architecture/Reports to review status">Reports to review status</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Roles_and_environment_level" title="WPD:Infrastructure/architecture/Roles and environment level">Roles and environment level</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/SSL_certificates" title="WPD:Infrastructure/architecture/SSL certificates">SSL certificates</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/The_salt_master" title="WPD:Infrastructure/architecture/The salt master">The salt master</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish" title="WPD:Infrastructure/architecture/Things to consider when we expose service via Fastly and Varnish">Things to consider when we expose service via Fastly and Varnish</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Useful_commands" title="WPD:Infrastructure/architecture/Useful commands">Useful commands</a></li>
<li> <strong class="selflink">VM roles</strong></div></li></ul>
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
<h1><span class="mw-headline" id="VM_Roles">VM Roles</span></h1>
<h2><span class="mw-headline" id="Network_diagram_overview">Network diagram overview</span></h2>
<h3><span class="mw-headline" id="Former_configuration">Former configuration</span></h3>
<p>@@TODO make variant of <i>Future configuration</i> to illustrate difference.
</p>
<h3><span class="mw-headline" id="Future_configuration">Future configuration</span></h3>
<p>In order to allow us to support more than one backend server and a simplified frontend configuration scheme, we are going to create a cluster of NGINX servers that’ll serve every requests.  While some components are served by Fastly and others aren’t, the NGINX cluster will serve all of them regardless.
</p><p><a href="/wiki/File:Component-diagram-internal.png" class="image"><img alt="Component-diagram-internal.png" src="//static.webplatform.org/w/public/8/83/Component-diagram-internal.png" width="1624" height="841" /></a>
</p><p><br />
</p>
<h1><span class="mw-headline" id="Roles">Roles</span></h1>
<p>In order to have a fully functional site we need to have at least one VM for each of the following roles. Some VMs can fill more than one role.
</p><p>The <b>following list is in order of importance</b> based on the fact <b>that the ones below would generally rely on the ones over them</b>;
</p>
<h2><span class="mw-headline" id="source">source</span></h2>
<p>This VM is used to mirror every dependencies we are using. While most of the repositories are open to the public, some of them aren’t.
</p><p>Note that although we could have a staging <i>source</i> VM (i.e. <i>source.webplatformstaging.org</i>), ONLY <i>source.webplatform.org</i> should be considered as a source of truth.
</p>
<ul><li> <b>How many required</b>: Only one</li>
<li> <b>Must it have a public IP address?</b>: yes</li>
<li> <b>Expected public hostname</b>: source.webplatform.org</li>
<li> <b>Must it have a Volume</b>: <i>yes</i>  (to store the code repositories)</li>
<li> <b>Must it have a DNS reverse lookup</b>: No</li>
<li> <b>What does it do?</b>:
<ul><li> <i>Source code hosting</i> through git, using Gitolite. We might soon either use back Gerrit or Phabricator</li></ul></li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="salt">salt</span></h2>
<p>Before the infrastructure rework sprint of January 2015, the salt master was the only VM that must not be deleted. Since then its possible to create a fresh VM and apply a set of scripts to have a new master. The procedure to create a salt master is in <a href="/wiki/WPD:Infrastructure/architecture/The_salt_master" title="WPD:Infrastructure/architecture/The salt master">WPD:Infrastructure/architecture/The_salt_master</a>.
</p>
<ul><li> <b>How many required</b>: Only one</li>
<li> <b>Must it have a public IP address?</b>: yes</li>
<li> <b>Expected public hostname</b>: salt.webplatform.org</li>
<li> <b>Must it have a Volume</b>: yes  (to store the backups and other work files)</li>
<li> <b>Must it have a DNS reverse lookup</b>: No</li>
<li> <b>What does it do?</b>:
<ul><li> <i>DNS server</i> (using 'gdnsd'), every other VM has <i>/etc/resolv.conf</i> pointing to the salt master</li>
<li> <i>Salt master</i>, each changes on every VM is made from that VM</li>
<li> <i>SSH jump box</i>: SSH Access to every VM is made through that VM. A banner on login gives the current environment 'level', and ssh configuration to use</li>
<li> <i>rsync</i> (through an 'xinetd' service), each VM can pull files from it. Including backups</li></ul></li></ul>
<h3><span class="mw-headline" id="Design_decisions">Design decisions</span></h3>
<ul><li> The salt master was originally a VM that we had to pray to keep running. From now on everything under <b>/srv/</b> should be managed in a git repository. If its managed by something not obvious, there’s should be a <b>README.md</b> file @@TODO, ensure the file is present.</li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="Also_related">Also related</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="https://gist.github.com/WebPlatformDocs/01c09df78f05612c281f">Gist containing every essential bootstrap script</a>. (take the contents of the Gist as a snapshot. @@TODO, put link to authoritative version here)</li>
<li> <a rel="nofollow" class="external text" href="https://gist.github.com/WebPlatformDocs/780307ff289864ba02f5#file-salt-master-conf">Salt Master Monit config</a>  (take the contents of the Gist as a snapshot. @@TODO, put link to authoritative version here)</li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/The_salt_master" title="WPD:Infrastructure/architecture/The salt master">WPD:Infrastructure/architecture/The_salt_master</a></li></ul>
<h2><span class="mw-headline" id="mail">mail</span></h2>
<p>Every VMs has <i>exim4</i> configured to send mail to the VM that has the "mail" role.
</p><p>According to email server management best practices, it would be better to have two. Having only one is OK.
</p>
<ul><li> <b>How many required</b>: One. </li>
<li> <b>Must it have a public IP address?</b>: yes</li>
<li> <b>Expected public hostname</b>: mail.webplatform.org</li>
<li> <b>Must it have a Volume</b>: No</li>
<li> <b>Must it have a DNS reverse lookup</b>:
<ul><li> <i>mail.webplatform.org</i></li>
<li> <i>mail2.webplatform.org</i></li>
<li> <i>mail.webplatformstaging.org</i></li>
<li> <i>mail2.webplatformstaging.org</i></li></ul></li>
<li> <b>Must it have publicly opened ports?</b>:
<ul><li> 25 (ensure Postfix only authorizes our machines to relay email!!)</li></ul></li>
<li> <b>What does it do?</b>:
<ul><li> SMTP relay (using Postfix) to the outside world</li>
<li> OpenDKIM to sign emails before sending them</li>
<li> Mailgraph, creates rrd graphs to visualize the email traffic</li></ul></li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="backup">backup</span></h2>
<p>The VM that gathers backups from every other VMs.
</p>
<ul><li> <b>How many required</b>: Only one</li>
<li> <b>Must it have a public IP address?</b>: No</li>
<li> <b>Expected public hostname</b>: N/A</li>
<li> <b>Must it have a Volume</b>: yes (not vital, very useful in need of recovery)</li>
<li> <b>Must it have a DNS reverse lookup</b>: No</li>
<li> <b>Must it have publicly opened ports?</b>: No</li>
<li> <b>What does it do?</b>:
<ul><li> rsync data from other VMs to keep backups (cronjob made by root)</li>
<li> shares through NFS snapshots for ElasticSearch</li></ul></li></ul>
<h3><span class="mw-headline" id="Design_decisions_2">Design decisions</span></h3>
<p>ElasticSearch snapshot setup requires we have a network mount point. While we previously had a GlusterFS cluster that could have been used for that purpose, we decided to change our setup to stop using it. We therefore needed, again, to setup network share. This time It has been decided to use NFS from the backup VM and potentially share through it only what’s required to facilitate backups but not as a main way to gather data when generating web pages.
</p>
<h3><span class="mw-headline" id="Also_related_2">Also related</span></h3>
<ul><li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster#How_backups_are_made" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">ElasticSearch cluster; How backups are made</a></li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="masterdb">masterdb</span></h2>
<p>There must only one that has both <i>db</i> AND <i>masterdb</i> (e.g. <b>db1-masterdb</b>). Note that the number isn’t important, just that by convention the lower number is the one we use as a master to send writes to. 
</p>
<ul><li> <b>How many required</b>: One</li>
<li> <b>Must it have a public IP address?</b>: N/A</li>
<li> <b>Expected public hostname</b>: N/A</li>
<li> <b>Must it have a Volume</b>: yes (not vital, very useful in need of recovery)</li>
<li> <b>Must it have a DNS reverse lookup</b>: No</li>
<li> <b>Must it have publicly opened ports?</b>: No</li>
<li> <b>What does it do?</b>:
<ul><li> "Meta" role, other configuration could use it as an indice to know which one is the entry point</li></ul></li></ul>
<h3><span class="mw-headline" id="Design_decisions_3">Design decisions</span></h3>
<ul><li> While its not the case at the moment, the objective behind the the role name "master" was to have a way to recognize which should be considered as an entry point within a cluster (e.g. elasticsearch, postgresql, mail). The name "masterdb" could be renamed "master" and the states configuration should be adjusted to allow other services to use this pattern.</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="db">db</span></h2>
<p>The first database server we originally had was MySQL 5.1 and the VM had a name starting by <i>db</i>. 
</p>
<ul><li> <b>How many required</b>: One or more</li>
<li> <b>Must it have a public IP address?</b>: No</li>
<li> <b>Expected public hostname</b>: N/A</li>
<li> <b>Must it have a Volume</b>: yes (not vital, very useful in need of recovery)</li>
<li> <b>Must it have a DNS reverse lookup</b>: No</li>
<li> <b>Must it have publicly opened ports?</b>: No</li>
<li> <b>What does it do?</b>:
<ul><li> MariaDB server v 10.x</li>
<li> MariaDB replication (when applicable)</li></ul></li></ul>
<h3><span class="mw-headline" id="Also_related_3">Also related</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="https://renoirboulanger.com/blog/2015/01/create-mariadb-cluster-replication-ssl-salt-stack">Create a MariaDB cluster with replication over SSL</a> has been written to describe how to create a VM</li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Managing_MySQL_replication" title="WPD:Infrastructure/procedures/Managing MySQL replication">WPD:Infrastructure/procedures/Managing_MySQL_replication</a></li></ul>
<h3><span class="mw-headline" id="Design_decisions_4">Design decisions</span></h3>
<ul><li> As of the time this was written, it’s a known fact that while we do have two database servers, only one is used by all our web applications.  The other database server is only used as a hot backup with replication over SSL setup. All reads and writes are sent to the only VM that has both <i>db</i> and <i>masterdb</i> roles.</li>
<li> The upcoming infrastructure changes would have to be more specific as we’ll also need to have a PostgreSQL cluster and we’ll have to create a different role name for the different vendor.</li>
<li> We do not forbid database writes on ANY db server and that even though we may have one VM with the role masterdb because we want to be able to quickly change master.</li>
<li> It is planned to use new replication features such as ones that we can send writes to any nodes and the replication will be made consistent everywhere. This has to be tested first though.</li>
<li> At the beginning this VM was running on Ubuntu 10.04 with MySQL 5.1</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="sessions">sessions</span></h2>
<p>This VM runs both <b>Redis</b> and <b>Memcached</b>. It depends which session storage mechanism each Web app supports. ONLY session data are stored in those keystores, nothing else.
</p><p>This VM is only accessible from internal network which is sensible considering its use. To add one more notch up, this VM should have its services to have some more enforcement to prevent access to the session tokens it stores (e.g. by requiring password and such). 
</p>
<ul><li> <b>How many required</b>: One or more</li>
<li> <b>Must it have a public IP address?</b>: No</li>
<li> <b>Expected public hostname</b>: N/A</li>
<li> <b>Must it have a Volume</b>: N/A</li>
<li> <b>Must it have a DNS reverse lookup</b>: N/A</li>
<li> <b>Must it have publicly opened ports?</b>: No</li>
<li> <b>What does it do?</b>:
<ul><li> <i>Redis server</i></li>
<li> <i>Memcached server</i></li></ul></li></ul>
<h3><span class="mw-headline" id="Design_decisions_5">Design decisions</span></h3>
<ul><li> The objective of the <i>sessions</i> VM is to store only user session data in a key store (redis, memcached, etc) so we do not mix general use object cache web applications would make.</li>
<li> Note that there’s no enforcement, authentications, checks for who and what we send at the moment of writing of this document</li>
<li> Each web app VM will eventually run a proxy to the sessions storage this VM provides with a software called <i>Nutcracker</i> (a.k.a. <a rel="nofollow" class="external text" href="https://github.com/twitter/twemproxy/">TwEmProxy</a>) </li>
<li> As with other keystore VMs such as the ones with roles <b>redis</b> and <b>memcache</b>, the port should be the default value from the VM itself. Each client VM to sessions will also expose the default port as if it was local.</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="accounts">accounts</span></h2>
<ul><li> <b>How many required</b>: 1</li>
<li> <b>Must it have a public IP address?</b>: Yes (for now, until we make it behind NGINX)</li>
<li> <b>Expected public hostname</b>:</li>
<li> <b>Must it have a Volume</b>: N/A</li>
<li> <b>Must it have a DNS reverse lookup</b>: N/A</li>
<li> <b>Must it have publicly opened ports?</b>: N/A</li>
<li> <b>What does it do?</b>:
<ul><li> OAuth2 server ("fxa-oauth-server")</li>
<li> Internal auth API server ("fxa-auth-server")</li>
<li> Profile server ("fxa-profile-server")</li>
<li> Auth server frontend ("fxa-content-server")</li></ul></li></ul>
<h3><span class="mw-headline" id="Design_decisions_6">Design decisions</span></h3>
<p>While at the moment we do expose an HTTP server through NGINX to the public, this VM will be eventually not visible.
</p><p>It is planned, in <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/115">webplatform/ops#115</a></b>, that we get the IP address it uses to make a new set of hostnames and create a "round robin" (i.e. a DNS name that has more than one IP address) and create a NGINX frontend proxy. This new proxy would serve content from internal backends to the public without exposing 
</p>
<h2><span class="mw-headline" id="memcache">memcache</span></h2>
<ul><li> <b>How many required</b>: More than one</li>
<li> <b>Must it have a public IP address?</b>: No</li>
<li> <b>Expected public hostname</b>: N/A</li>
<li> <b>Must it have a Volume</b>: N/A</li>
<li> <b>Must it have a DNS reverse lookup</b>: N/A</li>
<li> <b>Must it have publicly opened ports?</b>: N/A</li>
<li> <b>What does it do?</b>:
<ul><li> Memcached server</li></ul></li></ul>
<h3><span class="mw-headline" id="Design_decisions_7">Design decisions</span></h3>
<ul><li> Memcached is an extremely simple API. Although we can enforce SSL certificate validation, it is not done by default and it also has no authentication. The practice is to ensure that only nodes that should have access can make commands to it. The way to do is to either use Security Groups from the cloud provider, or firewall rules inside the VM.</li>
<li> Create a Memcache cluster per use case. For example we could have a memcached cluster for sessions, and another one to cache heavy pages.  If we need to purge the heavy pages cache we can send a purge command to all nodes from that cluster without worrying to destroy every user sessions.</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="elastic">elastic</span></h2>
<ul><li> <b>How many required</b>: One or more</li>
<li> <b>Must it have a public IP address?</b>: No</li>
<li> <b>Expected public hostname</b>: N/A</li>
<li> <b>Must it have a Volume</b>: N/A</li>
<li> <b>Must it have a DNS reverse lookup</b>: N/A</li>
<li> <b>Must it have publicly opened ports?</b>:  N/A</li>
<li> <b>What does it do?</b>:
<ul><li> Elasticsearch server</li></ul></li></ul>
<h3><span class="mw-headline" id="Design_decisions_8">Design decisions</span></h3>
<ul><li> ElasticSearch doesn’t have authentication. If we are to expose it to the public, it MUST be from an API that would forbid dangerous commands. Something not done yet; It’ll be eventually required.</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="app">app</span></h2>
<ul><li> <b>How many required</b>:</li>
<li> <b>Must it have a public IP address?</b>:</li>
<li> <b>Expected public hostname</b>:</li>
<li> <b>Must it have a Volume</b>:</li>
<li> <b>Must it have a DNS reverse lookup</b>:</li>
<li> <b>Must it have publicly opened ports?</b>:</li>
<li> <b>What does it do?</b>:</li></ul>
<h3><span class="mw-headline" id="Design_decisions_9">Design decisions</span></h3>
<ul><li> Originally made to run all web apps when we launched in 2012: mediawiki, blog and later were TheBugGenie and so on. After some time Ryan decided to move the blog to one VM and with other speed problems to create another VM for BugGenie. This is why we have that many VMs nowadays.</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="blog">blog</span></h2>
<ul><li> <b>How many required</b>:</li>
<li> <b>Must it have a public IP address?</b>:</li>
<li> <b>Expected public hostname</b>:</li>
<li> <b>Must it have a Volume</b>:</li>
<li> <b>Must it have a DNS reverse lookup</b>:</li>
<li> <b>Must it have publicly opened ports?</b>:</li>
<li> <b>What does it do?</b>:</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="project">project</span></h2>
<ul><li> <b>How many required</b>:</li>
<li> <b>Must it have a public IP address?</b>:</li>
<li> <b>Expected public hostname</b>:</li>
<li> <b>Must it have a Volume</b>:</li>
<li> <b>Must it have a DNS reverse lookup</b>:</li>
<li> <b>Must it have publicly opened ports?</b>:</li>
<li> <b>What does it do?</b>:
<ul><li> Runs The Bug Genie</li></ul></li></ul>
<h3><span class="mw-headline" id="Design_Decisions_10">Design Decisions</span></h3>
<ul><li> VM created to host exclusively Bug Genie project management.</li>
<li> Bug Genie will eventually be phased out in favor to something else.</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="notes">notes</span></h2>
<ul><li> <b>How many required</b>:</li>
<li> <b>Must it have a public IP address?</b>:</li>
<li> <b>Expected public hostname</b>:</li>
<li> <b>Must it have a Volume</b>:</li>
<li> <b>Must it have a DNS reverse lookup</b>:</li>
<li> <b>Must it have publicly opened ports?</b>:</li>
<li> <b>What does it do?</b>:</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="bots">bots</span></h2>
<ul><li> <b>How many required</b>:</li>
<li> <b>Must it have a public IP address?</b>:</li>
<li> <b>Expected public hostname</b>:</li>
<li> <b>Must it have a Volume</b>:</li>
<li> <b>Must it have a DNS reverse lookup</b>:</li>
<li> <b>Must it have publicly opened ports?</b>:</li>
<li> <b>What does it do?</b>:</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="jobrunner">jobrunner</span></h2>
<ul><li> <b>How many required</b>:</li>
<li> <b>Must it have a public IP address?</b>:</li>
<li> <b>Expected public hostname</b>:</li>
<li> <b>Must it have a Volume</b>:</li>
<li> <b>Must it have a DNS reverse lookup</b>:</li>
<li> <b>Must it have publicly opened ports?</b>:</li>
<li> <b>What does it do?</b>:</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="piwik">piwik</span></h2>
<ul><li> <b>How many required</b>:</li>
<li> <b>Must it have a public IP address?</b>:</li>
<li> <b>Expected public hostname</b>:</li>
<li> <b>Must it have a Volume</b>:</li>
<li> <b>Must it have a DNS reverse lookup</b>:</li>
<li> <b>Must it have publicly opened ports?</b>:</li>
<li> <b>What does it do?</b>:</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="nginx">nginx</span></h2>
<ul><li> <b>How many required</b>:</li>
<li> <b>Must it have a public IP address?</b>:</li>
<li> <b>Expected public hostname</b>:</li>
<li> <b>Must it have a Volume</b>:</li>
<li> <b>Must it have a DNS reverse lookup</b>:</li>
<li> <b>Must it have publicly opened ports?</b>:</li>
<li> <b>What does it do?</b>:</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="specs">specs</span></h2>
<ul><li> <b>How many required</b>:</li>
<li> <b>Must it have a public IP address?</b>:</li>
<li> <b>Expected public hostname</b>:</li>
<li> <b>Must it have a Volume</b>:</li>
<li> <b>Must it have a DNS reverse lookup</b>:</li>
<li> <b>Must it have publicly opened ports?</b>:</li>
<li> <b>What does it do?</b>:</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="hhvmbackend">hhvmbackend</span></h2>
<ul><li> <b>How many required</b>:</li>
<li> <b>Must it have a public IP address?</b>:</li>
<li> <b>Expected public hostname</b>:</li>
<li> <b>Must it have a Volume</b>:</li>
<li> <b>Must it have a DNS reverse lookup</b>:</li>
<li> <b>Must it have publicly opened ports?</b>:</li>
<li> <b>What does it do?</b>:</li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:58597-0!*!0!!*!5!*!esi=1 and timestamp 20150731185708 and revision id 101119
 -->
