==Summary==
blah blah

==Syntax==
{| class="wikitable template_test"
! Property name
! Values
! Example
|-
| rowspan="2"| border-radius
| [[#length_value|length]]
| [[#length_examples|border-radius: 1em;]]
|-
| [[#percentage_value|percentage]]
| [[#percentage_examples|border-radius: 10%;]]
|}

==Values==

<dt id="length_value" class="template_test">length</dt>
<dd class="template_test">The size of the circle radius or the horizontal and vertical radii, for elliptical curves. 
<br>
It can be expressed in any unit allowed in CSS <length> data types. em units are useful for controls that scale proportionally with the font-size. Viewport-relative units (vw, vh, vmin, vmax) can be useful for controls that scale with the viewport size. 
<br>
Negative values are invalid.</dd>

<dt id="percentage_value" class="template_test">percentage</dt>
<dd class="template_test">The size of the corner radius, in percentages of the box’s dimensions.
<br>
Specifically, percentages for the horizontal axis refer to the width of the box, percentages for the vertical axis refer to the height of the box.
<br>
Negative values are invalid.</dd>

==Examples==

===length examples===
 border-radius: 1em;

 border-radius: 5px;

===percentage examples===
 border-radius: 10%;

 border-radius: 50%;