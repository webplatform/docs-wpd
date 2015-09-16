---
title: Docs pages analytics
uri: 'WPD:Infrastructure/Components/Docs pages analytics'

---
**INCOMPLETE**, see *WebPlatform GitHub operations issue tracker*, at **[webplatform/ops\#149](https://github.com/webplatform/ops/issues/149)**

How to get data from MediaWiki.

## Tools found

-   [Statistics Special page](/Special:Statistics) or its command-line equivalent [*showSiteStats* maintenance script](https://www.mediawiki.org/wiki/Manual:ShowSiteStats.php), e.g. `php mediawiki/maintenance/showSiteStats.php`
    -   Refresh site stats with [*InitSiteStats.php*](https://www.mediawiki.org/wiki/Manual:InitSiteStats.php), e.g. `php mediawiki/maintenance/initSiteStats.php`

### [StatMediaWiki](https://meta.wikimedia.org/wiki/StatMediaWiki) (outdated)

**Outcome:** Couldn’t make something work in a reasonable time. Code was made against earlier version of MW and isn’t maintained.

TL;DR. Its a Python project can read from a database snapshot, crunch some data, and generate reports. Unfortunately, it has next to no docs, although I could get something at [in this wiki](http://edutechwiki.unige.ch/en/StatMediaWiki).

Unfortunately it seems the Python code is making database queries to MediaWiki database tables changed since the time *StatMediaWiki* was made and wasn’t completing execution.

See also the [StatMediaWiki Talk page](https://meta.wikimedia.org/wiki/Talk:StatMediaWiki)

### [Usage Statistics Extension](https://www.mediawiki.org/wiki/Extension:Usage_Statistics)

**Outcome:** Couldn’t make it work due to incompatibility caused by some calls that were using deprecated methods. After some more tests, it gives usage data per user; doesn’t match what we want to get.

### [Limn](http://reportcard.wmflabs.org/) (to be phased out by wmf)

**Outcome:** After consultation with *\#wikimedia-analytics* folks, Limn ([repo](https://github.com/wikimedia/limn)) is a visualization tool, one has to feed it with reports. In order to use it, we have to have crunched data, see [limn *datasources*](http://reportcard.wmflabs.org/datasources). To get data, Wikimedia foundation uses *wikimetrics* and *Quarry*.

### Also

-   <https://meta.wikimedia.org/wiki/WikiXRay>
-   <https://www.mediawiki.org/wiki/Analytics/Wikistats> <https://stats.wikimedia.org/>

## What Wikimedia do

Wikimedia Foundation has an *Analytics* team ([ref](http://www.mediawiki.org/wiki/Analytics)) and separate their work in @@ sub projects.

[Research and Data](http://www.mediawiki.org/wiki/Analytics/Research_and_Data)
:   To help making research-informed decisions. See [**\#Research-and-Data** in Wikimedia Phabricator](https://phabricator.wikimedia.org/tag/Research-and-Data/)
[Wikimetrics](http://www.mediawiki.org/wiki/Analytics/Wikimetrics)
:   A web based tool designed to simplify the measurement.

### [Quarry](http://quarry.wmflabs.org/)

Run database queries from the web browser.

*Quarry* ([repo](https://github.com/wikimedia/analytics-quarry-web)) is a tool written in Python that allows to make database queries from a web browser and expose publicly the results.

Here are a few interesting ones:

-   [Catalan Wikipedia users who published more than one article](http://quarry.wmflabs.org/query/3033)
-   [Files uploaded to two projects](http://quarry.wmflabs.org/query/947)
-   [Most edited pages in Portugese Wikipedia](http://quarry.wmflabs.org/query/3012)
-   [New active users in Lativian Wikipedia](http://quarry.wmflabs.org/query/2930)

### [WikiMetrics](https://metrics.wmflabs.org/)

[](/File:wikimetrics-screenshot-namespaceedits.png)

Sample database query

![](/WPD/assets/thumb/d/de/wikimetrics-screenshot-namespaceedits.png/300px-wikimetrics-screenshot-namespaceedits.png)

WikiMetrics is a sandbox we can import and run scripts to get usage statistics.

TL;DR ... a way to get wiki activity reports and statistics, one has to run it inside a sandboxed MediaWiki installation in which we import a database snapshot from production so it can crunch metrics.

Wikimetrics also helps to generate database queries that can be run to make reports

-   *Freenode IRC* channel: *\#wikimedia-analytics*
-   [project description page](http://www.mediawiki.org/wiki/Analytics/Wikimetrics), see also [former project description page "*User Metrics*"](http://www.mediawiki.org/wiki/User_Metrics)
-   [Wkimedia Phabricator KanBan board](https://phabricator.wikimedia.org/tag/Analytics-Wikimetrics/)
-   [code mirror on GitHub](https://github.com/wikimedia/analytics-wikimetrics)
