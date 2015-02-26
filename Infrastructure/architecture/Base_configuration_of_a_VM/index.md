{{:WPD:Infrastructure/architecture}}
= Base configuration of a VM =

Here is a few details that every VMs has in common

* Ubuntu 14.04 LTS
* Each VM has a full name describing its role and environment level known internally pointing to private IPs (e.g. ''app3-jobrunner.production.wpdn'').
* Apt has automatic security updates enabled
* IPv6 is supported by DreamCompute, but disabled for the moment
* Private IPv4 networking enabled at ''security groups'' levels accross VMs, adresses are in <code>10.10.10.0/24</code> range (e.g. ''10.10.10.2'').
* Nothing is exposed publicly except the bare minimum
* Access to ANY VM is only made through the salt master acting as a '''JumpBox''', see [[#Accessing_a_VM_using_SSH|Accessing a VM using SSH]]
* Get to know what was the ''cloud-init'' "userdata" scripts given at creation time <code>curl http://169.254.169.254/openstack/2013-10-17/user_data</code>
* The names will define what softwares and web apps are going to be deployed, for more information about how it works see [[WPD:Infrastructure/architecture/Roles_and_environment_level|'''Roles and environment level''']]
* Monit has automatic service checks definitions installed through Salt stack. [[WPD:Infrastructure/Monitoring/Monit|More about '''Monit''']] and about how to [[WPD:Infrastructure/architecture/Reports_to_review_status#Using_Monit|get Monit reports]].


=== Every VMs, except mail ===

* Uses locally configured ''exim4'' to send email through the ''email relay'' (''mail.webplatform.org'') allowing us to have only one mail server to maintain.


=== Mail ===

* The mail relay (e.g. ''mail.webplatform.org'') takes care of converting to publicly addressable origin but has headers to know which VM sent the message

=== Every VMs that runs backend ===

At this time its the VM with roles: '''app''', '''project''', '''piwik''', '''blog'''. But eventually it’ll be attached differently.

* Every web app configuration (e.g. ''/srv/salt/code/files/wiki/Settings.php.jinja'') uses Redis and Memcached as if it was local
* Nutcracker acts as a Redis and Memcached proxy on every VMs of the roles listed above
* Nutcracker configuration is managed by salt, lists of nodes are in ''/srv/pillar/infra/staging.sls'' with pillar keys ''infra:sessions_redis'', ''infra:sessions_memcache'', ''infra:alpha_redis'', ''infra:alpha_memcache'', list them like this:
  salt app\* pillar.get infra:sessions_redis
* Only Sessions data MUST be sent to localhost keystore at default port number, configured at both web app level and/or backend configuration itself (e.g. ''php.ini'')
* Other keystore caches uses a different port, ending by '''55''' (e.g. Memcached 127.0.0.1:11255, Redis 127.0.0.1:6355) local nutcracker proxy 

=== VMs with either redis or memcache or session roles ===

* Listens on default port on private IPv4 interface of their respective service
* No web app should call them directly, use Nutcracker as a proxy instead

== Accessing a VM using SSH ==

To work on any VM on WebPlatform architecture, you have to have one of the site operators to add your SSH public key. Once you have access, you’ll be able to jump to the VMs you are granted access through what’s called a '''SSH Jumpbox'''.

One of the common use-case for this setup is to gain access to [[WPD:Infrastructure/architecture/Reports_to_review_status]], or to make some random checks.

The following will explain how you can install on your local machine the configuration you need to connect to the VMs through SSH.

=== How it works ===

In summary, a ''SSH Jumpbox'' is basically a way to refer to a VM within a private network using a publicly available SSH server acting as a proxy.

To work on a cluster on a given level, you can use the salt master as a SOCKS proxy to view privileged reports such as service health and usage reports.  

To view the internal only reports, configure one of your web browser to use your local computer as a proxy through the SSH tunnel we will create.

  ssh salt.webplatform.org -C -D 1080

This would allow you to connect only to the salt master and have a SOCKS proxy. To access all VMs and simplify the commands to use, read on.

=== Setting automatically a SOCKS proxy in your SSH configuration ===

A reliable solution is to setup your local ssh client to do things for you automatically.

Those things can be done in '''~/.ssh/config''' file the following line within the appropriate '''Host''' block. Or using PuTTY, if you use Windows.

 ### WPD Production
 Host production.wpdn
   Hostname salt.webplatform.org
   ProxyCommand none
   DynamicForward 1080
 Host *.production.wpdn
   ProxyCommand ssh -e @ -o StrictHostKeyChecking=no -a -W %h:%p production.wpdn

'''Note''' this block is an example of what you can use to have a '''DynamicForward''' automatically installed. 

To connect to the salt master, you’d have to do this instead and all will be setup automatically:

  ssh production.wpdn

You can even connect to a VM directly using the salt master as a ''Jump Box''

  ssh app1.production.wpdn

To use the proxy, you need at least one SSH connection established to the infrastructure.

'''IMPORTANT''' Make sure you always use the connection block that the salt master provides you at connection time as this example here might become outdated.


=== Configuring a web browser to use the proxy ===

Once connected, you have to configure a web browser to use your new '''DynamicForward''' SOCKS proxy. 

In modern Firefox version, you can do that by going into '''Preferences''', '''Advanced''', '''Network''' tab, then '''Connection''' button. You’ll see a window similar to below. Adjust accordingly.

[[File:201502-Firefox-Network-settings.png]]
 
To learn how to configure your web browser to use SSH as a SOCKS proxy, you can view the [https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Dynamic_Port_Forwarding SSH Port forwarding help pages on '''help.ubuntu.com''']