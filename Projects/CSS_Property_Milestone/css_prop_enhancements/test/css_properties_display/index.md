{{Page_Title|display}}
{{Flags
|Content=Compatibility Incomplete
}}
{{Standardization_Status|W3C Recommendation}}
{{API_Name}}
{{Summary_Section|Specifies the type of rendering box used for an element. In HTML, default display property values are based on behaviors listed in the HTML specifications or from the browser or user's default style sheet. The default value in XML is inline.

In addition to specifying one of the many different display box types, setting the display value to none lets you turn off (hide) the display of an element. A display element set to none ensures all descendant elements are also hidden. In these situations, the document renders as though the element does not exist in the document tree.
}}
{{CSS Property
|Initial value=inline
|Applies to=All elements
|Inherited=No
|Media=visual
|Computed value=As specified, except for root element, floated elements, and absolutely positioned elements
|Animatable=No
|CSS object model property=display
|CSS percentages=???
|Values={{CSS Property Value
|Data Type=display-value
|Description=A keyword that defines the rendering type to apply to the element. Possible values are '''none''', '''inline''', '''block''', '''list-item''', '''inline-block''', '''inline-table''', '''table''', '''table-caption''', '''table-cell''', '''table-column''', '''table-column-group''', '''table-footer-group''', '''table-header-group''', '''table-row''', '''table-row-group''', '''flex''', '''inline-flex''', '''grid''', '''inline-grid''', and '''run-in'''.
}}{{CSS Property Value
|Data Type=inherit
|Description=By default, the CSS display property is not inherited ("Inherited: no"). However, when the inherited property has been specified on an element ("Inherited: Yes"), the element uses the computed value of that property on its parent element. Only the root element of the document gets the initial value given in the property's summary.
}}{{CSS Property Value
|Data Type=inline
|Description=An element set to inline generates one or more inline element boxes.
}}
{{CSS Property Value
|Data Type=none
|Description=Turns off the display of an element (it has no effect on layout); all descendant elements also have their display turned off. The document is rendered as though the element did not exist. To render an element box's dimensions, yet have its contents be invisible, set the visibility property to hidden. This is a basic value in CSS 1.
}}
{{CSS Property Value
|Data Type=list-item
|Description=Generates a block box for the content and a separate list-item. This is a basic value in CSS 1.
}}{{CSS Property Value
|Data Type=inline-block
|Description=The element generates a block element box that flows with surrounding content as if it were a single inline box--and behaves like a replaced element. This is a basic value in CSS 2.1.
}}{{CSS Property Value
|Data Type=inline-table
|Description=The inline-table value does not have a direct mapping in HTML. It behaves like a &#60;table&#62; HTML element, but as an inline box, rather than a block-level box. Inside the table box is a block-level context. This is a table model value in CSS 2.1.
}}{{CSS Property Value
|Data Type=table
|Description=Behaves like the &#60;table&#62; HTML element. It defines a block-level box. This is a table model value in CSS 2.1.
}}{{CSS Property Value
|Data Type=table-caption
|Description=Behaves like the &#60;caption&#62; HTML element. This is a table model value in CSS 2.1.
}}{{CSS Property Value
|Data Type=table-cell
|Description=Behaves like the &#60;td&#62; HTML element. This is a table model value in CSS 2.1.
}}{{CSS Property Value
|Data Type=table-column
|Description=Behaves like the &#60;col&#62; HTML element. This is a table model value in CSS 2.1.
}}{{CSS Property Value
|Data Type=table-column-group 
|Description=Behaves like the &#60;colgroup&#62; HTML element. This is a table model value in CSS 2.1.
}}{{CSS Property Value
|Data Type=table-footer-group
|Description=Behaves like the &#60;tfoot&#62; HTML element. This is a table model value in CSS 2.1.
}}{{CSS Property Value
|Data Type=table-header-group
|Description=Behaves like the corresponding &#60;thead&#62; HTML element. This is a table model value in CSS 2.1.
}}{{CSS Property Value
|Data Type=table-row
|Description=Behaves like the &#60;tr&#62; HTML element. This is a table model value in CSS 2.1.
}}{{CSS Property Value
|Data Type=table-row-group
|Description=Behaves like the &#60;tbody&#62; HTML element. This is a table model value in CSS 2.1.
}}{{CSS Property Value
|Data Type=flex
|Description=Behaves like an block element for laying out content in the flexbox model. This is a flexbox model value in CSS3.
}}{{CSS Property Value
|Data Type=inline-flex
|Description=Behaves like an inline element for laying out content in the flexbox model. This is a flexbox model value in CSS3.
}}{{CSS Property Value
|Data Type=grid
|Description=Behaves like a block element for laying out content in the grid model.
Note: At the time of this writing, most modern browsers do not support this property. This is a grid box model value (an experimental tag in CSS 3.0).
}}{{CSS Property Value
|Data Type=inline-grid
|Description=Behaves like an inline element for laying out content in the grid model. This is a grid box model value (an experimental tag in CSS 3.0).
}}{{CSS Property Value
|Data Type=run-in
|Description=The behavior depends on the following conditions:

* If the run-in box contains a block box, same as block.
* If a block box follows the run-in box, the run-in box becomes the first inline box of the block box.
* If a inline box follows, the run-in box becomes a block box. .
}}{{CSS Property Value
|Data Type=block
|Description=Generates a block element box. This is a basic value in CSS 1.
}}{{CSS Property Value
|Data Type=inline-table
|Description=The inline-table value does not have a direct mapping in HTML. It behaves like a &#60;table&#62; HTML element, but as an inline box, rather than a block-level box. Inside the table box is a block-level context. This is a table model value in CSS 2.1.
}}
}}
{{Examples_Section
|Not_required=No
|Examples={{Single Example
|Language=CSS
|Description=Specify the rendering type as block or inline to define how the element will display. Set the element to inherit the rendering values of its parent container:
|Code=p.block 
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
}}
}}
{{Notes_Section
|Usage='''Basic values in CSS 1'''

none: Turns off the display of an element (it has no effect on layout); all descendant elements also have their display turned off. The document is rendered as though the element did not exist. To render an element box's dimensions, yet have its contents be invisible, set the visibility property to hidden.

inline: Generates one or more inline element boxes.

block: Generates a block element box.

list-item: Generates a block box for the content and a separate list-item.

'''Extended values in CSS 2.1'''

inline-block: The element generates a block element box that flows with surrounding content as if it were a single inline box--and behaves like a replaced element.

'''Table model values in CSS 2.1'''

inline-table: The inline-table value does not have a direct mapping in HTML. It behaves like a &#60;table&#62; HTML element, but as an inline box, rather than a block-level box. Inside the table box is a block-level context.

table: Behaves like the &#60;table&#62; HTML element. It defines a block-level box.

table-caption: Behaves like the &#60;caption&#62; HTML element.

table-cell: Behaves like the &#60;td&#62; HTML element.

table-column: Behaves like the &#60;col&#62; HTML element.

table-column-group: Behaves like the &#60;colgroup&#62; HTML element. 

table-footer-group: Behaves like the &#60;tfoot&#62; HTML element.

table-header-group: Behaves like the corresponding &#60;thead&#62; HTML element. 

table-row: Behaves like the &#60;tr&#62; HTML element.

table-row-group: Behaves like the &#60;tbody&#62; HTML element.

'''Flexbox model values in CSS3'''

flex: Behaves like an block element for laying out content in the flexbox model.

inline-flex: Behaves like an inline element for laying out content in the flexbox model.

'''Grid box model values (experimental in CSS3)'''

grid: Behaves like a block element for laying out content in the grid model. 

Note: At the time of this writing, most modern browsers do not support this property.

inline-grid: Behaves like an inline element for laying out content in the grid model. 

'''Experimental values'''

run-in: The behavior depends on the following conditions: 
*If the run-in box contains a block box, same as block.
*If a block box follows the run-in box, the run-in box becomes the first inline box of the block box.
*If a inline box follows, the run-in box becomes a block box.
}}
{{Related_Specifications_Section
|Specifications={{Related Specification
|Name=CSS Basic Box Model
|URL=http://dev.w3.org/csswg/css3-box/#display
|Status=Working Draft
}}{{Related Specification
|Name=CSS Grid Layout
|URL=http://dev.w3.org/csswg/css3-grid-layout/#grid-declaration0
|Status=Working Draft
}}{{Related Specification
|Name=CSS Flexible Box Layout Module
|URL=http://dev.w3.org/csswg/css3-flexbox/#flex-containers
|Status=Candidate Recommendation
}}{{Related Specification
|Name=CSS Level 2 (Revision 1)
|URL=http://www.w3.org/TR/CSS2/visuren.html#display-prop
|Status=Recommendation
}}{{Related Specification
|Name=CSS Level 1
|URL=http://www.w3.org/TR/CSS1/#display
|Status=Recommendation
}}
}}
{{Compatibility_Section
|Not_required=No
|Imported_tables=
|Desktop_rows={{Compatibility Table Desktop Row
|Chrome_supported=Yes
|Chrome_version=18 (Win) and 17 (Mac)
|Chrome_prefixed_supported=No
|Chrome_prefixed_version=
|Firefox_supported=Yes
|Firefox_version=10.0.2
|Firefox_prefixed_supported=No
|Firefox_prefixed_version=
|Internet_explorer_supported=Yes
|Internet_explorer_version=5.5
|Internet_explorer_prefixed_supported=No
|Internet_explorer_prefixed_version=
|Opera_supported=Yes
|Opera_version=11.61 (Win) and 11.61 (Mac)
|Opera_prefixed_supported=No
|Opera_prefixed_version=
|Safari_supported=Yes
|Safari_version=5.1 (Win) and 5.1.2 (Mac)
|Safari_prefixed_supported=No
|Safari_prefixed_version=
}}
|Mobile_rows={{Compatibility Table Mobile Row
|Android_supported=Yes
|Android_version=2.1
|Android_prefixed_supported=No
|Android_prefixed_version=
|Blackberry_supported=Yes
|Blackberry_version=7.0
|Blackberry_prefixed_supported=No
|Blackberry_prefixed_version=
|Chrome_mobile_supported=Unknown
|Chrome_mobile_version=
|Chrome_mobile_prefixed_supported=No
|Chrome_mobile_prefixed_version=
|Firefox_mobile_supported=Unknown
|Firefox_mobile_version=
|Firefox_mobile_prefixed_supported=No
|Firefox_mobile_prefixed_version=
|IE_mobile_supported=Unknown
|IE_mobile_version=
|IE_mobile_prefixed_supported=No
|IE_mobile_prefixed_version=
|Opera_mobile_supported=Yes
|Opera_mobile_version=5.0
|Opera_mobile_prefixed_supported=No
|Opera_mobile_prefixed_version=
|Opera_mini_supported=Yes
|Opera_mini_version=5.0
|Opera_mini_prefixed_supported=No
|Opera_mini_prefixed_version=
|Safari_mobile_supported=Yes
|Safari_mobile_version=3.2
|Safari_mobile_prefixed_supported=No
|Safari_mobile_prefixed_version=
}}
|Notes_rows={{Compatibility Notes Row
|Browser=IE
|Version=All
|Note=flex and inline-flex are not supported in Internet Explorer.
}}{{Compatibility Notes Row
|Browser=IE
|Version=< 8
|Note=display:inline-block only works on inline elements, not on block elements.
}}{{Compatibility Notes Row
|Browser=IE
|Version=<7
|Note=Table display not supported.
}}{{Compatibility Notes Row
|Browser=Firefox
|Version=16+
|Note=Supports inline-block and table display.
}}{{Compatibility Notes Row
|Browser=Chrome
|Version=23+
|Note=Supports inline-block and table display.
}}{{Compatibility Notes Row
|Browser=Opera
|Version=12.1+
|Note=Supports inline-block and table display.
}}{{Compatibility Notes Row
|Browser=Firefox
|Version=All
|Note=Does not support run-in, grid, or inline-grid.
}}{{Compatibility Notes Row
|Browser=Internet Explorer
|Version=Al
|Note=Does not support flex or inline-flex.
}}{{Compatibility Notes Row
|Browser=Safari
|Version=All
|Note=Does not support flex or inline-flex.
}}{{Compatibility Notes Row
|Browser=iOS Safari 
|Version=3.2+
|Note=Supports inline-block and table display.
}}
}}
{{See_Also_Section
|Topic_clusters=CSS Font, Fonts, Text
|External_links=* Quirksmode: [http://www.quirksmode.org/css/display.html: The display property]
* W3 Schools: [http://www.w3schools.com/cssref/pr_class_display.asp: CSS display property]
* Mozilla: [https://developer.mozilla.org/en-US/docs/CSS/display: CSS Display Property]
}}
{{Topics|CSS}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}