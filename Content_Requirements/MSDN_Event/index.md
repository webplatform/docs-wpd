---
title: WPD:Content Requirements/MSDN Event
---
<p><i>This page is where you document the migration mapping for each "Category type" in your content that you identified in the spreadsheet tab.</i>
</p>
<h2><span class="mw-headline" id="Page_Category_Migration_Mapping_Event">Page Category Migration Mapping Event</span></h2>
<h3><span class="mw-headline" id="URL_Mapping">URL Mapping</span></h3>
<p><i>URL mapping is handled in the spreadsheet</i>
</p>
<h4><span class="mw-headline" id="Page_Form">Page Form</span></h4>
<p>Use the <a href="/wiki/Form:Event" title="Form:Event">Form:Event</a> form.
</p><p><a href="/w/index.php?title=Template:TODO:_Update_this_with_the_new_fields_from_Event&amp;action=edit&amp;redlink=1" class="new" title="Template:TODO: Update this with the new fields from Event (page does not exist)">Template:TODO: Update this with the new fields from Event</a>
</p>
<h2><span class="mw-headline" id="API_Object">API_Object</span></h2>
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
<h4><span class="mw-headline" id="API_Object_Property">API Object Property</span></h4>
<pre>
{{API_Object
|Subclass_of=PARENT
|Overview=OVERVIEW
}}
</pre>
<p>Where:
</p>
<ul><li> <b>PARENT</b> is the URL (starting after ...docs/) that points to the superclass (t</li></ul>
<p><br />
</p>
<div class="note">
<p><b>Note</b>:  There does not appear to be a way to figure this out from the attribute articles in MSDN, although the information must be held somewhere
</p>
</div>
<ul><li> <b>OVERVIEW</b> is the content of the first paragraph in the article</li></ul>
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
{{Topics|DOM}}
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

<!-- Saved in parser cache with key wpwiki:pcache:idhash:1439-0!*!0!!*!*!*!esi=1 and timestamp 20150731182547 and revision id 5923
 -->
