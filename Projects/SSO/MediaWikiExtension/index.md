= MediaWiki SSO using Firefox Accounts =

This page describes various details on how to install and find code specific to WebPlatform.org SSO installation related to MediaWiki. To have an higher level description of how we implemented it, see [[WPD:Projects/SSO/How_we_implemented_it]].

== Repositories ==

* [https://github.com/webplatform/mediawiki-fxa-sso GitHub]
* Wikimedia Gerrit ([https://git.wikimedia.org/summary/mediawiki%2Fextensions%2FWebPlatformAuth gitblit],  [https://gerrit.wikimedia.org/r/#/admin/projects/mediawiki/extensions/WebPlatformAuth clone project])

== Configuration sample ==

To use our Accounts server, you have to ask us [mailto:team-webplatform-systems@w3.org on the team-webplatform-systems mailing list] to add your webapp to our OAuth Resource Server.

<syntaxhighlight>
require_once( "$IP/extensions/WebPlatformAuth/WebPlatformAuth.php" );
$wgWebPlatformAuth['client']['id']             = '...';
$wgWebPlatformAuth['client']['secret']         = '...';
$wgWebPlatformAuth['endpoints']['fxa_oauth']   = 'https://oauth.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['endpoints']['fxa_profile'] = 'https://profile.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['methods']['authorize']     = 'authorization';
$wgWebPlatformAuth['methods']['token']         = 'token';
</syntaxhighlight>

== Links ==
* [http://www.mediawiki.org/wiki/Manual:How_to_debug How to debug MW]