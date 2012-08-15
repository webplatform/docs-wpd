'''This is a temporary page to pull together an example of what the ideal end state will be. It includes some content from MDN that is not compatible with the WPD license, and should be removed soon.'''
=Node.appendChild()=
==Summary==
Node.appendChild() adds a node to the end of the list of children of a specified parent node. If the node already exists it is removed from current parent node, then added to new parent node.

==Syntax==
 var child=''element''.appendChild(''child'');

===Parameters===
* <code>element</code> is the parent element.
* <code>child</code> is the node to append underneath <code>parent</code>. Also returned.

===Return Value===
Returns <code>child</code>, the element that was appended.

==Examples==
[[DOM/interfaces/examples/appendChild | View live examples]]

<syntaxhighlight>
//LANGUAGE-TAG: JavaScript
//Create a div and append it to the body.
var oDiv=document.createElement("DIV");
document.body.appendChild(oDiv);
</syntaxhighlight>

==Usage==

If <code>child</child> is a reference to an existing node in the document, <code>appendChild</code> moves it from its current position to the new position (i.e. there is no requirement to remove the node from its parent node before appending it to some other node).

This also means that a node can't be in two points of the document simultaneously. So if the node already has a parent, it is first removed, then appended at the new position.

You can use '''cloneNode''' to make a copy of the node before appending it under the new parent. (Note that the copies made with '''cloneNode''' will not be automatically kept in sync.)

This method is not allowed to move nodes between different documents. If you want to '''appendNode''' from a different document (for example to display results from AJAX request) you must first use '''importNode'''.

'''appendChild()''' is one of the fundamental methods of web programming using the DOM. The '''appendChild()''' method inserts a new node into the DOM structure of a document, and is the second part of the one-two, create-and-append process so central to building web pages programmatically.

This method is accessible at run time. If elements are removed at run time, before the closing tag is parsed, areas of the document might not render.

==Specifications==
{| class="wikitable"
|-
! Specification !! Status !! Relevant changes
|-
| [http://www.w3.org/TR/DOM-Level-3-Core/core.html#ID-184E7107 DOM Level 3 Core] || Recommendation || Original specification
|}

==Browser Compatibility==
'''Implementation Note''': Would have the Compatibility_Incomplete flag
===Desktop===
<div id="compat-desktop">
  <table class="compat-table">
       <tr>
        <th>Feature</th>
        <th>Chrome</th>
        <th>Firefox (Gecko)</th>
        <th>Internet Explorer</th>
        <th>Opera</th>
        <th>Safari</th>
      </tr>
      <tr>
        <td>Basic support</td>
        <td>Supported (when?)</td>
        <td>Supported (when?)</td>
        <td>Supported (when?)</td>
        <td>Supported(when?)</td>
        <td>Supported(when?)</td>
      </tr>
  </table>
</div>

===Mobile===
<div id="compat-mobile">
  <table class="compat-table">
      <tr>
        <th>Feature</th>
        <th>Android</th>
        <th>Firefox Mobile (Gecko)</th>
        <th>IE Phone</th>
        <th>Opera Mobile</th>
        <th>Safari Mobile</th>
      </tr>
      <tr>
        <td>Basic support</td>
        <td>Supported (when?)</td>
        <td>Supported (when?)</td>
        <td>Supported (when?)</td>
        <td>Supported (when?)</td>
        <td>Supported (when?)</td>
      </tr>
  </table>
</div>

===Compatibility Notes===

{| class="wikitable"
! Browser
! Version
! Note
|-
| Internet Explorer
| 6+ 
|When using the <code>!DOCTYPE</code> declaration to specify standards-compliant mode, the default value for this property is <code>medium</code>, not <code>small</code>.
|-
| Internet Explorer 
| 4+
| Possible length values specified in a relative measurement, using the height of the element's font (em) or the height of the letter "x" (ex)
|}

==See Also==
Related methods: insertBefore, replaceChild and removeChild.
===Related CSS Properties===
* <code>[[CSS/properties/font | font]]</code>
* <code>[[CSS/properties/font-family | font-family]]</code>
* <code>[[CSS/properties/font-size | font-size]]</code>
* <code>[[CSS/properties/font-size-adjust | font-size-adjust]]</code>
* <code>[[CSS/properties/font-stretch | font-stretch]]</code>
* <code>[[CSS/properties/font-style | font-style]]</code>
* <code>[[CSS/properties/font-variant | font-variant]]</code>
* <code>[[CSS/properties/font-weight | font-weight]]</code>

===Related CSS At Rules===
* <code>[[CSS/atrules/@font-face | @font-face]]</code>

===Related DOM Interfaces===
* <code>[[DOM/element/CSSStyleDeclaration | CSSStyleDeclaration]]</code>

===Related DOM properties===
* <code>[[DOM/element/properties/currentStyle | element.currentStyle]]</code>
* <code>[[DOM/element/properties/defaults | element.defaults]]</code> ''IE Only''

<details>
	<summary>This article contains content originally from external sources, including ones licensed under the CC-BY-SA license.</summary>
	<div>
		Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network:
<a href="http://developer.mozilla.org/foo" target="_blank">Foo</a>
	</div>
	<div>
		Portions of this content come from Foo.org: <a href="http://foo.org/baz" target="_blank">Baz</a>
	</div>
</details>