---
title: WPD:Example Pages/CSS
---
<p><b>This is a temporary page to pull together an example of what the ideal end state will be. It includes some content from MDN that is not compatible with the WPD license, and should be removed soon.</b>
</p><p>Based on: <a rel="nofollow" class="external free" href="https://developer.mozilla.org/en-US/docs/CSS/font-size">https://developer.mozilla.org/en-US/docs/CSS/font-size</a> and <a rel="nofollow" class="external free" href="http://msdn.microsoft.com/en-us/library/ie/ms530759(v=vs.85).aspx">http://msdn.microsoft.com/en-us/library/ie/ms530759(v=vs.85).aspx</a>
</p>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>The <code>font-size</code> CSS properties specifies the size of the font used for text in the object. Setting the font size may, in turn, change the size of other items, since it is used to compute the value of <code>em</code> and <code>ex</code> length units.
</p><p><b>Implementation Note</b>: use property of type text so we can pull this out elsewhere
</p>
<h2><span class="mw-headline" id="Overview_table">Overview table</span></h2>
<table class="wikitable">

<tr>
<td> <a href="/w/index.php?title=CSS/Concepts/Initial-Value&amp;action=edit&amp;redlink=1" class="new" title="CSS/Concepts/Initial-Value (page does not exist)"> Initial Value</a> </td>
<td> <code>medium</code>
</td></tr>
<tr>
<td> Applies to </td>
<td> All elements
</td></tr>
<tr>
<td> <a href="/w/index.php?title=CSS/concepts/Inherited&amp;action=edit&amp;redlink=1" class="new" title="CSS/concepts/Inherited (page does not exist)"> Inherited</a> </td>
<td> Yes
</td></tr>
<tr>
<td> Percentages </td>
<td> Relative to parent element's font size
</td></tr>
<tr>
<td> Media </td>
<td> <code><a href="/w/index.php?title=CSS/media/visual&amp;action=edit&amp;redlink=1" class="new" title="CSS/media/visual (page does not exist)"> visual</a></code>
</td></tr>
<tr>
<td> <a href="/w/index.php?title=CSS/concepts/Computed-value&amp;action=edit&amp;redlink=1" class="new" title="CSS/concepts/Computed-value (page does not exist)"> Computed value</a> </td>
<td> Absolute length
</td></tr>
<tr>
<td> <a href="/w/index.php?title=CSS/concepts/CSSOM&amp;action=edit&amp;redlink=1" class="new" title="CSS/concepts/CSSOM (page does not exist)"> CSS Object Model Property</a> </td>
<td> <code>fontSize</code>
</td></tr>
<tr>
<td> Animatable </td>
<td> No
</td></tr></table>
<h2><span class="mw-headline" id="Syntax">Syntax</span></h2>
<pre><code>font-size:  xx-small | x-small | small | medium | large | x-large | xx-large</code>
<code>font-size: smaller | larger</code>
<code>font-size: </code><em>&lt;length&gt;</em> <code>|</code> <em>&lt;percentage&gt; </em>
</pre>
<p><i><b>Implementation Note:</b> Each keyword above should be automatically generated and link to the relevant part of the Values section below. Have a template for this block based on a query to properties that are set in values section to create it.</i>
</p>
<h2><span class="mw-headline" id="Values">Values</span></h2>
<p><i><b>Implementation Note:</b> We need to be able to differentiate between literal values, data types and placeholders.</i> 
</p>
<dl><dt><code>xx-small</code>, <code>x-small</code>, <code>small</code>, <code>medium</code>, <code>large</code>, <code>x-large</code>, <code>xx-large</code></dt>
<dd> Indicate predefined abosolute font sizes. Named font sizes scale according to the user's font setting preferences.  </dd></dl>
<dl><dt><code>larger</code>, <code>smaller</code></dt>
<dd> Relatively larger or smaller than the parent element's font size, by roughly the ratio used to separate the absolute-size keywords relative to the font size of the parent object. </dd></dl>
<dl><dt><a href="/w/index.php?title=CSS/datatypes/length&amp;action=edit&amp;redlink=1" class="new" title="CSS/datatypes/length (page does not exist)">&lt;length&gt;</a></dt>
<dd> A positive length, followed by an absolute units designator (<code>cm</code>, <code>mm</code>, <code>in</code>, <code>pt</code>, or <code>pc</code>) or a relative units designator (<code>em</code>, <code>ex</code>, or <code>px</code>). When the units are specified in <code>em</code> or <code>ex</code>, the size is defined relative to the size of the font on the parent element of the element in question. For example, <code>0.5em</code> is half the font size of the parent of the current element. Negative values are not allowed. </dd></dl>
<dl><dt><i>percentage</i></dt>
<dd> A positive percentage of the parent element's font size, followed by a percent symbol (%). The value is a percentage of the parent object's font size. Negative values are not allowed.</dd></dl>
<h2><span class="mw-headline" id="Examples">Examples</span></h2>
<p><a href="/w/index.php?title=CSS/examples&amp;action=edit&amp;redlink=1" class="new" title="CSS/examples (page does not exist)"> View live examples</a>
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">/* LANGUAGE-TAG: CSS */
/* Set paragraph text to be very large. */
p { font-size: xx-large }
&#160;
/* Set h1 (level 1 heading) text to be 2.5 times the size
 * of the text around it. */
h1 { font-size: 250% }
&#160;
/* Sets text enclosed within span tag to be 16px */
span { font-size: 16px; }</pre></div></div>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">//LANGUAGE-TAG: JavaScript
var ele = document.getElementyById(&quot;my-paragraph&quot;);
ele.style.fontSize = &quot;small&quot;;</pre></div></div>
<h2><span class="mw-headline" id="Usage">Usage</span></h2>
<p>There are several ways to specify the font size, with keywords or numerical values for pixels or ems. Choose the appropriate method based on the needs for the particular web page.
</p>
<h3><span class="mw-headline" id="Keywords">Keywords</span></h3>
<p>Keywords are a good way to set the size of fonts on the web. By setting a keyword font size on the body element, you can set relative font-sizing everywhere else on the page, giving you the ability to easily scale the font up or down on the entire page accordingly.
Pixels
</p><p>Setting the font size in pixel values (<code>px</code>) is a good choice when you need pixel accuracy. A <code>px</code> value is static. This is an OS-independent and cross-browser way of literally telling the browsers to render the letters at exactly the number of pixels in height that you specified. The results may vary slightly across browsers, as they may use different algorithms to achieve a similar effect.
</p><p>Font sizing settings can also be used in combination. For example, if a parent element is set to <code>16px</code> and its child element is set to <code>larger</code>, the child element displays larger than the parent element in the page.
</p>
<div style="background: none repeat scroll 0 0 #FAF9E2; border-color: #DDDAAA; border-style: solid; border-width: 1px 0; color: #5D5636; line-height: 1.5em; margin-bottom: 1.286em; padding: 0.75em 15px;">
<p>Note: Defining font sizes in pixel is <i>not accessible</i>, because the user cannot change the font size from the browser. (For example, users with limited vision may wish to set the font size much larger than the size chosen by a web designer.) Therefore, avoid using pixels for font sizes if you wish to create an inclusive design.
</p>
</div>
<h3><span class="mw-headline" id="Ems">Ems</span></h3>
<p>Another way of setting the font size is with <code>em</code> values. The size of an <code>em</code> value is dynamic. When defining the <code>font-size</code> property, an <code>em</code> is equal to the size of the font that applies to the parent of the element in question. If you haven't set the font size anywhere on the page, then it is the browser default, which is probably 16px. So, by default 1em = 16px, and 2em = 32px. If you set a font-size of 20px on the body element, then 1em = 20px and 2em = 40px. Note that the value 2 is essentially a multiplier of the current <code>em</code> size.
</p><p>In order to calculate the <code>em</code> equivalent for any pixel value required, you can use this formula:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="css source-css"><pre class="de1">em <span class="sy0">=</span> desired <span class="kw2">element</span> pixel <span class="kw5">value</span> / parent <span class="kw2">element</span> <span class="kw1">font-size</span> in pixels</pre></div></div>
<p>For example, suppose the font-size of the body of the page is set to 1em, with the browser standard of 1em = 16px; if the font-size you want is 12px, then you should specify 0.75em (because 12/16 = 0.75). Similarly, if you want a font size of 10px, then specify 0.625em (10/16 = 0.625); for 22px, specify 1.375em (22/16).
</p><p>A popular technique to use throughout the document is to set the the font-size of the body to 62.5% (that is 62.5% of the default of 16px), which equates to 10px, or 0.625em. Now you can set the font-size for any elements using em units, with an easy-to-remember conversion, by dividing the px value by 10. This way 6px = 0.6em, 8px = 0.8em, 12px = 1.2em, 14px = 1.4em, 16px = 1.6em. For example:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="css source-css"><pre class="de1">body <span class="br0">&#123;</span>
  <span class="kw1">font-size</span><span class="sy0">:</span> <span class="re3">62.5%</span><span class="sy0">;</span> <span class="coMULTI">/* font-size 1em = 10px */</span>
<span class="br0">&#125;</span>
p <span class="br0">&#123;</span>
  <span class="kw1">font-size</span><span class="sy0">:</span> <span class="re3">1.6em</span><span class="sy0">;</span> <span class="coMULTI">/* 1.6em = 16px */</span>
<span class="br0">&#125;</span></pre></div></div>
<p>The em is a very useful unit in CSS, since it can adapt automatically to the font that the reader chooses to use.
</p>
<h2><span class="mw-headline" id="Notes">Notes</span></h2>
<p>The <code>em</code> and <code>ex</code> units on the font-size property are relative to the parent element's font size (unlike all other properties, where they're relative to the font size on the element). This means em units and percentages do the same thing for font-size.
</p>
<h2><span class="mw-headline" id="Specifications">Specifications</span></h2>
<table class="wikitable">

<tr>
<th> Specification </th>
<th> Status </th>
<th> Relevant changes
</th></tr>
<tr>
<td> <a rel="nofollow" class="external text" href="http://dev.w3.org/csswg/css3-fonts/#font-size-prop">CSS Fonts Module Level 3</a> </td>
<td> Working Draft </td>
<td> No change
</td></tr>
<tr>
<td> <a rel="nofollow" class="external text" href="http://dev.w3.org/csswg/css3-transitions/#animatable-css">CSS Transitions</a> </td>
<td> Working Draft </td>
<td> Defines <code>font-size</code> as animatable
</td></tr>
<tr>
<td> <a rel="nofollow" class="external text" href="http://www.w3.org/TR/CSS2/fonts.html#propdef-font-size">CSS 2 (Revision 1)</a> </td>
<td> Recommendation </td>
<td> No change
</td></tr>
<tr>
<td> <a rel="nofollow" class="external text" href="http://www.w3.org/TR/CSS1/#font-size">CSS Level 1</a> </td>
<td> Recommendation </td>
<td> Original specification
</td></tr></table>
<h2><span class="mw-headline" id="Browser_Compatibility">Browser Compatibility</span></h2>
<h3><span class="mw-headline" id="Desktop">Desktop</span></h3>
<div id="compat-desktop">
  <table class="compat-table">
       <tr>
        <th>Feature</th>
        <th>Chrome</th>
        <th>Firefox (Gecko)</th>
        <th>Internet Explorer</th>
        <th>Opera</th>
        <th>Safari</th>
      </tr>
      <tr>
        <td>Basic support</td>
        <td>5.0<br />4.0 <span style="border:1px solid black; padding:2px">-webkit</span></td>
        <td><a href="/w/index.php?title=Template:CompatGeckoDesktop(%221%22)&amp;action=edit&amp;redlink=1" class="new" title="Template:CompatGeckoDesktop(&quot;1&quot;) (page does not exist)">Template:CompatGeckoDesktop("1")</a></td>
        <td>5.5</td>
        <td>7.0</td>
        <td>1.0</td>
      </tr>
  </table>
</div>
<p><i><b>Implementation Note:</b> The prefix tag (here, a fake value just to show it off) would be a link to the concept of prefixes.</i>
</p>
<h3><span class="mw-headline" id="Mobile">Mobile</span></h3>
<div id="compat-mobile">
  <table class="compat-table">
      <tr>
        <th>Feature</th>
        <th>Android</th>
        <th>Firefox Mobile (Gecko)</th>
        <th>IE Phone</th>
        <th>Opera Mobile</th>
        <th>Safari Mobile</th>
      </tr>
      <tr>
        <td>Basic support</td>
        <td>1.0</td>
        <td><a href="/w/index.php?title=Template:CompatGeckoMobile(%221%22)&amp;action=edit&amp;redlink=1" class="new" title="Template:CompatGeckoMobile(&quot;1&quot;) (page does not exist)">Template:CompatGeckoMobile("1")</a></td>
        <td>6.0</td>
        <td>6.0</td>
        <td>1.0</td>
      </tr>
  </table>
</div>
<h3><span class="mw-headline" id="Compatibility_Notes">Compatibility Notes</span></h3>
<table class="wikitable">
<tr>
<th> Browser
</th>
<th> Version
</th>
<th> Note
</th></tr>
<tr>
<td> Internet Explorer
</td>
<td> 6+
</td>
<td>When using the <code>!DOCTYPE</code> declaration to specify standards-compliant mode, the default value for this property is <code>medium</code>, not <code>small</code>.
</td></tr>
<tr>
<td> Internet Explorer
</td>
<td> 4+
</td>
<td> Possible length values specified in a relative measurement, using the height of the element's font (em) or the height of the letter "x" (ex)
</td></tr></table>
<h2><span class="mw-headline" id="See_Also">See Also</span></h2>
<h3><span class="mw-headline" id="Related_CSS_Properties">Related CSS Properties</span></h3>
<ul><li> <code><a href="/w/index.php?title=CSS/properties/font&amp;action=edit&amp;redlink=1" class="new" title="CSS/properties/font (page does not exist)"> font</a></code></li>
<li> <code><a href="/w/index.php?title=CSS/properties/font-family&amp;action=edit&amp;redlink=1" class="new" title="CSS/properties/font-family (page does not exist)"> font-family</a></code></li>
<li> <code><a href="/w/index.php?title=CSS/properties/font-size&amp;action=edit&amp;redlink=1" class="new" title="CSS/properties/font-size (page does not exist)"> font-size</a></code></li>
<li> <code><a href="/w/index.php?title=CSS/properties/font-size-adjust&amp;action=edit&amp;redlink=1" class="new" title="CSS/properties/font-size-adjust (page does not exist)"> font-size-adjust</a></code></li>
<li> <code><a href="/w/index.php?title=CSS/properties/font-stretch&amp;action=edit&amp;redlink=1" class="new" title="CSS/properties/font-stretch (page does not exist)"> font-stretch</a></code></li>
<li> <code><a href="/w/index.php?title=CSS/properties/font-style&amp;action=edit&amp;redlink=1" class="new" title="CSS/properties/font-style (page does not exist)"> font-style</a></code></li>
<li> <code><a href="/w/index.php?title=CSS/properties/font-variant&amp;action=edit&amp;redlink=1" class="new" title="CSS/properties/font-variant (page does not exist)"> font-variant</a></code></li>
<li> <code><a href="/w/index.php?title=CSS/properties/font-weight&amp;action=edit&amp;redlink=1" class="new" title="CSS/properties/font-weight (page does not exist)"> font-weight</a></code></li></ul>
<h3><span class="mw-headline" id="Related_CSS_At_Rules">Related CSS At Rules</span></h3>
<ul><li> <code><a href="/w/index.php?title=CSS/atrules/@font-face&amp;action=edit&amp;redlink=1" class="new" title="CSS/atrules/@font-face (page does not exist)"> @font-face</a></code></li></ul>
<h3><span class="mw-headline" id="Related_DOM_Interfaces">Related DOM Interfaces</span></h3>
<ul><li> <code><a href="/w/index.php?title=DOM/element/CSSStyleDeclaration&amp;action=edit&amp;redlink=1" class="new" title="DOM/element/CSSStyleDeclaration (page does not exist)"> CSSStyleDeclaration</a></code></li></ul>
<h3><span class="mw-headline" id="Related_DOM_properties">Related DOM properties</span></h3>
<ul><li> <code><a href="/w/index.php?title=DOM/element/properties/currentStyle&amp;action=edit&amp;redlink=1" class="new" title="DOM/element/properties/currentStyle (page does not exist)"> element.currentStyle</a></code></li>
<li> <code><a href="/w/index.php?title=DOM/element/properties/defaults&amp;action=edit&amp;redlink=1" class="new" title="DOM/element/properties/defaults (page does not exist)"> element.defaults</a></code> <i>IE Only</i></li></ul>
<p>&lt;details&gt;
	&lt;summary&gt;This article contains content originally from external sources, including ones licensed under the CC-BY-SA license.&lt;/summary&gt;
</p>
	<div>
<p>		Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network:
&lt;a href="<a rel="nofollow" class="external free" href="http://developer.mozilla.org/foo">http://developer.mozilla.org/foo</a>" target="_blank"&gt;Foo&lt;/a&gt;
</p>
	</div>
	<div>
<p>		Portions of this content come from Foo.org: &lt;a href="<a rel="nofollow" class="external free" href="http://foo.org/baz">http://foo.org/baz</a>" target="_blank"&gt;Baz&lt;/a&gt;
</p>
	</div>
<p>&lt;/details&gt;
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:195-0!*!0!!*!*!*!esi=1 and timestamp 20150731181434 and revision id 794
 -->
