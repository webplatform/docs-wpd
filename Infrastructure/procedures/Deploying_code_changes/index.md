== Deploying code bases ==

There's four current code bases:

;code.root: the document root.
;code.docs_current: the version of MediaWiki that runs the site.
;code.docs_test: a version of MediaWiki that can be used to test changes.
;code.docs_settings: the shared configuration files between test and current. This code base is automatically deployed with docs_current and docs_test, but can be deployed separately, if wanted.

Each code base is stored in the salt repository on the deployment system (10.4.238.151 - we need a DNS entry for this), at ''/srv/salt/code''. To make a change, using robots.txt in the root code base:

# cd /srv/salt/code/root
# <edit robots.txt>
# git commit -a -m 'my message here'
#* Every code base is version controlled, please version control your changes.
# salt-run deploy.run code.root

The process is the same for all code bases. There's a few notes for the docs code base, though: there's a couple weird exceptions to how the repositories are versioned. The MediaWiki extensions are submodules of the git repo. It's proper to update the submodule version in the parent repo, then have git update the submodule. One extension (SemanticForms) is using svn, rather than git, since it hasn't migrated yet.

For all repos where it's possible (like docs), it's always best to update upstream, then pull your changes in to the local repos. Local changes are dangerous.

== Adding a new code base ==

The deployment code is using salt runners that call salt states that aren't included in the top state configuration. These non-top called states are only called during deployment. We do this so that we can separate deployment of applications from configuration of the instances. That said, adding a new code base for deployment is the same as writing any other salt state.

The deployment salt states are in /srv/salt/code/<code_base>.sls. Here's the root code base's state:

 /var/www:
   file.recurse:
     - include_empty: true
     - clean: true
     - source: salt://code/root/

See the [http://salt.readthedocs.org/en/latest/ref/states/all/salt.states.file.html file.recurse salt state documentation]. This simply tells salt that the contents of ''/var/www'' should exactly match the content at ''/srv/salt/code/root''. Note that ''/srv/salt'' is salt's base directory, and it is left out of the path when using ''source''.

Here's another example for docs_current:

 # Include the common settings for the docs repo
 include:
   - code.docs_settings

 /srv/webplatform/wiki/current:
   file.recurse:
     - include_empty: true
     - clean: true
     - source: salt://code/docs/current

Like the root example, this tells salt that the contents of ''/srv/webplatform/wiki/current'' should exactly match the contents of ''/srv/salt/code/docs/current''. There's one extra thing in this example, which is the inclusion of another salt state.

code.docs_settings is ''/src/salt/code/docs_settings.sls''; which has the following:

 /srv/webplatform/wiki/Settings.php:
   file.managed:
     - source: salt://code/docs/Settings.php
     - user: root
     - group: www-data
     - mode: 440

Notice that this directive manages only a single file, which is at ''/srv/salt/code/docs/Settings.php''. Since it is included in ''docs_current'', it'll automatically get deployed with ''docs_current''. It can also be deployed separately, though, since it's a standalone state.