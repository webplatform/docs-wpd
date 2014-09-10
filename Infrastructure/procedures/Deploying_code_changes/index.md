= Deploying code bases =

The site is using various softwares, each of them are synced from the deployment server to their dedicated VMs.


== Summary ==

There's four current code bases, run via '''sudo salt-run deploy.run <codebase>''':

;code.root: /srv/code/root - the document root.
;code.docs_nextgen: /srv/code/docs/nextgen/mediawiki - the version of MediaWiki that runs the site
;code.nonshared: /srv/code/nonshared - static content that is specific to domains.
;code.piwik: /srv/code/piwik - the location of the site metrics software.
;code.qwebirc: /srv/code/qwebirc - the location of the IRC browser client software.
;code.blog: /srv/code/blog/current - the location of the wordpress software.
;code.talk: /srv/code/talk/forums/current - the location of questions2answers software.

Each code base is stored in the salt repository on the deployment VM (''deployment.webplatform.org'') in a dedicated folder within ''/srv/code''.

<!-- TO BE UPDATED
# cd /srv/code/www
# <edit robots.txt>
# git commit -am 'my commit message'
#* Every code base is version controlled, please version control your changes.
# sudo salt-run deploy.run code.root

The process is the same for all code bases. There's a few notes for the docs code base, though: there's a couple weird exceptions to how the repositories are versioned. The MediaWiki extensions are submodules of the git repo. It's proper to update the submodule version in the parent repo, then have git update the submodule. One extension (SemanticForms) is using svn, rather than git, since it hasn't migrated yet.

For all repos where it's possible (like docs), it's always best to update upstream, then pull your changes in to the local repos. Local changes are dangerous.

==== Git ====

It's best if the extensions are added as git submodules, since the rest of the extensions are done this way (except SemanticForms, which is not yet in the [https://gerrit.wikimedia.org/mediawiki-extensions.txt list of git-supported extensions] on "gerrit", the WikiMedia git server):

* ''git submodule add <url> <location>''

For example:
 ''laner@deployment:/srv/code/docs/current$ git submodule add https://gerrit.wikimedia.org/r/p/mediawiki/extensions/AdminLinks.git extensions/AdminLinks''

==== Updating the Database ====
Sometimes an extension will require updating the databases. To do this, change your permissions to root, and run:

<code>root@deployment:/srv/code/docs/current# php maintenance/update.php</code>

If the extension includes a SQL file to create new tables, run (for example):

<code>root@deployment:/srv/code/docs/current# php maintenance/sql.php extensions/NewSignupPage/user_register_track.sql
</code>

=== Testing MediaWiki changes via the test site ===

It's possible to test changes on docs.webplatform.org/test prior to deploying them to docs.webplatform.org/wiki. There's three things to know about this:

# Both are modified in the same place (/srv/code/docs/current), but they are deployed separately:
#* test: sudo salt-run deploy.run code.docs_test
#* wiki: sudo salt-run deploy.run code.docs_current
# To run maintenance scripts for test, you need to provide a configuration file via a flag; from /srv/code/docs/current:
#* php maintenance/<maintenance-script> --conf=../TestSettings.php
# The MediaWiki configuration is shared between test and wiki in Settings.php. Both test and wiki have exclusive configuration files as well. If you wish to add settings or extensions to test, you should edit TestSettings.php. Ensure you move your changes from TestSettings.php to Settings.php when done testing.

Best practice is to deploy the changes to test and test them out before deploying them to wiki.
-->

== Adding a new code base ==

The deployment code is using salt runners that call salt states that aren't included in the top state configuration. These non-top called states are only called during deployment. We do this so that we can separate deployment of applications from configuration of the instances. That said, adding a new code base for deployment is the same as writing any other salt state.

The deployment salt states are in /srv/code/<code_base>.sls. Here's the root code base's state:

  include:
    - rsync.codesync

  rsync -a --delete --no-perms --password-file=/etc/codesync.secret codesync@deployment.webplatform.org::code/root/ /var/www/:
    cmd.run:
      - user: root
      - group: root
      - require:
        - file: /etc/codesync.secret

We're simply doing an rsync of the root directory on the deployment system to a directory on the target system. Everything under code is shared via rsync (requiring the password in the password file).

Here's another example for docs_current:

  # Include the common settings for the docs repo
  include:
    - code.docs_settings
    - rsync.codesync

  rsync -a --delete --no-perms --password-file=/etc/codesync.secret codesync@deployment.webplatform.org::code/docs/current/ /srv/webplatform/wiki/current/:
    cmd.run:
      - user: root
      - group: root
      - require:
        - file: /etc/codesync.secret

Like the root example, this simply does an rsync to make the directories match. There's one extra thing in this example, which is the inclusion of another deployment code base (code.docs_settings).

code.docs_settings is ''/src/salt/code/docs_settings.sls''; which has the following:

  include:
    - rsync.codesync
  rsync -a --no-perms --password-file=/etc/codesync.secret codesync@deployment.webplatform.org::code/docs/Settings.php /srv/webplatform/wiki/Settings.php:
    cmd.run:
      - user: root
      - group: root
      - require:
        - file: /etc/codesync.secret

Notice that this directive manages only a single file, which is at ''/srv/salt/code/docs/Settings.php''. Since it is included in ''docs_current'', it'll automatically get deployed with ''docs_current''. It can also be deployed separately, though, since it's a standalone state.

=== Committing and Deploying Content ===

Inside the proper directory, run:

 git commit -a "Message"

To deploy: 

 sudo salt-run deploy.run code.codebasename

Such as 

 sudo salt-run deploy.run code.nonshared