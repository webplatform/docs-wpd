---
title: display
overview_table:
  '[Initial value](/css/concepts/initial_value)': '`inline`'
  'Applies to': 'All elements'
  '[Inherited](/css/concepts/inherited)': 'No'
  Media: visual
  '[Computed value](/css/concepts/computed_value)': 'As specified, except for root element, floated elements, and absolutely positioned elements'
  Animatable: 'No'
  '[CSS Object Model Property](/css/concepts/cssom)': '`display`'
  Percentages: "\_???"
standardization_status: 'W3C Recommendation'
summary: "Specifies the type of rendering box used for an element. In HTML, default display property values are based on behaviors listed in the HTML specifications or from the browser or user's default style sheet. The default value in XML is inline.\n"
tags:
  - CSS
  - Properties
uri: 'WPD:Projects/CSS Property Milestone/css prop enhancements/test/css properties display'

---
## Summary

Specifies the type of rendering box used for an element. In HTML, default display property values are based on behaviors listed in the HTML specifications or from the browser or user's default style sheet. The default value in XML is inline.

In addition to specifying one of the many different display box types, setting the display value to none lets you turn off (hide) the display of an element. A display element set to none ensures all descendant elements are also hidden. In these situations, the document renders as though the element does not exist in the document tree.

## Overview table

[Initial value](/css/concepts/initial_value)
:   `inline`

Applies to
:   All elements

[Inherited](/css/concepts/inherited)
:   No

Media
:   visual

[Computed value](/css/concepts/computed_value)
:   As specified, except for root element, floated elements, and absolutely positioned elements

Animatable
:   No

[CSS Object Model Property](/css/concepts/cssom)
:   `display`

Percentages
:    ???

## Syntax

## Values

display-value
:   A keyword that defines the rendering type to apply to the element. Possible values are **none**, **inline**, **block**, **list-item**, **inline-block**, **inline-table**, **table**, **table-caption**, **table-cell**, **table-column**, **table-column-group**, **table-footer-group**, **table-header-group**, **table-row**, **table-row-group**, **flex**, **inline-flex**, **grid**, **inline-grid**, and **run-in**.

inherit
:   By default, the CSS display property is not inherited ("Inherited: no"). However, when the inherited property has been specified on an element ("Inherited: Yes"), the element uses the computed value of that property on its parent element. Only the root element of the document gets the initial value given in the property's summary.

inline
:   An element set to inline generates one or more inline element boxes.

none
:   Turns off the display of an element (it has no effect on layout); all descendant elements also have their display turned off. The document is rendered as though the element did not exist. To render an element box's dimensions, yet have its contents be invisible, set the visibility property to hidden. This is a basic value in CSS 1.

list-item
:   Generates a block box for the content and a separate list-item. This is a basic value in CSS 1.

inline-block
:   The element generates a block element box that flows with surrounding content as if it were a single inline box--and behaves like a replaced element. This is a basic value in CSS 2.1.

inline-table
:   The inline-table value does not have a direct mapping in HTML. It behaves like a \<table\> HTML element, but as an inline box, rather than a block-level box. Inside the table box is a block-level context. This is a table model value in CSS 2.1.

table
:   Behaves like the \<table\> HTML element. It defines a block-level box. This is a table model value in CSS 2.1.

table-caption
:   Behaves like the \<caption\> HTML element. This is a table model value in CSS 2.1.

table-cell
:   Behaves like the \<td\> HTML element. This is a table model value in CSS 2.1.

table-column
:   Behaves like the \<col\> HTML element. This is a table model value in CSS 2.1.

table-column-group
:   Behaves like the \<colgroup\> HTML element. This is a table model value in CSS 2.1.

table-footer-group
:   Behaves like the \<tfoot\> HTML element. This is a table model value in CSS 2.1.

table-header-group
:   Behaves like the corresponding \<thead\> HTML element. This is a table model value in CSS 2.1.

table-row
:   Behaves like the \<tr\> HTML element. This is a table model value in CSS 2.1.

table-row-group
:   Behaves like the \<tbody\> HTML element. This is a table model value in CSS 2.1.

flex
:   Behaves like an block element for laying out content in the flexbox model. This is a flexbox model value in CSS3.

inline-flex
:   Behaves like an inline element for laying out content in the flexbox model. This is a flexbox model value in CSS3.

grid
:   Behaves like a block element for laying out content in the grid model.

Note: At the time of this writing, most modern browsers do not support this property. This is a grid box model value (an experimental tag in CSS 3.0).

inline-grid
:   Behaves like an inline element for laying out content in the grid model. This is a grid box model value (an experimental tag in CSS 3.0).

run-in
:   The behavior depends on the following conditions:

-   If the run-in box contains a block box, same as block.
-   If a block box follows the run-in box, the run-in box becomes the first inline box of the block box.
-   If a inline box follows, the run-in box becomes a block box. .

block
:   Generates a block element box. This is a basic value in CSS 1.

ruby
:   Specifies that an element defines a **ruby** structure. This and the following values are from the [CSS3 Ruby Module](http://go.microsoft.com/fwlink/p/?linkid=203763). This value only applies to the supported ruby elements, **rt** and **ruby**.

ruby-base
:   Specifies that an element defines a ruby base. This value only applies to the supported ruby elements, **rt** and **ruby**.

ruby-text
:   Specifies that an element defines a **ruby text**. This value only applies to the supported ruby elements, **rt** and **ruby**.

ruby-base-container
:   Specifies a container for one or more ruby base elements. This value only applies to the supported ruby elements, **rt** and **ruby**.

ruby-text-container
:   Specifies a container for one or more ruby text elements. This value only applies to the supported ruby elements, **rt** and **ruby**.

-ms-flexbox
:   Internet Explorer 10. Specifies a block-level flexible box ("flexbox") container. For more information on flexbox containers, see [Flexible Box ("Flexbox") Layout](/css/flexbox).

-ms-inline-flexbox
:   Internet Explorer 10. Specifies an inline-level flexible box ("flexbox") container. For more information on flexbox containers, see [Flexible Box ("Flexbox") Layout](/css/flexbox).

-ms-grid
:   Internet Explorer 10. Specifies a block-level Grid element. For more information on grid layout, see Grid Layout.

-ms-inline-grid
:   Internet Explorer 10. Specifies an inline-level Grid element. For more information on grid layout, see Grid Layout.

## Examples

Change a `span`-element from its initial display `inline` to display as block-level element.

``` html
Some example text
<style>
  span {
    display: block;
  }
</style>
```

**Second example**

Do not display an element by using `display: none;`.

``` html
<div>Some example text</div>
<style>
  div {
    display: none;
  }
</style>
```

**Third example**

Specify the rendering type as block or inline to define how the element will display. Set the element to inherit the rendering values of its parent container:

``` html
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
```

## Usage

     Basic values in CSS 1

-   none
-   inline
-   block
-   list-item

**Extended values in CSS 2.1**

-   inline-block

**Table model values in CSS 2.1**

-   inline-table
-   table
-   table-caption
-   table-cell
-   table-column
-   table-column-group
-   table-footer-group
-   table-header-group
-   table-row
-   table-row-group

**Flexbox model values in CSS3**

-   flex
-   inline-flex

**Grid box model values (experimental in CSS3)**

-   grid
-   inline-grid

**Experimental values**

-   run-in

## Related specifications

[CSS Basic Box Model](http://dev.w3.org/csswg/css3-box/#display)
:   Working Draft

[CSS Grid Layout](http://dev.w3.org/csswg/css3-grid-layout/#grid-declaration)
:   Working Draft

[CSS Flexible Box Layout Module](http://dev.w3.org/csswg/css3-flexbox/#flex-containers)
:   Candidate Recommendation

[CSS Level 2 (Revision 1)](http://www.w3.org/TR/CSS2/visuren.html#display-prop)
:   Recommendation

[CSS Level 1](http://www.w3.org/TR/CSS1/#display)
:   Recommendation

## See also

### Related articles

#### CSS Font

-   [font-family](/css/properties/font-family)

-   [font-kerning](/css/properties/font-kerning)

-   [font-language-override](/css/properties/font-language-override)

-   [font-size](/css/properties/font-size)

-   [font-size-adjust](/css/properties/font-size-adjust)

-   [font-style](/css/properties/font-style)

-   [font-synthesis](/css/properties/font-synthesis)

-   [font-variant](/css/properties/font-variant)

-   [kerning-mode](/css/properties/kerning-mode)

-   [kerning-pair-threshold](/css/properties/kerning-pair-threshold)

-   [text-rendering](/css/properties/text-rendering)

-   [text-underline](/css/properties/text-underline)

-   [user-modify](/css/properties/user-modify)

#### Fonts

-   [@font-face](/css/atrules/@font-face)

-   [Font related properties](/css/fonts)

-   [font-variant](/css/fonts/font-variant)

-   [font](/css/properties/font)

-   [font-family](/css/properties/font-family)

-   [font-feature-settings](/css/properties/font-feature-settings)

-   [font-kerning](/css/properties/font-kerning)

-   [font-language-override](/css/properties/font-language-override)

-   [font-size](/css/properties/font-size)

-   [font-size-adjust](/css/properties/font-size-adjust)

-   [font-stretch](/css/properties/font-stretch)

-   [font-style](/css/properties/font-style)

-   [font-synthesis](/css/properties/font-synthesis)

-   [font-variant](/css/properties/font-variant)

-   [max-font-size](/css/properties/max-font-size)

-   [min-font-size](/css/properties/min-font-size)

-   [user-modify](/css/properties/user-modify)

-   [size](/html/attributes/size)

-   [font](/html/elements/font)

#### Text

-   [block-progression](/css/properties/block-progression)

-   [font-language-override](/css/properties/font-language-override)

-   [font-size](/css/properties/font-size)

-   [font-synthesis](/css/properties/font-synthesis)

-   [hanging-punctuation](/css/properties/hanging-punctuation)

-   [hyphenate-limit-chars](/css/properties/hyphenate-limit-chars)

-   [hyphenate-limit-lines](/css/properties/hyphenate-limit-lines)

-   [hyphenate-limit-zone](/css/properties/hyphenate-limit-zone)

-   [hyphens](/css/properties/hyphens)

-   [ime-mode](/css/properties/ime-mode)

-   [layout-flow](/css/properties/layout-flow)

-   [layout-grid](/css/properties/layout-grid)

-   [layout-grid-char](/css/properties/layout-grid-char)

-   [layout-grid-line](/css/properties/layout-grid-line)

-   [layout-grid-mode](/css/properties/layout-grid-mode)

-   [layout-grid-type](/css/properties/layout-grid-type)

-   [letter-spacing](/css/properties/letter-spacing)

-   [line-break](/css/properties/line-break)

-   [max-font-size](/css/properties/max-font-size)

-   [min-font-size](/css/properties/min-font-size)

-   [text-overflow-ellipsis](/css/properties/text-overflow-ellipsis)

-   [text-overflow-mode](/css/properties/text-overflow-mode)

-   [text-rendering](/css/properties/text-rendering)

-   [text-underline-position](/css/properties/text-underline-position)

-   [text-underline-style](/css/properties/text-underline-style)

-   [text-underline-width](/css/properties/text-underline-width)

-   [user-input](/css/properties/user-input)

-   [user-modify](/css/properties/user-modify)

-   [Text](/css/text)

-   [size](/html/attributes/size)

-   [b](/html/elements/b)

-   [b](/html/elements/b/ja)

-   [br](/html/elements/br)

-   [br](/html/elements/br/ja)

-   [caption](/html/elements/caption)

-   [cite](/html/elements/cite)

-   [code](/html/elements/code)

-   [del](/html/elements/del)

-   [dfn](/html/elements/dfn)

-   [em](/html/elements/em)

-   [font](/html/elements/font)

-   [hr](/html/elements/hr)

-   [i](/html/elements/i)

-   [ins](/html/elements/ins)

-   [kbd](/html/elements/kbd)

-   [mark](/html/elements/mark)

-   [samp](/html/elements/samp)

-   [strong](/html/elements/strong)

-   [Achieving typographic effects with the canvas tag](/tutorials/canvas_texteffects)

### External resources

-   Quirksmode: [The display property](http://www.quirksmode.org/css/display.html)
-   Mozilla Developer Network: [CSS Reference: The display property](https://developer.mozilla.org/en-US/docs/CSS/display)

## Notes

### Remarks

To render an element box's dimensions, yet have its contents be invisible, see the [visibility](/css/properties/visibility) property.

All visible HTML **div** object is a block element, and a **span** object is an inline element. Block elements typically start a new line and can contain other block elements and inline elements. Inline elements do not typically start a new line and can contain other inline elements or data. Changing the values for the **display** property affects the layout of the surrounding content by:

-   Adding a new line after the element with the value **block**.
-   Removing a line from the element with the value **inline**.
-   Hiding the data for the element with the value **none**.

In contrast to the [visibility](/css/properties/visibility) property, `display: none` reserves no space for the object on the screen. The `table-header-group` and `table-footer-group` values can be used to specify that the contents of the `thead` and `tfoot` elements are displayed on every page for a table that spans multiple pages.

You can use `inline-block` to give an object a layout without specifying the object's height or width.

The Cascading Style Sheets (CSS) table display model does not require explicit elements to correspond with the HTML tags. For example, an element styled as `display: table-cell` does not need to be contained within a block that is styled `display: table-row` to be styled correctly. Implicit table elements are created as necessary in an attempt to make the document valid. Contrast this behavior to the traditional HTML table model, where table elements are implicitly closed early to avoid unexpected nesting.

### Rendering for floating or absolute positioned elements

|Specified value|Computed value|
|:--------------|:-------------|
|inline-table|table|
|inline, run-in, table-row-group, table-column, table-column-group, table-header-group, table-footer-group, table-row, table-cell, table-caption, inline-block|block|
|others|same as specified|

