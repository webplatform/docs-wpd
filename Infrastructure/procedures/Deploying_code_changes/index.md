{{:WPD:Infrastructure/architecture}}
= Deploying code changes =

This document describes how to apply code changes on managed web applications that runs ''webplatform.org''.

The way we update code is handled from the salt master and apply changes where it applies. To see the detail of what every VM has in common, refer to [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM]].

The process of deploying is going to change into something that will allow us to ensure that we can revert to the same state the web app was built from without any risks of broken external dependencies. [https://github.com/webplatform/ops/issues?milestone=1 see the project ''webplatform/ops'' milestone] that has this objective.


== Procedure ==

This procedure will take into account that you have an existing set of VMs already installed  [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM]] and managed by the [[WPD:Infrastructure/architecture/The_salt_master]].

The following will show you how we can replace an existing VM that we want to replace with a new one.

== Booting a VM ==

Let’s replace a app1 with a brand new instance.

To To boot a VM, its better to use the salt master and issue a '''nova''':

  nova boot --image Ubuntu-14.04-Trusty --user-data /srv/opsconfigs/userdata.txt --key_name renoirb-staging --flavor lightspeed --security-groups default,frontend app1

The previous command assumes that DreamCompute dashboard has some of your own SSH public keys. Normally I recommend that it has two keys, one per deployment level. 

'''Tip''': Since every VM has a private network and that we dont give public IP address to all of them, we instead give a passphrase protected SSH public key per user, per environment. The reason is that if it is required to SSH to a new VM that didn’t yet have had "state.highstate" run on it, you won’t be able to access it anyway. To do so, make sure the OpenStack Horizon dashboard has at least two public keys and that you made a copy of both public and private keys in the private pillars in '''/srv/private/pillars/sshkeys/'' on the salt master.

Now that a VM is booted, here’s how we initiate it;

  salt-key -y -a app1
  salt app1 grains.get level
  salt app1 state.highstate

The four previous commands do the following;

# add the new VM to the salt master
# Its a sanity check to see what’s the value of ''level'' grain (e.g. staging, production) to confirm it has what we expect
# run ''state.highstate'', and go get some water (it takes some time to run)

'''Tip''' most important commands are available in <code>/srv/salt/README.md</code> on the salt master.

=== Typical commands ===

You can get to know which level a VM is configured by running;

  salt project grains.get level
  project:
    production

To work with a VM, you can target actions based on their roles;

Getting the roles of a VM:

  salt db\* grains.get roles
  db1-masterdb:
    - db
    - masterdb
  db2:
    - db

'''Note''' the number are only there to allow us to quickly differentiate them, you should see here that the role names doesn’t have numbers in them. 

Deploying code on VMs of a given role:

  salt app\* state.sls code

Which is basically what the following command do;

  wpd-deploy app

The latter is an alias for the comfort of everyday use and can be done without being root.


== Deploying/updating a web app ==

Each role name states are defined in an ''sls'' file in <code>/srv/salt/vm</code> (yeah, its a bad name, it’ll change!) and from there, you’ll see any rsync scripts it uses to copy code the salt master hosts in ''/srv/code/foo/repo''. 

'''NOTE''' the command ''wpd-deploy foo'' '''ISN’T LIMITED''' to copying files from folders in ''/srv/code/foo/bar'', its also about ensuring that some configuration are applied.  Its prudent to double check what will happen always check the matching state (e.g.  ''wpd-deploy foo'') in the matching ''sls'' file (e.g. ''/srv/salt/vm/foo.sls'')

To update a webapp, run the following commands. Salt will know which VM has to get the code:

;app:<code>wpd-deploy app</code>&nbsp;&nbsp;<nowiki>[''/srv/code/www/repo'', ''/srv/code/compat/repo'', ''/srv/code/dabblet/repo'', ''/srv/code/wiki/repo'']</nowiki>
;blog:<code>wpd-deploy blog</code>&nbsp;&nbsp;<nowiki>[''/srv/code/blog/repo'']</nowiki>
;notes:<code>wpd-deploy notes</code>&nbsp;&nbsp;<nowiki>[''/srv/code/notes-server/repo'']</nowiki>
;piwik:<code>wpd-deploy piwik</code>&nbsp;&nbsp;<nowiki>[''/srv/code/piwik/repo'']</nowiki>
;project:<code>wpd-deploy project</code>&nbsp;&nbsp;<nowiki>[''/srv/code/buggenie/repo'']</nowiki>
;accounts:<code>wpd-deploy accounts</code>

The detail of what each roles does is described in [[WPD:Infrastructure/architecture/VM_roles]].

=== Screenshot ===

[[File:screenshot-wpd-deploy-project-run.png]]