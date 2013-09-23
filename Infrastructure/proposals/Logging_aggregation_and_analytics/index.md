== Summary ==
In order to get as much information on the system as possible, we have to aggregate log events. 

Current state is using UDP as a way to transfer log data and is not reliable by nature of the protocol, it is acceptable to drop packets. Not acceptable for log messages.

See '''[http://jasonwilder.com/blog/2012/01/03/centralized-logging/ This blog post about Centralized logging by Joson Wilder]''' to understand the idea behind.

Also, see this presentation: [http://www.youtube.com/watch?v=RuUFnog29M4 Logstash and other things by Jordan Sissel of Dreamhost]

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

== Reference ==

* [http://saltstarters.org/example/ahammond/salt_logstash Salt state configuration for LogStash], using [http://logstash.net/ Log stash]
* [https://github.com/heroku/logplex LogPlex]
* [https://github.com/facebook/scribe/wiki Scribe] (a facebook project)

=== Articles and tutotials ===
* [http://blog.pkhamre.com/2012/07/05/visualizing-logdata-with-logstash-statsd-and-graphite/ Visualizing log data with logstash] (adapt to Ganglia?)
* http://stackoverflow.com/questions/680200/application-log-aggregation-management-and-notifications
* http://opencast.org/article/graylog2-matterhorn-centralized-log-management
* [http://www.logalyze.com/product/major-features Logalize]
* [http://nichol.as/zeromq-an-introduction ZeroMQ, an introduction] (Answers: what is zero mq anyway?)
* [http://www.logstash.net/docs/1.2.1/tutorials/getting-started-centralized]
* [http://www.rexconsulting.net/tip-centralized-logging-benefits.html]
* [http://urbanairship.com/blog/2010/10/05/centralized-logging-using-rsyslog/]
* [http://jasonwilder.com/blog/2012/01/03/centralized-logging/]
* [http://imcol.in/tag/rabbitmq/]
* [http://hron.me/blog/2012/10/logging-with-logstash/]
* [http://sysadvent.blogspot.ca/2009/12/cron-practices.html]
* [http://blog.tagged.com/2012/05/grabbing-full-java-stack-traces-from-syslog-ng-with-logstash/]
* [http://jpmens.net/2012/08/06/my-logstash-and-graylog2-notes/]
* [http://benwilber.net/realtime-pixel-tracking-nginx-syslog-ng-redis]