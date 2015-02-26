__INDEX__
{{:WPD:Infrastructure/architecture}}
= Roles and environment level =

Each VM has code and configuration deployed to them depending on two factors; ''role'' and environment ''level''. 

;role: defines what gets deployed (e.g. service package, web application, etc).
;level: will ensure deployment specific details (e.g. passwords, keys, SSL certificates, top level domain name, etc) are applied.

This document describes how we define what configuration and code will be applied on a given VM.

== Roles ==

The roles of a VM is defined by its name, more than one role can be assigned on a single VM. 

Roles are parsed from the name as a list of role names separated by dashes, minus any number it might find.  If you have a VM name '''redis-alpha1''', the roles will therefore be: <nowiki>["redis","alpha"]</nowiki>

Some roles are made to ensure configuration based on design decisions (e.g. detect which database VM is the ones we should send writes to). Other roles are about the web application code we deploy, refer to the section  [[WPD:Infrastructure/procedures/Deploying_code_changes#Deploying.2Fupdating_a_web_app|Deploying and/or updating a web app in '''Deploying code changes'']].

For an example of a VM with two roles that doesn’t deploy a web application could be a VM with the name "'''db5-masterdb'''" which would be used as the main ("''masterdb''") database server ("''db''").  Another example would be a VM with the name "''notes''" which installs hypothesis.

The piece of code that makes the parsing is managed by a small piece of Python code in <code>/srv/salt/_grains/purpose.py</code> (see below) that parses the name.

Getting the VM’s ''roles'' can be done like this:

  salt db5-masterdb grains.get roles
  db5-masterdb:
    - db
    - masterdb

Making an action only on VMs that has a given role can be done in one command.

The following command gives the a NGINX status view each VM that has ''nginx'' as a role through [http://docs.saltstack.com/en/latest/ref/modules/all/salt.modules.nginx.html#salt.modules.nginx.status ''Salt Stack'' '''nginx.status''' module], more reports are available in [[WPD:Infrastructure/architecture/Reports_to_review_status]]

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


'''Continue reading about roles in [[WPD:Infrastructure/architecture/VM_roles]]'''

== Level ==

The "''environment level''" is defined as a <code>key: value</code> string (e.g. "level: production") in <code>/etc/salt/grains</code>. That file is created when the VM is created using the salt master managed <code>/srv/opsconfig/userdata.txt</code> '''cloud-init'' boot script.  

Getting the ''environment level'' name that the VM knows it has can be done like this:

  salt vmname grains.get level
  vmname:
    staging

'''Tip''' Its a convention to keep in an OpenStack project ONLY contain ONE environment level. Mixing might cause to confusion and manipulation mistakes.


= Related =

== How salt detects the roles? ==

In the  [https://github.com/webplatform/states states] code, generally available in the salt master <code>/srv/salt/_grains/purpose.py</code>. The code looks like this.

<syntaxHighlight lang=python>
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
</syntaxHighlight>