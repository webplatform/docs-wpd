---
title: WPD:Infrastructure/proposals/Logging aggregation and analytics
---
<h1><span class="mw-headline" id="Logging_aggregation_and_analytics">Logging aggregation and analytics</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>In order to get as much information on the system as possible, we have to aggregate log events. 
</p><p>Current state is using UDP as a way to transfer log data and is not reliable by nature of the protocol, it is acceptable to drop packets. Not acceptable for log messages.
</p><p>See <b><a rel="nofollow" class="external text" href="http://jasonwilder.com/blog/2012/01/03/centralized-logging/">This blog post about Centralized logging by Joson Wilder</a></b> to understand the idea behind.
</p><p>Also, see this presentation: <a rel="nofollow" class="external text" href="http://www.youtube.com/watch?v=RuUFnog29M4">Logstash and other things by Jordan Sissel of Dreamhost</a>
</p>
<h3><span class="mw-headline" id="Related_tasks">Related tasks</span></h3>
<ul><li> Initiating the project <a rel="nofollow" class="external text" href="http://project.webplatform.org/infrastructure/issues/INFR-39">#INFR-39</a></li></ul>
<h2><span class="mw-headline" id="Overview">Overview</span></h2>
<p>An ideal system should:
</p>
<ol><li> Accept messages from all the nodes and their services</li>
<li> Use some FIFO or queue to make sure we do not lose messages or overflow the internal network traffic</li>
<li> Provide a web-based interface to search events</li>
<li> Index all log messages and parse known elements such as date formats, and categorize by type of service</li>
<li> Be open-source, and hosted within our own infrastructure</li></ol>
<p>Found:
</p>
<ol><li> LogStash</li>
<li> Graylog2</li>
<li> Scribe</li></ol>
<h2><span class="mw-headline" id="Data_sources">Data sources</span></h2>
<ul><li> Salt stack minion <tt>log_file</tt> parameter</li>
<li> Apache2 in every vhost <tt>ErrorLog syslog:local</tt> and <tt>php_flag log_errors on</tt></li>
<li> NGINX in every vhost</li>
<li> Local syslog service to forward, configure message queue</li>
<li> Add hooks in some web apps
<ol><li> MediaWiki hooks <a class="external autonumber" href="http://www.mediawiki.org/wiki/Manual:Hooks/PageContentSave">[1]</a></li>
<li> BugGenie</li>
<li> WordPress</li></ol></li></ul>
<h2><span class="mw-headline" id="Reference">Reference</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="http://saltstarters.org/example/ahammond/salt_logstash">Salt state configuration for LogStash</a>, using <a rel="nofollow" class="external text" href="http://logstash.net/">Log stash</a></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/heroku/logplex">LogPlex</a></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/facebook/scribe/wiki">Scribe</a> (a facebook project)</li></ul>
<h3><span class="mw-headline" id="Articles_and_tutotials">Articles and tutotials</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="http://blog.pkhamre.com/2012/07/05/visualizing-logdata-with-logstash-statsd-and-graphite/">Visualizing log data with logstash</a> (adapt to Ganglia?)</li>
<li> <a rel="nofollow" class="external free" href="http://stackoverflow.com/questions/680200/application-log-aggregation-management-and-notifications">http://stackoverflow.com/questions/680200/application-log-aggregation-management-and-notifications</a></li>
<li> <a rel="nofollow" class="external free" href="http://opencast.org/article/graylog2-matterhorn-centralized-log-management">http://opencast.org/article/graylog2-matterhorn-centralized-log-management</a></li>
<li> <a rel="nofollow" class="external text" href="http://www.logalyze.com/product/major-features">Logalize</a></li>
<li> <a rel="nofollow" class="external text" href="http://nichol.as/zeromq-an-introduction">ZeroMQ, an introduction</a> (Answers: what is zero mq anyway?)</li>
<li> <a rel="nofollow" class="external autonumber" href="http://www.logstash.net/docs/1.2.1/tutorials/getting-started-centralized">[2]</a></li>
<li> <a rel="nofollow" class="external autonumber" href="http://www.rexconsulting.net/tip-centralized-logging-benefits.html">[3]</a></li>
<li> <a rel="nofollow" class="external autonumber" href="http://urbanairship.com/blog/2010/10/05/centralized-logging-using-rsyslog/">[4]</a></li>
<li> <a rel="nofollow" class="external autonumber" href="http://jasonwilder.com/blog/2012/01/03/centralized-logging/">[5]</a></li>
<li> <a rel="nofollow" class="external autonumber" href="http://imcol.in/tag/rabbitmq/">[6]</a></li>
<li> <a rel="nofollow" class="external autonumber" href="http://hron.me/blog/2012/10/logging-with-logstash/">[7]</a></li>
<li> <a rel="nofollow" class="external autonumber" href="http://sysadvent.blogspot.ca/2009/12/cron-practices.html">[8]</a></li>
<li> <a rel="nofollow" class="external autonumber" href="http://blog.tagged.com/2012/05/grabbing-full-java-stack-traces-from-syslog-ng-with-logstash/">[9]</a></li>
<li> <a rel="nofollow" class="external autonumber" href="http://jpmens.net/2012/08/06/my-logstash-and-graylog2-notes/">[10]</a></li>
<li> <a rel="nofollow" class="external autonumber" href="http://benwilber.net/realtime-pixel-tracking-nginx-syslog-ng-redis">[11]</a></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:10472-0!*!*!!*!*!*!esi=1 and timestamp 20150731184608 and revision id 40895
 -->
