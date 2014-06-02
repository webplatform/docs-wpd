= How we implemented SSO =

The objective of this document is to describe the various moving parts involved in creating SSO for WebPlatform.org

It is meant to give a high level overview of the parts without going too much in the code.

== Steps ==

=== 1. From a page, when you click login ===

Generate a link that summarize where you were ("state"), store that to memcache, go to the authentication with client key ("client") so you see where to login, you would see "Sign in to WebPlatform Test" (see attachment: sso_steps_login.png).

Once it worked (or after creating an account) it sends you to the callback. The callback is defined in the OAuth server configuration —not in the URL, like it is in most case, and the reason of security breach.


=== 2. Redirected to web app callback url ===

From that callback, we get two keys from the server and it allows your local web application to finish handshake.

* State key: Is part of the url, so we can resume where we were. In our case, it will be able to read from memcache later
* Code: A string that is not, yet, an OAuth token. But allows you to continue the handshake.

Based on that we have to make a under the hood request back to the OAuth server, to register authorization.

=== 3. Register authorization token ===

This call is from the backend server (i.e. MediaWiki in PHP) that isn’t visible from the web browser.

Using the POST https://oauth.accounts.webplatform.org/v1/authorization we send a set of data

* client key
* client secret
* code

It returns to you a "Bearer token" that we will use to send to the profile server.

This is also where we could add what’s missing for [#SSO and remembering]. See what i’d do here in [#SSO and remembering]

With a bearer token, wen can read from our first OAuth protected API: The profile server


=== 4. Reading data from the profile server ===

Anybody with a Bearer token can ask details of a user, its a specific HTTP call and you provide that token along the way, you basically end up with something in return or an error.

In our case, that's what we want all client applications (WebPlatform live wiki, WebPlatform test wiki, Annotator, etc) wants to start from.

Otherwise, we woule have to start all over again. My suggestion described at [#SSO and remembering] could resume from that step and save us the hassle to ask users to login from each client web application.

Assuming we have a valid Bearer token, we would get a JSON object looking like this:

<syntaxhighlight>  
{username: 'renoirb', fullName: 'Renoir Boulanger', email: 'renoir@w3.org'}
</syntaxhighlight>

We can now start the local session.

=== 5. Initialize local web application session ===

Based on the data received from the profile server, we intialize a session locally.

* Check if it can find a user matching the given username
* Create a new user if not
* Start local session, cookies, etc.


== SSO and remembering ==

Provided we would have a way to store the user Bearer token somewhere and that other WebPlatform client application would be able to retrieve it, we would be able to have this passwordless login.

By adding a routine to save to memcache what we get at step 3 [#How SSO is implemented], we could have all other clients web apps to start from step 4.

What it does:
* Create a predictable key name for memcache
* Store to memcache
* Adjust MediaWiki extension to retrieve it
* Make sure that memcache isn’t accessible publicly!