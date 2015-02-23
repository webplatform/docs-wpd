{{:WPD:Infrastructure/architecture}}
= The Salt Master =

[[WPD:Infrastructure/procedures/Deploying_code_changes|Deploying code changes on the site]] is made through a VM, named "salt" we refer to this machine as the "Salt Master" we generally connect through SSH at the name '''salt.webplatform.org'''.

The software we use for configuration management is called "[http://saltstack.com/ Salt Stack]", we refer to the machine that has a copy of all the configuration files