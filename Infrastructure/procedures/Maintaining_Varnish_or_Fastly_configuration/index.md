---
title: WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration
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
<li> <a href="/wiki/WPD:Infrastructure/architecture/VM_roles" title="WPD:Infrastructure/architecture/VM roles">VM roles</a></div></li></ul>
<p><b>See also</b>
</p>
<ul><li> <a href="/wiki/WPD:Infrastructure/procedures/Deploying_code_changes" title="WPD:Infrastructure/procedures/Deploying code changes">Deploying code changes</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Replacing_a_VM" title="WPD:Infrastructure/procedures/Replacing a VM">Replacing a VM</a></li>
<li> <strong class="selflink">Maintaining Fastly configuration</strong></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Managing_MySQL_replication" title="WPD:Infrastructure/procedures/Managing MySQL replication">Managing MySQL replication</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it" title="WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it">Create new database credentials and configure a web application to use it</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">Maintaining ElasticSearch cluster</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_email_services" title="WPD:Infrastructure/procedures/Maintaining email services">Maintaining email services</a></li></ul>
</div>
<h1><span class="mw-headline" id="Maintaining_Varnish.2FFastly_configuration">Maintaining Varnish/Fastly configuration</span></h1>
<p>The following summarizes how to manage our Varnish caching service served by our friends at <a rel="nofollow" class="external text" href="https://fastly.com">Fastly</a>. Note that the documentation describes how Varnish works but also how to manage Fastly very own Varnish cluster so we don’t have to.
</p><p>This document is specific on how to maintain Varnish configuration at Fastly. Notes that describes the specifics of things we should keep in mind when configuring the cache should be moved to <a href="/wiki/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish" title="WPD:Infrastructure/architecture/Things to consider when we expose service via Fastly and Varnish">Things to consider when we expose service via Fastly and Varnish</a>
</p>
<h2><span class="mw-headline" id="Abastract">Abastract</span></h2>
<p>If your system uses cookies, which is most of the time the case, Varnish does not caches. The configuration MUST to be adjusted to each site specifics. Details such as a web application sending HTTP headers such as Cache-Control, Set-Cookie, Cookie can still prevent caching to happen.
</p><p>This page is about keeping notes on current Varnish configuration files and notes to help maintaining an appropriate caching strategy. 
</p>
<h2><span class="mw-headline" id="NOTES">NOTES</span></h2>
<h3><span class="mw-headline" id="Varnish_version_and_limitations">Varnish version and limitations</span></h3>
<p>An important detail to remember is that Fastly is using Varnish 2.1.4, their configuration specifics do not support either pipe, ban, nor purging with ACL. 
</p><p>Also, the way to provide CDN service is with what they call "Shield", it is basically a layer of application that stores a local copy of what is grabbed by a service backend server. Provided that the backend server do not explicitly prevent caching, or that the VCL has appropriate adjustments, Fastly will send files from the Shield before hitting again the backend servers.
</p><p>VCL is the Varnish Configuration language file, throughout the panel, we can see two VCL buttons, the one beside the service name and revision is to download the generated VCL, whereas we can also provide our own VCL that must have keywords so the panel adds content to it.
</p><p>A recommended way to work is to follow <b><a rel="nofollow" class="external text" href="https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL-">How do I mix and match Fastly VCL with custom VCL</a></b>
</p>
<h3><span class="mw-headline" id="Details_to_consider">Details to consider</span></h3>
<h4><span class="mw-headline" id="MediaWiki">MediaWiki</span></h4>
<p>Here are the specifics for MediaWiki
</p>
<ul><li> Note that most of the cookies starts with the <i>$wgDBname</i> string from the <i>Settings*.php</i> file. In the list below, its value is 'wpwiki'.</li>
<li> Delete all cookies, except: wpwikiUserID, wpwiki_session, wpwikiUserName, Token, LoggedOut, dismissSiteNotice</li>
<li> Only place to set cookies are when UserLogin, UserLogout</li></ul>
<p><b>Reminder</b> more notes about specifics for each web application we deployed are noted in  <a href="/wiki/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish" title="WPD:Infrastructure/architecture/Things to consider when we expose service via Fastly and Varnish"><b>Things to consider when we expose service via Fastly and Varnish</b></a>
</p>
<h2><span class="mw-headline" id="Accessing_VCL_configuration_from_Fastly">Accessing VCL configuration from Fastly</span></h2>
<p><a href="/wiki/File:20131121-Fastly-vcl-buttons.png" class="image"><img alt="20131121-Fastly-vcl-buttons.png" src="//static.webplatform.org/w/public/6/68/20131121-Fastly-vcl-buttons.png" width="978" height="638" /></a>
To access/overwrite the file in Fastly, go to:
</p>
<ul><li> <a rel="nofollow" class="external text" href="https://app.fastly.com/">Fastly pannel</a>, login</li>
<li> Select targeted site (e.g. <i>docs.webplatform.org</i>)</li>
<li> Configure tab on top, Configure button</li>
<li> VCL on the left</li></ul>
<h4><span class="mw-headline" id="Wizard_to_add_a_backend_host">Wizard to add a backend host</span></h4>
<p>While describing how to debug an issue we had with Semantic MediaWiki, I described how to change which public IPs would be proxyed by Fastly.
</p><p>The screenshot below is described in <a href="/wiki/WPD:Infrastructure/procedures/Rebuilding_Semantic_Media_Wiki_when_job_queue_is_going_out_of_control" title="WPD:Infrastructure/procedures/Rebuilding Semantic Media Wiki when job queue is going out of control">WPD:Infrastructure/procedures/Rebuilding_Semantic_Media_Wiki_when_job_queue_is_going_out_of_control</a>
</p><p><a href="/wiki/File:fastly-docs-service-hosts-screenshot.png" class="image"><img alt="fastly-docs-service-hosts-screenshot.png" src="//static.webplatform.org/w/public/f/fb/fastly-docs-service-hosts-screenshot.png" width="800" height="634" /></a>
</p>
<h3><span class="mw-headline" id="Current_Fastly_configuration">Current Fastly configuration</span></h3>
<p>Make the content of snippet as a file and upload it to the Fastly control pannel.
</p><p>Configuration files are stored on <a rel="nofollow" class="external text" href="https://github.com/webplatform/varnish-configs">Github, in <b>webplatform/varnish-configs</b> project</a>, the VCL file name should match the subdomain and also the service bane in Fastly dashboard.
</p>
<h2><span class="mw-headline" id="Reference">Reference</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL-">Fastly: How to mix and match Fastly VCL with custom VCL (Varnish configuration file)</a></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/varnish-configs"><b>WebPlatform</b> varnish-configs GitHub repository</a></li>
<li> See also more notes on the topic at <a href="/wiki/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish" title="WPD:Infrastructure/architecture/Things to consider when we expose service via Fastly and Varnish">Things to consider when we expose service via Fastly and Varnish</a></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.089 seconds
Real time usage: 1.844 seconds
Preprocessor visited node count: 47/1000000
Preprocessor generated node count: 74/1000000
Post‐expand include size: 993/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%   37.204      1 - -total
100.00%   37.204      1 - WPD:Infrastructure/architecture
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:12455-0!*!0!!*!5!*!esi=1 and timestamp 20150730193808 and revision id 101238
 -->
