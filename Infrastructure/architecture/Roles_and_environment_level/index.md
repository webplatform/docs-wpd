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

'''Continue reading about roles in [[WPD:Infrastructure/architecture/VM_roles]]'''

== Level ==

The level is defined as a simple "<code>level: production</code>" line in <code>/etc/salt/grains</code>. That file is created when the VM boots for the first time from the salt master using.

Getting the level that the VM knows it has would be done like this:

'''Tip''' Its a convention to keep in an OpenStack project ONLY contain ONE environment level. Mixing might cause to confusion and manipulation mistakes.