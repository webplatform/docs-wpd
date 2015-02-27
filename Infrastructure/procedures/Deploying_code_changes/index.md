{{:WPD:Infrastructure/architecture}}
= Deploying code changes =

This document describes how to apply code changes on managed web applications that runs ''webplatform.org''.

The way we update code is handled from the salt master and apply changes where it applies. To see the detail of what every VM has in common, refer to [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM]].

The process of deploying is going to change into something that will allow us to ensure that we can revert to the same state the web app was built from without any risks of broken external dependencies. [https://github.com/webplatform/ops/issues?milestone=1 see the project ''webplatform/ops'' milestone] that has this objective.


== Procedure ==

This procedure will take into account that you have an existing set of VMs already installed  [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM]] and managed by the [[WPD:Infrastructure/architecture/The_salt_master]].

In this example we’ll update the code on all VMs that fills the ''role'' of '''app'''.

'''Related'''; if you want to see how to update a database password, you can also look at [[WPD:Infrastructure/architecture/Useful_commands#Create a database, a user, set new privileges and update a web application]]

* First, make sure the role you want to target touches the VMs you want

  salt app\* grains.get roles
  app1-jobrunner:
    - app
    - jobrunner
  app2:
    - app
  app3:
    - app

=== Running a code update ===

Deploying code on VMs of a given role:

  salt app\* state.sls code

You can also target the same set of VM using salt ''grains'' [http://docs.saltstack.com/en/latest/topics/targeting/grains.html targeting variant];

  salt -G 'roles:app' state.sls code

Which is basically what the following command do;

  wpd-deploy app

The latter is an alias for the comfort of everyday use and can be done without being root.

Output should look like this;

[[File:Running_wpd-deploy.png]]


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

== Related ==

* The detail of what each roles does is described in [[WPD:Infrastructure/architecture/VM_roles]].
* How to replace a VM has details on how to deploy code too [[WPD:Infrastructure/procedures/Replacing_a_VM]].
* To know what code is going to be deployed, refer to [[WPD:Infrastructure/architecture/Roles_and_environment_level]]
* [[WPD:Infrastructure/architecture/Useful_commands#Create a database, a user, set new privileges and update a web application|How to update database details in a web application]]