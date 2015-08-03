---
title: WPD:Flags/Notes
---
<p>These are early notes about the Flags concept.
</p>
<h2><span class="mw-headline" id="List_of_Categorization_Flags">List of Categorization Flags</span></h2>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  These aren't implemented as "Flags" anymore, but normal form fields.
</p>
</div>
<p><b>We will revisit this whole thing in the future. On hold for now.</b>
</p><p>These are flags that call out special status of articles. They do not represent work that must be done on the article, but rather properties of the things the article documents.
</p>
<h3><span class="mw-headline" id="Standardization_Status">Standardization Status</span></h3>
<ul><li> W3C_Editors_Draft</li>
<li> W3C_Working_Draft</li>
<li> W3C_Candidate_Recommendation</li>
<li> W3C_Recommendation</li>
<li> Deprecated <i>For technologies that have been replaced or retracted, and are not recommended for use (but which are valuable to have for reference)</i></li>
<li> Non-standard <i>For technologies that are not yet being standardized in any formal body, don't have 2 or more compatible implementations, and likely never will</i></li>
<li> Defacto-standard <i>For technologies that are not yet standardized, but have 2 or more compatible implementations (modulo prefixes)</i></li>
<li> Experimental <i>For technologies that are not yet being standardized, don't have 2 or more compatible implementations, but aim to one day be a standard</i></li>
<li> <i>TODO: fill out this list with other standards bodies</i></li></ul>
<h3><span class="mw-headline" id="Browser_Support">Browser Support</span></h3>
<p>Which browsers support this technology.  'Stable' means that that browser's most recent main release includes support. 'Preview' means that a preview release of that browser (e.g. a "Beta", "Alpha", or "Developer Preview") includes support. Only one of these tags should be included for each browser (and always the highest one).
</p>
<ul><li> Internet_Explorer_Stable</li>
<li> Firefox_Stable</li>
<li> Safari_Stable</li>
<li> Opera_Stable</li>
<li> Chrome_Stable</li>
<li> Internet_Explorer_Preview</li>
<li> Firefox_Preview</li>
<li> Safari_Preview</li>
<li> Opera_Preview</li>
<li> Chrome_Preview</li></ul>
<h3><span class="mw-headline" id="Prefixes">Prefixes</span></h3>
<ul><li> Prefix_Everywhere <i>Every stable browser this ships in includes the prefix</i></li>
<li> Prefix_Somewhere <i>At least one stable browser ships this without a prefix</i></li>
<li> Prefix_Nowhere <i>No stable browser ships this with a prefix</i></li></ul>
<h2><span class="mw-headline" id="Design">Design</span></h2>
<p><a href="/wiki/WPD:Design/Flags" title="WPD:Design/Flags">Flag appearance and icons</a>
</p><p><br />
<i>These are even earlier notes:</i>
</p>
<h2><span class="mw-headline" id="Design_exploration">Design exploration</span></h2>
<h3><span class="mw-headline" id="Presentation">Presentation</span></h3>
<p>Most warning templates are displayed as a banner, often at the top of a page before the content, but sometimes inline in the content itself. This is eye-catching, but can be distracting.  The goal is to draw attention to the warning without detracting from the use of the page.
</p>
<h4><span class="mw-headline" id="Presentation_Proposal">Presentation Proposal</span></h4>
<p>One way to make is easy for people to assess the status easily is by having color-coded flags (e.g. CSS ribbons) with icon arranged along the top edge of the content area, each with a different indicator; mousing over these flags would raise a tooltip indicating the specific message.
</p><p>(See <a rel="nofollow" class="external text" href="http://schepers.cc/wpd/Ribbons_Web_Elements_Preview2.jpg">Top Ribbons</a> for a visual example of this type of flag, and <a rel="nofollow" class="external text" href="http://schepers.cc/webplatform/flags.svg">Flags Mock</a> for a mock of what this could look like on this site.)
</p>
<h3><span class="mw-headline" id="User_Experience">User Experience</span></h3>
<p>Traditionally, these flags are added by using a specific bit of Mediawiki markdown to the page.  However, not everyone is familiar with the way to do this, and discovering the correct types of "content flags" is not obvious.
</p>
<h4><span class="mw-headline" id="UX_Proposal">UX Proposal</span></h4>
<p>Each page could feature a dropdown, with a Semantic Form backend, that automatically adds the appropriate flag template to the content (and also records who flagged it). This could look like a simple button that says "Flag this page", and expands into a set of options when pressed.
</p>
<h2><span class="mw-headline" id="Implementation">Implementation</span></h2>
<p>You can see the current implementation of flags in the WPD wiki at the page <a href="/wiki/css/properties/font-size" title="css/properties/font-size">css/properties/font-size</a>, and at its corresponding <a rel="nofollow" class="external text" href="http://webplatform.org/d/index.php?title=css/properties/font-size&amp;action=formedit">edit form</a>.
</p><p>The following are the pages involved in the data structure for setting flags:
</p><p>"Form template" page (a reusable section of form syntax):
</p>
<ul><li> <a href="/wiki/Template:Flags_form_section" title="Template:Flags form section" class="mw-redirect">Template:Flags form section</a></li></ul>
<p>Display template (will eventually get called by each main template):
</p>
<ul><li> <a href="/wiki/Template:Flags" title="Template:Flags">Template:Flags‎</a></li></ul>
<p>Property pages:
</p>
<ul><li> <a href="/wiki/Property:High-level_issue" title="Property:High-level issue">Property:High-level issue</a></li>
<li> <a href="/wiki/Property:Content_quality_flag" title="Property:Content quality flag">Property:Content quality flag</a></li>
<li> <a href="/w/index.php?title=Property:Compatibility_quality_flag&amp;action=edit&amp;redlink=1" class="new" title="Property:Compatibility quality flag (page does not exist)">Property:Compatibility quality flag</a></li>
<li> <a href="/w/index.php?title=Property:Examples_quality_flag&amp;action=edit&amp;redlink=1" class="new" title="Property:Examples quality flag (page does not exist)">Property:Examples quality flag</a></li>
<li> <a href="/wiki/Property:Accessibility_flag" title="Property:Accessibility flag">Property:Accessibility flag</a></li></ul>
<p>And you can see one example of pages being aggregated by their flags, using a Semantic MediaWiki query, at <a href="/w/index.php?title=Stub_pages&amp;action=edit&amp;redlink=1" class="new" title="Stub pages (page does not exist)">Stub pages</a>.
</p>
<h2><span class="mw-headline" id="Requirements">Requirements</span></h2>
<p><i>This is a section kept for historical purposes only</i>
The specific implementation for this will require coordination between content needs, technical implementation abilities, and visual design. Here are the requirements that solutions should satisfy (in decreasing order of importance). Note that we're using "flags" as the catch-all term for these, but they might end up not being displayed that way.
</p>
<ul><li> Allow flags to be displayed in different styles depending on which type they are. For example, some may show as little flags at the top of the content , some may be big banners at the top of the content, and others could be subtle and at the bottom of the content.</li>
<li> Allow some method of listing which pages have a given flag on them</li>
<li> Make it easy for editors to add or remove flags</li>
<li> <i>-- Big gap in priority--</i></li>
<li> Allow some tags to be related in behavior/style/meaning (e.g. subclassing or categories)</li>
<li> Make it easy to define new tags as necessary <i>(this will be pretty rare)</i></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.043 seconds
Real time usage: 0.058 seconds
Preprocessor visited node count: 54/1000000
Preprocessor generated node count: 78/1000000
Post‐expand include size: 218/2097152 bytes
Template argument size: 69/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    4.251      1 - -total
100.00%    4.251      1 - Template:TODO
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:1378-0!*!0!!*!*!*!esi=1 and timestamp 20150730203651 and revision id 5178
 -->
