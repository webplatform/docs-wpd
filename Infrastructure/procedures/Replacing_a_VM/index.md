---
title: 'Replacing a VM'
uri: 'WPD:Infrastructure/procedures/Replacing a VM'

---
### [WebPlatform server Infrastructure architecture menu](/WPD:Infrastructure/architecture)

-   [Base configuration of a VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM)
-   [Reports to review status](/WPD:Infrastructure/architecture/Reports_to_review_status)
-   [Roles and environment level](/WPD:Infrastructure/architecture/Roles_and_environment_level)
-   [SSL certificates](/WPD:Infrastructure/architecture/SSL_certificates)
-   [The salt master](/WPD:Infrastructure/architecture/The_salt_master)
-   [Things to consider when we expose service via Fastly and Varnish](/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish)
-   [Useful commands](/WPD:Infrastructure/architecture/Useful_commands)
-   [VM roles](/WPD:Infrastructure/architecture/VM_roles)

**See also**

-   [Deploying code changes](/WPD:Infrastructure/procedures/Deploying_code_changes)
-   **Replacing a VM**
-   [Maintaining Fastly configuration](/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration)
-   [Managing MySQL replication](/WPD:Infrastructure/procedures/Managing_MySQL_replication)
-   [Create new database credentials and configure a web application to use it](/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it)
-   [Maintaining ElasticSearch cluster](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster)
-   [Maintaining email services](/WPD:Infrastructure/procedures/Maintaining_email_services)

This document describes how to replace any VM in an existing deployment (e.g. staging) with a new one, install/update targeted web application and apply current configurations. All of that is done in a way that we can replace a faulty VM without affecting the site uptime.

Using our *Salt Stack* (not published yet, see */srv/salt* and *WebPlatform GitHub operations issue tracker*, at **[webplatform/ops\#48](https://github.com/webplatform/ops/issues/48)**), rebuilding a VM is reduced to a few commands and makes it cheap to replace any components which gives us the insurance that we can consistently have the same outcome.

**Remember** most recurring commands are listed at the bottom of `/srv/salt/README.md` on the salt master.

## Introduction

**EVERYTHING** in WebPlatform infrastructure is managed through source control, including what configures (i.e. the [states](https://github.com/webplatform/states)) from the VM acting as a *salt-master*, every VM can be replaced at will. Our infrastructure and scripts are specifically crafted to communicate with an [OpenStack cluster](http://www.openstack.org/). Over the years we’ve moved from multiple clusters without any problems and we are very happy with how reliable the *OpenStack* components are.

Our infrastructure runs currently on **[DreamCompute](http://www.dreamhost.com/cloud/computing/)**, a managed OpenStack cluster graciously sponsored to us by **[DreamHost](http://www.dreamhost.com/)** and the configuration is managed by a software called **[Salt Stack](http://saltstack.com/)**.

## Procedure

In this procedure we will replace a app2 VM with another that has more *vRAM* and *vCPU*.

Technically OpenStack allows us to "resize" a VM and after a few minutes get the new capacity. Depending of the OpenStack deployment, its even possible to make such resizes without interruption. For the purpose of this tutorial, we’ll walk through the steps of replacing a VM regardless of whether or not our current OpenStack host supports resizing.

Since we have either Fastly or a NGINX proxy in front of most web applications, the fact that a VM isn’t live doesn’t break the site as the frontends already takes care of asking other VMs in the same cluster.

In the end of this document, we will should be able to swap two VMs without interruptions.

**About Fastly/Varnish** if you need to work with Fastly/Varnish, refer to [WPD:Infrastructure/procedures/Maintaining\_Varnish\_or\_Fastly\_configuration](/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration)

**Note**; the output of the commands shown in this document were done from the staging deployment level.

### Get the details of one VM

     nova list | grep app2
     | ... | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.215, 173.236.254.224 |

We know that *app2* has two IP addresses assigned

-   private: *10.10.10.215*
-   public: *173.236.254.224*. If we look at the *Fastly* dashboard, we should have this IP in; *docs (staging)*, *www (staging)*, *code (staging)* services.

What is the flavor (i.e. Size of RAM and number of CPUs) *app2* has?

     nova show app2|grep flavor
     | flavor                               | supersonic (200)                                                       |

 What *supersonic* has (showing only some here);

     nova flavor-list
     +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+
     | ID  | Name       | Memory_MB | Disk | Ephemeral | Swap | VCPUs | RXTX_Factor | Is_Public |
     +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+
     | 100 | subsonic   | 1024      | 80   | 0         |      | 1     | 1.0         | True      |
     | 200 | supersonic | 2048      | 80   | 0         |      | 1     | 1.0         | True      |
     | 300 | lightspeed | 4096      | 80   | 0         |      | 2     | 1.0         | True      |
     +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+

### Prepare to replace app2

Let’s unregister *app2*’s *salt-minion* from the *salt-master*

     salt-key -y -d app2

*app2* still has its public IP address —we didn’t delete it— we only did remove it from the *salt-master*. Benefit here is that we will refer to our new VM as *app2* without conflicts when interacting via the *salt* commands.

**Tip** Unless the VM in question is "*flapping*" (inconsistently breaks the site), we could delete the faulty VM right away. If that VM is behind a proxy such as *Fastly* or part of a NGINX backends, other servers will take the load until a new one is in place.

### Create a new VM

Boot a new VM;

    nova boot --image Ubuntu-14.04-Trusty --user-data /srv/opsconfigs/userdata.txt --key_name renoirb-staging --flavor lightspeed --security-groups default,frontend app2

Notice a few details:

`/srv/opsconfigs/userdata.txt`
:   is a configuration file that gets adjusted by the salt master from the salt master itself. It enforces a few details such as DNS and the IP address of the salt master
`--key_name renoirb-staging`
:   assumes you would have your own passphrase protected SSH public key in the OpenStack Horizon dashboard
`--security-groups default,frontend`
:   Are the firewall rules managed by OpenStack, make sure they exists in the OpenStack Horizon dashboard

**Tip** Since every VM has a private network and that we dont give public IP address to all of them, we instead give a passphrase protected SSH public key per user, per environment. The reason is that if it is required to SSH to a new VM that didn’t yet have had "state.highstate" run on it, you won’t be able to access it anyway. To do so, make sure the OpenStack Horizon dashboard has at least two public keys and that you made a copy of both public and private keys in the private pillars in */srv/private/pillars/sshkeys/* on the salt master.

### Wait until the VM is ready

The *cloud-init* script we gave at */srv/opsconfigs/userdata.txt* does also ensure the VM will have the lastest version of everything, plus salt stack minion installed.

That way, all we have to do is to check from the salt master if we can see it.

     salt-key
     Accepted Keys:
       accounts
       app1
       app3
       backup
       blog
       db1-masterdb
       elastic
       mail
       memcache-alpha1
       notes
       piwik
       project
       redis-alpha1
       salt
       sessions1
     Unaccepted Keys:
       app2
     Rejected Keys:

We should see **app2** in **Unaccepted Keys**, we can accept the new VM like this:

     salt-key -y -a app2

Then, wait a few seconds. You can see if the VM is ready by issuing a *test.version* command.

     salt app2 test.version

*Note* Accepting a new VM to the salt master is very quick. Sometimes it takes more time to get a response because the salt master might have a few automated scripts to run. Those scripts are called **Salt Reactor** (see *`/srv/salt/reactor/reactions/*.sls`*) that are configured to run when a VM has been added.

### The VM is ready

Once the "test.version" test answers quickly, we are ready to continue. Before going any further, always run a sanity check if the VM has the essential "level" grain at the value. In our case, we should get "staging".

     salt app2 grains.get level
     app2:
        staging

We are ready!

**Tip** every salt commands are run from their targeted minion (in this example; *app2*). It means that if we lose SSH connection from the master will not break the salt run. In fact the command waits for the execution to complete as a comfort for us.

     salt app2 state.highstate

Go drink a glass of water. It takes a while.

## Replacing something else than app2?

Replacing a *web app runner* role VM such as *app*, *piwik*, *project*, or *notes* is pretty straight forward.

In other cases, we need also to update the a few pillars of the current environment.

The essential pillars to look for are the following:

-   `/srv/private/pillar/accounts/staging.sls`
-   `/srv/private/pillar/accounts/staging_oauth.sls`
-   `/srv/pillar/infra/staging.sls`

**Tip** if you are in "production" level, just look at the files with **production** instead.

The rule of thumb is that what’s in **/srv/pillar** MUST have nothing private as its publicly visible on GitHub.

All private data is stored in **/srv/private** and have its own separate Git repository that only trusted people should have access.

Here are a few situations where you have to update contents in one of those files:

### Infra pillar

The configurations in **/srv/pillar/infra/** are mostly about what’s the current IP address to use for a given use. Each configuration file (in **/srv/salt/code/files**) gets the exact IP it need from there.

-   Adding/Removing a VM with the **memcached** role
-   Adding/Removing a VM with the **sessions** role
-   Adding/Removing a VM with the **redis** role
-   Adding/Removing a VM with the **db** role
-   Adding/Removing a VM with the **elastic** role
-   Adding/Removing a VM with the **mail** role
-   Update the internal DNS zone (**gdnsd\_timestamp**). Most useful if you change any of the above

### Accounts pillar

This is where we store the private data. Database passwords, external providers API keys and so on. The convention is to have a specific set per environment level so we keep a separate deployment and can throughly test every layers somewhere safe before affecting the live site.

-   Every password and private keys are stored in **/srv/private/pillar/accounts/staging.sls**.
-   Accounts system OAuth2 relying parties client configurations and private keys are in **/srv/private/pillar/accounts/staging\_oauth.sls**.

With this, it will be possible to change service passwords across only by changing the private pillar and the service itself. Each relying web application will read the new password from there.

## Apply configuration and code packages

@@TODO adjust once we harmonized the way to install web apps.

To apply configuration according to current set of VMs we have do the following.

**Tip** always make sure every VM are "awake" and replies to ping commands before running them. You can run the following commands a few times, sometimes some might been sleepy.

     salt-run manage.status
     down:
     up:
       - accounts
       - app1
       - app2
       - app3
       - backup
       - blog
       - db1-masterdb
       - elastic
       - mail
       - memcache-alpha1
       - notes
       - piwik
       - project
       - redis-alpha1
       - salt
       - sessions1

Now let’s deploy the code and apply regenerate configuration files

     wpd-deploy app

This commands ensures that configuration files are applied on top of each web app with the current configuration. This ensure that can minimize hardcoded information.

The output should look like this;

![Running wpd-deploy.png](//static.webplatform.org/0/0d/Running_wpd-deploy.png)

## Testing before flipping the switch?

If you are testing a new configuration or plugin, it might be prudent to ensure that what you’ve worked on works before making it visible through the sites (i.e. **webplatformstaging.org** or **webplatform.org**). To do we can map a temporary public IP address and add it to your local **hosts** file.

You can do so by following the next steps with another IP address, or use the OpenStack Horizon Dashboard the site is running on. Technically each VM requires first to have a public IP address so that a proxy (in most case; Fastly) can serve from it.

Remember that each web app is deployed based on the role name, you can get them in [WPD:Infrastructure/procedures/Deploying\_code\_changes\#Deploying.2Fupdating\_a\_web\_app](/WPD:Infrastructure/procedures/Deploying_code_changes#Deploying.2Fupdating_a_web_app).

## Prepare to flip the Floating IP address

Let’s get the network adapter details of our new VM. This procedure will take into account that we didn’t test with another temporary IP address.

**Note** you might get two entries if you didn’t delete yet the old VM, the new VM should be the one that has only a private IP address.

-   We first need to know what is the private IP address of our VMs

<!-- -->

     nova list | grep app2
     | ... | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.218 |
     | ... | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.215, 173.236.254.224 |

Remember when we asked app2 what was their public and private IP addresses.

Old app2 has:

-   10.10.10.215 (private)
-   173.236.254.224 (public, that we’ll give to the new app2)

New app2 has:

-   10.10.10.218 (private)

## Flipping the floating IP

The following commands in the order in which we need the proper values. Each field are generally hexadecimal strings of about 64 characters and dashes. In this example, they are replaced as "foo" and "bar" to illustrate their appropriate positions.

-   Get the **id** of the floating IP we need. Fields from this command are in the order: id, fixed IP address, Floating IP address, port Id. We only care about the id, here: **foo**.

<!-- -->

     neutron floatingip-list | grep 173.236.254.224
     | foo |  10.10.10.215   |  173.236.254.224  |    |

-   We also need what’s called the port id identifier. Its the first column, here: "bar".

<!-- -->

     neutron port-list | grep 10.10.10.218
     | bar |      | fa:16:3e:c1:6c:a0 | {"subnet_id": "...", "ip_address": "10.10.10.218"}

-   We do have what we need to assign, enter them in this order:

<!-- -->

     neutron floatingip-associate --fixed-ip-address 10.10.10.218 foo bar

The new vm *app2* has now the public IP and the old VM is not used anymore

## Delete the old app2 VM

Now that we have two app2 VMs in our OpenStack cluster, we cannot refer to the name to *nova*. Not a big deal, we can use the uuid string to refer to a VM. Note that I renamed the UUID here as "buzz" and "bizz", they won’t look like this in a real deployment.

Since we already know that we just changed the Floating IP to the *app2* VM we want to keep, it means that we know which one to delete.

     nova list | grep app2
     | buzz | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.215 |
     | bizz | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.218, 173.236.254.224 |

We can delete the VM

     nova delete buzz

We are done!
