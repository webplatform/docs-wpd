---
title: Reports to review status
uri: 'WPD:Infrastructure/architecture/Reports to review status'

---
### [WebPlatform server Infrastructure architecture menu](/WPD:Infrastructure/architecture)

-   [Base configuration of a VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM)
-   **Reports to review status**
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
-   [Create new database credentials and configure a web application to use it](/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it)
-   [Maintaining ElasticSearch cluster](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster)
-   [Maintaining email services](/WPD:Infrastructure/procedures/Maintaining_email_services)

From the [The Salt Master](/WPD:Infrastructure/architecture/The_salt_master) we can get various system health status. This document describes how to access them.

# Reports

## How many emails has been sent

We have [*Mailgraph*](http://mailgraph.schweikert.ch/) installed on all *mail* VMs. With it, we can visualize how many emails are being sent to our mail server. It should display the number of refusals (e.g. somebody outside our network trying to use us) over time.

From the browser, through [\#Read reports from a VM through private network](#Read_reports_from_a_VM_through_private_network).

     http://mail/cgi-bin/mailgraph.cgi

Should look like this:

![20150106 mailgraph day.png](/WPD/assets/public/d/da/20150106_mailgraph_day.png)![20150104 mailgraph day.png](/WPD/assets/public/4/44/20150104_mailgraph_day.png)

**Note** please disregard the address in the screenshot, it has been taken during deployment scripts has been set in place.

## Getting to know the status of a php5-fpm backend

You can make a basic *GET /php-status* to any VMs that has **php5-fpm** running. (@@TODO make a role to get all of them and remove the need to guess)

There are a few variants we can get data;

-   Simple report

<!-- -->

     curl piwik/php-status

-   A more detailed report of each worker process

<!-- -->

     curl piwik/php-status?full

-   "Ping" check if *php5-fpm* connection is accessible from NGINX

<!-- -->

     curl piwik/php-ping

![nginx fastcgi status full.png](/WPD/assets/public/3/3f/nginx_fastcgi_status_full.png)![nginx fastcgi status.png](/WPD/assets/public/f/f5/nginx_fastcgi_status.png)

**Note** that in this example I used an SSH tunnel *-L 8080:piwik:80*, but it could have been done through [\#Read reports from a VM through private network](#Read_reports_from_a_VM_through_private_network).

## Getting to know the status of an NGINX web server

-   From the local network

<!-- -->

     curl piwik/nginx-status
     Active connections: 1
     server accepts handled requests
      3031 3031 3024
     Reading: 0 Writing: 1 Waiting: 0

-   From salt

<!-- -->

     salt piwik nginx.status
     piwik:
       ----------
       accepted:
           3030
       active connections:
           1
       handled:
           3030
       reading:
           0
       requests:
           3023
       waiting:
           0
       writing:
           1


## Getting to know the status of an Apache2 web server

-   From salt

<!-- -->

     salt app\* apache.server_status
     app3:
       ----------
       BusyWorkers:
           3
       BytesPerReq:
           865.907
       BytesPerSec:
           3152.89
       CPULoad:
           0.300867
       IdleWorkers:
           16
       ReqPerSec:
           3.64114
       Scoreboard:
           ----------
           .:
               45
           C:
               2
           D:
               0
           G:
               0
           I:
               0
           K:
               0
           L:
               0
           R:
               0
           S:
               0
           W:
               1
           _:
               16
       Total Accesses:
           40748
       Total kBytes:
           34457
       Uptime:
           11191

## Nutcracker

Nutcracker should run on any VM that runs a backend.

You can query its status from the VM itself, through the localhost loopback (only!) by doing a *GET* request like this:

     curl localhost:22222 | python -m json.tool
     {
       "sessions_redis": {
           "10.10.10.177:6379": {
               "in_queue": 0,
               "in_queue_bytes": 0,
               "out_queue": 0,
               "out_queue_bytes": 0,
               "request_bytes": 2681,
               "requests": 28,
               "response_bytes": 713,
               "responses": 27,
               "server_connections": 0,
               "server_ejected_at": 0,
               "server_eof": 1,
               "server_err": 0,
               "server_timedout": 1
           },
           "client_connections": 0,
           "client_eof": 0,
           "client_err": 14,
           "forward_error": 1,
           "fragments": 0,
           "server_ejects": 0
       },
       "source": "app1",
       "timestamp": 1425064419,
       "uptime": 9285,
       "version": "0.3.0"
     }

**Note** the output has been truncated to only one backend to illustrate what data the call provides.

-   Use salt to get data

<!-- -->

     salt -C 'G@roles:app or G@roles:blog or G@roles:piwik or G@roles:project' cmd.run 'curl -s localhost:22222'
     // Data will be similar to the previous example

 Notice how I am targeting the minions using [Salt Compound matcher](http://docs.saltstack.com/en/latest/topics/targeting/compound.html) and asking it to give me Nutcracker status data.

Eventually we could use similar mechanism to gather status on services to learn how the server is going.

## MySQL/MariaDB

We can check what’s the state of the MySQL server by issuing the following commands.

They are available through [*Salt Stack* **mysql** module](http://docs.saltstack.com/en/latest/ref/modules/all/salt.modules.mysql.html#salt.modules.mysql.get_slave_status)

### Get replication status

     salt db2 mysql.get_slave_status
     db2:
       ----------
       Connect_Retry:
           10
       Master_Host:
           masterdb.local.wpdn
       Master_SSL_Allowed:
           Yes
       Master_SSL_CA_File:
           /etc/mysql/ca-cert.pem
       Master_SSL_Cert:
           /etc/mysql/client-cert.pem
       Master_SSL_Crl:
           /etc/mysql/ca-cert.pem
       Master_SSL_Key:
           /etc/mysql/client-key.pem
     // ... truncated

### Get replication master status

     salt -G 'roles:masterdb' mysql.get_master_status
     db1-masterdb:
       ----------
       File:
           mariadbrepl-bin.000093
       Position:
           32058870
     // ... truncated

### Get process list

     salt -G 'roles:db' mysql.processlist
     db2:
       |_
         ----------
         Command:
             Connect
         Id:
             3
         Info:
             None
         Progress:
             0.0
         State:
             Slave has read all relay log; waiting for the slave I/O thread to update it
         Time:
             1
         User:
             system user
         db:
             None

### Misc. reports available on MySQL servers through Salt stack

Here are a few possibly useful commands to pick from;

**Note** its even possible to work on grants/privileges, add/delete databases. Note that if you do so, you MUST make sure that you do it ONLY on the salt master. To learn more, refer to [*Salt Stack* documentation at **mysql** module](http://docs.saltstack.com/en/latest/ref/modules/all/salt.modules.mysql.html#salt.modules.mysql.get_slave_status).

     salt db2 mysql.get_slave_status
     salt -G 'roles:masterdb' mysql.get_master_status
     salt -G 'roles:db' mysql.status

## MediaWiki

Some reports can be gathered from the MediaWiki API. Here’s a list of a few useful ones. If you want to change the way they are displayed, you can change the *&format=* URL fragment (ref: [*MediaWiki.org* documentation](https://www.mediawiki.org/wiki/API:Main_page#The_format).

### Misc. reports

-   [Contributors on **css/properties/border** page (through the API)](https://docs.webplatform.org/w/api.php?format=jsonfm&action=query&prop=contributors&continue=&titles=css/properties/border)
-   [Contributions made by a specific user](https://docs.webplatform.org/wiki/Special:Contributions/Renoirb)
-   [More details about a user (through the API)](https://docs.webplatform.org/w/api.php?format=jsonfm&action=query&list=users&ususers=Renoirb&usprop=blockinfo%7Cgroups%7Ceditcount%7Cemailable)

### User creation log

As long as we don’t have a separate accounts system in place for every components, including our wiki, we need to review in each web application the new accounts that are being created. If we have too many accounts created, it means that we might be under spambot attacks.

-   [list new users (through the API)](https://docs.webplatform.org/w/api.php?format=jsonfm&action=query&list=logevents&letype=newusers&lelimit=50&leprop=user%7Ctimestamp)

![20150106-account-creation-log-api.png](/WPD/assets/public/d/d3/20150106-account-creation-log-api.png)

### What’s the IP address of a given user?

In case of need to review how our infrastructure is being abused, we can get to know the IP address of visitors so that we can effectively ban them.

To do so, we are using the [*MediaWiki CheckUser* Extension](https://www.mediawiki.org/wiki/Extension:CheckUser). Only users of the wiki with sysop privileges can review this information.

![20150108-visualizing-visitor-IP-vs-users.png](/WPD/assets/public/a/a3/20150108-visualizing-visitor-IP-vs-users.png)

## Using Monit

Monit is a software that you can configure to check if a service is accessible or running and how it can make sure its up automatically for you.

**More about Monit in [WPD:Infrastructure/Monitoring/Monit](/WPD:Infrastructure/Monitoring/Monit)**

### From the salt master

We can get **monit** reports **from the salt master** like this

     salt -G 'roles:app' monit.summary
     app2-jobrunner:
       ----------
       Process:
           ----------
           apache2:
               Running
           nutcracker:
               Running
           openssh-server:
               Running
           salt-minion:
               Running
       System:
           ----------
           app2-jobrunner.production.wpdn:
               Running
     app1:
       ----------
       Process:
           ----------
           apache2:
               Running
           nutcracker:
               Running
           openssh-server:
               Running
           salt-minion:
               Running
       System:
           ----------
           app1.production.wpdn:
               Running

Or from the same VM:

     sudo salt-call monit.summary
     [INFO    ] Executing command 'monit summary' in directory '/root'
     local:
       ----------
       Process:
           ----------
           exim4:
               Running
           gdnsd:
               Running
           openssh-server:
               Running
           salt-master:
               Running
           salt-minion:
               Running
           syslog-ng:
               Running
       System:
           ----------
           salt.production.wpdn:
               Running

### From the web frontend

To do this, you need to create a SOCKS proxy like its described in [\#Read reports from a VM through private network](#Read_reports_from_a_VM_through_private_network)

Once connected through ssh with the proxy described, you can connect like this:

     http://monit:p4ssword@sessions1:2812/

Which should look like this;

![20150224-monit-status-preview.png](/WPD/assets/public/5/5d/20150224-monit-status-preview.png)

#### Monit password

The password is not "p4ssword", you’ll have to look at **/srv/private/pillar/accounts/** file yourself at **accounts:monit:admin\_password** or in the VM itself at **/etc/monit/conf.d/defaults.conf**.

An alternate way to get to know the password is to use salt like this:

     salt-call pillar.get accounts:monit:admin_password
     local:
       p4ssword

## Read reports from a VM through private network

To view the internal only reports, you need to setup your local machine to pass through our *Jumpbox*. The instructions are available in [Accessing a VM using SSH in **Base configuration of a VM'**](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM#Accessing_a_VM_using_SSH)
