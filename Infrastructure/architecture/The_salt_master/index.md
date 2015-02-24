{{:WPD:Infrastructure/architecture}}
= The Salt Master =

[[WPD:Infrastructure/procedures/Deploying_code_changes|Deploying code changes on the site]] is made through a VM, named "salt" we refer to this machine as the "Salt Master" we generally connect through SSH at the name '''salt.webplatform.org'''.

The software we use for configuration management is called '''[http://saltstack.com/ Salt Stack]''', we refer to the machine that has a copy of all the configuration files.

Commands that can be done from the salt master VM in the terminal, but some could also be visualized from within your local web browser through [[WPD:Infrastructure/architecture/Reports_to_review_status#Read reports from a VM through private network|Read reports from a VM through private network]] in [[WPD:Infrastructure/architecture/Reports_to_review_status]].