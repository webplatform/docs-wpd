---
title: WPD:Browser Testing/QuirksMode
---
<h2><span class="mw-headline" id="QuirksMode_Browser_Compatibility_data_model">QuirksMode Browser Compatibility data model</span></h2>
<h3><span class="mw-headline" id="Purpose">Purpose</span></h3>
<p>The browser compatibility tables on <a rel="nofollow" class="external free" href="http://quirksmode.org">http://quirksmode.org</a> have been the prime sources for browser incompatibility information for years now.
</p><p>This proposal aims at creating an API with which anyone can query the compatibility database and build their own compatibility tables.
</p>
<h3><span class="mw-headline" id="API">API</span></h3>
<p>QuirksMode currently stores its data in HTML tables, and does not offer downloadable data or an API. This document describes the QuirksMode data model should work.
</p><p>The API should allow anyone to request compatibility information for one or more methods, properties, or CSS declarations in one or more browsers. A JSON file will be delivered, and it will be up to the owner of the requesting script to do something with this data.
</p>
<h3><span class="mw-headline" id="Data_model">Data model</span></h3>
<p>The “rows” consist of DOM methods and properties, as well as CSS declarations. The “columns” consist of browsers. In each intersection a compatibility status text is shown.
</p><p>In addition, each method/property/declaration has one text that describes it, one code example, and a link to a test page.
</p><p>Specific intersections may also have a related text. For instance, if attributes[index] in IE8 is judged “Incorrect,” a related text describes the exact problem. This text should be sent with the rest of the data whenever a user requests attributes[index] in IE8.
</p>
<h4><span class="mw-headline" id="Methods.2C_properties.2C_and_declarations">Methods, properties, and declarations</span></h4>
<p>In theory the compatibility tables contain all DOM methods and properties and all CSS declarations. (In practice they contain a subset of each; I haven’t bothered to test CSS margin, for instance.)
</p><p>The API should allow users to request an arbitrary number of methods, properties, and declarations.
</p><p>In order to allow users to easily request related methods, properties, and declarations, they will be sorted into groups; for instance “DOM – Attributes”, “CSS – typography” etc. This allows users to specify a group and automatically receive all methods, properties, and declarations in that group.
</p><p>These groups have to be defined further. Currently I define groups by grouping methods, properties, and declarations in tables with a specific purpose.
</p><p>All methods, properties, and declarations should have the following related items:
</p>
<ul><li> a text that briefly describes its purpose</li>
<li> a code example with explanations</li>
<li> a link to a test page</li>
<li> (possibly links to related items; the current compatibility tables do not have this feature)</li></ul>
<h4><span class="mw-headline" id="Browsers">Browsers</span></h4>
<p>The API should also allow users to request an arbitrary number of browsers.
</p><p>To make it easier for the users to request related data, browsers, too, will be sorted into groups. For instance, the Android G1 and Android G2 browsers both belong to the groups “Android”, “WebKit”, and “Mobile browsers”
</p><p>These browser groups have to be defined. Currently the mobile tables show browser groups; “Opera Mobile”, “S60 WebKit” etc. but this scheme has to be extended considerably.
</p>
<h4><span class="mw-headline" id="Compatibility_data">Compatibility data</span></h4>
<p>At the intersection of each individual method, property, or declaration and each individual browser there is a compatibility text, which can have the following values:
</p>
<table class="wikitable">
<tr>
<th> Yes
</th>
<td> Supported completely and correctly
</td></tr>
<tr>
<th> Almost
</th>
<td> Supported completely and correctly except for a minor issue
</td></tr>
<tr>
<th> Incomplete
</th>
<td> Supported correctly but not completely
</td></tr>
<tr>
<th> Alternative
</th>
<td> Supported, but with alternative syntax
</td></tr>
<tr>
<th> Untestable
</th>
<td> Cannot be tested; usually because it depends on another item that is not supported
</td></tr>
<tr>
<th> To be tested
</th>
<td> DEFAULT. Item has not been tested yet in this browser.
</td></tr>
<tr>
<th> Minimal
</th>
<td> Supported in theory, but unusable in practice
</td></tr>
<tr>
<th> Incorrect
</th>
<td> Returns incorrect value
</td></tr>
<tr>
<th> Buggy
</th>
<td> Does something it should not do
</td></tr>
<tr>
<th> No
</th>
<td> Not supported
</td></tr>
<tr>
<th> Crash
</th>
<td> Crashes browser
</td></tr></table>
<p>If the value is Almost, Incomplete, Alternative, Minimal, Incorrect or Buggy, there should be a related text that describes the exact problem in the browser. This text should be sent together with the compatibility information.
</p><p>(The values Yes, No, Untestable and Crash may also have such texts, but usually they’re pretty self-explanatory.)
</p><p><br />
</p>
<h3><span class="mw-headline" id="Example">Example</span></h3>
<p>As an example, let’s take a look at the <b>attributes[index]</b> entry in the <a rel="nofollow" class="external text" href="http://www.quirksmode.org/dom/w3c_core.html#attributes">current compatibility tables</a>.
</p><p><a href="/wiki/File:QuirksMode-example.png" class="image"><img alt="QuirksMode-example.png" src="//static.webplatform.org/w/public/9/98/QuirksMode-example.png" width="1059" height="305" /></a>
</p><p>The method is attributes[index].
</p>
<ul><li> The browsers are all desktop browsers (IE5.5, 6, 7, 8-as-7 and 8-as-8; Firefox 2.0, 3.0 and 3.5, Safari 3.0, 3.1 and 4.0; Chrome 2.0, Opera 9.51 and 10a, and Konqueror 3.5.7; these could possibly form the group “desktop browsers”)</li>
<li> The “An array with...” and “Do not use ... instead” texts are the description.</li>
<li> The “x.attributes[1] ... in source code order” and “Do yourself ... array” texts are the code example.</li>
<li> “Alternative”, “Incorrect”, etc., are the status texts</li>
<li> The “Firefox and IE8 ...” text should be linked to all Firefox versions as well as IE8-as-8.</li>
<li> The “IE5-7” text should be linked to IE5.5, 6, and 7.</li>
<li> The “IE5.5” text should be linked to IE5.5</li>
<li> The “Test page” link leads to the test page.</li>
<li> Thus, if a user would request attributes[index] for IE 7 and 8 he would get all data except for the IE5.5 text. If he would leave out IE entirely he would not receive the IE5-7 and IE5.5 texts.</li></ul>
<h2><span class="mw-headline" id="JSON_Example">JSON Example</span></h2>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{
   &quot;vh and vw&quot;: {
	&quot;test&quot;: &quot;http://quirksmode.org/css/units-values/viewport.html&quot;,
	&quot;spec&quot;: &quot;http://www.w3.org/TR/css3-values/#viewport-relative-lengths&quot;,
	&quot;description&quot;: &quot;Percentages of the layout viewport width or height&quot;,
	&quot;example&quot;: {
		code: &quot;width: 50vw&quot;,
		explanation: &quot;Element's width is 50% of layout viewport width&quot;
	},
	&quot;compatibility&quot;: {
		&quot;desktop&quot;: {
			&quot;IE7&quot;: &quot;No&quot;,
			&quot;IE8&quot;: &quot;No&quot;,
			&quot;IE9&quot;: &quot;Yes&quot;,
			&quot;IE10&quot;: &quot;Yes&quot;
			&quot;FF 19 Win&quot;: &quot;Yes&quot;,
			&quot;FF 19 Mac&quot;: &quot;Yes&quot;,
			&quot;Saf 6.0.2&quot;: &quot;Incomplete&quot;,
			&quot;Chrome 25 Win&quot;: &quot;Incomplete&quot;,
			&quot;Chrome 25 Mac&quot;: &quot;Incomplete&quot;,
			&quot;Yandex 1.5 Mac&quot;: &quot;Incomplete&quot;,
			&quot;Op 12.14 Win&quot;: &quot;No&quot;,
			&quot;Op 12.14 Mac&quot;: &quot;No&quot;,
		},
		&quot;mobile&quot;: {
			&quot;iOS5&quot;: &quot;No&quot;,
			&quot;iOS6&quot;: &quot;Incomplete&quot;,
			&quot;Android 2&quot;: &quot;No&quot;,
			&quot;Android 3&quot;: &quot;No&quot;,
			&quot;Android 4&quot;: &quot;No&quot;,
			&quot;Chrome 18 Android&quot;: &quot;No&quot;,
			&quot;Chrome 25 Android&quot;: &quot;Incorrect&quot;,
			&quot;Opera Mini&quot;: &quot;No&quot;,
			&quot;Opera Mobile 12&quot;: &quot;No&quot;,
			&quot;Opera Mobile 14&quot;: &quot;Buggy&quot;,
			&quot;BB6&quot;: &quot;No&quot;,
			&quot;BB7&quot;: &quot;No&quot;,
			&quot;BB PB&quot;: &quot;No&quot;,
			&quot;Nokia Xpress&quot;: &quot;No&quot;,
			&quot;MeeGo&quot;: &quot;No&quot;,
			&quot;Symbian Anna&quot;: &quot;No&quot;,
			&quot;Symbian Belle&quot;: &quot;No&quot;,
			&quot;UC&quot;: &quot;No&quot;,
			&quot;NetFront&quot;: &quot;No&quot;,
			&quot;Dolphin&quot;: &quot;Incorrect&quot;,
			&quot;One&quot;: &quot;No&quot;,
			&quot;Tizen&quot;: &quot;Incorrect&quot;,
			&quot;IE9 WP&quot;: &quot;Incomplete&quot;,
			&quot;IE10 WP&quot;: &quot;Yes&quot;
			&quot;Firefox&quot;: &quot;No&quot;,
		}
	},
	&quot;notes&quot;: {
		{
			&quot;text&quot;: &quot;Widths not updated when the viewport changes, for instance by changing the orientation&quot;,
			&quot;browsers&quot;: [&quot;Saf 6.0.2&quot;,&quot;Chrome 25 Win&quot;,&quot;Chrome 25 Mac&quot;,&quot;Yandex 1.5 Mac&quot;,&quot;iOS6&quot;,&quot;Chrome 25 Android&quot;,&quot;Tizen&quot;,&quot;IE9 WP&quot;]
		},
		{
			&quot;text&quot;: &quot;Unit relative to the visual viewport, not to the layout viewport.&quot;,
			&quot;browsers&quot;: [&quot;Chrome 25 Android&quot;,&quot;Dolphin&quot;,&quot;Tizen&quot;]
		},
		{
			&quot;text&quot;: &quot;Weird numbers that bear no discernible relation to any viewport.&quot;,
			&quot;browsers&quot;: [&quot;Opera 14&quot;]
		},
	}
}</pre></div></div>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:8152-0!*!*!!*!5!*!esi=1 and timestamp 20150731184041 and revision id 30687
 -->
