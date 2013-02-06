{{Page_Title|display}}
{{Flags}}
{{Standardization_Status|W3C Recommendation}}
{{API_Name}}
{{Summary_Section|Specifies the type of rendering box used for an element. In HTML, default display property values are based on behaviors listed in the HTML specifications or from the browser or user's default style sheet. The default value in XML is inline.

In addition to specifying one of the many different display box types, setting the display value to none lets you turn off (hide) the display of an element. A display element set to none ensures all descendant elements are also hidden. In these situations, the document renders as though the element does not exist in the document tree.}}
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
}}
{{Examples_Section
|Not_required=No
|Examples={{Single Example
|Language=CSS
|Description=Specify the rendering type as block or inline to define how the element will display. Set the element to inherit the rendering values of its parent container:
|Code=p.block 
{
display:block; /Sets the element to display in a box model rendering type.
}

p.inline 
{
display:inline; /Sets the element to display inline inside the current element.
}

p.inherit 
{
display:inherit; /Sets the display value to inherit its parent container's display values.
}
}}{{Single Example
|Language=HTML
|Description=The interactive utility demonstrates absolute values applied to a block of text, and relative values applied to the first sentence.
|Code=See live example above.
|LiveURL=http://letmespellitoutforyou.com/x/webplatform/fontSize.html
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

inline-table: The inline-table value does not have a direct mapping in HTML. It behaves like a <table> HTML element, but as an inline box, rather than a block-level box. Inside the table box is a block-level context.

table: Behaves like the &#60;table&#62; HTML element. It defines a block-level box.

table-caption: Behaves like the <caption> HTML element.

table-cell: Behaves like the <td> HTML element.

table-column: Behaves like the <col> HTML element.

table-column-group: Behaves like the <colgroup> HTML element. 

table-footer-group: Behaves like the <tfoot> HTML element.

table-header-group: Behaves like the corresponding <thead> HTML element. 

table-row: Behaves like the <tr> HTML element.

table-row-group: Behaves like the <tbody> HTML element.

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
|Name=CSS Fonts Module Level 3
|URL=http://www.w3.org/wiki/CSS/Properties/display
|Status=Working Draft
}}{{Related Specification
|Name=CSS Values and Units Module Level 3
|URL=http://www.w3.org/TR/css3-values/
|Status=Candidate Recommendation
}}
}}
{{Compatibility_Section
|Not_required=No
|Imported_tables=
|Desktop_rows={{Compatibility Table Desktop Row
|Chrome_supported=Yes
|Chrome_version=1.0
|Chrome_prefixed_supported=No
|Chrome_prefixed_version=
|Firefox_supported=Yes
|Firefox_version=1.0
|Firefox_prefixed_supported=No
|Firefox_prefixed_version=
|Internet_explorer_supported=Yes
|Internet_explorer_version=5.5
|Internet_explorer_prefixed_supported=No
|Internet_explorer_prefixed_version=
|Opera_supported=Yes
|Opera_version=7.0
|Opera_prefixed_supported=No
|Opera_prefixed_version=
|Safari_supported=Yes
|Safari_version=1.0
|Safari_prefixed_supported=No
|Safari_prefixed_version=
}}
|Mobile_rows={{Compatibility Table Mobile Row
|Android_supported=Yes
|Android_version=1.0
|Android_prefixed_supported=No
|Android_prefixed_version=
|Blackberry_supported=Yes
|Blackberry_version=3.8
|Blackberry_prefixed_supported=No
|Blackberry_prefixed_version=
|Chrome_mobile_supported=Yes
|Chrome_mobile_version=1.0
|Chrome_mobile_prefixed_supported=No
|Chrome_mobile_prefixed_version=
|Firefox_mobile_supported=Yes
|Firefox_mobile_version=1.0
|Firefox_mobile_prefixed_supported=No
|Firefox_mobile_prefixed_version=
|IE_mobile_supported=Yes
|IE_mobile_version=6.0
|IE_mobile_prefixed_supported=No
|IE_mobile_prefixed_version=
|Opera_mobile_supported=Yes
|Opera_mobile_version=6.0
|Opera_mobile_prefixed_supported=No
|Opera_mobile_prefixed_version=
|Opera_mini_supported=Yes
|Opera_mini_version=1.0
|Opera_mini_prefixed_supported=No
|Opera_mini_prefixed_version=
|Safari_mobile_supported=Yes
|Safari_mobile_version=1.0
|Safari_mobile_prefixed_supported=No
|Safari_mobile_prefixed_version=
}}
|Notes_rows={{Compatibility Notes Row
|Browser=IE
|Version=≤ 6.0
|Note=Requires a [[html/elements/!DOCTYPE|'''!DOCTYPE''']] declaration that triggers [[concepts/standards_mode|standards mode]], otherwise the initial value is '''small''' rather than '''medium'''.
}}{{Compatibility Notes Row
|Browser=IE
|Version=≤ 7.0
|Note=Does not support '''inherit''' as a value.
}}{{Compatibility Notes Row
|Browser=IE
|Version=≤ 8.0
|Note=Does not resize text specified with absolute pixel measurements when using the browser's ''text-resize'' feature, but does resize correctly when zooming the page.
}}{{Compatibility Notes Row
|Browser=IE
|Version=≤ 8.0
|Note=Does not support [[css/units/length|'''rem''']] values; specify other supported values as fallback properties.
}}{{Compatibility Notes Row
|Browser=All
|Note=Check compatibility for more recent [[css/units/length|viewport unit values]].
}}
}}
{{See_Also_Section
|Topic_clusters=CSS Font, Fonts, Text
|External_links=* Smashing: [http://www.smashingmagazine.com/2011/10/07/16-pixels-body-copy-anything-less-costly-mistake 16 Pixels: For Body Copy. Anything Less Is a Costly Mistake]
* HTML5 Boilerplate: [https://github.com/h5bp/html5-boilerplate/issues/724 Reasoning behind default font-size and line-height]
* A List Apart: [http://www.alistapart.com/articles/howtosizetextincss How to Size Text in CSS]
* Mozilla: [http://mxr.mozilla.org/mozilla/source/layout/style/html.css default style sheet]
* WebKit: [http://trac.webkit.org/browser/trunk/Source/WebCore/css/html.css default style sheet]
}}
{{Topics|CSS}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}