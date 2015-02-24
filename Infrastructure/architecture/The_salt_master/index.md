{{:WPD:Infrastructure/architecture}}
= The Salt Master =

[[WPD:Infrastructure/procedures/Deploying_code_changes|Deploying code changes on the site]] is made through a VM, named "salt" we refer to this machine as the "Salt Master" we generally connect through SSH at the name '''salt.webplatform.org'''.

The software we use for configuration management is called '''[http://saltstack.com/ Salt Stack]''', we refer to the machine that has a copy of all the configuration files.

Commands that can be done from the salt master VM in the terminal, but some could also be visualized from within your local web browser through [[#Read reports from a VM through private network]].

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

== Read reports from a VM through private network ==

To work on a cluster on a given level, you can use the salt master as a SOCKS proxy to view privileged reports such as service health and usage reports.  

To view the internal only reports, configure one of your web browser to use your local computer as a proxy through the SSH tunnel we will create.

  ssh salt.webplatform.org -C -D 1080

=== Available reports ===

* ''Email reports'': ''http://mail/cgi-bin/mailgraph.cgi'', only on ''mail'' VMs using [http://mailgraph.schweikert.ch/ ''Mailgraph'']
* ''Monit VM dashboard view'': ''http://admin:password@app1:2812/''  (all VMs has this available), using [http://mmonit.com/monit/ Monit]
* '''NGINX''' server status, from a VM that runs NGINX: e.g. ''http://piwik/nginx-status''
* '''php5-fpm''' status, from a VM that runs ''php5-fpm'': ''http://piwik/fcgi-status''