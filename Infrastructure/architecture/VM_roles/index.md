---
title: VM Roles
uri: 'WPD:Infrastructure/architecture/VM roles'

---
### <span>[WebPlatform server Infrastructure architecture menu](/WPD:Infrastructure/architecture)</span>

-   [Base configuration of a VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM)
-   [Reports to review status](/WPD:Infrastructure/architecture/Reports_to_review_status)
-   [Roles and environment level](/WPD:Infrastructure/architecture/Roles_and_environment_level)
-   [SSL certificates](/WPD:Infrastructure/architecture/SSL_certificates)
-   [The salt master](/WPD:Infrastructure/architecture/The_salt_master)
-   [Things to consider when we expose service via Fastly and Varnish](/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish)
-   [Useful commands](/WPD:Infrastructure/architecture/Useful_commands)
-   **VM roles**

**See also**

-   [Deploying code changes](/WPD:Infrastructure/procedures/Deploying_code_changes)
-   [Replacing a VM](/WPD:Infrastructure/procedures/Replacing_a_VM)
-   [Maintaining Fastly configuration](/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration)
-   [Managing MySQL replication](/WPD:Infrastructure/procedures/Managing_MySQL_replication)
-   [Create new database credentials and configure a web application to use it](/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it)
-   [Maintaining ElasticSearch cluster](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster)
-   [Maintaining email services](/WPD:Infrastructure/procedures/Maintaining_email_services)

## <span>Network diagram overview</span>

### <span>Former configuration</span>

@@TODO make variant of *Future configuration* to illustrate difference.

### <span>Future configuration</span>

In order to allow us to support more than one backend server and a simplified frontend configuration scheme, we are going to create a cluster of NGINX servers that’ll serve every requests. While some components are served by Fastly and others aren’t, the NGINX cluster will serve all of them regardless.

![Component-diagram-internal.png](/WPD/assets/public/8/83/Component-diagram-internal.png)

# <span>Roles</span>

In order to have a fully functional site we need to have at least one VM for each of the following roles. Some VMs can fill more than one role.

The **following list is in order of importance** based on the fact **that the ones below would generally rely on the ones over them**;

## <span>source</span>

This VM is used to mirror every dependencies we are using. While most of the repositories are open to the public, some of them aren’t.

Note that although we could have a staging *source* VM (i.e. *source.webplatformstaging.org*), ONLY *source.webplatform.org* should be considered as a source of truth.

-   **How many required**: Only one
-   **Must it have a public IP address?**: yes
-   **Expected public hostname**: source.webplatform.org
-   **Must it have a Volume**: *yes* (to store the code repositories)
-   **Must it have a DNS reverse lookup**: No
-   **What does it do?**:
    -   *Source code hosting* through git, using Gitolite. We might soon either use back Gerrit or Phabricator

## <span>salt</span>

Before the infrastructure rework sprint of January 2015, the salt master was the only VM that must not be deleted. Since then its possible to create a fresh VM and apply a set of scripts to have a new master. The procedure to create a salt master is in [WPD:Infrastructure/architecture/The\_salt\_master](/WPD:Infrastructure/architecture/The_salt_master).

-   **How many required**: Only one
-   **Must it have a public IP address?**: yes
-   **Expected public hostname**: salt.webplatform.org
-   **Must it have a Volume**: yes (to store the backups and other work files)
-   **Must it have a DNS reverse lookup**: No
-   **What does it do?**:
    -   *DNS server* (using 'gdnsd'), every other VM has */etc/resolv.conf* pointing to the salt master
    -   *Salt master*, each changes on every VM is made from that VM
    -   *SSH jump box*: SSH Access to every VM is made through that VM. A banner on login gives the current environment 'level', and ssh configuration to use
    -   *rsync* (through an 'xinetd' service), each VM can pull files from it. Including backups

### <span>Design decisions</span>

-   The salt master was originally a VM that we had to pray to keep running. From now on everything under **/srv/** should be managed in a git repository. If its managed by something not obvious, there’s should be a **README.md** file @@TODO, ensure the file is present.

### <span>Also related</span>

-   [Gist containing every essential bootstrap script](https://gist.github.com/WebPlatformDocs/01c09df78f05612c281f). (take the contents of the Gist as a snapshot. @@TODO, put link to authoritative version here)
-   [Salt Master Monit config](https://gist.github.com/WebPlatformDocs/780307ff289864ba02f5#file-salt-master-conf) (take the contents of the Gist as a snapshot. @@TODO, put link to authoritative version here)
-   [WPD:Infrastructure/architecture/The\_salt\_master](/WPD:Infrastructure/architecture/The_salt_master)

## <span>mail</span>

Every VMs has *exim4* configured to send mail to the VM that has the "mail" role.

According to email server management best practices, it would be better to have two. Having only one is OK.

-   **How many required**: One.
-   **Must it have a public IP address?**: yes
-   **Expected public hostname**: mail.webplatform.org
-   **Must it have a Volume**: No
-   **Must it have a DNS reverse lookup**:
    -   *mail.webplatform.org*
    -   *mail2.webplatform.org*
    -   *mail.webplatformstaging.org*
    -   *mail2.webplatformstaging.org*
-   **Must it have publicly opened ports?**:
    -   25 (ensure Postfix only authorizes our machines to relay email!!)
-   **What does it do?**:
    -   SMTP relay (using Postfix) to the outside world
    -   OpenDKIM to sign emails before sending them
    -   Mailgraph, creates rrd graphs to visualize the email traffic

## <span>backup</span>

The VM that gathers backups from every other VMs.

-   **How many required**: Only one
-   **Must it have a public IP address?**: No
-   **Expected public hostname**: N/A
-   **Must it have a Volume**: yes (not vital, very useful in need of recovery)
-   **Must it have a DNS reverse lookup**: No
-   **Must it have publicly opened ports?**: No
-   **What does it do?**:
    -   rsync data from other VMs to keep backups (cronjob made by root)
    -   shares through NFS snapshots for ElasticSearch

### <span>Design decisions</span>

ElasticSearch snapshot setup requires we have a network mount point. While we previously had a GlusterFS cluster that could have been used for that purpose, we decided to change our setup to stop using it. We therefore needed, again, to setup network share. This time It has been decided to use NFS from the backup VM and potentially share through it only what’s required to facilitate backups but not as a main way to gather data when generating web pages.

### <span>Also related</span>

-   [ElasticSearch cluster; How backups are made](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster#How_backups_are_made)

## <span>masterdb</span>

There must only one that has both *db* AND *masterdb* (e.g. **db1-masterdb**). Note that the number isn’t important, just that by convention the lower number is the one we use as a master to send writes to.

-   **How many required**: One
-   **Must it have a public IP address?**: N/A
-   **Expected public hostname**: N/A
-   **Must it have a Volume**: yes (not vital, very useful in need of recovery)
-   **Must it have a DNS reverse lookup**: No
-   **Must it have publicly opened ports?**: No
-   **What does it do?**:
    -   "Meta" role, other configuration could use it as an indice to know which one is the entry point

### <span>Design decisions</span>

-   While its not the case at the moment, the objective behind the the role name "master" was to have a way to recognize which should be considered as an entry point within a cluster (e.g. elasticsearch, postgresql, mail). The name "masterdb" could be renamed "master" and the states configuration should be adjusted to allow other services to use this pattern.

## <span>db</span>

The first database server we originally had was MySQL 5.1 and the VM had a name starting by *db*.

-   **How many required**: One or more
-   **Must it have a public IP address?**: No
-   **Expected public hostname**: N/A
-   **Must it have a Volume**: yes (not vital, very useful in need of recovery)
-   **Must it have a DNS reverse lookup**: No
-   **Must it have publicly opened ports?**: No
-   **What does it do?**:
    -   MariaDB server v 10.x
    -   MariaDB replication (when applicable)

### <span>Also related</span>

-   [Create a MariaDB cluster with replication over SSL](https://renoirboulanger.com/blog/2015/01/create-mariadb-cluster-replication-ssl-salt-stack) has been written to describe how to create a VM
-   [WPD:Infrastructure/procedures/Managing\_MySQL\_replication](/WPD:Infrastructure/procedures/Managing_MySQL_replication)

### <span>Design decisions</span>

-   As of the time this was written, it’s a known fact that while we do have two database servers, only one is used by all our web applications. The other database server is only used as a hot backup with replication over SSL setup. All reads and writes are sent to the only VM that has both *db* and *masterdb* roles.
-   The upcoming infrastructure changes would have to be more specific as we’ll also need to have a PostgreSQL cluster and we’ll have to create a different role name for the different vendor.
-   We do not forbid database writes on ANY db server and that even though we may have one VM with the role masterdb because we want to be able to quickly change master.
-   It is planned to use new replication features such as ones that we can send writes to any nodes and the replication will be made consistent everywhere. This has to be tested first though.
-   At the beginning this VM was running on Ubuntu 10.04 with MySQL 5.1

## <span>sessions</span>

This VM runs both **Redis** and **Memcached**. It depends which session storage mechanism each Web app supports. ONLY session data are stored in those keystores, nothing else.

This VM is only accessible from internal network which is sensible considering its use. To add one more notch up, this VM should have its services to have some more enforcement to prevent access to the session tokens it stores (e.g. by requiring password and such).

-   **How many required**: One or more
-   **Must it have a public IP address?**: No
-   **Expected public hostname**: N/A
-   **Must it have a Volume**: N/A
-   **Must it have a DNS reverse lookup**: N/A
-   **Must it have publicly opened ports?**: No
-   **What does it do?**:
    -   *Redis server*
    -   *Memcached server*

### <span>Design decisions</span>

-   The objective of the *sessions* VM is to store only user session data in a key store (redis, memcached, etc) so we do not mix general use object cache web applications would make.
-   Note that there’s no enforcement, authentications, checks for who and what we send at the moment of writing of this document
-   Each web app VM will eventually run a proxy to the sessions storage this VM provides with a software called *Nutcracker* (a.k.a. [TwEmProxy](https://github.com/twitter/twemproxy/))
-   As with other keystore VMs such as the ones with roles **redis** and **memcache**, the port should be the default value from the VM itself. Each client VM to sessions will also expose the default port as if it was local.

## <span>accounts</span>

-   **How many required**: 1
-   **Must it have a public IP address?**: Yes (for now, until we make it behind NGINX)
-   **Expected public hostname**:
-   **Must it have a Volume**: N/A
-   **Must it have a DNS reverse lookup**: N/A
-   **Must it have publicly opened ports?**: N/A
-   **What does it do?**:
    -   OAuth2 server ("fxa-oauth-server")
    -   Internal auth API server ("fxa-auth-server")
    -   Profile server ("fxa-profile-server")
    -   Auth server frontend ("fxa-content-server")

### <span>Design decisions</span>

While at the moment we do expose an HTTP server through NGINX to the public, this VM will be eventually not visible.

It is planned, in *WebPlatform GitHub operations issue tracker*, at **[webplatform/ops\#115](https://github.com/webplatform/ops/issues/115)**, that we get the IP address it uses to make a new set of hostnames and create a "round robin" (i.e. a DNS name that has more than one IP address) and create a NGINX frontend proxy. This new proxy would serve content from internal backends to the public without exposing

## <span>memcache</span>

-   **How many required**: More than one
-   **Must it have a public IP address?**: No
-   **Expected public hostname**: N/A
-   **Must it have a Volume**: N/A
-   **Must it have a DNS reverse lookup**: N/A
-   **Must it have publicly opened ports?**: N/A
-   **What does it do?**:
    -   Memcached server

### <span>Design decisions</span>

-   Memcached is an extremely simple API. Although we can enforce SSL certificate validation, it is not done by default and it also has no authentication. The practice is to ensure that only nodes that should have access can make commands to it. The way to do is to either use Security Groups from the cloud provider, or firewall rules inside the VM.
-   Create a Memcache cluster per use case. For example we could have a memcached cluster for sessions, and another one to cache heavy pages. If we need to purge the heavy pages cache we can send a purge command to all nodes from that cluster without worrying to destroy every user sessions.

## <span>elastic</span>

-   **How many required**: One or more
-   **Must it have a public IP address?**: No
-   **Expected public hostname**: N/A
-   **Must it have a Volume**: N/A
-   **Must it have a DNS reverse lookup**: N/A
-   **Must it have publicly opened ports?**: N/A
-   **What does it do?**:
    -   Elasticsearch server

### <span>Design decisions</span>

-   ElasticSearch doesn’t have authentication. If we are to expose it to the public, it MUST be from an API that would forbid dangerous commands. Something not done yet; It’ll be eventually required.

## <span>app</span>

-   **How many required**:
-   **Must it have a public IP address?**:
-   **Expected public hostname**:
-   **Must it have a Volume**:
-   **Must it have a DNS reverse lookup**:
-   **Must it have publicly opened ports?**:
-   **What does it do?**:

### <span>Design decisions</span>

-   Originally made to run all web apps when we launched in 2012: mediawiki, blog and later were TheBugGenie and so on. After some time Ryan decided to move the blog to one VM and with other speed problems to create another VM for BugGenie. This is why we have that many VMs nowadays.

## <span>blog</span>

-   **How many required**:
-   **Must it have a public IP address?**:
-   **Expected public hostname**:
-   **Must it have a Volume**:
-   **Must it have a DNS reverse lookup**:
-   **Must it have publicly opened ports?**:
-   **What does it do?**:

## <span>project</span>

-   **How many required**:
-   **Must it have a public IP address?**:
-   **Expected public hostname**:
-   **Must it have a Volume**:
-   **Must it have a DNS reverse lookup**:
-   **Must it have publicly opened ports?**:
-   **What does it do?**:
    -   Runs The Bug Genie

### <span>Design Decisions</span>

-   VM created to host exclusively Bug Genie project management.
-   Bug Genie will eventually be phased out in favor to something else.

## <span>notes</span>

-   **How many required**:
-   **Must it have a public IP address?**:
-   **Expected public hostname**:
-   **Must it have a Volume**:
-   **Must it have a DNS reverse lookup**:
-   **Must it have publicly opened ports?**:
-   **What does it do?**:

## <span>bots</span>

-   **How many required**:
-   **Must it have a public IP address?**:
-   **Expected public hostname**:
-   **Must it have a Volume**:
-   **Must it have a DNS reverse lookup**:
-   **Must it have publicly opened ports?**:
-   **What does it do?**:

## <span>jobrunner</span>

-   **How many required**:
-   **Must it have a public IP address?**:
-   **Expected public hostname**:
-   **Must it have a Volume**:
-   **Must it have a DNS reverse lookup**:
-   **Must it have publicly opened ports?**:
-   **What does it do?**:

## <span>piwik</span>

-   **How many required**:
-   **Must it have a public IP address?**:
-   **Expected public hostname**:
-   **Must it have a Volume**:
-   **Must it have a DNS reverse lookup**:
-   **Must it have publicly opened ports?**:
-   **What does it do?**:

## <span>nginx</span>

-   **How many required**:
-   **Must it have a public IP address?**:
-   **Expected public hostname**:
-   **Must it have a Volume**:
-   **Must it have a DNS reverse lookup**:
-   **Must it have publicly opened ports?**:
-   **What does it do?**:

## <span>specs</span>

-   **How many required**:
-   **Must it have a public IP address?**:
-   **Expected public hostname**:
-   **Must it have a Volume**:
-   **Must it have a DNS reverse lookup**:
-   **Must it have publicly opened ports?**:
-   **What does it do?**:

## <span>hhvmbackend</span>

-   **How many required**:
-   **Must it have a public IP address?**:
-   **Expected public hostname**:
-   **Must it have a Volume**:
-   **Must it have a DNS reverse lookup**:
-   **Must it have publicly opened ports?**:
-   **What does it do?**:
