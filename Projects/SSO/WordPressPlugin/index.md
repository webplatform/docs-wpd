= WordPress plugin =

Not done yet. Taking notes.

See the following hooks:
* [https://github.com/WordPress/WordPress/blob/master/wp-login.php#L37 login_head]

= To do =

== On login attempt, send to RP ==
http://adambrown.info/p/wp_hooks/hook/login_head?version=3.9&file=wp-login.php
<syntaxhighlight>
add_action( 'login_head', 'prout' );
function prout( )
{
  header('Location: https://accounts.webplatform.org/oauth/signin');
}
</syntaxhighlight>

== Handle if user exists, create if needed, start session ==

* [http://core.trac.wordpress.org/browser/tags/3.9.1/src/wp-includes/pluggable.php#L0 
* hook set_current_user
* http://wordpress.stackexchange.com/questions/83985/auto-log-in-hook-is-requiring-a-page-refresh