---
title: How we implemented SSO
uri: 'WPD:Projects/SSO/How we implemented it'

---
The objective of this document is to describe how we implemented a SSO solution for WebPlatform.org. It is meant to give an idea of the various moving parts.

If you want to see the high level description, refer to [WPD:Projects/SSO/Login Workflows](/WPD:Projects/SSO/Login_Workflows) or if you want a shorter version, go to [WPD:Projects/SSO/OAuth2\_handshake\_process\_in\_a\_few\_cURL\_calls](/WPD:Projects/SSO/OAuth2_handshake_process_in_a_few_cURL_calls).

The authentication portal is using our own fork of Mozilla Firefox Accounts ("FxA") deployed on WebPlatform.org infrastructure. Details of the adaptations are described in [WPD:Projects/SSO/Adapt\_Firefox\_Accounts\_for\_WebPlatform](/WPD:Projects/SSO/Adapt_Firefox_Accounts_for_WebPlatform).

### <span>Stories</span>

The present document describe how we address a set of user stories but it should be noted that the final result is expected to use the SSO across ALL WebPlatform.org services and participating W3C Specifications.

-   As a non authenticated person, I want to edit in the [a page on docs.webplatform.org/wiki/](http://docs.webplatform.org/wiki/css/properties/border) ("A").
-   As a non authenticated person, I want to add annotations on a participating [W3C spec that supports annotations](http://www.w3.org/2014/annotation/experiment/webaudio.html) ("B")
-   As a non authenticated person, I want to experiment with Docs features in the [WebPlatform Docs "test" wiki](http://docs.webplatform.org/test/css/properties/border) ("C").
-   As a non authenticated person, I want to be allowed to edit in the [WebPlatform Docs Staging wiki](http://docs.mroftalpbew.org/wiki/Main_Page) ("D") and see if the upcoming deployment will work
-   As a non authenticated visitor, I want to start a session and be allowed to perform [A, B, C, D] without authenticating myself more than once

### <span>Workflows</span>

Repeating what was described in [WPD:Projects/SSO/Login Workflows](/WPD:Projects/SSO/Login_Workflows), to be detailed in this page.

In order to fulfill the given [\#Stories](#Stories), we needed to implement a SSO solution covers the following:

-   Get authenticated through a single authority (see [\#Delegating authentication](#Delegating_authentication))
-   [\#Read user data](#Read_user_data) from an API,
-   Let each configured web applications to detect a session on the authority (see [\#SSO and remembering](#SSO_and_remembering))
-   handle their local users and session (see [\#Initialize local web application session](#Initialize_local_web_application_session)), and
-   Detect automatically if there is a session in the accounts server, and start it automatically (see [\#JavaScript shared module: Detect and start automatically a session](#JavaScript_shared_module:_Detect_and_start_automatically_a_session))

* * * * *

## <span>Delegating authentication</span>

This step is meant to address the **Get authenticated through a single authority** workflow.

### <span>0. Preamble</span>

In this implementation we are passing through authentication to get an OAuth2 Bearer authorization token so that we can get data on the behalf of the authenticated user.

The following makes use of the generated Authorization token to read a profile server and read associated user data (i.e. email address, full name, username, etc.) that will be used in all web applications.

*NOTE* At the moment, the Authorization token is used only once. In future development, we might want to add features and will need to store securely that token to make other actions on the behalf of the user.

### <span>1. Configure the OAuth server to accept requests from a client</span>

In OAuth terminology, a client is a consumer that is authorized to rely on the OAuth server. A client can be a web application, but its not only limited to that.

In this example, we are going to show how the [WebPlatform Docs "test" wiki](http://docs.webplatform.org/test/css/properties/border) ("C") gets data from the various layers.

Client configuration is described in the project documentation available in the [WebPlatform's fork of FxA OAuth Server in *docs/clients.md*](https://github.com/webplatform/fxa-oauth-server/blob/master/docs/clients.md).

Within FxA OAuth server configuration, a `client: [/* array of clients */]` entry looks like this:

``` js
{
  "id": "7e7e11299d95d789",
  "secret": "a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa",
  "name": "WebPlatform Test",
  "image_uri": "...",
  "redirectUri":"http://docs.webplatform.org/test/Special:AccountsHandler/callback",
  "whitelisted": true
}
```

-   `id`: Is a 8 byte hexadecimal string that you will need to have on the client configuration
-   `secret`: Is a 32 byte hexadecimal string that you will also need on the client configuration.
-   `redirectUri`: Is where you should send the users to when they successfully authenticated.

To continue with our example, we are connecting to a MediaWiki installation that has the [WPD:Projects/SSO/MediaWikiExtension](/WPD:Projects/SSO/MediaWikiExtension) available. In the case of that particular extension, it expects that we send authenticated users back to `Special:AccountsHandler/callback`.

### <span>2. Configure client</span>

Configuring a client to use our OAuth server can be different depending on how the extension implements OAuth2.

Regardless of the exact configuration lines or code, every OAuth2 clients has similar configuration lines.

Such as:

-   Start the process
-   Generate an Authorization token

In the case of our implementation, we also added (`fxa_profile`) so that we can read user data from somewhere.

Our MediaWiki extension has similar configuration in its `Settings.php` file:

```
require_once( "$IP/extensions/WebPlatformAuth/WebPlatformAuth.php" );
$wgWebPlatformAuth['client']['id']             = '7e7e11299d95d789';
$wgWebPlatformAuth['client']['secret']         = 'a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa';
$wgWebPlatformAuth['endpoints']['fxa_oauth']   = 'https://oauth.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['endpoints']['fxa_profile'] = 'https://profile.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['methods']['authorize']     = 'authorization';
$wgWebPlatformAuth['methods']['token']         = 'token';
```

 While configuration can be different depending on the client extension, a few endpoints are required to be used in our installation.

-   `GET https://oauth.accounts.webplatform.org/v1/authorization`
-   `POST https://oauth.accounts.webplatform.org/v1/authorization`
-   `POST https://oauth.accounts.webplatform.org/v1/token`
-   `GET https://profile.accounts.webplatform.org/v1/session/read`, with scope '`session`'

Most of these requests aren’t made through the browser but through a server-side HTTP client. In the MediaWiki extension, we are using Guzzle.

*NOTE* Even though the calls are aimed at endpoints under SSL, it feels safer to have those requests made outside of the reach of the visitor web browser.

### <span>3. Possibility: Detected a session</span>

On page load, a non blocking [\#JavaScript shared module: Detect and start automatically a session](#JavaScript_shared_module:_Detect_and_start_automatically_a_session) attempts to read from the [accounts server](https://accounts.webplatform.org/) to see whether a session is already opened or not.

The outline of what’s happening is described in [\#SSO and remembering](#SSO_and_remembering).

If no session is detected, the module does nothing.

### <span>4. From a page, when you click login</span>

The MediaWiki extension detects the click and sends you to `Special:AccountsHandler/start`. Its an internal process to generate a redirect to the OAuth2 authentication flow.

The web application generates and sends user to the OAuth authentication endpoint, with some data:

-   The client identifier ("`client_id`")
-   What the application wants ("`scope`")
-   What state it was in ("`state`"), this is a random key used to store inside a key store such as Memcache so we can retrieve the state data after the authentication process.

**NOTE** In Mozilla Firefox Accounts, the `callbackUri` is configured in the server configuration directly. This is considered safer to trust only the configuration file in contrast to common OAuth2 server implementation where they also want the `callbackUri` as part of the first redirect. This is a way to address a security breach in original OAuth2 specification.

Since the OAuth server knows who is the client, it adjusts the title to "Sign in to WebPlatform Test".

![sso steps login dialog.png](/WPD/assets/public/3/31/sso_steps_login_dialog.png)

**NOTE** In the screenshot above, you see *scope=profile*. Since that snapshot, we changed the scope name to *session* because we needed to differentiate web application that will use OAuth to create local sessions from future use cases.

Once the authentication worked the [accounts server](https://accounts.webplatform.org/) sends you to the `callbackUri` (e.g. `Special:AccountsHandler/callback` for Media Wiki).

### <span>5. Redirected the callback URI</span>

From that callback, we get two keys:

-   `state`: Is that string we gave in the previous step, we get it back so we can resume where we were before the authentication process. If the state data (e.g. previous page visited) was serialized and sent to Memcache, we can ask it once again and resume.
-   `code`: This is a one-time token that we can use to get an OAuth2 Token. In this example, its "SOMETHING\_LONG"

The callback URI looks like this:

`/wiki/Special:AccountsHandler/callback?code=SOMETHING_LONG&state=5a72cd23b1b5feb8`

Based on the received data, we can continue with the OAuth2 handshake.

### <span>6. Get an Authorization token</span>

From the `callbackUri` handler, with the expected data (`state`, `code`) we make a few HTTP calls server to server (i.e. invisible to the web browser).

The call to get the Authorization token contains:

-   `client_id`: The identifier we configured in both OAuth server and the client
-   `client secret`: The shared secret
-   `code`: The one-time code we got when redirected to the `callbackUri`.

The request is similar to this cURL call:

```
curl -XPOST -H 'Content-Type: application/json' \
     'https://oauth.accounts.webplatform.org/v1/token' \
     -d '{"client_id":"7e7e11299d95d789",
          "client_secret":"a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa",
          "code":"SOMETHING_LONG"}'
```

 We get in exchange the Authorization token in a response that looks like this:

``` js
{"access_token":"6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31",
 "token_type":"bearer",
 "scope":"session"}
```

 The `access_token` is what we needed to act on the behalf of the logged in user.

At the time, the only protected service is the profile server, but we might want to protect other components later down the road.

**NOTE** An OAuth Authorization token is basically a key to make actions on the behalf of a valid user. In this regard, it is of the utmost importance to have it sent only through SSL, and, ideally, always outside of the reach of the web browser.

### <span>7. Finsish off things</span>

Continued in [\#Read user data](#Read_user_data), and then [\#Initialize local web application session](#Initialize_local_web_application_session) workflow.

* * * * *

## <span>Read user data</span>

This step is meant to address the **Read user data through an API** workflow.

Assuming our web application has a valid *Authorization token*, OR *session token*, we can get the account data we need from the profile server.

The profile server **MUST return the same data** regardless of whether it got an *Authorization token* or a *session token*.

The Profile server has two distinct methods to provide user data.

-   One to *read* the user data for the first time, requiring a valid OAuth2 Authorization token
-   One to *recover* the user data, meaning the server already has a session opened on the [accounts server](https://accounts.webplatform.org/) and we want to use the same data.

To read more about recovering a session, refer to [\#SSO and remembering](#SSO_and_remembering) workflow.

The call to the profile server looks like the following cURL calls:

**With an Authorization token**:

```
curl -H 'Content-Type: application/json' \
     -H "Authorization: Bearer 6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31" \
     'https://profile.accounts.webplatform.org/v1/session/read'
```

**With a session token**:

**NOTE**; The `sessionToken` is available from the [Accounts server settings view](https://accounts.webplatform.org/settings) only once a user is logged in. To access it, we are using cross-frame communication and read the token from localStorage API.

``` js
// URI https://accounts.webplatform.org/settings
var obj = JSON.parse(window.localStorage.getItem('__fxa_session')) || {};
console.log(obj); // if there is a session, obj.sessionToken will have what we need
```

 Use the `obj.sessionToken` after `Session` in the following cURL:

```
curl -v -H 'Content-Type: application/json' \
        -H "Authorization: Session 095dc99de03e99c6d93211aced561c6a28800cdd20fe2ff55ef4626401a04045" \
        'https://profile.accounts.webplatform.org/v1/session/recover'
```

If the profile server accepted either methods, we get a JSON object looking like this:

``` js
{"username": "jdoe",
 "fullName": "John Doe",
 "email": "hi@example.org",
 "uid": "3E09D6DF843341BC921A25423AB83BAF" }
```

 We can now start the session in the client web application.

**NOTE** Authorization headers is functionally the same as what the web browser does with cookies. In fact, during a browsing session that has cookies, they are sent along with every HTTP requests. And that is, regardless of whether its an image, a CSS file, or a web page. The cookie is therefore a way to tell the application server to tell who the visitor is and potentially change the returned resource.

* * * * *

## <span>Initialize local web application session</span>

This step is meant to address the **handle their local users and session** workflow and what the backend code MUST implement.

One of the key behavior in a SSO system is that each configured application relies on an authority to provide common user data (e.g. email, username, fullName), but also to confirm if it can start a session locally and overriding its own user validation system.

### <span>0. Preamble</span>

The following MUST be done in the backend code answering at the what is refered to as "**callback**" (e.g. `Special:AccountsHandler/callback`) on each relying parties who wants to use the SSO.

It handles the following steps:

-   Read data from profile server
-   Find matching user, and/or create a new one
-   Start a session
-   Return a status code for the [\#JavaScript shared module: Detect and start automatically a session](#JavaScript_shared_module:_Detect_and_start_automatically_a_session)

This component answers in two different scenarios:

-   GET request with two parameters (e.g. `Special:AccountsHandler/callback?code=aaa&state=bbb`), "[\#1.1 Possibility: Completing an OAuth2 handshake](#1.1_Possibility:_Completing_an_OAuth2_handshake)"
-   POST request with `recoveryPayload` data, "[\#1.2 Possibility: Resuming a session confirmed by the accounts server](#1.2_Possibility:_Resuming_a_session_confirmed_by_the_accounts_server)".

In both *Behavior forks*, the returned data from the profile server MUST be in the following format:

``` js
{"username": "jdoe",
 "fullName": "John Doe",
 "email": "hi@example.org",
 "uid": "3E09D6DF843341BC921A25423AB83BAF" }
```

 Since each web application can have different database and ways to refer to a given user, we are using this information to find if a user already exists in the local database, or we create one with the default details for the user.

Based on the data received from the profile server, we initialize a session locally.

### <span>1. Behavior forks</span>

Here is how the backend code MUST behave in both cases.

The steps are basically the same, but acts differently depending of what initiated the process.

Here are the differences in both cases.

#### <span>1.1 Possibility: Completing an OAuth2 handshake</span>

This section covers what the backend does when it got called during an OAuth2 workflow during [\#Delegating authentication](#Delegating_authentication) and mentionned in [\#5. Redirected the callback URI](#5._Redirected_the_callback_URI).

In this case, we are provided with TWO keys through a `GET` request to our callback (e.g. `Special:AccountsHandler/callback`)

-   `code`: The one-time token that is the last step to get an Authorization token
-   `state`: A key identifier that we got when we saved away in a key store (e.g. Memcache) the state before signing in.

##### <span>1.1.1 Get an OAuth2 authorization token</span>

With the `code` in hand, we can [\#6. Get an Authorization token](#6._Get_an_Authorization_token), then ask the profile server the user data.

As described in [\#6. Get an Authorization token](#6._Get_an_Authorization_token).

##### <span>1.1.2 Read data from profile server</span>

As described in [\#Read user data](#Read_user_data) *With an Authorization token* (OAuth2).

##### <span>1.1.3 Find matching user, and/or create a new one</span>

This is specific to each web application, for MediaWiki you can refer to [WPD:Projects/SSO/MediaWikiExtension](/WPD:Projects/SSO/MediaWikiExtension).

##### <span>1.1.4 Start a session</span>

This is specific to each web application, for MediaWiki you can refer to [WPD:Projects/SSO/MediaWikiExtension](/WPD:Projects/SSO/MediaWikiExtension).

##### <span>1.1.5 Resume previous state</span>

During previous OAuth2 workflow steps, we saved some data in a key store ("state") and we can use it to send the user where he was in.

In the case of the [WPD:Projects/SSO/MediaWikiExtension](/WPD:Projects/SSO/MediaWikiExtension), we currently store the previous page the user visited and would look like this:

``` html
{return_to:"http://docs.webplatform.org/wiki/WPD:Projects/SSO/Login_Workflows"}
```

 Based on that information, we issue a redirect and the user is back where he was.

#### <span>1.2 Possibility: Resuming a session confirmed by the accounts server</span>

This section covers what the backend does when we detected a session through the frontend discovery mechanism [WPD:Projects/SSO/Login Workflows\#Starting a session by communicating with accounts server](/WPD:Projects/SSO/Login_Workflows#Starting_a_session_by_communicating_with_accounts_server).

In this case, we are provided with ONE key through a `POST` request to our callback (e.g. `Special:AccountsHandler/callback`)

-   `recoveryPayload`: Containing the data used to ask the profile server

**NOTE** This step is currently getting directly the `sessionToken` and will eventually changed, see reasons in [WPD:Projects/SSO/Improvements roadmap\#Recovering session data](/WPD:Projects/SSO/Improvements_roadmap#Recovering_session_data).

##### <span>1.2.1 Make a request with the received data</span>

As described in [\#SSO and remembering](#SSO_and_remembering), in the step [\#4. Read data from the profile server with a recoveryPayload](#4._Read_data_from_the_profile_server_with_a_recoveryPayload).

##### <span>1.2.1 Read data from profile server</span>

As described in [\#Read user data](#Read_user_data) *With a session token*.

##### <span>1.2.2 Find matching user, and/or create a new one</span>

This is specific to each web application, for MediaWiki you can refer to [WPD:Projects/SSO/MediaWikiExtension](/WPD:Projects/SSO/MediaWikiExtension).

##### <span>1.2.3 Start a session</span>

This is specific to each web application, for MediaWiki you can refer to [WPD:Projects/SSO/MediaWikiExtension](/WPD:Projects/SSO/MediaWikiExtension).

##### <span>1.2.4 Return an HTTP response</span>

This step is required by the [\#JavaScript shared module: Detect and start automatically a session](#JavaScript_shared_module:_Detect_and_start_automatically_a_session) so it knows whether it should reload or not the page and let the user use the current site as an authenticated user.

-   `204`: All went fine, reload!
-   `4xx`: Stop there, no valid session was found
-   `5xx`: Stop there, an unexpected error happened

If the status is not an error (e.g. 4xx, 5xx), we can send an error message in the response body with a `Content-type: text/plain` HTTP header.

* * * * *

## <span>SSO and remembering</span>

This step is meant to address the **Let each configured web applications to detect a session on the authority** workflow.

As described in [\#Stories](#Stories), the following describes how we can get the same data from [\#Read user data](#Read_user_data), but without asking for the user to authenticate again.

To have the system to not ask the user to authenticate again we needed to find a way to check if a session is opened, and get the user data so I can create a local session from that trusted source.

Most of the following would happen at [\#3. Possibility: Detected a session](#3._Possibility:_Detected_a_session) then [\#Read user data](#Read_user_data) using a [\#JavaScript shared module: Detect and start automatically a session](#JavaScript_shared_module:_Detect_and_start_automatically_a_session) that handles the checks and makes the local web application to [\#Initialize local web application session](#Initialize_local_web_application_session) automatically for the user.

### <span>0. Preamble</span>

This is what’s currently implemented. Ideally it should leverage what’s proposed in the previous section. A high level description is available at [WPD:Projects/SSO/Login Workflows\#Starting a session by communicating with accounts server](/WPD:Projects/SSO/Login_Workflows#Starting_a_session_by_communicating_with_accounts_server)

While this implementation proposal is some sort of workaround, it is designed to provide the same data we would get if the issue [WPD:Projects/SSO/Improvements roadmap\#Leveraging completely OAuth2](/WPD:Projects/SSO/Improvements_roadmap#Leveraging_completely_OAuth2).

In either case, we first need to discover whether a session is already opened using Content Security Policies and Cross Frame communication through a hidden iframe via JavaScript.

**Story**: A person signed in to work on testing a feature in the SSO enabled [WebPlatform Docs Staging wiki](http://docs.mroftalpbew.org/wiki/Main_Page) ("D"). Later in his browsing session, the user wants to add an comment to a [W3C spec that supports annotations](http://www.w3.org/2014/annotation/experiment/webaudio.html) ("B"). Without having to enter his credentials more than once.

The workflow in this code proposal should be run before [\#4. From a page, when you click login](#4._From_a_page.2C_when_you_click_login).

The following is separated in two parts:

-   [\#JavaScript shared module: Detect and start automatically a session](#JavaScript_shared_module:_Detect_and_start_automatically_a_session)
-   [\#Initialize local web application session](#Initialize_local_web_application_session)

#### <span>1. Sign in to ("D")</span>

Continuing our scenario, let’s use the [WebPlatform Docs Staging wiki](http://docs.mroftalpbew.org/wiki/Main_Page) ("D")

Complete signin in process through the accounts server (the OAuth way), and you should get back to the staging wiki with a session opened.

**NOTE**: Once you passed this step, you can see on the [accounts server](https://accounts.webplatform.org/) that it no loger prompts you to authenticate.

#### <span>2. Go to ("B"), another web app that also uses the accounts server</span>

Continuing our scenario, we will want to add a comment on a [W3C spec that supports annotations](http://www.w3.org/2014/annotation/experiment/webaudio.html) ("B")

The following JavaScript happen.

##### <span>2.1. From B, prepare to handle confirmation</span>

This is where we listen to what we get from the accounts server, validate if a session exists, and trigger the calls to the profile server and handle the returned data.

``` js
window.addEventListener("message", function(returned){console.log(returned.data)}, false);
```

 NOTE: This is handled in file [\#JavaScript shared module: Detect and start automatically a session](#JavaScript_shared_module:_Detect_and_start_automatically_a_session)

##### <span>2.2. From B, open a iframe to ("C")</span>

For this to work, we have to make sure that the Content server sends appropriate CSP headers on the FxA content server.

``` js
    // See 0.2
    app.use(helmet.csp({"script-src":["'self'", "*.webplatform.org", "*.mroftalpbew.org", "*.global.ssl.fastly.net", "*.w3.org"]}));
```

 Create the iframe

``` js
    var authChecker=document.createElement('iframe');authChecker.src='https://accounts.webplatform.org/';authChecker.frameworder=0;authChecker.width=0;authChecker.height=0;authChecker.id='authChecker';document.body.appendChild(authChecker);
```

 NOTE: This is handled in file [\#JavaScript shared module: Detect and start automatically a session](#JavaScript_shared_module:_Detect_and_start_automatically_a_session) at the

``` js
window.sso.init(closure, '/wiki/Special:AccountsHandler/callback');
```

##### <span>2.3. From B, Send trigger to ask confirmation from the iframe</span>

Since the iframe has reloaded fully the document and would behave the same as if the user went to <https://accounts.webplatform.org/> with an opened session, we can ask that iframe document to send us details of the session.

To do so, we are sending a request for confirmation, like this:

``` js
authChecker.contentWindow.postMessage('hi', 'https://accounts.webplatform.org/');
```

 NOTE: This is handled in file [\#JavaScript shared module: Detect and start automatically a session](#JavaScript_shared_module:_Detect_and_start_automatically_a_session). The trigger would be lauched from `window.sso.doCheck()` and handles the next steps until the backend comes in.

#### <span>3. From B, handle the response from the iframe</span>

Provided a session is already open, we should get something similar to:

``` js
{hasSession: true,
 recoveryPayload: "e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f"}
```

 If there is no session, or in case of failure, we would get:

``` js
{hasSession: false,
 recoveryPayload: null}
```

 Since the iframe and the communication would had failed from any non trusted source. If we are from a trusted source as described in 2.2, it is safe to assume that we are a legitimate relying party to the SSO system.

This is where the non blocking [\#JavaScript shared module: Detect and start automatically a session](#JavaScript_shared_module:_Detect_and_start_automatically_a_session) finish its lifecycle. Upon detecting an object that has `hasSession: true` AND a 64 character long string for `sessionToken`, it MUST send an Ajax POST to the local web application `callbackUri` with the token.

NOTE: This is know to bring a problem. The isussue is that if we use an unaltered sessionToken as the sole proof, anybody could know this and hijack a session on the relying party. This needs to be improved.

#### <span>4. Read data from the profile server with a recoveryPayload</span>

The following happens at [\#Initialize local web application session](#Initialize_local_web_application_session).

This endpoint will be available ONLY through the internal network of WebPlatform and the W3C.

Compared to a call with an OAuth Authorization token, we are going to call a different endpoint that will correlate the data attached to the user session.

The special endpoint, only available through a limited set of IP address answers to `/v1/session/recover` and requires an "Authorization" header similar to OAuth, but with a Session token instead.

```
curl -v -H 'Content-Type: application/json' \
        -H "Authorization: Session e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f" \
        'https://profile.accounts.webplatform.org/v1/session/recover'
```

*NOTE* This endpoint is available at the moment but might not be accessible anymore by end of June 2014.

Here are the HTTP Response body the endpoint would return:

-   200 OK, with JSON object containing data when session exist (shown above)
-   410 GONE, with error JSON object, when session doesn’t exist
-   401 UNAUTHORIZED, with error JSON object, when request is malformed

##### <span>4.1. Under the hood</span>

Under the hood, the profile server endpoint at `GET /v1/session/recover` makes database queries similar to:

```
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
```

 The database should either return an empty result, or user data:

       +----------------------------------+----------------+----------+--------------+
       | uid                              | email          | username | fullName     |
       +----------------------------------+----------------+----------+--------------+
       | 3E09D6DF843341BC921A25423AB83BAF | hi@example.org | jdoe     | John Doe     |
       +----------------------------------+----------------+----------+--------------+

#### <span>5. Returning the data to the server</span>

If the web application could get a response from `session/recover`, and finds a result, it returns a JSON object:

``` js
  {"username": "jdoe",
   "fullName": "John Doe",
   "email": "hi@example.org",
   "uid": "3E09D6DF843341BC921A25423AB83BAF" }
```

 In the case of an invalid or expired `sessionToken`, an error should be returned. See possible errors at [\#4. Read data from the profile server with a recoveryPayload](#4._Read_data_from_the_profile_server_with_a_recoveryPayload)

The rest MUST comply to what’s described in [\#Initialize local web application session](#Initialize_local_web_application_session).

* * * * *

## <span>JavaScript shared module: Detect and start automatically a session</span>

This step is meant to address the **Detect automatically if there is a session in the accounts server, and start it automatically** workflow.

It describes the behavior of a non blocking JavaScript module meant to detect and start automatically a session for the user.

Client code is available in [JavaScript SsoHandler class in this gist](https://gist.github.com/WebPlatformDocs/fe3149c60d6ed95c7e16)

### <span>1. Event handler to validate a session</span>

**NOTE**: This event handler is about answering what’s triggered bye the module and is installed in the accounts server code.

In our own fork and branch of `fxa-content-server`, in [app/scripts/views/base.js](https://github.com/webplatform/fxa-content-server/blob/webplatform-customizations/app/scripts/views/base.js)

``` js
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
```

### <span>2. And adjust the CSP policies</span>

**NOTE**: The Content Security Policy changes here is about letting the module to communicate with the accounts server.

In our own fork and branch of `fxa-content-server`, in [server/bin/fxa-content-server.js](https://github.com/webplatform/fxa-content-server/blob/webplatform-customizations/server/bin/fxa-content-server.js)

``` js
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
```

### <span>3. JavaScript client to handle automatic sign in</span>

This section describes what the module actually does.

-   Make sure it doesn't try to do things if local web app already has a session
-   Provide a way to tell whether it already has a session opened
-   Make sure it works without any external library; to be deployed on all SSO relying parties
-   Handle creation of iframe and the `postMessage()`
-   Handle reply from cross-frame request
-   Cross-frame response, validate returned values has keys: `[hasSession, sessionToken]`
-   Make async call to local web application callback through POST
-   If return response of local callback is successful, reload page

It exposes two methods to the `window.sso` object:

-   `window.sso.init(hasSessionClosure, localCallbackEndpoint);` To initialize (see below)
-   `window.sso.doCheck()`, to bootstrap the process (should be done once the iframe is loaded).

``` js
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
```

 Once the iframe is loaded:

``` js
window.sso.doCheck();
```

**NOTE**: If we had a session, the communication triggered at `window.sso.doCheck();`, would had provided us the required data to start automatically and resume at [\#Initialize local web application session](#Initialize_local_web_application_session).