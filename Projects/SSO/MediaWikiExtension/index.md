---
title: 'MediaWiki SSO using Firefox Accounts'
uri: 'WPD:Projects/SSO/MediaWikiExtension'

---
This page describes various details on how to install and find code specific to WebPlatform.org SSO installation related to MediaWiki. To have an higher level description of how we implemented it, see [WPD:Projects/SSO/How\_we\_implemented\_it](/WPD:Projects/SSO/How_we_implemented_it).

## Repositories

-   [GitHub](https://github.com/webplatform/mediawiki-fxa-sso)
-   Wikimedia Gerrit ([gitblit](https://git.wikimedia.org/summary/mediawiki%2Fextensions%2FWebPlatformAuth), [clone project](https://gerrit.wikimedia.org/r/#/admin/projects/mediawiki/extensions/WebPlatformAuth))

## Configuration sample

To use our Accounts server, you have to ask us [on the team-webplatform-systems mailing list](mailto:team-webplatform-systems@w3.org) to add your webapp to our OAuth Resource Server.

``` html
require_once( "$IP/extensions/WebPlatformAuth/WebPlatformAuth.php" );
$wgWebPlatformAuth['client']['id']             = '...';
$wgWebPlatformAuth['client']['secret']         = '...';
$wgWebPlatformAuth['endpoints']['fxa_oauth']   = 'https://oauth.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['endpoints']['fxa_profile'] = 'https://profile.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['methods']['authorize']     = 'authorization';
$wgWebPlatformAuth['methods']['token']         = 'token';
```

## Links

-   [How to debug MW](http://www.mediawiki.org/wiki/Manual:How_to_debug)
