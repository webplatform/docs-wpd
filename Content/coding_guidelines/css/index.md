---
title: WPD:Content/coding guidelines/css
path: Content/coding_guidelines/css

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
<p><br />
</p>
<pre class="language-css" data-lang="css">
/* ==========================================================================
   Section comment block
   ========================================================================== */

/* Sub-section comment block
   ========================================================================== */

/**
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
 */

/* Basic comment */
</pre>
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
<p><br />
</p>
<pre class="language-css" data-lang="css">
.selector-1,
.selector-2,
.selector-3[type="text"] {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  display: block;
  font-family: helvetica, arial, sans-serif;
  color: #333;
  background: #fff;
  background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}
</pre>
<p><br />
</p>
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
<p><br />
</p>
<pre class="language-css" data-lang="css">
.selector {
  /* Position */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 10;

  /* Display &amp; Box Model */
  display: inline-block;
  overflow: hidden;
  box-sizing: border-box;
  width: 100px;
  height: 100px;
  padding: 10px;
  border: 10px solid #333;
  margin: 10px;

  /* Font */
  font-family: sans-serif;
  font-size: 16px;

  /* Text */
  text-align: right;

  /* Colors */
  color: #fff;
  background: #000;

  /* Others */
  cursor: pointer;

  /* Animation */
  transition-property: all;
  transition-duration: .25s;
}
</pre>
<p><br />
Strict alphabetical ordering is also relatively popular, but the drawback is that it separates related properties. For example, position offsets are no longer grouped together and box-model properties can end up spread throughout a declaration block.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Exceptions_and_slight_deviations">Exceptions and slight deviations</span></h3>
<p>Large blocks of single declarations can use a slightly different, single-line format. In this case, a space should be included after the opening brace and before the closing brace.
</p><p><br />
</p>
<pre class="language-css" data-lang="css">
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
</pre>
<p><br />
Long, comma-separated property values - such as collections of gradients or shadows - can be arranged across multiple lines in an effort to improve readability and produce more useful diffs. There are various formats that could be used; one example is shown below.
</p><p><br />
</p>
<pre class="language-css" data-lang="css">
.selector {
  background-image:
    linear-gradient(#fff, #ccc),
    linear-gradient(#f3c, #4ec);
  box-shadow:
    1px 1px 1px #000,
    2px 2px 1px 1px #ccc inset;
}
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="Naming">Naming</span></h2>
<p>Naming is hard, but it is very important. It is a crucial part of the process of developing a maintainable code base, and ensuring that you have a relatively scalable interface between your HTML and CSS.
</p>
<ul><li> Avoid systematic use of abbreviated class names. Do not make things difficult to understand.</li>
<li> Use clear, thoughtful, and appropriate names for HTML classes.</li>
<li> Pick an understandable and consistent naming pattern that makes sense both within HTML files and CSS files.</li>
<li> Selectors for components should uses class names; avoid the use of generic tags and unique ids.</li></ul>
<p><br />
</p>
<pre class="language-css" data-lang="css">
/* Example of code with bad names */
.s-scr {
  overflow: auto;
}

.cb {
  background: #000;
}

/* Example of code with better names */
.is-scrollable {
  overflow: auto;
}

.column-body {
  background: #000;
}
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="Practical_example">Practical example</span></h2>
<pre class="language-css" data-lang="css">
/* ==========================================================================
   Grid layout
   ========================================================================== */

/**
  * Example HTML:
  *
  * <div class="grid">
  *   <div class="cell cell-5"></div>
  *   <div class="cell cell-5"></div>
  * </div>
<pre> */
</pre>
<p>.grid {
</p>
<pre> overflow: visible;
 height: 100%;
 /* Prevent inline-block cells wrapping */
 white-space: nowrap;
 /* Remove inter-cell whitespace */
 font-size: 0;
</pre>
<p>}
</p><p>.cell {
</p>
<pre> position: relative;
 display: inline-block;
 overflow: hidden;
 box-sizing: border-box;
 width: 20%;
 height: 100%;
 /* Set the inter-cell spacing */
 padding: 0 10px;
 border: 2px solid #333;
 vertical-align: top;
 /* Reset white-space */
 white-space: normal;
 /* Reset font-size */
 font-size: 16px;
</pre>
<p>}
</p><p>/* Cell states */
</p><p>.cell.is-animating {
</p>
<pre> background-color: #fffdec;
</pre>
<p>}
</p><p>/* Cell dimensions
</p>
<pre>  ========================================================================== */
</pre>
<p>.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }
</p><p>/* Cell modifiers
</p>
<pre>  ========================================================================== */
</pre>
<p>.cell--detail,
.cell--important {
</p>
<pre> border-width: 4px;
</pre>
<p>}
</p>
</pre>
<div class="attribution">
<p><br />
</p><p><br />
</p>
</div>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:6070-0!*!*!!*!*!*!esi=1 and timestamp 20150810200001 and revision id 33761
 -->
