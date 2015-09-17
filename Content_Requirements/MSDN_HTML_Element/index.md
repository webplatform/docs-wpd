---
title: 'MSDN HTML Element'
uri: 'WPD:Content Requirements/MSDN HTML Element'

---
*This page is where you document the migration mapping for each "Category type" in your content that you identified in the spreadsheet tab.*

## Page Category Migration Mapping CSS Property

### URL Mapping

*URL mapping is handled in the spreadsheet*

#### Page Form

You need to create **TWO** forms. Use the [Form:Markup\_Element](/Form:Markup_Element) form, as well as the [Form:API\_Object](/Form:API_Object) form; the MSDN content is a mix of content that we want to be two different page types in WPD.

## Markup\_Element

### Field values

The output of the script should be effectively the concatenation of the PRE blocks below, but where the values have been filled in as described.

**Note**: All content should be run through an HTML-to-MediaWiki converter. All occurrences of vertical pipe must be replaced with {{!}} and all occurrences of equals should be replaced with {{=}}

#### Flags

    {{Flags
    |High-level issues=Stub, Needs Topics, Missing Relevant Sections, Data Not Semantic
    |Content=Incomplete, Compatibility Incomplete, Examples Best Practices
    }}

#### Standardization Status

    {{Standardization_Status|}}

#### API Name

    {{API_Name}}

#### Summary

    {{Summary_Section|SUMMARY_INFORMATION}}

Where:

-   **SUMMARY\_INFORMATION** is the first \<p\> element in the content

#### Markup Element

    {{Markup_Element
    |DOM_interface=URL
    }}

Where:

-   **URL** is the url of the corresponding API\_Object article being created at this import step.

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

    {{Topics|HTML,}}

#### External Attribution

    {{External_Attribution
    |Is_CC-BY-SA=No
    |Sources=MSDN
    |MSDN_link=LINK_VALUE
    }}

Where:

-   **LINK\_VALUE** is the link to the live URL of the source doc.

## API\_Object

### Field values

The output of the script should be effectively the concatenation of the PRE blocks below, but where the values have been filled in as described.

**Note**: All content should be run through an HTML-to-MediaWiki converter. All occurrences of vertical pipe must be replaced with {{!}} and all occurrences of equals should be replaced with {{=}}

#### Flags

    {{Flags
    |High-level issues=Stub, Needs Topics, Missing Relevant Sections, Data Not Semantic
    |Content=Incomplete, Compatibility Incomplete, Examples Best Practices
    }}

#### Standardization Status

    {{Standardization_Status|}}

#### API Name

    {{API_Name}}

#### Summary

    {{Summary_Section|SUMMARY_INFORMATION}}

Where:

-   **SUMMARY\_INFORMATION** is the first \<p\> element in the content

#### API Object

    {{API_Object
    |Subclass_of=dom/apis/OBJECT
    }}

Where:

-   **OBJECT** is the name of the last item in the DOM Information sections' inheritance hierarchy.

**Note**: The properties and methods on the page can be ignored because they will be affixed to the correct interface object when they are created during the import.

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

    {{Topics|DOM}}

#### External Attribution

    {{External_Attribution
    |Is_CC-BY-SA=No
    |Sources=MSDN
    |MSDN_link=LINK_VALUE
    }}

Where:

-   **LINK\_VALUE** is the link to the live URL of the source doc.
