---
title: WPD:Projects/Homepage
---
<h2><span class="mw-headline" id="Homepage_project">Homepage project</span></h2>
<h3><span class="mw-headline" id="Summary">Summary</span></h3>
<p>This document describes the status and points to other related documentation for the <a rel="nofollow" class="external text" href="http://www.webplatform.org">www.webplatform.org "landing  page"</a> and various static content that aren't and should not be managed by a CMS. 
</p><p>The code is available on <a rel="nofollow" class="external text" href="https://github.com/webplatform/www.webplatform.org">github.com/webplatform.org/www.webplatform.org</a>, you can contribute by forking and submitting a pull-request,  report issues in <a rel="nofollow" class="external text" href="https://github.com/webplatform/www.webplatform.org/issues/new?title=Describe%20issue%20found%20&amp;labels=bug&amp;assignee=renoirb&amp;body=URL:%20Insert%20address%20where%20you%20found%20the%20problem">the repository issue tracker</a>.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Scope">Scope</span></h3>
<p>Static content are pages that we do not want to allow edition without audit such as: The landing page,  the stewards section, the logo, and error pages. Since those pages are't going to change frequently we could use serve plain static files directly, and when we need to change content, leverage a static site generator to create the documents but prevent us copy-pasting code through many files.
</p><p>Also, in order to improve the load time our our page, we could set in place workflows that helps us organize our CSS/JavaScript files and allow us to serve them with appropriate caching headers and reduced file-size (i.e. minification). Since the content at <i>www.webplatform.org</i> is mostly static, doesn't have application that requires cookies it will help us increase our HTTP cache HIT rate for both static pages and CSS/JavaScript files.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Objectives">Objectives</span></h3>
<ol><li> Workspace where a contributor can fork and improve CSS/JavaScript assets</li>
<li> Serve from one place all CSS/JavaScript, already minified (currently using MediaWiki's minifier; create load for no tangible benefit)</li>
<li> Ensure uniformity in pages without relying on server side language</li>
<li> Provide a workspace where we can focus on HTML/CSS/JavaScript without backend code involved</li></ol>
<p><br />
</p>
<h3><span class="mw-headline" id="Requirements">Requirements</span></h3>
<h4><span class="mw-headline" id="Functional">Functional</span></h4>
<ol><li> Leverage tools to generate, concatenate, validate, minify assets before deploying; serving only static files to the live site.</li>
<li> Support pages nesting in directories, for example: <i>stewards/microsoft</i></li>
<li> Support multiple tools (e.g. Process Markdown to HTML, Process templating engine, etc)</li></ol>
<h4><span class="mw-headline" id="Non_functional">Non functional</span></h4>
<ol><li> Workspace has to allow contributor to use without a too steep learning-curve</li>
<li> Tools to use the language of the Web Platform (e.g. JavaScript)</li>
<li> Serve as a reference to illustrate current Frontend development best-practices</li>
<li> Have as less as possible technology requirements (i.e. if we can rely only on JavaScript+Node, the better)</li></ol>
<h3><span class="mw-headline" id="Choice">Choice</span></h3>
<p><a href="/wiki/User:Renoirb" title="User:Renoirb">User:renoirb</a> has personally tried a few static site generators and found that <a rel="nofollow" class="external text" href="http://docpad.org/">DocPad</a> was the most sensible choice. What made the choice clear was that it took less than one hour to be able to do basic things such as sub pages, and other things described in the <a href="#Requirements">#Requirements</a> sections.  Among the projects <a href="/wiki/User:Renoirb" title="User:Renoirb">User:renoirb</a> tried were: Assemble, Octopress, Jekyll,  and Ghost.
</p><p>Besides the fact that DocPad was  uses CoffeeScript, we are not forced to use it in our own code.
</p>
<h2><span class="mw-headline" id="See_also">See also</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="https://gist.github.com/balupton/5519403">Use DocPad to pull and render content from a GitHub repository</a></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.018 seconds
Real time usage: 0.020 seconds
Preprocessor visited node count: 34/1000000
Preprocessor generated node count: 40/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:18114-0!*!0!!*!*!*!esi=1 and timestamp 20150731111109 and revision id 49912
 -->
