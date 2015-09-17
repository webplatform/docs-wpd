---
title: 'WordPress plugin'
uri: 'WPD:Projects/SSO/WordPressPlugin'

---
Not done yet. Taking notes.

# To do

-   Detect login, and send to accounts RP frontend
-   Detect return from RP with two GET parms state, code to get Bearer token
-   How to find user, Create one if inexistent
-   How to start a session

# Tests

## On login attempt, send to RP

-   [login\_head hook](http://adambrown.info/p/wp_hooks/hook/login_head?version=3.9&file=wp-login.php)

``` html
add_action( 'login_head', 'prout' );
function prout( )
{
  header('Location: https://accounts.webplatform.org/oauth/signin');
}
```

## Unsorted pointers

-   [wp\_set\_auth\_cookie](http://codex.wordpress.org/Function_Reference/wp_set_auth_cookie)
-   [set\_current\_user hoook](http://core.trac.wordpress.org/browser/tags/3.9.1/src/wp-includes/pluggable.php#L0)
-   <http://wordpress.stackexchange.com/questions/83985/auto-log-in-hook-is-requiring-a-page-refresh>
-   <https://codex.wordpress.org/Plugin_API/Action_Reference>
