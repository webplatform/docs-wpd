---
title: 'CSS'
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - CSS/Concepts/Initial-Value
    - CSS/concepts/Inherited
    - CSS/media/visual
    - CSS/concepts/Computed-value
    - CSS/concepts/CSSOM
    - CSS/datatypes/length
    - CSS/examples
    - CSS/properties/font
    - CSS/properties/font-family
    - CSS/properties/font-size
    - CSS/properties/font-size-adjust
    - CSS/properties/font-stretch
    - CSS/properties/font-style
    - CSS/properties/font-variant
    - CSS/properties/font-weight
    - CSS/atrules/@font-face
    - DOM/element/CSSStyleDeclaration
    - DOM/element/properties/currentStyle
    - DOM/element/properties/defaults
    - 'Template:CompatGeckoDesktop("1")'
    - 'Template:CompatGeckoMobile("1")'
uri: 'WPD:Example Pages/CSS'

---
**This is a temporary page to pull together an example of what the ideal end state will be. It includes some content from MDN that is not compatible with the WPD license, and should be removed soon.**

Based on: <https://developer.mozilla.org/en-US/docs/CSS/font-size> and <http://msdn.microsoft.com/en-us/library/ie/ms530759(v=vs.85).aspx>

## Summary

The `font-size` CSS properties specifies the size of the font used for text in the object. Setting the font size may, in turn, change the size of other items, since it is used to compute the value of `em` and `ex` length units.

**Implementation Note**: use property of type text so we can pull this out elsewhere

## Overview table

||
|[Initial Value](/w/index.php?title=CSS/Concepts/Initial-Value&action=edit&redlink=1)|`medium`|
|Applies to|All elements|
|[Inherited](/w/index.php?title=CSS/concepts/Inherited&action=edit&redlink=1)|Yes|
|Percentages|Relative to parent element's font size|
|Media|` visual`|
|[Computed value](/w/index.php?title=CSS/concepts/Computed-value&action=edit&redlink=1)|Absolute length|
|[CSS Object Model Property](/w/index.php?title=CSS/concepts/CSSOM&action=edit&redlink=1)|`fontSize`|
|Animatable|No|

## Syntax

    font-size:  xx-small | x-small | small | medium | large | x-large | xx-large
    font-size: smaller | larger
    font-size: <length> | <percentage>

***Implementation Note:** Each keyword above should be automatically generated and link to the relevant part of the Values section below. Have a template for this block based on a query to properties that are set in values section to create it.*

## Values

***Implementation Note:** We need to be able to differentiate between literal values, data types and placeholders.*

`xx-small`, `x-small`, `small`, `medium`, `large`, `x-large`, `xx-large`
:   Indicate predefined abosolute font sizes. Named font sizes scale according to the user's font setting preferences.

`larger`, `smaller`
:   Relatively larger or smaller than the parent element's font size, by roughly the ratio used to separate the absolute-size keywords relative to the font size of the parent object.

[\<length\>](/w/index.php?title=CSS/datatypes/length&action=edit&redlink=1)
:   A positive length, followed by an absolute units designator (`cm`, `mm`, `in`, `pt`, or `pc`) or a relative units designator (`em`, `ex`, or `px`). When the units are specified in `em` or `ex`, the size is defined relative to the size of the font on the parent element of the element in question. For example, `0.5em` is half the font size of the parent of the current element. Negative values are not allowed.

*percentage*
:   A positive percentage of the parent element's font size, followed by a percent symbol (%). The value is a percentage of the parent object's font size. Negative values are not allowed.

## Examples

[View live examples](/w/index.php?title=CSS/examples&action=edit&redlink=1)

``` html
/* LANGUAGE-TAG: CSS */
/* Set paragraph text to be very large. */
p { font-size: xx-large }

/* Set h1 (level 1 heading) text to be 2.5 times the size
 * of the text around it. */
h1 { font-size: 250% }

/* Sets text enclosed within span tag to be 16px */
span { font-size: 16px; }
```

``` html
//LANGUAGE-TAG: JavaScript
var ele = document.getElementyById("my-paragraph");
ele.style.fontSize = "small";
```

## Usage

There are several ways to specify the font size, with keywords or numerical values for pixels or ems. Choose the appropriate method based on the needs for the particular web page.

### Keywords

Keywords are a good way to set the size of fonts on the web. By setting a keyword font size on the body element, you can set relative font-sizing everywhere else on the page, giving you the ability to easily scale the font up or down on the entire page accordingly. Pixels

Setting the font size in pixel values (`px`) is a good choice when you need pixel accuracy. A `px` value is static. This is an OS-independent and cross-browser way of literally telling the browsers to render the letters at exactly the number of pixels in height that you specified. The results may vary slightly across browsers, as they may use different algorithms to achieve a similar effect.

Font sizing settings can also be used in combination. For example, if a parent element is set to `16px` and its child element is set to `larger`, the child element displays larger than the parent element in the page.

Note: Defining font sizes in pixel is *not accessible*, because the user cannot change the font size from the browser. (For example, users with limited vision may wish to set the font size much larger than the size chosen by a web designer.) Therefore, avoid using pixels for font sizes if you wish to create an inclusive design.

### Ems

Another way of setting the font size is with `em` values. The size of an `em` value is dynamic. When defining the `font-size` property, an `em` is equal to the size of the font that applies to the parent of the element in question. If you haven't set the font size anywhere on the page, then it is the browser default, which is probably 16px. So, by default 1em = 16px, and 2em = 32px. If you set a font-size of 20px on the body element, then 1em = 20px and 2em = 40px. Note that the value 2 is essentially a multiplier of the current `em` size.

In order to calculate the `em` equivalent for any pixel value required, you can use this formula:

``` css
em = desired element pixel value / parent element font-size in pixels
```

 For example, suppose the font-size of the body of the page is set to 1em, with the browser standard of 1em = 16px; if the font-size you want is 12px, then you should specify 0.75em (because 12/16 = 0.75). Similarly, if you want a font size of 10px, then specify 0.625em (10/16 = 0.625); for 22px, specify 1.375em (22/16).

A popular technique to use throughout the document is to set the the font-size of the body to 62.5% (that is 62.5% of the default of 16px), which equates to 10px, or 0.625em. Now you can set the font-size for any elements using em units, with an easy-to-remember conversion, by dividing the px value by 10. This way 6px = 0.6em, 8px = 0.8em, 12px = 1.2em, 14px = 1.4em, 16px = 1.6em. For example:

``` css
body {
  font-size: 62.5%; /* font-size 1em = 10px */
}
p {
  font-size: 1.6em; /* 1.6em = 16px */
}
```

 The em is a very useful unit in CSS, since it can adapt automatically to the font that the reader chooses to use.

## Notes

The `em` and `ex` units on the font-size property are relative to the parent element's font size (unlike all other properties, where they're relative to the font size on the element). This means em units and percentages do the same thing for font-size.

## Specifications

|Specification|Status|Relevant changes|
|:------------|:-----|:---------------|
|[CSS Fonts Module Level 3](http://dev.w3.org/csswg/css3-fonts/#font-size-prop)|Working Draft|No change|
|[CSS Transitions](http://dev.w3.org/csswg/css3-transitions/#animatable-css)|Working Draft|Defines `font-size` as animatable|
|[CSS 2 (Revision 1)](http://www.w3.org/TR/CSS2/fonts.html#propdef-font-size)|Recommendation|No change|
|[CSS Level 1](http://www.w3.org/TR/CSS1/#font-size)|Recommendation|Original specification|

## Browser Compatibility

### Desktop

|Feature|Chrome|Firefox (Gecko)|Internet Explorer|Opera|Safari|
|:------|:-----|:--------------|:----------------|:----|:-----|
|Basic support|5.0
4.0 <span style="border:1px solid black; padding:2px">-webkit</span>|[Template:CompatGeckoDesktop("1")](/w/index.php?title=Template:CompatGeckoDesktop(%221%22)&action=edit&redlink=1)|5.5|7.0|1.0|

***Implementation Note:** The prefix tag (here, a fake value just to show it off) would be a link to the concept of prefixes.*

### Mobile

|Feature|Android|Firefox Mobile (Gecko)|IE Phone|Opera Mobile|Safari Mobile|
|:------|:------|:---------------------|:-------|:-----------|:------------|
|Basic support|1.0|[Template:CompatGeckoMobile("1")](/w/index.php?title=Template:CompatGeckoMobile(%221%22)&action=edit&redlink=1)|6.0|6.0|1.0|

### Compatibility Notes

|Browser|Version|Note|
|:------|:------|:---|
|Internet Explorer|6+|When using the `!DOCTYPE` declaration to specify standards-compliant mode, the default value for this property is `medium`, not `small`.|
|Internet Explorer|4+|Possible length values specified in a relative measurement, using the height of the element's font (em) or the height of the letter "x" (ex)|

## See Also

### Related CSS Properties

-   ` font`
-   ` font-family`
-   ` font-size`
-   ` font-size-adjust`
-   ` font-stretch`
-   ` font-style`
-   ` font-variant`
-   ` font-weight`

### Related CSS At Rules

-   ` @font-face`

### Related DOM Interfaces

-   ` CSSStyleDeclaration`

### Related DOM properties

-   ` element.currentStyle`
-   ` element.defaults` *IE Only*

\<details\> \<summary\>This article contains content originally from external sources, including ones licensed under the CC-BY-SA license.\</summary\>

Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network: \<a href="<http://developer.mozilla.org/foo>" target="\_blank"\>Foo\</a\>

Portions of this content come from Foo.org: \<a href="<http://foo.org/baz>" target="\_blank"\>Baz\</a\>

\</details\>
