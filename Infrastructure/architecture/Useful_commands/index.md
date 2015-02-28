{{:WPD:Infrastructure/architecture}}
= Useful commands =

A few "one off" commands using salt stack listed by their potential use.

Maintenance should be done through the state system. But sometimes we still need "one off" commands on servers themselves and it would be creating cruft to have them in the state scripts.

== Using salt from the ''salt master'' ==

Since everything should be managed through salt, but we are in a situation where we might not want to change the states, we can do the following commands.

=== Remove a file ===

  salt \* file.remove /etc/monit/conf.d/exim4.conf

=== Remove a user ===

  salt \* user.delete foobar remove=True force=True


=== Replace a line in a config file ===

  salt app\* file.replace /etc/php5/apache2/php.ini pattern='expose_php = On' repl='expose_php = Off'

=== Reload a service ===

  salt app\* service.reload apache2