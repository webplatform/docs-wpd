---
title: WPD:Infrastructure/procedures/Piwik Tracking code installation
---
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>How is installed the tracking code throughout the web application.
</p>
<h2><span class="mw-headline" id="Web_applications">Web applications</span></h2>
<h3><span class="mw-headline" id="BugGenie">BugGenie</span></h3>
<ul><li> File <b>core/templates/footer.inc.php</b> has the Piwik tracking code</li>
<li> Visitor exclusion: None</li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="MediaWiki">MediaWiki</span></h3>
<ul><li> Based on <a class="external text" href="http://www.mediawiki.org/wiki/Extension:Piwik_Integration">MediaWiki Piwik Integration</a></li>
<li> Created two files in <i>code/docs/current/extensions/piwik/</i></li>
<li> Added file:  <a rel="nofollow" class="external text" href="https://raw.github.com/DaSchTour/piwik-mediawiki-extension/master/Piwik.php">piwik-mediawiki-extension Piwik.hooks.php</a></li>
<li> Added file from: <a rel="nofollow" class="external text" href="https://raw.github.com/DaSchTour/piwik-mediawiki-extension/master/Piwik.php">piwik-mediawiki-extension Piwik.php</a></li>
<li> Modified code/docs/Settings.php accordingly to [6]</li>
<li> Visitor exclusion: None</li></ul>
<h3><span class="mw-headline" id="Status_.28tumblr.29">Status (tumblr)</span></h3>
<ul><li> Login to Tumblr, in Settings, WebPlatform.org site, Search for Theme, click 'customize', find 'Edit HTML' button, added code.</li>
<li> Visitor exclusion: None</li></ul>
<h3><span class="mw-headline" id="WordPress">WordPress</span></h3>
<ul><li> Installed <a rel="nofollow" class="external text" href="http://wordpress.org/plugins/wp-piwik/">Wp-Piwik plugin</a></li>
<li> Visitor exclusion: None</li></ul>
<h3><span class="mw-headline" id="Static_pages">Static pages</span></h3>
<ul><li> Edited in file: code/nonshared/webplatform/templates/container_close.html</li>
<li> Used on the pages:
<ol><li> <a rel="nofollow" class="external free" href="http://talk.webplatform.org/">http://talk.webplatform.org/</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.webplatform.org/errors/503.html">http://www.webplatform.org/errors/503.html</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.webplatform.org/errors/404.html">http://www.webplatform.org/errors/404.html</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.webplatform.org/stewards/adobe/">http://www.webplatform.org/stewards/adobe/</a> (and all other stewards)</li>
<li> <a rel="nofollow" class="external free" href="http://www.webplatform.org/logo/">http://www.webplatform.org/logo/</a></li></ol></li>
<li> Visitor exclusion: None</li></ul>
<h3><span class="mw-headline" id="Customizations">Customizations</span></h3>
<h4><span class="mw-headline" id="MediaWiki_2">MediaWiki</span></h4>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">// In file Piwik.hooks.php, within AddPiwik method
&#160;
    $wgPiwikCustomJS[] = <span class="sc2">&lt;&lt;&lt;<span class="st0">'JS'</span></span>
&#160;
<span class="sc2">          <span class="sy0">//</span> Note from renoirb: Should be moved somewhere else soon</span>
<span class="sc2">          jQuery<span class="br0">&#40;</span>document<span class="br0">&#41;</span>.ready<span class="br0">&#40;</span>function<span class="br0">&#40;</span><span class="br0">&#41;</span><span class="br0">&#123;</span></span>
<span class="sc2">              jQuery<span class="br0">&#40;</span><span class="st0">'body'</span><span class="br0">&#41;</span>.on<span class="br0">&#40;</span><span class="st0">'click'</span>, <span class="st0">'#ca-edit'</span>, function<span class="br0">&#40;</span><span class="br0">&#41;</span><span class="br0">&#123;</span></span>
<span class="sc2">                 if <span class="br0">&#40;</span>typeof _paq&#160;!<span class="sy0">==</span> <span class="st0">'undefined'</span><span class="br0">&#41;</span> <span class="br0">&#123;</span></span>
<span class="sc2">                    _paq.push<span class="br0">&#40;</span><span class="br0">&#91;</span><span class="st0">'trackGoal'</span>,<span class="nu0">1</span><span class="br0">&#93;</span><span class="br0">&#41;</span>;<span class="sy0">//</span> Goal specific to edit a page</span>
<span class="sc2">                 <span class="br0">&#125;</span></span>
<span class="sc2">              <span class="br0">&#125;</span><span class="br0">&#41;</span>;</span>
<span class="sc2">          <span class="br0">&#125;</span><span class="br0">&#41;</span>;</span>
&#160;
<span class="sc2">JS;</span>
&#160;
<span class="sc2">    <span class="sy0">//</span> Do NOT fail the attempt if it failed, please.</span>
<span class="sc2">    try <span class="br0">&#123;</span></span>
<span class="sc2">      if <span class="br0">&#40;</span> $wgUser-&gt;</span>isAnon() === false ) {
        $userName = $wgUser-&gt;getName();
        $wgPiwikCustomJS[] = '          _paq.push([&quot;setCustomVariable&quot;,1,&quot;username&quot;,&quot;'.$userName.'&quot;, &quot;visit&quot;]);'.PHP_EOL;
      }
    } catch(Exception $e) {  }</pre></div></div>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:10320-0!*!*!!*!*!*!esi=1 and timestamp 20150731184552 and revision id 40828
 -->
