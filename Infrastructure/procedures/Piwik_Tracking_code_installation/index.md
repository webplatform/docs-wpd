---
title: WPD:Infrastructure/procedures/Piwik Tracking code installation
path: Infrastructure/procedures/Piwik_Tracking_code_installation

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
<pre class="language-html5" data-lang="html5">
// In file Piwik.hooks.php, within AddPiwik method

    $wgPiwikCustomJS[] = <<<'JS'

          // Note from renoirb: Should be moved somewhere else soon
          jQuery(document).ready(function(){
              jQuery('body').on('click', '#ca-edit', function(){
                 if (typeof _paq&#160;!== 'undefined') {
                    _paq.push(['trackGoal',1]);// Goal specific to edit a page
                 }
              });
          });

JS;

    // Do NOT fail the attempt if it failed, please.
    try {
      if ( $wgUser->isAnon() === false ) {
        $userName = $wgUser->getName();
        $wgPiwikCustomJS[] = '          _paq.push(["setCustomVariable",1,"username","'.$userName.'", "visit"]);'.PHP_EOL;
      }
    } catch(Exception $e) {  }
</pre>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:10320-0!*!*!!*!*!*!esi=1 and timestamp 20150810200035 and revision id 40828
 -->
