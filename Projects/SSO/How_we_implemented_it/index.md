= How we implemented SSO =

== Summary ==

The objective of this document is to describe how we implemented a SSO solution for WebPlatform.org. It is meant to give an idea of the various moving parts. If you want to see the high level description, refer to [[WPD:Projects/SSO/Login Workflows]]

The authentication portal is using our own fork of Mozilla Firefox Accounts ("FxA") deployed on WebPlatform.org infrastructure. Details of the adaptations are described in [[WPD:Projects/SSO/Adapt_Firefox_Accounts_for_WebPlatform]].


=== Stories ===

The present document describe how we address a set of user stories but it should be noted that the final result is expected to use the SSO across ALL WebPlatform.org services and participating W3C Specifications.

* As a non authenticated person, I want to edit in the [http://docs.webplatform.org/wiki/css/properties/border a page on docs.webplatform.org/wiki/] ("A").
* As a non authenticated person, I want to add annotations on a participating [http://www.w3.org/2014/annotation/experiment/webaudio.html W3C spec that supports annotations] ("B")
* As a non authenticated person, I want to experiment with Docs features in the [http://docs.webplatform.org/test/css/properties/border WebPlatform Docs "test" wiki] ("C").
* As a non authenticated person, I want to be allowed to edit in the [http://docs.mroftalpbew.org/wiki/Main_Page WebPlatform Docs Staging wiki] ("D") and see if the upcoming deployment will work
* As a non authenticated visitor, I want to start a session and be allowed to perform [A, B, C, D] without authenticating myself more than once


=== Workflows ===

Repeating what was described in [[WPD:Projects/SSO/Login Workflows]], to be detailed in this page.

In order to fulfill the given [[#Stories]], we needed to implement a SSO solution covers the following:
* Get authenticated through a single authority (see [[#Delegating authentication]])
* [[#Read user data]] from an API, 
* Let each configured web applications to detect a session on the authority (see [[#SSO and remembering]])
* handle their local users and session (see [[#Initialize local web application session]]), and
* Detect automatically if there is a session in the accounts server, and start it automatically (see [[#JavaScript shared module: Detect and start automatically a session]])


----


== Delegating authentication ==

This step is meant to address the '''Get authenticated through a single authority''' workflow.

=== 0. Preamble ===

In this implementation we are passing through authentication to get an OAuth2 Bearer authorization token so that we can get data on the behalf of the authenticated user.

The following makes use of the generated Authorization token to read a profile server and read associated user data (i.e. email address, full name, username, etc.) that will be used in all web applications.

''NOTE'' At the moment, the Authorization token is used only once. In future development, we might want to add features and will need to store securely that token to make other actions on the behalf of the user.


=== 1. Configure the OAuth server to accept requests from a client ===

In OAuth terminology, a client is a consumer that is authorized to rely on the OAuth server. A client can be a web application, but its not only limited to that.

In this example, we are going to show how the [http://docs.webplatform.org/test/css/properties/border WebPlatform Docs "test" wiki] ("C") gets data from the various layers.

Client configuration is described in the project documentation available in the  [https://github.com/webplatform/fxa-oauth-server/blob/master/docs/clients.md WebPlatform's fork of FxA OAuth Server in ''docs/clients.md''].

Within FxA OAuth server configuration, a <tt>client: [/* array of clients */]</tt> entry looks like this:

<syntaxHighlight lang="javascript">
{
  "id": "7e7e11299d95d789",
  "secret": "a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa",
  "name": "WebPlatform Test",
  "image_uri": "...",
  "redirectUri":"http://docs.webplatform.org/test/Special:AccountsHandler/callback",
  "whitelisted": true
}
</syntaxHighlight>

* <tt>id</tt>: Is a 8 byte hexadecimal string that you will need to have on the client configuration
* <tt>secret</tt>: Is a 32 byte hexadecimal string that you will also need on the client configuration.
* <tt>redirectUri</tt>: Is where you should send the users to when they successfully authenticated.

To continue with our example, we are connecting to a MediaWiki installation that has the [[WPD:Projects/SSO/MediaWikiExtension]] available. In the case of that particular extension, it expects that we send authenticated users back to <tt>Special:AccountsHandler/callback</tt>.


=== 2. Configure client ===

Configuring a client to use our OAuth server can be different depending on how the extension implements OAuth2.

Regardless of the exact configuration lines or code, every OAuth2 clients has similar configuration lines.

Such as:
* Start the process
* Generate an Authorization token

In the case of our implementation, we also added (<tt>fxa_profile</tt>) so that we can read user data from somewhere.

Our MediaWiki extension has similar configuration in its <tt>Settings.php</tt> file:

<syntaxHighlight lang="php">
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
* <tt>GET https://profile.accounts.webplatform.org/v1/session/read</tt>, with scope '<tt>session</tt>'

Most of these requests aren’t made through the browser but through a server-side HTTP client. In the MediaWiki extension, we are using Guzzle.

''NOTE'' Even though the calls are aimed at endpoints under SSL, it feels safer to have those requests made outside of the reach of the visitor web browser.


=== 3. Possibility: Detected a session ===

On page load, a non blocking [[#JavaScript shared module: Detect and start automatically a session]] attempts to read from the [https://accounts.webplatform.org/ accounts server] to see whether a session is already opened or not. 

The outline of what’s happening is described in [[#SSO and remembering]].

If no session is detected, the module does nothing.


=== 4. From a page, when you click login ===

The MediaWiki extension detects the click and sends you to <tt>Special:AccountsHandler/start</tt>. Its an internal process to generate a redirect to the OAuth2 authentication flow.

The web application generates and sends user to the OAuth authentication endpoint, with some data:
* The client identifier ("<tt>client_id</tt>")
* What the application wants ("<tt>scope</tt>")
* What state it was in ("<tt>state</tt>"), this is a random key used to store inside a key store such as Memcache so we can retrieve the state data after the authentication process.

'''NOTE''' In Mozilla Firefox Accounts, the <tt>callbackUri</tt> is configured in the server configuration directly. This is considered safer to trust only the configuration file in contrast to common OAuth2 server implementation where they also want the <tt>callbackUri</tt> as part of the first redirect. This is a way to address a security breach in original OAuth2 specification.

Since the OAuth server knows who is the client, it adjusts the title to "Sign in to WebPlatform Test".

[[File:sso_steps_login_dialog.png]]

'''NOTE''' In the screenshot above, you see ''scope=profile''. Since that snapshot, we changed the scope name to  ''session'' because we needed to differentiate web application that will use OAuth to create local sessions from future use cases.

Once the authentication worked the [https://accounts.webplatform.org/ accounts server] sends you to the <tt>callbackUri</tt> (e.g. <tt>Special:AccountsHandler/callback</tt> for Media Wiki).


=== 5. Redirected the callback URI ===

From that callback, we get two keys:

* <tt>state</tt>: Is that string we gave in the previous step, we get it back so we can resume where we were before the authentication process. If the state data (e.g. previous page visited) was serialized and sent to Memcache, we can ask it once again and resume.
* <tt>code</tt>: This is a one-time token that we can use to get an OAuth2 Token. In this example, its "SOMETHING_LONG"

The callback URI looks like this:

<code><nowiki>/wiki/Special:AccountsHandler/callback?code=SOMETHING_LONG&state=5a72cd23b1b5feb8</nowiki></code>

Based on the received data, we can continue with the OAuth2 handshake.


=== 6. Get an Authorization token ===

From the <tt>callbackUri</tt> handler, with the expected data (<tt>state</tt>, <tt>code</tt>) we make a few HTTP calls server to server (i.e. invisible to the web browser).

The call to get the Authorization token contains:

* <tt>client_id</tt>: The identifier we configured in both OAuth server and the client
* <tt>client secret</tt>: The shared secret
* <tt>code</tt>: The one-time code we got when redirected to the <tt>callbackUri</tt>.

The request is similar to this cURL call:

<syntaxHighlight lang="bash">
curl -XPOST -H 'Content-Type: application/json' \
     'https://oauth.accounts.webplatform.org/v1/token' \
     -d '{"client_id":"7e7e11299d95d789",
          "client_secret":"a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa",
          "code":"SOMETHING_LONG"}'
</syntaxHighlight>

We get in exchange the Authorization token in a response that looks like this:

<syntaxHighlight lang="javascript">
{"access_token":"6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31",
 "token_type":"bearer",
 "scope":"session"}
</syntaxHighlight>

The <tt>access_token</tt> is what we needed to act on the behalf of the logged in user.

At the time, the only protected service is the profile server, but we might want to protect other components later down the road.

'''NOTE''' An OAuth Authorization token is basically a key to make actions on the behalf of a valid user. In this regard, it is of the utmost importance to have it sent only through SSL, and, ideally, always outside of the reach of the web browser.


=== 7. Finsish off things ===

Continued in [[#Read user data]], and then [[#Initialize local web application session]] workflow.


----


== Read user data ==

This step is meant to address the '''Read user data through an API''' workflow.

Assuming our web application has a valid ''Authorization token'', OR ''session token'', we can get the account data we need from the profile server.

The profile server '''MUST return the same data''' regardless of whether it got an ''Authorization token'' or a ''session token''.

The Profile server has two distinct methods to provide user data. 
* One to ''read'' the user data for the first time, requiring a valid OAuth2 Authorization token
* One to ''recover'' the user data, meaning the server already has a session opened on the [https://accounts.webplatform.org/ accounts server] and we want to use the same data.

To read more about recovering a session, refer to [[#SSO and remembering]] workflow.

The call to the profile server looks like the following cURL calls:

'''With an Authorization token''':
<syntaxHighlight lang="bash">
curl -H 'Content-Type: application/json' \
     -H "Authorization: Bearer 6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31" \
     'https://profile.accounts.webplatform.org/v1/session/read'
</syntaxHighlight>

'''With a session token''':

'''NOTE'''; The <tt>sessionToken</tt> is available from the [https://accounts.webplatform.org/settings Accounts server settings view] only once a user is logged in. To access it, we are using cross-frame communication and read the token from localStorage API.

<syntaxHighlight lang="javascript">
// URI https://accounts.webplatform.org/settings
var obj = JSON.parse(window.localStorage.getItem('__fxa_session')) || {};
console.log(obj); // if there is a session, obj.sessionToken will have what we need
</syntaxHighlight>

Use the <tt>obj.sessionToken</tt> after <tt>Session</tt> in the following cURL:

<syntaxHighlight lang="bash">
curl -v -H 'Content-Type: application/json' \
        -H "Authorization: Session 095dc99de03e99c6d93211aced561c6a28800cdd20fe2ff55ef4626401a04045" \
        'https://profile.accounts.webplatform.org/v1/session/recover'
</syntaxHighlight>


If the profile server accepted either methods, we get a JSON object looking like this:

<syntaxHighlight lang="javascript">
{"username": "jdoe",
 "fullName": "John Doe",
 "email": "hi@example.org",
 "uid": "3E09D6DF843341BC921A25423AB83BAF" }
</syntaxHighlight>

We can now start the session in the client web application.

'''NOTE''' Authorization headers is functionally the same as what the web browser does with cookies. In fact, during a browsing session that has cookies, they are sent along with every HTTP requests. And that is, regardless of whether its an image, a CSS file, or a web page. The cookie is therefore a way to tell the application server to tell who the visitor is and potentially change the returned resource.


----


== Initialize local web application session ==

This step is meant to address the '''handle their local users and session''' workflow and what the backend code MUST implement.

One of the key behavior in a SSO system is that each configured application relies on an authority to provide common user data (e.g. email, username, fullName), but also to confirm if it can start a session locally and overriding its own user validation system.

=== 0. Preamble ===

The following MUST be done in the backend code answering at the what is refered to as "'''callback'''" (e.g. <tt>Special:AccountsHandler/callback</tt>) on each relying parties who wants to use the SSO. 

It handles the following steps:
* Read data from profile server
* Find matching user, and/or create a new one
* Start a session
* Return a status code for the [[#JavaScript shared module: Detect and start automatically a session]] 

This component answers in two different scenarios:
* GET request with two parameters (e.g. <tt>Special:AccountsHandler/callback?code=aaa&state=bbb</tt>), "[[#1.1 Possibility: Completing an OAuth2 handshake]]"
* POST request with <tt>recoveryPayload</tt> data, "[[#1.2 Possibility: Resuming a session confirmed by the accounts server]]".

In both ''Behavior forks'', the returned data from the profile server MUST be in the following format:

<syntaxHighlight lang="javascript">
{"username": "jdoe",
 "fullName": "John Doe",
 "email": "hi@example.org",
 "uid": "3E09D6DF843341BC921A25423AB83BAF" }
</syntaxHighlight>

Since each web application can have different database and ways to refer to a given user, we are using this information to find if a user already exists in the local database, or we create one with the default details for the user.

Based on the data received from the profile server, we initialize a session locally.


=== 1. Behavior forks ===

Here is how the backend code MUST behave in both cases.

The steps are basically the same, but acts differently depending of what initiated the process.

Here are the differences in both cases.

==== 1.1 Possibility: Completing an OAuth2 handshake ====

This section covers what the backend does when it got called during an OAuth2 workflow during [[#Delegating authentication]] and mentionned in [[#5. Redirected the callback URI]].

In this case, we are provided with TWO keys through a <tt>GET</tt> request to our callback (e.g. <tt>Special:AccountsHandler/callback</tt>)

* <tt>code</tt>: The one-time token that is the last step to get an Authorization token
* <tt>state</tt>: A key identifier that we got when we saved away in a key store (e.g. Memcache) the state before signing in.

===== 1.1.1 Get an OAuth2 authorization token =====

With the <tt>code</tt> in hand, we can [[#6. Get an Authorization token]], then ask the profile server the user data.

As described in [[#6. Get an Authorization token]].

===== 1.1.2 Read data from profile server =====

As described in [[#Read user data]] ''With an Authorization token'' (OAuth2).

===== 1.1.3 Find matching user, and/or create a new one =====

This is specific to each web application, for MediaWiki you can refer to [[WPD:Projects/SSO/MediaWikiExtension]].

===== 1.1.4 Start a session =====

This is specific to each web application, for MediaWiki you can refer to [[WPD:Projects/SSO/MediaWikiExtension]].

===== 1.1.5 Resume previous state =====

During previous OAuth2 workflow steps, we saved some data in a key store ("state") and we can use it to send the user where he was in.

In the case of the [[WPD:Projects/SSO/MediaWikiExtension]], we currently store the previous page the user visited and would look like this:

<syntaxHighlight lang="javascript>
{return_to:"http://docs.webplatform.org/wiki/WPD:Projects/SSO/Login_Workflows"}
</syntaxHighlight>

Based on that information, we issue a redirect and the user is back where he was.


==== 1.2 Possibility: Resuming a session confirmed by the accounts server  ====

This section covers what the backend does when we detected a session through the frontend discovery mechanism [[WPD:Projects/SSO/Login Workflows#Starting a session by communicating with accounts server]].

In this case, we are provided with ONE key through a <tt>POST</tt> request to our callback (e.g. <tt>Special:AccountsHandler/callback</tt>)

* <tt>recoveryPayload</tt>: Containing the data used to ask the profile server

'''NOTE''' This step is currently getting directly the <tt>sessionToken</tt> and will eventually changed, see reasons in [[WPD:Projects/SSO/Improvements roadmap#Recovering session data]].

===== 1.2.1 Make a request with the received data =====

As described in [[#SSO and remembering]], in the step [[#4. Read data from the profile server with a recoveryPayload]].

===== 1.2.1 Read data from profile server =====

As described in [[#Read user data]] ''With a session token''.

===== 1.2.2 Find matching user, and/or create a new one =====

This is specific to each web application, for MediaWiki you can refer to [[WPD:Projects/SSO/MediaWikiExtension]].

===== 1.2.3 Start a session =====

This is specific to each web application, for MediaWiki you can refer to [[WPD:Projects/SSO/MediaWikiExtension]].

===== 1.2.4 Return an HTTP response =====

This step is required by the [[#JavaScript shared module: Detect and start automatically a session]] so it knows whether it should reload or not the page and let the user use the current site as an authenticated user.

* <tt>204</tt>: All went fine, reload!
* <tt>4xx</tt>: Stop there, no valid session was found
* <tt>5xx</tt>: Stop there, an unexpected error happened

If the status is not an error (e.g. 4xx, 5xx), we can send an error message in the response body with a <tt>Content-type: text/plain</tt> HTTP header.

----


== SSO and remembering ==

This step is meant to address the '''Let each configured web applications to detect a session on the authority''' workflow.

As described in [[#Stories]], the following describes how we can get the same data from [[#Read user data]], but without asking for the user to authenticate again.

To have the system to not ask the user to authenticate again we needed to find a way to check if a session is opened, and get the user data so I can create a local session from that trusted source.

Most of the following would happen at [[#3. Possibility: Detected a session]] then [[#Read user data]] using a [[#JavaScript shared module: Detect and start automatically a session]] that handles the checks and makes the local web application to [[#Initialize local web application session]] automatically for the user.


=== 0. Preamble ===

This is what’s currently implemented. Ideally it should leverage what’s proposed in the previous section. A high level description is available at [[WPD:Projects/SSO/Login Workflows#Starting a session by communicating with accounts server]]

While this implementation proposal is some sort of workaround, it is designed to provide the same data we would get if the issue [[WPD:Projects/SSO/Improvements roadmap#Leveraging completely OAuth2]].

In either case, we first need to discover whether a session is already opened using Content Security Policies and Cross Frame communication through a hidden iframe via JavaScript.

'''Story''': A person signed in to work on testing a feature in the SSO enabled [http://docs.mroftalpbew.org/wiki/Main_Page WebPlatform Docs Staging wiki] ("D"). Later in his browsing session, the user wants to add an comment to a [http://www.w3.org/2014/annotation/experiment/webaudio.html W3C spec that supports annotations] ("B"). Without having to enter his credentials more than once.

The workflow in this code proposal should be run before [[#4. From a page, when you click login]].

The following is separated in two parts:
* [[#JavaScript shared module: Detect and start automatically a session]]
* [[#Initialize local web application session]]

==== 1. Sign in to ("D") ====

Continuing our scenario, let’s use the [http://docs.mroftalpbew.org/wiki/Main_Page WebPlatform Docs Staging wiki] ("D")

Complete signin in process through the accounts server (the OAuth way), and you should get back to the staging wiki with a session opened.

'''NOTE''': Once you passed this step, you can see on the [https://accounts.webplatform.org/ accounts server] that it no loger prompts you to authenticate.

==== 2. Go to ("B"), another web app that also uses the accounts server ====

Continuing our scenario, we will want to add a comment on a [http://www.w3.org/2014/annotation/experiment/webaudio.html W3C spec that supports annotations] ("B")

The following JavaScript happen.

===== 2.1. From B, prepare to handle confirmation =====

This is where we listen to what we get from the accounts server, validate if a session exists, and trigger the calls to the profile server and handle the returned data.

<syntaxHighlight lang="javascript">
window.addEventListener("message", function(returned){console.log(returned.data)}, false);
</syntaxHighlight>

NOTE: This is handled in file [[#JavaScript shared module: Detect and start automatically a session]]

===== 2.2. From B, open a iframe to ("C") =====

For this to work, we have to make sure that the Content server sends appropriate CSP headers on the FxA content server.

<syntaxHighlight lang="javascript">
    // See 0.2
    app.use(helmet.csp({"script-src":["'self'", "*.webplatform.org", "*.mroftalpbew.org", "*.global.ssl.fastly.net", "*.w3.org"]}));
</syntaxHighlight>

Create the iframe

<syntaxHighlight lang="javascript">
    var authChecker=document.createElement('iframe');authChecker.src='https://accounts.webplatform.org/';authChecker.frameworder=0;authChecker.width=0;authChecker.height=0;authChecker.id='authChecker';document.body.appendChild(authChecker);
</syntaxHighlight>

NOTE: This is handled in file [[#JavaScript shared module: Detect and start automatically a session]] at the 

<syntaxHighlight lang="javascript">
window.sso.init(closure, '/wiki/Special:AccountsHandler/callback');
</syntaxHighlight>

===== 2.3. From B, Send trigger to ask confirmation from the iframe =====

Since the iframe has reloaded fully the document and would behave the same as if the user went to https://accounts.webplatform.org/ with an opened session, we can ask that iframe document to send us details of the session.

To do so, we are sending a request for confirmation, like this:

<syntaxHighlight lang="javascript">
authChecker.contentWindow.postMessage('hi', 'https://accounts.webplatform.org/');
</syntaxHighlight>

NOTE: This is handled in file [[#JavaScript shared module: Detect and start automatically a session]]. The trigger would be lauched from <tt>window.sso.doCheck()</tt> and handles the next steps until the backend comes in.

==== 3. From B, handle the response from the iframe ====

Provided a session is already open, we should get something similar to:

<syntaxHighlight lang="javascript">
{hasSession: true,
 recoveryPayload: "e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f"}
</syntaxHighlight>

If there is no session, or in case of failure, we would get:

<syntaxHighlight lang="javascript">
{hasSession: false,
 recoveryPayload: null}
</syntaxHighlight>

Since the iframe and the communication would had failed from any non trusted source. If we are from a trusted source as described in 2.2, it is safe to assume that we are a legitimate relying party to the SSO system.

This is where the non blocking [[#JavaScript shared module: Detect and start automatically a session]] finish its lifecycle.  Upon detecting an object that has <tt>hasSession: true</tt> AND a 64 character long string for <tt>sessionToken</tt>, it MUST send an Ajax POST to the local web application <tt>callbackUri</tt> with the token.

NOTE: This is know to bring a problem. The isussue is that if we use an unaltered sessionToken as the sole proof, anybody could know this and hijack a session on the relying party. This needs to be improved.

==== 4. Read data from the profile server with a recoveryPayload ====

The following happens at [[#Initialize local web application session]].

This endpoint will be available ONLY through the internal network of WebPlatform and the W3C.

Compared to a call with an OAuth Authorization token, we are going to call a different endpoint that will correlate the data attached to the user session.

The special endpoint, only available through a limited set of IP address answers to <tt>/v1/session/recover</tt> and requires an "Authorization" header similar to OAuth, but with a Session token instead.

<syntaxHighlight lang="bash">
curl -v -H 'Content-Type: application/json' \
        -H "Authorization: Session e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f" \
        'https://profile.accounts.webplatform.org/v1/session/recover'
</syntaxHighlight>

''NOTE'' This endpoint is available at the moment but might not be accessible anymore by end of June 2014.

Here are the HTTP Response body the endpoint would return:
* 200 OK, with JSON object containing data when session exist (shown above)
* 410 GONE, with error JSON object, when session doesn’t exist
* 401 UNAUTHORIZED, with error JSON object, when request is malformed

===== 4.1. Under the hood =====

Under the hood, the profile server endpoint at <tt>GET /v1/session/recover</tt> makes database queries similar to:

<syntaxHighlight lang="mysql">
SELECT 
  HEX(s.uid) AS uid,
  a.normalizedEmail AS email, 
  a.username AS username,
  a.fullName AS fullName 
FROM 
  sessionTokens AS s,
  accounts AS a 
WHERE 
  s.uid = a.uid 
AND
  tokenData = unhex('e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f');
</syntaxHighlight>

The database should either return an empty result, or user data:

    +----------------------------------+----------------+----------+--------------+
    | uid                              | email          | username | fullName     |
    +----------------------------------+----------------+----------+--------------+
    | 3E09D6DF843341BC921A25423AB83BAF | hi@example.org | jdoe     | John Doe     |
    +----------------------------------+----------------+----------+--------------+

==== 5. Returning the data to the server ====

If the web application could get a response from <tt>session/recover</tt>, and finds a result, it returns a JSON object:

<syntaxHighlight lang="javascript">
  {"username": "jdoe",
   "fullName": "John Doe",
   "email": "hi@example.org",
   "uid": "3E09D6DF843341BC921A25423AB83BAF" }
</syntaxHighlight>

In the case of an invalid or expired <tt>sessionToken</tt>, an error should be returned. See possible errors at [[#4. Read data from the profile server with a recoveryPayload]]

The rest MUST comply to what’s described in [[#Initialize local web application session]].

----

== JavaScript shared module: Detect and start automatically a session ==

This step is meant to address the '''Detect automatically if there is a session in the accounts server, and start it automatically''' workflow.

It describes the behavior of a non blocking JavaScript module meant to detect and start automatically a session for the user.

Client code is available in [https://gist.github.com/WebPlatformDocs/fe3149c60d6ed95c7e16 JavaScript SsoHandler class in this gist]


=== 1. Event handler to validate a session ===

'''NOTE''': This event handler is about answering what’s triggered bye the module and is installed in the accounts server code.

In our own fork and branch of <tt>fxa-content-server</tt>, in [https://github.com/webplatform/fxa-content-server/blob/webplatform-customizations/app/scripts/views/base.js app/scripts/views/base.js]

<syntaxHighlight lang="javascript">
      // WebPlatform Specific ===============================
      // file: app/scripts/views/base.js
      // line: 40
      // See: http://docs.webplatform.org/wiki/WPD:Projects/SSO/How_we_implemented_it#JavaScript_shared_module:_Detect_and_start_automatically_a_session
      var fxaC = this.fxaClient;
      function readAndReplyHasSession( e ) {
        var b = window.localStorage.getItem('__fxa_session');
        var sessionData = JSON.parse(b);

        fxaC.isSignedIn(sessionData.sessionToken)
            .done(
              function( promised ){
                // Will eventually change, as decribed in 
                //   http://docs.webplatform.org/wiki/WPD:Projects/SSO/Improvements_roadmap#Recovering_session_data
                e.source.postMessage({hasSession: promised, recoveryPayload: sessionData.sessionToken || null}, e.origin);
              }
            );
      }
      window.addEventListener("message", readAndReplyHasSession, false);
      // /WebPlatform Specific ==============================
</syntaxHighlight>

=== 2. And adjust the CSP policies ===

'''NOTE''': The Content Security Policy changes here is about letting the module to communicate with the accounts server.

In our own fork and branch of <tt>fxa-content-server</tt>, in [https://github.com/webplatform/fxa-content-server/blob/webplatform-customizations/server/bin/fxa-content-server.js server/bin/fxa-content-server.js]

<syntaxHighlight lang="javascript">
  // WebPlatform Specific ===============================
  // File: server/bin/fxa-content-server.js
  // Line: 62
  // Adjust helmet to accept xss from specific hosts
  // see: https://github.com/evilpacket/helmet
  // Comment, this:
  //app.use(helmet.xframe('deny'));
  // Instead:
  app.use(helmet.csp({"script-src":["'self'", "*.webplatform.org", "*.mroftalpbew.org", "*.global.ssl.fastly.net", "*.w3.org"]}));
  // /WebPlatform Specific ==============================
</syntaxHighlight>

=== 3. JavaScript client to handle automatic sign in ===

This section describes what the module actually does.

* Make sure it doesn't try to do things if local web app already has a session
* Provide a way to tell whether it already has a session opened
* Make sure it works without any external library; to be deployed on all SSO relying parties
* Handle creation of iframe and the <tt>postMessage()</tt>
* Handle reply from cross-frame request
* Cross-frame response, validate returned values has keys: <tt>[hasSession, sessionToken]</tt>
* Make async call to local web application callback through POST
* If return response of local callback is successful, reload page

It exposes two methods to the <tt>window.sso</tt> object:

* <tt>window.sso.init(hasSessionClosure, localCallbackEndpoint);</tt> To initialize (see below)
* <tt>window.sso.doCheck()</tt>, to bootstrap the process (should be done once the iframe is loaded).

<syntaxHighlight lang="javascript">
    window.sso.init( 
      function () { 
        /* 
           Provide a closure that 
           will tell the JavaScript 
           handler whether the current 
           visitor has a session or 
           not.

           MUST RETURN a bool
 
           false === no session, please start the checks
         */ 
        return false;
      }, 
      '/wiki/Special:AccountsHandler/callback'
    );
</syntaxHighlight>

Once the iframe is loaded:

<syntaxHighlight lang="javascript">
window.sso.doCheck();
</syntaxHighlight>

'''NOTE''': If we had a session, the communication triggered at <tt>window.sso.doCheck();</tt>, would had provided us the required data to start automatically and resume at [[#Initialize local web application session]].