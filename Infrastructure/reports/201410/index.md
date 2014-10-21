= October 2014 sprint =

== Objectives ==

# Every VMs w/ up to date softwares (database server, linux, etc)
# Every web application to work under SSL
# Every web applications are built on top of a Git release our customizations patched on top of them
# Refactor server configuration scripts in a way such that we can have a fully working clone of the production site. Without impacting it. 
# Everything has to be public, except passwords and private keys
# Setup a system such that if a module gets merged to a specific branch triggers an automatic update of the code on the servers
# Setup a staging version of the site that replicates everything in a separate OpenStack project. Any component of the site could be used by adding 'staging' to it.
# Set in place a system that "listens" to given GitHub repository to update the related component.

In other words; webplatform''Staging''.org is ''one'' "sandbox", anybody could build another full server stack of our site on the side too. 

Private data/passwords will be kept private to key contributors, of course.

== Progress ==

=== What’s done ===

* Most of the infrastructure
* web apps:
** WordPress
** BugGenie
** MediaWiki
** Firefox Accounts
** Piwik
** Specs


=== What’s missing ===

* Database cluster
* Redis/Memcache
* Server statistics (ganglia)
* Server logging
* Last VM types to upgrade (the more recent ones, should be easy)
** Mail
** Accounts
** Notes
* Missing web apps;
** webat25.org
** drafts.webplatform.org
* Set in place automation