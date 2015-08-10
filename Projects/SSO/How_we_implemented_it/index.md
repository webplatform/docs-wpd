---
title: WPD:Projects/SSO/How we implemented it
path: Projects/SSO/How_we_implemented_it

---
<h1><span class="mw-headline" id="How_we_implemented_SSO">How we implemented SSO</span></h1>
<p>The objective of this document is to describe how we implemented a SSO solution for WebPlatform.org. It is meant to give an idea of the various moving parts. 
</p><p>If you want to see the high level description, refer to <a href="/wiki/WPD:Projects/SSO/Login_Workflows" title="WPD:Projects/SSO/Login Workflows">WPD:Projects/SSO/Login Workflows</a> or if you want a shorter version, go to <a href="/wiki/WPD:Projects/SSO/OAuth2_handshake_process_in_a_few_cURL_calls" title="WPD:Projects/SSO/OAuth2 handshake process in a few cURL calls">WPD:Projects/SSO/OAuth2_handshake_process_in_a_few_cURL_calls</a>.
</p><p>The authentication portal is using our own fork of Mozilla Firefox Accounts ("FxA") deployed on WebPlatform.org infrastructure. Details of the adaptations are described in <a href="/wiki/WPD:Projects/SSO/Adapt_Firefox_Accounts_for_WebPlatform" title="WPD:Projects/SSO/Adapt Firefox Accounts for WebPlatform">WPD:Projects/SSO/Adapt_Firefox_Accounts_for_WebPlatform</a>.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Stories">Stories</span></h3>
<p>The present document describe how we address a set of user stories but it should be noted that the final result is expected to use the SSO across ALL WebPlatform.org services and participating W3C Specifications.
</p>
<ul><li> As a non authenticated person, I want to edit in the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/css/properties/border">a page on docs.webplatform.org/wiki/</a> ("A").</li>
<li> As a non authenticated person, I want to add annotations on a participating <a rel="nofollow" class="external text" href="http://www.w3.org/2014/annotation/experiment/webaudio.html">W3C spec that supports annotations</a> ("B")</li>
<li> As a non authenticated person, I want to experiment with Docs features in the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/test/css/properties/border">WebPlatform Docs "test" wiki</a> ("C").</li>
<li> As a non authenticated person, I want to be allowed to edit in the <a rel="nofollow" class="external text" href="http://docs.mroftalpbew.org/wiki/Main_Page">WebPlatform Docs Staging wiki</a> ("D") and see if the upcoming deployment will work</li>
<li> As a non authenticated visitor, I want to start a session and be allowed to perform [A, B, C, D] without authenticating myself more than once</li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="Workflows">Workflows</span></h3>
<p>Repeating what was described in <a href="/wiki/WPD:Projects/SSO/Login_Workflows" title="WPD:Projects/SSO/Login Workflows">WPD:Projects/SSO/Login Workflows</a>, to be detailed in this page.
</p><p>In order to fulfill the given <a href="#Stories">#Stories</a>, we needed to implement a SSO solution covers the following:
</p>
<ul><li> Get authenticated through a single authority (see <a href="#Delegating_authentication">#Delegating authentication</a>)</li>
<li> <a href="#Read_user_data">#Read user data</a> from an API, </li>
<li> Let each configured web applications to detect a session on the authority (see <a href="#SSO_and_remembering">#SSO and remembering</a>)</li>
<li> handle their local users and session (see <a href="#Initialize_local_web_application_session">#Initialize local web application session</a>), and</li>
<li> Detect automatically if there is a session in the accounts server, and start it automatically (see <a href="#JavaScript_shared_module:_Detect_and_start_automatically_a_session">#JavaScript shared module: Detect and start automatically a session</a>)</li></ul>
<p><br />
</p>
<hr />
<p><br />
</p>
<h2><span class="mw-headline" id="Delegating_authentication">Delegating authentication</span></h2>
<p>This step is meant to address the <b>Get authenticated through a single authority</b> workflow.
</p>
<h3><span class="mw-headline" id="0._Preamble">0. Preamble</span></h3>
<p>In this implementation we are passing through authentication to get an OAuth2 Bearer authorization token so that we can get data on the behalf of the authenticated user.
</p><p>The following makes use of the generated Authorization token to read a profile server and read associated user data (i.e. email address, full name, username, etc.) that will be used in all web applications.
</p><p><i>NOTE</i> At the moment, the Authorization token is used only once. In future development, we might want to add features and will need to store securely that token to make other actions on the behalf of the user.
</p><p><br />
</p>
<h3><span class="mw-headline" id="1._Configure_the_OAuth_server_to_accept_requests_from_a_client">1. Configure the OAuth server to accept requests from a client</span></h3>
<p>In OAuth terminology, a client is a consumer that is authorized to rely on the OAuth server. A client can be a web application, but its not only limited to that.
</p><p>In this example, we are going to show how the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/test/css/properties/border">WebPlatform Docs "test" wiki</a> ("C") gets data from the various layers.
</p><p>Client configuration is described in the project documentation available in the  <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-oauth-server/blob/master/docs/clients.md">WebPlatform's fork of FxA OAuth Server in <i>docs/clients.md</i></a>.
</p><p>Within FxA OAuth server configuration, a <tt>client: [/* array of clients */]</tt> entry looks like this:
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
{
  "id": "7e7e11299d95d789",
  "secret": "a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa",
  "name": "WebPlatform Test",
  "image_uri": "...",
  "redirectUri":"http://docs.webplatform.org/test/Special:AccountsHandler/callback",
  "whitelisted": true
}
</pre>
<p><br />
</p>
<ul><li> <tt>id</tt>: Is a 8 byte hexadecimal string that you will need to have on the client configuration</li>
<li> <tt>secret</tt>: Is a 32 byte hexadecimal string that you will also need on the client configuration.</li>
<li> <tt>redirectUri</tt>: Is where you should send the users to when they successfully authenticated.</li></ul>
<p>To continue with our example, we are connecting to a MediaWiki installation that has the <a href="/wiki/WPD:Projects/SSO/MediaWikiExtension" title="WPD:Projects/SSO/MediaWikiExtension">WPD:Projects/SSO/MediaWikiExtension</a> available. In the case of that particular extension, it expects that we send authenticated users back to <tt>Special:AccountsHandler/callback</tt>.
</p><p><br />
</p>
<h3><span class="mw-headline" id="2._Configure_client">2. Configure client</span></h3>
<p>Configuring a client to use our OAuth server can be different depending on how the extension implements OAuth2.
</p><p>Regardless of the exact configuration lines or code, every OAuth2 clients has similar configuration lines.
</p><p>Such as:
</p>
<ul><li> Start the process</li>
<li> Generate an Authorization token</li></ul>
<p>In the case of our implementation, we also added (<tt>fxa_profile</tt>) so that we can read user data from somewhere.
</p><p>Our MediaWiki extension has similar configuration in its <tt>Settings.php</tt> file:
</p><p><br />
</p>
<pre class="language-php" data-lang="php">
require_once( "$IP/extensions/WebPlatformAuth/WebPlatformAuth.php" );
$wgWebPlatformAuth['client']['id']             = '7e7e11299d95d789';
$wgWebPlatformAuth['client']['secret']         = 'a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa';
$wgWebPlatformAuth['endpoints']['fxa_oauth']   = 'https://oauth.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['endpoints']['fxa_profile'] = 'https://profile.accounts.webplatform.org/v1/';
$wgWebPlatformAuth['methods']['authorize']     = 'authorization';
$wgWebPlatformAuth['methods']['token']         = 'token';
</pre>
<p><br />
While configuration can be different depending on the client extension, a few endpoints are required to be used in our installation.
</p>
<ul><li> <tt>GET <a rel="nofollow" class="external free" href="https://oauth.accounts.webplatform.org/v1/authorization">https://oauth.accounts.webplatform.org/v1/authorization</a></tt></li>
<li> <tt>POST <a rel="nofollow" class="external free" href="https://oauth.accounts.webplatform.org/v1/authorization">https://oauth.accounts.webplatform.org/v1/authorization</a></tt></li>
<li> <tt>POST <a rel="nofollow" class="external free" href="https://oauth.accounts.webplatform.org/v1/token">https://oauth.accounts.webplatform.org/v1/token</a></tt></li>
<li> <tt>GET <a rel="nofollow" class="external free" href="https://profile.accounts.webplatform.org/v1/session/read">https://profile.accounts.webplatform.org/v1/session/read</a></tt>, with scope '<tt>session</tt>'</li></ul>
<p>Most of these requests aren’t made through the browser but through a server-side HTTP client. In the MediaWiki extension, we are using Guzzle.
</p><p><i>NOTE</i> Even though the calls are aimed at endpoints under SSL, it feels safer to have those requests made outside of the reach of the visitor web browser.
</p><p><br />
</p>
<h3><span class="mw-headline" id="3._Possibility:_Detected_a_session">3. Possibility: Detected a session</span></h3>
<p>On page load, a non blocking <a href="#JavaScript_shared_module:_Detect_and_start_automatically_a_session">#JavaScript shared module: Detect and start automatically a session</a> attempts to read from the <a rel="nofollow" class="external text" href="https://accounts.webplatform.org/">accounts server</a> to see whether a session is already opened or not. 
</p><p>The outline of what’s happening is described in <a href="#SSO_and_remembering">#SSO and remembering</a>.
</p><p>If no session is detected, the module does nothing.
</p><p><br />
</p>
<h3><span class="mw-headline" id="4._From_a_page.2C_when_you_click_login">4. From a page, when you click login</span></h3>
<p>The MediaWiki extension detects the click and sends you to <tt>Special:AccountsHandler/start</tt>. Its an internal process to generate a redirect to the OAuth2 authentication flow.
</p><p>The web application generates and sends user to the OAuth authentication endpoint, with some data:
</p>
<ul><li> The client identifier ("<tt>client_id</tt>")</li>
<li> What the application wants ("<tt>scope</tt>")</li>
<li> What state it was in ("<tt>state</tt>"), this is a random key used to store inside a key store such as Memcache so we can retrieve the state data after the authentication process.</li></ul>
<p><b>NOTE</b> In Mozilla Firefox Accounts, the <tt>callbackUri</tt> is configured in the server configuration directly. This is considered safer to trust only the configuration file in contrast to common OAuth2 server implementation where they also want the <tt>callbackUri</tt> as part of the first redirect. This is a way to address a security breach in original OAuth2 specification.
</p><p>Since the OAuth server knows who is the client, it adjusts the title to "Sign in to WebPlatform Test".
</p><p><a href="/wiki/File:sso_steps_login_dialog.png" class="image"><img alt="sso steps login dialog.png" src="//static.webplatform.org/w/public/3/31/sso_steps_login_dialog.png" width="800" height="640" /></a>
</p><p><b>NOTE</b> In the screenshot above, you see <i>scope=profile</i>. Since that snapshot, we changed the scope name to  <i>session</i> because we needed to differentiate web application that will use OAuth to create local sessions from future use cases.
</p><p>Once the authentication worked the <a rel="nofollow" class="external text" href="https://accounts.webplatform.org/">accounts server</a> sends you to the <tt>callbackUri</tt> (e.g. <tt>Special:AccountsHandler/callback</tt> for Media Wiki).
</p><p><br />
</p>
<h3><span class="mw-headline" id="5._Redirected_the_callback_URI">5. Redirected the callback URI</span></h3>
<p>From that callback, we get two keys:
</p>
<ul><li> <tt>state</tt>: Is that string we gave in the previous step, we get it back so we can resume where we were before the authentication process. If the state data (e.g. previous page visited) was serialized and sent to Memcache, we can ask it once again and resume.</li>
<li> <tt>code</tt>: This is a one-time token that we can use to get an OAuth2 Token. In this example, its "SOMETHING_LONG"</li></ul>
<p>The callback URI looks like this:
</p><p><code>/wiki/Special:AccountsHandler/callback?code=SOMETHING_LONG&amp;state=5a72cd23b1b5feb8</code>
</p><p>Based on the received data, we can continue with the OAuth2 handshake.
</p><p><br />
</p>
<h3><span class="mw-headline" id="6._Get_an_Authorization_token">6. Get an Authorization token</span></h3>
<p>From the <tt>callbackUri</tt> handler, with the expected data (<tt>state</tt>, <tt>code</tt>) we make a few HTTP calls server to server (i.e. invisible to the web browser).
</p><p>The call to get the Authorization token contains:
</p>
<ul><li> <tt>client_id</tt>: The identifier we configured in both OAuth server and the client</li>
<li> <tt>client secret</tt>: The shared secret</li>
<li> <tt>code</tt>: The one-time code we got when redirected to the <tt>callbackUri</tt>.</li></ul>
<p>The request is similar to this cURL call:
</p><p><br />
</p>
<pre class="language-bash" data-lang="bash">
curl -XPOST -H 'Content-Type: application/json' \
     'https://oauth.accounts.webplatform.org/v1/token' \
     -d '{"client_id":"7e7e11299d95d789",
          "client_secret":"a331e8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2aa",
          "code":"SOMETHING_LONG"}'
</pre>
<p><br />
We get in exchange the Authorization token in a response that looks like this:
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
{"access_token":"6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31",
 "token_type":"bearer",
 "scope":"session"}
</pre>
<p><br />
The <tt>access_token</tt> is what we needed to act on the behalf of the logged in user.
</p><p>At the time, the only protected service is the profile server, but we might want to protect other components later down the road.
</p><p><b>NOTE</b> An OAuth Authorization token is basically a key to make actions on the behalf of a valid user. In this regard, it is of the utmost importance to have it sent only through SSL, and, ideally, always outside of the reach of the web browser.
</p><p><br />
</p>
<h3><span class="mw-headline" id="7._Finsish_off_things">7. Finsish off things</span></h3>
<p>Continued in <a href="#Read_user_data">#Read user data</a>, and then <a href="#Initialize_local_web_application_session">#Initialize local web application session</a> workflow.
</p><p><br />
</p>
<hr />
<p><br />
</p>
<h2><span class="mw-headline" id="Read_user_data">Read user data</span></h2>
<p>This step is meant to address the <b>Read user data through an API</b> workflow.
</p><p>Assuming our web application has a valid <i>Authorization token</i>, OR <i>session token</i>, we can get the account data we need from the profile server.
</p><p>The profile server <b>MUST return the same data</b> regardless of whether it got an <i>Authorization token</i> or a <i>session token</i>.
</p><p>The Profile server has two distinct methods to provide user data. 
</p>
<ul><li> One to <i>read</i> the user data for the first time, requiring a valid OAuth2 Authorization token</li>
<li> One to <i>recover</i> the user data, meaning the server already has a session opened on the <a rel="nofollow" class="external text" href="https://accounts.webplatform.org/">accounts server</a> and we want to use the same data.</li></ul>
<p>To read more about recovering a session, refer to <a href="#SSO_and_remembering">#SSO and remembering</a> workflow.
</p><p>The call to the profile server looks like the following cURL calls:
</p><p><b>With an Authorization token</b>:
</p>
<pre class="language-bash" data-lang="bash">
curl -H 'Content-Type: application/json' \
     -H "Authorization: Bearer 6243bbcf3f1f451cc5b3f47e662568b90863995a4e675a3073eb72434ab2ba31" \
     'https://profile.accounts.webplatform.org/v1/session/read'
</pre>
<p><br />
<b>With a session token</b>:
</p><p><b>NOTE</b>; The <tt>sessionToken</tt> is available from the <a rel="nofollow" class="external text" href="https://accounts.webplatform.org/settings">Accounts server settings view</a> only once a user is logged in. To access it, we are using cross-frame communication and read the token from localStorage API.
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
// URI https://accounts.webplatform.org/settings
var obj = JSON.parse(window.localStorage.getItem('__fxa_session')) || {};
console.log(obj); // if there is a session, obj.sessionToken will have what we need
</pre>
<p><br />
Use the <tt>obj.sessionToken</tt> after <tt>Session</tt> in the following cURL:
</p><p><br />
</p>
<pre class="language-bash" data-lang="bash">
curl -v -H 'Content-Type: application/json' \
        -H "Authorization: Session 095dc99de03e99c6d93211aced561c6a28800cdd20fe2ff55ef4626401a04045" \
        'https://profile.accounts.webplatform.org/v1/session/recover'
</pre>
<p><br />
</p><p>If the profile server accepted either methods, we get a JSON object looking like this:
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
{"username": "jdoe",
 "fullName": "John Doe",
 "email": "hi@example.org",
 "uid": "3E09D6DF843341BC921A25423AB83BAF" }
</pre>
<p><br />
We can now start the session in the client web application.
</p><p><b>NOTE</b> Authorization headers is functionally the same as what the web browser does with cookies. In fact, during a browsing session that has cookies, they are sent along with every HTTP requests. And that is, regardless of whether its an image, a CSS file, or a web page. The cookie is therefore a way to tell the application server to tell who the visitor is and potentially change the returned resource.
</p><p><br />
</p>
<hr />
<p><br />
</p>
<h2><span class="mw-headline" id="Initialize_local_web_application_session">Initialize local web application session</span></h2>
<p>This step is meant to address the <b>handle their local users and session</b> workflow and what the backend code MUST implement.
</p><p>One of the key behavior in a SSO system is that each configured application relies on an authority to provide common user data (e.g. email, username, fullName), but also to confirm if it can start a session locally and overriding its own user validation system.
</p>
<h3><span class="mw-headline" id="0._Preamble_2">0. Preamble</span></h3>
<p>The following MUST be done in the backend code answering at the what is refered to as "<b>callback</b>" (e.g. <tt>Special:AccountsHandler/callback</tt>) on each relying parties who wants to use the SSO. 
</p><p>It handles the following steps:
</p>
<ul><li> Read data from profile server</li>
<li> Find matching user, and/or create a new one</li>
<li> Start a session</li>
<li> Return a status code for the <a href="#JavaScript_shared_module:_Detect_and_start_automatically_a_session">#JavaScript shared module: Detect and start automatically a session</a> </li></ul>
<p>This component answers in two different scenarios:
</p>
<ul><li> GET request with two parameters (e.g. <tt>Special:AccountsHandler/callback?code=aaa&amp;state=bbb</tt>), "<a href="#1.1_Possibility:_Completing_an_OAuth2_handshake">#1.1 Possibility: Completing an OAuth2 handshake</a>"</li>
<li> POST request with <tt>recoveryPayload</tt> data, "<a href="#1.2_Possibility:_Resuming_a_session_confirmed_by_the_accounts_server">#1.2 Possibility: Resuming a session confirmed by the accounts server</a>".</li></ul>
<p>In both <i>Behavior forks</i>, the returned data from the profile server MUST be in the following format:
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
{"username": "jdoe",
 "fullName": "John Doe",
 "email": "hi@example.org",
 "uid": "3E09D6DF843341BC921A25423AB83BAF" }
</pre>
<p><br />
Since each web application can have different database and ways to refer to a given user, we are using this information to find if a user already exists in the local database, or we create one with the default details for the user.
</p><p>Based on the data received from the profile server, we initialize a session locally.
</p><p><br />
</p>
<h3><span class="mw-headline" id="1._Behavior_forks">1. Behavior forks</span></h3>
<p>Here is how the backend code MUST behave in both cases.
</p><p>The steps are basically the same, but acts differently depending of what initiated the process.
</p><p>Here are the differences in both cases.
</p>
<h4><span class="mw-headline" id="1.1_Possibility:_Completing_an_OAuth2_handshake">1.1 Possibility: Completing an OAuth2 handshake</span></h4>
<p>This section covers what the backend does when it got called during an OAuth2 workflow during <a href="#Delegating_authentication">#Delegating authentication</a> and mentionned in <a href="#5._Redirected_the_callback_URI">#5. Redirected the callback URI</a>.
</p><p>In this case, we are provided with TWO keys through a <tt>GET</tt> request to our callback (e.g. <tt>Special:AccountsHandler/callback</tt>)
</p>
<ul><li> <tt>code</tt>: The one-time token that is the last step to get an Authorization token</li>
<li> <tt>state</tt>: A key identifier that we got when we saved away in a key store (e.g. Memcache) the state before signing in.</li></ul>
<h5><span class="mw-headline" id="1.1.1_Get_an_OAuth2_authorization_token">1.1.1 Get an OAuth2 authorization token</span></h5>
<p>With the <tt>code</tt> in hand, we can <a href="#6._Get_an_Authorization_token">#6. Get an Authorization token</a>, then ask the profile server the user data.
</p><p>As described in <a href="#6._Get_an_Authorization_token">#6. Get an Authorization token</a>.
</p>
<h5><span class="mw-headline" id="1.1.2_Read_data_from_profile_server">1.1.2 Read data from profile server</span></h5>
<p>As described in <a href="#Read_user_data">#Read user data</a> <i>With an Authorization token</i> (OAuth2).
</p>
<h5><span class="mw-headline" id="1.1.3_Find_matching_user.2C_and.2For_create_a_new_one">1.1.3 Find matching user, and/or create a new one</span></h5>
<p>This is specific to each web application, for MediaWiki you can refer to <a href="/wiki/WPD:Projects/SSO/MediaWikiExtension" title="WPD:Projects/SSO/MediaWikiExtension">WPD:Projects/SSO/MediaWikiExtension</a>.
</p>
<h5><span class="mw-headline" id="1.1.4_Start_a_session">1.1.4 Start a session</span></h5>
<p>This is specific to each web application, for MediaWiki you can refer to <a href="/wiki/WPD:Projects/SSO/MediaWikiExtension" title="WPD:Projects/SSO/MediaWikiExtension">WPD:Projects/SSO/MediaWikiExtension</a>.
</p>
<h5><span class="mw-headline" id="1.1.5_Resume_previous_state">1.1.5 Resume previous state</span></h5>
<p>During previous OAuth2 workflow steps, we saved some data in a key store ("state") and we can use it to send the user where he was in.
</p><p>In the case of the <a href="/wiki/WPD:Projects/SSO/MediaWikiExtension" title="WPD:Projects/SSO/MediaWikiExtension">WPD:Projects/SSO/MediaWikiExtension</a>, we currently store the previous page the user visited and would look like this:
</p><p><br />
</p>
<pre class="language-html5" data-lang="html5">
{return_to:"http://docs.webplatform.org/wiki/WPD:Projects/SSO/Login_Workflows"}
</pre>
<p><br />
Based on that information, we issue a redirect and the user is back where he was.
</p><p><br />
</p>
<h4><span class="mw-headline" id="1.2_Possibility:_Resuming_a_session_confirmed_by_the_accounts_server">1.2 Possibility: Resuming a session confirmed by the accounts server</span></h4>
<p>This section covers what the backend does when we detected a session through the frontend discovery mechanism <a href="/wiki/WPD:Projects/SSO/Login_Workflows#Starting_a_session_by_communicating_with_accounts_server" title="WPD:Projects/SSO/Login Workflows">WPD:Projects/SSO/Login Workflows#Starting a session by communicating with accounts server</a>.
</p><p>In this case, we are provided with ONE key through a <tt>POST</tt> request to our callback (e.g. <tt>Special:AccountsHandler/callback</tt>)
</p>
<ul><li> <tt>recoveryPayload</tt>: Containing the data used to ask the profile server</li></ul>
<p><b>NOTE</b> This step is currently getting directly the <tt>sessionToken</tt> and will eventually changed, see reasons in <a href="/wiki/WPD:Projects/SSO/Improvements_roadmap#Recovering_session_data" title="WPD:Projects/SSO/Improvements roadmap">WPD:Projects/SSO/Improvements roadmap#Recovering session data</a>.
</p>
<h5><span class="mw-headline" id="1.2.1_Make_a_request_with_the_received_data">1.2.1 Make a request with the received data</span></h5>
<p>As described in <a href="#SSO_and_remembering">#SSO and remembering</a>, in the step <a href="#4._Read_data_from_the_profile_server_with_a_recoveryPayload">#4. Read data from the profile server with a recoveryPayload</a>.
</p>
<h5><span class="mw-headline" id="1.2.1_Read_data_from_profile_server">1.2.1 Read data from profile server</span></h5>
<p>As described in <a href="#Read_user_data">#Read user data</a> <i>With a session token</i>.
</p>
<h5><span class="mw-headline" id="1.2.2_Find_matching_user.2C_and.2For_create_a_new_one">1.2.2 Find matching user, and/or create a new one</span></h5>
<p>This is specific to each web application, for MediaWiki you can refer to <a href="/wiki/WPD:Projects/SSO/MediaWikiExtension" title="WPD:Projects/SSO/MediaWikiExtension">WPD:Projects/SSO/MediaWikiExtension</a>.
</p>
<h5><span class="mw-headline" id="1.2.3_Start_a_session">1.2.3 Start a session</span></h5>
<p>This is specific to each web application, for MediaWiki you can refer to <a href="/wiki/WPD:Projects/SSO/MediaWikiExtension" title="WPD:Projects/SSO/MediaWikiExtension">WPD:Projects/SSO/MediaWikiExtension</a>.
</p>
<h5><span class="mw-headline" id="1.2.4_Return_an_HTTP_response">1.2.4 Return an HTTP response</span></h5>
<p>This step is required by the <a href="#JavaScript_shared_module:_Detect_and_start_automatically_a_session">#JavaScript shared module: Detect and start automatically a session</a> so it knows whether it should reload or not the page and let the user use the current site as an authenticated user.
</p>
<ul><li> <tt>204</tt>: All went fine, reload!</li>
<li> <tt>4xx</tt>: Stop there, no valid session was found</li>
<li> <tt>5xx</tt>: Stop there, an unexpected error happened</li></ul>
<p>If the status is not an error (e.g. 4xx, 5xx), we can send an error message in the response body with a <tt>Content-type: text/plain</tt> HTTP header.
</p>
<hr />
<p><br />
</p>
<h2><span class="mw-headline" id="SSO_and_remembering">SSO and remembering</span></h2>
<p>This step is meant to address the <b>Let each configured web applications to detect a session on the authority</b> workflow.
</p><p>As described in <a href="#Stories">#Stories</a>, the following describes how we can get the same data from <a href="#Read_user_data">#Read user data</a>, but without asking for the user to authenticate again.
</p><p>To have the system to not ask the user to authenticate again we needed to find a way to check if a session is opened, and get the user data so I can create a local session from that trusted source.
</p><p>Most of the following would happen at <a href="#3._Possibility:_Detected_a_session">#3. Possibility: Detected a session</a> then <a href="#Read_user_data">#Read user data</a> using a <a href="#JavaScript_shared_module:_Detect_and_start_automatically_a_session">#JavaScript shared module: Detect and start automatically a session</a> that handles the checks and makes the local web application to <a href="#Initialize_local_web_application_session">#Initialize local web application session</a> automatically for the user.
</p><p><br />
</p>
<h3><span class="mw-headline" id="0._Preamble_3">0. Preamble</span></h3>
<p>This is what’s currently implemented. Ideally it should leverage what’s proposed in the previous section. A high level description is available at <a href="/wiki/WPD:Projects/SSO/Login_Workflows#Starting_a_session_by_communicating_with_accounts_server" title="WPD:Projects/SSO/Login Workflows">WPD:Projects/SSO/Login Workflows#Starting a session by communicating with accounts server</a>
</p><p>While this implementation proposal is some sort of workaround, it is designed to provide the same data we would get if the issue <a href="/wiki/WPD:Projects/SSO/Improvements_roadmap#Leveraging_completely_OAuth2" title="WPD:Projects/SSO/Improvements roadmap">WPD:Projects/SSO/Improvements roadmap#Leveraging completely OAuth2</a>.
</p><p>In either case, we first need to discover whether a session is already opened using Content Security Policies and Cross Frame communication through a hidden iframe via JavaScript.
</p><p><b>Story</b>: A person signed in to work on testing a feature in the SSO enabled <a rel="nofollow" class="external text" href="http://docs.mroftalpbew.org/wiki/Main_Page">WebPlatform Docs Staging wiki</a> ("D"). Later in his browsing session, the user wants to add an comment to a <a rel="nofollow" class="external text" href="http://www.w3.org/2014/annotation/experiment/webaudio.html">W3C spec that supports annotations</a> ("B"). Without having to enter his credentials more than once.
</p><p>The workflow in this code proposal should be run before <a href="#4._From_a_page.2C_when_you_click_login">#4. From a page, when you click login</a>.
</p><p>The following is separated in two parts:
</p>
<ul><li> <a href="#JavaScript_shared_module:_Detect_and_start_automatically_a_session">#JavaScript shared module: Detect and start automatically a session</a></li>
<li> <a href="#Initialize_local_web_application_session">#Initialize local web application session</a></li></ul>
<h4><span class="mw-headline" id="1._Sign_in_to_.28.22D.22.29">1. Sign in to ("D")</span></h4>
<p>Continuing our scenario, let’s use the <a rel="nofollow" class="external text" href="http://docs.mroftalpbew.org/wiki/Main_Page">WebPlatform Docs Staging wiki</a> ("D")
</p><p>Complete signin in process through the accounts server (the OAuth way), and you should get back to the staging wiki with a session opened.
</p><p><b>NOTE</b>: Once you passed this step, you can see on the <a rel="nofollow" class="external text" href="https://accounts.webplatform.org/">accounts server</a> that it no loger prompts you to authenticate.
</p>
<h4><span class="mw-headline" id="2._Go_to_.28.22B.22.29.2C_another_web_app_that_also_uses_the_accounts_server">2. Go to ("B"), another web app that also uses the accounts server</span></h4>
<p>Continuing our scenario, we will want to add a comment on a <a rel="nofollow" class="external text" href="http://www.w3.org/2014/annotation/experiment/webaudio.html">W3C spec that supports annotations</a> ("B")
</p><p>The following JavaScript happen.
</p>
<h5><span class="mw-headline" id="2.1._From_B.2C_prepare_to_handle_confirmation">2.1. From B, prepare to handle confirmation</span></h5>
<p>This is where we listen to what we get from the accounts server, validate if a session exists, and trigger the calls to the profile server and handle the returned data.
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
window.addEventListener("message", function(returned){console.log(returned.data)}, false);
</pre>
<p><br />
NOTE: This is handled in file <a href="#JavaScript_shared_module:_Detect_and_start_automatically_a_session">#JavaScript shared module: Detect and start automatically a session</a>
</p>
<h5><span class="mw-headline" id="2.2._From_B.2C_open_a_iframe_to_.28.22C.22.29">2.2. From B, open a iframe to ("C")</span></h5>
<p>For this to work, we have to make sure that the Content server sends appropriate CSP headers on the FxA content server.
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
    // See 0.2
    app.use(helmet.csp({"script-src":["'self'", "*.webplatform.org", "*.mroftalpbew.org", "*.global.ssl.fastly.net", "*.w3.org"]}));
</pre>
<p><br />
Create the iframe
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
    var authChecker=document.createElement('iframe');authChecker.src='https://accounts.webplatform.org/';authChecker.frameworder=0;authChecker.width=0;authChecker.height=0;authChecker.id='authChecker';document.body.appendChild(authChecker);
</pre>
<p><br />
NOTE: This is handled in file <a href="#JavaScript_shared_module:_Detect_and_start_automatically_a_session">#JavaScript shared module: Detect and start automatically a session</a> at the 
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
window.sso.init(closure, '/wiki/Special:AccountsHandler/callback');
</pre>
<p><br />
</p>
<h5><span class="mw-headline" id="2.3._From_B.2C_Send_trigger_to_ask_confirmation_from_the_iframe">2.3. From B, Send trigger to ask confirmation from the iframe</span></h5>
<p>Since the iframe has reloaded fully the document and would behave the same as if the user went to <a rel="nofollow" class="external free" href="https://accounts.webplatform.org/">https://accounts.webplatform.org/</a> with an opened session, we can ask that iframe document to send us details of the session.
</p><p>To do so, we are sending a request for confirmation, like this:
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
authChecker.contentWindow.postMessage('hi', 'https://accounts.webplatform.org/');
</pre>
<p><br />
NOTE: This is handled in file <a href="#JavaScript_shared_module:_Detect_and_start_automatically_a_session">#JavaScript shared module: Detect and start automatically a session</a>. The trigger would be lauched from <tt>window.sso.doCheck()</tt> and handles the next steps until the backend comes in.
</p>
<h4><span class="mw-headline" id="3._From_B.2C_handle_the_response_from_the_iframe">3. From B, handle the response from the iframe</span></h4>
<p>Provided a session is already open, we should get something similar to:
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
{hasSession: true,
 recoveryPayload: "e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f"}
</pre>
<p><br />
If there is no session, or in case of failure, we would get:
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
{hasSession: false,
 recoveryPayload: null}
</pre>
<p><br />
Since the iframe and the communication would had failed from any non trusted source. If we are from a trusted source as described in 2.2, it is safe to assume that we are a legitimate relying party to the SSO system.
</p><p>This is where the non blocking <a href="#JavaScript_shared_module:_Detect_and_start_automatically_a_session">#JavaScript shared module: Detect and start automatically a session</a> finish its lifecycle.  Upon detecting an object that has <tt>hasSession: true</tt> AND a 64 character long string for <tt>sessionToken</tt>, it MUST send an Ajax POST to the local web application <tt>callbackUri</tt> with the token.
</p><p>NOTE: This is know to bring a problem. The isussue is that if we use an unaltered sessionToken as the sole proof, anybody could know this and hijack a session on the relying party. This needs to be improved.
</p>
<h4><span class="mw-headline" id="4._Read_data_from_the_profile_server_with_a_recoveryPayload">4. Read data from the profile server with a recoveryPayload</span></h4>
<p>The following happens at <a href="#Initialize_local_web_application_session">#Initialize local web application session</a>.
</p><p>This endpoint will be available ONLY through the internal network of WebPlatform and the W3C.
</p><p>Compared to a call with an OAuth Authorization token, we are going to call a different endpoint that will correlate the data attached to the user session.
</p><p>The special endpoint, only available through a limited set of IP address answers to <tt>/v1/session/recover</tt> and requires an "Authorization" header similar to OAuth, but with a Session token instead.
</p><p><br />
</p>
<pre class="language-bash" data-lang="bash">
curl -v -H 'Content-Type: application/json' \
        -H "Authorization: Session e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f" \
        'https://profile.accounts.webplatform.org/v1/session/recover'
</pre>
<p><br />
<i>NOTE</i> This endpoint is available at the moment but might not be accessible anymore by end of June 2014.
</p><p>Here are the HTTP Response body the endpoint would return:
</p>
<ul><li> 200 OK, with JSON object containing data when session exist (shown above)</li>
<li> 410 GONE, with error JSON object, when session doesn’t exist</li>
<li> 401 UNAUTHORIZED, with error JSON object, when request is malformed</li></ul>
<h5><span class="mw-headline" id="4.1._Under_the_hood">4.1. Under the hood</span></h5>
<p>Under the hood, the profile server endpoint at <tt>GET /v1/session/recover</tt> makes database queries similar to:
</p><p><br />
</p>
<pre class="language-mysql" data-lang="mysql">
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
</pre>
<p><br />
The database should either return an empty result, or user data:
</p>
<pre>   +----------------------------------+----------------+----------+--------------+
   | uid                              | email          | username | fullName     |
   +----------------------------------+----------------+----------+--------------+
   | 3E09D6DF843341BC921A25423AB83BAF | hi@example.org | jdoe     | John Doe     |
   +----------------------------------+----------------+----------+--------------+
</pre>
<h4><span class="mw-headline" id="5._Returning_the_data_to_the_server">5. Returning the data to the server</span></h4>
<p>If the web application could get a response from <tt>session/recover</tt>, and finds a result, it returns a JSON object:
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
  {"username": "jdoe",
   "fullName": "John Doe",
   "email": "hi@example.org",
   "uid": "3E09D6DF843341BC921A25423AB83BAF" }
</pre>
<p><br />
In the case of an invalid or expired <tt>sessionToken</tt>, an error should be returned. See possible errors at <a href="#4._Read_data_from_the_profile_server_with_a_recoveryPayload">#4. Read data from the profile server with a recoveryPayload</a>
</p><p>The rest MUST comply to what’s described in <a href="#Initialize_local_web_application_session">#Initialize local web application session</a>.
</p>
<hr />
<h2><span class="mw-headline" id="JavaScript_shared_module:_Detect_and_start_automatically_a_session">JavaScript shared module: Detect and start automatically a session</span></h2>
<p>This step is meant to address the <b>Detect automatically if there is a session in the accounts server, and start it automatically</b> workflow.
</p><p>It describes the behavior of a non blocking JavaScript module meant to detect and start automatically a session for the user.
</p><p>Client code is available in <a rel="nofollow" class="external text" href="https://gist.github.com/WebPlatformDocs/fe3149c60d6ed95c7e16">JavaScript SsoHandler class in this gist</a>
</p><p><br />
</p>
<h3><span class="mw-headline" id="1._Event_handler_to_validate_a_session">1. Event handler to validate a session</span></h3>
<p><b>NOTE</b>: This event handler is about answering what’s triggered bye the module and is installed in the accounts server code.
</p><p>In our own fork and branch of <tt>fxa-content-server</tt>, in <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-content-server/blob/webplatform-customizations/app/scripts/views/base.js">app/scripts/views/base.js</a>
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
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
</pre>
<p><br />
</p>
<h3><span class="mw-headline" id="2._And_adjust_the_CSP_policies">2. And adjust the CSP policies</span></h3>
<p><b>NOTE</b>: The Content Security Policy changes here is about letting the module to communicate with the accounts server.
</p><p>In our own fork and branch of <tt>fxa-content-server</tt>, in <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-content-server/blob/webplatform-customizations/server/bin/fxa-content-server.js">server/bin/fxa-content-server.js</a>
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
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
</pre>
<p><br />
</p>
<h3><span class="mw-headline" id="3._JavaScript_client_to_handle_automatic_sign_in">3. JavaScript client to handle automatic sign in</span></h3>
<p>This section describes what the module actually does.
</p>
<ul><li> Make sure it doesn't try to do things if local web app already has a session</li>
<li> Provide a way to tell whether it already has a session opened</li>
<li> Make sure it works without any external library; to be deployed on all SSO relying parties</li>
<li> Handle creation of iframe and the <tt>postMessage()</tt></li>
<li> Handle reply from cross-frame request</li>
<li> Cross-frame response, validate returned values has keys: <tt>[hasSession, sessionToken]</tt></li>
<li> Make async call to local web application callback through POST</li>
<li> If return response of local callback is successful, reload page</li></ul>
<p>It exposes two methods to the <tt>window.sso</tt> object:
</p>
<ul><li> <tt>window.sso.init(hasSessionClosure, localCallbackEndpoint);</tt> To initialize (see below)</li>
<li> <tt>window.sso.doCheck()</tt>, to bootstrap the process (should be done once the iframe is loaded).</li></ul>
<p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
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
</pre>
<p><br />
Once the iframe is loaded:
</p><p><br />
</p>
<pre class="language-javascript" data-lang="javascript">
window.sso.doCheck();
</pre>
<p><br />
<b>NOTE</b>: If we had a session, the communication triggered at <tt>window.sso.doCheck();</tt>, would had provided us the required data to start automatically and resume at <a href="#Initialize_local_web_application_session">#Initialize local web application session</a>.
</p>
<!-- 
NewPP limit report
CPU time usage: 0.135 seconds
Real time usage: 1.008 seconds
Preprocessor visited node count: 383/1000000
Preprocessor generated node count: 676/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:23263-0!*!0!!*!5!*!esi=1 and timestamp 20150810141208 and revision id 71179
 -->
