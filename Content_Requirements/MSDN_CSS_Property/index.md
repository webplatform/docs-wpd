---
title: WPD:Content Requirements/MSDN CSS Property
---
<p><i>This page is where you document the migration mapping for each "Category type" in your content that you identified in the spreadsheet tab.</i>
</p>
<h2><span class="mw-headline" id="Page_Category_Migration_Mapping_CSS_Property">Page Category Migration Mapping CSS Property</span></h2>
<h3><span class="mw-headline" id="URL_Mapping">URL Mapping</span></h3>
<p><i>Input URL</i>:  <a rel="nofollow" class="external free" href="http://msdn.microsoft.com/en-us/library/ie/ms530759(v=vs.85).aspx">http://msdn.microsoft.com/en-us/library/ie/ms530759(v=vs.85).aspx</a>
</p><p><i>Final URL</i>: <a rel="nofollow" class="external free" href="http://webplatform.org/docs/css/properties/foo">http://webplatform.org/docs/css/properties/foo</a>
</p><p>Note: the input URL does not contain any information required in output URL. The foo name comes from the &lt;h1&gt; title on the input page, with the content "foo property".
</p><p>The url should not include the "property" suffix and should be lower-case with hypens separating the words, in line with the actual property-name in CSS (e.g. <code>font-size</code>, <code>background-position</code>)
</p>
<h4><span class="mw-headline" id="Page_Form">Page Form</span></h4>
<p>Use the <a href="/wiki/Form:CSS_Property" title="Form:CSS Property">Form:CSS_Property</a> form.
</p>
<h3><span class="mw-headline" id="Field_values">Field values</span></h3>
<p>The output of the script should be effectively the concatenation of the PRE blocks below, but where the values have been filled in as described.
</p><p><b>Note</b>: All content should be run through an HTML-to-MediaWiki converter. All occurrences of vertical pipe must be replaced with {{!}} and all occurrences of equals should be replaced with {{=}}
</p>
<h4><span class="mw-headline" id="Flags">Flags</span></h4>
<pre>
{{Flags
|High-level issues=Needs Topics, Missing Relevant Sections, Data Not Semantic
|Content=Incomplete, Not Neutral, Compatibility Incomplete, Examples Best Practices
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
<h4><span class="mw-headline" id="CSS_Property">CSS Property</span></h4>
<pre>
{{CSS Property
|Initial value=INITIAL_VALUE
|Applies to=APPLIES_TO_VALUE
|Inherited=INHERITED_VALUE
|Media=MEDIA_VALUE
|Computed value=
|Animatable=
|CSS object model property=
|CSS percentages=
|Values=CSS_VALUES_VALUE
}}
</pre>
<p>Where:
</p>
<ul><li> '<b>INITIAL_VALUE</b> comes from the Initial value field of the source's overview table</li>
<li> <b>APPLIES_TO_VALUE</b> comes from the Applies to value field of the sources' overview table</li>
<li> <b>INHERITED_VALUE</b> comes from the Inherited field in the source's overview table, where "1" is Yes and "0" is "No"</li>
<li> <b>MEDIA_VALUE</b> comes from the Media field in the source's overview table.</li>
<li> <b>CSS_VALUES_VALUE</b> is a concatenation of values (one for each header in the Property Values section of the source) of the form:</li></ul>
<pre>
{{CSS Property Value
|Data Type=HEADER_VALUE
|Description=DESCRIPTION_VALUE
}}
</pre>
<p>Where:
</p>
<ul><li> <b>HEADER_VALUE</b> is the value of the header for that value in the source document</li>
<li> <b>DESCRIPTION_VALUE</b> is the value of the paragraph for that value in the source document</li></ul>
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
{{Topics|CSS}}
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

<!-- Saved in parser cache with key wpwiki:pcache:idhash:1182-0!*!0!!*!*!*!esi=1 and timestamp 20150731182342 and revision id 4300
 -->
