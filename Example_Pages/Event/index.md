---
title: 'Event'
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - MouseEvent
    - Element
    - Event/examples/click
    - 'See live example'
    - HTML5
    - 'DOM 3 Events: MouseEvent'
    - 'DOM Level 2: MouseEvent'
    - 'HTML 4.01'
    - 'DOM Reference'
    - 'DOM Event Reference'
    - mouseenter
    - mouseleave
    - mousedown
    - mousemove
    - mouseout
    - mouseover
    - mouseup
    - dblclick
    - Event
    - UIEvent
    - DOM/element/properties/currentStyle
    - DOM/element/properties/defaults
    - 'Flag:Non-standard'
    - 'Template:CompatGeckoDesktop("1")'
    - 'Template:CompatGeckoMobile("1")'
uri: 'WPD:Example Pages/Event'

---
**This is a temporary page to pull together an example of what the ideal end state will be. It includes some content from MDN that is not compatible with the WPD license, and should be removed soon.** Draws from:

-   <https://developer.mozilla.org/en-US/docs/DOM/DOM_event_reference/mouseenter>
-   <https://developer.mozilla.org/en-US/docs/DOM/MouseEvent>
-   <http://msdn.microsoft.com/en-us/library/ie/ms536913%28v=vs.85%29.aspx>

## Summary

The `click` event type is dispatched when the user activates the primary pointer indicator (e.g., the left mouse button) on an element.

## Syntax

<table class="wikitable">
<tr>
<th>
</th>
<th>
Keyword

</th>
<th>
Sample Usage

</th>
</tr>
<tr>
<th>
Event Type

</th>
<td>
`click`

</td>
<td>
`object.addEventListener("click", handler, useCapture);`

</td>
</tr>
<tr>
<th>
Event Attribute

</th>
<td>
`onclick`

</td>
<td>
`<element onclick = "handler(event)">`

</td>
</tr>
<tr>
<th>
Event Property

</th>
<td>
`onclick`

</td>
<td>
`object.onclick = handler;`

</td>
</tr>
</table>
## Event Properties

<table class="wikitable">
<tr>
<th>
Interface

</th>
<td>
[MouseEvent](/w/index.php?title=MouseEvent&action=edit&redlink=1)

</td>
</tr>
<tr>
<th>
Synchronous

</th>
<td>
Yes

</td>
</tr>
<tr>
<th>
Bubbles

</th>
<td>
No

</td>
</tr>
<tr>
<th>
Target

</th>
<td>
[Element](/w/index.php?title=Element&action=edit&redlink=1)

</td>
</tr>
<tr>
<th>
Cancelable

</th>
<td>
No

</td>
</tr>
<tr>
<th>
Default action

</th>
<td>
None

</td>
</tr>
</table>
## Interface

The `click` event type uses the `MouseEvent` interface.

***Implementation Note:** begin transclusion of `MouseEvent` interface.*

<table>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
<thead>
<tr class="header">
<th align="left">Property</th>
<th align="left">Type</th>
<th align="left">Description</th>
<th align="left">Read only</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">screenX</td>
<td align="left">long</td>
<td align="left">The X coordinate of the mouse pointer in global (screen) coordinates.</td>
<td align="left">Yes</td>
</tr>
<tr class="even">
<td align="left">screenY</td>
<td align="left">long</td>
<td align="left">The Y coordinate of the mouse pointer in global (screen) coordinates.</td>
<td align="left">Yes</td>
</tr>
<tr class="odd">
<td align="left">clientX</td>
<td align="left">long</td>
<td align="left">The X coordinate of the mouse pointer in local (DOM content) coordinates.</td>
<td align="left">Yes</td>
</tr>
<tr class="even">
<td align="left">clientY</td>
<td align="left">long</td>
<td align="left">The Y coordinate of the mouse pointer in local (DOM content) coordinates.</td>
<td align="left">Yes</td>
</tr>
<tr class="odd">
<td align="left">ctrlKey</td>
<td align="left">boolean</td>
<td align="left">true if the control key was down when the mouse event was fired.</td>
<td align="left">Yes</td>
</tr>
<tr class="even">
<td align="left">shiftKey</td>
<td align="left">boolean</td>
<td align="left">true if the shift key was down when the mouse event was fired.</td>
<td align="left">Yes</td>
</tr>
<tr class="odd">
<td align="left">altKey</td>
<td align="left">boolean</td>
<td align="left">true if the alt key was down when the mouse event was fired.</td>
<td align="left">Yes</td>
</tr>
<tr class="even">
<td align="left">metaKey</td>
<td align="left">boolean</td>
<td align="left">true if the meta key was down when the mouse event was fired.</td>
<td align="left">Yes</td>
</tr>
<tr class="odd">
<td align="left">button</td>
<td align="left">unsigned short</td>
<td align="left">The button number that was pressed when the mouse event was fired: Left button=0, middle button=1 (if present), right button=2. For mice configured for left handed use in which the button actions are reversed the values are instead read from right to left.</td>
<td align="left">Yes</td>
</tr>
<tr class="even">
<td align="left">buttons</td>
<td align="left">unsigned short</td>
<td align="left">The buttons being pressed when the mouse event was fired: Left button=1, Right button=2, Middle (wheel) button=4, 4th button (typically, &quot;Browser Back&quot; button)=8, 5th button (typically, &quot;Browser Forward&quot; button)=16. If two or more buttons are pressed, returns the logical sum of the values. E.g., if Left button and Right button are pressed, returns 3 (=1 | 2).</td>
<td align="left">Yes</td>
</tr>
<tr class="odd">
<td align="left">relatedTarget</td>
<td align="left">nsIDOMEventTarget</td>
<td align="left">The target to which the event applies.</td>
<td align="left">Yes</td>
</tr>
<tr class="even">
<td align="left">mozPressure
<pre><code> Non-standard</code></pre></td>
<td align="left">float</td>
<td align="left">The amount of pressure applied to a touch or tablet device when generating the event; this value ranges between 0.0 (minimum pressure) and 1.0 (maximum pressure).</td>
<td align="left">Yes</td>
</tr>
</tbody>
</table>

### Methods

    boolean getModifierState(in DOMString keyArg);

#### getModifierState()

Returns the current state of the specified modifier key. See the document of KeyboardEvent.getModifierState() for the detail.

**DOM level 3 Requires Gecko 15.0**?

    boolean getModifierState(
      in DOMString keyArg
    );

***Implementation Note:** end transclusion of `MouseEvent` interface.*

## Examples

[View live examples](/w/index.php?title=Event/examples/click&action=edit&redlink=1)

### Example: Click Event Origin

This example uses the event object to gain information about the origin of the click. In addition, it cancels the default action to prevent navigation of anchor elements, unless the SHIFT key is pressed. Normally a Shift+Click opens the target of a link in a new window; however, the script replaces the current document by setting the location of the window object.

[See live example](/w/index.php?title=See_live_example&action=edit&redlink=1)

``` html
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
```

### Example: Binding the Click Event to Controls

This example shows how to bind the `click` event to grouped controls.

[See live example](/w/index.php?title=See_live_example&action=edit&redlink=1)

``` html
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
```

## Usage

If the user clicks the left mouse button, the `click` event for an object occurs only if the mouse pointer is over the object and an `mousedown` and an `mouseup` event occur in that order. For example, if the user clicks the mouse on the object but moves the mouse pointer away from the object before releasing, no `click` event occurs.

The `click` event changes the value of a control in a group. This change initiates the event for the group, not for the individual control. For example, if the user clicks a radio button or check box in a group, the `click` event occurs after the `beforeupdate` and `afterupdate` events for the control group.

If the user clicks an object that can receive the input focus but does not already have the focus, the `focus` event occurs for that object before the `click` event. If the user double-clicks the left mouse button in a control, an `dblclick` event occurs immediately after the `click` event.

Although the `click` event is available on a large number of HTML elements, if a document is to be accessible to keyboard users, you should restrict its use to the a, input, area, and button elements. These elements automatically allow keyboard access through the TAB key, making documents that use the elements accessible to keyboard users. For more information, please see the section on writing accessible Dynamic HTML.

Initiates any action associated with the object. For example, if the user clicks an a object, the client loads the document specified by the href property. To cancel the default behavior, set the returnValue property of the event object to FALSE.

To invoke this event, do one of the following:

-   Click the object.
-   Invoke the `click` method.
-   Press the ENTER key in a form.
-   Press the access key for a control.
-   Select an item in a combo box or list box by clicking the left mouse button or by pressing the arrow keys and then pressing the ENTER key.

## Notes

None.

## Specifications

|Specification|Status|Relevant changes|
|:------------|:-----|:---------------|
|[HTML5](/w/index.php?title=HTML5&action=edit&redlink=1)|Working Draft|*list changes* (onclick attribute)|
|[DOM 3 Events: MouseEvent](/w/index.php?title=DOM_3_Events:_MouseEvent&action=edit&redlink=1)|Working Draft|*list changes*|
|[DOM Level 2: MouseEvent](/w/index.php?title=DOM_Level_2:_MouseEvent&action=edit&redlink=1)|Recommendation|Original DOM specification|
|[HTML 4.01](/w/index.php?title=HTML_4.01&action=edit&redlink=1)|Recommendation|Original onclick attribute specification|

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
|Basic support|1.0|[Template:CompatGeckoMobile("1")](/w/index.php?title=Template:CompatGeckoMobile(%221%22)&action=edit&redlink=1)|1.0|1.0|1.0|

### Compatibility Notes

|Browser|Version|Note|
|:------|:------|:---|
|Firefox|15.0|Introduces the `buttons` attribute on attribute on Windows, Linux (GTK) and Mac. On Mac OS X 10.5, the `buttons` attribute always returns 0 because there is no platform API for implementing this feature.|
|Firefox|15.0|On Windows, if user installed a mouse driver and its utility software which can customize button actions (e.g., IntelliPoint and SetPoint), the Middle (wheel) button, 4th button and 5th button may not be set actually even when they're pressed.|
|Firefox|15.0|On Linux (GTK), 4th button and 5th button are not supported. And also, `mouseup` event always have the releasing button information in this attribute value.|

## See Also

The [DOM Reference](/w/index.php?title=DOM_Reference&action=edit&redlink=1) and the [DOM Event Reference](/w/index.php?title=DOM_Event_Reference&action=edit&redlink=1).

### Related Event Properties

-   `mouseenter`
-   `mouseleave`
-   `mousedown`
-   `mousemove`
-   `mousedown`
-   `mouseout`
-   `mouseover`
-   `mouseup`
-   `click`
-   `dblclick`

### Related DOM Interfaces

-   `Event`
    -   `UIEvent`
        -   `MouseEvent`

### Related DOM properties

-   ` element.currentStyle`
-   ` element.defaults` [Flag:Non-standard](/w/index.php?title=Flag:Non-standard&action=edit&redlink=1) *IE Only*

### Allowed Elements

**list elements? or list element groups?**

-   All Core HTML elements
-   All Core SVG elements
-   any others in comma-separated list

\<details\> \<summary\>This article contains content originally from external sources, including ones licensed under the CC-BY-SA license.\</summary\>

Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network: \<a href="<http://developer.mozilla.org/foo>" target="\_blank"\>Foo\</a\>

Portions of this content come from Foo.org: \<a href="<http://foo.org/baz>" target="\_blank"\>Baz\</a\>

\</details\>
