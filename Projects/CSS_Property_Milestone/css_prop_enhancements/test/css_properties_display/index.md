---
title: WPD:Projects/CSS Property Milestone/css prop enhancements/test/css properties display
---
<h1><span class="mw-headline" id="display">display</span></h1>
<p><span class="standardization_status" title="W3C Recommendation">W3C Recommendation</span>
</p>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>Specifies the type of rendering box used for an element. In HTML, default display property values are based on behaviors listed in the HTML specifications or from the browser or user's default style sheet. The default value in XML is inline.
</p><p>In addition to specifying one of the many different display box types, setting the display value to none lets you turn off (hide) the display of an element. A display element set to none ensures all descendant elements are also hidden. In these situations, the document renders as though the element does not exist in the document tree.
</p>
<h2><span class="mw-headline" id="Overview_table">Overview table</span></h2>
<table class="wikitable overview_table">
<tr>
<th> <a href="/wiki/css/concepts/initial_value" title="css/concepts/initial value"> Initial value</a>
</th>
<td> <code>inline</code>
</td></tr>
<tr>
<th> Applies to
</th>
<td> All elements
</td></tr>
<tr>
<th> <a href="/wiki/css/concepts/inherited" title="css/concepts/inherited"> Inherited</a>
</th>
<td> No
</td></tr>
<tr>
<th> Media
</th>
<td> visual
</td></tr>
<tr>
<th> <a href="/wiki/css/concepts/computed_value" title="css/concepts/computed value"> Computed value</a>
</th>
<td> As specified, except for root element, floated elements, and absolutely positioned elements
</td></tr>
<tr>
<th> Animatable
</th>
<td> No
</td></tr>
<tr>
<th> <a href="/wiki/css/concepts/cssom" title="css/concepts/cssom"> CSS Object Model Property</a>
</th>
<td> <code>display</code>
</td></tr>
<tr>
<th> Percentages
</th>
<td>&#160;???
</td></tr>
</table>
<h2><span class="mw-headline" id="Syntax">Syntax</span></h2>
<h2><span class="mw-headline" id="Values">Values</span></h2>
<div class="css-property">
<dl><dt><b>display-value</b></dt>
<dd><i>A keyword that defines the rendering type to apply to the element. Possible values are <b>none</b>, <b>inline</b>, <b>block</b>, <b>list-item</b>, <b>inline-block</b>, <b>inline-table</b>, <b>table</b>, <b>table-caption</b>, <b>table-cell</b>, <b>table-column</b>, <b>table-column-group</b>, <b>table-footer-group</b>, <b>table-header-group</b>, <b>table-row</b>, <b>table-row-group</b>, <b>flex</b>, <b>inline-flex</b>, <b>grid</b>, <b>inline-grid</b>, and <b>run-in</b>.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>inherit</b></dt>
<dd><i>By default, the CSS display property is not inherited ("Inherited: no"). However, when the inherited property has been specified on an element ("Inherited: Yes"), the element uses the computed value of that property on its parent element. Only the root element of the document gets the initial value given in the property's summary.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>inline</b></dt>
<dd><i>An element set to inline generates one or more inline element boxes.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>none</b></dt>
<dd><i>Turns off the display of an element (it has no effect on layout); all descendant elements also have their display turned off. The document is rendered as though the element did not exist. To render an element box's dimensions, yet have its contents be invisible, set the visibility property to hidden. This is a basic value in CSS 1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>list-item</b></dt>
<dd><i>Generates a block box for the content and a separate list-item. This is a basic value in CSS 1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>inline-block</b></dt>
<dd><i>The element generates a block element box that flows with surrounding content as if it were a single inline box--and behaves like a replaced element. This is a basic value in CSS 2.1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>inline-table</b></dt>
<dd><i>The inline-table value does not have a direct mapping in HTML. It behaves like a &#60;table&#62; HTML element, but as an inline box, rather than a block-level box. Inside the table box is a block-level context. This is a table model value in CSS 2.1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>table</b></dt>
<dd><i>Behaves like the &#60;table&#62; HTML element. It defines a block-level box. This is a table model value in CSS 2.1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>table-caption</b></dt>
<dd><i>Behaves like the &#60;caption&#62; HTML element. This is a table model value in CSS 2.1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>table-cell</b></dt>
<dd><i>Behaves like the &#60;td&#62; HTML element. This is a table model value in CSS 2.1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>table-column</b></dt>
<dd><i>Behaves like the &#60;col&#62; HTML element. This is a table model value in CSS 2.1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>table-column-group</b></dt>
<dd><i>Behaves like the &#60;colgroup&#62; HTML element. This is a table model value in CSS 2.1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>table-footer-group</b></dt>
<dd><i>Behaves like the &#60;tfoot&#62; HTML element. This is a table model value in CSS 2.1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>table-header-group</b></dt>
<dd><i>Behaves like the corresponding &#60;thead&#62; HTML element. This is a table model value in CSS 2.1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>table-row</b></dt>
<dd><i>Behaves like the &#60;tr&#62; HTML element. This is a table model value in CSS 2.1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>table-row-group</b></dt>
<dd><i>Behaves like the &#60;tbody&#62; HTML element. This is a table model value in CSS 2.1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>flex</b></dt>
<dd><i>Behaves like an block element for laying out content in the flexbox model. This is a flexbox model value in CSS3.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>inline-flex</b></dt>
<dd><i>Behaves like an inline element for laying out content in the flexbox model. This is a flexbox model value in CSS3.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>grid</b></dt>
<dd><i>Behaves like a block element for laying out content in the grid model.</i></dd></dl>
<p>Note: At the time of this writing, most modern browsers do not support this property. This is a grid box model value (an experimental tag in CSS 3.0).
</p>
</div>
<div class="css-property">
<dl><dt><b>inline-grid</b></dt>
<dd><i>Behaves like an inline element for laying out content in the grid model. This is a grid box model value (an experimental tag in CSS 3.0).</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>run-in</b></dt>
<dd><i>The behavior depends on the following conditions:</i></dd></dl>
<ul><li> If the run-in box contains a block box, same as block.</li>
<li> If a block box follows the run-in box, the run-in box becomes the first inline box of the block box.</li>
<li> If a inline box follows, the run-in box becomes a block box. .</li></ul>
</div>
<div class="css-property">
<dl><dt><b>block</b></dt>
<dd><i>Generates a block element box. This is a basic value in CSS 1.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>ruby</b></dt>
<dd><i>Specifies that an element defines a <b>ruby</b> structure. This and the following values are from the <a rel="nofollow" class="external text" href="http://go.microsoft.com/fwlink/p/?linkid=203763">CSS3 Ruby Module</a>. This value only applies to the supported ruby elements, <b>rt</b> and <b>ruby</b>.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>ruby-base</b></dt>
<dd><i>Specifies that an element defines a ruby base.  This value only applies to the supported ruby elements, <b>rt</b> and <b>ruby</b>.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>ruby-text</b></dt>
<dd><i>Specifies that an element defines a <b>ruby text</b>.  This value only applies to the supported ruby elements, <b>rt</b> and <b>ruby</b>.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>ruby-base-container</b></dt>
<dd><i>Specifies a container for one or more ruby base elements.  This value only applies to the supported ruby elements, <b>rt</b> and <b>ruby</b>.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>ruby-text-container</b></dt>
<dd><i>Specifies a container for one or more ruby text elements.  This value only applies to the supported ruby elements, <b>rt</b> and <b>ruby</b>.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>-ms-flexbox</b></dt>
<dd><i>Internet Explorer 10. Specifies a block-level flexible box ("flexbox") container. For more information on flexbox containers, see <a href="/wiki/css/flexbox" title="css/flexbox" class="mw-redirect">Flexible Box ("Flexbox") Layout</a>.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>-ms-inline-flexbox</b></dt>
<dd><i>Internet Explorer 10. Specifies an inline-level flexible box ("flexbox") container. For more information on flexbox containers, see <a href="/wiki/css/flexbox" title="css/flexbox" class="mw-redirect">Flexible Box ("Flexbox") Layout</a>.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>-ms-grid</b></dt>
<dd><i>Internet Explorer 10. Specifies a block-level Grid element. For more information on grid layout, see Grid Layout.</i></dd></dl>
</div>
<div class="css-property">
<dl><dt><b>-ms-inline-grid</b></dt>
<dd><i>Internet Explorer 10. Specifies an inline-level Grid element. For more information on grid layout, see Grid Layout.</i></dd></dl>
</div>
<p><br />
</p>
<h2><span class="mw-headline" id="Examples">Examples</span></h2>
<p>Change a <code>span</code>-element from its initial display <code>inline</code> to display as block-level element.
</p>
<div class="example" style="position:relative">
<p><span class="language">HTML</span>
</p>
<pre>
&lt;span&gt;Some example text&lt;/span&gt;
&lt;style&gt;
  span {
    display: block;
  }
&lt;/style&gt;
</pre>
</div>
<p><b>Second example</b>
</p><p>Do not display an element by using <code>display: none;</code>.
</p>
<div class="example" style="position:relative">
<p><span class="language">HTML</span>
</p>
<pre>
&lt;div&gt;Some example text&lt;/div&gt;
&lt;style&gt;
  div {
    display: none;
  }
&lt;/style&gt;
</pre>
</div>
<p><b>Third example</b>
</p><p>Specify the rendering type as block or inline to define how the element will display. Set the element to inherit the rendering values of its parent container:
</p>
<div class="example" style="position:relative">
<p><span class="language">HTML</span>
</p>
<pre>
p.block 
{
display:block; //Sets the element to display in a box model rendering type.
}

p.inline 
{
display:inline; //Sets the element to display inline inside the current element.
}

p.inherit 
{
display:inherit; //Sets the display value to inherit its parent container's display values.
}
</pre>
</div>
<h2><span class="mw-headline" id="Usage">Usage</span></h2>
<p><b>Basic values in CSS 1</b>
</p>
<ul><li>none</li>
<li>inline</li>
<li>block</li>
<li>list-item</li></ul>
<p><b>Extended values in CSS 2.1</b>
</p>
<ul><li>inline-block</li></ul>
<p><b>Table model values in CSS 2.1</b>
</p>
<ul><li>inline-table</li>
<li>table</li>
<li>table-caption</li>
<li>table-cell</li>
<li>table-column</li>
<li>table-column-group</li>
<li>table-footer-group</li>
<li>table-header-group</li>
<li>table-row</li>
<li>table-row-group</li></ul>
<p><b>Flexbox model values in CSS3</b>
</p>
<ul><li>flex</li>
<li>inline-flex</li></ul>
<p><b>Grid box model values (experimental in CSS3)</b>
</p>
<ul><li>grid</li>
<li>inline-grid</li></ul>
<p><b>Experimental values</b>
</p>
<ul><li>run-in</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Related_specifications">Related specifications</span></h2>
<table class="wikitable relatedspecs">

<tr>
<th> Specification </th>
<th> Status </th>
<th> Related Changes
</th></tr>
<tr>
<td><a rel="nofollow" class="external text" href="http://dev.w3.org/csswg/css3-box/#display">CSS Basic Box Model</a> </td>
<td> Working Draft </td>
<td>
</td></tr>
<tr>
<td><a rel="nofollow" class="external text" href="http://dev.w3.org/csswg/css3-grid-layout/#grid-declaration">CSS Grid Layout</a> </td>
<td> Working Draft </td>
<td>
</td></tr>
<tr>
<td><a rel="nofollow" class="external text" href="http://dev.w3.org/csswg/css3-flexbox/#flex-containers">CSS Flexible Box Layout Module</a> </td>
<td> Candidate Recommendation </td>
<td>
</td></tr>
<tr>
<td><a rel="nofollow" class="external text" href="http://www.w3.org/TR/CSS2/visuren.html#display-prop">CSS Level 2 (Revision 1)</a> </td>
<td> Recommendation </td>
<td>
</td></tr>
<tr>
<td><a rel="nofollow" class="external text" href="http://www.w3.org/TR/CSS1/#display">CSS Level 1</a> </td>
<td> Recommendation </td>
<td>
</td></tr></table>
<h2><span class="mw-headline" id="See_also">See also</span></h2>
<h3><span class="mw-headline" id="Related_articles">Related articles</span></h3>
<h4><span class="mw-headline" id="CSS_Font">CSS Font</span></h4>
<ul><li> <a href="/wiki/css/properties/font-family" title="css/properties/font-family">font-family</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-kerning" title="css/properties/font-kerning">font-kerning</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-language-override" title="css/properties/font-language-override">font-language-override</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-size" title="css/properties/font-size">font-size</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-size-adjust" title="css/properties/font-size-adjust">font-size-adjust</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-style" title="css/properties/font-style">font-style</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-synthesis" title="css/properties/font-synthesis">font-synthesis</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-variant" title="css/properties/font-variant">font-variant</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/kerning-mode" title="css/properties/kerning-mode">kerning-mode</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/kerning-pair-threshold" title="css/properties/kerning-pair-threshold">kerning-pair-threshold</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/text-rendering" title="css/properties/text-rendering">text-rendering</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/text-underline" title="css/properties/text-underline">text-underline</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/user-modify" title="css/properties/user-modify">user-modify</a></li></ul>
<h4><span class="mw-headline" id="Fonts">Fonts</span></h4>
<ul><li> <a href="/wiki/css/atrules/@font-face" title="css/atrules/@font-face">@font-face</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/fonts" title="css/fonts">Font related properties</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/fonts/font-variant" title="css/fonts/font-variant">font-variant</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font" title="css/properties/font">font</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-family" title="css/properties/font-family">font-family</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-feature-settings" title="css/properties/font-feature-settings">font-feature-settings</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-kerning" title="css/properties/font-kerning">font-kerning</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-language-override" title="css/properties/font-language-override">font-language-override</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-size" title="css/properties/font-size">font-size</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-size-adjust" title="css/properties/font-size-adjust">font-size-adjust</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-stretch" title="css/properties/font-stretch">font-stretch</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-style" title="css/properties/font-style">font-style</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-synthesis" title="css/properties/font-synthesis">font-synthesis</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-variant" title="css/properties/font-variant">font-variant</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/max-font-size" title="css/properties/max-font-size">max-font-size</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/min-font-size" title="css/properties/min-font-size">min-font-size</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/user-modify" title="css/properties/user-modify">user-modify</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/attributes/size" title="html/attributes/size">size</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/font" title="html/elements/font">font</a></li></ul>
<h4><span class="mw-headline" id="Text">Text</span></h4>
<ul><li> <a href="/wiki/css/properties/block-progression" title="css/properties/block-progression">block-progression</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-language-override" title="css/properties/font-language-override">font-language-override</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-size" title="css/properties/font-size">font-size</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/font-synthesis" title="css/properties/font-synthesis">font-synthesis</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/hanging-punctuation" title="css/properties/hanging-punctuation">hanging-punctuation</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/hyphenate-limit-chars" title="css/properties/hyphenate-limit-chars">hyphenate-limit-chars</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/hyphenate-limit-lines" title="css/properties/hyphenate-limit-lines">hyphenate-limit-lines</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/hyphenate-limit-zone" title="css/properties/hyphenate-limit-zone">hyphenate-limit-zone</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/hyphens" title="css/properties/hyphens">hyphens</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/ime-mode" title="css/properties/ime-mode">ime-mode</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/layout-flow" title="css/properties/layout-flow">layout-flow</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/layout-grid" title="css/properties/layout-grid">layout-grid</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/layout-grid-char" title="css/properties/layout-grid-char">layout-grid-char</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/layout-grid-line" title="css/properties/layout-grid-line">layout-grid-line</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/layout-grid-mode" title="css/properties/layout-grid-mode">layout-grid-mode</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/layout-grid-type" title="css/properties/layout-grid-type">layout-grid-type</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/letter-spacing" title="css/properties/letter-spacing">letter-spacing</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/line-break" title="css/properties/line-break">line-break</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/max-font-size" title="css/properties/max-font-size">max-font-size</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/min-font-size" title="css/properties/min-font-size">min-font-size</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/text-overflow-ellipsis" title="css/properties/text-overflow-ellipsis">text-overflow-ellipsis</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/text-overflow-mode" title="css/properties/text-overflow-mode">text-overflow-mode</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/text-rendering" title="css/properties/text-rendering">text-rendering</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/text-underline-position" title="css/properties/text-underline-position">text-underline-position</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/text-underline-style" title="css/properties/text-underline-style">text-underline-style</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/text-underline-width" title="css/properties/text-underline-width">text-underline-width</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/user-input" title="css/properties/user-input">user-input</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/properties/user-modify" title="css/properties/user-modify">user-modify</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/css/text" title="css/text">Text</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/attributes/size" title="html/attributes/size">size</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/b" title="html/elements/b">b</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/b/ja" title="html/elements/b/ja">b</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/br" title="html/elements/br">br</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/caption" title="html/elements/caption">caption</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/cite" title="html/elements/cite">cite</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/code" title="html/elements/code">code</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/del" title="html/elements/del">del</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/dfn" title="html/elements/dfn">dfn</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/em" title="html/elements/em">em</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/font" title="html/elements/font">font</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/hr" title="html/elements/hr">hr</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/i" title="html/elements/i">i</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/ins" title="html/elements/ins">ins</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/kbd" title="html/elements/kbd">kbd</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/mark" title="html/elements/mark">mark</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/samp" title="html/elements/samp">samp</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/html/elements/strong" title="html/elements/strong">strong</a></li></ul>
<p><br />
</p>
<ul><li> <a href="/wiki/tutorials/canvas_texteffects" title="tutorials/canvas texteffects">Achieving typographic effects with the canvas tag</a></li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="External_resources">External resources</span></h3>
<ul><li> Quirksmode: <a rel="nofollow" class="external text" href="http://www.quirksmode.org/css/display.html">The display property</a></li>
<li> Mozilla Developer Network: <a rel="nofollow" class="external text" href="https://developer.mozilla.org/en-US/docs/CSS/display">CSS Reference: The display property</a></li></ul>
<div class="attribution">
<p><br />
</p><p><br />
</p>
</div>
<h2><span class="mw-headline" id="Notes">Notes</span></h2>
<h3><span class="mw-headline" id="Remarks">Remarks</span></h3>
<p>To render an element box's dimensions, yet have its contents be invisible, see the <a href="/wiki/css/properties/visibility" title="css/properties/visibility">visibility</a> property.
</p><p>All visible HTML <b>div</b> object is a block element, and a <b>span</b> object is an inline element. Block elements typically start a new line and can contain other block elements and inline elements. Inline elements do not typically start a new line and can contain other inline elements or data. Changing the values for the <b>display</b> property affects the layout of the surrounding content by:
</p>
<ul><li>Adding a new line after the element with the value <b>block</b>.</li>
<li>Removing a line from the element with the value <b>inline</b>.</li>
<li>Hiding the data for the element with the value <b>none</b>.</li></ul>
<p>In contrast to the <a href="/wiki/css/properties/visibility" title="css/properties/visibility">visibility</a> property, <code>display: none</code> reserves no space for the object on the screen.
The <code>table-header-group</code> and <code>table-footer-group</code> values can be used to specify that the contents of the <code>thead</code> and <code>tfoot</code> elements are displayed on every page for a table that spans multiple pages.
</p><p>You can use <code>inline-block</code> to give an object a layout without specifying the object's height or width.
</p><p>The Cascading Style Sheets (CSS) table display model does not require explicit elements to correspond with the HTML tags. For example, an element styled as <code>display: table-cell</code> does not need to be contained within a block that is styled <code>display: table-row</code> to be styled correctly. Implicit table elements are created as necessary in an attempt to make the document valid. Contrast this behavior to the traditional HTML table model, where table elements are implicitly closed early to avoid unexpected nesting.
</p>
<h3><span class="mw-headline" id="Rendering_for_floating_or_absolute_positioned_elements">Rendering for floating or absolute positioned elements</span></h3>
<table>
<tr>
<th> Specified value </th>
<th> Computed value
</th></tr>
<tr>
<td> inline-table </td>
<td> table
</td></tr>
<tr>
<td> inline, run-in, table-row-group, table-column, table-column-group, table-header-group, table-footer-group, table-row, table-cell, table-caption, inline-block </td>
<td> block
</td></tr>
<tr>
<td> others </td>
<td> same as specified
</td></tr></table>
<p><br />
</p>
<!-- 
NewPP limit report
CPU time usage: 0.511 seconds
Real time usage: 0.594 seconds
Preprocessor visited node count: 2304/1000000
Preprocessor generated node count: 8940/1000000
Post‐expand include size: 56751/2097152 bytes
Template argument size: 34733/2097152 bytes
Highest expansion depth: 7/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%  475.170      1 - -total
 48.03%  228.227      1 - Template:See_Also_Section
 31.80%  151.095      1 - Template:CSS_Property
 24.08%  114.418     31 - Template:CSS_Property_Value
 15.48%   73.576     80 - Template:See_Also_Item
  4.04%   19.194      1 - Template:Examples_Section
  2.90%   13.787      3 - Template:Single_Example
  2.65%   12.569      1 - Template:Page_Title
  2.39%   11.367      1 - Template:Related_Specifications_Section
  2.03%    9.653      1 - Template:Flags
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:7379-0!*!0!!*!*!*!esi=1 and timestamp 20150731111058 and revision id 31535
 -->
