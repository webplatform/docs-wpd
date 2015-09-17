---
title: 'Logging aggregation and analytics'
uri: 'WPD:Infrastructure/proposals/Logging aggregation and analytics'

---
## Summary

In order to get as much information on the system as possible, we have to aggregate log events.

Current state is using UDP as a way to transfer log data and is not reliable by nature of the protocol, it is acceptable to drop packets. Not acceptable for log messages.

See **[This blog post about Centralized logging by Joson Wilder](http://jasonwilder.com/blog/2012/01/03/centralized-logging/)** to understand the idea behind.

Also, see this presentation: [Logstash and other things by Jordan Sissel of Dreamhost](http://www.youtube.com/watch?v=RuUFnog29M4)

### Related tasks

-   Initiating the project [\#INFR-39](http://project.webplatform.org/infrastructure/issues/INFR-39)

## Overview

An ideal system should:

1.  Accept messages from all the nodes and their services
2.  Use some FIFO or queue to make sure we do not lose messages or overflow the internal network traffic
3.  Provide a web-based interface to search events
4.  Index all log messages and parse known elements such as date formats, and categorize by type of service
5.  Be open-source, and hosted within our own infrastructure

Found:

1.  LogStash
2.  Graylog2
3.  Scribe

## Data sources

-   Salt stack minion `log_file` parameter
-   Apache2 in every vhost `ErrorLog syslog:local` and `php_flag log_errors on`
-   NGINX in every vhost
-   Local syslog service to forward, configure message queue
-   Add hooks in some web apps
    1.  MediaWiki hooks [[1]](http://www.mediawiki.org/wiki/Manual:Hooks/PageContentSave)
    2.  BugGenie
    3.  WordPress

## Reference

-   [Salt state configuration for LogStash](http://saltstarters.org/example/ahammond/salt_logstash), using [Log stash](http://logstash.net/)
-   [LogPlex](https://github.com/heroku/logplex)
-   [Scribe](https://github.com/facebook/scribe/wiki) (a facebook project)

### Articles and tutotials

-   [Visualizing log data with logstash](http://blog.pkhamre.com/2012/07/05/visualizing-logdata-with-logstash-statsd-and-graphite/) (adapt to Ganglia?)
-   <http://stackoverflow.com/questions/680200/application-log-aggregation-management-and-notifications>
-   <http://opencast.org/article/graylog2-matterhorn-centralized-log-management>
-   [Logalize](http://www.logalyze.com/product/major-features)
-   [ZeroMQ, an introduction](http://nichol.as/zeromq-an-introduction) (Answers: what is zero mq anyway?)
-   [[2]](http://www.logstash.net/docs/1.2.1/tutorials/getting-started-centralized)
-   [[3]](http://www.rexconsulting.net/tip-centralized-logging-benefits.html)
-   [[4]](http://urbanairship.com/blog/2010/10/05/centralized-logging-using-rsyslog/)
-   [[5]](http://jasonwilder.com/blog/2012/01/03/centralized-logging/)
-   [[6]](http://imcol.in/tag/rabbitmq/)
-   [[7]](http://hron.me/blog/2012/10/logging-with-logstash/)
-   [[8]](http://sysadvent.blogspot.ca/2009/12/cron-practices.html)
-   [[9]](http://blog.tagged.com/2012/05/grabbing-full-java-stack-traces-from-syslog-ng-with-logstash/)
-   [[10]](http://jpmens.net/2012/08/06/my-logstash-and-graylog2-notes/)
-   [[11]](http://benwilber.net/realtime-pixel-tracking-nginx-syslog-ng-redis)
