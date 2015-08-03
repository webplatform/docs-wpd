---
title: WPD:Projects/SSO/WordPressPlugin
---
<h1><span class="mw-headline" id="WordPress_plugin">WordPress plugin</span></h1>
<p>Not done yet. Taking notes.
</p><p><br />
</p>
<h1><span class="mw-headline" id="To_do">To do</span></h1>
<ul><li> Detect login, and send to accounts RP frontend</li>
<li> Detect return from RP with two GET parms state, code to get Bearer token</li>
<li> How to find user, Create one if inexistent</li>
<li> How to start a session</li></ul>
<p><br />
</p>
<h1><span class="mw-headline" id="Tests">Tests</span></h1>
<h2><span class="mw-headline" id="On_login_attempt.2C_send_to_RP">On login attempt, send to RP</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="http://adambrown.info/p/wp_hooks/hook/login_head?version=3.9&amp;file=wp-login.php">login_head hook</a></li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">add_action( 'login_head', 'prout' );
function prout( )
{
  header('Location: https://accounts.webplatform.org/oauth/signin');
}</pre></div></div>
<p><br />
</p>
<h2><span class="mw-headline" id="Unsorted_pointers">Unsorted pointers</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="http://codex.wordpress.org/Function_Reference/wp_set_auth_cookie">wp_set_auth_cookie</a></li>
<li> <a rel="nofollow" class="external text" href="http://core.trac.wordpress.org/browser/tags/3.9.1/src/wp-includes/pluggable.php#L0">set_current_user hoook</a></li>
<li> <a rel="nofollow" class="external free" href="http://wordpress.stackexchange.com/questions/83985/auto-log-in-hook-is-requiring-a-page-refresh">http://wordpress.stackexchange.com/questions/83985/auto-log-in-hook-is-requiring-a-page-refresh</a></li>
<li> <a rel="nofollow" class="external free" href="https://codex.wordpress.org/Plugin_API/Action_Reference">https://codex.wordpress.org/Plugin_API/Action_Reference</a></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.015 seconds
Real time usage: 0.015 seconds
Preprocessor visited node count: 27/1000000
Preprocessor generated node count: 44/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:23024-0!*!*!!*!*!*!esi=1 and timestamp 20150731111130 and revision id 55811
 -->
