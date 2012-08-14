'''This is a temporary page to pull together an example of what the ideal end state will be. It includes some content from MDN that is not compatible with the WPD license, and should be removed soon.'''

==Summary==
Specifies the size of the font used for text in the object. Setting the font size may, in turn, change the size of other items, since it is used to compute the value of ''em'' and ''ex'' length units.

==Overview table==
{| class="wikitable"
|-
| [[CSS/Concepts/Initial-Value | Initial Value]] || Medium
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

where values are defined below.

==Values==
'''absolute-size'''
Set of keywords that indicate predefined font sizes. Named font sizes scale according to the user's font setting preferences. Possible values include the following: ''xx-small, x-small, small, medium, large, x-large, xx-large''. 

'''relative-size''' 
Set of keywords that are interpreted as relative to the font size of the parent object.

'''length''' 
Floating-point number, followed by an absolute units designator (cm, mm, in, pt, or pc) or a relative units designator (em, ex, or px). For more information about the supported length units, see the CSS Values and Units Reference. 

'''percentage''' 
Integer, followed by a percent (%). The value is a percentage of the parent object's font size. In Internet Explorer 3.0, the value is calculated as a percentage of the default font size.

==Possible approaches==


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
As of Microsoft Internet Explorer 6, when you use the <tt>!DOCTYPE</tt> declaration to specify standards-compliant mode, the default value for this property is <tt>medium</tt>, not <tt>small</tt>.

Possible length values specified in a relative measurement, using the height of the element's font (em) or the height of the letter "x" (ex), are supported in Microsoft Internet Explorer 4.0 and later.

==See Also==