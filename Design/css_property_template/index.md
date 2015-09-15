---
title: font-size
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - 'css/data types/numeric'
uri: 'WPD:Design/css property template'

---
\<compatability topic="css" type="property" feature="font-size" format="list"\> \</compatability\>

## <span>Summary</span>

`font-size` sets the font size of the element to which it is applied, and that of its descendants. You can size text using absolute measurements, or measurements relative to the affected element's parent or root elements. [CSS Text Styling Fundamentals](/guides/css_text_styling_fundamentals) provides an overview.

## <span>Syntax</span>

<table class="wikitable template_test">
<tr>
<th>
Property name

</th>
<th>
Values

</th>
<th>
Example

</th>
</tr>
<tr>
<th rowspan="4">
font-size

</th>
<td>
[absolute-size](#absolute-size_value)

</td>
<td>
[font-size: small;](#absolute-size_examples)

</td>
</tr>
<tr>
<td>
[relative-size](#relative-size_value)

</td>
<td>
[font-size: larger;](#relative-size_examples)

</td>
</tr>
<tr>
<td>
[length](#length_value)

</td>
<td>
[font-size: 1.5em;](#length_examples)

</td>
</tr>
<tr>
<td>
[percentage](#percentage_value)

</td>
<td>
[font-size: 110%;](#percentage_examples)

</td>
</tr>
</table>
## <span>Values</span>

absolute-size
:   A set of keywords indicating predefined font sizes that scale according to font setting preferences or each browser's default values. From small to large, possible values are **xx-small**, **x-small**, **small**, **medium**, **large**, **x-large**, and **xx-large**.
    **Keywords:**

    -   `xx-small` 3/5 parent font-size
    -   `x-small` 3/4 parent font-size
    -   `small` 8/9 parent font-size
    -   `medium` 1 parent font-size
    -   `large` 6/5 parent font-size
    -   `x-large` 3/2 parent font-size
    -   `xx-large` 2/1 parent font-size

relative-size
:   A set of keywords interpreted relative to the parent element's **font-size** — either **smaller** or **larger**.
    **Keywords:**

    -   `smaller` 1 increment lower than parent font-size (e.g. if the parent font-size is `medium`, the `smaller` value would be interpreted as `small`)
    -   `larger` 1 increment higher than parent font-size (e.g. if the parent font-size is `medium`, the `larger` value would be interpreted as `large`)

length
:   A positive numeric value followed by a string designating [absolute or relative units of length](/css/data_types/length). Proportional [**em** and **ex**](/css/data_types/length) measurements are based on the parent element's **font-size**, while [**rem**](/css/data_types/length) measurements are based on that of the root element.
percentage
:   A positive integer followed by a percent ([**%**](/w/index.php?title=css/data_types/numeric&action=edit&redlink=1)), indicating a percentage of the parent element's **font-size**.

## <span>Overview table</span>

||
|Initial value|`medium`|
|Applies to|All elements|
|Inherited|Yes|
|Media|visual|
|Computed value|absolute size in **px** units|
|Animatable|Yes|
|CSS Object Model Property|`fontSize`|

## <span>Examples</span>

### <span>absolute-size examples</span>

``` html
 font-size: small;
```

``` html
 font-size: xx-large;
```

### <span>relative-size examples</span>

``` html
 font-sizes: larger;
```

``` html
 font-sizes: smaller;
```

### <span>length examples</span>

``` html
 font-size: 1.5em;
```

``` html
 border-radius: 5px;
```

### <span>percentage examples</span>

``` html
 font-size: 110%;
```

``` html
 border-radius: 50%;
```

### <span>Other examples</span>

Redefine the typical **16px** default **medium** value as **10px**, then redefine other tags in proportion to the root:

``` html
html { font-size: 62.5%; }
/*
16 * 62.5% == 10
*/

h1 { font-size: 3.6rem }   /* 36px */
h2 { font-size: 2.4rem }   /* 24px */
p  { font-size: 1.4rem }   /* 14px */
```

## <span>Usage</span>

## <span>Notes</span>

## <span>Compatibility</span>

\<compatability topic="css" type="property" feature="font-size"\> \</compatability\>

## <span>Related Specifications</span>

|Specification|Status|Related Changes|
|:------------|:-----|:--------------|
|[CSS Fonts Module Level 3](http://www.w3.org/TR/css3-fonts/#font-size-prop)|Working Draft||
|[CSS Values and Units Module Level 3](http://www.w3.org/TR/css3-values/)|Candidate Recommendation||
|[Cascading Style Sheets Level 2 Revision 1 (CSS 2.1) Specification](http://www.w3.org/TR/CSS2/)|W3C Recommendation||

## <span>See Also</span>