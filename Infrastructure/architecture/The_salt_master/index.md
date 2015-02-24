{{:WPD:Infrastructure/architecture}}
= The Salt Master =

[[WPD:Infrastructure/procedures/Deploying_code_changes|Deploying code changes on the site]] is made through a VM, named "salt" we refer to this machine as the "Salt Master" we generally connect through SSH at the name '''salt.webplatform.org'''.

The software we use for configuration management is called "[http://saltstack.com/ Salt Stack]", we refer to the machine that has a copy of all the configuration files

Commands that can be done from the salt master VM in the terminal.

== Getting to know the status of a php5-fpm backend ==

  curl http://piwik/fcgi-status
  pool:                 www
  process manager:      dynamic
  start time:           20/Feb/2015:14:09:09 -0500
  start since:          346509
  accepted conn:        2910
  listen queue:         0
  max listen queue:     0
  listen queue len:     128
  idle processes:       5
  active processes:     1
  total processes:      6
  max active processes: 3
  max children reached: 0
  slow requests:        0

  curl piwik/fcgi-status?full
  pool:                 www
  process manager:      dynamic
  start time:           20/Feb/2015:14:09:09 -0500
  start since:          346688
  accepted conn:        2913
  listen queue:         0
  max listen queue:     0
  listen queue len:     128
  idle processes:       5
  active processes:     1
  total processes:      6
  max active processes: 3
  max children reached: 0
  slow requests:        0
  
  ************************
  pid:                  19439
  state:                Idle
  start time:           20/Feb/2015:14:09:09 -0500
  start since:          346688
  requests:             490
  request duration:     221937
  request method:       -
  request URI:          -
  content length:       0
  user:                 -
  script:               -
  last request cpu:     72.09
  last request memory:  5242880
  ...


== Read reports from other VMs through private network ==

To work on a cluster on a given level, you can use the salt master as a SOCKS proxy to view privileged reports such as service health and usage reports.  

To view the internal only reports, configure one of your web browser to use your local computer as a proxy through the SSH tunnel we will create.

  ssh salt.webplatform.org -C -D 1080

=== Available reports ===

* ''Email reports'': ''http://mail/cgi-bin/mailgraph.cgi'', only on ''mail'' VMs using [http://mailgraph.schweikert.ch/ ''Mailgraph'']
* ''Monit VM dashboard view'': ''http://admin:password@app1:2812/''  (all VMs has this available), using [http://mmonit.com/monit/ Monit]