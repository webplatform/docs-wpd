---
title: WPD:External Attribution
---
<p>Most articles automatically maintain a history of all edits and who made them. However, some articles are seeded with already-comprehensive content that comes from external sites. Maintaining a link to the original content helps give credit to those sites, maintain a historical link to the original copy in case it is necessary in the future, and in some cases it is required by the license of the original source.
</p>
<h2><span class="mw-headline" id="Legal_Note">Legal Note</span></h2>
<p>Note that there are some potential exceptions to our general policy on attribution and external sources:
</p>
<ul><li> Documents that only state facts, and not interpretation, are not protected by copyright, and are thus outside the bounds of licensing . But this line can be gray... a compilation of facts is protected by copyright if the selection and arrangement of the material is original. Thus, if the contribution is based on another source, it's safer to provide and preserve attribution;</li>
<li> If all the original material from a particular source has been excised from the article, attribution for that source can optionally be removed; in practice, however, we are only using this to deliberately simplify the license the article is available under, e.g., if the original content was under CC-BY-SA (Attribution and Share Alike), we might remove all the old material so the replacement article can be reused under CC-BY. Even so, we may choose to keep the original attribution for social reasons.</li></ul>
<h2><span class="mw-headline" id="Adding_external_attribution_to_an_article">Adding external attribution to an article</span></h2>
<p>External attribution for a site should be added to an article when:
</p>
<ul><li> You are copying in text from an existing WPD article that contains external attribution (including when you are merging articles)</li>
<li> You are directly copying in a substantial piece of text, from a site that is already listed in the external attribution list, below. When in doubt about if the text is substantial, assume it is. (Remember to always ensure the license of the origin site is compatible with copying the text to this site before copying, even for sites already on the external attribution list.) <b>The guideline for substantial is: if it's long enough that it's possible to re-write the content in your own words</b>. In practice, this means that simple facts (like which version a given feature was supported by a browser) aren't substantial, but things that are a sentence or more are. If you are bringing in content from one of these sources but is not substantial, you should still include attribution to the original source (just not apply the alternate license for that content).</li></ul>
<p>If you are bringing in standard Creative Commons licensed content (CC-BY), such as from HTML5Rocks or Dev.Opera, your first edit to the WPD page should try to keep the original content as intact as possible. This way, future modifications to the original CC-BY content can be tracked using the built-in wiki versioning system without complicating the copyright attribution notices. There is no need for a wrapper &lt;div&gt; to indicate CC-BY content.
</p><p><b>Mixing in content with a CC-BY-SA license adds a lot of administrative overhead (WPD uses a different license) and therefore such imports should be avoided if at all possible.</b> This includes mixing in content from Mozilla Developer Network. If the text is short enough, consider rewriting it in your own words instead of copying directly. Any content that is licensed CC-BY-SA <b>must</b> be wrapped in a <code>&lt;div class='license-cc-by-sa'&gt;</code> to make it clear which portions of the content are under that license. See the <a href="#Dealing_With_CC-BY-SA_Content"> Dealing With CC-BY-SA Content</a> section below for more information.
</p><p>To add external attribution to an article, choose "Edit with Form" and check off the applicable box in the bottom of the form. Providing the actual link is optional in most cases; if it's not provided it will default to the organization's information page on WPD.
</p><p><b>Special note for Mozilla Developer Network content</b>: Mozilla Developer Network content is licensed under a CC-BY-SA license. If the article you are editing contains content originally from that site and the license has <i>not</i> <a href="/wiki/WPD:Copyright" title="WPD:Copyright"> been converted to the WPD license</a>, you <b>must check off the CC-BY-SA checkbox</b> when editing the article and <b>include a link to the original site.</b> Again, think carefully before mixing in CC-BY-SA content, as it is a different license from the rest of the site. See the <a href="#Dealing_With_CC-BY-SA_Content"> Dealing With CC-BY-SA Content</a> section below for more information.
</p>
<h2><span class="mw-headline" id="Canonical_list_of_sites_that_are_on_the_external_attribution_list">Canonical list of sites that are on the external attribution list</span></h2>
<p>The canonical list of external attribution sites is maintained at <a href="/wiki/Property:External_Attribution_Source" title="Property:External Attribution Source">Property:External_Attribution_Source</a>. The list has been copied here for convenience: 
</p>
<ul><li> <a rel="nofollow" class="external text" href="http://developer.mozilla.org">MDN</a></li>
<li> <a rel="nofollow" class="external text" href="http://www.html5rocks.com">HTML5Rocks</a></li>
<li> <a rel="nofollow" class="external text" href="http://www.MSDN.com">MSDN</a></li>
<li> <a rel="nofollow" class="external text" href="http://developers.facebook.com/html5">Facebook HTML5 Resource Center</a></li>
<li> <i>and some others</i></li></ul>
<p>This list will populate the article-editing form.
</p>
<h2><span class="mw-headline" id="Maintaining_the_list_of_external_attribution_sites">Maintaining the list of external attribution sites</span></h2>
<p>The list of sites that get external attribution is deliberately kept small. All items on the list should:
</p>
<ul><li> Have at least five articles on WPD that would list that site for external attribution</li>
<li> Be a well-regarded site that the community feels has valuable and accurate content.</li></ul>
<p>If you believe that there is a site that fulfills these requirements that is not yet on the list, contact an administrator to have them add it to the canonical list.
</p>
<h2><span class="mw-headline" id="Dealing_with_CC-BY-SA_content">Dealing with CC-BY-SA content</span></h2>
<p>In some cases there will be portions of content that come from sites with a CC-BY-SA license, like the Mozilla Developer Network (as opposed to the default CC-BY license for WPD). Maintaining content under multiple licenses is an administrative burden, and it is our long-term goal to remove CC-BY-SA licensed content from the site. Only sites in the canonical list of external attribution sites may have CC-BY-SA content ported over.
</p><p>These portions of content must be clearly marked in the wikitext with <code>&lt;div class='license-cc-by-sa'&gt;</code>. Those divs may not be removed until the license has <a href="/wiki/WPD:Copyright" title="WPD:Copyright"> been converted to the WPD license</a>. Any edits inside that box should retain the box.
</p><p>You can remove that box by rewriting the content inside the box in your own words and removing the original content inside that box.
</p><p>An article should have the CC-BY-SA configuration box checked in the "Edit with Form" page if and only if there are some <code>&lt;div class='license-cc-by-sa'&gt;</code> blocks in the article.
</p><p>Code without the CC-BY-SA configuration box checked falls under the normal license of the WPD, CC-BY.
</p>
<h2><span class="mw-headline" id="Example_box">Example box</span></h2>
<p>For articles with some CC-BY-SA content:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"><span class="sc2">&lt;<span class="kw2">details</span>&gt;</span>
  <span class="sc2">&lt;<span class="kw2">summary</span>&gt;</span>This article contains content originally from external sources, including ones licensed under the CC-BY-SA license.<span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">summary</span>&gt;</span>
  <span class="sc2">&lt;<span class="kw2">p</span>&gt;</span>
    Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network:
<span class="sc2">&lt;<span class="kw2">a</span> <span class="kw3">href</span><span class="sy0">=</span><span class="st0">&quot;http://developer.mozilla.org/foo&quot;</span> <span class="kw3">target</span><span class="sy0">=</span><span class="st0">&quot;_blank&quot;</span>&gt;</span>Foo<span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">a</span>&gt;</span>
  <span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">p</span>&gt;</span>
  <span class="sc2">&lt;<span class="kw2">p</span>&gt;</span>
    Portions of this content come from Foo.org: <span class="sc2">&lt;<span class="kw2">a</span> <span class="kw3">href</span><span class="sy0">=</span><span class="st0">&quot;http://foo.org/baz&quot;</span> <span class="kw3">target</span><span class="sy0">=</span><span class="st0">&quot;_blank&quot;</span>&gt;</span>Baz<span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">a</span>&gt;</span>
  <span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">p</span>&gt;</span>
<span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">details</span>&gt;</span></pre></div></div>
<p>For articles with no CC-BY-SA content:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"><span class="sc2">&lt;<span class="kw2">details</span>&gt;</span>
  <span class="sc2">&lt;<span class="kw2">summary</span>&gt;</span>This article contains content originally from external sources.<span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">summary</span>&gt;</span>
  <span class="sc2">&lt;<span class="kw2">p</span>&gt;</span>
    Portions of this content come from the Mozilla Developer Network:
<span class="sc2">&lt;<span class="kw2">a</span> <span class="kw3">href</span><span class="sy0">=</span><span class="st0">&quot;http://developer.mozilla.org/foo&quot;</span> <span class="kw3">target</span><span class="sy0">=</span><span class="st0">&quot;_blank&quot;</span>&gt;</span>Foo<span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">a</span>&gt;</span>
  <span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">p</span>&gt;</span>
  <span class="sc2">&lt;<span class="kw2">p</span>&gt;</span>
    Portions of this content come from Foo.org: <span class="sc2">&lt;<span class="kw2">a</span> <span class="kw3">href</span><span class="sy0">=</span><span class="st0">&quot;http://foo.org/baz&quot;</span> <span class="kw3">target</span><span class="sy0">=</span><span class="st0">&quot;_blank&quot;</span>&gt;</span>Baz<span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">a</span>&gt;</span>
  <span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">p</span>&gt;</span>
<span class="sc2">&lt;<span class="sy0">/</span><span class="kw2">details</span>&gt;</span></pre></div></div>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  some browsers don't support the details element, so we'll need a polyfill.
</p>
</div>

<!-- 
NewPP limit report
CPU time usage: 0.043 seconds
Real time usage: 0.047 seconds
Preprocessor visited node count: 34/1000000
Preprocessor generated node count: 94/1000000
Post‐expand include size: 224/2097152 bytes
Template argument size: 75/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    4.643      1 - -total
100.00%    4.643      1 - Template:TODO
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:194-0!*!0!!*!*!*!esi=1 and timestamp 20150730202725 and revision id 67493
 -->
