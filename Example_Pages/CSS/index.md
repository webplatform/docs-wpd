'''This is a temporary page to pull together an example of what the ideal end state will be. It includes some content from MDN that is not compatible with the WPD license, and should be removed soon.'''

==Summary==
The <code>font-size</code> CSS properties specifies the size of the font used for text in the object. Setting the font size may, in turn, change the size of other items, since it is used to compute the value of <code>em</code> and <code>ex</code> length units.

==Overview table==
{| class="wikitable"
|-
| [[CSS/Concepts/Initial-Value | Initial Value]] || <code>medium</code>
|-
| Applies to || All elements
|-
| [[CSS/concepts/Inherited | Inherited]] || Yes
|-
| Percentages || Relative to parent element's font size
|-
| Media || <code>[[CSS/media/visual | visual]]</code>
|-
| [[CSS/concepts/Computed-value | Computed value]] || Absolute length
|}

==Syntax==
font-size: <absolute-size> | <relative-size> | <length> | <percentage> 

where <values> are defined below.

NB: This section is automatically generated from the Values section below.

==Values==
'''absolute-size'''

Indicate predefined font sizes. Named font sizes scale according to the user's font setting preferences. Possible values include the following: ''xx-small, x-small, small, medium, large, x-large, xx-large''. 

'''relative-size''' 

Larger or smaller than the parent element's font size, by roughly the ratio used to separate the absolute-size keywords,
relative to the font size of the parent object. Possible values include the following: ''larger, smaller''.

'''length''' 

A positive length, followed by an absolute units designator (cm, mm, in, pt, or pc) or a relative units designator (em, ex, or px). When the units are specified in em or ex, the size is defined relative to the size of the font on the parent element of the element in question. For example, 0.5em is half the font size of the parent of the current element.

'''percentage''' 

A positive percentage of the parent element's font size, followed by a percent (%). The value is a percentage of the parent object's font size.

==Possible approaches==

There are several ways to specify the font size, with keywords or numerical values for pixels or ems. Choose the appropriate method based on the needs for the particular web page.

===Keywords===

Keywords are a good way to set the size of fonts on the web. By setting a keyword font size on the body element, you can set relative font-sizing everywhere else on the page, giving you the ability to easily scale the font up or down on the entire page accordingly.
Pixels

Setting the font size in pixel values (<code>px</code>) is a good choice when you need pixel accuracy. A <code>px</code> value is static. This is an OS-independent and cross-browser way of literally telling the browsers to render the letters at exactly the number of pixels in height that you specified. The results may vary slightly across browsers, as they may use different algorithms to achieve a similar effect.

Font sizing settings can also be used in combination. For example, if a parent element is set to <code>16px</code> and its child element is set to <code>larger</code>, the child element displays larger than the parent element in the page.

<div style="background: none repeat scroll 0 0 #FAF9E2;
    border-color: #DDDAAA;
    border-style: solid;
    border-width: 1px 0;
    color: #5D5636;
    line-height: 1.5em;
    margin-bottom: 1.286em;
    padding: 0.75em 15px;">
Note: Defining font sizes in pixel is ''not accessible'', because the user cannot change the font size from the browser. (For example, users with limited vision may wish to set the font size much larger than the size chosen by a web designer.) Therefore, avoid using pixels for font sizes if you wish to create an inclusive design.
</div>

===Ems===

Another way of setting the font size is with <code>em</code> values. The size of an <code>em</code> value is dynamic. When defining the <code>font-size</code> property, an <code>em</code> is equal to the size of the font that applies to the parent of the element in question. If you haven't set the font size anywhere on the page, then it is the browser default, which is probably 16px. So, by default 1em = 16px, and 2em = 32px. If you set a font-size of 20px on the body element, then 1em = 20px and 2em = 40px. Note that the value 2 is essentially a multiplier of the current <code>em</code> size.

In order to calculate the <code>em</code> equivalent for any pixel value required, you can use this formula:

<syntaxhighlight lang="css">
em = desired element pixel value / parent element font-size in pixels
</syntaxhighlight>

For example, suppose the font-size of the body of the page is set to 1em, with the browser standard of 1em = 16px; if the font-size you want is 12px, then you should specify 0.75em (because 12/16 = 0.75). Similarly, if you want a font size of 10px, then specify 0.625em (10/16 = 0.625); for 22px, specify 1.375em (22/16).

A popular technique to use throughout the document is to set the the font-size of the body to 62.5% (that is 62.5% of the default of 16px), which equates to 10px, or 0.625em. Now you can set the font-size for any elements using em units, with an easy-to-remember conversion, by dividing the px value by 10. This way 6px = 0.6em, 8px = 0.8em, 12px = 1.2em, 14px = 1.4em, 16px = 1.6em. For example:

<syntaxhighlight lang="css">
body {
  font-size: 62.5%; /* font-size 1em = 10px */
}
p {
  font-size: 1.6em; /* 1.6em = 16px */
}
</syntaxhighlight>

The em is a very useful unit in CSS, since it can adapt automatically to the font that the reader chooses to use.

==Examples==
[[CSS/examples | View live examples]]
<syntaxhighlight>
/* Set paragraph text to be very large. */
p { font-size: xx-large }
 
/* Set h1 (level 1 heading) text to be 2.5 times the size
 * of the text around it. */
h1 { font-size: 250% }
 
/* Sets text enclosed within span tag to be 16px */
span { font-size: 16px; }
</syntaxhighlight>

==Notes==
Negative values are not allowed. 

The ''em'' and ''ex'' units on the font-size property are relative to the parent element's font size (unlike all other properties, where they're relative to the font size on the element). This means em units and percentages do the same thing for font-size.

==Specifications==
{| class="wikitable"
|-
! Specification !! Status !! Notes
|-
| [http://dev.w3.org/csswg/css3-fonts/#font-size-prop CSS Fonts Module Level 3] || Working Draft || No change
|-
| [http://dev.w3.org/csswg/css3-transitions/#animatable-css CSS Transitions] || Working Draft || Defines <code>font-size</code> as animatable
|-
| [http://www.w3.org/TR/CSS2/fonts.html#propdef-font-size CSS 2 (Revision 1)] || Recommendation || No change
|-
| [http://www.w3.org/TR/CSS1/#font-size CSS Level 1] || ||
|}

==Browser Compatibility==

===Desktop===
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
        <td>1.0</td>
        <td>{{ CompatGeckoDesktop("1") }}</td>
        <td>5.5</td>
        <td>7.0</td>
        <td>1.0</td>
      </tr>
  </table>
</div>
===Mobile===
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
        <td>{{ CompatGeckoMobile("1") }}</td>
        <td>6.0</td>
        <td>6.0</td>
        <td>1.0</td>
      </tr>
  </table>
</div>

===Microsoft Internet Explorer===
As of Microsoft Internet Explorer 6, when you use the <code>!DOCTYPE</code> declaration to specify standards-compliant mode, the default value for this property is <code>medium</code>, not <code>small</code>.

Possible length values specified in a relative measurement, using the height of the element's font (em) or the height of the letter "x" (ex), are supported in Microsoft Internet Explorer 4.0 and later.

==See Also==
===Related CSS Properties===
* <code>[[CSS/properties/font | font]]</code>
* <code>[[CSS/properties/font-family | font-family]]</code>
* <code>[[CSS/properties/font-size | font-size]]</code>
* <code>[[CSS/properties/font-size-adjust | font-size-adjust]]</code>
* <code>[[CSS/properties/font-stretch | font-stretch]]</code>
* <code>[[CSS/properties/font-style | font-style]]</code>
* <code>[[CSS/properties/font-variant | font-variant]]</code>
* <code>[[CSS/properties/font-weight | font-weight]]</code>

==Related CSS At Rules==
* <code>[[CSS/atrules/@font-face | @font-face]]</code>

==Related DOM Interfaces==
* <code>[[DOM/element/CSSStyleDeclaration | CSSStyleDeclaration]]</code>

==Related DOM properties==
* <code>[[DOM/element/properties/currentStyle | element.currentStyle]]</code>
* <code>[[DOM/element/properties/defaults | element.defaults]]</code> ''IE Only''

<details>
	<summary>This article contains content originally from external sources, including ones licensed under the CC-BY-SA license.</summary>
	<div>
		Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network:
<a href="http://developer.mozilla.org/foo" target="_blank">Foo</a>
	</div>
	<div>
		Portions of this content come from Foo.org: <a href="http://foo.org/baz" target="_blank">Baz</a>
	</div>
</details>