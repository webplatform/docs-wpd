---
title: WPD:Projects/CSS Property Milestone/css prop enhancements
---
<h1><span class="mw-headline" id="Suggested_design_enhancements_for_CSS_properties">Suggested design enhancements for CSS properties</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p><a rel="nofollow" class="external text" href="http://letmespellitoutforyou.com/x/webplatform/font_size.html">This page</a> is a suggested mockup of how a CSS property page should look.
Compared to the <a href="/wiki/css/properties/font-size" title="css/properties/font-size">original font-size property page</a>, there are several enhancements that would need to be implemented, and here is a list of the most significant. They're broken down into 3 basic categories: <b>SKIN</b> requiring mostly modified CSS, <b>TEMPLATE</b> requiring a change in how content is generated and flows onto the final HTML page, and <b>FORM</b> for changes in the text-input UI.
</p>
<ol><li> <b>[SKIN]</b> Page title &amp; summary are on the same line in this example; formatted as left/right justification with negative margin for overlay; this is fragile for cases where text in either runs too long.</li>
<li> <b>[TEMPLATE]</b> Removed hard-coded "W3C Recommendation" text. If necessary, use a graphic to represent options or otherwise push it out of the main text flow.</li>
<li> <b>[FORM]</b> "Specifies the size of text" is currently called a "summary", hopefully a simple sentence reflected in CSS property listings.  The "This property sets the..." text offers more fleshed-out expository context not intended for listings. New field needed in template. What to call it? Summary-listing/Summary-extended?</li>
<li> <b>[TEMPLATE]</b> Removed the implicit "Summary" &amp; "Overview table" headings.</li>
<li> <b>[TEMPLATE]</b> Under "Values", each &lt;dt&gt;/&lt;dd&gt; pair generate incorrectly in its own &lt;dl&gt;, which also produces unnecessary rules. Regardless, Suggest removing the rule formatting altogether as too busy.</li>
<li> <b>[TEMPLATE/SKIN]</b> Heavily reformatted the property value overview table. Suggest shading all rows white here.</li>
<li> <b>[TEMPLATE]</b> Each cell title ("Computed value"/"Initial value") should link to a concept page.</li>
<li> <b>[TEMPLATE]</b> Inherited/Animatable use check/X icons rather than Yes/No text.</li>
<li> <b>[FORM]</b> Current template only allows one media type, but property may well apply to more.</li>
<li> <b>[FORM]</b> Added an extra "Shorthand" field to overview table. Suggest a field in e.g. template for font-size to specify "font". Then font-size page would display "Shorthand: font" and font page would display "Shorthand for: font-family, font-size, font-weight" ... etc. for all properties that share the same shorthand.</li>
<li> <b>[TEMPLATE]</b> If property is marked as "inherited", should a syntax line &amp; value description be automatically generated, or is it implicit, and is link to the "inherited" concept sufficient? Authors should not have to redundantly hard-code the "inherit" value at any rate.</li>
<li> <b>[FORM]</b> Fixed keyword values are bold, while variables are italic. The template provides no way to make that important distinction.</li>
<li> <b>[TEMPLATE/SKIN]</b> Default text for &lt;dd&gt; text in "Values" section should not be italic.</li>
<li> <b>[TEMPLATE]</b> Heavily reformatted &amp; merged the compatibility table.</li>
<li> <b>[TEMPLATE]</b> Separated sub-issues in compatibility table (e.g. "vw/vh/vmin viewport units") with col-spanned table headings.</li>
<li> <b>[FORM]</b> Under compatibility notes, added less-than/greater-than/equals for explicit relation to version numbers.</li>
<li> <b>[TEMPLATE]</b> Removed redundant "See Also" head; used "Related Articles" instead. </li>
<li> <b>[TEMPLATE]</b> Pushed Specification info into "Related Articles" area</li>
<li> <b>[SKIN]</b> Reformatted most related-article links as 3-column to save space. (Can CSS formatting kick in after # of list items exceeds a threshold? For 3-col format, should kick in with &gt;6 items to prevent orphans.)</li>
<li> <b>[FORM]</b> Directly embedded a sample page as an &lt;iframe&gt;. This is only a suggested UI. Hopefully dabblet sample pages can be presented this way, directly available on the page next to doc that describes it.</li>
<li> <b>[FORM]</b> Suggest adding explicit "example" template options for embedded samples, and for images showing the result of CSS formatting described in other code examples. (Suggest support for &gt;1 inline image, useful to clarify before/after scenarios.)</li>
<li> <b>[FORM]</b> Unclear what "Percentages" template option is intended for "Top-Level Summary", but it is not reflected in the resulting overview table.</li>
<li> <b>[TEMPLATE]</b> Headings may be reshuffled in output.</li>
<li> <b>[TEMPLATE]</b> If only one "Basic support" feature is considered in compatibility table, do not include explicit column span heading. If other sub-features are included, include explicit column spans.</li>
<li> <b>[TEMPLATE]</b> If appropriate to include explicit "inherit"  or "initial" values within "Values" listing (not sure if it is), generate it from supplied metadata, and append it.</li>
<li> <b>[FORM]</b> Should there be a compatibility-table row for tablet-class browsers?</li>
<li> <b>[TEMPLATE]</b> When both prefix &amp; unprefixed support is specified, include them in the same cell (e.g.: "5.0&lt;br/&gt;&lt;span class="tinyWebkitPrefix"&gt;3.0&lt;/span&gt;"). Support is the crucial info to convey; having to implement redundant property prefixes is relatively trivial.</li>
<li> <b>[FORM]</b> Option to include sample syntax with each syntax item. E.g., along with variable "length" syntax item, a quick sample would be "1.5em" as it appears in the sample.</li>
<li> <b>[FORM]</b> Clarify the expected scope of each input field. What's the difference between "Usage" and "Notes"?</li>
<li> <b>[SKIN]</b> On basic principle, increase line-height within UL/OL/DL lists to match body text. I mean, just look at this page.</li></ol>
<p><br />
</p><p><br />
</p>
<div class="attribution">
<p><br />
</p><p><br />
</p>
</div>

<!-- 
NewPP limit report
CPU time usage: 0.051 seconds
Real time usage: 0.065 seconds
Preprocessor visited node count: 80/1000000
Preprocessor generated node count: 776/1000000
Post‐expand include size: 1379/2097152 bytes
Template argument size: 1827/2097152 bytes
Highest expansion depth: 4/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%   46.962      1 - -total
 25.98%   12.201      1 - Template:Page_Title
 20.21%    9.490      1 - Template:Flags
 16.67%    7.830      1 - Template:External_Attribution
 12.50%    5.868      1 - Template:Summary_Section
  8.52%    4.002      1 - Template:Notes_Section
  6.74%    3.167      1 - Template:Topics
  5.71%    2.682      1 - Template:Basic_Page
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:7237-0!*!0!!*!*!*!esi=1 and timestamp 20150730203142 and revision id 29254
 -->
