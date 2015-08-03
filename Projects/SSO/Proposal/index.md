---
title: WPD:Projects/SSO/Proposal
---
<h2><span class="mw-headline" id="Goals">Goals</span></h2>
<ul><li> Annotation on WPD by signing into MW</li>
<li> Annotation on specs, using WPD account, without a pop-up</li>
<li> Use same account on various WPD web applications (i.e. test wiki, issue tracker, blog, etc)</li></ul>
<h2><span class="mw-headline" id="Known_limitations">Known limitations</span></h2>
<ul><li>  Users who opt-in to third-party cookie blocking cannot log in from the sidebar if it is served from its own domain
<ul><li> Safari blocks third-party cookies by default</li></ul></li></ul>
<p>The hypothes.is Chrome extension requests permissions at install time to modify browser settings. Then it whitelists the Hypothes.is domain as a third-party cookie exception. This option is unavailable for the case of embedding the application directly.
</p>
<h2><span class="mw-headline" id="Possibilities">Possibilities</span></h2>
<h3><span class="mw-headline" id="WPD">WPD</span></h3>
<ol><li> No authentication UI in the sidebar. All authentication is done in MW. Hypothesis produces a plugin for the annotation sidebar which sniffs the MW authentication.</li></ol>
<h3><span class="mw-headline" id="Specs">Specs</span></h3>
<ol><li> Authentication in the sidebar against MW API. Requires domain to be www.w3.org</li>
<li> Authentication in the sidebar against FxA OAuth API*.</li></ol>
<p>The domain must be www.w3.org or the FxA OAuth server.
</p>
<h2><span class="mw-headline" id="Questions">Questions</span></h2>
<p>Can we add reverse proxy routes for /notes on www.w3.org and wpd such that the iframe is always same domain? Our backend has no trouble with being served from two domains at once. This would be the simplest route because it means we can leave authentication in the sidebar for specs.
</p><p>Example:
</p>
<ul><li> w3.org/notes</li>
<li> webplatform.org/notes</li></ul>
<h2><span class="mw-headline" id="Proposal">Proposal</span></h2>
<ul><li> Hypothesis develops MW authentication
<ul><li> Front end: sniff the MW auth (used for WPD)</li>
<li> Back end: username/password auth against MW API (used for specs)</li></ul></li>
<li> W3C continues to roll out FxA</li>
<li> We choose a hard stop date. If FxA is deployed by then, Hypothesis develops a back end which authentications username/password against FxA.</li></ul>
<p><b>We will have pop-ups</b> on spec pages unless we put Hypothesis and MW (or FxA) on the same domain. Switching to FxA/OAuth does not change this.
</p>
<h2><span class="mw-headline" id="Estimates">Estimates</span></h2>
<ul><li> <b>MediaWiki front-end authentication sniffing:</b> 1-2 days</li>
<li> <b>MediaWiki back-end authentication interop:</b> 1-2 days</li>
<li> <b>FxA back-end authentication interop:</b> 2-3 days</li>
<li> <b>FxA roll-out:</b>&#160;????? (Renoir?)</li></ul>
<p>I propose a hard stop for FxA roll-out at Monday, May 26th. That gives Hypothesis the next week to focus intensely on IE11 support and a solid week for authentication work against either FxA or MW, with a few days left over for testing the deployment and time dilation.
</p>
<!-- 
NewPP limit report
CPU time usage: 0.013 seconds
Real time usage: 0.014 seconds
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

<!-- Saved in parser cache with key wpwiki:pcache:idhash:22187-0!*!*!!*!*!*!esi=1 and timestamp 20150731111128 and revision id 57253
 -->
