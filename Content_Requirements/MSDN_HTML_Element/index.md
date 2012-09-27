''This page is where you document the migration mapping for each "Category type" in your content that you identified in the spreadsheet tab.''

==Page Category Migration Mapping CSS Property==

===URL Mapping===
''URL mapping is handled in the spreadsheet''

====Page Form====
You need to create '''TWO''' forms.
Use the [[Form:Markup_Element]] form, as well as the [[Form:API_Object]] form; the MSDN content is a mix of content that we want to be two different page types in WPD.

==Markup_Element==

===Field values===
The output of the script should be effectively the concatenation of the PRE blocks below, but where the values have been filled in as described.

'''Note''': All content should be run through an HTML-to-MediaWiki converter. All occurrences of vertical pipe must be replaced with <nowiki>{{!}}</nowiki> and all occurrences of equals should be replaced with <nowiki>{{=}}</nowiki>
====Flags====
<pre>
{{Flags
|High-level issues=Stub, Needs Topics, Missing Relevant Sections, Data Not Semantic
|Content=Incomplete, Compatibility Incomplete, Examples Best Practices
}}
</pre>


====Standardization Status====
<pre>
{{Standardization_Status|}}
</pre>

====API Name====
<pre>
{{API_Name}}
</pre>

====Summary====
<pre>
{{Summary_Section|SUMMARY_INFORMATION}}
</pre>
Where:
* '''SUMMARY_INFORMATION''' is the first <nowiki><p></nowiki> element in the content

====Markup Element====
<pre>
{{Markup_Element
|DOM_interface=URL
}}
</pre>
Where:
* '''URL''' is the url of the corresponding API_Object article being created at this import step. 

====Examples Section====
<pre>
{{Examples_Section
|Not_required=No
|Examples=EXAMPLES_VALUE
}}
</pre>

Where:
* '''EXAMPLES_VALUE''' is a concatenation of the following code, one for each sample in the source document:
<pre>
{{Single Example
|Language=
|Description=DESCRIPTION_VALUE
|Code=CODE_VALUE
|LiveURL=URL_VALUE
}}
</pre>

Where:
* '''DESCRIPTION_VALUE''' is the paragraph immediately before the link to the example in the source document
* '''CODE_VALUE''' is the unescaped value of the code from the example, following the general escaping rules for pipes and equals.
* '''URL_VALUE''' is equal to the href of the link preceding the example in the source document

====Notes====
<pre>
{{Notes_Section
|Notes=NOTES_VALUE
}}
</pre>

Where:
* '''NOTES_VALUE''' is the content of the "Remarks" section in the source document

====Topics====
<pre>
{{Topics|HTML,}}
</pre>

====External Attribution====
<pre>
{{External_Attribution
|Is_CC-BY-SA=No
|Sources=MSDN
|MSDN_link=LINK_VALUE
}}
</pre>

Where:
* '''LINK_VALUE''' is the link to the live URL of the source doc.

==API_Object==

===Field values===
The output of the script should be effectively the concatenation of the PRE blocks below, but where the values have been filled in as described.

'''Note''': All content should be run through an HTML-to-MediaWiki converter. All occurrences of vertical pipe must be replaced with <nowiki>{{!}}</nowiki> and all occurrences of equals should be replaced with <nowiki>{{=}}</nowiki>
====Flags====
<pre>
{{Flags
|High-level issues=Stub, Needs Topics, Missing Relevant Sections, Data Not Semantic
|Content=Incomplete, Compatibility Incomplete, Examples Best Practices
}}
</pre>


====Standardization Status====
<pre>
{{Standardization_Status|}}
</pre>

====API Name====
<pre>
{{API_Name}}
</pre>

====Summary====
<pre>
{{Summary_Section|SUMMARY_INFORMATION}}
</pre>
Where:
* '''SUMMARY_INFORMATION''' is the first <nowiki><p></nowiki> element in the content

====API Object====
<pre>
{{API_Object
|Subclass_of=dom/apis/OBJECT
}}
</pre>
Where:
* '''OBJECT''' is the name of the last item in the DOM Information sections' inheritance hierarchy.

{{Note| The properties and methods on the page can be ignored because they will be affixed to the correct interface object when they are created during the import.}}

====Examples Section====
<pre>
{{Examples_Section
|Not_required=No
|Examples=EXAMPLES_VALUE
}}
</pre>

Where:
* '''EXAMPLES_VALUE''' is a concatenation of the following code, one for each sample in the source document:
<pre>
{{Single Example
|Language=
|Description=DESCRIPTION_VALUE
|Code=CODE_VALUE
|LiveURL=URL_VALUE
}}
</pre>

Where:
* '''DESCRIPTION_VALUE''' is the paragraph immediately before the link to the example in the source document
* '''CODE_VALUE''' is the unescaped value of the code from the example, following the general escaping rules for pipes and equals.
* '''URL_VALUE''' is equal to the href of the link preceding the example in the source document

====Notes====
<pre>
{{Notes_Section
|Notes=NOTES_VALUE
}}
</pre>

Where:
* '''NOTES_VALUE''' is the content of the "Remarks" section in the source document

====Topics====
<pre>
{{Topics|DOM}}
</pre>

====External Attribution====
<pre>
{{External_Attribution
|Is_CC-BY-SA=No
|Sources=MSDN
|MSDN_link=LINK_VALUE
}}
</pre>

Where:
* '''LINK_VALUE''' is the link to the live URL of the source doc.