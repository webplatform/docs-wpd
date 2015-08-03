---
title: WPD:Projects/SSO/MediaWikiExtension
---
<h1><span class="mw-headline" id="MediaWiki_SSO_using_Firefox_Accounts">MediaWiki SSO using Firefox Accounts</span></h1>
<p>This page describes various details on how to install and find code specific to WebPlatform.org SSO installation related to MediaWiki. To have an higher level description of how we implemented it, see <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How_we_implemented_it</a>.
</p>
<h2><span class="mw-headline" id="Repositories">Repositories</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/mediawiki-fxa-sso">GitHub</a></li>
<li> Wikimedia Gerrit (<a rel="nofollow" class="external text" href="https://git.wikimedia.org/summary/mediawiki%2Fextensions%2FWebPlatformAuth">gitblit</a>,  <a rel="nofollow" class="external text" href="https://gerrit.wikimedia.org/r/#/admin/projects/mediawiki/extensions/WebPlatformAuth">clone project</a>)</li></ul>
<h2><span class="mw-headline" id="Configuration_sample">Configuration sample</span></h2>
<p>To use our Accounts server, you have to ask us <a rel="nofollow" class="external text" href="mailto:team-webplatform-systems@w3.org">on the team-webplatform-systems mailing list</a> to add your webapp to our OAuth Resource Server.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">require_once( &quot;$IP/extensions/WebPlatformAuth/WebPlatformAuth.php&quot; );
$wgWebPlatformAuth['client']['id']             = '...';
$wgWebPlatformAuth['client']['secret']         = '...';
$wgWebPlatformAuth['endpoints']['fxa_oauth']   = 'https://oauth.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['endpoints']['fxa_profile'] = 'https://profile.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['methods']['authorize']     = 'authorization';
$wgWebPlatformAuth['methods']['token']         = 'token';</pre></div></div>
<h2><span class="mw-headline" id="Links">Links</span></h2>
<ul><li> <a class="external text" href="http://www.mediawiki.org/wiki/Manual:How_to_debug">How to debug MW</a></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.018 seconds
Real time usage: 0.020 seconds
Preprocessor visited node count: 23/1000000
Preprocessor generated node count: 40/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:22695-0!*!0!!*!*!*!esi=1 and timestamp 20150731111125 and revision id 56083
 -->
