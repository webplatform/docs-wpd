---
title: Deploying code changes
uri: 'WPD:Infrastructure/procedures/Deploying code changes'

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

-   **Deploying code changes**
-   [Replacing a VM](/WPD:Infrastructure/procedures/Replacing_a_VM)
-   [Maintaining Fastly configuration](/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration)
-   [Managing MySQL replication](/WPD:Infrastructure/procedures/Managing_MySQL_replication)
-   [Create new database credentials and configure a web application to use it](/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it)
-   [Maintaining ElasticSearch cluster](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster)
-   [Maintaining email services](/WPD:Infrastructure/procedures/Maintaining_email_services)

This document describes how to apply code changes on managed web applications that runs *webplatform.org*.

The way we update code is handled from the salt master and apply changes where it applies. To see the detail of what every VM has in common, refer to [WPD:Infrastructure/architecture/Base\_configuration\_of\_a\_VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM).

The process of deploying is going to change into something that will allow us to ensure that we can revert to the same state the web app was built from without any risks of broken external dependencies. [see the project *webplatform/ops* milestone](https://github.com/webplatform/ops/issues?milestone=1) that has this objective.

## Procedure

This procedure will take into account that you have an existing set of VMs already installed [WPD:Infrastructure/architecture/Base\_configuration\_of\_a\_VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM) and managed by the [WPD:Infrastructure/architecture/The\_salt\_master](/WPD:Infrastructure/architecture/The_salt_master).

In this example we’ll update the code on all VMs that fills the *role* of **app**.

**Related**; if you want to see how to update a database password and apply the changes to a managed web application, go to [Create new database credentials and configure a web application to use it](/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it)

-   First, make sure the role you want to target touches the VMs you want

<!-- -->

     salt app\* grains.get roles
     app1-jobrunner:
       - app
       - jobrunner
     app2:
       - app
     app3:
       - app

### Running a code update

Deploying code on VMs of a given role:

     salt app\* state.sls code

You can also target the same set of VM using salt *grains* [targeting variant](http://docs.saltstack.com/en/latest/topics/targeting/grains.html);

     salt -G 'roles:app' state.sls code

Which is basically what the following command do;

     wpd-deploy app

The latter is an alias for the comfort of everyday use and can be done without being root.

Output should look like this;

![Running wpd-deploy.png](/WPD/assets/public/0/0d/Running_wpd-deploy.png)

## Deploying/updating a web app

ANY deployment is made through Salt Stack. The deployment code is publicly available on *GitHub* as [**webplatform/salt-states**](https://github.com/webplatform/salt-states).

Each role name states are defined in an *sls* file in `/srv/salt/roles` and from there, you’ll see any rsync scripts it uses to copy code the salt master hosts in */srv/code/foo/repo*.

**NOTE** the command *wpd-deploy foo* **ISN’T LIMITED** to copying files from folders in */srv/code/foo/bar*, its also about ensuring that some configuration are applied. Its prudent to double check what will happen always check the matching state (e.g. *wpd-deploy foo*) in the matching *sls* file (e.g. */srv/salt/roles/foo.sls*)

To update a webapp, run the following commands. Salt will know which VM has to get the code:

app
:   `wpd-deploy app`  [''/srv/code/www/repo'', ''/srv/code/compat/repo'', ''/srv/code/dabblet/repo'', ''/srv/code/wiki/repo'']
blog
:   `wpd-deploy blog`  [''/srv/code/blog/repo'']
notes
:   `wpd-deploy notes`  [''/srv/code/notes-server/repo'']
piwik
:   `wpd-deploy piwik`  [''/srv/code/piwik/repo'']
project
:   `wpd-deploy project`  [''/srv/code/buggenie/repo'']
accounts
:   `wpd-deploy accounts`

## Related

-   The detail of what each roles does is described in [WPD:Infrastructure/architecture/VM\_roles](/WPD:Infrastructure/architecture/VM_roles).
-   How to replace a VM has details on how to deploy code too [WPD:Infrastructure/procedures/Replacing\_a\_VM](/WPD:Infrastructure/procedures/Replacing_a_VM).
-   To know what code is going to be deployed, refer to [WPD:Infrastructure/architecture/Roles\_and\_environment\_level](/WPD:Infrastructure/architecture/Roles_and_environment_level)
-   [How to update database details in a web application](/WPD:Infrastructure/architecture/Useful_commands#Create_a_database.2C_a_user.2C_set_new_privileges_and_update_a_web_application)
