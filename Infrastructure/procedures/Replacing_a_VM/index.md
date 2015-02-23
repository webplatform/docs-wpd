{{:WPD:Infrastructure/architecture}}
= Replacing a VM =

This document will describe how you can replace any VM in an existing deployment (e.g. production) with a new one.

This kind of action is most useful when we feel a VM has been compromised, or broken. Every VM, including the salt master, is designed to be replaceable parts of a cluster.

'''Note'''; the output of the commands shown here were done from the staging deployment level.

== Procedure ==

In this exercise we will replace a functioning app2 VM with a bigger one.

Technically OpenStack allows us to "resize" a VM and after a few minutes get the new capacity. Depending of the OpenStack deployment, its even possible to make such resizes without interruption.

Since we have either Fastly or a NGINX proxy in front of most web applications, the fact that a VM isn’t live doesn’t break the site as the frontends already takes care of asking other VMs in the same cluster.

You will see that the new VM is taken into account only when we apply the public IP address to it.

=== Get the details of one VM ===

  nova list | grep app2
  | ... | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.215, 173.236.254.224 |

We know that ''app2'' has two IP addresses assigned

* private: ''10.10.10.215''
* public: ''173.236.254.224''. If we look at the ''Fastly'' dashboard, we should have this IP in; ''docs (staging)'', ''www (staging)'', ''code (staging)'' services.

What is the flavor (i.e. Size of RAM and number of CPUs)  app2 has?

  nova show app2|grep flavor
  | flavor                               | supersonic (200)                                                       |


What ''supersonic'' has (showing only some here);

  nova flavor-list
  +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+
  | ID  | Name       | Memory_MB | Disk | Ephemeral | Swap | VCPUs | RXTX_Factor | Is_Public | 
  +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+
  | 100 | subsonic   | 1024      | 80   | 0         |      | 1     | 1.0         | True      |
  | 200 | supersonic | 2048      | 80   | 0         |      | 1     | 1.0         | True      |
  | 300 | lightspeed | 4096      | 80   | 0         |      | 2     | 1.0         | True      |
  +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+


=== Prepare to replace app2 ===
  
Since we are going to delete ''app2'' here, we can remove it from our salt master and boot a new one.

  salt-key -y -d app2

The VM ''app2'' still has its public IP address, we only removed it from salt so we can use that name again.

Let’s not delete the VM right away. Unless, of course, the VM in question has "flapping" services (i.e. on-off) and breaks the live site.


=== Create a new VM ===

 nova boot --image Ubuntu-14.04-Trusty --user-data /srv/opsconfigs/userdata.txt --key_name renoirb-staging --flavor lightspeed --security-groups default,frontend app2

Notice a few details:

;<code>/srv/opsconfigs/userdata.txt</code>: is a configuration file that gets adjusted by the salt master from the salt master itself. It enforces a few details such as DNS and the IP address of the salt master
;<code>--key_name renoirb-staging</code>: assumes you would have your own passphrase protected SSH public key  in the OpenStack Horizon dashboard
;<code>--security-groups default,frontend</code>: Are the firewall rules managed by OpenStack, make sure they exists in the OpenStack Horizon dashboard

'''Tip''' Since every VM has a private network and that we dont give public IP address to all of them, we instead give a passphrase protected SSH public key per user, per environment. The reason is that if it is required to SSH to a new VM that didn’t yet have had "state.highstate" run on it, you won’t be able to access it anyway. To do so, make sure the OpenStack Horizon dashboard has at least two public keys and that you made a copy of both public and private keys in the private pillars in ''/srv/private/pillars/sshkeys/'' on the salt master.

'''Remember''' most recurring commands are listed at the bottom of <code>/srv/salt/README.md</code> on the salt master.

=== Wait until the VM is ready ===

The ''cloud-init'' script we gave at ''/srv/opsconfigs/userdata.txt'' does also ensure the VM will have the lastest version of everything, plus salt stack minion installed.

That way, all we have to do is to check from the salt master if we can see it.

  salt-keysalt-key
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

We should see '''app2''' in '''Unaccepted Keys''', we can accept the new VM like this:

  salt-key -y -a app2

Then, wait a few seconds. You can see if the VM is ready by issuing a ''test.version'' command.

  salt app2 test.version

''Note'' Accepting a new VM to the salt master is very quick. Sometimes it takes more time to get a response because the salt master might have a few automated scripts to run. Those scripts are called '''Salt Reactor''' (see ''<code>/srv/salt/reactor/reactions/*.sls</code>'') that are configured to run when a VM has been added.


=== The VM is ready ===

Once the "test.version" test answers quickly, we are ready to continue.  Before going any further, always run a sanity check if the VM has the essential "level" grain at the value. In our case, we should get "staging".

  salt app2 grains.get level
  app2:
     staging

We are ready! 

'''Tip''' every salt commands are run from their targeted minion (in this example; ''app2''). It means that if we lose SSH connection from the master will not break the salt run. In fact the command waits for the execution to complete as a comfort for us.

  salt app2 state.highstate

Go drink a glass of water. It takes a while.

== Apply configuration and code packages ==

@@TODO adjust once we harmonized the way to install web apps.

To apply configuration according to current set of VMs we have do the following.

'''Tip''' always make sure every VM are "awake" and replies to ping commands before running them. You can run the following commands a few times, sometimes some might been sleepy.

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

This commands ensures that configuration files are applied on top of each web app with the current configuration.  This ensure that can minimize hardcoded information.

The output should look like this;

[[File:Running_wpd-deploy.png]]

== Testing before flipping the switch? ==

If you are testing a new configuration or plugin, it might be prudent to ensure that what you’ve worked on works before making it visible through the sites (i.e. '''webplatformstaging.org''' or '''webplatform.org'''). To do we can map a temporary public IP address and add it to your local '''hosts''' file.

You can do so by following the next steps with another IP address, or use the OpenStack Horizon Dashboard the site is running on. Technically each VM requires first to have a public IP address so that a proxy (in most case; Fastly) can serve from it.

Remember that each web app is deployed based on the role name, you can get them in [[WPD:Infrastructure/procedures/Deploying_code_changes#Deploying.2Fupdating_a_web_app|Deploying code changes at ''Deploying/updating a web app]].

== Prepare to flip the Floating IP address ==

Let’s get the network adapter details of our new VM. This procedure will take into account that we didn’t test with another temporary IP address.

'''Note''' you might get two entries if you didn’t delete yet the old VM, the new VM should be the one that has only a private IP address.

* We first need to know what is the private IP address of our VMs

  nova list | grep app2
  | ... | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.218 |
  | ... | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.215, 173.236.254.224 |

Remember when we asked app2 what was their public and private IP addresses.

Old app2 has:
* 10.10.10.215 (private)
* 173.236.254.224 (public, that we’ll give to the new app2)

New app2 has:
* 10.10.10.218 (private)


== Flipping the floating IP ==

The following commands in the order in which we need the proper values. Each field are generally hexadecimal strings of about 64 characters and dashes. In this example, they are replaced as "foo" and "bar" to illustrate their appropriate positions.

* Get the '''id'' of the floating IP we need. Fields from this command are in the order: id, fixed IP address, Floating IP address, port Id. We only care about the id, here: '''foo'''.

  neutron floatingip-list | grep 173.236.254.224
  | foo |  10.10.10.215   |  173.236.254.224  |    |

* We also need what’s called the port id identifier. Its the first column, here: "bar".

  neutron port-list | grep 10.10.10.218
  | bar |      | fa:16:3e:c1:6c:a0 | {"subnet_id": "...", "ip_address": "10.10.10.218"}

* We do have what we need to assign, enter them in this order:

  neutron floatingip-associate --fixed-ip-address 10.10.10.218 foo bar

The new vm ''app2'' has now the public IP and the old VM is not used anymore