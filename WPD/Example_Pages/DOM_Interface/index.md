---
title: Element
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - DOM/interfaces/HTMLElement
    - DOM/interfaces/SVGElement
    - DOM/interface/node
    - DOM/interface/HTMLElement
    - DOM/interface/SVGElement
    - DOM/interfaces/Element/properties/children
    - DOM/interfaces/Element/properties/parentNode
    - DOM/interfaces/Element/methods/insertBefore
    - DOM/interfaces/Element/methods/replaceChild
    - DOM/interfaces/element/insertBefore
    - DOM/interfaces/element/replaceChild
    - DOM/interfaces/element/removeChild
    - DOM/concepts/document-model
uri: 'WPD:Example Pages/DOM Interface'

---
**This is a temporary page to pull together an example of what the ideal end state will be. It includes some content from MDN that is not compatible with the WPD license, and should be removed soon.**

Based on: <https://developer.mozilla.org/en-US/docs/DOM/Element> and <http://msdn.microsoft.com/en-us/library/ie/hh772117(v=vs.85).aspx>

## <span>Summary</span>

Element is a DOM interface that forms the basis of the API for DOM objects. Other interfaces, like [HTMLElement](/w/index.php?title=DOM/interfaces/HTMLElement&action=edit&redlink=1) or [SVGElement](/w/index.php?title=DOM/interfaces/SVGElement&action=edit&redlink=1), will sub-class from Element and add new parts of the API.

## <span>Overview Table</span>

**Implementation note**: The *Others...* should be a template that calls out that this is a work item. Slash just include them automatically.

||
|Inherits from|` Node`|
|Sub-interfaces|` HTMLElement`, ` SVGElement`, *Incomplete list...*|

## <span>Properties</span>

**Implementation Note**: The summaries would be automatically transcluded from the page

**Implementation Note**: The list of these would be automatically generated.

|Name|Summary|
|:---|:------|
|` children`|Children is all of the children of a node.|
|` parentNode`|parentNode is the parent of the node.|
|*Many, many others...*||

## <span>Methods</span>

**Implementation Note**: The summaries would be automatically transcluded from the page

**Implementation Note**: The list of these would be automatically generated.

|Name|Summary|
|:---|:------|
|`appendChild(element) `|Node.appendChild() adds a node to the end of the list of children of a specified parent node. If the node already exists it is removed from current parent node, then added to new parent node.|
|` insertBefore(element)`|Node.appendChild() adds a node to the end of the list of children of a specified parent node. If the node already exists it is removed from current parent node, then added to new parent node.|
|` replaceChild(element)`|Node.appendChild() adds a node to the end of the list of children of a specified parent node. If the node already exists it is removed from current parent node, then added to new parent node.|
|*Many, many others...*||

## <span>Events</span>

``` html
//LANGUAGE-TAG: JavaScript
//Create a div and append it to the body.
var oDiv=document.createElement("DIV");
document.body.appendChild(oDiv);
```

## <span>Usage</span>

If `child</child> is a reference to an existing node in the document, <code>appendChild` moves it from its current position to the new position (i.e. there is no requirement to remove the node from its parent node before appending it to some other node).

This also means that a node can't be in two points of the document simultaneously. So if the node already has a parent, it is first removed, then appended at the new position.

You can use **cloneNode** to make a copy of the node before appending it under the new parent. (Note that the copies made with **cloneNode** will not be automatically kept in sync.)

This method is not allowed to move nodes between different documents. If you want to **appendNode** from a different document (for example to display results from AJAX request) you must first use **importNode**.

**appendChild()** is one of the fundamental methods of web programming using the DOM. The **appendChild()** method inserts a new node into the DOM structure of a document, and is the second part of the one-two, create-and-append process so central to building web pages programmatically.

This method is accessible at run time. If elements are removed at run time, before the closing tag is parsed, areas of the document might not render.

## <span>Specifications</span>

|Specification|Status|Relevant changes|
|:------------|:-----|:---------------|
|[DOM Level 3 Core](http://www.w3.org/TR/DOM-Level-3-Core/core.html#ID-184E7107)|Recommendation|Original specification|

## <span>Browser Compatibility</span>

**Implementation Note**: Would have the Compatibility\_Incomplete flag

### <span>Desktop</span>

|Feature|Chrome|Firefox (Gecko)|Internet Explorer|Opera|Safari|
|:------|:-----|:--------------|:----------------|:----|:-----|
|Basic support|Supported (when?)|Supported (when?)|Supported (when?)|Supported(when?)|Supported(when?)|

### <span>Mobile</span>

|Feature|Android|Firefox Mobile (Gecko)|IE Phone|Opera Mobile|Safari Mobile|
|:------|:------|:---------------------|:-------|:-----------|:------------|
|Basic support|Supported (when?)|Supported (when?)|Supported (when?)|Supported (when?)|Supported (when?)|

### <span>Compatibility Notes</span>

|Browser|Version|Note|
|:------|:------|:---|
|Internet Explorer|6+|This method now applies to the attribute object.|
|Internet Explorer|9+|Exceptions are only supported when webpages are displayed in IE9 Standards mode.|

## <span>See Also</span>

**Implementation Note**: These should be auto-generated via tags.

### <span>Related DOM Methods</span>

-   ` insertBefore`
-   ` replaceChild`
-   ` removeChild`

### <span>Related DOM Concepts</span>

-   [About the DOM object model](/w/index.php?title=DOM/concepts/document-model&action=edit&redlink=1)

\<details\> \<summary\>This article contains content originally from external sources, including ones licensed under the CC-BY-SA license.\</summary\>

Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network: \<a href="<http://developer.mozilla.org/foo>" target="\_blank"\>Foo\</a\>

Portions of this content come from Foo.org: \<a href="<http://foo.org/baz>" target="\_blank"\>Baz\</a\>

\</details\>