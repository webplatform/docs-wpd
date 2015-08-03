---
title: WPD:Browser Testing/CanIUse
---
<h2><span class="mw-headline" id="CanIUse_Data_Model">CanIUse Data Model</span></h2>
<p>The features-json directory includes JSON files for every feature found on the caniuse.com website.
Maintaining these files on GitHub allows anyone to update or contribute to the support data on the site.
</p>
<h3><span class="mw-headline" id="How_it_works">How it works</span></h3>
<p>The data on the site is stored in a database.
This data is periodically exported to the JSON files on GitHub.
Once a change or new file here has been approved, it is integrated back into the database
and the subsequent export files should be the same as the imported ones.
Not too confusing, I hope.&#160;:)
</p>
<h3><span class="mw-headline" id="Supported_changes">Supported changes</span></h3>
<p>Currently the following feature information can be modified:
</p>
<ul><li> <b>title</b> — Feature name (used for the title of the table)</li>
<li> <b>description</b> — Brief description of feature</li>
<li> <b>spec</b> — Spec URL</li>
<li> <b>status</b> — Spec status, one of the following:
<ul><li> `rec` - W3C Recommendation</li>
<li> `pr` - W3C Proposed Recommendation</li>
<li> `cr` - W3C Candidate Recommendation</li>
<li> `wd` - W3C Working Draft</li>
<li> `other` - Non-W3C, but reputable</li>
<li> `unoff` - Unofficial or W3C "Note"</li></ul></li>
<li> <b>links</b> — Array of "link" objects consisting of URL and short description of link</li>
<li> <b>bugs</b> — Array of "bug" objects consisting of a bug description</li>
<li> <b>categories</b> — Array of categories, any of the following:
<ul><li> `HTML5`</li>
<li> `CSS`</li>
<li> `CSS2`</li>
<li> `CSS3`</li>
<li> `SVG`</li>
<li> `PNG`</li>
<li> `JS API`</li>
<li> `Canvas`</li>
<li> `DOM`</li>
<li> `Other`</li></ul></li>
<li> <b>stats</b> — The collection of support data for a given set of browsers/versions. Only the support value strings can be modified. Values are space-separated characters with these meanings:
<ul><li> `y` - (<b>Y</b>)es, supported</li>
<li> `a` - (<b>A</b>)lmost supported (aka Partial support)</li>
<li> `n` - (<b>N</b>)o support</li>
<li> `p` - No support, but has (<b>P</b>)olyfill</li>
<li> `u` - Support (<b>u</b>)nknown</li>
<li> `x` - Requires prefi(<b>x</b>) to work </li></ul></li>
<li> <b>notes</b> — Notes on feature support, often to explain what partial support refers to</li>
<li> <b>ucprefix</b> — Prefix should start with an uppercase letter</li>
<li> <b>parent</b> — ID of parent feature</li>
<li> <b>keywords</b> — Comma separated words that will match the feature in a search</li>
<li> <b>shown</b> — Whether or not feature is ready to be shown on the site. This can be left as false if the support data or information for other fields is still being collected</li></ul>
<h3><span class="mw-headline" id="Adding_a_feature">Adding a feature</span></h3>
<p>To add a feature, simply add another JSON file to the directory with the base file name as the feature ID (only alphanumeric characters and hyphens please). If you want to submit a feature but don't have all information available for it yet, make sure you set the "shown" flag to false.
</p>
<h3><span class="mw-headline" id="Unsupported_changes">Unsupported changes</span></h3>
<p>Currently it is not possible to:
</p>
<ul><li> Add a new browser or browser version (this will be made possible later)</li>
<li> Add a test for any given feature (should also come later)</li>
<li> Add any object properties not already defined above</li>
<li> Modify the <b>usage\_perc\_y</b> or <b>usage\_perc\_a</b> values (these values are generated)</li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:8154-0!*!*!!*!*!*!esi=1 and timestamp 20150731184048 and revision id 30690
 -->
