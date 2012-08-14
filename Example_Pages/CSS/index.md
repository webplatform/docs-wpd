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

==Specifications==

==Browser Compatibility==

==See Also==