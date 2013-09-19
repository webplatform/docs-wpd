== Summary ==
How is installed the tracking code throughout the web application.

== Web applications ==

=== BugGenie ===
* File '''core/templates/footer.inc.php''' has the Piwik tracking code
* Visitor exclusion: None


=== MediaWiki ===
* Based on [http://www.mediawiki.org/wiki/Extension:Piwik_Integration MediaWiki Piwik Integration]
* Created two files in ''code/docs/current/extensions/piwik/''
* Added file:  [https://raw.github.com/DaSchTour/piwik-mediawiki-extension/master/Piwik.php piwik-mediawiki-extension Piwik.hooks.php]
* Added file from: [https://raw.github.com/DaSchTour/piwik-mediawiki-extension/master/Piwik.php piwik-mediawiki-extension Piwik.php]
* Modified code/docs/Settings.php accordingly to [6]
* Visitor exclusion: will not track authenticated MediaWiki Administrator users
 
=== Status (tumblr) ===
* Login to Tumblr, in Settings, WebPlatform.org site, Search for Theme, click 'customize', find 'Edit HTML' button, added code.
* Visitor exclusion: None

=== WordPress ===
* Installed [http://wordpress.org/plugins/wp-piwik/ Wp-Piwik plugin]
* Visitor exclusion: will not track authenticated WordPress with role Administrator

=== Static pages ===
* Edited in file: code/nonshared/webplatform/templates/container_close.html
* Used on the pages:
*# http://talk.webplatform.org/
*# http://www.webplatform.org/errors/503.html
*# http://www.webplatform.org/errors/404.html
*# http://www.webplatform.org/stewards/adobe/ (and all other stewards)
*# http://www.webplatform.org/logo/
* Visitor exclusion: None