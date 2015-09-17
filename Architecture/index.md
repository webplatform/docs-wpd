---
title: 'Site architecture'
summary: 'Here we describe how the site content is organized so that you can find it by following the path in the URL.'
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - HTML
    - CSS
    - SVG
    - js
    - proprietary
    - 'WPD:Architecture/Markup Structure'
    - 'WPD:Architecture/JavaScript Statements'
    - 'WPD:Architecture/JavaScript Operator'
    - 'WPD:Architecture/Regex metacharacter'
    - 'WPD:Architecture/Data type'
    - 'WPD:Architecture/Constants'
    - 'WPD:Architecture/CSS @rule Reference'
    - 'WPD:Architecture/CSS Function Reference'
    - 'WPD:Architecture/CSS Keyword Reference'
    - 'WPD:Architecture/CSS Media Features'
    - 'WPD:Architecture/Glossary'
uri: 'WPD:Architecture'

---
## Summary

Here we describe how the site content is organized so that you can find it by following the path in the URL.

**Note**: ***IMPORTANT***: Content below this box is old. Please refer to [WPD:Content/Topic\_Hierarchy](/WPD:Content/Topic_Hierarchy) and [WPD:Getting\_Started](/WPD:Getting_Started) for the latest best practices.

# Ask us!

If you have a question about how to contribute to webplatform.org, you'll find us chatting away at **irc.freenode.org** in the **\#webplatform** chat room. See [Help](/WPD:Help) for more information.

-   [Topics](/WPD:Architecture/Topics)

## Site Structure

The root of the wiki is `docs.webplatform.org/wiki/`. This is the wiki where all documentation will exist, and it is collaborative.

The structure of the wiki is broken down into technology, characteristic, and article name. For example, the URL for the `href` attribute in HTML is `html/attributes/href`.

Article names are case-sensitive (e.g. `getAttribute`). but the proposal is to use lowercase names for the hierarchy (e.g. *html* instead of *HTML*).

### Proposed Site Structure

See also [Topic Hierarchy](/WPD:Content/Topic_Hierarchy).

-   [concepts](/concepts)
    -   concepts / accessibility
    -   concepts / information architecture
    -   concepts / internet and web
    -   concepts / one web
    -   concepts / progressive enhancement
    -   concepts / programming
    -   concepts / mobile web
    -   concepts / responsive design
    -   concepts / security
    -   concepts / ux
    -   concepts / *foo*
-   [HTML](/w/index.php?title=HTML&action=edit&redlink=1)
    -   HTML / *foo*
    -   HTML / validation
    -   HTML / quirks mode
    -   HTML / data-types
        -   HTML / data-types / *foo*
    -   HTML / Elements
        -   HTML / Elements / *foo*
    -   HTML / attributes
        -   HTML / attributes / *foo*
    -   HTML / apis
        -   HTML / apis / *foo*
        -   HTML / apis / methods
            -   HTML / apis / methods / *foo*
        -   HTML / apis / properties
            -   HTML / apis / properties / *foo*
    -   HTML/tutorials (read-only) a list of tutorials categorized as HTML
-   [CSS](/w/index.php?title=CSS&action=edit&redlink=1)
    -   CSS / *foo*
    -   CSS / inheritance
    -   CSS / cascade
    -   CSS / vendor prefixes
    -   CSS / data-types
    -   CSS / data-types / length
        -   CSS / data-types / *foo*
    -   CSS / properties
        -   CSS / properties / *foo*
    -   CSS / functions
        -   CSS / functions / "foo"
    -   CSS / keywords
        -   CSS / keywords / "foo"
    -   CSS / selectors
        -   CSS / selectors / *foo*
    -   CSS / atrules
        -   CSS / atrules / "foo"
    -   CSS / apis
        -   CSS / apis / *foo*
        -   CSS / apis / methods
            -   CSS / apis / methods / *foo*
        -   CSS / apis / properties
            -   CSS / apis / properties / *foo*
    -   CSS / tutorials (a list of tutorials categorized as CSS)
-   [SVG](/w/index.php?title=SVG&action=edit&redlink=1)
    -   SVG / *foo*
    -   SVG / data-types
        -   SVG / data-types / *foo*
    -   SVG / Elements
        -   SVG / Elements / *foo*
    -   SVG / attributes
        -   SVG / attributes / *foo*
    -   SVG / apis
        -   SVG / apis / *foo*
        -   SVG / apis / methods
            -   SVG / apis / methods / *foo*
        -   SVG / apis / properties
            -   svg / apis / properties / *foo*
    -   SVG / tutorials (a list of tutorials categorized as SVG)
-   [mathml](/mathml)
    -   mathml / *foo*
    -   mathml / data-types
        -   mathml / data-types / *foo*
    -   mathml / elements
        -   mathml / elements / *foo*
    -   mathml / attributes
        -   mathml / attributes / *foo*
    -   mathml / tutorials (a list of tutorials categorized as MathML)
-   [xml](/xml)
    -   xml / *foo*
    -   xml / data-types
        -   xml / data-types / *foo*
    -   xml / elements
        -   xml / elements / *foo*
    -   xml / attributes
        -   xml / attributes / *foo*
    -   xml / tutorials (a list of tutorials categorized as XML)
-   [aria](/aria)
    -   aria / *foo*
    -   aria / attributes
        -   aria / attributes / *foo*
    -   aria / tutorials (a list of tutorials categorized as ARIA)
-   [apis](/apis)
    -   apis / *foo*
        -   apis / *foo* / *foobar* (interface)
            -   apis / *foo* / *foobar* / *baz* method
            -   apis / *foo* / *foobar* / *baz* property
    -   apis / *quux* (the Quux API has only one interface)
        -   apis / *quux* / *quux* method
        -   apis / *quux* / *quux* property
-   [dom](/dom)
    -   dom / *foo*
    -   dom / apis
        -   dom / apis / *foo*
        -   dom / apis / methods
            -   dom / apis / methods / *foo*
        -   dom / apis / properties
            -   dom / apis / properties / *foo*
    -   dom / tutorials (a list of tutorials categorized as DOM)
-   [events](/events)
    -   events / *foo*
    -   events / apis
        -   events / apis / methods
            -   events / apis / methods / *foo*
        -   events / apis / properties
            -   events / apis / properties / *foo*
    -   dom / tutorials (a list of tutorials categorized as events)
-   [js](/w/index.php?title=js&action=edit&redlink=1)
    -   js / feature-detection
    -   js / OOP
    -   js / apis-general-context
    -   js / *foo*
    -   js / data-types
        -   js / data-types / string
        -   js / data-types / number
        -   js / data-types / *foo*
    -   js / syntax
        -   js / syntax / *foo*
    -   js / objects
        -   js / objects / *foo*
    -   js / functions
        -   js / functions / *foo*
    -   js / statements
        -   js / statements / *foo*
    -   js / operators
        -   js / operators / *foo*
    -   js / tutorials (a list of tutorials categorized as Javascript)
    -   js / libraries
        -   js / libraries / jQuery
        -   js / libraries / *foo*
-   [glossary](/glossary)
-   [tutorials](/tutorials) (links to tech-specific tutorials)
    -   tutorials / web standards curriculum
    -   tutorials / responsive web design
    -   tutorials / accessibility
    -   tutorials / *foo*
-   [proprietary](/w/index.php?title=proprietary&action=edit&redlink=1)
    -   proprietary / microsoft
        -   proprietary / microsoft / pinned sites
        -   proprietary / microsoft / silverlight
        -   proprietary / microsoft / *foo*
    -   proprietary / opera
        -   proprietary / opera / extensions
        -   proprietary / opera / *foo*
    -   proprietary / google
        -   proprietary / google / NaCl
        -   proprietary / google / *foo*
    -   proprietary / apple
        -   proprietary / apple / *foo*
    -   proprietary / mozilla
        -   proprietary / mozilla / *foo*
    -   proprietary / *foo*

### Content Requirements

See also the [Content Requirements](/WPD:Content_Requirements) page.

## Page Types

These are types of reference pages we need for the site's information architecture.

**Note:** These are basic primitives that need unique templates in MediaWiki; having a unique template allows us to perform queries and aggregations, and supplements the page hierarchy architecture structure as a method of categorization; another way of categorizing them is through MediaWiki categories that can be added to each page. There may be some templates that only reuse the same basic elements as other pages, such as page name, summary, syntax, and example; it is still useful to have unique templates for them for purposes of organization and querying.

-   [WPD:Architecture/Common Aspects](/WPD:Architecture/Common_Aspects) which are included in all reference pages (transclusion?)
-   [WPD:Architecture/Element Reference](/WPD:Architecture/Element_Reference)
    -   Examples: elements for HTML, SVG, MathML
-   [WPD:Architecture/Attribute Reference](/WPD:Architecture/Attribute_Reference)
    -   Examples: attributes for HTML, SVG, and MathML elements
-   [WPD:Architecture/Markup Structure](/w/index.php?title=WPD:Architecture/Markup_Structure&action=edit&redlink=1)
    -   Examples: Doctypes, comments, CDATA sections, entities (?)
-   [WPD:Architecture/JavaScript Statements](/w/index.php?title=WPD:Architecture/JavaScript_Statements&action=edit&redlink=1)
    -   Subcategories: Control structures, declarations
-   [WPD:Architecture/JavaScript Operator](/w/index.php?title=WPD:Architecture/JavaScript_Operator&action=edit&redlink=1)
-   [WPD:Architecture/Regex metacharacter](/w/index.php?title=WPD:Architecture/Regex_metacharacter&action=edit&redlink=1)
    -   Subcategories: Expressions (character classes, grouping etc), Quantifiers, Anchors, Assertions, Flags
-   [WPD:Architecture/Object](/WPD:Architecture/Object)
    -   [WPD:Architecture/Object Method Reference](/WPD:Architecture/Object_Method_Reference)
    -   [WPD:Architecture/Object property Reference](/WPD:Architecture/Object_property_Reference)
-   [WPD:Architecture/Data type](/w/index.php?title=WPD:Architecture/Data_type&action=edit&redlink=1)
    -   CSS Property types, HTML and SVG attribute value types
    -   In JS, every primitive also corresponds to an object. E.g. there are numbers and Number objects. Will they both be described by the same page or different pages?
-   [WPD:Architecture/Constants](/w/index.php?title=WPD:Architecture/Constants&action=edit&redlink=1)
    -   This might be for constants in APIs, but also might include things like a table of color names, ascii entity codes, etc.
-   [CSS @rule Reference](/w/index.php?title=WPD:Architecture/CSS_@rule_Reference&action=edit&redlink=1)
-   [CSS Selector Reference](/WPD:Architecture/CSS_Selector_Reference)
    -   Note: Pseudo-classes and pseudo-elements and other selectors will all use the same template but we should have tags to differentiate them.
-   [CSS Property Reference](/WPD:Architecture/CSS_Property_Reference)
-   [CSS Function Reference](/w/index.php?title=WPD:Architecture/CSS_Function_Reference&action=edit&redlink=1)
-   [CSS Keyword Reference](/w/index.php?title=WPD:Architecture/CSS_Keyword_Reference&action=edit&redlink=1)
-   [CSS Media Features](/w/index.php?title=WPD:Architecture/CSS_Media_Features&action=edit&redlink=1)
    -   for media queries, import rules, style declarations
-   [WPD:Architecture/Event Reference](/WPD:Architecture/Event_Reference)
-   [WPD:Architecture/Protocol Reference](/WPD:Architecture/Protocol_Reference)
-   [WPD:Architecture/Tutorial](/WPD:Architecture/Tutorial)
-   [WPD:Architecture/Media\_Content](/WPD:Architecture/Media_Content)
-   [WPD:Architecture/Glossary](/w/index.php?title=WPD:Architecture/Glossary&action=edit&redlink=1)

## Article Naming Conventions

Suggested Titling/Naming Convention for Article Types (Dave Gash).

See [WPD:Manual\_Of\_Style\#Descriptive\_Titles Manual Of Style, Descriptive Titles](/WPD:Manual_Of_Style#Descriptive_Titles_Manual_Of_Style.2C_Descriptive_Titles)

### Notes

-   Should attributes in the same language that apply to different elements with different values for each have a different page, or should there be an aggregate page with multiple sections?

## Notes

-   We want aggregated pages, where content from other related pages is transcluded into a single page
    -   '**Example:'** the page for an interface will contain all the transcluded information from the individual method and property pages
    -   '**Example:'** the page for the **font** shorthand property will also contain the pages (or links to) font-family, font-feature-settings, font-kerning, font-language-override, font-size, font-size-adjust, font-stretch, font-style, font-variant, font-variant-ligatures, and font-weight properties
    -   '**Example:'** the page for an element will contain all the information for each of its attributes, which are each a separate page. (**Note:** what about the **href** attribute, which appears on multiple elements... maybe some thing like a sub-form, for context for each element where it appears?)

-   For CSS property values (and other pages), we want not only a linked *data type* (e.g. \<length\>), but also an explanation of what the length means in that context, the range of values, etc. (Some sort of sub-form? see "Multiple-instance templates")
