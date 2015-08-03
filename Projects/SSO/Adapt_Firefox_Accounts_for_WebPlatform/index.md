---
title: WPD:Projects/SSO/Adapt Firefox Accounts for WebPlatform
---
<h1><span class="mw-headline" id="Adapt_Firefox_Accounts_for_WebPlatform">Adapt Firefox Accounts for WebPlatform</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>Firefox Accounts ("FxA") is an Identity Provider system made by Mozilla that has been rolled out with Firefox 29 released in May 2014. It will eventually be the centerpiece for their Marketplace and other services, the first components are about authentication, and to serve as a Resource Provider.
</p><p>WebPlatform is using its own fork of FxA to serve as a SSO and this document describes the changes that has been made to it.
</p>
<h2><span class="mw-headline" id="What_is_Firefox_Accounts.2C_and_why.3F">What is Firefox Accounts, and why?</span></h2>
<p>The choice of using FxA for our authentication service is due to our interest to limit our technology stack as much as its sane to do so. But FxA also supports other requirements we have, such as:
</p>
<ul><li> Use of JavaScript/NodeJS</li>
<li> Supports multiple languages</li>
<li> Maintained by an active community who also happens to be <a rel="nofollow" class="external text" href="http://www.webplatform.org/stewards/mozilla">one of our Stewards, Mozilla</a></li></ul>
<p>FxA provides has a set of loosely coupled components. Namely, a <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-js-client">JavaScript client ("fxa-js-client")</a>, a <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-content-server">Content server ("fxa-content-server")</a> that’s taking care of the Web UI but also email templates. The Content server also <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-content-server-l10n">supports Localization ("fxa-content-server-l10n")</a> allowing us to support multi-lingual content. In the backend side, FxA exposes <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-auth-server">an API ("fxa-auth-server")</a>, and last but not least, an <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-oauth-server">OAuth2 resource provider ("fxa-oauth-server")</a>.
</p><p>Our use of FxA will be limited to a minimum to suit our needs. In the future, we might consider using other components managed by the FxA community, such as:  <a rel="nofollow" class="external text" href="https://github.com/mozilla/fxa-customs-server">customs-server</a> that’s taking care to validate emails, manage bounces and help prevent spam, and also <a rel="nofollow" class="external text" href="https://github.com/mozilla/fxa-auth-db-server">auth-db-server</a> that will provide a REST/HTTP frontend to the database servers, and many other components available on <a rel="nofollow" class="external text" href="https://github.com/mozilla?query=fxa-">their GitHub projects</a>.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Components">Components</span></h2>
<p>We forked the following components based on recommended version/tags from the Mozilla fxa team.
</p>
<ul><li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-content-server">fxa-content-server</a>, using branch master</li>
<li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-content-server-l10n">fxa-content-server-l10n</a>, adjusting content based off of the same branch as fxa-content-server</li>
<li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-js-client">fxa-js-client</a>, that is installed within fxa-content-server via the bower.json file</li>
<li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-auth-server">fxa-auth-server</a>, branch webplatform-customizations</li>
<li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-oauth-server">fxa-oauth-server</a></li></ul>
<h2><span class="mw-headline" id="Changes">Changes</span></h2>
<h3><span class="mw-headline" id="Accept_username_field.2C_and_allow_to_force_creation_date">Accept username field, and allow to force creation date</span></h3>
<ol><li> Accept two fields [username, fullName] and allow forcing createdAt
<ol><li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-auth-server/issues/1">fxa-auth-server issue #1</a>, patch <a href="/wiki/File:fxa-auth-server-patch-0001-Adressing-1-for-fxa-auth-server.txt" title="File:fxa-auth-server-patch-0001-Adressing-1-for-fxa-auth-server.txt">File:fxa-auth-server-patch-0001-Adressing-1-for-fxa-auth-server.txt</a></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-js-client/issues/1">fxa-js-client issue #1</a></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-content-server/issues/1">fxa-content-server issue #1</a></li></ol></li></ol>
<p><br />
</p>
<h3><span class="mw-headline" id="On_login.2C_also_support_using_username_instead_of_email">On login, also support using username instead of email</span></h3>
<p><b>Status: In analysis</b>
</p><p>The idea is that we would like to not change behavior for users when they login with their username. 
</p><p><b>Limitations</b>
</p>
<ul><li> we do not want to change FxA too much (i.e. not break updates).</li>
<li> since the <a rel="nofollow" class="external text" href="https://github.com/mozilla/fxa-auth-server/wiki/onepw-protocol#login-obtaining-the-sessiontoken">way to validate user uses cryptography based on the email</a>, we cannot just fake emails in the field, we will need it at many places such as confirming the user email and it would be a too big change</li></ul>
<p><br />
<b>Proposed solution</b>
</p><p>Since we already implemented to accept username in <a href="#Accept_username_field.2C_and_allow_to_force_creation_date">#Accept username field, and allow to force creation date</a>, we can create a set of API mirroring the original, but to find by username.
</p><p>What we can do:
</p>
<ul><li> Create a distinct:
<ul><li> login screen in content-server (e.g. /signin2) that shows username+password fields</li>
<li> login API endpoint to api-server to accept those two fields</li>
<li> Adjust API endpoint to use a different SELECT query to find user to make crypto checks. i.e. will continue as usual, but instead of searching user entry in database by provided email, we will allow to use username.</li></ul></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.029 seconds
Real time usage: 0.047 seconds
Preprocessor visited node count: 26/1000000
Preprocessor generated node count: 32/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:22335-0!*!*!!*!5!*!esi=1 and timestamp 20150731111118 and revision id 56080
 -->
