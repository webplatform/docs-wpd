= How we implemented SSO =

== Summary ==

The objective of this document is to describe how we implemented a SSO solution for WebPlatform.org. It is meant to give a high level overview of the various moving parts parts.

The authentication portal is using our own fork of Mozilla Firefox Accounts ("FxA") deployed on WebPlatform.org infrastructure. Details of the adaptations are described in [[WPD:Projects/SSO/Adapt_Firefox_Accounts_for_WebPlatform]].

=== Stories ===

The present document describe how we adress a set of user stories but it should be noted that the final result is expected to use the SSO accross ALL WebPlatform.org services and participating W3C Specifications.

* As a non authenticated person, I want to edit in the [http://docs.webplatform.org/wiki/css/properties/border a page on docs.webplatform.org/wiki/] ("A").
* As a non authenticated person, I want to add annotations on a participating [http://www.w3.org/2014/annotation/experiment/webaudio.html W3C spec that supports annotations] ("B")
* As a non authenticated person, I want to experiment with Docs features in the [http://docs.webplatform.org/test/css/properties/border WebPlatform Docs "test" wiki] ("C").
* As a non authenticated person, I want to be allowed to edit in the [http://docs.mroftalpbew.org/wiki/Main_Page WebPlatform Docs Staging wiki] ("D") and see if the upcoming deployment will work
* As a non authenticated visitor, I want to start a session and be allowed to perform [A, B, C, D] without authenticating myself more than once


== Using OAuth2 to start a session ==

=== 0. Premise ===

In order to fulfill the given [[#Stories]], we needed to implement a SSO solution that allows multiple web applications ("client") communicate to the accounts server, provide a single authority resource to feed relying clients with centralized user data, and let each configured web applications to handle their local users and sessions.

In this implementation we are passing through authentication to get an OAuth2 Bearer token so that we can get data on the behalf of the authenticated user.

The following makes use of the generated Authorization token to read a profile server and read associated user data (i.e. email address, full name, username, etc.) that will be used in all web applications.

''NOTE'' At the moment, the Authorization token is used only once. In future development, we might want to add features and will need to store securely that token to make other actions on the behalf of the user.


=== 1. Configure the OAuth server to accept requests from a client ===

In OAuth terminology, a client is a consumer that is authorized to rely on the OAuth server. A client can be a web application, but its not only limited to that.

In this example, we are going to show how the [http://docs.webplatform.org/test/css/properties/border WebPlatform Docs "test" wiki] ("C") gets data from the various layers.

Client configuration is described in the project documentation available in the  [https://github.com/webplatform/fxa-oauth-server/blob/master/docs/clients.md WebPlatform's fork of FxA OAuth Server in ''docs/clients.md''].

An client entry looks like this:

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

To continue with our example, we are connecting to a MediaWiki installation that has the [[WPD:Projects/SSO/MediaWikiExtension]] available. In the case of that particular extension, it expects that we send authenticated users back to '''Special::AccountsHandler/callback'''.


=== 2. Configure client ===

Configuring a client to use our OAuth server can be different depending on how the extension implements OAuth2.

Regardless of the exact configuration lines or code, every OAuth2 clients has similar configuration lines.

Such as:
* Start the process
* Generate an Authorization token

In the case of our implementation, we also added (<tt>fxa_profile</tt>) so that we can read user data from somewhere.

Our MediaWiki extension has similar configuration in its <tt>Settings.php</tt> file:

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

Most of these requests aren’t made through the browser but through a server-side HTTP client. In the MediaWiki extension, we are using Guzzle.

''NOTE'' Even though the calls are aimed at endpoints under SSL, it feels safer to have those requests made outside of the reach of the visitor web browser.


=== 3. Possibility: Detected a session ===

On page load, a non blocking JavaScript module attempts to read from the accounts server to see whether a session is already opened or not. The outline of what’s happening is described in [[#SSO and remembering]].

If no session is detected, the module does nothing.


=== 4. From a page, when you click login ===

The MediaWiki extension detects the click and sends you to '''Special:AccountsHandler/start'''. Its an internal process to generate a redirect to the OAuth2 authentication flow.

The web application generates and sends user to the OAuth authentication endpoint, with some data:
* The client identifier ("<tt>client_id</tt>")
* What the application wants ("<tt>scope</tt>")
* What state it was in ("state"), this is a random key used to store inside a keystore such as memcache so we can retrieve the state data after the authentication process.

'''NOTE''' In Mozilla Firefox Accounts, the <tt>callbackUri</tt> is configured in the server configuration directly. This is considered safer to trust only the configuration file in contrast to common OAuth2 server implementation where they also want the <tt>callbackUri</tt> as part of the first redirect. This is a way to address a security breach in original OAuth2 specification.

Since the OAuth server knows who is the client, it adjusts the title to "Sign in to WebPlatform Test".

[[File:sso_steps_login_dialog.png]]

'''NOTE''' In the screenshot above, you see ''scope=profile''. Since that snapshot, we changed the scope name to  ''session'' because we needed to differentiate web application that will use OAuth to create local sessions from future use cases.

Once the authentication worked the accounts server sends you to the <tt>callbackUri</tt> (e.g. <tt>Special:AccountsHandler/callback</tt> for Media Wiki).


=== 5. Redirected the callback URI ===

From that callback, we get two keys:

* <tt>state</tt>: Is that string we gave in the previous step, we get it back so we can resume where we were before the authentication process. If the state data (e.g. previous page visited) was serialized and sent to Memcache, we can ask it once again and resume.
* <tt>code</tt>: This is a one-time token that we can use to get an OAuth2 Token. In this example, its "SOMETHING_LONG"

The callback URI looks like this:
    <nowiki>http://docs.webplatform.org/test/Special:AccountsHandler/callbackcode=SOMETHING_LONG&state=5a72cd23b1b5feb8</nowiki>

Based on the received data, we can continue with the OAuth2 handshake.


=== 6. Get an Authorization token ===

From the <tt>callbackUri</tt> handler, with the expected data (<tt>state</tt>, <tt>code</tt>) we make a few HTTP calls server to server (i.e. invisible to the web browser).

The call to get the Authorization token contains:

* <tt>client_id</tt>: The identifier we configured in both OAuth server and the client
* <tt>client secret</tt>: The shared secret
* <tt>code</tt>: The one-time code we got when redirected to the <tt>callbackUri</tt>.

The request is similar to this cURL call:

<syntaxHighlight>
curl -XPOST \
    -H 'Content-Type: application/json' \
    'https://oauth.accounts.webplatform.org/v1/token' \
    -d '{"client_id":"7e7e11299d95d789",
         "client_secret":"a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa",
         "code":"SOMETHING_LONG"}'
</syntaxHighlight>

We get in exchange the Authorization token in a response that looks like this:

<syntaxHighlight>
  {"access_token":"6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31",
   "token_type":"bearer",
   "scope":"session"}
</syntaxHighlight>

The <tt>access_token</tt> is what we needed to act on the behalf of the logged in user.

At the time, the only protected service is the profile server, but we might want to protect other components later down the road.

'''NOTE''' An OAuth Authorization token is basically a key to make actions on the behalf of a valid user. In this regard, it is of the utmost importance to have it sent only through SSL, and, ideally, always outside of the reach of the web browser.


=== 7. Reading from the profile server ===

Assuming our web application has a valid Authorization token, we can get the account data we need from the profile server.

Each requests made to an OAuth2 protected API such as the profile server has to be made accompanied with the Authorization token in the HTTP request header.

The call looks like this using cURL:

<syntaxHighlight>
curl -H 'Content-Type: application/json' \
     -H "Authorization: Bearer 6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31" \
     'https://profile.accounts.webplatform.org/v1/session/read'
</syntaxHighlight>

If the profile server accepted our Authorization token, we should get a JSON object looking like this:

<syntaxHighlight>
  {"username": "jdoe",
   "fullName": "John Doe",
   "email": "hi@example.org",
   "uid": "3E09D6DF843341BC921A25423AB83BAF" }
</syntaxHighlight>

We can now start the session in the client web application.

'''NOTE''' Authorization headers is functionally the same as what the web browser does with cookies. In fact, during a browsing session that has cookies, they are sent along with every HTTP requests. And that is, regardless of whether its an image, a CSS file, or a web page. The cookie is therefore a way to tell the application server to tell who the visitor is and potentially change the returned resource.


=== 8. Initialize local web application session ===

''NOTE'' In the case of the <tt>callbackUri</tt> detected a <tt>sessionToken</tt> parameter in its URL instead of OAuth’s <tt>code</tt>, <tt>state</tt>, the web application will then handle local actions from here. To read more about this possibility, refer to [[#SSO and remembering]], at the step [[#4. With a sessionToken, we can read data from the profile server]]

One of the key behavior in a SSO system is that each configured application relies on an authority to provide common user data (e.g. email, username, fullName), but also to confirm if it can start a session locally and overriding its own user validation system.

Regardless of whether we got the data from the profile server with OAuth protected <tt>/v1/session/read</tt> OR <tt>/v1/session/recover?sessionToken=...</tt>, it MUST have the same data for the same user.

<syntaxHighlight>
  {"username": "jdoe",
   "fullName": "John Doe",
   "email": "hi@example.org",
   "uid": "3E09D6DF843341BC921A25423AB83BAF" }
</syntaxHighlight>

The profile server fills the purpose of providing that user data, and the Accounts server to confirm that the request is legitimate.

Since each web application can have different database, we are using this information to find if a user already exists in the local database, or we create one with the default details for the user.

Based on the data received from the profile server, we initialize a session locally.

* Check if it can find a user matching the given username
* Create a new user if not
* Start local session, cookies, etc.

Also, from the state key we had earlier, we can resume where we were by retrieving what was stored originally in Memcache.

In the case of MediaWiki, we currently store the previous page the user visited and would look like this:

    {"return_to":"http://docs.webplatform.org/wiki/WPD:Projects/SSO/Login_Workflows"}

Based on that information, we issue a redirect and the user is back where he was.


----



== SSO and remembering ==

As described in [[#Stories]], the following describes how we can get the same data from [[#Using OAuth2 to start a session]], but without asking for the user to authenticate again.

To illustrate, we are going to show what happens when we:

* Authenticate from a [http://www.w3.org/2014/annotation/experiment/webaudio.html W3C spec] ("B")
* Want to use experiment with Docs features in the [http://docs.webplatform.org/test/css/properties/border "test" wiki at docs.webplatform.org/test/] ("C").

Which, both, are the first using our new Accounts system.

To have the system to not ask the user to authenticate again we needed to find a way to check if a session is opened, and get the user data so I can create a local session from that trusted source.

Most of the following would happen at [[#3. Possibility: Detected a session]] during [[#Using OAuth2 to start a session]] with a non blocking JavaScript module #TODO.



=== SSO and remembering, proposal 1 ===

While the original design of Firefox Accounts OAuth server was to remember if a user previously authenticated, that functionality is not implemented yet.

The issue is known and documented [https://github.com/mozilla/fxa-content-server/issues/1195 in their GitHub issue #1195].

In the eventuality of the Firefox Accounts OAuth server changes its behavior, we will still need a non-blocking JavaScript module to check whether a session is already opened.


=== SSO and remembering, proposal 2 ===

While this implementation proposal is some sort of workaround, it is designed to provide the same data we would get if the issue [[#SSO and remembering, proposal 1]].

In either case, we first need to discover whether a session is already opened using Content Security Policies and Cross Frame communication through a hidden iframe via JavaScript.

'''Story''': A person signed in to work on testing a feature in the SSO enabled [http://docs.mroftalpbew.org/wiki/Main_Page WebPlatform Docs Staging wiki] ("D"). Later in his browsing session, the user wants to add an comment to a [http://www.w3.org/2014/annotation/experiment/webaudio.html W3C spec that supports annotations] ("B"). Without having to enter his credentials more than once.

The workflow in this code proposal should be run before [[#4. From a page, when you click login]].

The following is separated in two parts:
* Detecting a sessino through a non blocking JavaScript detection module
* Creating a local session (by resuming from [[#8. Initialize local web application session]])

==== Code to add ====

The following code will handle the missing behavior we need to enable our feature.

===== 0.1. Event handler to validate a session =====

In our own fork and branch of <tt>fxa-content-server</tt>, in [https://github.com/webplatform/fxa-content-server/blob/webplatform-customizations/app/scripts/views/base.js app/scripts/views/base.js]

<syntaxHighlight>
      // WebPlatform Specific ===============================
      // file: app/scripts/views/base.js
      // line: 40
      // See: http://docs.webplatform.org/wiki/WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering.2C_proposal_2
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

In our own fork and branch of <tt>fxa-content-server</tt>, in [https://github.com/webplatform/fxa-content-server/blob/webplatform-customizations/server/bin/fxa-content-server.js server/bin/fxa-content-server.js]

<syntaxHighlight>
  // WebPlatform Specific ===============================
  // File: server/bin/fxa-content-server.js
  // Line: 62
  // Adjust helmet to accept xss from specific hosts
  // see: https://github.com/evilpacket/helmet
  // Comment, this:
  //app.use(helmet.xframe('deny'));
  // Instead:
  app.use(helmet.csp({"script-src":["'self'", "*.webplatform.org", "*.mroftalpbew.org", "*.fastly.com", "*.w3.org"]}));
  // /WebPlatform Specific ==============================
</syntaxHighlight>

==== 1. Sign in to ("D") ====

In our case, let’s use the [http://docs.mroftalpbew.org/wiki/Main_Page WebPlatform Docs Staging wiki] ("D")

Complete signin in process through the accounts server, and you should get back to the staging wiki —note the word webplatform spelled backwards in the domain name— with a session opened.


==== 2. Go to ("B"), another web app that also uses the accounts server ====

In this example, we will want to add a comment on a [http://www.w3.org/2014/annotation/experiment/webaudio.html W3C spec that supports annotations] ("B")

The following JavaScript MUST happen.

===== 2.1. From B, prepare to handle confirmation =====

This is where we listen to what we get from the accounts server, validate if a session exists, and trigger the calls to the profile server and handle the returned data.

    window.addEventListener("message", function(returned){console.log(returned.data)}, false);

===== 2.2. From B, open a iframe to ("C") =====

For this to work, we have to make sure that the Content server sends appropriate CSP headers on the FxA content server.

    // See 0.2
    app.use(helmet.csp({"script-src":["'self'", "*.webplatform.org", "*.mroftalpbew.org", "*.fastly.com", "*.w3.org"]}));

Create the iframe

    var authChecker=document.createElement('iframe');authChecker.src='https://accounts.webplatform.org/';authChecker.frameworder=0;authChecker.width=0;authChecker.height=0;authChecker.id='authChecker';document.body.appendChild(authChecker);


===== 2.3. From B, Send trigger to ask confirmation from the iframe =====

Since the iframe has reloaded fully the document and would behave the same as if the user went to https://accounts.webplatform.org/ with an opened session, we can ask that iframe document to send us details of the session.

To do so, we are sending a request for confirmation, like this:

    authChecker.contentWindow.postMessage('hi', 'https://accounts.webplatform.org/');


==== 3. From B, handle the response from the iframe ====

Provided a session is already open, we should get something similar to:

    {hasSession: true, sessionToken: "e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f"}

If there is no session, or in case of failure, we would get:

    {hasSession: false, sessionToken: null}

Since the iframe and the communication would had failed from any non trusted source. If we are from a trusted source as described in 2.2, it is safe to assume that we are a legitimate relying party to the SSO system.

This is where the non blocking JavaScript module finish its lifecycle.  Upon detecting an object that has <tt>hasSession: true</tt> AND a 64 character long string for <tt>sessionToken</tt>, it MUST send an Ajax POST to the local web application <tt>callbackUri</tt> with the token.


==== 4. With a sessionToken, we can read data from the profile server ====

The following happens at [[#8. Initialize local web application session]] when we detect a <tt>sessionToken</tt>

This endpoint will be available ONLY through the internal network of WebPlatform and the W3C.

Compared to a call with an OAuth Authorization token, we are going to call a different endpoint that will correlate the data attached to the user session.

The special endpoint, only available through a limited set of IP address answers to <tt>/v1/session/recover?sessionToken=...</tt>.

    curl 'https://profile.accounts.webplatform.org/v1/session/recover?sessionToken=e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f'

''NOTE'' This endpoint is available at the moment but might not be accessible anymore by end of June 2014.


===== 4.1. Under the hood =====

Under the hood, the profile server endpoint at <tt>session/recover</tt> makes database queries similar to:

    SELECT HEX(s.uid) AS uid, a.normalizedEmail AS email, a.username AS username, a.fullName AS fullName FROM sessionTokens AS s, accounts AS a WHERE s.uid = a.uid AND tokenData = unhex('e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f');

The database should either return an empty result, or user data:

    +----------------------------------+----------------+----------+--------------+
    | uid                              | email          | username | fullName     |
    +----------------------------------+----------------+----------+--------------+
    | 3E09D6DF843341BC921A25423AB83BAF | hi@example.org | jdoe     | John Doe     |
    +----------------------------------+----------------+----------+--------------+

==== 5. Returning the data to the server ====

If the web application could get a response from <tt>session/recover</tt>, and finds a result, it returns a JSON object similar to:

<syntaxHighlight>
  {"username": "jdoe",
   "fullName": "John Doe",
   "email": "hi@example.org",
   "uid": "3E09D6DF843341BC921A25423AB83BAF" }
</syntaxHighlight>

That is what we expect to get to successfully resume [[#8. Initialize local web application session]].

In the case of an invalid or expired sessionToken, nothing/an error should be returned.