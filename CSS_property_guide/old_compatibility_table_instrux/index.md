---
title: WPD:CSS property guide/old compatibility table instrux
---
<h2><span class="mw-headline" id="editing_the_compatibility_table">editing the compatibility table</span></h2>
<p>Fill in as many options on the compatibility table as you can. Data can be found in places such as caniuse.com, MDN and quierksmode. You'll need to full in a separate entry in both the desktop and mobile table sections, for each bit of support data, and think about what different support entries you will need — in the case of background-image, I decided it would be useful to have separate entries for basic background-image support, SVG background image support, multiple background images, and CSS gradients. You can find some more useful ideas on gathering support data at <a href="/wiki/WPD:Getting_Started/Compatibility" title="WPD:Getting Started/Compatibility">Compatibility</a>.
</p><p>A basic, reasonable approach is as follows:
</p>
<ul><li> Leave any compatibility data that is already there in the page; generall y it will have been extracted from the original source of the page, for example MSDN, so should be fairly accurate.</li>
<li> Try to find a page covering the same property on MDN (in your search engine, search for "MDN property-name"). Use MDN to verify data you've already got, and copy across data you've not already got. MDN is fairly good for getting information on support for older, more mature properties, like basic background-image support!</li>
<li> Also search for the property/feature you are looking for support data on, at caniuse.com. Again, copy across missing data, and use it to verify any data you've not already got.</li>
<li> For anything you can't find, leave it as "unknown" for now</li>
<li> If you do manage to complete a set of compatibility data for a CSS property, uncheck the "compatibility incomplete" flag checkbox at the top of the page.</li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:8283-0!*!0!*!*!*!*!esi=1 and timestamp 20150731184155 and revision id 31420
 -->
