---
title: WPD:Annotations/Scenarios
---
<h2><span class="mw-headline" id="Reviewing_Specifications">Reviewing Specifications</span></h2>
<p>A reader wishes to read and provide feedback on a W3C specification.
</p><p>See <a href="/wiki/WPD:Annotations/Workflows" title="WPD:Annotations/Workflows">Workflows</a>.
</p>
<h2><span class="mw-headline" id="Identifying_Documentation_Points">Identifying Documentation Points</span></h2>
<ol><li> A reader wishes to identify basic features of a spec that need to be documented. For example, a reader could walk through a CSS spec and annotated each of the CSS properties. Note that the reader does not have to understand the feature or have to document it themselves; that is a separate task.</li>
<li> A reader wishes to highlight a specific passage in a spec as being important for a documentation site to provide clear developer/designer guidance on. For example, a reader notices a tricky, unexpected detail in the specification for the CSS border-radius property that they think needs a call-out in the documentation. Note that the reader may be an expert, or may be a newbie who is requesting a specific explanation.</li></ol>
<h3><span class="mw-headline" id="Issues">Issues</span></h3>
<ul><li> Annotations should be able to be marked as relevant for documentation
<ul><li> Annotation tool could provide a UI that inserts the appropriate tag into that annotation</li></ul></li>
<li> Annotations on a spec should be reflected not only in sidebar of spec, but in a requirements document for contributors to documentation site (e.g. WebPlatform.org)
<ul><li> Annotation server could provide multiple views of document, including one that adds annotation to appropriate page on documentation site (e.g. If a reader highlights a tricky part of CSS border-radius that needs explanation, annotation tool could show that annotation in the spec, but also on docs.webplatform.org/wiki/css/properties/border-radius page, and also on a generated page that list all annotations for CSS issues.</li></ul></li></ul>
<h2><span class="mw-headline" id="Indicating_Documentation_Points">Indicating Documentation Points</span></h2>
<p>A Working Group wishes to inform the reader where to find developer/designer documentation for any given feature in a specification.
</p>
<h2><span class="mw-headline" id="Issues_2">Issues</span></h2>
<ul><li> WG wishes to automate this task
<ul><li> Annotation tool / server could provide an API for bots to add or update annotations based on a known, consistent scheme for documenting features (e.g. a regular site hierarchy or metadata)</li>
<li> Documentation contributors could ensure that relevant specs are listed in page for documented feature, making it easier for a bot to automate this task</li></ul></li></ul>
<h2><span class="mw-headline" id="Notification_of_Change_of_Specification">Notification of Change of Specification</span></h2>
<p>A documentation project wishes to keep their documentation in sync with changes made to a related specification, and to indicate that stability and status to their readers.
</p>
<h2><span class="mw-headline" id="Issues_3">Issues</span></h2>
<ul><li> Project wishes to automate this task
<ul><li> Annotation tool / server could provide an API for bots to add or update annotations based on a known, consistent scheme for documenting features (e.g. a regular site hierarchy or metadata)</li>
<li> Documentation contributors could ensure that relevant specs are listed in page for documented feature, making it easier for a bot to automate this task</li></ul></li>
<li> Project wishes to be notified of changes to the spec
<ul><li> A bot could monitor publications, run a diff on specific sections of the versions of a spec, and add annotations to the appropriate page on the documentation site indicating a change</li></ul></li></ul>
<h2><span class="mw-headline" id="Identifying_Testable_Assertions">Identifying Testable Assertions</span></h2>
<p>A reader wishes to manually walk through the spec and identify selections for suitability (or need) for testing.
</p>
<h3><span class="mw-headline" id="Issues_4">Issues</span></h3>
<ul><li> User may wish to select multiple non-contiguous passages, on the same or different pages in the same document, for combinatorial testing
<ul><li> UI could provide a way to add selection passages to same annotation</li></ul></li></ul>
<h2><span class="mw-headline" id="Indicating_Status_of_Tests_or_Implementations">Indicating Status of Tests or Implementations</span></h2>
<p>A Working Group wishes to inform the reader which parts of the spec are at different levels of stability, in terms of number of tests or known implementations, and wishes to provide links to tests and implementation reports. 
</p>
<h3><span class="mw-headline" id="Issues_5">Issues</span></h3>
<ul><li> These annotations should be indicated in a different way than normal text annotations
<ul><li> Annotation tool could insert icons on a per-section level indicating status</li>
<li> Annotation tool could style feature / section name differently based on relative stability, or give stability marker</li></ul></li>
<li> WG wishes to automate this task
<ul><li> Annotation tool / server could provide an API for bots to add or update annotations</li></ul></li></ul>
<h2><span class="mw-headline" id="Keeping_Private_Notes_on_Specifications">Keeping Private Notes on Specifications</span></h2>
<p>A reader, or set of reader, wish to highlight and annotate parts of the spec for personal/internal review, before commenting on them publicly. For example, a company may wish to discuss the IP considerations of a spec, comparing to their IP portfolio, or known IP from others, as part of a risk assessment.
</p>
<h3><span class="mw-headline" id="Issues_6">Issues</span></h3>
<ul><li> User doesn't wish to share annotations with others (yet or ever)
<ul><li> Annotation tool could allow user to store (non-sensitive) on normal annotation server with view permissions set to self or set of friends</li>
<li> Important that annotations are not simply hidden by CSS, but rather not downloaded for unauthorized users at all</li></ul></li>
<li> User may not wish sensitive annotations to be stored on a external site
<ul><li> Annotation tool could be configured to store annotations on user's own annotation server</li>
<li> User could use their own annotation tool and server</li></ul></li></ul>
<h2><span class="mw-headline" id="Unanchored_Annotation">Unanchored Annotation</span></h2>
<p>A reader wishes to leave an annotation or comment about the site as a whole, not a particular page. For example, a reader may wish to add a feature request for the site, or comment on the quality of the site as a whole.
</p>
<h3><span class="mw-headline" id="Issues_7">Issues</span></h3>
<ul><li> Annotations should be anchorable to the site without a page referent
<ul><li> </li></ul></li>
<li> Unanchored annotations should be allowed to be added while on any site of the page without anchoring to that page
<ul><li> </li></ul></li>
<li> Unanchored annotations should not accumulate on the site landing page or index page, because they will clutter that page
<ul><li></li></ul></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.022 seconds
Real time usage: 0.023 seconds
Preprocessor visited node count: 58/1000000
Preprocessor generated node count: 64/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:13307-0!*!0!!*!*!*!esi=1 and timestamp 20150731112207 and revision id 42991
 -->
