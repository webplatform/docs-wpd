---
title: WPD:Infrastructure/Components/Docs pages analytics
path: Infrastructure/Components/Docs_pages_analytics

---
<h1><span class="mw-headline" id="Docs_pages_analytics">Docs pages analytics</span></h1>
<p><b>INCOMPLETE</b>, see <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/149">webplatform/ops#149</a></b>
</p><p>How to get data from MediaWiki.
</p>
<h2><span class="mw-headline" id="Tools_found">Tools found</span></h2>
<ul><li> <a href="/wiki/Special:Statistics" title="Special:Statistics">Statistics Special page</a> or its command-line equivalent <a class="external text" href="https://www.mediawiki.org/wiki/Manual:ShowSiteStats.php"><i>showSiteStats</i> maintenance script</a>, e.g.  <code>php mediawiki/maintenance/showSiteStats.php</code>
<ul><li> Refresh site stats with <a class="external text" href="https://www.mediawiki.org/wiki/Manual:InitSiteStats.php"><i>InitSiteStats.php</i></a>, e.g.  <code>php mediawiki/maintenance/initSiteStats.php</code></li></ul></li></ul>
<h3><span class="mw-headline" id="StatMediaWiki_.28outdated.29"><a rel="nofollow" class="external text" href="https://meta.wikimedia.org/wiki/StatMediaWiki">StatMediaWiki</a> (outdated)</span></h3>
<p><b>Outcome:</b> Couldn’t make something work in a reasonable time. Code was made against earlier version of MW and isn’t maintained.
</p><p>TL;DR. Its a Python project can read from a database snapshot, crunch some data, and generate reports. Unfortunately, it has next to no docs, although I could get something at <a rel="nofollow" class="external text" href="http://edutechwiki.unige.ch/en/StatMediaWiki">in this wiki</a>. 
</p><p>Unfortunately it seems the Python code is making database queries to MediaWiki database tables changed since the time <i>StatMediaWiki</i> was made and wasn’t completing execution. 
</p><p>See also the <a rel="nofollow" class="external text" href="https://meta.wikimedia.org/wiki/Talk:StatMediaWiki">StatMediaWiki Talk page</a>
</p>
<h3><span class="mw-headline" id="Usage_Statistics_Extension"><a class="external text" href="https://www.mediawiki.org/wiki/Extension:Usage_Statistics">Usage Statistics Extension</a></span></h3>
<p><b>Outcome:</b> Couldn’t make it work due to incompatibility caused by some calls that were using deprecated methods. After some more tests, it gives usage data per user; doesn’t match what we want to get.
</p>
<h3><span class="mw-headline" id="Limn_.28to_be_phased_out_by_wmf.29"><a rel="nofollow" class="external text" href="http://reportcard.wmflabs.org/">Limn</a> (to be phased out by wmf)</span></h3>
<p><b>Outcome:</b> After consultation with <i>#wikimedia-analytics</i> folks, Limn (<a rel="nofollow" class="external text" href="https://github.com/wikimedia/limn">repo</a>) is a visualization tool, one has  to feed it with reports. In order to use it, we have to have crunched data, see <a rel="nofollow" class="external text" href="http://reportcard.wmflabs.org/datasources">limn <i>datasources</i></a>. To get data, Wikimedia foundation uses <i>wikimetrics</i> and <i>Quarry</i>.
</p>
<h3><span class="mw-headline" id="Also">Also</span></h3>
<ul><li> <a rel="nofollow" class="external free" href="https://meta.wikimedia.org/wiki/WikiXRay">https://meta.wikimedia.org/wiki/WikiXRay</a></li>
<li> <a class="external free" href="https://www.mediawiki.org/wiki/Analytics/Wikistats">https://www.mediawiki.org/wiki/Analytics/Wikistats</a> <a rel="nofollow" class="external free" href="https://stats.wikimedia.org/">https://stats.wikimedia.org/</a></li></ul>
<h2><span class="mw-headline" id="What_Wikimedia_do">What Wikimedia do</span></h2>
<p>Wikimedia Foundation has an <i>Analytics</i> team (<a class="external text" href="http://www.mediawiki.org/wiki/Analytics">ref</a>) and separate their work in @@ sub projects.
</p>
<dl><dt><a class="external text" href="http://www.mediawiki.org/wiki/Analytics/Research_and_Data">Research and Data</a></dt>
<dd> To help making research-informed decisions. See <a rel="nofollow" class="external text" href="https://phabricator.wikimedia.org/tag/Research-and-Data/"><b>#Research-and-Data</b> in Wikimedia Phabricator</a></dd>
<dt><a class="external text" href="http://www.mediawiki.org/wiki/Analytics/Wikimetrics">Wikimetrics</a></dt>
<dd> A web based tool designed to simplify the measurement.</dd></dl>
<p><br />
</p>
<h3><span class="mw-headline" id="Quarry"><a rel="nofollow" class="external text" href="http://quarry.wmflabs.org/">Quarry</a></span></h3>
<p>Run database queries from the web browser. 
</p><p><i>Quarry</i> (<a rel="nofollow" class="external text" href="https://github.com/wikimedia/analytics-quarry-web">repo</a>) is a tool written in Python that allows to make database queries from a web browser and expose publicly the results.
</p><p>Here are a few interesting ones:
</p>
<ul><li> <a rel="nofollow" class="external text" href="http://quarry.wmflabs.org/query/3033">Catalan Wikipedia users who published more than one article</a></li>
<li> <a rel="nofollow" class="external text" href="http://quarry.wmflabs.org/query/947">Files uploaded to two projects</a></li>
<li> <a rel="nofollow" class="external text" href="http://quarry.wmflabs.org/query/3012">Most edited pages in Portugese Wikipedia</a> </li>
<li> <a rel="nofollow" class="external text" href="http://quarry.wmflabs.org/query/2930">New active users in Lativian Wikipedia</a></li></ul>
<h3><span class="mw-headline" id="WikiMetrics"><a rel="nofollow" class="external text" href="https://metrics.wmflabs.org/">WikiMetrics</a></span></h3>
<div class="thumb tright"><div class="thumbinner" style="width:302px;"><a href="/wiki/File:wikimetrics-screenshot-namespaceedits.png" class="image"><img alt="" src="//static.webplatform.org/w/thumb/d/de/wikimetrics-screenshot-namespaceedits.png/300px-wikimetrics-screenshot-namespaceedits.png" width="300" height="291" class="thumbimage" srcset="//static.webplatform.org/w/thumb/d/de/wikimetrics-screenshot-namespaceedits.png/450px-wikimetrics-screenshot-namespaceedits.png 1.5x, //static.webplatform.org/w/thumb/d/de/wikimetrics-screenshot-namespaceedits.png/600px-wikimetrics-screenshot-namespaceedits.png 2x" /></a>  <div class="thumbcaption"><div class="magnify"><a href="/wiki/File:wikimetrics-screenshot-namespaceedits.png" class="internal" title="Enlarge"></a></div>Sample database query</div></div></div>
<p>WikiMetrics is a sandbox we can import and run scripts to get usage statistics.
</p><p>TL;DR ... a way to get wiki activity reports and statistics, one has to run it inside a sandboxed MediaWiki installation in which we import a database snapshot from production so it can crunch metrics.
</p><p>Wikimetrics also helps to generate database queries that can be run to make reports
</p><p><br />
</p>
<ul><li> <i>Freenode IRC</i> channel: <i>#wikimedia-analytics</i></li>
<li> <a class="external text" href="http://www.mediawiki.org/wiki/Analytics/Wikimetrics">project description page</a>, see also <a class="external text" href="http://www.mediawiki.org/wiki/User_Metrics">former project description page "<i>User Metrics</i>"</a></li>
<li> <a rel="nofollow" class="external text" href="https://phabricator.wikimedia.org/tag/Analytics-Wikimetrics/">Wkimedia Phabricator KanBan board</a></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/wikimedia/analytics-wikimetrics">code mirror on GitHub</a></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:58645-0!*!*!!*!5!*!esi=1 and timestamp 20150810202506 and revision id 101404
 -->
