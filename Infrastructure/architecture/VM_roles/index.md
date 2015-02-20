= VM Roles =

In order to have a fully functional site we need to have at least one VM for each of the following roles. Some VMs can fill more than one role.

The following list is in order of importance based on the fact that the ones below would generally rely on the ones over them; 



== source ==

This VM is used to mirror every dependencies we are using. While most of the repositories are open to the public, some of them aren’t.

Note that although we could have a staging ''source'' VM (i.e. ''source.webplatformstaging.org''), ONLY ''source.webplatform.org'' should be considered as a source of truth.

* '''How many required''': Only one
* '''Must it have a public IP address?''': yes
* '''Expected public hostname''': source.webplatform.org
* '''Must it have a Volume''': ''yes''  (to store the code repositories)
* '''Must it have a DNS reverse lookup''': No
* '''What does it do?''':
** ''Source code hosting'' through git, using Gitolite


== salt ==

Before the infrastructure rework sprint of January 2015, the salt master was the only VM that must not be deleted. Since then its possible to create a fresh VM and apply a set of scripts to have a new master. The procedure to create a salt master is in [[WPD:Infrastructure/architecture/The_salt_master]].

* '''How many required''': Only one
* '''Must it have a public IP address?''': yes
* '''Expected public hostname''': salt.webplatform.org
* '''Must it have a Volume''': yes  (to store the backups and other work files)
* '''Must it have a DNS reverse lookup''': No
* '''What does it do?''':
** ''DNS server'' (using 'gdnsd'), every other VM has ''/etc/resolv.conf'' pointing to the salt master
** ''Salt master'', each changes on every VM is made from that VM
** ''SSH jump box'': SSH Access to every VM is made through that VM. A banner on login gives the current environment 'level', and ssh configuration to use
** ''rsync'' (through an 'xinetd' service), each VM can pull files from it. Including backups

=== Also related ===

* [https://gist.github.com/WebPlatformDocs/01c09df78f05612c281f Gist containing every essential bootstrap script]. (take the contents of the Gist as a snapshot. @@TODO, put link to authoritative version here)
* [https://gist.github.com/WebPlatformDocs/780307ff289864ba02f5#file-salt-master-conf Salt Master Monit config]  (take the contents of the Gist as a snapshot. @@TODO, put link to authoritative version here)

=== How to use ===

To work on a cluster on a given level, you can use the salt master as a SOCKS proxy to view privilegied reports such as service health and usage reports.  

To view the internal only reports, configure one of your web browser to use your local computer as a proxy through the SSH tunnel we will create.

  ssh salt.webplatform.org -C -D 1080

'''Reports view''':
* ''Email reports'': ''http://mail/cgi-bin/mailgraph.cgi'', only on ''mail'' VMs using [http://mailgraph.schweikert.ch/ ''Mailgraph'']
* ''Monit VM dashboard view'': ''http://admin:password@app1:2812/''  (all VMs has this available), using [http://mmonit.com/monit/ Monit]



== mail ==

Every VMs has ''exim4'' configured to send mail to the VM that has the "mail" role.

According to email server management best practices, it would be better to have two. Having only one is OK.

* '''How many required''': One. 
* '''Must it have a public IP address?''': yes
* '''Expected public hostname''': mail.webplatform.org
* '''Must it have a Volume''': No
* '''Must it have a DNS reverse lookup''':
** ''mail.webplatform.org''
** ''mail2.webplatform.org''
** ''mail.webplatformstaging.org''
** ''mail2.webplatformstaging.org''
* '''Must it have publicly opened ports?''':
** 25 (ensure Postfix only authorizes our machines to relay email!!)
* '''What does it do?''':
** SMTP relay (using Postfix) to the outside world
** OpenDKIM to sign emails before sending them
** Mailgraph


== masterdb ==

There must only one that has both ''db'' AND ''masterdb'' (e.g. '''db1-masterdb'''). Note that the number isn’t important, just that by convention the lower number is the one we use as a master to send writes to. 

While its not the case at the moment, the objective behind the the role name "master" was to have a way to recognize which should be considered as an entry point within a cluster (e.g. elasticsearch, postgresql, mail).

* '''How many required''': One or more
* '''Must it have a public IP address?''': N/A
* '''Expected public hostname''': N/A
* '''Must it have a Volume''': yes (not vital, very useful in need of recovery)
* '''Must it have a DNS reverse lookup''': No
* '''Must it have publicly opened ports?''': No
* '''What does it do?''':
** "Meta" role, other configuration could use it as an indice to know which one is the entry point


== db ==

As of when this document was written, it’s a known fact that while we do have two database servers, only one is used by all our web applications.  The other database server is only used as a hot backup with replication over SSL setup. All reads and writes are sent to the only VM that has both ''db'' and ''masterdb'' roles.

* '''How many required''': One or more
* '''Must it have a public IP address?''': No
* '''Expected public hostname''': N/A
* '''Must it have a Volume''': yes (not vital, very useful in need of recovery)
* '''Must it have a DNS reverse lookup''': No
* '''Must it have publicly opened ports?''': No
* '''What does it do?''':
** MariaDB server
** MariaDB replication (when applicable)

=== Also related ===
* [https://renoirboulanger.com/blog/2015/01/create-mariadb-cluster-replication-ssl-salt-stack Create a MariaDB cluster with replication over SSL] has been written to describe how to create a VM
* [[WPD:Infrastructure/procedures/Managing_MySQL_replication]]

=== Design decisions ===
* We do not forbid database writes on ANY db server and that even though we may have one VM with the role masterdb because we want to be able to quickly change master.
* It is planned to use new replication features such as ones that we can send writes to any nodes and the replication will be made consistent everywhere. This has to be tested first though.


=== Changing MariaDB replication master ===
Quoting what I wrote on [https://renoirboulanger.com/blog/2015/01/create-mariadb-cluster-replication-ssl-salt-stack/ a blog post I wrote on January 2015: Create a MariaDB cluster with replication over SSL]:

* From the masterdb MySQL server, in a command line session
* Lock writes on masterdb databases <code>FLUSH TABLES WITH READ LOCK;</code> (make sure this session stays open, the lock only lasts with the session you used to write it. See [https://mariadb.com/kb/en/mariadb/flush-tables-for-export/ MariaDB flush tables pages])
* From a secondary MySQL server; Wait replication to catch up <code>SHOW SLAVE STATUS\G</code>
* Remove replication configuration 
* Tell all web apps to use new database master (from the salt master, change the '''infra:hosts_entries:masterdb'' key in  '''/srv/pillar/infra/production.sls''' (or '''/srv/pillar/infra/staging.sls''' for staging).
* From the masterdb; remove database lock by closing the session opened earlier
* Setup new replication configuration to use new master

@@TODO, Make a more precise procedure with new setup and how to manage.


== sessions ==

This VM runs both '''Redis''' and '''Memcached'''. It depends which session storage mechanism each Web app supports. ONLY session data are stored in those keystores, nothing else.

This VM is only accessible from internal network which is sensible considering its use. To add one more notch up, this VM should have its services to have some more enforcement to prevent access to the session tokens it stores (e.g. by requiring password and such). 

* '''How many required''': One or more
* '''Must it have a public IP address?''': No
* '''Expected public hostname''': N/A
* '''Must it have a Volume''': N/A
* '''Must it have a DNS reverse lookup''': N/A
* '''Must it have publicly opened ports?''': No
* '''What does it do?''':
** ''Redis server''
** ''Memcached server''

=== Design decisions ===
* The objective of the ''sessions'' VM is to store only user session data in a key store (redis, memcached, etc) so we do not mix general use object cache web applications would make.
* Note that there’s no enforcement, authentications, checks for who and what we send at the moment of writing of this document
* Each web app VM will eventually run a proxy to the sessions storage this VM provides with a software called ''Nutcracker'' (a.k.a. [https://github.com/twitter/twemproxy/ TwEmProxy]) 

== accounts ==

* '''How many required''':
* '''Must it have a public IP address?''':
* '''Expected public hostname''':
* '''Must it have a Volume''':
* '''Must it have a DNS reverse lookup''':
* '''Must it have publicly opened ports?''':
* '''What does it do?''':

=== Design decisions ===
* [https://github.com/webplatform/ops/issues/115 webplatform/ops#115]: While at the moment we do expose an HTTP server through NGINX to the public, this VM will be eventually not visible. It is planned that we get the IP address it uses to make a new set of hostnames and create a "round robin" (i.e. a DNS name that has more than one IP address) and create a NGINX frontend proxy. This new proxy would serve content from internal backends to the public without exposing 

== memcache ==

* '''How many required''':
* '''Must it have a public IP address?''':
* '''Expected public hostname''':
* '''Must it have a Volume''':
* '''Must it have a DNS reverse lookup''':
* '''Must it have publicly opened ports?''':
* '''What does it do?''':


== elastic ==

* '''How many required''':
* '''Must it have a public IP address?''':
* '''Expected public hostname''':
* '''Must it have a Volume''':
* '''Must it have a DNS reverse lookup''':
* '''Must it have publicly opened ports?''':
* '''What does it do?''':


== app ==

* '''How many required''':
* '''Must it have a public IP address?''':
* '''Expected public hostname''':
* '''Must it have a Volume''':
* '''Must it have a DNS reverse lookup''':
* '''Must it have publicly opened ports?''':
* '''What does it do?''':


== blog ==

* '''How many required''':
* '''Must it have a public IP address?''':
* '''Expected public hostname''':
* '''Must it have a Volume''':
* '''Must it have a DNS reverse lookup''':
* '''Must it have publicly opened ports?''':
* '''What does it do?''':


== project ==

* '''How many required''':
* '''Must it have a public IP address?''':
* '''Expected public hostname''':
* '''Must it have a Volume''':
* '''Must it have a DNS reverse lookup''':
* '''Must it have publicly opened ports?''':
* '''What does it do?''':


== notes ==

* '''How many required''':
* '''Must it have a public IP address?''':
* '''Expected public hostname''':
* '''Must it have a Volume''':
* '''Must it have a DNS reverse lookup''':
* '''Must it have publicly opened ports?''':
* '''What does it do?''':


== bots ==

* '''How many required''':
* '''Must it have a public IP address?''':
* '''Expected public hostname''':
* '''Must it have a Volume''':
* '''Must it have a DNS reverse lookup''':
* '''Must it have publicly opened ports?''':
* '''What does it do?''':


== jobrunner ==

* '''How many required''':
* '''Must it have a public IP address?''':
* '''Expected public hostname''':
* '''Must it have a Volume''':
* '''Must it have a DNS reverse lookup''':
* '''Must it have publicly opened ports?''':
* '''What does it do?''':


== Which VM has which role? ==

You can get to know which roles are assigned per VM by running the following command:

    salt \* grains.get roles

== A sample cluster ==

The following is a set of VMs showing the roles they are filling.