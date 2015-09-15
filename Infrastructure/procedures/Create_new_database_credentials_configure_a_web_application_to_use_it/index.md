---
title: Create new database credentials and configure a web application to use it
uri: 'WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it'

---
### <span>[WebPlatform server Infrastructure architecture menu](/WPD:Infrastructure/architecture)</span>

-   [Base configuration of a VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM)
-   [Reports to review status](/WPD:Infrastructure/architecture/Reports_to_review_status)
-   [Roles and environment level](/WPD:Infrastructure/architecture/Roles_and_environment_level)
-   [SSL certificates](/WPD:Infrastructure/architecture/SSL_certificates)
-   [The salt master](/WPD:Infrastructure/architecture/The_salt_master)
-   [Things to consider when we expose service via Fastly and Varnish](/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish)
-   [Useful commands](/WPD:Infrastructure/architecture/Useful_commands)
-   [VM roles](/WPD:Infrastructure/architecture/VM_roles)

**See also**

-   [Deploying code changes](/WPD:Infrastructure/procedures/Deploying_code_changes)
-   [Replacing a VM](/WPD:Infrastructure/procedures/Replacing_a_VM)
-   [Maintaining Fastly configuration](/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration)
-   [Managing MySQL replication](/WPD:Infrastructure/procedures/Managing_MySQL_replication)
-   **Create new database credentials and configure a web application to use it**
-   [Maintaining ElasticSearch cluster](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster)
-   [Maintaining email services](/WPD:Infrastructure/procedures/Maintaining_email_services)

... or **"How to change database configuration and ensure every affected web application gets the new passswords"**.

The concept of states are ideal to manage many aspects of a running system. But one of the "gray zones" are about database credentials, or whether or not we should send commands to set database credentials at every deployment system "apply configuration" run. For this reason we do not enforce them in the salt states.

But what if we want to change the database details? Here’s how.

In this example, we’ll create a new database for our WordPress blog instance, import an existing snapshot and apply the new database configuration and deploy it. In this tutorial we will focus solely on the use of the deployment system ("salt stack") and the deployment itself.

## <span>Procedure</span>

-   Create a new database

<!-- -->

     salt -G 'roles:masterdb' mysql.db_create wpblog utf8 utf8_general_ci

-   Add a new database user and privileges

<!-- -->

     salt -G 'roles:masterdb' mysql.user_create user_blog '%' somepassword
     salt -G 'roles:masterdb' mysql.grant_add 'ALL' 'wpblog.*' 'user_blog' '%'

-   Check if the secondary database replication servers are in good state

<!-- -->

     salt -G 'roles:db' mysql.get_slave_status

The following details of the output means "*all is OK!*"

       Seconds_Behind_Master:
           0
       Slave_IO_Running:
           Yes
       Slave_IO_State:
           Waiting for master to send event
       Slave_SQL_Running:
           Yes

-   Check if Monit says the database servers are fine too. If everything says "*running*" its all great!

<!-- -->

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

-   Import the previous database snapshot
    -   *scp* the database backup file to the current **masterdb** VM
    -   import the database into the server (e.g. **mysql wpblog \< wpblog.sql**)
    -   the other VMs with the role db (the ones that doesn’t have "masterdb" in their name) should catch up automatically with the replication
-   Change the database details you just created in the pillar file. If the command was run from production, the file to change would be **/srv/private/pillars/accounts/production.sls**
-   To review what’s going to be applied will be */srv/salt/vm/blog.sls*. That is because the role we are working on at this moment is "blog". If you want to review why, take a look at the [section about roles](/WPD:Infrastructure/architecture/Roles_and_environment_level) and the [details of each roles](/WPD:Infrastructure/architecture/VM_roles).
-   Make the configuration file to be applied on top of the web app configuration.

<!-- -->

     wpd-deploy blog

It should look like in this image, with all "green", but of course with the mention of "blog" instead of "app".

![Running wpd-deploy.png](/WPD/assets/public/0/0d/Running_wpd-deploy.png)

-   Last step is to apply *state.highstate*. Its OK to run it more than once, the configuration are written to enforce a state and can be applied in any order, the important is to get all "green".

<!-- -->

     salt blog state.highstate