= WordPress plugin =

Not done yet. Taking notes.

See the following hooks:
* [https://github.com/WordPress/WordPress/blob/master/wp-login.php#L37 login_head]

= To do =

* Detect login, and send to accounts RP frontend
* Detect return from RP with two GET parms state, code to get Bearer token
* How to find user, Create one if inexistent
* How to start a session

= Tests =

== On login attempt, send to RP ==

* [http://adambrown.info/p/wp_hooks/hook/login_head?version=3.9&file=wp-login.php login_head hook]

<syntaxhighlight>
add_action( 'login_head', 'prout' );
function prout( )
{
  header('Location: https://accounts.webplatform.org/oauth/signin');
}
</syntaxhighlight>

== Unsorted pointers ==

* http://codex.wordpress.org/Function_Reference/wp_set_auth_cookie
* [http://core.trac.wordpress.org/browser/tags/3.9.1/src/wp-includes/pluggable.php#L0  set_current_user hoook]
* http://wordpress.stackexchange.com/questions/83985/auto-log-in-hook-is-requiring-a-page-refresh
* https://codex.wordpress.org/Plugin_API/Action_Reference