{{:WPD:Infrastructure/architecture}}
= Deploying code changes =

This document describes how to apply code changes on managed web applications that runs ''webplatform.org''.

The way we update code is handled from the salt master and apply changes where it applies. To see the detail of what every VM has in common, refer to [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM|Base configuration of a VM]].

The process of deploying is going to change into something that will allow us to ensure that we can revert to the same state the web app was built from without any risks of broken external dependencies. [https://github.com/webplatform/ops/issues?milestone=1 see the project ''webplatform/ops'' milestone] that has this objective.


== Procedure ==

This procedure will take into account that you have an existing set of VMs already installed  [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM]] and managed by the [[WPD:Infrastructure/architecture/The_salt_master]].

To learn how to replace a VM, refer to [[WPD:Infrastructure/procedures/Replacing_a_VM|'''Replacing a VM''' procedure]]

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