---
title: WPD:Example Pages/Event
path: Example_Pages/Event

---
<p><b>This is a temporary page to pull together an example of what the ideal end state will be. It includes some content from MDN that is not compatible with the WPD license, and should be removed soon.</b>
Draws from:
</p>
<ul><li> <a rel="nofollow" class="external free" href="https://developer.mozilla.org/en-US/docs/DOM/DOM_event_reference/mouseenter">https://developer.mozilla.org/en-US/docs/DOM/DOM_event_reference/mouseenter</a></li>
<li> <a rel="nofollow" class="external free" href="https://developer.mozilla.org/en-US/docs/DOM/MouseEvent">https://developer.mozilla.org/en-US/docs/DOM/MouseEvent</a></li>
<li> <a rel="nofollow" class="external free" href="http://msdn.microsoft.com/en-us/library/ie/ms536913%28v=vs.85%29.aspx">http://msdn.microsoft.com/en-us/library/ie/ms536913%28v=vs.85%29.aspx</a></li></ul>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>The <code>click</code> event type is dispatched when the user activates the primary pointer indicator (e.g., the left mouse button) on an element.
</p>
<h2><span class="mw-headline" id="Syntax">Syntax</span></h2>
<table class="wikitable">
<tr>
<th>
</th>
<th> Keyword
</th>
<th> Sample Usage
</th></tr>
<tr>
<th> Event Type
</th>
<td> <code>click</code>
</td>
<td> <code>object.addEventListener("click", handler, useCapture);</code>
</td></tr>
<tr>
<th> Event Attribute
</th>
<td> <code>onclick</code>
</td>
<td> <code>&lt;element onclick = "handler(event)"&gt;</code>
</td></tr>
<tr>
<th> Event Property
</th>
<td> <code>onclick</code>
</td>
<td> <code>object.onclick = handler;</code>
</td></tr></table>
<h2><span class="mw-headline" id="Event_Properties">Event Properties</span></h2>
<table class="wikitable">
<tr>
<th> Interface
</th>
<td> <a href="/w/index.php?title=MouseEvent&amp;action=edit&amp;redlink=1" class="new" title="MouseEvent (page does not exist)">MouseEvent</a>
</td></tr>
<tr>
<th> Synchronous
</th>
<td> Yes
</td></tr>
<tr>
<th> Bubbles
</th>
<td> No
</td></tr>
<tr>
<th> Target
</th>
<td> <a href="/w/index.php?title=Element&amp;action=edit&amp;redlink=1" class="new" title="Element (page does not exist)">Element</a>
</td></tr>
<tr>
<th> Cancelable
</th>
<td> No
</td></tr>
<tr>
<th> Default action
</th>
<td> None
</td></tr></table>
<h2><span class="mw-headline" id="Interface">Interface</span></h2>
<p>The <code>click</code> event type uses the <code>MouseEvent</code> interface.
</p><p><i><b>Implementation Note:</b> begin transclusion of <code>MouseEvent</code> interface.</i>
</p>
<table class="wikitable">
<tr>
<th> Property
</th>
<th> Type
</th>
<th> Description
</th>
<th> Read only
</th></tr>
<tr>
<td> screenX
</td>
<td> long
</td>
<td> The X coordinate of the mouse pointer in global (screen) coordinates.
</td>
<td> Yes
</td></tr>
<tr>
<td> screenY
</td>
<td> long
</td>
<td> The Y coordinate of the mouse pointer in global (screen) coordinates.
</td>
<td> Yes
</td></tr>
<tr>
<td> clientX
</td>
<td> long
</td>
<td> The X coordinate of the mouse pointer in local (DOM content) coordinates.
</td>
<td> Yes
</td></tr>
<tr>
<td> clientY
</td>
<td> long
</td>
<td> The Y coordinate of the mouse pointer in local (DOM content) coordinates.
</td>
<td> Yes
</td></tr>
<tr>
<td> ctrlKey
</td>
<td> boolean
</td>
<td> true if the control key was down when the mouse event was fired.
</td>
<td> Yes
</td></tr>
<tr>
<td> shiftKey
</td>
<td> boolean
</td>
<td> true if the shift key was down when the mouse event was fired.
</td>
<td> Yes
</td></tr>
<tr>
<td> altKey
</td>
<td> boolean
</td>
<td> true if the alt key was down when the mouse event was fired.
</td>
<td> Yes
</td></tr>
<tr>
<td> metaKey
</td>
<td> boolean
</td>
<td> true if the meta key was down when the mouse event was fired.
</td>
<td> Yes
</td></tr>
<tr>
<td> button
</td>
<td> unsigned short
</td>
<td> The button number that was pressed when the mouse event was fired: Left button=0, middle button=1 (if present), right button=2. For mice configured for left handed use in which the button actions are reversed the values are instead read from right to left.
</td>
<td> Yes
</td></tr>
<tr>
<td> buttons
</td>
<td> unsigned short
</td>
<td> The buttons being pressed when the mouse event was fired: Left button=1, Right button=2, Middle (wheel) button=4, 4th button (typically, "Browser Back" button)=8, 5th button (typically, "Browser Forward" button)=16. If two or more buttons are pressed, returns the logical sum of the values. E.g., if Left button and Right button are pressed, returns 3 (=1 | 2).
</td>
<td> Yes
</td></tr>
<tr>
<td> relatedTarget
</td>
<td> nsIDOMEventTarget
</td>
<td> The target to which the event applies.
</td>
<td> Yes
</td></tr>
<tr>
<td> mozPressure
<pre> <b>Non-standard</b>
</pre>
</td>
<td> float
</td>
<td> The amount of pressure applied to a touch or tablet device when generating the event; this value ranges between 0.0 (minimum pressure) and 1.0 (maximum pressure).
</td>
<td> Yes
</td></tr></table>
<h3><span class="mw-headline" id="Methods">Methods</span></h3>
<pre>boolean getModifierState(in DOMString keyArg);
</pre>
<h4><span class="mw-headline" id="getModifierState.28.29">getModifierState()</span></h4>
<p>Returns the current state of the specified modifier key. See the document of KeyboardEvent.getModifierState() for the detail. 
</p><p><b>DOM level 3 Requires Gecko 15.0</b>?
</p>
<pre>boolean getModifierState(
  in DOMString keyArg
);
</pre>
<p><i><b>Implementation Note:</b> end transclusion of <code>MouseEvent</code> interface.</i>
</p>
<h2><span class="mw-headline" id="Examples">Examples</span></h2>
<p><a href="/w/index.php?title=Event/examples/click&amp;action=edit&amp;redlink=1" class="new" title="Event/examples/click (page does not exist)"> View live examples</a>
</p>
<h3><span class="mw-headline" id="Example:_Click_Event_Origin">Example: Click Event Origin</span></h3>
<p>This example uses the event object to gain information about the origin of the click. In addition, it cancels the default action to prevent navigation of anchor elements, unless the SHIFT key is pressed. Normally a Shift+Click opens the target of a link in a new window; however, the script replaces the current document by setting the location of the window object.
</p><p><a href="/w/index.php?title=See_live_example&amp;action=edit&amp;redlink=1" class="new" title="See live example (page does not exist)">See live example</a>
</p><p><br />
</p>
<pre class="language-html5" data-lang="html5">
<script type="text/javascript">
/* This code cancels the event. If the click occurs in an anchor
   and the SHIFT key is down, the document is navigated. */
function clickIt()  
{
    var e = window.event.srcElement
    txtName.value = e.tagName;
    txtType.value = e.type;
    if ((e.tagName == "A") &amp;&amp; 
        (window.event.shiftKey)) {
        window.location.href = e.href;
    }
    
    window.event.returnValue = false; 
}
</script>
<body onclick="clickIt()">
<p>To follow a link, click while pressing the SHIFT key.</p>
<p><a href="about:blank">Click Here</a>
<textarea name="txtName"></textarea> <textarea name="txtType"></textarea>
</body>
</p>
</pre>
<p><br />
</p>
<h3><span class="mw-headline" id="Example:_Binding_the_Click_Event_to_Controls">Example: Binding the Click Event to Controls</span></h3>
<p>This example shows how to bind the <code>click</code> event to grouped controls.
</p><p><a href="/w/index.php?title=See_live_example&amp;action=edit&amp;redlink=1" class="new" title="See live example (page does not exist)">See live example</a>
</p><p><br />
</p>
<pre class="language-html5" data-lang="html5">
<head>
<script type="text/javascript">
function CookieGroup() 
{
txtOutput.value = window.event.srcElement.value;
}
</script>
</head>
<body>
<!-- Controls are grouped by giving them the same NAME but unique IDs. -->
<p>Grouped Radio Buttons<br>
<input type="radio" 
    name="rdoTest" 
    id="Cookies" 
    value="accept_cookies" 
    checked 
    onclick="CookieGroup()"><br>
<input type="radio" 
    name="rdoTest" 
    id="NoCookies" 
    value="refuse_cookies" 
    onclick="CookieGroup()"><br>
</p>
<p>Ungrouped Radio Button<br>
<input type="radio" 
    name="rdoTest1" 
    value="chocolate-chip_cookies" 
    onclick="CookieGroup()"><br>
</p>
<p>Value of control on which the onclick event has fired<br>
<textarea name="txtOutput" style="width: 250px"></textarea> </p>
<p></body>
</p>
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="Usage">Usage</span></h2>
<p>If the user clicks the left mouse button, the <code>click</code> event for an object occurs only if the mouse pointer is over the object and an <code>mousedown</code> and an <code>mouseup</code> event occur in that order. For example, if the user clicks the mouse on the object but moves the mouse pointer away from the object before releasing, no <code>click</code> event occurs.
</p><p>The <code>click</code> event changes the value of a control in a group. This change initiates the event for the group, not for the individual control. For example, if the user clicks a radio button or check box in a group, the <code>click</code> event occurs after the <code>beforeupdate</code> and <code>afterupdate</code> events for the control group.
</p><p>If the user clicks an object that can receive the input focus but does not already have the focus, the <code>focus</code> event occurs for that object before the <code>click</code> event. If the user double-clicks the left mouse button in a control, an <code>dblclick</code> event occurs immediately after the <code>click</code> event.
</p><p>Although the <code>click</code> event is available on a large number of HTML elements, if a document is to be accessible to keyboard users, you should restrict its use to the a, input, area, and button elements. These elements automatically allow keyboard access through the TAB key, making documents that use the elements accessible to keyboard users. For more information, please see the section on writing accessible Dynamic HTML.
</p><p>Initiates any action associated with the object. For example, if the user clicks an a object, the client loads the document specified by the href property. To cancel the default behavior, set the returnValue property of the event object to FALSE.
</p><p>To invoke this event, do one of the following:
</p>
<ul><li> Click the object.</li>
<li> Invoke the <code>click</code> method.</li>
<li> Press the ENTER key in a form.</li>
<li> Press the access key for a control.</li>
<li> Select an item in a combo box or list box by clicking the left mouse button or by pressing the arrow keys and then pressing the ENTER key.</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Notes">Notes</span></h2>
<p>None.
</p>
<h2><span class="mw-headline" id="Specifications">Specifications</span></h2>
<table class="wikitable">

<tr>
<th> Specification </th>
<th> Status </th>
<th> Relevant changes
</th></tr>
<tr>
<td> <a href="/w/index.php?title=HTML5&amp;action=edit&amp;redlink=1" class="new" title="HTML5 (page does not exist)">HTML5</a> </td>
<td> Working Draft </td>
<td> <i>list changes</i> (onclick attribute)
</td></tr>
<tr>
<td> <a href="/w/index.php?title=DOM_3_Events:_MouseEvent&amp;action=edit&amp;redlink=1" class="new" title="DOM 3 Events: MouseEvent (page does not exist)">DOM 3 Events: MouseEvent</a> </td>
<td> Working Draft </td>
<td> <i>list changes</i>
</td></tr>
<tr>
<td> <a href="/w/index.php?title=DOM_Level_2:_MouseEvent&amp;action=edit&amp;redlink=1" class="new" title="DOM Level 2: MouseEvent (page does not exist)">DOM Level 2: MouseEvent</a> </td>
<td> Recommendation </td>
<td> Original DOM specification
</td></tr>
<tr>
<td> <a href="/w/index.php?title=HTML_4.01&amp;action=edit&amp;redlink=1" class="new" title="HTML 4.01 (page does not exist)">HTML 4.01</a> </td>
<td> Recommendation </td>
<td> Original onclick attribute specification
</td></tr></table>
<p><br />
</p>
<h2><span class="mw-headline" id="Browser_Compatibility">Browser Compatibility</span></h2>
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
        <td>5.0<br />4.0 <span style="border:1px solid black; padding:2px">-webkit</span></td>
        <td><a href="/w/index.php?title=Template:CompatGeckoDesktop(%221%22)&amp;action=edit&amp;redlink=1" class="new" title="Template:CompatGeckoDesktop(&quot;1&quot;) (page does not exist)">Template:CompatGeckoDesktop("1")</a></td>
        <td>5.5</td>
        <td>7.0</td>
        <td>1.0</td>
      </tr>
  </table>
</div>
<p><i><b>Implementation Note:</b> The prefix tag (here, a fake value just to show it off) would be a link to the concept of prefixes.</i>
</p>
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
        <td>1.0</td>
        <td><a href="/w/index.php?title=Template:CompatGeckoMobile(%221%22)&amp;action=edit&amp;redlink=1" class="new" title="Template:CompatGeckoMobile(&quot;1&quot;) (page does not exist)">Template:CompatGeckoMobile("1")</a></td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
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
<td> Firefox
</td>
<td> 15.0
</td>
<td> Introduces the <code>buttons</code> attribute on attribute on Windows, Linux (GTK) and Mac. On Mac OS X 10.5, the <code>buttons</code> attribute always returns 0 because there is no platform API for implementing this feature.
</td></tr>
<tr>
<td> Firefox
</td>
<td> 15.0
</td>
<td> On Windows, if user installed a mouse driver and its utility software which can customize button actions (e.g., IntelliPoint and SetPoint), the Middle (wheel) button, 4th button and 5th button may not be set actually even when they're pressed.
</td></tr>
<tr>
<td> Firefox
</td>
<td> 15.0
</td>
<td> On Linux (GTK), 4th button and 5th button are not supported. And also, <code>mouseup</code> event always have the releasing button information in this attribute value.
</td></tr></table>
<h2><span class="mw-headline" id="See_Also">See Also</span></h2>
<p>The <a href="/w/index.php?title=DOM_Reference&amp;action=edit&amp;redlink=1" class="new" title="DOM Reference (page does not exist)">DOM Reference</a> and the <a href="/w/index.php?title=DOM_Event_Reference&amp;action=edit&amp;redlink=1" class="new" title="DOM Event Reference (page does not exist)">DOM Event Reference</a>.
</p>
<h3><span class="mw-headline" id="Related_Event_Properties">Related Event Properties</span></h3>
<ul><li> <code><a href="/w/index.php?title=mouseenter&amp;action=edit&amp;redlink=1" class="new" title="mouseenter (page does not exist)">mouseenter</a></code></li>
<li> <code><a href="/w/index.php?title=mouseleave&amp;action=edit&amp;redlink=1" class="new" title="mouseleave (page does not exist)">mouseleave</a></code></li>
<li> <code><a href="/w/index.php?title=mousedown&amp;action=edit&amp;redlink=1" class="new" title="mousedown (page does not exist)">mousedown</a></code></li>
<li> <code><a href="/w/index.php?title=mousemove&amp;action=edit&amp;redlink=1" class="new" title="mousemove (page does not exist)">mousemove</a></code></li>
<li> <code><a href="/w/index.php?title=mousedown&amp;action=edit&amp;redlink=1" class="new" title="mousedown (page does not exist)">mousedown</a></code></li>
<li> <code><a href="/w/index.php?title=mouseout&amp;action=edit&amp;redlink=1" class="new" title="mouseout (page does not exist)">mouseout</a></code></li>
<li> <code><a href="/w/index.php?title=mouseover&amp;action=edit&amp;redlink=1" class="new" title="mouseover (page does not exist)">mouseover</a></code></li>
<li> <code><a href="/w/index.php?title=mouseup&amp;action=edit&amp;redlink=1" class="new" title="mouseup (page does not exist)">mouseup</a></code></li>
<li> <code>click</code></li>
<li> <code><a href="/w/index.php?title=dblclick&amp;action=edit&amp;redlink=1" class="new" title="dblclick (page does not exist)">dblclick</a></code></li></ul>
<h3><span class="mw-headline" id="Related_DOM_Interfaces">Related DOM Interfaces</span></h3>
<ul><li> <code><a href="/w/index.php?title=Event&amp;action=edit&amp;redlink=1" class="new" title="Event (page does not exist)">Event</a></code>
<ul><li> <code><a href="/w/index.php?title=UIEvent&amp;action=edit&amp;redlink=1" class="new" title="UIEvent (page does not exist)">UIEvent</a></code>
<ul><li> <code><a href="/w/index.php?title=MouseEvent&amp;action=edit&amp;redlink=1" class="new" title="MouseEvent (page does not exist)">MouseEvent</a></code></li></ul></li></ul></li></ul>
<h3><span class="mw-headline" id="Related_DOM_properties">Related DOM properties</span></h3>
<ul><li> <code><a href="/w/index.php?title=DOM/element/properties/currentStyle&amp;action=edit&amp;redlink=1" class="new" title="DOM/element/properties/currentStyle (page does not exist)"> element.currentStyle</a></code></li>
<li> <code><a href="/w/index.php?title=DOM/element/properties/defaults&amp;action=edit&amp;redlink=1" class="new" title="DOM/element/properties/defaults (page does not exist)"> element.defaults</a></code> <a href="/w/index.php?title=Flag:Non-standard&amp;action=edit&amp;redlink=1" class="new" title="Flag:Non-standard (page does not exist)">Flag:Non-standard</a> <i>IE Only</i></li></ul>
<h3><span class="mw-headline" id="Allowed_Elements">Allowed Elements</span></h3>
<p><b>list elements? or list element groups?</b>
</p>
<ul><li> All Core HTML elements</li>
<li> All Core SVG elements</li>
<li> any others in comma-separated list</li></ul>
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
<!-- Saved in parser cache with key wpwiki:pcache:idhash:203-0!*!0!!*!*!*!esi=1 and timestamp 20150810195946 and revision id 768
 -->
