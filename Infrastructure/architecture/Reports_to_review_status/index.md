{{:WPD:Infrastructure/architecture}}
= Reports to review status =

From the  [[WPD:Infrastructure/architecture/The_salt_master|The Salt Master]] we can get various system health status. This document describes how to access them.

__TOC__

= Reports =

== How many emails has been sent ==

We can visualize how many emails are being sent to our mail server. It should display the number of refusals (e.g. somebody outside our network trying to use us) over time.

From the browser, through [[#Read reports from a VM through private network]].

  http://mail/cgi-bin/mailgraph.cgi

Should look like this:

[[File:20150106_mailgraph_day.png]]
[[File:20150104_mailgraph_day.png]]

'''Note''' that this screenshot was made to illustrate a crisis we’ve had but you can see notes that should illustrate what we can get from the reports.

== Getting to know the status of a php5-fpm backend ==

You can make a basic ''GET /fcgi-status'' to any VMs that has '''php5-fpm''' running. (@@TODO make a role to get all of them and remove the need to guess)

There are a few variants we can get data;

* Simple report

  curl piwik/fcgi-status

* A more detailed version

  curl piwik/fcgi-status?full

[[File:nginx_fastcgi_status_full.png]]
[[File:nginx_fastcgi_status.png]]

'''Note''' that in this example I used an SSH tunnel ''-L 8080:piwik:80'', but it could have been done through [[#Read reports from a VM through private network]].

== Getting to know the status of an NGINX web server ==

* From the local network

  curl piwik/nginx-status
  Active connections: 1
  server accepts handled requests
   3031 3031 3024
  Reading: 0 Writing: 1 Waiting: 0

* From salt

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
  

== Getting to know the status of an Apache2 web server ==

* From salt

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

== MySQL/MariaDB replication status ==

We can check what’s the state of the MySQL server by issuing the following commands. They are available through [http://docs.saltstack.com/en/latest/ref/modules/all/salt.modules.mysql.html#salt.modules.mysql.get_slave_status ''Salt Stack'' '''mysql''' module]

=== Get replication status ===

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
 
=== Get replication master status ===

  salt -G 'roles:masterdb' mysql.get_master_status
  db1-masterdb:
    ----------
    File:
        mariadbrepl-bin.000093
    Position:
        32058870
  // ... truncated

=== Get process list ===

  salt -G 'roles:db' mysql.processlist
  db2:
    |_
      ----------
      Command:
          Connect
      Host:

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

=== Other reports commands available on MySQL servers through Salt stack  ===

Here are a few possibly useful commands to pick from;

'''Note''' its even possible to work on grants/privileges, add/delete databases. Note that if you do so, you MUST make sure that you do it ONLY on the salt master.

  salt db2 mysql.get_slave_status
  salt -G 'roles:masterdb' mysql.get_master_status
  salt -G 'roles:db' mysql.status
  salt -G 'roles:db' mysql.query mydb "SHOW STATUS WHERE `variable_name` IN('Threads_connected','Connections','Connection_errors_tcpwrap','Connection_errors_peer_address','Connection_errors_max_connections');"

== MediaWiki ==

=== User creation log ===

As long as we don’t have a separate accounts system in place for every components, including our wiki, we need to review in each web application the new accouts that are being created. If we have too many accounts created, it means that we might be under spambot attacks.

The following links gives an example on how to get the ''User creation log'' from MediaWiki, you can get different formats by changing the ''&format='' fragment, ref: [https://www.mediawiki.org/wiki/API:Main_page#The_format ''MediaWiki.org'', the format URL fragment].

* https://docs.webplatform.org/w/api.php?format=jsonfm&action=query&list=logevents&letype=newusers&lelimit=50&leprop=user|timestamp

[[File:20150106-account-creation-log-api.png]]

=== What’s the IP address of a given user? ==

In case of need to review how our infrastructure is being abused, we can get to know the IP address of visitors so that we can effectively ban them.

To do so, we are using the [https://www.mediawiki.org/wiki/Extension:CheckUser ''MediaWiki CheckUser'' Extension]. Only users of the wiki with sysop privileges can review this information.

[[File:20150108-visualizing-visitor-IP-vs-users.png]]

== Read reports from a VM through private network ==

To work on a cluster on a given level, you can use the salt master as a SOCKS proxy to view privileged reports such as service health and usage reports.  

To view the internal only reports, configure one of your web browser to use your local computer as a proxy through the SSH tunnel we will create.

  ssh salt.webplatform.org -C -D 1080

=== Available reports ===

* ''Email reports'': ''http://mail/cgi-bin/mailgraph.cgi'', only on ''mail'' VMs using [http://mailgraph.schweikert.ch/ ''Mailgraph'']
* ''Monit VM dashboard view'': ''http://admin:password@app1:2812/''  (all VMs has this available), using [http://mmonit.com/monit/ Monit]
* '''NGINX''' server status, from a VM that runs NGINX: e.g. ''http://piwik/nginx-status''
* '''php5-fpm''' status, from a VM that runs ''php5-fpm'': ''http://piwik/fcgi-status''