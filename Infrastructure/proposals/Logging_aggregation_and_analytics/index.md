== Summary ==
In order to get as much information on the system as possible, we have to aggregate log events. 

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
* Salt stack minion <pre>log_file</pre> parameter
* Apache2 in every vhost <pre>ErrorLog syslog:local</pre> and <pre>php_flag log_errors on</pre>