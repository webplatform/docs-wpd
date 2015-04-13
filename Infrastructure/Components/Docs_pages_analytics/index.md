= Docs pages analytics =

'''INCOMPLETE''', see {{OperationsTask|149}}

How to get data from MediaWiki.

== Tools found ==

* [[Special:Statistics|Statistics Special page]] or its command-line equivalent [https://www.mediawiki.org/wiki/Manual:ShowSiteStats.php ''showSiteStats'' maintenance script], e.g.  <code>php mediawiki/maintenance/showSiteStats.php</code>
** Refresh site stats with [https://www.mediawiki.org/wiki/Manual:InitSiteStats.php ''InitSiteStats.php''], e.g.  <code>php mediawiki/maintenance/initSiteStats.php</code>

=== [https://meta.wikimedia.org/wiki/StatMediaWiki StatMediaWiki] (outdated) ===

'''Outcome:''' Couldn’t make something work in a reasonable time. Code was made against earlier version of MW and isn’t maintained.

TL;DR. Its a Python project can read from a database snapshot, crunch some data, and generate reports. Unfortunately, it has next to no docs, although I could get something at [http://edutechwiki.unige.ch/en/StatMediaWiki in this wiki]. 

Unfortunately it seems the Python code is making database queries to MediaWiki database tables changed since the time ''StatMediaWiki'' was made and wasn’t completing execution. 

See also the [https://meta.wikimedia.org/wiki/Talk:StatMediaWiki StatMediaWiki Talk page]

=== [https://www.mediawiki.org/wiki/Extension:Usage_Statistics Usage Statistics Extension] ===

'''Outcome:''' Couldn’t make it work due to incompatibility caused by some calls that were using deprecated methods. After some more tests, it gives usage data per user; doesn’t match what we want to get.

=== [http://reportcard.wmflabs.org/ Limn] (to be phased out by wmf) ===

'''Outcome:''' After consultation with ''#wikimedia-analytics'' folks, Limn ([https://github.com/wikimedia/limn repo]) is a visualization tool, one has  to feed it with reports. In order to use it, we have to have crunched data, see [http://reportcard.wmflabs.org/datasources limn ''datasources'']. To get data, Wikimedia foundation uses ''wikimetrics'' and ''Quarry''.

=== Also ===

* https://meta.wikimedia.org/wiki/WikiXRay
* https://www.mediawiki.org/wiki/Analytics/Wikistats https://stats.wikimedia.org/

== What Wikimedia do ==

Wikimedia Foundation has an ''Analytics'' team ([http://www.mediawiki.org/wiki/Analytics ref]) and separate their work in @@ sub projects.

;[http://www.mediawiki.org/wiki/Analytics/Research_and_Data Research and Data]: To help making research-informed decisions. See [https://phabricator.wikimedia.org/tag/Research-and-Data/ '''#Research-and-Data''' in Wikimedia Phabricator]
;[http://www.mediawiki.org/wiki/Analytics/Wikimetrics Wikimetrics]: A web based tool designed to simplify the measurement.


=== [http://quarry.wmflabs.org/ Quarry] ===

Run database queries from the web browser. 

''Quarry'' ([https://github.com/wikimedia/analytics-quarry-web repo]) is a tool written in Python that allows to make database queries from a web browser and expose publicly the results.

Here are a few interesting ones:
* [http://quarry.wmflabs.org/query/3033 Catalan Wikipedia users who published more than one article]
* [http://quarry.wmflabs.org/query/947 Files uploaded to two projects]
* [http://quarry.wmflabs.org/query/3012 Most edited pages in Portugese Wikipedia] 
* [http://quarry.wmflabs.org/query/2930 New active users in Lativian Wikipedia]

=== [https://metrics.wmflabs.org/ WikiMetrics] ===
[[File:wikimetrics-screenshot-namespaceedits.png|thumb|Sample database query]]

WikiMetrics is a sandbox we can import and run scripts to get usage statistics.

TL;DR ... a way to get wiki activity reports and statistics, one has to run it inside a sandboxed MediaWiki installation in which we import a database snapshot from production so it can crunch metrics.

Wikimetrics also helps to generate database queries that can be run to make reports


* ''Freenode IRC'' channel: ''#wikimedia-analytics''
* [http://www.mediawiki.org/wiki/Analytics/Wikimetrics project description page], see also [http://www.mediawiki.org/wiki/User_Metrics former project description page "''User Metrics''"]
* [https://phabricator.wikimedia.org/tag/Analytics-Wikimetrics/ Wkimedia Phabricator KanBan board]
* [https://github.com/wikimedia/analytics-wikimetrics code mirror on GitHub]