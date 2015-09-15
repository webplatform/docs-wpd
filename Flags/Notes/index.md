---
title: Notes
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - 'Stub pages'
    - 'Property:Compatibility quality flag'
    - 'Property:Examples quality flag'
uri: 'WPD:Flags/Notes'

---
These are early notes about the Flags concept.

## <span>List of Categorization Flags</span>

**TODO**: These aren't implemented as "Flags" anymore, but normal form fields.

**We will revisit this whole thing in the future. On hold for now.**

These are flags that call out special status of articles. They do not represent work that must be done on the article, but rather properties of the things the article documents.

### <span>Standardization Status</span>

-   W3C\_Editors\_Draft
-   W3C\_Working\_Draft
-   W3C\_Candidate\_Recommendation
-   W3C\_Recommendation
-   Deprecated *For technologies that have been replaced or retracted, and are not recommended for use (but which are valuable to have for reference)*
-   Non-standard *For technologies that are not yet being standardized in any formal body, don't have 2 or more compatible implementations, and likely never will*
-   Defacto-standard *For technologies that are not yet standardized, but have 2 or more compatible implementations (modulo prefixes)*
-   Experimental *For technologies that are not yet being standardized, don't have 2 or more compatible implementations, but aim to one day be a standard*
-   *TODO: fill out this list with other standards bodies*

### <span>Browser Support</span>

Which browsers support this technology. 'Stable' means that that browser's most recent main release includes support. 'Preview' means that a preview release of that browser (e.g. a "Beta", "Alpha", or "Developer Preview") includes support. Only one of these tags should be included for each browser (and always the highest one).

-   Internet\_Explorer\_Stable
-   Firefox\_Stable
-   Safari\_Stable
-   Opera\_Stable
-   Chrome\_Stable
-   Internet\_Explorer\_Preview
-   Firefox\_Preview
-   Safari\_Preview
-   Opera\_Preview
-   Chrome\_Preview

### <span>Prefixes</span>

-   Prefix\_Everywhere *Every stable browser this ships in includes the prefix*
-   Prefix\_Somewhere *At least one stable browser ships this without a prefix*
-   Prefix\_Nowhere *No stable browser ships this with a prefix*

## <span>Design</span>

[Flag appearance and icons](/WPD:Design/Flags)

*These are even earlier notes:*

## <span>Design exploration</span>

### <span>Presentation</span>

Most warning templates are displayed as a banner, often at the top of a page before the content, but sometimes inline in the content itself. This is eye-catching, but can be distracting. The goal is to draw attention to the warning without detracting from the use of the page.

#### <span>Presentation Proposal</span>

One way to make is easy for people to assess the status easily is by having color-coded flags (e.g. CSS ribbons) with icon arranged along the top edge of the content area, each with a different indicator; mousing over these flags would raise a tooltip indicating the specific message.

(See [Top Ribbons](http://schepers.cc/wpd/Ribbons_Web_Elements_Preview2.jpg) for a visual example of this type of flag, and [Flags Mock](http://schepers.cc/webplatform/flags.svg) for a mock of what this could look like on this site.)

### <span>User Experience</span>

Traditionally, these flags are added by using a specific bit of Mediawiki markdown to the page. However, not everyone is familiar with the way to do this, and discovering the correct types of "content flags" is not obvious.

#### <span>UX Proposal</span>

Each page could feature a dropdown, with a Semantic Form backend, that automatically adds the appropriate flag template to the content (and also records who flagged it). This could look like a simple button that says "Flag this page", and expands into a set of options when pressed.

## <span>Implementation</span>

You can see the current implementation of flags in the WPD wiki at the page [css/properties/font-size](/css/properties/font-size), and at its corresponding [edit form](http://webplatform.org/d/index.php?title=css/properties/font-size&action=formedit).

The following are the pages involved in the data structure for setting flags:

"Form template" page (a reusable section of form syntax):

-   [Template:Flags form section](/Template:Flags_form_section)

Display template (will eventually get called by each main template):

-   [Template:Flags‎](/Template:Flags)

Property pages:

-   [Property:High-level issue](/Property:High-level_issue)
-   [Property:Content quality flag](/Property:Content_quality_flag)
-   [Property:Compatibility quality flag](/w/index.php?title=Property:Compatibility_quality_flag&action=edit&redlink=1)
-   [Property:Examples quality flag](/w/index.php?title=Property:Examples_quality_flag&action=edit&redlink=1)
-   [Property:Accessibility flag](/Property:Accessibility_flag)

And you can see one example of pages being aggregated by their flags, using a Semantic MediaWiki query, at [Stub pages](/w/index.php?title=Stub_pages&action=edit&redlink=1).

## <span>Requirements</span>

*This is a section kept for historical purposes only* The specific implementation for this will require coordination between content needs, technical implementation abilities, and visual design. Here are the requirements that solutions should satisfy (in decreasing order of importance). Note that we're using "flags" as the catch-all term for these, but they might end up not being displayed that way.

-   Allow flags to be displayed in different styles depending on which type they are. For example, some may show as little flags at the top of the content , some may be big banners at the top of the content, and others could be subtle and at the bottom of the content.
-   Allow some method of listing which pages have a given flag on them
-   Make it easy for editors to add or remove flags
-   *-- Big gap in priority--*
-   Allow some tags to be related in behavior/style/meaning (e.g. subclassing or categories)
-   Make it easy to define new tags as necessary *(this will be pretty rare)*
