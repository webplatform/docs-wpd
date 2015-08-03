---
title: WPD:Projects/SSO/Improvements roadmap
---
<h1><span class="mw-headline" id="Improvements_roadmap">Improvements roadmap</span></h1>
<p>The steps described in <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it</a> can be improved, this page describes some proposals.
</p>
<h2><span class="mw-headline" id="Recovering_session_data">Recovering session data</span></h2>
<p>This change proposal is about making sure the exchanged information is encoded in ways that only the intended audience can use.
</p>
<h3><span class="mw-headline" id="Problem_in_the_original_steps">Problem in the original steps</span></h3>
<p>ANYBODY who got access to a sessionToken, could become that user. And that is as long as the victim keeps his session opened on the accounts server. Because there is no way to validate if the request is made from the legitimate user.
</p><p>This security issue is no different than any web application that doesn’t use SSL. After all, the way a web server has to differentiate a visitor from another is basically a set of cookies, one of them serves as a session token.
</p><p>One obvious solution is to have SSL across the whole site, but its not always possible. We cannot force the user to go back and forth from SSL if they are OK without it. But we cannot leave such powerful data without encoding it either.
</p>
<h3><span class="mw-headline" id="Proposed_solution_steps">Proposed solution steps</span></h3>
<p>To solve the possible exploit, let’s revisit the original steps described in <a href="/wiki/WPD:Projects/SSO/Login_Workflows#Starting_a_session_by_communicating_with_accounts_server" title="WPD:Projects/SSO/Login Workflows">WPD:Projects/SSO/Login Workflows#Starting a session by communicating with accounts server</a>. Differences are shown in <b>bold</b>, removed steps has been <s>crossed out</s>.
</p>
<ul><li> In the accounts server:
<ul><li> <b>Add a wrapper within FxA server node processes (i.e. not possible to call from the browser), make sure the wrapper module isn’t going to be publicly available (e.g. in a secret project in Gerrit), to manage the encoding</b> (#TODO)</li>
<li> <b>Encode the sessionToken in some way with a shared secret key (e.g. using AES)</b></li>
<li> <b>Save the encoded sessionToken in a LocalStorage variable "<tt>recoveryPayload</tt>", but instead of a 64 characters long HEX string, <tt>recoveryPayload</tt> will a JSON object (e.g. <tt>{recoveryPayload: {packet: "...", cipherId: 1}}</tt>)</b></li>
<li> Accept framing (i.e. accept to create iframe from other domain names that we control) through appropriate CSP policies.</li>
<li> <s>Create an event handler that replies with a JSON object that reads the sessionToken in current localStorage. (Note that in the returned object, we rename the key <i>sessionToken</i> to <i>recoveryPayload</i>) (e.g. <tt>{recoveryPayload: "e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f", hasSession: true}</tt>)</s></li>
<li> <b>Create an event handler that replies with a JSON object that reads the current <tt>recoveryPayload</tt> value in localStorage. </b></li></ul></li>
<li> Through JavaScript, on a web application relying on the SSO (details in <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#JavaScript_shared_module:_Detect_and_start_automatically_a_session" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#JavaScript shared module: Detect and start automatically a session</a>):
<ul><li> Check if web application has a session locally, if not, continue</li>
<li> Create a communication channel as an hidden iframe, if the accounts server doesn’t forbid due to CSP policy, continue.</li>
<li> Use <tt>postMessage</tt> to communicate through the iframe opened to the accounts server</li>
<li> Handle response from <tt>postMessage</tt>, use the returned data (i.e. <s><tt>sessionToken</tt></s> <b><tt>recoveryPayload</tt></b> value) into a POST body member called "recoveryPayload"</li>
<li> Make a <tt>POST</tt> request to the current web app callback (e.g. <tt>/wiki/Special:AccountsHandler/callback</tt>) with  "recoveryPayload" <b>that has to get url encoded</b></li></ul></li>
<li> In the backend code (details in <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#Initialize_local_web_application_session" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#Initialize local web application session</a>):
<ul><li> Accept <tt>POST</tt> requests with a "recoveryPayload" parameter<s>, make sure it’s 64 hexadecimal characters</s></li>
<li> <s>Rename the "recoveryPayload" as "sessionToken"</s></li>
<li> <b>Decode the urlencoded "recoveryPayload" blob, then unpack the data using the shared secret key. If the payload makes any sense, has a property called "sessionToken", continue</b></li>
<li> <b>If the sessionToken property is 64 hexadecimal characters, use it for the next step</b></li>
<li> Make an off-the-band call over SSL to the profile server</li>
<li> Read a JSON object with the user data</li>
<li> Create a session without further validation</li>
<li> Return an HTTP status code: <tt>204</tt> if it worked, <tt>4xx</tt> if it didn’t, <tt>5xx</tt> if an unexpected backend error happened. (see <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#1.2.4_Return_an_HTTP_response" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#1.2.4 Return an HTTP response</a>)</li></ul></li></ul>
<p><b>Pros</b>:
</p>
<ul><li> Only the encoded packet will be communicated across frames</li>
<li> If a relying party doesn’t use SSL, the data will need to be decoded to be useful</li>
<li> Whether or not the session had a "man in the middle", the attacker will
<ul><li> The used crypto cipher is not explicitly communicated in the process, only a "cypherId" number </li>
<li> Still need to get the secret key  —that is NEVER communicated in the process— to unpack the encoded "recoveryPayload" contents.</li>
<li> not get a chance to get anything useful from the JavaScript call to the call back GET parameters</li></ul></li>
<li> Each backend application will have to unpack the recoveryPayload, validate if it makes sense BEFORE communicating with the profile.accounts.webplatform.org endpoint.</li></ul>
<p><b>What we could add on top of it</b>:
</p>
<ul><li> Sign the response from the profile server using JWT format, see <a rel="nofollow" class="external text" href="https://github.com/mozilla/jwcrypto">jwcrypto</a></li>
<li> Validate on the backend whether the response from the profile server is valid</li>
<li> Have SSL everywhere</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Leveraging_completely_OAuth2">Leveraging completely OAuth2</span></h2>
<p>The current implementation described at <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#SSO and remembering</a> doesn’t use OAuth2 token in all communications. While the original design of Firefox Accounts OAuth server was to remember if a user previously authenticated, that functionality is not implemented yet.
</p><p>The issue is known and documented <a rel="nofollow" class="external text" href="https://github.com/mozilla/fxa-content-server/issues/1195">in their GitHub issue tracker #1195</a>.
</p><p>In the eventuality of the Firefox Accounts OAuth server changes its behavior, we still need a non-blocking <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it#JavaScript_shared_module:_Detect_and_start_automatically_a_session" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How we implemented it#JavaScript shared module: Detect and start automatically a session</a> to check whether a session is already opened.
</p>
<h3><span class="mw-headline" id="Proposed_solution">Proposed solution</span></h3>
<p>TBD
</p>
<!-- 
NewPP limit report
CPU time usage: 0.024 seconds
Real time usage: 0.026 seconds
Preprocessor visited node count: 22/1000000
Preprocessor generated node count: 28/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:25204-0!*!0!!*!*!*!esi=1 and timestamp 20150731111123 and revision id 58885
 -->
