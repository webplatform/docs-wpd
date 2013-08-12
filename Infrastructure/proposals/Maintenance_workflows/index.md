== Summary ==
This document describe how to work on the infrastructure, to commission/de-commision services, and work on the infrastructure without affecting it directly.

In other words, the process is about describing how to create a local workspace using sets of Virtual Machines develop a specific use-case prior to deploy it on the cloud hosting infrastructure into production.


Required tools

1. Vagrant

This utility is the virtual machine handler. It automates manipulation with Oracle VirtualBox and providers. It runs on Windows, Linux and Mac OS X.

Version [1.1 and up][1], see [documentation][0] at: 

  [0]: http://docs.vagrantup.com/v2/installation/index.html
  [1]: http://www.vagrantup.com/
  [2]: http://chocolatey.org/packages/vagrant

Note: Under windows, it is recommended to [use Chocolatey][2] to handle the installation of vagrant for you.



2. Salty vagrant

This is a plugin  to Vagrant that allows us to use Salt Stack within Vagrant as a provisioner.

Installing works in a terminal window with the following command:

    vagrant plugin install vagrant-salt

See the [documentation for more details][3]

  [3]: https://github.com/saltstack/salty-vagrant



3. States repositories

We can use our own internal repositories.

Please note that I am currently searching a way to fork the states depending on the environment, for example during the development of a new tool, we might not need ALL instances (memcached, storage, etc). 

@Ryan if you have suggestion about the above, let me know.

This means that part of the work to do is to actually separate the states definitions and be able to declare within our environment that we are replicating the production but not in production.

Currently, the repositories are hosted in renoirb@jay.w3.org:~/git/wpd/deployment/  and are copied from my local environment and should be then pulled from there into production.

@Doug,Ryan: I know it is not optimal, but I need somewhere to move files to-and-from, it'll be somewhere better as soon as we have a proper private git repo. 



Next steps

I am currently modifying the states to isolate piwik out of app[+d]  to a separate instance. 

Progress is going well, I wanted to share with you how I am working prior to tell that I am ready for deployment.