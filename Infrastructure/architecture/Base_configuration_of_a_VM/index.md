{{:WPD:Infrastructure/architecture}}
= Base configuration of a VM =

Here is a few details that every VMs has in common

* Ubuntu 14.04 LTS
* Automatic security updates
* IPv6 disabled
* Monit, read more at [[WPD:Infrastructure/Monitoring/Monit]]
* Private IPv4 networking enabled accross VMs, adresses are in <code>10.10.10.0/24</code> range (e.g. ''10.10.10.2'').
* Get to know what was the ''cloud-init'' "userdata" scripts given at creation time <code>curl http://169.254.169.254/openstack/2013-10-17/user_data</code>