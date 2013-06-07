=font-size=
<compatability topic="css" type="property" feature="font-size" format="list"> </compatability>

==Summary==
<code>font-size</code> sets the font size of the element to which it is applied, and that of its descendants. You can size text using absolute measurements, or measurements relative to the affected element's parent or root elements. [[guides/css_text_styling_fundamentals|CSS Text Styling Fundamentals]] provides an overview.

==Syntax==
{| class="wikitable template_test"
! Property name
! Values
! Example
|-
! rowspan="4"| font-size
| [[#absolute-size_value|absolute-size]]
| [[#absolute-size_examples|font-size: small;]]
|-
| [[#relative-size_value|relative-size]]
| [[#relative-size_examples|font-size: larger;]]
|-
| [[#length_value|length]]
| [[#length_examples|font-size: 1.5em;]]
|-
| [[#percentage_value|percentage]]
| [[#percentage_examples|font-size: 110%;]]
|}

==Values==
<dl>
<dt id="absolute-size_value" class="template_test">absolute-size</dt>
<dd class="template_test">A set of keywords indicating predefined font sizes that scale according to font setting preferences or each browser's default values. From small to large, possible values are '''xx-small''', '''x-small''', '''small''', '''medium''', '''large''', '''x-large''', and '''xx-large'''.
<br>
'''Keywords:'''
<ul class="keywords">
   <li><code class="value keyword">xx-small</code> 3/5 parent font-size</li>
   <li><code class="value keyword">x-small</code> 3/4 parent font-size</li>
   <li><code class="value keyword">small</code> 8/9 parent font-size</li>
   <li><code class="value keyword">medium</code> 1 parent font-size</li>
   <li><code class="value keyword">large</code> 6/5 parent font-size</li>
   <li><code class="value keyword">x-large</code> 3/2 parent font-size</li>
   <li><code class="value keyword">xx-large</code> 2/1 parent font-size</li>
</ul>
</dd>

<dt id="relative-size_value" class="template_test">relative-size</dt>
<dd class="template_test">A set of keywords interpreted relative to the parent element's '''font-size''' — either '''smaller''' or '''larger'''.
<br>
'''Keywords:'''
<ul class="keywords">
    <li><code class="value keyword">smaller</code> 1 increment lower than parent font-size (e.g. if the parent font-size is <code>medium</code>, the <code>smaller</code> value would be interpreted as <code>small</code>)</li>
   <li><code class="value keyword">larger</code>  1 increment higher than parent font-size (e.g. if the parent font-size is <code>medium</code>, the <code>larger</code> value would be interpreted as <code>large</code>)</li>
</ul>
</dd>

<dt id="length_value" class="template_test">length</dt>
<dd class="template_test">A positive numeric value followed by a string designating [[css/data_types/length|absolute or relative units of length]]. Proportional [[css/data_types/length|'''em''' and '''ex''']] measurements are based on the parent element's '''font-size''', while [[css/data_types/length|'''rem''']] measurements are based on that of the root element.</dd>

<dt id="percentage_value" class="template_test">percentage</dt>
<dd class="template_test">A positive integer followed by a percent ([[css/data_types/numeric|'''%''']]), indicating a percentage of the parent element's '''font-size'''.</dd>
</dl>

==Overview table==
{| class="wikitable"
| Initial value
| <code>medium</code>
|-
| Applies to
| All elements
|-
| Inherited
|  Yes
|-
| Media
| visual
|-
| Computed value
| absolute size in '''px''' units
|-
| Animatable
| Yes
|-
| CSS Object Model Property
| <code>fontSize</code>
|}

==Examples==

===absolute-size	 examples===
<syntaxhighlight>
 font-size: small;
</syntaxhighlight>

<syntaxhighlight>
 font-size: xx-large;
</syntaxhighlight>

===relative-size examples===
<syntaxhighlight>
 font-sizes: larger;
</syntaxhighlight>

<syntaxhighlight>
 font-sizes: smaller;
</syntaxhighlight>

===length examples===
<syntaxhighlight>
 font-size: 1.5em;
</syntaxhighlight>

<syntaxhighlight>
 border-radius: 5px;
</syntaxhighlight>

===percentage examples===
<syntaxhighlight>
 font-size: 110%;
</syntaxhighlight>

<syntaxhighlight>
 border-radius: 50%;
</syntaxhighlight>

===Other examples===
Redefine the typical '''16px''' default '''medium''' value as '''10px''', then redefine other tags in proportion to the root:
<syntaxhighlight>
html { font-size: 62.5%; } 
/* 
16 * 62.5% == 10 
*/

h1 { font-size: 3.6rem }   /* 36px */
h2 { font-size: 2.4rem }   /* 24px */
p  { font-size: 1.4rem }   /* 14px */
</syntaxhighlight>


==Usage==

==Notes==

==Compatibility==
<compatability topic="css" type="property" feature="font-size"> </compatability>

==Related Specifications==
{| class="wikitable"
! Specification
! Status
! Related Changes
|-
| [http://www.w3.org/TR/css3-fonts/#font-size-prop CSS Fonts Module Level 3]
| Working Draft
| 
|-
| [http://www.w3.org/TR/css3-values/ CSS Values and Units Module Level 3]
| Candidate Recommendation
| 
|-
| [http://www.w3.org/TR/CSS2/ Cascading Style Sheets Level 2 Revision 1 (CSS 2.1) Specification]
| W3C Recommendation
| 
|}

==See Also==