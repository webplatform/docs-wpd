---
title: WPD:Example Pages/DOM Interface Leaf
path: Example_Pages/DOM_Interface_Leaf

---
<p><b>This is a temporary page to pull together an example of what the ideal end state will be. It includes some content from MDN that is not compatible with the WPD license, and should be removed soon.</b>
</p><p>Based on: <a rel="nofollow" class="external free" href="https://developer.mozilla.org/en-US/docs/DOM/Node.appendChild">https://developer.mozilla.org/en-US/docs/DOM/Node.appendChild</a> and <a rel="nofollow" class="external free" href="http://msdn.microsoft.com/en-us/library/ie/ms535934(v=vs.85).aspx">http://msdn.microsoft.com/en-us/library/ie/ms535934(v=vs.85).aspx</a>
</p>
<h1><span class="mw-headline" id="Node.appendChild.28.29">Node.appendChild()</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>Node.appendChild() adds a node to the end of the list of children of a specified parent node. If the node already exists it is removed from current parent node, then added to new parent node.
</p>
<h2><span class="mw-headline" id="Syntax">Syntax</span></h2>
<pre>var child=<i>element</i>.appendChild(<i>child</i>);
</pre>
<h3><span class="mw-headline" id="Parameters">Parameters</span></h3>
<ul><li> <code>element</code> is the parent element.</li>
<li> <code>child</code> is the node to append underneath <code>parent</code>. Also returned.</li></ul>
<h3><span class="mw-headline" id="Return_Value">Return Value</span></h3>
<p>Returns <code>child</code>, the element that was appended.
</p>
<h2><span class="mw-headline" id="Examples">Examples</span></h2>
<p><a href="/w/index.php?title=DOM/interfaces/examples/appendChild&amp;action=edit&amp;redlink=1" class="new" title="DOM/interfaces/examples/appendChild (page does not exist)"> View live examples</a>
</p><p><br />
</p>
<pre class="language-html5" data-lang="html5">
//LANGUAGE-TAG: JavaScript
//Create a div and append it to the body.
var oDiv=document.createElement("DIV");
document.body.appendChild(oDiv);
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="Usage">Usage</span></h2>
<p>If <code>child</code> is a reference to an existing node in the document, <code>appendChild</code> moves it from its current position to the new position (i.e. there is no requirement to remove the node from its parent node before appending it to some other node).
</p><p>This also means that a node can't be in two points of the document simultaneously. So if the node already has a parent, it is first removed, then appended at the new position.
</p><p>You can use <b>cloneNode</b> to make a copy of the node before appending it under the new parent. (Note that the copies made with <b>cloneNode</b> will not be automatically kept in sync.)
</p><p>This method is not allowed to move nodes between different documents. If you want to <b>appendNode</b> from a different document (for example to display results from AJAX request) you must first use <b>importNode</b>.
</p><p><b>appendChild()</b> is one of the fundamental methods of web programming using the DOM. The <b>appendChild()</b> method inserts a new node into the DOM structure of a document, and is the second part of the one-two, create-and-append process so central to building web pages programmatically.
</p><p>This method is accessible at run time. If elements are removed at run time, before the closing tag is parsed, areas of the document might not render.
</p>
<h2><span class="mw-headline" id="Specifications">Specifications</span></h2>
<table class="wikitable">

<tr>
<th> Specification </th>
<th> Status </th>
<th> Relevant changes
</th></tr>
<tr>
<td> <a rel="nofollow" class="external text" href="http://www.w3.org/TR/DOM-Level-3-Core/core.html#ID-184E7107">DOM Level 3 Core</a> </td>
<td> Recommendation </td>
<td> Original specification
</td></tr></table>
<h2><span class="mw-headline" id="Browser_Compatibility">Browser Compatibility</span></h2>
<p><b>Implementation Note</b>: Would have the Compatibility_Incomplete flag
</p><p><b>Implementation Note:</b>&#160;: Supported (when?) should ideally be a template or something we can query on, low priority.
</p>
<h3><span class="mw-headline" id="Desktop">Desktop</span></h3>
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
<h3><span class="mw-headline" id="Mobile">Mobile</span></h3>
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
<h3><span class="mw-headline" id="Compatibility_Notes">Compatibility Notes</span></h3>
<table class="wikitable">
<tr>
<th> Browser
</th>
<th> Version
</th>
<th> Note
</th></tr>
<tr>
<td> Internet Explorer
</td>
<td> 6+
</td>
<td>This method now applies to the attribute object.
</td></tr>
<tr>
<td> Internet Explorer
</td>
<td> 9+
</td>
<td> Exceptions are only supported when webpages are displayed in IE9 Standards mode.
</td></tr></table>
<h2><span class="mw-headline" id="See_Also">See Also</span></h2>
<p><b>Implementation Note</b>: These should be auto-generated via tags.
</p>
<h3><span class="mw-headline" id="Related_DOM_Methods">Related DOM Methods</span></h3>
<ul><li> <code><a href="/w/index.php?title=DOM/interfaces/element/insertBefore&amp;action=edit&amp;redlink=1" class="new" title="DOM/interfaces/element/insertBefore (page does not exist)"> insertBefore</a></code></li>
<li> <code><a href="/w/index.php?title=DOM/interfaces/element/replaceChild&amp;action=edit&amp;redlink=1" class="new" title="DOM/interfaces/element/replaceChild (page does not exist)"> replaceChild</a></code></li>
<li> <code><a href="/w/index.php?title=DOM/interfaces/element/removeChild&amp;action=edit&amp;redlink=1" class="new" title="DOM/interfaces/element/removeChild (page does not exist)"> removeChild</a></code></li></ul>
<h3><span class="mw-headline" id="Related_DOM_Concepts">Related DOM Concepts</span></h3>
<ul><li> <a href="/w/index.php?title=DOM/concepts/document-model&amp;action=edit&amp;redlink=1" class="new" title="DOM/concepts/document-model (page does not exist)"> About the DOM object model</a></li></ul>
<p>&lt;details&gt;
	&lt;summary&gt;This article contains content originally from external sources, including ones licensed under the CC-BY-SA license.&lt;/summary&gt;
</p>
	<div>
<p>		Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network:
&lt;a href="<a rel="nofollow" class="external free" href="http://developer.mozilla.org/foo">http://developer.mozilla.org/foo</a>" target="_blank"&gt;Foo&lt;/a&gt;
</p>
	</div>
	<div>
<p>		Portions of this content come from Foo.org: &lt;a href="<a rel="nofollow" class="external free" href="http://foo.org/baz">http://foo.org/baz</a>" target="_blank"&gt;Baz&lt;/a&gt;
</p>
	</div>
<p>&lt;/details&gt;
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:199-0!*!0!!*!*!*!esi=1 and timestamp 20150810195934 and revision id 662
 -->
