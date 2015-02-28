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

* Make the configuration file to be applied on top of the web app configuration. 

  wpd-deploy blog

It should look like in this image, with all "green", but of course with the mention of "blog" instead of "app".

[[File:Running_wpd-deploy.png]]

* Last step is to apply ''state.highstate''. Its OK to run it more than once, the configuration are written to enforce a state and can be applied in any order, the important is to get all "green".

  salt blog state.highstate