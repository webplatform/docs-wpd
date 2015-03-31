= October 2014 sprint report =

This sprint is about refactoring the full server infrastructure to ease the maintenance work and automate what’s possible.

In order to get more details on the work that has been done, refer to [[WPD:Infrastructure/analysis/2014-Improvements_plan|''2014 Improvements plan'' page]]


== Goal ==

The goal of this sprint is to have a separation between ''development'' (e.g. a local Vagrant VM, or code checkout), ''staging'' (i.e. a full deployment) and ''production'' (i.e. the live site) so we can test our changes in an environment without impacting the live "production" site.

== Requirements ==

# Every VMs w/ up to date softwares (database server, linux, etc)
# Every web application to work under SSL
# Every web applications are built on top of a Git release our customizations patched on top of them, see [[#Updating the web applications]]
# Refactor server configuration scripts in a way such that we can have a fully working clone of the production site. Without impacting it. 
# Everything has to be public, except passwords and private keys
# Setup a system such that if a module gets merged to a specific branch triggers an automatic update of the code on the servers
# Setup a staging version of the site that replicates everything in a separate OpenStack project. Any component of the site could be used by adding 'staging' to it.
# Set in place a system that "listens" to given GitHub repository to update the related component. See [[#Automatic updates]]

In other words, we should be able to work on anything in; webplatform''Staging''.org as a "sandbox" (i.e. do not touch live "production" site), which will allow anybody to replicate the full environment regardless of where its hosted or which top level domain name its being used.


== Expected outcome ==

* Have a COMPLETELY INDEPENDENT set of Virtual Machines to serve the FULL public facing webplatform.org components (i.e. blog, docs, project.webplatform.org)
* Before deploying to production, every components MUST be running fine on ''webplatformSTAGING.org'' (a.k.a. "'''staging'''")
* Deploy automatically on git push (GitHub hooks) on master branch and/or a release tag (TBD)
* Self-contained environment at every level; e.g, ''staging'' MUST NOT use any resources from ''production''
* Full clone of the site for each components; e.g. '''blog.webplatform.org''' (production), '''blog.webplatformSTAGING.org''' (staging).
* Harmonize configuration settings across the softwares, automate them based on known data facts, do not rely on internal DNS
* Remove anything that isn’t used anymore, and simplify system as much as possible

== Tasks summary ==

... tasks details are in [[WPD:Infrastructure/analysis/2014-Improvements_plan]]

* Publish to the public all our deployment scripts, with correct author attribution, without passwords nor private data
* Set in place a system that will update code automatically when a contributor push on watched Git repos
* Salt reactor pull, and run scripts (bower, grunt, composer, etc) and makes a zip archive, deploy archive
* Salt reactor launch rsync when changes are detected
* Ensure all components works on BOTH '''webplatform.org''' AND '''webplatformSTAGING.org''' top level domains, ''without configuration switches''
* Ensure all VM are on Ubuntu 14.04 LTS
* Make sure every components are working as it should


== Status ==

'''NOTE''': Project is completed.

* Missing web apps;
** webat25.org (won’t be migrated, we will convert as a static site by May 2015)
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