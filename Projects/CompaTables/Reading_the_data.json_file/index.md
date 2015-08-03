---
title: WPD:Projects/CompaTables/Reading the data.json file
---
<h1><span class="mw-headline" id="Reading_the_JSON_file">Reading the JSON file</span></h1>
<p>Some examples on how you can read the data using <i>underscore-cli</i>.
</p>
<h2><span class="mw-headline" id="Query_using_the_terminal">Query using the terminal</span></h2>
<p>The compatibility data can be read either from the published location <a rel="nofollow" class="external text" href="http://docs.webplatform.org/compat/data.json">docs.webplatform.org/compat/data.json</a> or through the <a rel="nofollow" class="external text" href="https://github.com/webplatform/compatibility-data"><b>webplatform/compatibility-data</b> project on GitHub</a>. The latter provides the <i>underscore-cli</i> dependency out of the box.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="bash source-bash"><pre class="de1"><span class="kw2">git clone</span> https:<span class="sy0">//</span>github.com<span class="sy0">/</span>webplatform<span class="sy0">/</span>compatibility-data.git
<span class="kw3">cd</span> compatibility-data
npm <span class="kw2">install</span>
<span class="kw2">cat</span> data-human.json <span class="sy0">|</span> underscore extract <span class="st_h">'data.css.cursor'</span>
<span class="br0">&#91;</span>
  <span class="br0">&#123;</span>
    <span class="st0">&quot;breadcrumb&quot;</span>: <span class="br0">&#91;</span><span class="st0">&quot;css&quot;</span>, <span class="st0">&quot;cursor&quot;</span><span class="br0">&#93;</span>,
    <span class="st0">&quot;jsonselect&quot;</span>: <span class="st0">&quot;:root &gt; .data &gt; .css &gt; .cursor&quot;</span>,
    <span class="st0">&quot;contents&quot;</span>: <span class="br0">&#123;</span> <span class="st0">&quot;desktop&quot;</span>: <span class="br0">&#123;</span> <span class="br0">&#125;</span>, <span class="st0">&quot;mobile&quot;</span>: <span class="br0">&#123;</span> <span class="br0">&#125;</span> <span class="br0">&#125;</span>,
    <span class="st0">&quot;links&quot;</span>: <span class="br0">&#91;</span>
      <span class="br0">&#123;</span>
        <span class="st0">&quot;title&quot;</span>: <span class="st0">&quot;Original article on MDN in css cursor&quot;</span>,
        <span class="st0">&quot;url&quot;</span>: <span class="st0">&quot;https://developer.mozilla.org/en-US/docs/Web/CSS/cursor&quot;</span>
      <span class="br0">&#125;</span>
    <span class="br0">&#93;</span>
  <span class="br0">&#125;</span>
<span class="br0">&#93;</span></pre></div></div>

<!-- 
NewPP limit report
CPU time usage: 0.033 seconds
Real time usage: 0.034 seconds
Preprocessor visited node count: 9/1000000
Preprocessor generated node count: 32/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:26595-0!*!*!!*!*!*!esi=1 and timestamp 20150731040624 and revision id 70600
 -->
