= MediaWiki SSO using Firefox Accounts =

*Repository*: https://github.com/webplatform/mediawiki-fxa-sso

== Configuration sample ==

To use our Accounts server, you have to ask us [mailto:team-webplatform-systems@w3.org] to add your webapp to our OAuth Resource Server.

<syntaxhighlight>
require_once( "$IP/extensions/WebPlatformAuth/WebPlatformAuth.php" );
$wgWebPlatformAuth['client']['id']             = '...';
$wgWebPlatformAuth['client']['secret']         = '...';
$wgWebPlatformAuth['endpoints']['fxa_oauth']   = 'https://oauth.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['endpoints']['fxa_profile'] = 'https://ssl.webplatform.org/v1/';
$wgWebPlatformAuth['methods']['authorize']     = 'authorization';
$wgWebPlatformAuth['methods']['token']         = 'token';
</syntaxhighlight>