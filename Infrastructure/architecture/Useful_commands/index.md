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

=== Create a database, a user, and set privileges ===

Since our site runs on existing databases our states don’t affect the database servers directly.

But if it happens that its been decided to change database details.

In this example, we’ll  create a new database for our WordPress blog instance and we’ll focus on the commands to issue using salt, where to change the configuration and what will make the webapp to have the new settings applied.


* Create a new database

  salt -G 'roles:masterdb' mysql.db_create wpblog utf8 utf8_general_ci

* Add a new database user and privileges

  salt -G 'roles:masterdb' mysql.user_create user_blog '%' somepassword
  salt -G 'roles:masterdb' mysql.grant_add 'ALL' 'wpblog.*' 'user_blog' '%'

* Check if the secondary database replication servers are in good state

  salt -G 'roles:db' mysql.get_slave_status

The following details of the output means "''all is OK!''"

    Seconds_Behind_Master:
        0
    Slave_IO_Running:
        Yes
    Slave_IO_State:
        Waiting for master to send event
    Slave_SQL_Running:
        Yes

* Check if Monit says the database servers are fine too. If everything says "''running''" its all great!

  salt -G 'roles:db' monit.summary
  db2:
    ----------
    Process:
        ----------
        exim4:
            Running
        mysql:
            Running
        openssh-server:
            Running
        salt-minion:
            Running
    System:
        ----------
        db2.production.wpdn:
            Running
  db1-masterdb:
    ----------
    Process:
        ----------
        exim4:
            Running
        mysql:
            Running
        openssh-server:
            Running
        salt-minion:
            Running
    System:
        ----------
        db1-masterdb.production.wpdn:
            Running

* Import the previous database snapshot
** ''scp'' the database backup file to the current '''masterdb''' VM
** import the database into the server (e.g. '''mysql wpblog < wpblog.sql''')
** the other VMs with the role db (the ones that doesn’t have "masterdb" in their name) should catch up automatically with the replication
* Change the database details you just created in the pillar file. If the command was run from production, the file to change would be '''/srv/private/pillars/accounts/production.sls'''

* Make the configuration file to be applied on top of the web app configuration

  wpd-deploy blog