---
title: MSDN Event
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - 'Template:TODO: Update this with the new fields from Event'
uri: 'WPD:Content Requirements/MSDN Event'

---
*This page is where you document the migration mapping for each "Category type" in your content that you identified in the spreadsheet tab.*

## <span>Page Category Migration Mapping Event</span>

### <span>URL Mapping</span>

*URL mapping is handled in the spreadsheet*

#### <span>Page Form</span>

Use the [Form:Event](/Form:Event) form.

[Template:TODO: Update this with the new fields from Event](/w/index.php?title=Template:TODO:_Update_this_with_the_new_fields_from_Event&action=edit&redlink=1)

## <span>API\_Object</span>

### <span>Field values</span>

The output of the script should be effectively the concatenation of the PRE blocks below, but where the values have been filled in as described.

**Note**: All content should be run through an HTML-to-MediaWiki converter. All occurrences of vertical pipe must be replaced with {{!}} and all occurrences of equals should be replaced with {{=}}

#### <span>Flags</span>

    {{Flags
    |High-level issues=Stub, Needs Topics, Missing Relevant Sections, Data Not Semantic
    |Content=Incomplete, Compatibility Incomplete, Examples Best Practices
    }}

#### <span>Standardization Status</span>

    {{Standardization_Status|}}

#### <span>API Name</span>

    {{API_Name}}

#### <span>Summary</span>

    {{Summary_Section|SUMMARY_INFORMATION}}

Where:

-   **SUMMARY\_INFORMATION** is the first \<p\> element in the content

#### <span>API Object Property</span>

    {{API_Object
    |Subclass_of=PARENT
    |Overview=OVERVIEW
    }}

Where:

-   **PARENT** is the URL (starting after ...docs/) that points to the superclass (t

**Note**: There does not appear to be a way to figure this out from the attribute articles in MSDN, although the information must be held somewhere

-   **OVERVIEW** is the content of the first paragraph in the article

#### <span>Examples Section</span>

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

#### <span>Notes</span>

    {{Notes_Section
    |Notes=NOTES_VALUE
    }}

Where:

-   **NOTES\_VALUE** is the content of the "Remarks" section in the source document

#### <span>Topics</span>

    {{Topics|DOM}}

#### <span>External Attribution</span>

    {{External_Attribution
    |Is_CC-BY-SA=No
    |Sources=MSDN
    |MSDN_link=LINK_VALUE
    }}

Where:

-   **LINK\_VALUE** is the link to the live URL of the source doc.
