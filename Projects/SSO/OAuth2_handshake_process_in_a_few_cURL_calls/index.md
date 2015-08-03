---
title: WPD:Projects/SSO/OAuth2 handshake process in a few cURL calls
---
<h1><span class="mw-headline" id="OAuth2_handshake_process_in_a_few_cURL_calls">OAuth2 handshake process in a few cURL calls</span></h1>
<p>What is the OAuth2 handshake after all?  It seems magical, but in fact, it can be reproduced by a few command line calls.
</p><p>The following describes the steps to retrieve your own profile user data from our profile server.
</p><p>It doesn’t matter that we expose some secrets in this web page, all you will get access from this process is your own data anyway.
</p><p>There is also a longer, in depth, version available at <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How_we_implemented_it</a>
</p>
<h3><span class="mw-headline" id="Requirements">Requirements</span></h3>
<ol><li> An account created on <a rel="nofollow" class="external text" href="https://accounts.webplatform.org/">accounts.webplatform.org</a></li>
<li> A command-line terminal with access to cURL (MacOS has one)</li>
<li> A client_id: <code>e2aa7a52c84b396d</code></li>
<li> A client_secret: <code>e2d1f060cb9e15e7452fe907abb214d32290df72bf954a6149de966378b996fb</code></li>
<li> An OAuth server, and an OAuth protected API (see below)</li></ol>
<p>Note: The both client_id, and client_secret are configured on WebPlatform OAuth server and, provided you finish the handshake, will redirect you to <code><a rel="nofollow" class="external free" href="http://127.0.0.1:5000/login">http://127.0.0.1:5000/login</a></code>.  
</p><p><br />
</p>
<h3><span class="mw-headline" id="TL.3BDR">TL;DR</span></h3>
<p>This process is about getting a one time code that you exchange for a "Bearer token". Once the steps are done, you will get redirected to <code><a rel="nofollow" class="external free" href="http://127.0.0.1:5000/login?code=WHAT_WE_WANT">http://127.0.0.1:5000/login?code=WHAT_WE_WANT</a></code>.
</p><p>Each steps along the way requires cURL, but one of them will have you 
If you have no web server on your own machine, it will just hang, but will have you what you seek for to finish off the steps.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Steps">Steps</span></h2>
<p>Here are the steps of the OAuth handshake all through cURL. Except the login, that will make you use your own web browser and <a rel="nofollow" class="external text" href="https://accounts.webplatform.org/">account details</a>, of course.
</p>
<div class="note">
<p>Also, if we want to have a <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering_remember_my_session" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering remember my session</a> and prevent us to ask for a password again, I pointed out where we could make it happen. Unfortunately for us, its not possible as it is right now.
</p>
</div>
<h3><span class="mw-headline" id="1._Get_handshake_starting_point_details">1. Get handshake starting point details</span></h3>
<p>Basically, its asking what data is related to this OAuth client so we
can start the handshake.
</p><p>Its a way to know if the service exists for the relying party, it lets
you ask for name, image to represent that service, etc.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="bash source-bash"><pre class="de1">  curl <span class="st_h">'https://oauth.accounts.webplatform.org/v1/client/e2aa7a52c84b396d'</span></pre></div></div>
<p>And the response body:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="bash source-bash"><pre class="de1"> <span class="br0">&#123;</span><span class="st0">&quot;name&quot;</span>:<span class="st0">&quot;Annotator (local)&quot;</span>,
  <span class="st0">&quot;image_uri&quot;</span>:<span class="st0">&quot;...&quot;</span>,
  <span class="st0">&quot;redirect_uri&quot;</span>:<span class="st0">&quot;http://127.0.0.1:5000/login&quot;</span><span class="br0">&#125;</span></pre></div></div>
<p>Note that it gives the <code>redirect_uri</code>. As in, we don’t trust ANY data sent by the client, we’ll send it there ourselves.
</p><p><br />
</p>
<h3><span class="mw-headline" id="2._Start_the_handshake">2. Start the handshake</span></h3>
<p>This step makes your browser go around through Response <code>Location: </code> header and change the browser location to that address.
</p><p>An important aspect is that this HTTP call allows you to ask what you
need ("<code>scope</code>"), and how to get back where you were afterwards ("<code>state</code>").
</p><p>The state identifier is useful because since you are leaving your own
application you might want to save the state somewhere else (e.g.
Memcached) and give a key ("<code>state</code>") so we can resume it later.
</p><p>The scope is a coma separated list of things the api exposes. This is
very liberal, but this is how relying parties and providers gets ask the
user to approve what he’s letting the APIs to communicate about him. In
our case, our SSO accepts "session", we might have more later.
</p><p>The request is very similar as <a href="#1._Get_handshake_starting_point_details_step_1">#1. Get handshake starting point details step 1</a>, but this time, we will get
redirected around. Remember that this URL is called by the relying site
and the browser follows the <code>Location:</code> response header.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="bash source-bash"><pre class="de1">  curl <span class="re5">-v</span> <span class="st_h">'https://oauth.accounts.webplatform.org/v1/authorization?scope=session&amp;action=signin&amp;state=8888&amp;client_id=e2aa7a52c84b396d'</span></pre></div></div>
<p><b>NOTE</b>: That the scope, state, and action can by anything. Those are simply declared at the beginning of the proces, and adds entropy to the crypto stuff happening behind the scenes.  The <code>action=signin</code> is a helper for the accounts server to know if we want to login or register. As for the <code>scope=session</code>, you can ask anything, only <code>session</code> will allow you to get things back in the end anyway.
</p><p>In the response headers...
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="bash source-bash"><pre class="de1"><span class="sy0">&lt;</span> HTTP<span class="sy0">/</span><span class="nu0">1.1</span> <span class="nu0">302</span> Moved Temporarily
<span class="sy0">&lt;</span> Server: nginx<span class="sy0">/</span>1.4.6 <span class="br0">&#40;</span>Ubuntu<span class="br0">&#41;</span>
<span class="sy0">&lt;</span> Date: Fri, <span class="nu0">18</span> Jul <span class="nu0">2014</span> 00:<span class="nu0">14</span>:<span class="nu0">23</span> GMT
<span class="sy0">&lt;</span> Content-Length: <span class="nu0">0</span>
<span class="sy0">&lt;</span> Location:
https:<span class="sy0">//</span>accounts.webplatform.org<span class="sy0">/</span>oauth<span class="sy0">/</span>signin?<span class="re2">scope</span>=session<span class="sy0">&amp;</span><span class="re2">state</span>=<span class="nu0">8888</span><span class="sy0">&amp;</span><span class="re2">client_id</span>=e2aa7a52c84b396d
<span class="sy0">&lt;</span> access-control-allow-origin: <span class="sy0">*</span>
<span class="sy0">&lt;</span> access-control-max-age: <span class="nu0">86400</span>
<span class="sy0">&lt;</span> access-control-allow-methods: GET, HEAD, POST, PUT, PATCH, DELETE, OPTIONS
<span class="sy0">&lt;</span> access-control-allow-headers: Authorization, Content-Type, If-None-Match
<span class="sy0">&lt;</span> access-control-expose-headers: WWW-Authenticate, Server-Authorization
<span class="sy0">&lt;</span> cache-control: no-cache</pre></div></div>
<p>Location is there, let’s copy that, and paste it in your own web
browser. You will need to sign-in.
</p>
<div class="note">
<p>Instead of doing like <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering_remember_my_session" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering remember my session</a>, if <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/WPD:Projects/SSO/Adapt_Firefox_Accounts_for_WebPlatform">our version of FxA</a> <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/WPD:Projects/SSO/Improvements_roadmap#Leveraging_completely_OAuth2">had handled remember session</a>, we could get right through. If that part was complete, it would "remember" you signed in already and we would already get to <a href="#4._Exchange_the_code_for_what_we_need">#4. Exchange the code for what we need</a> with a code in hand!
</p>
</div>
<p><br />
</p>
<h3><span class="mw-headline" id="3._Go_to_the_Location_and_ask_the_code">3. Go to the Location and ask the code</span></h3>
<p>Use your web browser, and sign in.
</p>
<pre> <a rel="nofollow" class="external free" href="https://accounts.webplatform.org/oauth/signin?scope=session&amp;state=8888&amp;client_id=e2aa7a52c84b396d">https://accounts.webplatform.org/oauth/signin?scope=session&amp;state=8888&amp;client_id=e2aa7a52c84b396d</a>
</pre>
<p><b>NOTE</b>: Replace "WebPlatform Test", in the following image, for "Annotator (local)"
</p><p><a href="/wiki/File:sso_steps_login_dialog.png" class="image"><img alt="sso steps login dialog.png" src="//static.webplatform.org/w/public/3/31/sso_steps_login_dialog.png" width="800" height="640" /></a>
</p><p><br />
Once its done, you should be redirected with a <code>code=...</code> visible in the address bar:
</p>
<pre> <a rel="nofollow" class="external free" href="http://127.0.0.1:5000/login?state=8888&amp;code=a6373251b8a61808633cfe32f3518b01bad01a9010d3c18ed2072d5335b421bb">http://127.0.0.1:5000/login?state=8888&amp;code=a6373251b8a61808633cfe32f3518b01bad01a9010d3c18ed2072d5335b421bb</a>
</pre>
<p><b>NOTE</b>: The code is no longer valid (its a one time, remember), you will have to get your own.
</p>
<div class="note">
<p>Like previously said about the feature miss. We wouldn’t had needed to ask the user to login if it was complete, we would have had gotten back to the initiating web app, the notes server here, the code and could start a session in his own web app.
</p>
</div>
<p><br />
</p>
<h3><span class="mw-headline" id="4._Exchange_the_code_for_what_we_need">4. Exchange the code for what we need</span></h3>
<p>This is done by the backend of the relying party site. The <code>callback_uri</code> expects
a <code>GET</code> request with a <code>&amp;code=...</code> string that it’ll communicate <b>Off the band</b> (i.e. from the web app server to the OAuth server, without passing through the visitor web browser).
</p><p>Its an important concept because we are sending around the client secret. Even though we are using SSL, we want to be sure that the client_secret is sent to the network as less as possible. In this case, only registered relying parties and OAuth servers will see this data being passed around.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="bash source-bash"><pre class="de1">  curl <span class="re5">-v</span> <span class="re5">-XPOST</span>
    <span class="re5">-H</span> <span class="st_h">'Content-Type: application/json'</span>
    <span class="st_h">'https://oauth.accounts.webplatform.org/v1/token'</span>
    <span class="re5">-d</span> <span class="st_h">'{&quot;client_id&quot;:&quot;e2aa7a52c84b396d&quot;, \
        &quot;client_secret&quot;:&quot;e2d1f060cb9e15e7452fe907abb214d32290df72bf954a6149de966378b996fb&quot;, \
         &quot;code&quot;:&quot;a6373251b8a61808633cfe32f3518b01bad01a9010d3c18ed2072d5335b421bb&quot;}'</span></pre></div></div>
<p><br />
We get the token we wanted in the response body:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="javascript source-javascript"><pre class="de1">&#160;
<span class="br0">&#123;</span><span class="st0">&quot;access_token&quot;</span><span class="sy0">:</span><span class="st0">&quot;f787622b3a7f818bceb9a7793f77afb669d72579325a7a9a3c853e540e5f5544&quot;</span><span class="sy0">,</span>
  <span class="st0">&quot;token_type&quot;</span><span class="sy0">:</span><span class="st0">&quot;bearer&quot;</span><span class="sy0">,</span>
  <span class="st0">&quot;scope&quot;</span><span class="sy0">:</span><span class="st0">&quot;session&quot;</span><span class="br0">&#125;</span></pre></div></div>
<p><b>NOTE</b>: That bearer token is invalid (i changed it), you will have to get your own&#160;;)
</p><p><br />
</p>
<h3><span class="mw-headline" id="5._Ask_stuff_to_an_OAuth2_protected_API">5. Ask stuff to an OAuth2 protected API</span></h3>
<p>So far, only a few are available, the profile server which gives us back data for our own users.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="bash source-bash"><pre class="de1">  curl <span class="re5">-H</span> <span class="st0">&quot;Authorization: Bearer f787622b3a7f818bceb9a7793f77afb669d72579325a7a9a3c853e540e5f5544&quot;</span>\
      <span class="st0">&quot;https://profile.accounts.webplatform.org/v1/session/read&quot;</span></pre></div></div>
<p>And the response body would look like this:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="javascript source-javascript"><pre class="de1"><span class="br0">&#123;</span><span class="st0">&quot;username&quot;</span><span class="sy0">:</span> <span class="st0">&quot;jdoe&quot;</span><span class="sy0">,</span>
 <span class="st0">&quot;fullName&quot;</span><span class="sy0">:</span> <span class="st0">&quot;John Doe&quot;</span><span class="sy0">,</span>
 <span class="st0">&quot;email&quot;</span><span class="sy0">:</span> <span class="st0">&quot;hi@example.org&quot;</span><span class="sy0">,</span>
 <span class="st0">&quot;uid&quot;</span><span class="sy0">:</span> <span class="st0">&quot;3E09D6DF843341BC921A25423AB83BAF&quot;</span> <span class="br0">&#125;</span></pre></div></div>

<!-- 
NewPP limit report
CPU time usage: 0.187 seconds
Real time usage: 1.457 seconds
Preprocessor visited node count: 97/1000000
Preprocessor generated node count: 206/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:27259-0!*!0!!*!5!*!esi=1 and timestamp 20150731111126 and revision id 63732
 -->
