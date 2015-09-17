---
title: 'Node.appendChild()'
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - DOM/interfaces/examples/appendChild
    - DOM/interfaces/element/insertBefore
    - DOM/interfaces/element/replaceChild
    - DOM/interfaces/element/removeChild
    - DOM/concepts/document-model
uri: 'WPD:Example Pages/DOM Interface Leaf'

---
**This is a temporary page to pull together an example of what the ideal end state will be. It includes some content from MDN that is not compatible with the WPD license, and should be removed soon.**

Based on: <https://developer.mozilla.org/en-US/docs/DOM/Node.appendChild> and <http://msdn.microsoft.com/en-us/library/ie/ms535934(v=vs.85).aspx>

## Summary

Node.appendChild() adds a node to the end of the list of children of a specified parent node. If the node already exists it is removed from current parent node, then added to new parent node.

## Syntax

    var child=element.appendChild(child);

### Parameters

-   `element` is the parent element.
-   `child` is the node to append underneath `parent`. Also returned.

### Return Value

Returns `child`, the element that was appended.

## Examples

[View live examples](/w/index.php?title=DOM/interfaces/examples/appendChild&action=edit&redlink=1)

``` html
//LANGUAGE-TAG: JavaScript
//Create a div and append it to the body.
var oDiv=document.createElement("DIV");
document.body.appendChild(oDiv);
```

## Usage

If `child` is a reference to an existing node in the document, `appendChild` moves it from its current position to the new position (i.e. there is no requirement to remove the node from its parent node before appending it to some other node).

This also means that a node can't be in two points of the document simultaneously. So if the node already has a parent, it is first removed, then appended at the new position.

You can use **cloneNode** to make a copy of the node before appending it under the new parent. (Note that the copies made with **cloneNode** will not be automatically kept in sync.)

This method is not allowed to move nodes between different documents. If you want to **appendNode** from a different document (for example to display results from AJAX request) you must first use **importNode**.

**appendChild()** is one of the fundamental methods of web programming using the DOM. The **appendChild()** method inserts a new node into the DOM structure of a document, and is the second part of the one-two, create-and-append process so central to building web pages programmatically.

This method is accessible at run time. If elements are removed at run time, before the closing tag is parsed, areas of the document might not render.

## Specifications

|Specification|Status|Relevant changes|
|:------------|:-----|:---------------|
|[DOM Level 3 Core](http://www.w3.org/TR/DOM-Level-3-Core/core.html#ID-184E7107)|Recommendation|Original specification|

## Browser Compatibility

**Implementation Note**: Would have the Compatibility\_Incomplete flag

**Implementation Note:** : Supported (when?) should ideally be a template or something we can query on, low priority.

### Desktop

|Feature|Chrome|Firefox (Gecko)|Internet Explorer|Opera|Safari|
|:------|:-----|:--------------|:----------------|:----|:-----|
|Basic support|Supported (when?)|Supported (when?)|Supported (when?)|Supported(when?)|Supported(when?)|

### Mobile

|Feature|Android|Firefox Mobile (Gecko)|IE Phone|Opera Mobile|Safari Mobile|
|:------|:------|:---------------------|:-------|:-----------|:------------|
|Basic support|Supported (when?)|Supported (when?)|Supported (when?)|Supported (when?)|Supported (when?)|

### Compatibility Notes

|Browser|Version|Note|
|:------|:------|:---|
|Internet Explorer|6+|This method now applies to the attribute object.|
|Internet Explorer|9+|Exceptions are only supported when webpages are displayed in IE9 Standards mode.|

## See Also

**Implementation Note**: These should be auto-generated via tags.

### Related DOM Methods

-   ` insertBefore`
-   ` replaceChild`
-   ` removeChild`

### Related DOM Concepts

-   [About the DOM object model](/w/index.php?title=DOM/concepts/document-model&action=edit&redlink=1)

\<details\> \<summary\>This article contains content originally from external sources, including ones licensed under the CC-BY-SA license.\</summary\>

Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network: \<a href="<http://developer.mozilla.org/foo>" target="\_blank"\>Foo\</a\>

Portions of this content come from Foo.org: \<a href="<http://foo.org/baz>" target="\_blank"\>Baz\</a\>

\</details\>
