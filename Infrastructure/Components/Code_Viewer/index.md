---
title: WPD:Infrastructure/Components/Code Viewer
---
<p>Among Web Platform Docs features is a live code viewer and pastebin. It allows us to keep in one place all code samples.
</p><p>The webapp we are using for this is <a rel="nofollow" class="external text" href="http://lea.verou.me">Lea Verou</a>'s <a rel="nofollow" class="external text" href="http://dabblet.com/">Dabblet</a> available at <a rel="nofollow" class="external text" href="http://code.webplatform.org/"><b>code.webplatform.org</b></a> and keeps the code in a <a rel="nofollow" class="external text" href="https://gist.github.com/WebPlatformDocs">dedicated GitHub Gists repository</a>.
</p>
<h2><span class="mw-headline" id="Features">Features</span></h2>
<ul><li> Provides a live preview of input HTML, CSS, SVG, JavaScript</li>
<li> Allows users to share code snippets with each other, as a pastebin <i>(mostly done, still replies on GitHub)</i></li>
<li> Provides a way to open example code from the wiki in live example without copy-paste <i>(some progress, not done)</i></li></ul>
<h2><span class="mw-headline" id="Needs_improvement">Needs improvement</span></h2>
<ul><li> Cannot work directly with raw HTML file and HTTP headers</li>
<li> Find way to add another file and define its content-type</li></ul>
<h2><span class="mw-headline" id="Integration">Integration</span></h2>
<p>Because integration has many aspects, we will roll out full support for this feature in several steps.
</p>
<h3><span class="mw-headline" id="Roadmap">Roadmap</span></h3>
<h4><span class="mw-headline" id="Phase_1:_Static_Live_Code_Viewer">Phase 1: Static Live Code Viewer</span></h4>
<p><b>Status:</b> <i>Done</i>
</p>
<h4><span class="mw-headline" id="Phase_2:_Open_Examples_from_Wiki">Phase 2: Open Examples from Wiki</span></h4>
<p><b>Status:</b> <i>not started</i>
</p>
<h4><span class="mw-headline" id="Phase_3:_Inline_Live_Examples">Phase 3: Inline Live Examples</span></h4>
<p><b>Status:</b> <i>not started</i>
</p>
<h4><span class="mw-headline" id="Phase_4:_Host_Gists_on_WebPlatform.org">Phase 4: Host Gists on WebPlatform.org</span></h4>
<p><b>Status:</b> <i>not started</i>
</p>
<h3><span class="mw-headline" id="Other_Tasks">Other Tasks</span></h3>
<h2><span class="mw-headline" id="Technical_Requirements">Technical Requirements</span></h2>
<h3><span class="mw-headline" id="Dedicated_Subdomain">Dedicated Subdomain</span></h3>
<p>The public URL will be <a rel="nofollow" class="external text" href="http://code.webplatform.org">code.webplatform.org</a>.
</p>
<h3><span class="mw-headline" id="Additional_Subdomains">Additional Subdomains</span></h3>
<p>In addition to the public-facing URL, Dabblet needs two additional subdomains for security reasons:
</p>
<ul><li> <b>Result preview:</b> This is only used internally and not displayed to the user. It's a separate domain for security reasons, otherwise people could write dabblets that leak the user's access token. On dabblet.com, this is called preview.dabblet.com</li>
<li> <b>Full-page results:</b> This is for results without any dabblet chrome around them. Separate subdomain for the same security reasons. On dabblet, this is result.dabblet.com. This is not critical, worst case we could just disable this feature.</li></ul>
<h4><span class="mw-headline" id="Why_are_separate_subdomains_needed.3F">Why are separate subdomains needed?</span></h4>
<p>localStorage is local per subdomain. In dabblet, localStorage stores the user’s Github access token. An access token is a unique string Github Oauth sends to dabblet after authentication is succesfull, to identify the current user, and dabblet uses that token in subsequent requests. If executed scripts had access to dabblet’s localStorage info, they could steal the current user’s access token and send it to an arbitrary server so some attacker could use it to log in to Github as the dabblet user that access token belonged to.
</p>
<h3><span class="mw-headline" id="Github_API_keys">Github API keys</span></h3>
<p><a rel="nofollow" class="external free" href="https://github.com/organizations/webplatform/settings/applications/34604">https://github.com/organizations/webplatform/settings/applications/34604</a>
</p>
<h3><span class="mw-headline" id="File_edits_required">File edits required</span></h3>
<ul><li> code/global.js for Client API key (Done)</li>
<li> Rename sample.oauth.php to oauth.php</li>
<li> oauth.php for domain and Client &amp; Secret API keys (Done)</li>
<li> HTML and JS files, for the domain</li>
<li> Change .htaccess with the proper domain and subdomains (Partially done)</li></ul>
<h3><span class="mw-headline" id="Git">Git</span></h3>
<p>Github repo: <a rel="nofollow" class="external free" href="https://github.com/webplatform/dabblet">https://github.com/webplatform/dabblet</a>
</p><p>TODO: Need to be able to have separate git subdirectory with the above as a remote, so we can easily pull changes. Might be a problem if we have a different structure for the subdomains (i.e. completely separate files instead of subfolders).
</p>
<h3><span class="mw-headline" id="Deploy">Deploy</span></h3>
<p>salt-run deploy.run code.dabblet
</p>
<h2><span class="mw-headline" id="Branding">Branding</span></h2>
<ul><li> Logo</li>
<li> Skinning (colors etc)</li>
<li> Prism theme (will also be used on WPD)</li>
<li> Links to WPD sections</li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.016 seconds
Real time usage: 0.017 seconds
Preprocessor visited node count: 71/1000000
Preprocessor generated node count: 76/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:7390-0!*!*!!*!*!*!esi=1 and timestamp 20150730203934 and revision id 62569
 -->
