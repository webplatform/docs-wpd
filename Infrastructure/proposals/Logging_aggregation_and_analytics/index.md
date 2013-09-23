== Summary ==
In order to get as much information on the system as possible, we have to aggregate log events. 

=== Related tasks ===
* Initiating the project [http://project.webplatform.org/infrastructure/issues/INFR-39 #INFR-39]

== Overview ==

An ideal system should:
# Accept messages from all the nodes and their services
# Use some FIFO or queue to make sure we do not lose messages or overflow the internal network traffic
# Provide a web-based interface to search events
# Index all log messages and parse known elements such as date formats, and categorize by type of service
# Be open-source, and hosted within our own infrastructure

Found:
# LogStash
# Graylog2
# Scribe

== Data sources ==
* Salt stack minion <tt>log_file</tt> parameter
* Apache2 in every vhost <tt>ErrorLog syslog:local</tt> and <tt>php_flag log_errors on</tt>
* NGINX in every vhost
* Local syslog service to forward, configure message queue
* Add hooks in some web apps
*# MediaWiki hooks [http://www.mediawiki.org/wiki/Manual:Hooks/PageContentSave]
*# BugGenie
*# WordPress