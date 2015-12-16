---
title: 'QuirksMode'
uri: 'WPD:Browser Testing/QuirksMode'

---
## QuirksMode Browser Compatibility data model

### Purpose

The browser compatibility tables on <http://quirksmode.org> have been the prime sources for browser incompatibility information for years now.

This proposal aims at creating an API with which anyone can query the compatibility database and build their own compatibility tables.

### API

QuirksMode currently stores its data in HTML tables, and does not offer downloadable data or an API. This document describes the QuirksMode data model should work.

The API should allow anyone to request compatibility information for one or more methods, properties, or CSS declarations in one or more browsers. A JSON file will be delivered, and it will be up to the owner of the requesting script to do something with this data.

### Data model

The “rows” consist of DOM methods and properties, as well as CSS declarations. The “columns” consist of browsers. In each intersection a compatibility status text is shown.

In addition, each method/property/declaration has one text that describes it, one code example, and a link to a test page.

Specific intersections may also have a related text. For instance, if attributes[index] in IE8 is judged “Incorrect,” a related text describes the exact problem. This text should be sent with the rest of the data whenever a user requests attributes[index] in IE8.

#### Methods, properties, and declarations

In theory the compatibility tables contain all DOM methods and properties and all CSS declarations. (In practice they contain a subset of each; I haven’t bothered to test CSS margin, for instance.)

The API should allow users to request an arbitrary number of methods, properties, and declarations.

In order to allow users to easily request related methods, properties, and declarations, they will be sorted into groups; for instance “DOM – Attributes”, “CSS – typography” etc. This allows users to specify a group and automatically receive all methods, properties, and declarations in that group.

These groups have to be defined further. Currently I define groups by grouping methods, properties, and declarations in tables with a specific purpose.

All methods, properties, and declarations should have the following related items:

-   a text that briefly describes its purpose
-   a code example with explanations
-   a link to a test page
-   (possibly links to related items; the current compatibility tables do not have this feature)

#### Browsers

The API should also allow users to request an arbitrary number of browsers.

To make it easier for the users to request related data, browsers, too, will be sorted into groups. For instance, the Android G1 and Android G2 browsers both belong to the groups “Android”, “WebKit”, and “Mobile browsers”

These browser groups have to be defined. Currently the mobile tables show browser groups; “Opera Mobile”, “S60 WebKit” etc. but this scheme has to be extended considerably.

#### Compatibility data

At the intersection of each individual method, property, or declaration and each individual browser there is a compatibility text, which can have the following values:

<table class="wikitable">
<tr>
<th>
Yes

</th>
<td>
Supported completely and correctly

</td>
</tr>
<tr>
<th>
Almost

</th>
<td>
Supported completely and correctly except for a minor issue

</td>
</tr>
<tr>
<th>
Incomplete

</th>
<td>
Supported correctly but not completely

</td>
</tr>
<tr>
<th>
Alternative

</th>
<td>
Supported, but with alternative syntax

</td>
</tr>
<tr>
<th>
Untestable

</th>
<td>
Cannot be tested; usually because it depends on another item that is not supported

</td>
</tr>
<tr>
<th>
To be tested

</th>
<td>
DEFAULT. Item has not been tested yet in this browser.

</td>
</tr>
<tr>
<th>
Minimal

</th>
<td>
Supported in theory, but unusable in practice

</td>
</tr>
<tr>
<th>
Incorrect

</th>
<td>
Returns incorrect value

</td>
</tr>
<tr>
<th>
Buggy

</th>
<td>
Does something it should not do

</td>
</tr>
<tr>
<th>
No

</th>
<td>
Not supported

</td>
</tr>
<tr>
<th>
Crash

</th>
<td>
Crashes browser

</td>
</tr>
</table>
If the value is Almost, Incomplete, Alternative, Minimal, Incorrect or Buggy, there should be a related text that describes the exact problem in the browser. This text should be sent together with the compatibility information.

(The values Yes, No, Untestable and Crash may also have such texts, but usually they’re pretty self-explanatory.)

### Example

As an example, let’s take a look at the **attributes[index]** entry in the [current compatibility tables](http://www.quirksmode.org/dom/w3c_core.html#attributes).

![QuirksMode-example.png](//static.webplatform.org/9/98/QuirksMode-example.png)

The method is attributes[index].

-   The browsers are all desktop browsers (IE5.5, 6, 7, 8-as-7 and 8-as-8; Firefox 2.0, 3.0 and 3.5, Safari 3.0, 3.1 and 4.0; Chrome 2.0, Opera 9.51 and 10a, and Konqueror 3.5.7; these could possibly form the group “desktop browsers”)
-   The “An array with...” and “Do not use ... instead” texts are the description.
-   The “x.attributes[1] ... in source code order” and “Do yourself ... array” texts are the code example.
-   “Alternative”, “Incorrect”, etc., are the status texts
-   The “Firefox and IE8 ...” text should be linked to all Firefox versions as well as IE8-as-8.
-   The “IE5-7” text should be linked to IE5.5, 6, and 7.
-   The “IE5.5” text should be linked to IE5.5
-   The “Test page” link leads to the test page.
-   Thus, if a user would request attributes[index] for IE 7 and 8 he would get all data except for the IE5.5 text. If he would leave out IE entirely he would not receive the IE5-7 and IE5.5 texts.

## JSON Example

``` html
{
   "vh and vw": {
    "test": "http://quirksmode.org/css/units-values/viewport.html",
    "spec": "http://www.w3.org/TR/css3-values/#viewport-relative-lengths",
    "description": "Percentages of the layout viewport width or height",
    "example": {
        code: "width: 50vw",
        explanation: "Element's width is 50% of layout viewport width"
    },
    "compatibility": {
        "desktop": {
            "IE7": "No",
            "IE8": "No",
            "IE9": "Yes",
            "IE10": "Yes"
            "FF 19 Win": "Yes",
            "FF 19 Mac": "Yes",
            "Saf 6.0.2": "Incomplete",
            "Chrome 25 Win": "Incomplete",
            "Chrome 25 Mac": "Incomplete",
            "Yandex 1.5 Mac": "Incomplete",
            "Op 12.14 Win": "No",
            "Op 12.14 Mac": "No",
        },
        "mobile": {
            "iOS5": "No",
            "iOS6": "Incomplete",
            "Android 2": "No",
            "Android 3": "No",
            "Android 4": "No",
            "Chrome 18 Android": "No",
            "Chrome 25 Android": "Incorrect",
            "Opera Mini": "No",
            "Opera Mobile 12": "No",
            "Opera Mobile 14": "Buggy",
            "BB6": "No",
            "BB7": "No",
            "BB PB": "No",
            "Nokia Xpress": "No",
            "MeeGo": "No",
            "Symbian Anna": "No",
            "Symbian Belle": "No",
            "UC": "No",
            "NetFront": "No",
            "Dolphin": "Incorrect",
            "One": "No",
            "Tizen": "Incorrect",
            "IE9 WP": "Incomplete",
            "IE10 WP": "Yes"
            "Firefox": "No",
        }
    },
    "notes": {
        {
            "text": "Widths not updated when the viewport changes, for instance by changing the orientation",
            "browsers": ["Saf 6.0.2","Chrome 25 Win","Chrome 25 Mac","Yandex 1.5 Mac","iOS6","Chrome 25 Android","Tizen","IE9 WP"]
        },
        {
            "text": "Unit relative to the visual viewport, not to the layout viewport.",
            "browsers": ["Chrome 25 Android","Dolphin","Tizen"]
        },
        {
            "text": "Weird numbers that bear no discernible relation to any viewport.",
            "browsers": ["Opera 14"]
        },
    }
}
```
