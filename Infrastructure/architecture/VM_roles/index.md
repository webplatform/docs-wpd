= VM Roles =

In order to have a fully functional site we need to have at least one VM for each of the following roles. Some VMs can fill more than one role.

The following list is in order of importance based on the fact that the ones below would generally rely on the ones over them; 

== Vital roles ==

=== source ===

This VM is used to mirror every dependencies we are using. While most of the repositories are open to the public, some of them aren’t.

Note that although we could have a staging ''source'' VM (i.e. ''source.webplatformstaging.org''), ONLY ''source.webplatform.org'' should be considered as a source of truth.

* '''How many required''': Only one
* '''Must it have a public IP address?'': yes
* '''Expected public domain name'': source.webplatform.org
* '''Must it have a Volume''': ''yes''  (to store the code repositories)
* '''Must it have a DNS reverse lookup''': No
* '''What does it do?''':
** ''Source code hosting'' through git, using Gitolite


=== salt ===

Before the infrastructure rework sprint of January 2015, the salt master was the only VM that must not be deleted. Since then its possible to create a fresh VM and apply a set of scripts to have a new master. The procedure to create a salt master is in [[WPD:Infrastructure/architecture/The_salt_master]].

;'''How many required''': Only one
;'''Must it have a public IP address?'': yes
;'''Expected public domain name'': salt.webplatform.org
;'''Must it have a Volume''': ''yes''  (to store the backups and other work files)
;'''Must it have a DNS reverse lookup''': No
;'''What does it do?''':
* ''DNS server'' (using 'gdnsd'), every other VM has ''/etc/resolv.conf'' pointing to the salt master
* ''Salt master'', each changes on every VM is made from that VM
* ''SSH jump box'': SSH Access to every VM is made through that VM. A banner on login gives the current environment 'level', and ssh configuration to use
* ''rsync'' (through an 'xinetd' service), each VM can pull files from it. Including backups

==== How to use ====

To work on a cluster on a given level, you can use the salt master as a SOCKS proxy to view privilegied reports such as service health and usage reports.  

To view the internal only reports, configure one of your web browser to use your local computer as a proxy through the SSH tunnel we will create.

  ssh salt.webplatform.org -C -D 1080

'''Reports view''':

;''Email reports'': [http://mail/cgi-bin/mailgraph.cgi Mailgraph] ''http://mail/cgi-bin/mailgraph.cgi'', only on ''mail'' VMs
;''Monit VM dashboard view'': ''http://admin:password@app1:2812/''  (all VMs has this available)

=== mail ===

Every VMs has ''exim4'' configured to send mail to the VM that has the "mail"" role.

According to email server management best practices, it would be better to have two. Having only one is OK.

* '''How many required''': One. 
* '''Must it have a public IP address?'': yes
* '''Expected public domain name'': mail.webplatform.org
* '''Must it have a Volume''': No
'''Must it have a DNS reverse lookup''':
* ''mail.webplatform.org''
* ''mail2.webplatform.org''
* ''mail.webplatformstaging''
* ''mail2.webplatformstaging.org''
* '''Must it have publicly opened ports?''':
** 25 (ensure Postfix only authorizes our machines to relay email!!)
* '''What does it do?''':
** SMTP relay (using Postfix) to the outside world
** OpenDKIM to sign emails before sending them
** Mailgraph

=== masterdb ===

There must only one that has both ''db'' AND ''masterdb'' (e.g. '''db1-masterdb'''). Note that the number isn’t important, just that by convention the lower number is the one we use as a master to send writes to. 

While its not the case at the moment, the objective behind the the role name "master" was to have a way to recognize which should be considered as an entry point within a cluster (e.g. elasticsearch, postgresql, mail).

;How many required: One or more
;Must it have a public IP address?: N/A
;Expected public domain name: N/A
;Must it have a Volume: No
;Must it have a DNS reverse lookup: No
;Must it have publicly opened ports?: No
;What does it do?:
* Meta role, other configuration could use it as an indice to know which one is the entry point

=== db ===

=== sessions ===

=== memcache ===

=== elastic ===

=== app ===

=== blog ===

=== project ===

=== notes ===

=== bots ===

=== jobrunner ===

== Which VM has which role? ==

You can get to know which roles are assigned per VM by running the following command:

    salt \* grains.get roles

== A sample cluster ==

The following is a set of VMs showing the roles they are filling.