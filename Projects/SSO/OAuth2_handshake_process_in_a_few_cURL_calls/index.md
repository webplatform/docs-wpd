== Description ==

What is the OAuth2 handshake after all?  It seems magical, but in fact, it can be reproduced by a few command line calls.

The following describes the steps to retrieve your own profile user data from our profile server.

It doesn’t matter that we expose some secrets in this web page, all you will get access from this process is your own data anyway.


=== Requirements ===
# An account created on [https://accounts.webplatform.org/ accounts.webplatform.org]
# A command-line terminal with access to cURL (MacOS has one)
# A client_id: <code>e2aa7a52c84b396d</code>
# A client_secret: <code>e2d1f060cb9e15e7452fe907abb214d32290df72bf954a6149de966378b996fb</code>
# An OAuth server, and an OAuth protected API (see below)

Note: The both client_id, and client_secret are configured on WebPlatform OAuth server and, provided you finish the handshake, will redirect you to <code>http://127.0.0.1:5000/login</code>.  


=== TL;DR ===

This process is about getting a one time code that you exchange for a "Bearer token". Once the steps are done, you will get redirected to <code>http://127.0.0.1:5000/login?code=WHAT_WE_WANT</code>.

Each steps along the way requires cURL, but one of them will have you 
If you have no web server on your own machine, it will just hang, but will have you what you seek for to finish off the steps.


== Steps ==

Here are the steps of the OAuth handshake all through cURL. Except the login, that will make you use your own web browser and [https://accounts.webplatform.org/ account details], of course.

Also, if we want to have a "[WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering remember my session]" and prevent us to ask for a password again, I pointed out where we could make it happen. Unfortunately for us, its not possible as it is right now.


=== 1. Get handshake starting point details ===

Basically, its asking what data is related to this OAuth client so we
can start the handshake.

Its a way to know if the service exists for the relying party, it lets
you ask for name, image to represent that service, etc.

<syntaxHighlight lang="bash">
  curl -v
'https://oauth.accounts.webplatform.org/v1/client/e2aa7a52c84b396d'

 {"name":"WebPlatform Notes",
  "image_uri":"...",
  "redirect_uri":"https://notes.webplatform.org/login"}
</syntaxHighlight>

Note that it gives the `redirect_uri`. As in, we don’t trust ANY data sent by the client, we’ll send it there ourselves.



=== 2. Start the handshake ===

This step makes your browser go around through Response `Location: ...`
redirect.

An important aspect is that this HTTP call allows you to ask what you
need ("scope"), and how to get back where you were afterwards ("state").

The state identifier is useful because since you are leaving your own
application you might want to save the state somewhere else (e.g.
Memcached) and give a key ("state") so we can resume it later.

The scope is a coma separated list of things the api exposes. This is
very liberal, but this is how relying parties and providers gets ask the
user to approve what he’s letting the APIs to communicate about him. In
our case, our SSO accepts "session", we might have more later.

The request is very similar as step 1, but this time, we will get
redirected around. Remember that this URL is called by the reyling site
and the browser follows the Location: redirects.


<syntaxHighlight lang="bash">
  curl -v
'https://oauth.accounts.webplatform.org/v1/authorization?scope=session&action=signin&state=8888&client_id=e2aa7a52c84b396d'
</syntaxHighlight>

In the response...

<syntaxHighlight lang="bash">
< HTTP/1.1 302 Moved Temporarily
< Server: nginx/1.4.6 (Ubuntu)
< Date: Fri, 18 Jul 2014 00:14:23 GMT
< Content-Length: 0
< Location:
https://accounts.webplatform.org/oauth/signin?scope=session&state=8888&client_id=e2aa7a52c84b396d
< access-control-allow-origin: *
< access-control-max-age: 86400
< access-control-allow-methods: GET, HEAD, POST, PUT, PATCH, DELETE, OPTIONS
< access-control-allow-headers: Authorization, Content-Type, If-None-Match
< access-control-expose-headers: WWW-Authenticate, Server-Authorization
< cache-control: no-cache
</syntaxHighlight>

Location is there, let’s copy that, and paste it in your own web
browser. You will need to sign-in.

<div class="notes">
This is where the current version of FxA that we are using is incomplete. If that part was complete, it would "remember" you signed in already and we would already get to step 4 with a code in hand!
</div>



=== 3. Go to the Location and ask the code ===

Go there, and sign in.

  https://accounts.webplatform.org/oauth/signin?scope=session&state=8888&client_id=e2aa7a52c84b396d

Once its done, you should be redirected with a code=... visible in the
address bar:

  https://notes.webplatform.org/login?state=8888&code=a6373251b8a61808633cfe32f3518b01bad01a9010d3c18ed2072d5335b421bb

'''NOTE''': The code is no longer valid (its a one time, remember), you will have to get your own.

<div class="notes">
Like previously said about the feature miss. We wouldn’t had needed to ask the user to login if it was complete, we would have had gotten back to the initiating web app, the notes server here, the code and could start a session in his own web app.
</div>


=== 4. Exchange the code for what we need ===

This is done by the backend when he got the GET request. Its an
important concept because we are sending around the client secret. Even
though we are using SSL, we want to be sure that the client_secret is
not sent everywhere around.

<syntaxHighlight lang="bash">
  curl -v -XPOST
    -H 'Content-Type: application/json'
    'https://oauth.accounts.webplatform.org/v1/token'
    -d '{"client_id":"e2aa7a52c84b396d", \
        "client_secret":"e2d1f060cb9e15e7452fe907abb214d32290df72bf954a6149de966378b996fb",
         "code":"a6373251b8a61808633cfe32f3518b01bad01a9010d3c18ed2072d5335b421bb"}'
</syntaxHighlight>


We get the token:

<syntaxHighlight lang="javascript"> 
{"access_token":"f787622b3a7f818bceb9a7793f77afb669d72579325a7a9a3c853e540e5f5544",
  "token_type":"bearer",
  "scope":"session"}
</syntaxHighlight>

NOTE: The token is invalid (i changed numbers), you will have to get your own ;)


=== 5. Ask stuff to an OAuth2 protected API ===

So far, only a few are available, the profile server which gives us back data for our own users.

<syntaxHighlight lang="bash">
  curl -v
    -H "Authorization: Bearer
f787622b3a7f818bceb9a7793f77afb669d72579325a7a9a3c853e540e5f5544"
    'https://profile.accounts.webplatform.org/v1/session/read'
</syntaxHighlight>