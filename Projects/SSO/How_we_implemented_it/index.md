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

* <tt>id</tt>: Is a 8 byte hexadecimal string that you will need to have on the client configuration
* <tt>secret</tt>: Is a 32 byte hexadecimal string that you will also need on the client configuration.
* <tt>redirectUri</tt>: Is where you should send the users to when they successfully authenticated. 


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
* The client identifier ("<tt>client_id</tt>")
* What the application wants ("<tt>scope</tt>")
* What state it was in ("state"), this is a random key used to store inside a keystore such as memcache so we can retrieve the state data after the authentication process.

Since the OAuth server knows who is the client, it adjusts the title to "Sign in to WebPlatform Test".

[[File:sso_steps_login_dialog.png]]

'''NOTE''' In the screenshot above, you see ''scope=profile'', since the snapshot, we changed the scope name to use the name ''session'' because we needed to differentiate web application that will use OAuth to create local sessions. The profile scope might be used for other purposes later down the road.

Once the authentication worked (maybe the user had to create an account first) the OAuth server sends you to the <tt>callbackUri</tt>. 

'''NOTE''' Compared to common OAuth2 server implementation, in Mozilla Firefox Accounts OAuth server, the callback is configured in the server configuration. In various OAuth2 implementation, the callback was also sent  through the OAuth signin and was the reason of a security breach.


=== 2. Redirected the callback URI ===

From that callback, we get two keys from the server and it allows your local web application to finish handshake.

The callback URI might look like this:

<syntaxHighlight>http://docs.webplatform.org/test/Special:AccountsHandler/callback?code=SOMETHING_LONG&state=5a72cd23b1b5feb8</syntaxHighlight>

* <tt>state</tt>: Is that string we gave in the previous step, we get it back so we can resume where we were before the authentication process. If the state data (e.g. previous page visited) was serialized and sent to Memcache, we can ask it once again and resume.
* <tt>code</tt>: This is a one-time token that we can use to get an OAuth2 Token. In this example, its "SOMETHING_LONG"

Based on the received data, we can make some a few calls to retrieve and store the required data.


=== 3. Register authorization token ===

This call is from the backend server (i.e. MediaWiki in PHP) that isn’t visible from the web browser.

The call to get the token contains the following data:

* <tt>client_id</tt>: The identifier we configured in both OAuth server and the client
* <tt>client secret</tt>: The shared secret
* <tt>code</tt>: The temporary token to get in exchange our OAuth2 Bearer token.

The request is similar to this cURL call:

<syntaxHighlight>
curl -XPOST -H 'Content-Type: application/json' 'https://oauth.accounts.webplatform.org/v1/token' -d '{"client_id":"7e7e11299d95d789","client_secret":"a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa","code":"SOMETHING_LONG"}'
</syntaxHighlight>

We get in exchange the Bearer token in a response similar to this:

<syntaxHighlight>
{"access_token":"6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31","token_type":"bearer","scope":"session"}
</syntaxHighlight>

The '''access_token''' is what we needed to get our user data from the our OAuth2 protected API: The profile server.

'''NOTE''' Anybody who has an OAuth Bearer token could eventually act as the user. At the time, the only protected service is the profile server, but we might want to protect other components later down the road.


=== 4. Reading data from the profile server ===

In our case, that's what we want all client applications (WebPlatform test wiki, Annotator, etc) wants to start from.

Otherwise, we would have to start all over again. My suggestion described at [[#SSO and remembering]] could resume from that step and save us the hassle to ask users to login from each client web application.

Each requests made to an OAuth2 protected API has to be made accompanied with the bearer token in the request header. 

Assuming our web application has a valid Bearer token, we can get the account data we need to start a session through the profile server. 

The call to the profile server can be done like this through cURL:

<syntaxHighlight>
curl  -H 'Content-Type: application/json' -H "Authorization: Bearer 6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31" 'https://profile.accounts.webplatform.org/v1/session/read'
</syntaxHighlight>

'''NOTE''' Sending headers is something quite natural, in fact, the web browsers does this for us all the time. When we request web pages on a website that has cookies —either for tracking, and/or to keep your current session— we are sending them for each element of the page, including images and assets. This is on the web server to take care to give a different document if he sees fit. In the case of an OAuth2 Bearer token, its is of the utmost importance to have it sent only through SSL, and ideally always outside of the reach of the web browser because it is basically a key to get information on your account, without asking your permission.
If the profile server accepted our Bearer token, we should get a JSON object looking like this:

<syntaxhighlight>{username: 'jdoe', fullName: 'John Doe', email: 'hi@example.org'}</syntaxhighlight>

We can now start the session in the client web application.


=== 5. Initialize local web application session ===

Since each web application can have different database, we are using this information to find if a user already exists in the local database, or we create one with the default details for the user. 

Based on the data received from the profile server, we initialize a session locally.

* Check if it can find a user matching the given username
* Create a new user if not
* Start local session, cookies, etc.

Also, from the state key, we can resume where we were by retrieving what was stored originally in Memcache. Once the handshake is finished, we delete the content of that state.

<syntaxhighlight>{return_to: 'http://docs.webplatform.org/wiki/WPD:Projects/SSO/Login_Workflows'}</syntaxhighlight>

Based on that information, we issue a redirect and the user is back where he was.


== SSO and remembering ==

=== SSO and remembering, proposal 1 ===

Provided we would have a way to store the user Bearer token somewhere and that other WebPlatform client application would be able to retrieve it, we would be able to have this password less login.

Since the Bearer token has a long enough lifetime that we could store it and retrieve it internally at will and create password less login for all other applications.

This key has a lot of value for potential attackers because it is the only key that would allow to impersonate anybody. This is why we should make sure it isn’t accessible publicly.

By adding a routine to save to memcache what we get at [[#3. Register authorization token]], we could have all other clients web apps to start from [[#4. Reading data from the profile server]].

Steps:
* Create a predictable key name and store it to memcache
* Adjust MediaWiki Extension —and eventually other client web applications— to retrieve it
* Make sure that memcache isn’t accessible publicly!

=== SSO and remembering, proposal 2 ===

'''Story''': A user clicks on login on an SSO enabled webapp. Once the OAuth handshake finished, the session is opened on the accounts.webplatform.org server.

How to get to know, somewhere else, that that handshake worked.

In run time order...

==== FxA needs the following code ====

===== 0.1. In fxa-content-server, add =====

<syntaxHighlight>
      // WebPlatform Specific ===============================
      // file: app/scripts/views/base.js
      // line: 40
      var fxaC = this.fxaClient;
      function readAndReplyHasSession( e ) {
        var b = window.localStorage.getItem('__fxa_session');
        var sessionData = JSON.parse(b);

        fxaC.isSignedIn(sessionData.sessionToken)
            .done(
              function( promised ){
                e.source.postMessage({hasSession: promised, sessionToken: sessionData.sessionToken || null}, e.origin);
              }
            );
      }
      window.addEventListener("message", readAndReplyHasSession, false);
      // /WebPlatform Specific ==============================
</syntaxHighlight>

===== 0.2. And adjust the CSP policies =====

(Not ready yet)

<syntaxHighlight>
      // WebPlatform Specific ===============================
      // file: server/bin/fxa-content-server.js
      // line: 62
      // Adjust helmet to accept xss from specific hosts
      // see: https://github.com/evilpacket/helmet
      //app.use(helmet.xframe('allow-from', 'http://docs.webplatform.org'));
      // /WebPlatform Specific ==============================
</syntaxHighlight>

==== 1. Sign in to ("A") ====

In our case, let’s connect through the staging ("A") wiki:

<syntaxHighlight>http://docs.mroftalpbew.org/wiki/Main_Page</syntaxHighlight>

Complete signin in process through the accounts server ("C"), and you should get back to the staging wiki with a session opened.


==== 2. Go to ("B"), another web app that also uses the accounts server ====

In this example, let’s use the test ("B") wiki:

<syntaxHighlight>http://docs.webplatform.org/test/Main_Page</syntaxHighlight>

The following JavaScript MUST happen.

===== 2.1. From B, prepare to receive message from C popup =====

This is where we listen to what we get from the accounts server, validate if a session exists, and trigger the calls to the profile server with the received data. (TODO)

    window.addEventListener("message", function(returned){console.log(returned.data)}, false);

===== 2.2. From B, open a popup to ("C") =====

    var popup = window.open('https://accounts.webplatform.org', 'authchecker', "menubar=yes,location=yes,resizable=yes,scrollbars=yes,status=yes");

'''NOTE''' Ideally, it should be an iframe but we need to adjust Content Security Policies (TODO).

===== 2.3. From B, Send trigger to ask message to the C window =====

Since C already has event listener described in 0.1, we should be able to send the following trigger:

    popup.postMessage("hi", "https://accounts.webplatform.org");

'''NOTE''' At the moment, we are sending a post message with random data, we might change the trigger mechanism later.

==== 3. From B, you should get back a response coming form C ====

Provided a session is already open, we should get something similar to:

    {hasSession: true, sessionToken: "e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f"}

If there is no session in the accounts server ("C"), we would get:

    {hasSession: false, sessionToken: null}

==== 4. With a sessionToken, we can read data from the profile server ====

An endpoint accepts requests only from a limited set of IP addresses (only internal to WebPlatform servers), with a sessionToken (TODO)

    GET https://profile.accounts.webplatform.org/v1/session/recover?sessionToken=e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f

The `session/recover` makes database queries similar to:

    SELECT HEX(s.uid) AS uid, a.normalizedEmail AS email, a.username AS username, a.fullName AS fullName FROM sessionTokens AS s, accounts AS a WHERE s.uid = a.uid AND tokenData = unhex('e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f');

Returns a JSON object:

    {username: 'jdoe', fullName: 'John Doe', email: 'hi@example.org'}

In the case of an invalid/expired sessionToken, nothing/an error should be returned. TODO