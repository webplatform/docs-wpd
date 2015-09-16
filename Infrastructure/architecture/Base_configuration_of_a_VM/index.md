---
title: Base configuration of a VM
uri: 'WPD:Infrastructure/architecture/Base configuration of a VM'

---
### [WebPlatform server Infrastructure architecture menu](/WPD:Infrastructure/architecture)

-   **Base configuration of a VM**
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
-   [Create new database credentials and configure a web application to use it](/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it)
-   [Maintaining ElasticSearch cluster](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster)
-   [Maintaining email services](/WPD:Infrastructure/procedures/Maintaining_email_services)

Here is a few details that every VMs has in common

-   Ubuntu 14.04 LTS
-   *Apt* is configured to have security updates installed automatically
-   IPv6 is supported by DreamCompute, but we aren’t using it yet. It’s disabled at *sysctl* level for now
-   Private IPv4 networking *security groups* is allowing VMs to communicate among themselves
-   Nothing is exposed to the public *Floating IPs*, except the bare minimum (e.g. TCP 80, 443 on web servers). Security groups are selectively opening ports to enforce the policy
-   Access to ANY VM is only made through the salt master acting as a *Jump box*, see [Accessing a VM using SSH](#Accessing_a_VM_using_SSH)
-   Every VM is booted from a basic Ubuntu 14.04 LTS image. A minimal *cloud-init* script installs *salt-minion* and makes it poke the *salt master*.
-   Each VM can consult their initial *cloud-init* script using OpenStack internal API by doing: `curl http://169.254.169.254/openstack/2013-10-17/user_data`
-   The VM name define what softwares, services, and web apps deployed on them. For more details about it, refer to the section about "roles" at [**Roles and environment level**](/WPD:Infrastructure/architecture/Roles_and_environment_level)
-   Monit has automatic service checks definitions installed through Salt stack. [More about **Monit**](/WPD:Infrastructure/Monitoring/Monit) and about how to [get Monit reports](/WPD:Infrastructure/architecture/Reports_to_review_status#Using_Monit).
-   Each VM has a full name describing its role and environment level known internally pointing to private IPs (e.g. *app3-jobrunner.production.wpdn*).

### Every VMs, except ones with the mail role

-   Uses locally configured *exim4* to send email through the *email relay* (*mail.webplatform.org*) allowing us to have only one mail server to maintain.

### Only VMs with mail role

-   The mail relay (e.g. *mail.webplatform.org*) takes care of converting to publicly addressable origin but has headers to know which VM sent the message

### Every VMs that has frontend role

-   At this time they have the name *nginx* in them, they should be renamed *frontend* as its what they’ll do. Besides VMs with the *backend* role will also have NGINX to serve internally static assets for the frontend so it would make more sense to remove potential confusion with the software name

### Every VMs with a backend

At this time its the VM with roles: **app**, **project**, **piwik**, **blog**. But eventually it’ll be attached differently.

-   Every web app configuration (e.g. */srv/salt/code/files/wiki/Settings.php.jinja*) uses Redis and Memcached as if it was local
-   Nutcracker acts as a Redis and Memcached proxy on every VMs of the roles listed above
-   Nutcracker configuration is managed by salt, lists of nodes are in */srv/pillar/infra/staging.sls* with pillar keys *infra:sessions\_redis*, *infra:sessions\_memcache*, *infra:alpha\_redis*, *infra:alpha\_memcache*, list them like this:

<!-- -->

     salt app\* pillar.get infra:sessions_redis

-   Only Sessions data MUST be sent to localhost keystore at default port number, configured at both web app level and/or backend configuration itself (e.g. *php.ini*)
-   Other keystore caches uses a different port, ending by **55** (e.g. Memcached 127.0.0.1:11255, Redis 127.0.0.1:6355) local nutcracker proxy
-   Should have a minimal NGINX server to serve static assets as part of the web software package its serving as a backend. The *frontend* VMs will poll static assets from there.

### VMs with either redis or memcache or session roles

-   Listens on default port on private IPv4 interface of their respective service
-   No web app should call them directly, use Nutcracker as a proxy instead
-   VMs with role *sessions* are separate from the other keystores by design so we can purge data from any other clusters without destroying our user sessions

## Accessing a VM using SSH

To work on any VM on WebPlatform architecture, you have to have one of the site operators to add your SSH public key. Once you have access, you’ll be able to jump to the VMs you are granted access through what’s called a *SSH Jump box*.

One of the common use-case for this setup is to gain access to [WPD:Infrastructure/architecture/Reports\_to\_review\_status](/WPD:Infrastructure/architecture/Reports_to_review_status), or to make some random checks.

The following will explain how you can install on your local machine the configuration you need to connect to the VMs through SSH.

### How it works

In summary, a *SSH Jump box* is basically a way to refer to a VM within a private network using a publicly available SSH server acting as a proxy.

To work on a cluster on a given level, you can use the salt master as a SOCKS proxy to view privileged reports such as service health and usage reports.

To view the internal only reports, configure one of your web browser to use your local computer as a proxy through the SSH tunnel we will create.

     ssh salt.webplatform.org -C -D 1080

This would allow you to connect only to the salt master and have a SOCKS proxy. To access all VMs and simplify the commands to use, read on.

### Setting automatically a SOCKS proxy in your SSH configuration

A reliable solution is to setup your local ssh client to do things for you automatically.

Those things can be done in **\~/.ssh/config** file the following line within the appropriate **Host** block. Or using PuTTY, if you use Windows.

    ### WPD Production
    Host production.wpdn
      Hostname salt.webplatform.org
      ProxyCommand none
      DynamicForward 1080
    Host *.production.wpdn
      ProxyCommand ssh -e @ -o StrictHostKeyChecking=no -a -W %h:%p production.wpdn

**Note** this block is an example of what you can use to have a **DynamicForward** automatically installed.

To connect to the salt master, you’d have to do this instead and all will be setup automatically:

     ssh production.wpdn

You can even connect to a VM directly using the salt master as a *Jump box*

     ssh app1.production.wpdn

To use the proxy, you need at least one SSH connection established to the infrastructure.

**IMPORTANT** Make sure you always use the connection block that the salt master provides you at connection time as this example here might become outdated.

### Configuring a web browser to use the proxy

Once connected, you have to configure a web browser to use your new **DynamicForward** SOCKS proxy.

In modern Firefox version, you can do that by going into **Preferences**, **Advanced**, **Network** tab, then **Connection** button. You’ll see a window similar to below. Adjust accordingly.

![201502-Firefox-Network-settings.png](/WPD/assets/public/e/ee/201502-Firefox-Network-settings.png)

To learn how to configure your web browser to use SSH as a SOCKS proxy, you can view the [SSH Port forwarding help pages on **help.ubuntu.com**](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Dynamic_Port_Forwarding)
