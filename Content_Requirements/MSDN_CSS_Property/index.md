''This page is where you document the migration mapping for each "Category type" in your content that you identified in the spreadsheet tab.''

==Page Category Migration Mapping CSS Property==

===URL Mapping===
''Input URL'':  http://msdn.microsoft.com/en-us/library/ie/ms530759(v=vs.85).aspx
''Final URL'': http://webplatform.org/docs/css/properties/foo

Note: the input URL does not contain any information required in output URL. The foo name comes from the <nowiki><h1> </nowiki>title on the input page, with the content "foo property".

The url should not include the "property" suffix and should be lower-case with hypens separating the words, in line with the actual property-name in CSS (e.g. <code>font-size</code>, <code>background-position</code>)

====Page Form====
Use the [[Form:CSS_Property]] form.

===Field values===
The output of the script should be effectively the concatenation of the PRE blocks below, but where the values have been filled in as described.

'''Note''': All content should be run through an HTML-to-MediaWiki converter. All occurrences of vertical pipe must be replaced with <nowiki>{{!}}</nowiki> and all occurrences of equals should be replaced with <nowiki>{{=}}</nowiki>
====Flags====
<pre>
{{Flags
|High-level issues=Missing Relevant Sections, Data Not Semantic, Needs Flags
|Content=Incomplete, Not Neutral, Content Missing Specification Links
|Compatibility=Missing
|Examples=Examples are not best practices
|Editorial notes=
}}
</pre>


====Standardization_Status.1====
<pre>
{{Standardization_Status|}}
</pre>

====API_Name====
<pre>
{{API_Name}}
</pre>

====Summary====
<pre>
{{Summary_Section|SUMMARY_INFORMATION}}
</pre>
Where:
* '''SUMMARY_INFORMATION''' is the first <nowiki><p></nowiki> element in the content

====CSS Property====
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
Where:
* ''''INITIAL_VALUE''' comes from the Initial value field of the source's overview table
* '''APPLIES_TO_VALUE''' comes from the Applies to value field of the sources' overview table
* '''INHERITED_VALUE''' comes from the Inherited field in the source's overview table, where "1" is Yes and "0" is "No"
* '''MEDIA_VALUE''' comes from the Media field in the source's overview table.
* '''CSS_VALUES_VALUE''' is a concatenation of values (one for each header in the Property Values section of the source) of the form:
<pre>
{CSS Property Value
|Data Type=HEADER_VALUE
|Description=DESCRIPTION_VALUE
}}
</pre>
Where:
* '''HEADER_VALUE''' is the value of the header for that value in the source document
* '''DESCRIPTION_VALUE''' is the value of the paragraph for that value in the source document

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