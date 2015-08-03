---
title: WPD:Content Requirements/MSDN HTML Attribute
---
<p><i>This page is where you document the migration mapping for each "Category type" in your content that you identified in the spreadsheet tab.</i>
</p>
<h2><span class="mw-headline" id="Page_Category_Migration_Mapping_HTML_Attribute">Page Category Migration Mapping HTML Attribute</span></h2>
<h3><span class="mw-headline" id="URL_Mapping">URL Mapping</span></h3>
<p><i>URL mapping is handled in the spreadsheet</i>
</p>
<h4><span class="mw-headline" id="Page_Form">Page Form</span></h4>
<p>You need to create <b>TWO</b> forms.
Use the <a href="/wiki/Form:Markup_Attribute" title="Form:Markup Attribute">Form:Markup_Attribute</a> form, as well as the <a href="/wiki/Form:API_Object_Property" title="Form:API Object Property">Form:API_Object_Property</a> form; the MSDN content is a mix of content that we want to be two different page types in WPD.
</p>
<h2><span class="mw-headline" id="Markup_Attribute">Markup_Attribute</span></h2>
<h3><span class="mw-headline" id="Field_values">Field values</span></h3>
<p>The output of the script should be effectively the concatenation of the PRE blocks below, but where the values have been filled in as described.
</p><p><b>Note</b>: All content should be run through an HTML-to-MediaWiki converter. All occurrences of vertical pipe must be replaced with {{!}} and all occurrences of equals should be replaced with {{=}}
</p>
<h4><span class="mw-headline" id="Flags">Flags</span></h4>
<pre>
{{Flags
|High-level issues=Stub, Needs Topics, Missing Relevant Sections, Data Not Semantic
|Content=Incomplete, Compatibility Incomplete, Examples Best Practices
}}
</pre>
<p><br />
</p>
<h4><span class="mw-headline" id="Standardization_Status">Standardization Status</span></h4>
<pre>
{{Standardization_Status|}}
</pre>
<h4><span class="mw-headline" id="API_Name">API Name</span></h4>
<pre>
{{API_Name}}
</pre>
<h4><span class="mw-headline" id="Summary">Summary</span></h4>
<pre>
{{Summary_Section|SUMMARY_INFORMATION}}
</pre>
<p>Where:
</p>
<ul><li> <b>SUMMARY_INFORMATION</b> is the first &lt;p&gt; element in the content</li></ul>
<h4><span class="mw-headline" id="Markup_Attribute_2">Markup Attribute</span></h4>
<pre>
{{Markup_Attribute
|Applies_to=URL
}}
</pre>
<p>Where:
</p>
<ul><li> <b>URL</b> is the url of the corresponding API_Object that this attribute applies to.</li></ul>
<p><br />
</p>
<div class="note">
<p><b>Note</b>:  There does not appear to be a way to figure this out from the attribute articles in MSDN, although the information must be held somewhere
</p>
</div>
<p><br />
</p>
<h4><span class="mw-headline" id="Examples_Section">Examples Section</span></h4>
<pre>
{{Examples_Section
|Not_required=No
|Examples=EXAMPLES_VALUE
}}
</pre>
<p>Where:
</p>
<ul><li> <b>EXAMPLES_VALUE</b> is a concatenation of the following code, one for each sample in the source document:</li></ul>
<pre>
{{Single Example
|Language=
|Description=DESCRIPTION_VALUE
|Code=CODE_VALUE
|LiveURL=URL_VALUE
}}
</pre>
<p>Where:
</p>
<ul><li> <b>DESCRIPTION_VALUE</b> is the paragraph immediately before the link to the example in the source document</li>
<li> <b>CODE_VALUE</b> is the unescaped value of the code from the example, following the general escaping rules for pipes and equals.</li>
<li> <b>URL_VALUE</b> is equal to the href of the link preceding the example in the source document</li></ul>
<h4><span class="mw-headline" id="Notes">Notes</span></h4>
<pre>
{{Notes_Section
|Notes=NOTES_VALUE
}}
</pre>
<p>Where:
</p>
<ul><li> <b>NOTES_VALUE</b> is the content of the "Remarks" section in the source document</li></ul>
<h4><span class="mw-headline" id="Topics">Topics</span></h4>
<pre>
{{Topics|HTML}}
</pre>
<h4><span class="mw-headline" id="External_Attribution">External Attribution</span></h4>
<pre>
{{External_Attribution
|Is_CC-BY-SA=No
|Sources=MSDN
|MSDN_link=LINK_VALUE
}}
</pre>
<p>Where:
</p>
<ul><li> <b>LINK_VALUE</b> is the link to the live URL of the source doc.</li></ul>
<h2><span class="mw-headline" id="API_Object_Property">API_Object_Property</span></h2>
<h3><span class="mw-headline" id="Field_values_2">Field values</span></h3>
<p>The output of the script should be effectively the concatenation of the PRE blocks below, but where the values have been filled in as described.
</p><p><b>Note</b>: All content should be run through an HTML-to-MediaWiki converter. All occurrences of vertical pipe must be replaced with {{!}} and all occurrences of equals should be replaced with {{=}}
</p>
<h4><span class="mw-headline" id="Flags_2">Flags</span></h4>
<pre>
{{Flags
|High-level issues=Stub, Needs Topics, Missing Relevant Sections, Data Not Semantic
|Content=Incomplete, Compatibility Incomplete, Examples Best Practices
}}
</pre>
<p><br />
</p>
<h4><span class="mw-headline" id="Standardization_Status_2">Standardization Status</span></h4>
<pre>
{{Standardization_Status|}}
</pre>
<h4><span class="mw-headline" id="API_Name_2">API Name</span></h4>
<pre>
{{API_Name}}
</pre>
<h4><span class="mw-headline" id="Summary_2">Summary</span></h4>
<pre>
{{Summary_Section|SUMMARY_INFORMATION}}
</pre>
<p>Where:
</p>
<ul><li> <b>SUMMARY_INFORMATION</b> is the first &lt;p&gt; element in the content</li></ul>
<h4><span class="mw-headline" id="API_Object_Property_2">API Object Property</span></h4>
<pre>
{{API_Object_Property
|Property_applies_to=OBJECT
|Read_only=
}}
</pre>
<p>Where:
</p>
<ul><li> <b>OBJECT</b> is the name of the last item in the DOM Information sections' inheritance hierarchy.</li></ul>
<p><br />
</p>
<div class="note">
<p><b>Note</b>:  There does not appear to be a way to figure this out from the attribute articles in MSDN, although the information must be held somewhere
</p>
</div>
<p><br />
</p>
<h4><span class="mw-headline" id="Examples_Section_2">Examples Section</span></h4>
<pre>
{{Examples_Section
|Not_required=No
|Examples=EXAMPLES_VALUE
}}
</pre>
<p>Where:
</p>
<ul><li> <b>EXAMPLES_VALUE</b> is a concatenation of the following code, one for each sample in the source document:</li></ul>
<pre>
{{Single Example
|Language=
|Description=DESCRIPTION_VALUE
|Code=CODE_VALUE
|LiveURL=URL_VALUE
}}
</pre>
<p>Where:
</p>
<ul><li> <b>DESCRIPTION_VALUE</b> is the paragraph immediately before the link to the example in the source document</li>
<li> <b>CODE_VALUE</b> is the unescaped value of the code from the example, following the general escaping rules for pipes and equals.</li>
<li> <b>URL_VALUE</b> is equal to the href of the link preceding the example in the source document</li></ul>
<h4><span class="mw-headline" id="Notes_2">Notes</span></h4>
<pre>
{{Notes_Section
|Notes=NOTES_VALUE
}}
</pre>
<p>Where:
</p>
<ul><li> <b>NOTES_VALUE</b> is the content of the "Remarks" section in the source document</li></ul>
<h4><span class="mw-headline" id="Topics_2">Topics</span></h4>
<pre>
{{Topics|DOM}}
</pre>
<h4><span class="mw-headline" id="External_Attribution_2">External Attribution</span></h4>
<pre>
{{External_Attribution
|Is_CC-BY-SA=No
|Sources=MSDN
|MSDN_link=LINK_VALUE
}}
</pre>
<p>Where:
</p>
<ul><li> <b>LINK_VALUE</b> is the link to the live URL of the source doc.</li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:1381-0!*!0!!*!*!*!esi=1 and timestamp 20150731182520 and revision id 4436
 -->
