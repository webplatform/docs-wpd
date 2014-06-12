= How we implemented SSO =

== Summary ==

The objective of this document is to describe the various moving parts involved in creating SSO for WebPlatform.org. It is meant to give a high level overview of the moving parts parts.

The authentication portal is using our own fork of Mozilla Firefox Accounts deployed on WebPlatform.org infrastructure. Details of the adaptations are described in [[WPD:Projects/SSO/Adapt_Firefox_Accounts_for_WebPlatform]].


== Steps ==

=== 1. Configure the OAuth server to accept requests from a client ===

In OAuth terminolgy, a client is a consumer that is authorized to rely on the OAuth server. A client can be, in our case, a web application.

In this example, we are allowing WebPlatform Docs test wiki to use the accounts server to authenticate users.

Client configuration is described in the project documentation available at [https://github.com/webplatform/fxa-oauth-server/blob/master/docs/clients.md docs/clients.md].

An entry in the OAuth server looks like this:

<syntaxHighlight>
  "clients": [
    {
       "id": "7e7e11299d95d789",
       "secret": "a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa",
       "name": "WebPlatform Test",
       "image_uri": "...",
       "redirectUri":"http://docs.webplatform.org/test/Special:AccountsHandler/callback",
       "whitelisted": true
    }
  ]
</syntaxHighlight>

* '''id''': Is a 8 byte hexadecimal string that you will need to have on the client configuration
* '''secret''': Is a 32 byte hexadecimal string that you will also need on the client configuration.
* '''redirectUri''': Is where you should send the users to when they successfully authenticated. 


=== 2. Configure client ===

Configuring a client to use our OAuth server can be different depending on how the extension implements OAuth2. In the previous example, we are connecting to a MediaWiki installation that has an extension (see [[WPD:Projects/SSO/MediaWikiExtension]]) that expects we send users to '''Special::AccountsHandler/callback''' after a successful authentication.

A configuration for a client has similar parameters:

<syntaxHighlight>
require_once( "$IP/extensions/WebPlatformAuth/WebPlatformAuth.php" );
$wgWebPlatformAuth['client']['id']             = '7e7e11299d95d789';
$wgWebPlatformAuth['client']['secret']         = 'a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa';
$wgWebPlatformAuth['endpoints']['fxa_oauth']   = 'https://oauth.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['endpoints']['fxa_profile'] = 'https://profile.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['methods']['authorize']     = 'authorization';
$wgWebPlatformAuth['methods']['token']         = 'token';
</syntaxHighlight>

While configuration can be different depending on the client extension, a few endpoints are required to be used in our installation.

* <tt>GET https://oauth.accounts.webplatform.org/v1/authorization</tt>
* <tt>POST https://oauth.accounts.webplatform.org/v1/authorization</tt>
* <tt>POST https://oauth.accounts.webplatform.org/v1/token</tt>
* <tt>GET https://profile.accounts.webplatform.org/v1/session/read</tt>, with scope 'session'

Most of these requests aren’t made through the browser but through a server-side HTTP client. In the MediaWiki extension, we are using Guzzle. Even though the calls are aimed at endpoints under SSL, it feels safer to have those requests made outside of the reach of the visitor web browser.


=== 1. From a page, when you click login ===

The web application generates and sends to an URI, it holds a few details:
* The client identifier ("client_id")
* What the application wants ("scope")
* What state it was in ("state"), this is a random key used to store inside a keystore such as memcache so we can retrieve the state data after the authentication process.

Since the OAuth server knows who is the client, it adjusts the title to "Sign in to WebPlatform Test".

[[File:sso_steps_login_dialog.png]]

Once the authentication worked (maybe the user had to create an account first) the OAuth server sends you to the <tt>callbackUri</tt>. 

'''NOTE''' Compared to common OAuth2 server implementation, in Mozilla Firefox Accounts OAuth server, the callback is configured in the server configuration. In various OAuth2 implementation, the callback was also sent  through the OAuth signin and was the reason of a security breach.


=== 2. Redirected the callback URI ===

From that callback, we get two keys from the server and it allows your local web application to finish handshake.

* <tt>state</tt>: Is that string we gave in the previous step, we get it back so we can resume where we were before the authentication process. If the state data (e.g. previous page visited) was serialized and sent to Memcache, we can ask it once again and resume.
* <tt>code</tt>: This is a one-time token that we can use to get an OAuth2 Token.

Based on the received data, we can make some a few calls to retrieve and store the required data.


=== 3. Register authorization token ===

This call is from the backend server (i.e. MediaWiki in PHP) that isn’t visible from the web browser.

Behind the scene (not visible in the browser), we send a POST to the endpoint along with some private data:

* client key
* client secret
* code

To get a token, we send a POST request similar to this cURL call:

<syntaxHighlight>
curl -XPOST -H 'Content-Type: application/json' 'https://oauth.accounts.webplatform.org/v1/token' -d '{"client_id":"7e7e11299d95d789","client_secret":"a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa","code":"SOMETHING_LONG"}'
</syntaxHighlight>

We get in exchange something similar to this

<syntaxHighlight>
{"access_token":"6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31","token_type":"bearer","scope":"session"}
</syntaxHighlight>

The '''access_token''' is what we needed to get our user data from the our OAuth2 protected API: The profile server.

'''NOTE''' Anybody who has an OAuth Bearer token could eventually act as the user. At the time, the only protected service is the profile server, but we might want to protect other components later down the road.


=== 4. Reading data from the profile server ===

In our case, that's what we want all client applications (WebPlatform test wiki, Annotator, etc) wants to start from.

Otherwise, we would have to start all over again. My suggestion described at [[#SSO and remembering]] could resume from that step and save us the hassle to ask users to login from each client web application.

Assuming we have a valid Bearer token, we can get the data we need through an HTTP call similar to this:

<syntaxHighlight>
curl -v -H "Authorization: Bearer 6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31" "https://profile.accounts.webplatform.org/v1/session/read"
</syntaxHighlight>

In return we get a JSON object looking like this:

<syntaxhighlight>{username: 'jdoe', fullName: 'John Doe', email: 'hi@example.org'}</syntaxhighlight>

We can now start the session in the browser.


=== 5. Initialize local web application session ===

Based on the data received from the profile server, we initialize a session locally.

* Check if it can find a user matching the given username
* Create a new user if not
* Start local session, cookies, etc.

Also, from the state key, we can resume where we were by retrieving what was stored originally in Memcache. Once the handshake is finished, we delete the content of that state.

<syntaxhighlight>{return_to: 'http://docs.webplatform.org/wiki/WPD:Projects/SSO/Login_Workflows'}</syntaxhighlight>

Based on that information, we issue a redirect and the user is back where he was.


== SSO and remembering ==

Provided we would have a way to store the user Bearer token somewhere and that other WebPlatform client application would be able to retrieve it, we would be able to have this password less login.

Since the Bearer token has a long enough lifetime that we could store it and retrieve it internally at will and create password less login for all other applications.

This key has a lot of value for potential attackers because it is the only key that would allow to impersonate anybody. This is why we should make sure it isn’t accessible publicly.

By adding a routine to save to memcache what we get at [[#3. Register authorization token]], we could have all other clients web apps to start from [[#4. Reading data from the profile server]].

Steps:
* Create a predictable key name and store it to memcache
* Adjust MediaWiki Extension —and eventually other client web applications— to retrieve it
* Make sure that memcache isn’t accessible publicly!