---
title: WPD:Projects/SSO/Login Workflows
---
<h1><span class="mw-headline" id="Login_workflows">Login workflows</span></h1>
<p>Both of these scenarios assume that the Annotator sidebar is loaded on the target page load via an explicit script reference; both use the same instance of Hypothes.is Annotator, hosted on WebPlatform.org (specifically, notes.webplatform.org).
</p>
<h2><span class="mw-headline" id="User_facing">User facing</span></h2>
<h3><span class="mw-headline" id="WebPlatform.org">WebPlatform.org</span></h3>
<ol><li> User arrives on content page <i>X</i> on WebPlatform.org
<ul><li> User wishes to edit or annotate page</li></ul></li>
<li> User clicks login link
<ul><li> Main login link on top of wiki page</li>
<li> Optional login link in Annotator sidebar</li></ul></li>
<li> User navigated to login page on WebPlatform.org (accounts.webplatform.org, using FxA)</li>
<li> User logs in via FxA</li>
<li> User redirected back to content page <i>X</i></li>
<li> MediaWiki and Annotator both reloaded with user logged in via authentication token 
<ul><li> Option 1: MediaWiki and Annotator both use token from FxA</li>
<li> Option 2: MediaWiki uses token from FxA, and Annotator uses token from MediaWiki</li></ul></li>
<li> User now able to edit wiki or leave annotation</li></ol>
<p>No popup needed?
</p><p><br />
</p>
<h3><span class="mw-headline" id="W3C_Specs">W3C Specs</span></h3>
<ol><li> User arrives on specification page <i>Y</i> on W3.org
<ul><li> User wishes to annotate specification</li></ul></li>
<li> User clicks login link in Annotator sidebar</li>
<li> User logs in with WebPlatform.org account through the Annotator sidebar
<ul><li> If browser has cross-site cookies enabled, user logs in directly in sidebar </li>
<li> If browser does not have cross-site cookies enabled, user logs in via a pop-up dialog</li></ul></li>
<li> Annotator sidebar obtains authentication token from accounts.webplatform.org, using FxA</li>
<li> Sidebar reloaded?</li>
<li> User now able to annotate specification page <i>Y</i></li></ol>
<p>Popup may be needed?
</p>
<h2><span class="mw-headline" id="How_the_code_has_to_behave">How the code has to behave</span></h2>
<h3><span class="mw-headline" id="Functionnal_workflows">Functionnal workflows</span></h3>
<p>Those are the functional requirements to enable SSO. Each workflow is detailed in <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it</a>
</p><p>In order to fulfill the given <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#Stories" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#Stories</a> and workflows, we needed to implement a SSO solution covers the following:
</p>
<ul><li> Get authenticated through a single authority (see <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#Delegating_authentication" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#Delegating authentication</a>)</li>
<li> <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#Read_user_data" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#Read user data</a> from an API, </li>
<li> Let each configured web applications to detect a session on the authority (see <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#SSO and remembering</a>)</li>
<li> handle their local users and session (see <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#Initialize_local_web_application_session" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#Initialize local web application session</a>), and</li>
<li> Detect automatically if there is a session in the accounts server, and start it automatically (see [[<a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#JavaScript_shared_module:_Detect_and_start_automatically_a_session" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#JavaScript shared module: Detect and start automatically a session</a>)</li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="Starting_a_session_by_communicating_with_accounts_server">Starting a session by communicating with accounts server</span></h3>
<p>This section covers what the <i>front-end</i> does to detect if a session is opened on the accounts server. To see the <i>back-end</i> part, refer to <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#1.2_Possibility:_Resuming_a_session_confirmed_by_the_accounts_server" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#1.2 Possibility: Resuming a session confirmed by the accounts server</a>, detailed in the section <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#SSO and remembering</a>
</p>
<ul><li> In the accounts server:
<ul><li> Accept framing (i.e. accept to create iframe from other domain names that we control) through appropriate CSP policies.</li>
<li> Create an event handler that replies with a JSON object that reads the sessionToken in current localStorage. (Note that in the returned object, we rename the key <i>sessionToken</i> to <i>recoveryPayload</i>) (e.g. <tt>{recoveryPayload: "e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f", hasSession: true}</tt>)</li></ul></li>
<li> Through JavaScript, on a web application relying on the SSO (details in <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#JavaScript_shared_module:_Detect_and_start_automatically_a_session" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#JavaScript shared module: Detect and start automatically a session</a>):
<ul><li> Check if web application has a session locally, if not, continue</li>
<li> Create a communication channel as an hidden iframe, if the accounts server doesn’t forbid due to CSP policy, continue.</li>
<li> Use <tt>postMessage</tt> to communicate through the iframe opened to the accounts server</li>
<li> Handle response from <tt>postMessage</tt>, use the returned data (i.e. <tt>sessionToken</tt> value) into a POST body member called "recoveryPayload"</li>
<li> Make a <tt>POST</tt> request to the current web app callback (e.g. <tt>/wiki/Special:AccountsHandler/callback</tt>) with "recoveryPayload"</li></ul></li>
<li> In the backend code (details in <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#Initialize_local_web_application_session" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#Initialize local web application session</a>):
<ul><li> Accept <tt>POST</tt> requests with a "recoveryPayload" parameter, make sure it’s 64 hexadecimal characters.</li>
<li> Rename the "recoveryPayload" as "sessionToken"</li>
<li> Make an off-the-band call over SSL to the profile server</li>
<li> Read a JSON object with the user data</li>
<li> Create a session without further validation</li>
<li> Return an HTTP status code: <tt>204</tt> if it worked, <tt>4xx</tt> if it didn’t, <tt>5xx</tt> if an unexpected backend error happened. (see <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#1.2.4_Return_an_HTTP_response" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#1.2.4 Return an HTTP response</a>)</li></ul></li></ul>
<p><b>NOTE</b>: This workflow is subject to change, the details is described in <a href="/wiki/WPD:Projects/SSO/Improvements_roadmap#Recovering_session_data" title="WPD:Projects/SSO/Improvements roadmap">WPD:Projects/SSO/Improvements roadmap#Recovering session data</a>.
</p>
<h2><span class="mw-headline" id="Reference">Reference</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="http://www.whatcodecraves.com/posts/2012/01/11/backbonejs-sessions-and-authentication">Sessions and authentication</a> describes how a session works, you can ignore what is specific to backbone.</li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.024 seconds
Real time usage: 0.026 seconds
Preprocessor visited node count: 30/1000000
Preprocessor generated node count: 36/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:22138-0!*!0!!*!*!*!esi=1 and timestamp 20150731111124 and revision id 63422
 -->
