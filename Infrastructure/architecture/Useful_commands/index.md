{{:WPD:Infrastructure/architecture}}
= Useful commands =

A few salt commands listed by their use.

Most of the commands should be done through the salt states in ''/srv/salt'', but sometimes we have no choice but to act quickly.


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