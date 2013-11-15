= Infrastructure Maintenance Workflows =

== Summary ==
This document describe how to work on the infrastructure, to commission/de-commision services, and work on the infrastructure and making it as transparent as possible.

== Required tools ==
# Installing Vagrant with Salt stack, see [[WPD:Infrastructure/procedures/Creating local multiple virtual machine state development environment]]

=== States repositories ===

We can use our own internal repositories. 

''NOTE'': I am currently importing them at the moment and this section is going to be adjusted accordingly.

Please note that I am currently searching a way to fork the states depending on the environment, for example during the development of a new tool, we might not need ALL instances (memcached, storage, etc). 

This means that part of the work to do is to actually separate the states definitions and be able to declare within our environment that we are replicating the production but not in production.

Currently, the repositories are hosted in renoirb@jay.w3.org:~/git/wpd/deployment/  and are copied from my local environment and should be then pulled from there into production.