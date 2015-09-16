---
title: MSDN CSS Property
uri: 'WPD:Content Requirements/MSDN CSS Property'

---
*This page is where you document the migration mapping for each "Category type" in your content that you identified in the spreadsheet tab.*

## Page Category Migration Mapping CSS Property

### URL Mapping

*Input URL*: <http://msdn.microsoft.com/en-us/library/ie/ms530759(v=vs.85).aspx>

*Final URL*: <http://webplatform.org/docs/css/properties/foo>

Note: the input URL does not contain any information required in output URL. The foo name comes from the \<h1\> title on the input page, with the content "foo property".

The url should not include the "property" suffix and should be lower-case with hypens separating the words, in line with the actual property-name in CSS (e.g. `font-size`, `background-position`)

#### Page Form

Use the [Form:CSS\_Property](/Form:CSS_Property) form.

### Field values

The output of the script should be effectively the concatenation of the PRE blocks below, but where the values have been filled in as described.

**Note**: All content should be run through an HTML-to-MediaWiki converter. All occurrences of vertical pipe must be replaced with {{!}} and all occurrences of equals should be replaced with {{=}}

#### Flags

    {{Flags
    |High-level issues=Needs Topics, Missing Relevant Sections, Data Not Semantic
    |Content=Incomplete, Not Neutral, Compatibility Incomplete, Examples Best Practices
    }}

#### Standardization Status

    {{Standardization_Status|}}

#### API Name

    {{API_Name}}

#### Summary

    {{Summary_Section|SUMMARY_INFORMATION}}

Where:

-   **SUMMARY\_INFORMATION** is the first \<p\> element in the content

#### CSS Property

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

Where:

-   '**INITIAL\_VALUE** comes from the Initial value field of the source's overview table
-   **APPLIES\_TO\_VALUE** comes from the Applies to value field of the sources' overview table
-   **INHERITED\_VALUE** comes from the Inherited field in the source's overview table, where "1" is Yes and "0" is "No"
-   **MEDIA\_VALUE** comes from the Media field in the source's overview table.
-   **CSS\_VALUES\_VALUE** is a concatenation of values (one for each header in the Property Values section of the source) of the form:

<!-- -->

    {{CSS Property Value
    |Data Type=HEADER_VALUE
    |Description=DESCRIPTION_VALUE
    }}

Where:

-   **HEADER\_VALUE** is the value of the header for that value in the source document
-   **DESCRIPTION\_VALUE** is the value of the paragraph for that value in the source document

#### Examples Section

    {{Examples_Section
    |Not_required=No
    |Examples=EXAMPLES_VALUE
    }}

Where:

-   **EXAMPLES\_VALUE** is a concatenation of the following code, one for each sample in the source document:

<!-- -->

    {{Single Example
    |Language=
    |Description=DESCRIPTION_VALUE
    |Code=CODE_VALUE
    |LiveURL=URL_VALUE
    }}

Where:

-   **DESCRIPTION\_VALUE** is the paragraph immediately before the link to the example in the source document
-   **CODE\_VALUE** is the unescaped value of the code from the example, following the general escaping rules for pipes and equals.
-   **URL\_VALUE** is equal to the href of the link preceding the example in the source document

#### Notes

    {{Notes_Section
    |Notes=NOTES_VALUE
    }}

Where:

-   **NOTES\_VALUE** is the content of the "Remarks" section in the source document

#### Topics

    {{Topics|CSS}}

#### External Attribution

    {{External_Attribution
    |Is_CC-BY-SA=No
    |Sources=MSDN
    |MSDN_link=LINK_VALUE
    }}

Where:

-   **LINK\_VALUE** is the link to the live URL of the source doc.
