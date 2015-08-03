---
title: WPD:Design/css property template
---
<h1><span class="mw-headline" id="font-size">font-size</span></h1>
<p>&lt;compatability topic="css" type="property" feature="font-size" format="list"&gt; &lt;/compatability&gt;
</p>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p><code>font-size</code> sets the font size of the element to which it is applied, and that of its descendants. You can size text using absolute measurements, or measurements relative to the affected element's parent or root elements. <a href="/wiki/guides/css_text_styling_fundamentals" title="guides/css text styling fundamentals">CSS Text Styling Fundamentals</a> provides an overview.
</p>
<h2><span class="mw-headline" id="Syntax">Syntax</span></h2>
<table class="wikitable template_test">
<tr>
<th> Property name
</th>
<th> Values
</th>
<th> Example
</th></tr>
<tr>
<th rowspan="4"> font-size
</th>
<td> <a href="#absolute-size_value">absolute-size</a>
</td>
<td> <a href="#absolute-size_examples">font-size: small;</a>
</td></tr>
<tr>
<td> <a href="#relative-size_value">relative-size</a>
</td>
<td> <a href="#relative-size_examples">font-size: larger;</a>
</td></tr>
<tr>
<td> <a href="#length_value">length</a>
</td>
<td> <a href="#length_examples">font-size: 1.5em;</a>
</td></tr>
<tr>
<td> <a href="#percentage_value">percentage</a>
</td>
<td> <a href="#percentage_examples">font-size: 110%;</a>
</td></tr></table>
<h2><span class="mw-headline" id="Values">Values</span></h2>
<dl>
<dt id="absolute-size_value" class="template_test">absolute-size</dt>
<dd class="template_test">A set of keywords indicating predefined font sizes that scale according to font setting preferences or each browser's default values. From small to large, possible values are <b>xx-small</b>, <b>x-small</b>, <b>small</b>, <b>medium</b>, <b>large</b>, <b>x-large</b>, and <b>xx-large</b>.
<br />
<b>Keywords:</b>
<ul class="keywords">
   <li><code class="value keyword">xx-small</code> 3/5 parent font-size</li>
   <li><code class="value keyword">x-small</code> 3/4 parent font-size</li>
   <li><code class="value keyword">small</code> 8/9 parent font-size</li>
   <li><code class="value keyword">medium</code> 1 parent font-size</li>
   <li><code class="value keyword">large</code> 6/5 parent font-size</li>
   <li><code class="value keyword">x-large</code> 3/2 parent font-size</li>
   <li><code class="value keyword">xx-large</code> 2/1 parent font-size</li>
</ul>
<p></dd>
</p><p><dt id="relative-size_value" class="template_test">relative-size</dt>
<dd class="template_test">A set of keywords interpreted relative to the parent element's <b>font-size</b> — either <b>smaller</b> or <b>larger</b>.
<br />
<b>Keywords:</b>
</p>
<ul class="keywords">
    <li><code class="value keyword">smaller</code> 1 increment lower than parent font-size (e.g. if the parent font-size is <code>medium</code>, the <code>smaller</code> value would be interpreted as <code>small</code>)</li>
   <li><code class="value keyword">larger</code>  1 increment higher than parent font-size (e.g. if the parent font-size is <code>medium</code>, the <code>larger</code> value would be interpreted as <code>large</code>)</li>
</ul>
<p></dd>
</p><p><dt id="length_value" class="template_test">length</dt>
<dd class="template_test">A positive numeric value followed by a string designating <a href="/wiki/css/data_types/length" title="css/data types/length">absolute or relative units of length</a>. Proportional <a href="/wiki/css/data_types/length" title="css/data types/length"><b>em</b> and <b>ex</b></a> measurements are based on the parent element's <b>font-size</b>, while <a href="/wiki/css/data_types/length" title="css/data types/length"><b>rem</b></a> measurements are based on that of the root element.</dd>
</p><p><dt id="percentage_value" class="template_test">percentage</dt>
<dd class="template_test">A positive integer followed by a percent (<a href="/w/index.php?title=css/data_types/numeric&amp;action=edit&amp;redlink=1" class="new" title="css/data types/numeric (page does not exist)"><b>%</b></a>), indicating a percentage of the parent element's <b>font-size</b>.</dd>
</p>
</dl>
<h2><span class="mw-headline" id="Overview_table">Overview table</span></h2>
<table class="wikitable">
<tr>
<td> Initial value
</td>
<td> <code>medium</code>
</td></tr>
<tr>
<td> Applies to
</td>
<td> All elements
</td></tr>
<tr>
<td> Inherited
</td>
<td>  Yes
</td></tr>
<tr>
<td> Media
</td>
<td> visual
</td></tr>
<tr>
<td> Computed value
</td>
<td> absolute size in <b>px</b> units
</td></tr>
<tr>
<td> Animatable
</td>
<td> Yes
</td></tr>
<tr>
<td> CSS Object Model Property
</td>
<td> <code>fontSize</code>
</td></tr></table>
<h2><span class="mw-headline" id="Examples">Examples</span></h2>
<h3><span class="mw-headline" id="absolute-size.09_examples">absolute-size	 examples</span></h3>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"> font-size: small;</pre></div></div>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"> font-size: xx-large;</pre></div></div>
<h3><span class="mw-headline" id="relative-size_examples">relative-size examples</span></h3>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"> font-sizes: larger;</pre></div></div>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"> font-sizes: smaller;</pre></div></div>
<h3><span class="mw-headline" id="length_examples">length examples</span></h3>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"> font-size: 1.5em;</pre></div></div>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"> border-radius: 5px;</pre></div></div>
<h3><span class="mw-headline" id="percentage_examples">percentage examples</span></h3>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"> font-size: 110%;</pre></div></div>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"> border-radius: 50%;</pre></div></div>
<h3><span class="mw-headline" id="Other_examples">Other examples</span></h3>
<p>Redefine the typical <b>16px</b> default <b>medium</b> value as <b>10px</b>, then redefine other tags in proportion to the root:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">html { font-size: 62.5%; } 
/* 
16 * 62.5% == 10 
*/
&#160;
h1 { font-size: 3.6rem }   /* 36px */
h2 { font-size: 2.4rem }   /* 24px */
p  { font-size: 1.4rem }   /* 14px */</pre></div></div>
<p><br />
</p>
<h2><span class="mw-headline" id="Usage">Usage</span></h2>
<h2><span class="mw-headline" id="Notes">Notes</span></h2>
<h2><span class="mw-headline" id="Compatibility">Compatibility</span></h2>
<p>&lt;compatability topic="css" type="property" feature="font-size"&gt; &lt;/compatability&gt;
</p>
<h2><span class="mw-headline" id="Related_Specifications">Related Specifications</span></h2>
<table class="wikitable">
<tr>
<th> Specification
</th>
<th> Status
</th>
<th> Related Changes
</th></tr>
<tr>
<td> <a rel="nofollow" class="external text" href="http://www.w3.org/TR/css3-fonts/#font-size-prop">CSS Fonts Module Level 3</a>
</td>
<td> Working Draft
</td>
<td>
</td></tr>
<tr>
<td> <a rel="nofollow" class="external text" href="http://www.w3.org/TR/css3-values/">CSS Values and Units Module Level 3</a>
</td>
<td> Candidate Recommendation
</td>
<td>
</td></tr>
<tr>
<td> <a rel="nofollow" class="external text" href="http://www.w3.org/TR/CSS2/">Cascading Style Sheets Level 2 Revision 1 (CSS 2.1) Specification</a>
</td>
<td> W3C Recommendation
</td>
<td>
</td></tr></table>
<h2><span class="mw-headline" id="See_Also">See Also</span></h2>

<!-- 
NewPP limit report
CPU time usage: 0.092 seconds
Real time usage: 0.097 seconds
Preprocessor visited node count: 162/1000000
Preprocessor generated node count: 286/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:8363-0!*!0!!*!*!*!esi=1 and timestamp 20150731113910 and revision id 33700
 -->
