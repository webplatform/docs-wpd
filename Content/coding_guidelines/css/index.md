---
title: WPD:Content/coding guidelines/css
---
<h1><span class="mw-headline" id="CSS_Coding_Guidelines">CSS Coding Guidelines</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>These guidelines aim to produce consistent coding style throughout all CSS examples on WebPlatform Docs.
</p><p>This article is based on Idiomatic CSS, a repository created by Nicolas Gallagher: <a rel="nofollow" class="external free" href="https://github.com/necolas/idiomatic-css">https://github.com/necolas/idiomatic-css</a>
</p>
<h2><span class="mw-headline" id="General_Principles">General Principles</span></h2>
<blockquote>"Part of being a good steward to a successful project is realizing that writing code for yourself is a Bad Idea™. If thousands of people are using your code, then write your code for maximum clarity, not your personal preference of how to get clever within the spec." - Idan Gazit</blockquote>
<ul><li> You are not a human code compiler/compressor, so do not try to be one.</li>
<li> All code in any code-base should look like a single person typed it, no matter how many people contributed.</li>
<li> Strictly enforce the agreed upon style.</li>
<li> If in doubt when deciding upon a style, use existing, common patterns.</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Whitespace">Whitespace</span></h2>
<p>Only one style should exist across the entire source of your code-base. Always be consistent in your use of whitespace. Use whitespace to improve readability.
</p>
<ul><li> Use soft indents (spaces).</li>
<li> Indent two spaces to maximize the amount of meaningful information per line.</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Comments">Comments</span></h2>
<ul><li> Place comments on a new line above their subject.</li>
<li> Avoid end of line comments.</li>
<li> Keep line-length to a sensible maximum, such as 80 columns.</li>
<li> Make liberal use of comments to break CSS code into discrete sections.</li>
<li> Use "sentence case" comments and consistent text indentation.</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="css source-css"><pre class="de1"><span class="coMULTI">/* ==========================================================================
   Section comment block
   ========================================================================== */</span>
&#160;
<span class="coMULTI">/* Sub-section comment block
   ========================================================================== */</span>
&#160;
<span class="coMULTI">/**
 * Short description using Doxygen-style comment format
 *
 * Long description first sentence starts here and continues on this line for a
 * while finally concluding here at the end of this paragraph.
 *
 * The long description is ideal for more detailed explanations and
 * documentation. It can include example HTML, URLs, or any other information
 * that is deemed necessary or useful.
 *
 * @tag This is a tag named 'tag'
 *
 * @todo This is a todo statement that describes an atomic task to be completed
 *   at a later date. It wraps after 80 characters and following lines are
 *   indented by 2 spaces.
 */</span>
&#160;
<span class="coMULTI">/* Basic comment */</span></pre></div></div>
<p><br />
</p>
<h2><span class="mw-headline" id="Format">Format</span></h2>
<ul><li> Use one discrete selector per line in multi-selector rulesets.</li>
<li> Include a single space before the opening brace of a ruleset.</li>
<li> Include one declaration per line in a declaration block.</li>
<li> Use one level of indentation for each declaration.</li>
<li> Include single space after the colon of a declaration.</li>
<li> Use lowercase and shorthand hex values, such as <code>#aaa</code>.</li>
<li> Use double quotes, like this <code>content: ""</code>.</li>
<li> Quote attribute values in selectors, such as <code>input[type="checkbox"]</code>.</li>
<li> Where allowed, avoid specifying units for zero-values, like this: <code>margin: 0</code>.</li>
<li> Include a space after each comma in comma-separated property or function values.</li>
<li> Include a semi-colon at the end of the last declaration in a declaration block.</li>
<li> Place the closing brace of a ruleset in the same column as the first character of the ruleset.</li>
<li> Separate each ruleset by a blank line.</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="css source-css"><pre class="de1">.selector-<span class="nu0">1</span><span class="sy0">,</span>
.selector-<span class="nu0">2</span><span class="sy0">,</span>
.selector-<span class="nu0">3</span><span class="br0">&#91;</span>type<span class="sy0">=</span><span class="st0">&quot;text&quot;</span><span class="br0">&#93;</span> <span class="br0">&#123;</span>
  -moz-box-sizing<span class="sy0">:</span> <span class="kw2">border-box</span><span class="sy0">;</span>
  -webkit-box-sizing<span class="sy0">:</span> <span class="kw2">border-box</span><span class="sy0">;</span>
  <span class="kw1">box-sizing</span><span class="sy0">:</span> <span class="kw2">border-box</span><span class="sy0">;</span>
  <span class="kw1">display</span><span class="sy0">:</span> <span class="kw2">block</span><span class="sy0">;</span>
  <span class="kw1">font-family</span><span class="sy0">:</span> helvetica<span class="sy0">,</span> arial<span class="sy0">,</span> <span class="kw2">sans-serif</span><span class="sy0">;</span>
  <span class="kw1">color</span><span class="sy0">:</span> <span class="re0">#333</span><span class="sy0">;</span>
  <span class="kw1">background</span><span class="sy0">:</span> <span class="re0">#fff</span><span class="sy0">;</span>
  <span class="kw1">background</span><span class="sy0">:</span> linear-gradient<span class="br0">&#40;</span><span class="re0">#fff</span><span class="sy0">,</span> <span class="kw3">rgba</span><span class="br0">&#40;</span><span class="nu0">0</span><span class="sy0">,</span> <span class="nu0">0</span><span class="sy0">,</span> <span class="nu0">0</span><span class="sy0">,</span> <span class="nu0">0.8</span><span class="br0">&#41;</span><span class="br0">&#41;</span><span class="sy0">;</span>
<span class="br0">&#125;</span></pre></div></div>
<h3><span class="mw-headline" id="Declaration_order">Declaration order</span></h3>
<p>Declarations should be ordered in accordance with a single principle.
Structurally important properties are declared prior to all others:
</p>
<ol><li> Position;</li>
<li> Box Model (Dimension);</li>
<li> Font;</li>
<li> Text;</li>
<li> Others;</li>
<li> Animation.</li></ol>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="css source-css"><pre class="de1"><span class="re1">.selector</span> <span class="br0">&#123;</span>
  <span class="coMULTI">/* Position */</span>
  <span class="kw1">position</span><span class="sy0">:</span> <span class="kw2">absolute</span><span class="sy0">;</span>
  <span class="kw1">top</span><span class="sy0">:</span> <span class="nu0">0</span><span class="sy0">;</span>
  <span class="kw1">right</span><span class="sy0">:</span> <span class="nu0">0</span><span class="sy0">;</span>
  <span class="kw1">bottom</span><span class="sy0">:</span> <span class="nu0">0</span><span class="sy0">;</span>
  <span class="kw1">left</span><span class="sy0">:</span> <span class="nu0">0</span><span class="sy0">;</span>
  <span class="kw1">z-index</span><span class="sy0">:</span> <span class="nu0">10</span><span class="sy0">;</span>
&#160;
  <span class="coMULTI">/* Display &amp; Box Model */</span>
  <span class="kw1">display</span><span class="sy0">:</span> <span class="kw2">inline-block</span><span class="sy0">;</span>
  <span class="kw1">overflow</span><span class="sy0">:</span> <span class="kw2">hidden</span><span class="sy0">;</span>
  <span class="kw1">box-sizing</span><span class="sy0">:</span> <span class="kw2">border-box</span><span class="sy0">;</span>
  <span class="kw1">width</span><span class="sy0">:</span> <span class="re3">100px</span><span class="sy0">;</span>
  <span class="kw1">height</span><span class="sy0">:</span> <span class="re3">100px</span><span class="sy0">;</span>
  <span class="kw1">padding</span><span class="sy0">:</span> <span class="re3">10px</span><span class="sy0">;</span>
  <span class="kw1">border</span><span class="sy0">:</span> <span class="re3">10px</span> <span class="kw2">solid</span> <span class="re0">#333</span><span class="sy0">;</span>
  <span class="kw1">margin</span><span class="sy0">:</span> <span class="re3">10px</span><span class="sy0">;</span>
&#160;
  <span class="coMULTI">/* Font */</span>
  <span class="kw1">font-family</span><span class="sy0">:</span> <span class="kw2">sans-serif</span><span class="sy0">;</span>
  <span class="kw1">font-size</span><span class="sy0">:</span> <span class="re3">16px</span><span class="sy0">;</span>
&#160;
  <span class="coMULTI">/* Text */</span>
  <span class="kw1">text-align</span><span class="sy0">:</span> <span class="kw1">right</span><span class="sy0">;</span>
&#160;
  <span class="coMULTI">/* Colors */</span>
  <span class="kw1">color</span><span class="sy0">:</span> <span class="re0">#fff</span><span class="sy0">;</span>
  <span class="kw1">background</span><span class="sy0">:</span> <span class="re0">#000</span><span class="sy0">;</span>
&#160;
  <span class="coMULTI">/* Others */</span>
  <span class="kw1">cursor</span><span class="sy0">:</span> <span class="kw2">pointer</span><span class="sy0">;</span>
&#160;
  <span class="coMULTI">/* Animation */</span>
  <span class="kw1">transition-property</span><span class="sy0">:</span> <span class="kw1">all</span><span class="sy0">;</span>
  <span class="kw1">transition-duration</span><span class="sy0">:</span> <span class="re3">.25s</span><span class="sy0">;</span>
<span class="br0">&#125;</span></pre></div></div>
<p>Strict alphabetical ordering is also relatively popular, but the drawback is that it separates related properties. For example, position offsets are no longer grouped together and box-model properties can end up spread throughout a declaration block.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Exceptions_and_slight_deviations">Exceptions and slight deviations</span></h3>
<p>Large blocks of single declarations can use a slightly different, single-line format. In this case, a space should be included after the opening brace and before the closing brace.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="css source-css"><pre class="de1"><span class="re1">.selector-1</span> <span class="br0">&#123;</span> <span class="kw1">width</span><span class="sy0">:</span> <span class="re3">10%</span><span class="sy0">;</span> <span class="br0">&#125;</span>
<span class="re1">.selector-2</span> <span class="br0">&#123;</span> <span class="kw1">width</span><span class="sy0">:</span> <span class="re3">20%</span><span class="sy0">;</span> <span class="br0">&#125;</span>
<span class="re1">.selector-3</span> <span class="br0">&#123;</span> <span class="kw1">width</span><span class="sy0">:</span> <span class="re3">30%</span><span class="sy0">;</span> <span class="br0">&#125;</span></pre></div></div>
<p>Long, comma-separated property values - such as collections of gradients or shadows - can be arranged across multiple lines in an effort to improve readability and produce more useful diffs. There are various formats that could be used; one example is shown below.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="css source-css"><pre class="de1"><span class="re1">.selector</span> <span class="br0">&#123;</span>
  <span class="kw1">background-image</span><span class="sy0">:</span>
    linear-gradient<span class="br0">&#40;</span><span class="re0">#fff</span><span class="sy0">,</span> <span class="re0">#ccc</span><span class="br0">&#41;</span><span class="sy0">,</span>
    linear-gradient<span class="br0">&#40;</span><span class="re0">#f3c</span><span class="sy0">,</span> <span class="re0">#4ec</span><span class="br0">&#41;</span><span class="sy0">;</span>
  <span class="kw1">box-shadow</span><span class="sy0">:</span>
    <span class="re3">1px</span> <span class="re3">1px</span> <span class="re3">1px</span> <span class="re0">#000</span><span class="sy0">,</span>
    <span class="re3">2px</span> <span class="re3">2px</span> <span class="re3">1px</span> <span class="re3">1px</span> <span class="re0">#ccc</span> <span class="kw2">inset</span><span class="sy0">;</span>
<span class="br0">&#125;</span></pre></div></div>
<p><br />
</p>
<h2><span class="mw-headline" id="Naming">Naming</span></h2>
<p>Naming is hard, but it is very important. It is a crucial part of the process of developing a maintainable code base, and ensuring that you have a relatively scalable interface between your HTML and CSS.
</p>
<ul><li> Avoid systematic use of abbreviated class names. Do not make things difficult to understand.</li>
<li> Use clear, thoughtful, and appropriate names for HTML classes.</li>
<li> Pick an understandable and consistent naming pattern that makes sense both within HTML files and CSS files.</li>
<li> Selectors for components should uses class names; avoid the use of generic tags and unique ids.</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="css source-css"><pre class="de1"><span class="coMULTI">/* Example of code with bad names */</span>
<span class="re1">.s-scr</span> <span class="br0">&#123;</span>
  <span class="kw1">overflow</span><span class="sy0">:</span> <span class="kw2">auto</span><span class="sy0">;</span>
<span class="br0">&#125;</span>
&#160;
<span class="re1">.cb</span> <span class="br0">&#123;</span>
  <span class="kw1">background</span><span class="sy0">:</span> <span class="re0">#000</span><span class="sy0">;</span>
<span class="br0">&#125;</span>
&#160;
<span class="coMULTI">/* Example of code with better names */</span>
<span class="re1">.is-scrollable</span> <span class="br0">&#123;</span>
  <span class="kw1">overflow</span><span class="sy0">:</span> <span class="kw2">auto</span><span class="sy0">;</span>
<span class="br0">&#125;</span>
&#160;
<span class="re1">.column-body</span> <span class="br0">&#123;</span>
  <span class="kw1">background</span><span class="sy0">:</span> <span class="re0">#000</span><span class="sy0">;</span>
<span class="br0">&#125;</span></pre></div></div>
<p><br />
</p>
<h2><span class="mw-headline" id="Practical_example">Practical example</span></h2>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="css source-css"><pre class="de1"><span class="coMULTI">/* ==========================================================================
   Grid layout
   ========================================================================== */</span>
&#160;
<span class="coMULTI">/**
  * Example HTML:
  *
  * &lt;div class=&quot;grid&quot;&gt;
  *   &lt;div class=&quot;cell cell-5&quot;&gt;&lt;/div&gt;
  *   &lt;div class=&quot;cell cell-5&quot;&gt;&lt;/div&gt;
  * &lt;/div&gt;
  */</span>
&#160;
<span class="re1">.grid</span> <span class="br0">&#123;</span>
  <span class="kw1">overflow</span><span class="sy0">:</span> <span class="kw2">visible</span><span class="sy0">;</span>
  <span class="kw1">height</span><span class="sy0">:</span> <span class="re3">100%</span><span class="sy0">;</span>
  <span class="coMULTI">/* Prevent inline-block cells wrapping */</span>
  <span class="kw1">white-space</span><span class="sy0">:</span> <span class="kw2">nowrap</span><span class="sy0">;</span>
  <span class="coMULTI">/* Remove inter-cell whitespace */</span>
  <span class="kw1">font-size</span><span class="sy0">:</span> <span class="nu0">0</span><span class="sy0">;</span>
<span class="br0">&#125;</span>
&#160;
<span class="re1">.cell</span> <span class="br0">&#123;</span>
  <span class="kw1">position</span><span class="sy0">:</span> <span class="kw2">relative</span><span class="sy0">;</span>
  <span class="kw1">display</span><span class="sy0">:</span> <span class="kw2">inline-block</span><span class="sy0">;</span>
  <span class="kw1">overflow</span><span class="sy0">:</span> <span class="kw2">hidden</span><span class="sy0">;</span>
  <span class="kw1">box-sizing</span><span class="sy0">:</span> <span class="kw2">border-box</span><span class="sy0">;</span>
  <span class="kw1">width</span><span class="sy0">:</span> <span class="re3">20%</span><span class="sy0">;</span>
  <span class="kw1">height</span><span class="sy0">:</span> <span class="re3">100%</span><span class="sy0">;</span>
  <span class="coMULTI">/* Set the inter-cell spacing */</span>
  <span class="kw1">padding</span><span class="sy0">:</span> <span class="nu0">0</span> <span class="re3">10px</span><span class="sy0">;</span>
  <span class="kw1">border</span><span class="sy0">:</span> <span class="re3">2px</span> <span class="kw2">solid</span> <span class="re0">#333</span><span class="sy0">;</span>
  <span class="kw1">vertical-align</span><span class="sy0">:</span> <span class="kw1">top</span><span class="sy0">;</span>
  <span class="coMULTI">/* Reset white-space */</span>
  <span class="kw1">white-space</span><span class="sy0">:</span> <span class="kw2">normal</span><span class="sy0">;</span>
  <span class="coMULTI">/* Reset font-size */</span>
  <span class="kw1">font-size</span><span class="sy0">:</span> <span class="re3">16px</span><span class="sy0">;</span>
<span class="br0">&#125;</span>
&#160;
<span class="coMULTI">/* Cell states */</span>
&#160;
<span class="re1">.cell</span><span class="re1">.is-animating</span> <span class="br0">&#123;</span>
  <span class="kw1">background-color</span><span class="sy0">:</span> <span class="re0">#fffdec</span><span class="sy0">;</span>
<span class="br0">&#125;</span>
&#160;
<span class="coMULTI">/* Cell dimensions
   ========================================================================== */</span>
&#160;
<span class="re1">.cell-1</span> <span class="br0">&#123;</span> <span class="kw1">width</span><span class="sy0">:</span> <span class="re3">10%</span><span class="sy0">;</span> <span class="br0">&#125;</span>
<span class="re1">.cell-2</span> <span class="br0">&#123;</span> <span class="kw1">width</span><span class="sy0">:</span> <span class="re3">20%</span><span class="sy0">;</span> <span class="br0">&#125;</span>
<span class="re1">.cell-3</span> <span class="br0">&#123;</span> <span class="kw1">width</span><span class="sy0">:</span> <span class="re3">30%</span><span class="sy0">;</span> <span class="br0">&#125;</span>
<span class="re1">.cell-4</span> <span class="br0">&#123;</span> <span class="kw1">width</span><span class="sy0">:</span> <span class="re3">40%</span><span class="sy0">;</span> <span class="br0">&#125;</span>
<span class="re1">.cell-5</span> <span class="br0">&#123;</span> <span class="kw1">width</span><span class="sy0">:</span> <span class="re3">50%</span><span class="sy0">;</span> <span class="br0">&#125;</span>
&#160;
<span class="coMULTI">/* Cell modifiers
   ========================================================================== */</span>
&#160;
.cell<span class="re4">--detail</span><span class="sy0">,</span>
<span class="re1">.cell<span class="re4">--important</span></span> <span class="br0">&#123;</span>
  <span class="kw1">border-width</span><span class="sy0">:</span> <span class="re3">4px</span><span class="sy0">;</span>
<span class="br0">&#125;</span></pre></div></div>
<div class="attribution">
<p><br />
</p><p><br />
</p>
</div>

<!-- 
NewPP limit report
CPU time usage: 0.177 seconds
Real time usage: 0.195 seconds
Preprocessor visited node count: 180/1000000
Preprocessor generated node count: 984/1000000
Post‐expand include size: 675/2097152 bytes
Template argument size: 764/2097152 bytes
Highest expansion depth: 4/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%  164.681      1 - -total
  9.19%   15.132      1 - Template:Page_Title
  6.07%    9.989      1 - Template:Flags
  5.77%    9.494      1 - Template:External_Attribution
  3.98%    6.554      1 - Template:Summary_Section
  2.86%    4.717      1 - Template:Notes_Section
  2.17%    3.570      1 - Template:Topics
  1.51%    2.481      1 - Template:Basic_Page
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:6070-0!*!*!!*!*!*!esi=1 and timestamp 20150731111813 and revision id 33761
 -->
