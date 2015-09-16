---
title: MSDN DOM Method
uri: 'WPD:Content Requirements/MSDN DOM Method'

---
*This page is where you document the migration mapping for each "Category type" in your content that you identified in the spreadsheet tab.*

## Page Category Migration Mapping DOM Method

### URL Mapping

*URL mapping is handled in the spreadsheet*

#### Page Form

Use the [Form:API\_Object\_Method](/Form:API_Object_Method) form.

## API\_Object\_Method

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

#### API Object Property

    {{API_Object_Method
    |Parameters=METHOD_PARAMETERS
    |Method_applies_to=OBJECT
    |Example_object_name=EXAMPLE_NAME
    |Return_value_name=RETURN_NAME
    |Javascript_data_type=DATA_TYPE
    |Return_value_description=RETURN_DESCRIPTION
    }}

Where:

-   **METHOD\_PARAMETERS** is a concatenation of Method Parameters, one for each on in the document (see next pre block).
-   **OBJECT** points to the URL of the most specific DOMInterface this applies to
-   **EXAMPLE\_NAME** is the italicized word in the syntax section of the source document
-   **RETURN\_NAME** is just "object"
-   **DATA\_TYPE** is just "DOM Node" unless we know it to be more specific. (See [Property:Javascript\_data\_type](/Property:Javascript_data_type) for a list that we may need to grow.
-   **RETURN\_DESCRIPTION** is the de-linked content in the "Return Value" section in source.

<!-- -->

    {{Method Parameter
    |Name=PARAMETER_NAME
    |Data type=PARAMETER_TYPE
    |Description=PARAMETER_DESCRIPTION
    |Optional=
    }}

Where:

-   **PARAMETER\_NAME** is the part in italics for that section under Parameter in the original source
-   **PARAMETER\_TYPE** is the data type of the parameter as specified in the source, mapped to our data types: [Property:Javascript\_data\_type](/Property:Javascript_data_type)
-   **PARAMETER\_DESCRIPTION** is the paragraph for that parameter in the source.

**Note**: We'll probably need a mapping from types in the MSDN docs to Types in our system (not an exhaustive list yet): [Property:Javascript\_data\_type](/Property:Javascript_data_type)

**Note**: There does not appear to be a way to figure this out from the attribute articles in MSDN, although the information must be held somewhere

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
