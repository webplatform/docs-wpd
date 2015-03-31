= October 2014 sprint report =

This sprint is about refactoring the full server infrastructure to ease the maintenance work and automate what’s possible.

In order to get more details on the work that has been done, refer to [[WPD:Infrastructure/analysis/2014-Improvements_plan|''2014 Improvements plan'' page]]

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