{{:WPD:Infrastructure/architecture}}
= Useful commands =

A few salt commands listed by their use.

Most of the commands should be done through the salt states in ''/srv/salt'', but sometimes we have no choice but to act quickly.


== Using salt from ==

=== Remove a file ===

  salt \* file.remove /etc/monit/conf.d/exim4.conf

=== Remove a user ===

  salt \* user.delete foobar remove=True force=True


=== Replace a line in a config file ===

  salt app\* file.replace /etc/php5/apache2/php.ini pattern='expose_php = On' repl='expose_php = Off'

=== Reload a service ===

  salt app\* service.reload apache2

=== Create a database, a user, and set privileges ===

Since our site runs on existing databases our states don’t affect the database servers directly.

But if it happens that its been decided to change database details.

In this example, we’ll  create a new database for our WordPress blog instance and we’ll focus on the commands to issue using salt, where to change the configuration and what will make the webapp to have the new settings applied.


* Create a new database

  salt -G 'roles:masterdb' mysql.db_create wpblog utf8 utf8_general_ci

* Import the backup

  // scp the database backup to the current masterdb VM
  // ... import using MySQL to the new VM
  // ... other VMs with the role db should catch up automatically with the replication

* Add database user and privileges

  salt -G 'roles:masterdb' mysql.user_create user_blog '%' somepassword
  salt -G 'roles:masterdb' mysql.grant_add 'ALL' 'wpblog.*' 'user_blog' '%'

* Change the database details you just created in the pillar file. If the command was run from production, the file to change would be '''/srv/private/pillars/accounts/production.sls'''

* Make the configuration file to be applied on top of the web app configuration

  wpd-deploy blog