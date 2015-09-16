---
title: CSS Coding Guidelines
summary: "These guidelines aim to produce consistent coding style throughout all CSS examples on WebPlatform Docs.\n"
tags:
  - Basic
  - Pages
  - CSS
uri: 'WPD:Content/coding guidelines/css'

---
## Summary

These guidelines aim to produce consistent coding style throughout all CSS examples on WebPlatform Docs.

This article is based on Idiomatic CSS, a repository created by Nicolas Gallagher: <https://github.com/necolas/idiomatic-css>

## General Principles

> "Part of being a good steward to a successful project is realizing that writing code for yourself is a Bad Idea™. If thousands of people are using your code, then write your code for maximum clarity, not your personal preference of how to get clever within the spec." - Idan Gazit

-   You are not a human code compiler/compressor, so do not try to be one.
-   All code in any code-base should look like a single person typed it, no matter how many people contributed.
-   Strictly enforce the agreed upon style.
-   If in doubt when deciding upon a style, use existing, common patterns.

## Whitespace

Only one style should exist across the entire source of your code-base. Always be consistent in your use of whitespace. Use whitespace to improve readability.

-   Use soft indents (spaces).
-   Indent two spaces to maximize the amount of meaningful information per line.

## Comments

-   Place comments on a new line above their subject.
-   Avoid end of line comments.
-   Keep line-length to a sensible maximum, such as 80 columns.
-   Make liberal use of comments to break CSS code into discrete sections.
-   Use "sentence case" comments and consistent text indentation.

``` css
/* ==========================================================================
   Section comment block
   ========================================================================== */

/* Sub-section comment block
   ========================================================================== */

/**
 * Short description using Doxygen-style comment format
 *
 * Long description first sentence starts here and continues on this line for a
 * while finally concluding here at the end of this paragraph.
 *
 * The long description is ideal for more detailed explanations and
 * documentation. It can include example HTML, URLs, or any other information
 * that is deemed necessary or useful.
 *
 * @tag This is a tag named 'tag'
 *
 * @todo This is a todo statement that describes an atomic task to be completed
 *   at a later date. It wraps after 80 characters and following lines are
 *   indented by 2 spaces.
 */

/* Basic comment */
```

## Format

-   Use one discrete selector per line in multi-selector rulesets.
-   Include a single space before the opening brace of a ruleset.
-   Include one declaration per line in a declaration block.
-   Use one level of indentation for each declaration.
-   Include single space after the colon of a declaration.
-   Use lowercase and shorthand hex values, such as `#aaa`.
-   Use double quotes, like this `content: ""`.
-   Quote attribute values in selectors, such as `input[type="checkbox"]`.
-   Where allowed, avoid specifying units for zero-values, like this: `margin: 0`.
-   Include a space after each comma in comma-separated property or function values.
-   Include a semi-colon at the end of the last declaration in a declaration block.
-   Place the closing brace of a ruleset in the same column as the first character of the ruleset.
-   Separate each ruleset by a blank line.

``` css
.selector-1,
.selector-2,
.selector-3[type="text"] {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  display: block;
  font-family: helvetica, arial, sans-serif;
  color: #333;
  background: #fff;
  background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}
```

### Declaration order

Declarations should be ordered in accordance with a single principle. Structurally important properties are declared prior to all others:

1.  Position;
2.  Box Model (Dimension);
3.  Font;
4.  Text;
5.  Others;
6.  Animation.

``` css
.selector {
  /* Position */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 10;

  /* Display & Box Model */
  display: inline-block;
  overflow: hidden;
  box-sizing: border-box;
  width: 100px;
  height: 100px;
  padding: 10px;
  border: 10px solid #333;
  margin: 10px;

  /* Font */
  font-family: sans-serif;
  font-size: 16px;

  /* Text */
  text-align: right;

  /* Colors */
  color: #fff;
  background: #000;

  /* Others */
  cursor: pointer;

  /* Animation */
  transition-property: all;
  transition-duration: .25s;
}
```

 Strict alphabetical ordering is also relatively popular, but the drawback is that it separates related properties. For example, position offsets are no longer grouped together and box-model properties can end up spread throughout a declaration block.

### Exceptions and slight deviations

Large blocks of single declarations can use a slightly different, single-line format. In this case, a space should be included after the opening brace and before the closing brace.

``` css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

 Long, comma-separated property values - such as collections of gradients or shadows - can be arranged across multiple lines in an effort to improve readability and produce more useful diffs. There are various formats that could be used; one example is shown below.

``` css
.selector {
  background-image:
    linear-gradient(#fff, #ccc),
    linear-gradient(#f3c, #4ec);
  box-shadow:
    1px 1px 1px #000,
    2px 2px 1px 1px #ccc inset;
}
```

## Naming

Naming is hard, but it is very important. It is a crucial part of the process of developing a maintainable code base, and ensuring that you have a relatively scalable interface between your HTML and CSS.

-   Avoid systematic use of abbreviated class names. Do not make things difficult to understand.
-   Use clear, thoughtful, and appropriate names for HTML classes.
-   Pick an understandable and consistent naming pattern that makes sense both within HTML files and CSS files.
-   Selectors for components should uses class names; avoid the use of generic tags and unique ids.

``` css
/* Example of code with bad names */
.s-scr {
  overflow: auto;
}

.cb {
  background: #000;
}

/* Example of code with better names */
.is-scrollable {
  overflow: auto;
}

.column-body {
  background: #000;
}
```

## Practical example

``` css
/* ==========================================================================
   Grid layout
   ========================================================================== */

/**
  * Example HTML:
  *
  * <div class="grid">
  *   <div class="cell cell-5"></div>
  *   <div class="cell cell-5"></div>
  * </div>
  */

.grid {
  overflow: visible;
  height: 100%;
  /* Prevent inline-block cells wrapping */
  white-space: nowrap;
  /* Remove inter-cell whitespace */
  font-size: 0;
}

.cell {
  position: relative;
  display: inline-block;
  overflow: hidden;
  box-sizing: border-box;
  width: 20%;
  height: 100%;
  /* Set the inter-cell spacing */
  padding: 0 10px;
  border: 2px solid #333;
  vertical-align: top;
  /* Reset white-space */
  white-space: normal;
  /* Reset font-size */
  font-size: 16px;
}

/* Cell states */

.cell.is-animating {
  background-color: #fffdec;
}

/* Cell dimensions
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Cell modifiers
   ========================================================================== */

.cell--detail,
.cell--important {
  border-width: 4px;
}
```
