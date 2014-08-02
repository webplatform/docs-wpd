= Description =

This page describes how to use MediaWiki Vagrant workspace and a set of scripts to reproduce docs.webplatform.org MediaWiki installation. It doesn’t include the actual database, but rather the full set of dependencies and customizations.

== Status: In progress ==
See related changesets in the main extension+skin and the vagrant workspace
* https://gerrit.wikimedia.org/r/#/c/151266/
* https://source.webplatform.org/r/#/c/9/

== Bundle extension features ==
* Add Piwik tracking codes to webplatform.org’s own piwik deployment, based off of [https://www.mediawiki.org/wiki/Extension:Piwik_Integration MediaWiki Piwik Integration]
* Adds breadcrumb at the top of the page based on the path
* Removes <nowiki>[edit]</nowiki> links by the section titles
* Creates the page Table of contents