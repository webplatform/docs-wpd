= October 2014 sprint report =

This sprint is about refactoring the full server infrastructure to ease the maintenance work and automate what’s possible.

== Objectives ==

# Every VMs w/ up to date softwares (database server, linux, etc)
# Every web application to work under SSL
# Every web applications are built on top of a Git release our customizations patched on top of them, see [[#Updating the web applications]]
# Refactor server configuration scripts in a way such that we can have a fully working clone of the production site. Without impacting it. 
# Everything has to be public, except passwords and private keys
# Setup a system such that if a module gets merged to a specific branch triggers an automatic update of the code on the servers
# Setup a staging version of the site that replicates everything in a separate OpenStack project. Any component of the site could be used by adding 'staging' to it.
# Set in place a system that "listens" to given GitHub repository to update the related component. See [[#Automatic updates]]

In other words; webplatform''Staging''.org is ''one'' "sandbox" (i.e. do not touch live "production" site), anybody could build another full server stack of our site on the side too. 

== Progress ==

=== What’s done ===

* Most of the infrastructure is now using more recent versions of servers and services (see [#What’s missing])
* Improved Fastly error messages, pointing to '''status.webplatform.org''' and the mailing list [http://www.webplatformstaging.org/errors/500.html see error page sample here]
* web apps:
** WordPress ([http://blog.webplatformstaging.org/2014/09/2nd-doc-sprint-in-amsterdam/ see], [https://github.com/webplatform/webplatform-wordpress-theme GitHub repo.])
** BugGenie ([https://project.webplatformstaging.org/content/issues/open see], [https://github.com/webplatform/thebuggenie/tree/webplatform-customizations GitHub repo.])
** MediaWiki ([https://docs.webplatformstaging.org/wiki/css/properties/border-collapse see], [https://github.com/webplatform/mediawiki-core/tree/1.24wmf16-wpd GitHub repo.], [https://github.com/webplatform/mediawiki-fxa-sso MediaWiki FxA client repo], [https://github.com/webplatform/mediawiki skin and custom extensions])
** Piwik ([https://stats.webplatformstaging.org/ see])
** Specs ([https://specs.webplatformstaging.org/ see])


=== What’s missing ===

'''NOTE''': Outdated

* Database cluster
* Redis/Memcache configuration
* Server statistics (ganglia)
* Server logging
* Last VM types to upgrade (the more recent ones, should be easy)
** Mail
** Accounts
** Notes
* Missing web apps;
** webat25.org
** drafts.webplatform.org
** Firefox Accounts ([https://accounts.webplatform.org/ see], [https://github.com/webplatform?query=fxa GitHub repo.])
** Notes server ([https://notes.webplatform.org/ see])
** Bots to log '''webplatform''' and '''webspecs''' freenode IRC channels
* Make sure that all web apps deployment are set to not accept index robots
* Set in place automation, see [[#Automatic updates]]


== Intervention plan ==

=== Updating the web applications ===

For each web application:

* Pick a version from GitHub, fork in our repo
* Get anything that’s not source-controlled in our code, make it as a patch on top of the original code
* Make sure the web app looks fine with the current CSS
* Make sure the configuration is adjusted by salt stack, nothing manual
* Make sure the theme doesn’t refer to production site, but current deployment
* Make sure that the assets are protocol relative (i.e. if site over SSL, call images and other assets through SSL too, keeping the bar "green")

Later, we’ll have a system that listens and updates the site automatically.

=== Automatic updates ===

A system that listens to new version tags on given GitHub repositories.

Once a tag is made, the staging salt master should;

# pull in the changes
# run any update scripts (sass, docpad, composer, etc)
# update all applicable web servers

More to come. This is the current next step.