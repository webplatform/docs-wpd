---
title: WPD:Annotations
path: Annotations

---
<h1><span class="mw-headline" id="Annotations">Annotations</span></h1>
<p>This is a scratch space for adding annotations to WebPlatform.org and to W3C specifications.
</p>
<h2><span class="mw-headline" id="Background">Background</span></h2>
<p>We want to enable annotations on W3C specifications and on WebPlatform.org, as a way to provide feedback into specs and documentation.
</p><p>The specific implementation we want to use will be based on the <a rel="nofollow" class="external text" href="http://okfnlabs.org/annotator/">Annotator project</a>, as implemented and enhanced by <a rel="nofollow" class="external text" href="http://hypothes.is/">Hypothes.is</a>, with an eye towards standardization informed by the <a rel="nofollow" class="external text" href="http://w3.org/community/openannotation/">W3C Open Annotation Community Group</a>.
</p>
<h2><span class="mw-headline" id="Status">Status</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="https://notes.webplatform.org/">Notes.WebPlatform.org</a> (a.k.a. "annotator") is deployed and running</li>
<li> Accounts server who’s taking care of authentication and OAuth authorizations is deployed and running</li>
<li> Annotations is enabled on those W3C specs:
<ul><li> <a rel="nofollow" class="external text" href="http://www.w3.org/TR/annotation-model/">Annotation Model</a></li></ul></li></ul>
<h3><span class="mw-headline" id="Email_Notifications">Email Notifications</span></h3>
<ul><li> E-mail notifications of annotations sent to W3C archive mailing list would work only when annotator is loaded on "w3.org" and "specs.webplatform.org".</li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="Current_issues">Current issues</span></h3>
<p>Refer to <a rel="nofollow" class="external text" href="https://github.com/webplatform/annotation-service/issues">webplatform/annotation-service issue tracker</a>
</p>
<h2><span class="mw-headline" id="Requirements_to_make_annotations_on_specs">Requirements to make annotations on specs</span></h2>
<ul><li> Credentials for identity on <b>accounts.webplatform.org</b> username and password</li>
<li> To get Mailing list archive
<ul><li> Documents must be hosted on "w3.org" or "specs.webplatform.org'"</li>
<li> Must contain </li></ul></li></ul>
<pre class="language-html5" data-lang="html5">
<a href="mailto:public-listname@w3.org" rel="reply-to">list name label</a>
</pre>
<ul><li> To make annotations on more than one URI but for the same spec, use canonical <i>link</i> tag in <i>head</i> of Document, e.g. </li></ul>
<pre class="language-html5" data-lang="html5">
<link rel="canonical" href="http://www.w3.org/TR/annotation-model/">
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="Interface">Interface</span></h2>
<ul><li> Toggle annotation functionality on or off
<ul><li> Can annotations be enabled without an extension, or must the user install an extension? Is there a script that could be hosted to do the same thing?</li></ul></li>
<li> Show annotations on demand</li>
<li> Optional: Add special "classes" of annotation, such as tests results, that display differently in the spec than simple text annotations (perhaps as icons for browser support)
<ul><li> <b>"editorial":</b> grammar change, typo, clarification</li>
<li> <b>"normative":</b> change to technical requirements of spec</li>
<li> <b>"request":</b> suggestion for new feature</li>
<li> <b>"testable":</b> marks section of spec as a testable assertion that needs one or more tests</li></ul></li>
<li> Provide separate document view of annotations outside sidebar context (e.g. a page that lists all annotations for a site, on a per-page, per-tag basis)</li>
<li> Provide status states, like:
<ul><li> <b>"new"</b> </li>
<li> <b>"accepted"</b> </li>
<li> <b>"assigned"</b> </li>
<li> <b>"resolved"</b> </li>
<li> <b>"rejected"</b> </li>
<li> might reuse existing hashtag functionality, with special behavior for certain states</li></ul></li>
<li> Provide different "annotation modes" specific to different tasks, filtering/hiding (based on tags) annotations for the other modes:
<ul><li> <b>"spec review"</b> </li>
<li> <b>"testable assertion"</b> </li>
<li> <b>"implementation and test status"</b> </li>
<li> <b>"documentation note or link"</b></li></ul></li></ul>
<h2><span class="mw-headline" id="Links">Links</span></h2>
<ul><li> <a href="/wiki/WPD:Annotations/Scenarios" title="WPD:Annotations/Scenarios">Scenarios</a></li>
<li> <a href="/wiki/WPD:Annotations/Workflows" title="WPD:Annotations/Workflows">Workflows</a></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.019 seconds
Real time usage: 0.021 seconds
Preprocessor visited node count: 48/1000000
Preprocessor generated node count: 76/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:11827-0!*!0!!*!*!*!esi=1 and timestamp 20150810164636 and revision id 100278
 -->
