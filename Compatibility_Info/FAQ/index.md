---
title: WPD:Compatibility Info/FAQ
---
<h1><span class="mw-headline" id="Frequently_Asked_Questions_.28.22FAQ.22.29">Frequently Asked Questions ("FAQ")</span></h1>
<p>Questions we have been asked about our use of the Compatibility data and tables in our content.
</p>
<h2><span class="mw-headline" id="Where_is_the_data_coming_from.3F">Where is the data coming from?</span></h2>
<p>The data was originally polled from <a rel="nofollow" class="external text" href="http://developer.mozilla.org">Mozilla Developer Network ("MDN")</a> as a one time import. The data was read using an <a rel="nofollow" class="external text" href="https://github.com/webplatform/mdn-compat-importer">importer we made for this purpose (code on GitHub)</a>. We converted into a JSON file that we used as a starting point.
</p><p>At this time we are maintaining this data in <a rel="nofollow" class="external text" href="https://github.com/webplatform/compatibility-data"><b>webplatform/compatibility-data</b> on GitHub</a>.
</p>
<h2><span class="mw-headline" id="The_compatibility_data_has_been_changed_since_I_maintained_it_in_the_wiki_.28where_is_it.3F.29">The compatibility data has been changed since I maintained it in the wiki (where is it?)</span></h2>
<p>When you added data to the document you are talking about, did you see the warning about our intention to not maintain compatibility data in the wiki?
</p><p>You do not see the previous compatibility table based on the wiki source because we separated the way of storing the data, and how to generate the tables from the wiki content.
</p><p>The compatibility data you see in <a rel="nofollow" class="external text" href="https://github.com/webplatform/compatibility-data">GitHub/webplatform/compatibility-data repo</a> as a big JSON file has been scraped from MDN, as a one time import, a few weeks ago.
</p><p>The objective of this is to ease the maintenance of the data, and eventually, remove the need to maintain manually. Our end goal is to feed data from browser builds test runs coming from <a rel="nofollow" class="external text" href="https://github.com/w3c/web-platform-test">GitHub/w3c/web-platform-test</a> tests which will give us great compat data accuracy.
</p><p><br />
</p>
<h2><span class="mw-headline" id="What_is_the_format_of_the_data.3F">What is the format of the data?</span></h2>
<p>Here is one entry sample. To represent this sample we could annotate it as <code>feature="css" topic="border"</code>.
</p><p>What generates the HTML table is inside "<b>contents</b>" section where we separate by "<i>mobile</i>" and "<i>desktop</i>" browser types. In each browser types, we list a sub feature description as the key. This feature description (e.g. "Basic support") is freeform text and anything can be used to describe.
</p><p>You can safely ignore the "breadcrumb", "jsonselect", and "notes" keys. They were created for maintenance and might be removed in a near future.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="javascript source-javascript"><pre class="de1"><span class="br0">&#123;</span>
  <span class="st0">&quot;data&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span>
    <span class="st0">&quot;css&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span>
      <span class="st0">&quot;border&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span>
        <span class="st0">&quot;breadcrumb&quot;</span><span class="sy0">:</span> <span class="br0">&#91;</span><span class="st0">&quot;css&quot;</span><span class="sy0">,</span> <span class="st0">&quot;border&quot;</span><span class="br0">&#93;</span><span class="sy0">,</span>
        <span class="st0">&quot;jsonselect&quot;</span><span class="sy0">:</span> <span class="st0">&quot;:root &gt; .data &gt; .css &gt; .border&quot;</span><span class="sy0">,</span>
        <span class="st0">&quot;contents&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span>
          <span class="st0">&quot;desktop&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span>
            <span class="st0">&quot;Basic support&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span>
              <span class="st0">&quot;Chrome&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;1.0&quot;</span><span class="sy0">:</span> <span class="st0">&quot;y&quot;</span> <span class="br0">&#125;</span><span class="sy0">,</span>
              <span class="st0">&quot;Firefox&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;notes&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;normal&quot;</span><span class="sy0">:</span> <span class="st0">&quot;1.0 (1.7 or earlier)&quot;</span> <span class="br0">&#125;</span><span class="sy0">,</span> <span class="st0">&quot;1.0&quot;</span><span class="sy0">:</span> <span class="st0">&quot;y&quot;</span> <span class="br0">&#125;</span><span class="sy0">,</span>
              <span class="st0">&quot;Internet Explorer&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;4.0&quot;</span><span class="sy0">:</span> <span class="st0">&quot;y&quot;</span> <span class="br0">&#125;</span><span class="sy0">,</span>
              <span class="st0">&quot;Opera&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;3.5&quot;</span><span class="sy0">:</span> <span class="st0">&quot;y&quot;</span> <span class="br0">&#125;</span><span class="sy0">,</span>
              <span class="st0">&quot;Safari&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;notes&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;normal&quot;</span><span class="sy0">:</span> <span class="st0">&quot;1.0 (85)&quot;</span> <span class="br0">&#125;</span><span class="sy0">,</span> <span class="st0">&quot;1.0&quot;</span><span class="sy0">:</span> <span class="st0">&quot;y&quot;</span> <span class="br0">&#125;</span>
            <span class="br0">&#125;</span>
          <span class="br0">&#125;</span><span class="sy0">,</span>
          <span class="st0">&quot;mobile&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span>
            <span class="st0">&quot;Basic support&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span>
              <span class="st0">&quot;Android&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;?&quot;</span><span class="sy0">:</span> <span class="st0">&quot;u&quot;</span> <span class="br0">&#125;</span><span class="sy0">,</span>
              <span class="st0">&quot;Firefox Mobile&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;notes&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;normal&quot;</span><span class="sy0">:</span> <span class="st0">&quot;1.0 (1.9.2)&quot;</span> <span class="br0">&#125;</span><span class="sy0">,</span> <span class="st0">&quot;1.0&quot;</span><span class="sy0">:</span> <span class="st0">&quot;y&quot;</span> <span class="br0">&#125;</span><span class="sy0">,</span>
              <span class="st0">&quot;IE Phone&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;?&quot;</span><span class="sy0">:</span> <span class="st0">&quot;u&quot;</span> <span class="br0">&#125;</span><span class="sy0">,</span>
              <span class="st0">&quot;Opera Mobile&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;?&quot;</span><span class="sy0">:</span> <span class="st0">&quot;u&quot;</span> <span class="br0">&#125;</span><span class="sy0">,</span>
              <span class="st0">&quot;Safari Mobile&quot;</span><span class="sy0">:</span> <span class="br0">&#123;</span> <span class="st0">&quot;1.0&quot;</span><span class="sy0">:</span> <span class="st0">&quot;y&quot;</span> <span class="br0">&#125;</span>
            <span class="br0">&#125;</span>
          <span class="br0">&#125;</span>
        <span class="br0">&#125;</span><span class="sy0">,</span>
        <span class="st0">&quot;links&quot;</span><span class="sy0">:</span> <span class="br0">&#91;</span>
          <span class="br0">&#123;</span>
            <span class="st0">&quot;title&quot;</span><span class="sy0">:</span> <span class="st0">&quot;Original article on MDN in css border&quot;</span><span class="sy0">,</span>
            <span class="st0">&quot;url&quot;</span><span class="sy0">:</span> <span class="st0">&quot;https://developer.mozilla.org/en-US/docs/Web/CSS/border&quot;</span>
          <span class="br0">&#125;</span>
        <span class="br0">&#93;</span>
      <span class="br0">&#125;</span>
    <span class="br0">&#125;</span>
  <span class="br0">&#125;</span>
<span class="br0">&#125;</span></pre></div></div>
<p><br />
</p>
<h3><span class="mw-headline" id="Support_level_values_legend">Support level values legend</span></h3>
<p>Based on <a rel="nofollow" class="external text" href="https://github.com/Fyrd/caniuse/blob/master/CONTRIBUTING.md#supported-changes">caniuse.com's</a> model:
</p>
<table>
<tr>
<td><b>y</b>
</td>
<td>(Y)es, supported by default
</td></tr>
<tr>
<td><b>a</b>
</td>
<td>(A)lmost supported (aka Partial support)
</td></tr>
<tr>
<td><b>n</b>
</td>
<td>(N)o support, or disabled by default
</td></tr>
<tr>
<td><b>p</b>
</td>
<td>No support, but has (P)olyfill
</td></tr>
<tr>
<td><b>u</b>
</td>
<td>Support <i>is</i> (u)nknown
</td></tr>
<tr>
<td><b>x</b>
</td>
<td>Requires prefi(x) to work
</td></tr></table>
<p><br />
</p>
<h2><span class="mw-headline" id="How_do_you_get_the_compatibility_tables_on_your_docs_pages.3F">How do you get the compatibility tables on your docs pages?</span></h2>
<p>We created a <a href="/wiki/WPD:Infrastructure/Components/WebPlatformDocsExtensionBundle" title="WPD:Infrastructure/Components/WebPlatformDocsExtensionBundle" class="mw-redirect">MediaWiki extension "WebPlatformDocs Extension bundle"</a> that takes care of generating the HTML views you see on our documentation pages. This extension reads the data from flat-file JSON file.
</p><p>Each documentation page that should require a compatibility table have, in some way, an inclusion of the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/Template:Compatibility">Template:Compatibility "template"</a>. If you want to see how we set the inclusion in place, head over to  <a href="/wiki/WPD:Projects/CompaTables/Adding_to_our_content" title="WPD:Projects/CompaTables/Adding to our content">WPD:Projects/CompaTables/Adding_to_our_content</a>.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Can_I_get_and_use_the_data.3F">Can I get and use the data?</span></h2>
<p>Sure you can!  Our compatibility table is based on a raw JSON file and you can use it too.  We serve it from <a rel="nofollow" class="external text" href="http://docs.webplatform.org/compat/data.json"><b>docs.webplatform.org/compat/data.json</b></a>, and also serve an idempotent <a rel="nofollow" class="external text" href="http://docs.webplatform.org/compat/data.json">"<i>human friendly</i>" (<b>data-human.json</b>) version with indentation</a>. 
</p><p>If you are command line inclined, you can also make queries to it using <i><a rel="nofollow" class="external text" href="https://github.com/ddopson/underscore-cli">underscore-cli</a></i>. The page <a href="/wiki/WPD:Projects/CompaTables/Reading_the_data.json_file" title="WPD:Projects/CompaTables/Reading the data.json file">WPD:Projects/CompaTables/Reading_the_data.json_file</a> explains how to do.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Can_I_improve_the_data.3F">Can I improve the data?</span></h2>
<p>Sure!  At this time, we published our raw compatibility data as <a rel="nofollow" class="external text" href="https://github.com/webplatform/compatibility-data"><b>webplatform/compatibility-data</b> on GitHub</a>. The manual edition is a temporary process until we improve it.
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:30852-0!*!0!!*!*!*!esi=1 and timestamp 20150731185616 and revision id 70680
 -->
