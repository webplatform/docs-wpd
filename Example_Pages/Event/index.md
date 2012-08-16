'''This is a temporary page to pull together an example of what the ideal end state will be. It includes some content from MDN that is not compatible with the WPD license, and should be removed soon.'''
Draws from:
* https://developer.mozilla.org/en-US/docs/DOM/DOM_event_reference/mouseenter
* https://developer.mozilla.org/en-US/docs/DOM/MouseEvent
* http://msdn.microsoft.com/en-us/library/ie/ms536913%28v=vs.85%29.aspx

==Summary==
The <code>click</code> event type is dispatched when the user activates the primary pointer indicator (e.g., the left mouse button) on an element.

==Syntax==
{| class="wikitable"
! 
! Keyword
! Sample Usage
|-
! Event Type
| <code>click</code>
| <code>object.addEventListener("click", handler, useCapture);</code>
|-
! Event Attribute
| <code>onclick</code>
| <code>&lt;element onclick = "handler(event)"&gt;</code>
|-
! Event Property
| <code>onclick</code>
| <code>object.onclick = handler;</code>
|}

==Event Properties==
{| class="wikitable"
! Interface
| [[MouseEvent]]
|-
! Synchronicity
| synchronous
|-
! Bubbles
| no
|-
! Target
| [[Element]]
|-
! Cancelable
| no
|-
! Default action
| none
|}

==Interface==
The <code>click</code> event type uses the <code>MouseEvent</code> interface.

 '''Note:''' begin transclusion of <code>MouseEvent</code> interface.

===Properties===
{| class="wikitable"
! Property
! Type
! Description
|-
| screenX 
| long
| The X coordinate of the mouse pointer in global (screen) coordinates. Read only.
|-
| screenY
| long
| The Y coordinate of the mouse pointer in global (screen) coordinates. Read only.
|-
| clientX
| long
| The X coordinate of the mouse pointer in local (DOM content) coordinates. Read only.
|-
| clientY
| long
| The Y coordinate of the mouse pointer in local (DOM content) coordinates. Read only.
|-
| ctrlKey
| boolean
| true if the control key was down when the mouse event was fired. Read only.
|-
| shiftKey
| boolean
| true if the shift key was down when the mouse event was fired. Read only.
|-
| altKey
| boolean
| true if the alt key was down when the mouse event was fired. Read only.
|-
| metaKey
| boolean
| true if the meta key was down when the mouse event was fired. Read only.
|-
| button
| unsigned short
| The button number that was pressed when the mouse event was fired: Left button=0, middle button=1 (if present), right button=2. For mice configured for left handed use in which the button actions are reversed the values are instead read from right to left. Read only.
|-
| buttons 
| unsigned short 	
| The buttons being pressed when the mouse event was fired: Left button=1, Right button=2, Middle (wheel) button=4, 4th button (typically, "Browser Back" button)=8, 5th button (typically, "Browser Forward" button)=16. If two or more buttons are pressed, returns the logical sum of the values. E.g., if Left button and Right button are pressed, returns 3 (=1 <nowiki>|</nowiki> 2). Read only.
|-
| relatedTarget
| nsIDOMEventTarget
| The target to which the event applies. Read only.
|-
| mozPressure 
  '''Non-standard'''
| float
| The amount of pressure applied to a touch or tablet device when generating the event; this value ranges between 0.0 (minimum pressure) and 1.0 (maximum pressure). Read only.
|}

===Methods===
 boolean getModifierState(in DOMString keyArg);

====getModifierState()====
Returns the current state of the specified modifier key. See the document of KeyboardEvent.getModifierState() for the detail. 

'''DOM level 3 Requires Gecko 15.0'''?

 boolean getModifierState(
   in DOMString keyArg
 );

 '''Note:''' end transclusion of <code>MouseEvent</code> interface.

==Examples==
[[Event/examples/click | View live examples]]

===Example 1===
This example uses the event object to gain information about the origin of the click. In addition, it cancels the default action to prevent navigation of anchor elements, unless the SHIFT key is pressed. Normally a Shift+Click opens the target of a link in a new window; however, the script replaces the current document by setting the location of the window object.

[[See live example]]

<syntaxhighlight>
<script type="text/javascript">
/* This code cancels the event. If the click occurs in an anchor
   and the SHIFT key is down, the document is navigated. */
function clickIt()  
{
    var e = window.event.srcElement
    txtName.value = e.tagName;
    txtType.value = e.type;
    if ((e.tagName == "A") && 
        (window.event.shiftKey)) {
        window.location.href = e.href;
    }
    
    window.event.returnValue = false; 
}
</script>
<body onclick="clickIt()">
<p>To follow a link, click while pressing the SHIFT key.</p>
<a href="about:blank">Click Here</a>
<textarea name="txtName"></textarea> <textarea name="txtType"></textarea>
</body>
</syntaxhighlight>

===Example 2===
This example shows how to bind the onclick event to grouped controls.

[[See live example]]

<syntaxhighlight>
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
</body>
</syntaxhighlight>

==Usage==
If the user clicks the left mouse button, the <code>click</code> event for an object occurs only if the mouse pointer is over the object and an <code>mousedown</code> and an <code>mouseup</code> event occur in that order. For example, if the user clicks the mouse on the object but moves the mouse pointer away from the object before releasing, no <code>click</code> event occurs.

The <code>click</code> event changes the value of a control in a group. This change initiates the event for the group, not for the individual control. For example, if the user clicks a radio button or check box in a group, the <code>click</code> event occurs after the <code>beforeupdate</code> and <code>afterupdate</code> events for the control group.

If the user clicks an object that can receive the input focus but does not already have the focus, the <code>focus</code> event occurs for that object before the <code>click</code> event. If the user double-clicks the left mouse button in a control, an <code>dblclick</code> event occurs immediately after the <code>click</code> event.

Although the <code>click</code> event is available on a large number of HTML elements, if a document is to be accessible to keyboard users, you should restrict its use to the a, input, area, and button elements. These elements automatically allow keyboard access through the TAB key, making documents that use the elements accessible to keyboard users. For more information, please see the section on writing accessible Dynamic HTML.

Initiates any action associated with the object. For example, if the user clicks an a object, the client loads the document specified by the href property. To cancel the default behavior, set the returnValue property of the event object to FALSE.

To invoke this event, do one of the following:

* Click the object.
* Invoke the <code>click</code> method.
* Press the ENTER key in a form.
* Press the access key for a control.
* Select an item in a combo box or list box by clicking the left mouse button or by pressing the arrow keys and then pressing the ENTER key.



==Notes==
None.

==Specifications==
{| class="wikitable"
|-
! Specification !! Status !! Relevant changes
|-
| [[HTML5]] || Working Draft || ''list changes'' (onclick attribute)
|-
| [[DOM 3 Events: MouseEvent]] || Working Draft || ''list changes''
|-
| [[DOM Level 2: MouseEvent]] || Recommendation || Original DOM specification
|-
| [[HTML 4.01]] || Recommendation || Original onclick attribute specification
|}


==Browser Compatibility==

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
        <td>5.0<br/>4.0 <span style='border:1px solid black; padding:2px'>-webkit</span></td>
        <td>{{ CompatGeckoDesktop("1") }}</td>
        <td>5.5</td>
        <td>7.0</td>
        <td>1.0</td>
      </tr>
  </table>
</div>

'''''Implementation Note:''' The prefix tag (here, a fake value just to show it off) would be a link to the concept of prefixes.''

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
        <td>1.0</td>
        <td>{{ CompatGeckoMobile("1") }}</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
      </tr>
  </table>
</div>

===Compatibility Notes===

{| class="wikitable"
! Browser
! Version
! Note
|-
| Firefox
| 15.0
| Introduces the <code>buttons</code> attribute on attribute on Windows, Linux (GTK) and Mac. On Mac OS X 10.5, the <code>buttons</code> attribute always returns 0 because there is no platform API for implementing this feature.
|-
| Firefox
| 15.0
| On Windows, if user installed a mouse driver and its utility software which can customize button actions (e.g., IntelliPoint and SetPoint), the Middle (wheel) button, 4th button and 5th button may not be set actually even when they're pressed.
|-
| Firefox
| 15.0
| On Windows, if user installed a mouse driver and its utility software which can customize button actions (e.g., IntelliPoint and SetPoint), the Middle (wheel) button, 4th button and 5th button may not be set actually even when they're pressed.
|}

==See Also==
The [[DOM Reference]] and the [[DOM Event Reference]].

===Related Event Properties===
* <code>[[mouseenter]]</code>
* <code>[[mouseleave]]</code>
* <code>[[mousedown]]</code>
* <code>[[mousemove]]</code>
* <code>[[mousedown]]</code>
* <code>[[mouseout]]</code>
* <code>[[mouseover]]</code>
* <code>[[mouseup]]</code>
* <code>click</code>
* <code>[[dblclick]]</code>

===Related DOM Interfaces===
* <code>[[Event]]</code>
** <code>[[UIEvent]]</code>
*** <code>[[MouseEvent]]</code>

===Related DOM properties===
* <code>[[DOM/element/properties/currentStyle | element.currentStyle]]</code>
* <code>[[DOM/element/properties/defaults | element.defaults]]</code> ''IE Only''

===Allowed Elements===
'''list elements? or list element groups?'''
* All Core HTML elements
* All Core SVG elements
* any others in comma-separated list

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