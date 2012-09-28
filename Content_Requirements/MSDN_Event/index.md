''This page is where you document the migration mapping for each "Category type" in your content that you identified in the spreadsheet tab.''

==Page Category Migration Mapping DOM Method==

===URL Mapping===
''URL mapping is handled in the spreadsheet''

====Page Form====
Use the [[Form:API_Object_Method]] form.

==API_Object_Method==

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

====API Object Property====
<pre>
{{API_Object_Method
|Parameters=METHOD_PARAMETERS
|Method_applies_to=OBJECT
|Example_object_name=EXAMPLE_NAME
|Return_value_name=RETURN_NAME
|Javascript_data_type=DATA_TYPE
|Return_value_description=RETURN_DESCRIPTION
}}
</pre>
Where:
* '''METHOD_PARAMETERS''' is a concatenation of Method Parameters, one for each on in the document (see next pre block).
* '''OBJECT''' points to the URL of the most specific DOMInterface this applies to
* '''EXAMPLE_NAME''' is the italicized word in the syntax section of the source document
* '''RETURN_NAME''' is just "object"
* '''DATA_TYPE''' is just "DOM Node" unless we know it to be more specific. (See [[Property:Javascript_data_type]] for a list that we may need to grow.
* '''RETURN_DESCRIPTION''' is the de-linked content in the "Return Value" section in source.
<pre>
{{Method Parameter
|Name=PARAMETER_NAME
|Data type=PARAMETER_TYPE
|Description=PARAMETER_DESCRIPTION
|Optional=
}}
</pre>
Where:
* '''PARAMETER_NAME''' is the part in italics for that section under Parameter in the original source
* '''PARAMETER_TYPE''' is the data type of the parameter as specified in the source, mapped to our data types: [[Property:Javascript_data_type]]
* '''PARAMETER_DESCRIPTION''' is the paragraph for that parameter in the source.

{{Note | We'll probably need a mapping from types in the MSDN docs to Types in our system (not an exhaustive list yet): [[Property:Javascript_data_type]]}}
{{Note | There does not appear to be a way to figure this out from the attribute articles in MSDN, although the information must be held somewhere}}

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