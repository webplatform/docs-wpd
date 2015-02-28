{{:WPD:Infrastructure/architecture}}
= Create new database credentials and configure a web application to use it =

The concept of states are ideal to manage many aspects of a running system. But one of the "gray zones" are about database credentials, or whether or not we should send commands to set database credentials at every deployment system "apply configuration" run. For this reason we do not enforce them in the salt states.
 
But what if we want to change the database details? Here’s how.

In this example, we’ll  create a new database for our WordPress blog instance, import an existing snapshot and apply the new database configuration and deploy it. In this tutorial we will focus solely on the use of the deployment system ("salt stack") and the deployment itself.

== Procedure ==

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
  Going to update roles for:
  blog:
     - blog
  Deploying...
  blog:
    Name: rsync -a --delete --no-perms --password-file=/etc/codesync.secret codesync@salt::code/packages/apt/ /srv/webplatform/apt/ - Function: cmd.run - Result: Changed
    Name: rsync -a --delete --no-perms --password-file=/etc/codesync.secret codesync@salt::code/www/repo/out/errors/ /srv/webplatform/errors/ - Function: cmd.run
   - Result: Changed
    Name: rsync -a  --exclude '.git' --no-perms --password-file=/etc/codesync.secret codesync@salt::code/blog/repo/ /srv/webplatform/blog/ - Function: cmd.run - Result: Changed
    Name: /srv/webplatform/blog - Function: file.directory - Result: Changed
    Name: /srv/webplatform/blog/local.php - Function: file.managed - Result: Changed
    Name: rsync -a --delete --no-perms --password-file=/etc/codesync.secret codesync@salt::code/packages/certificates/production/ /etc/ssl/webplatform/ - Function: cmd.run - Result: Changed
    Name: /etc/ssl/webplatform - Function: file.directory - Result: Changed
    Name: /var/www - Function: file.directory - Result: Changed
  
  Summary
  ------------
  Succeeded: 8 (changed=8)
  Failed:    0
  ------------
  Total states run:     8

* Last step is to apply ''state.highstate''

  salt blog state.highstate