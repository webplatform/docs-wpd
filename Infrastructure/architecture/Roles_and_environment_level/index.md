---
title: Roles and environment level
uri: 'WPD:Infrastructure/architecture/Roles and environment level'

---
### [WebPlatform server Infrastructure architecture menu](/WPD:Infrastructure/architecture)

-   [Base configuration of a VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM)
-   [Reports to review status](/WPD:Infrastructure/architecture/Reports_to_review_status)
-   **Roles and environment level**
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

Each VM has code and configuration deployed to them depending on two factors; *role* and environment *level*.

role
:   defines what gets deployed (e.g. service package, web application, etc).
level
:   will ensure deployment specific details (e.g. passwords, keys, SSL certificates, top level domain name, etc) are applied.

This document describes how we define what configuration and code will be applied on a given VM.

## Roles

The roles of a VM is defined by its name, more than one role can be assigned on a single VM.

Roles are parsed from the name as a list of role names separated by dashes, minus any number it might find. If you have a VM name **redis-alpha1**, the roles will therefore be: ["redis","alpha"]

Some roles are made to ensure configuration based on design decisions (e.g. detect which database VM is the ones we should send writes to). Other roles are about the web application code we deploy, refer to the section [Deploying and/or updating a web app in **Deploying code changes**](/WPD:Infrastructure/procedures/Deploying_code_changes#Deploying.2Fupdating_a_web_app).

For an example of a VM with two roles that doesn’t deploy a web application could be a VM with the name "**db5-masterdb**" which would be used as the main ("*masterdb*") database server ("*db*"). Another example would be a VM with the name "*notes*" which installs hypothesis.

The piece of code that makes the parsing is managed by a small piece of Python code in `/srv/salt/_grains/purpose.py` (see below) that parses the name.

Getting the VM’s *roles* can be done like this:

     salt db5-masterdb grains.get roles
     db5-masterdb:
       - db
       - masterdb

Making an action only on VMs that has a given role can be done in one command.

The following command gives the a NGINX status view each VM that has *nginx* as a role through [*Salt Stack* **nginx.status** module](http://docs.saltstack.com/en/latest/ref/modules/all/salt.modules.nginx.html#salt.modules.nginx.status), more reports are available in [WPD:Infrastructure/architecture/Reports\_to\_review\_status](/WPD:Infrastructure/architecture/Reports_to_review_status)

     salt -G 'roles:nginx' nginx.status
     specs-nginx:
       ----------
       accepted:
           3052
       active connections:
           1
       handled:
           3052
       reading:
           0
       requests:
           3045
       waiting:
           0
       writing:
           1
     ...

**Continue reading about roles in [WPD:Infrastructure/architecture/VM\_roles](/WPD:Infrastructure/architecture/VM_roles)**

## Level

The "*environment level*" is defined as a `key: value` string (e.g. "level: production") in `/etc/salt/grains`. That file is created when the VM is created using the salt master managed `/srv/opsconfig/userdata.txt` **cloud-init** boot script.

Getting the *environment level* name that the VM knows it has can be done like this:

     salt vmname grains.get level
     vmname:
       staging

**Tip** Its a convention to keep in an OpenStack project ONLY contain ONE environment level. Mixing might cause to confusion and manipulation mistakes.

# Related

## How salt detects the roles?

In the [salt-states](https://github.com/webplatform/salt-states) code repository, generally available in the salt master `/srv/salt/_grains/purpose.py`. The code looks like this.

```
#!/usr/bin/env python

import socket
from string import digits

hostname = socket.gethostname().translate(None, digits)

def roles():
        '''
        Parse the host hostname and creates a list of roles

        Based on the hostname (without domain name), should return:

                salt            -> grain:roles: ["salt"]
                redis-jobs1     -> grain:roles: ["redis","jobs"]

        '''
        dataObject = {'roles': hostname.split('-')}
        return dataObject
```
