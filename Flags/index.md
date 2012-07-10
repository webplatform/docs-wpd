One of the core concepts that we embraced early on was the idea of flagging content that is somehow controversial, whether it is out-of-date, missing information, factually incorrect, or specific to a particular vendor.

MediaWiki uses templates to provide these error messages.  For example see [http://www.mediawiki.org/wiki/Template:Warning Template:Warning]. This has the advantage that all pages that include a template are listed on a page for that template, so flagged content is more easily identified, and fixed if necessary (some flags may be intended as permanent, such as vendor-specific experiments).

Alex made demos of this functionality, and demoed it during a [https://www.w3.org/2012/06/18-webdoc-minutes.html#item01 telcon]. You can see an example of such a template ('''[[Template:Major_Style_Issue|"Major Style Issue"]]'''), how it is used on a '''[[CSS/Properties/border-radius|page that needs attention]]''', and the '''[[Special:WhatLinksHere/Template:Major_Style_Issue|list of pages]]''' that have that same issue (e.g. use that same template).

==Requirements==
The specific implementation for this will require coordination between content needs, technical implementation abilities, and visual design. Here are the requirements that solutions should satisfy (in decreasing order of importance). Note that we're using "flags" as the catch-all term for these, but they might end up not being displayed that way.

* Allow flags to be displayed in different styles depending on which type they are. For example, some may show as little flags at the top of the content , some may be big banners at the top of the content, and others could be subtle and at the bottom of the content.
* Allow some method of listing which pages have a given flag on them
* Make it easy for editors to add or remove flags
* ''-- Big gap in priority--''
* Allow some tags to be related in behavior/style/meaning (e.g. subclassing or categories)
* Make it easy to define new tags as necessary ''(this will be pretty rare)''

==List of Work Item Flags==
These articles mark work items that an article needs to bring it up to our quality standards. We seek to fix the issues that the flags address and get to zero work-item flags. Many of these flags are directly inspired by points in the [[WPD:Manual_Of_Style|Manual Of Style]].

===Content Quality (High-Level)===
* Template:Stub
* Template:Deletion_Candidate ''Applied to spam or irrelevant content''
* Template:Merge_Candidate ''Applied to duplicate content''
* Template:Copyright_Issue
* Template:Undescriptive_Title
* Template:Needs_Tags ''Applied to content that hasn't been processed to add all appropriate tags''

===Content Quality (Low-Level)===
====Content Quality====
* Template:Content_Outdated
* Template:Content_Incomplete
* Template:Content_Errors
* Template:Content_Not_Vendor_Neutral
* Template:Content_Biased_Voice
* Template:Content_Grammar_Spelling
* Template:Content_Needs_Best_Practices
* Template:Content_Missing_Specification_Links
* Template:Content_API_Documentation_Incomplete
* Template:Content_Includes_Discussion

====Compatibility Quality====
* Template:Compatibility_Outdated
* Template:Compatibility_Incomplete
* Template:Compatibility_Missing

====Examples Quality====
* Template:Examples_Needed
* Template:Examples_Errors ''Applied when the example code wouldn't work as described''
* Template:Examples_Best_Practices ''Applied when the example code works but doesn't follow best practices''

===Content Quality (Accessibility)===
* Template:Needs_Translation (missing language)
* Template:Needs_Accessibility
* Template:Outdated_Translation


==List of Categorization Flags==
These are flags that call out special status of articles. They do not represent work that must be done on the article, but rather properties of the things the article documents.
===Standardization Status===
* Template:W3C_Editors_Draft
* Template:W3C_Working_Draft
* Template:W3C_Candidate_Recommendation
* Template:W3C_Recommendation
* Template:Non-standard ''For technologies that are not yet being standardized in any formal body, don't have 2 or more compatible implementations, and likely never will''
* Template:Defacto-standard ''For technologies that are not yet standardized, but have 2 or more compatible implementations (modulo prefixes)''
* Template:Experimental ''For technologies that are not yet being standardized, don't have 2 or more compatible implementations, but aim to one day be a standard"
* ''TODO: fill out this list with other standards bodies''
===Browser Support===
Which browsers support this technology. 'Everywhere' means that more than 90% of that browsers' users world wide supports the technology (perhaps with prefixes). 'Stable' means that that browser's most recent stable release includes support. 'Preview' means that a preview release of that browser includes support. Only one of these tags should be included for each browser (and always the highest one).
* Template:Internet_Explorer_Everywhere
* Template:Firefox_Everywhere
* Template:Safari_Everywhere
* Template:Opera_Everywhere
* Template:Chrome_Everywhere
* Template:Internet_Explorer_Stable
* Template:Firefox_Stable
* Template:Safari_Stable
* Template:Opera_Stable
* Template:Chrome_Stable
* Template:Internet_Explorer_Preview
* Template:Firefox_Preview
* Template:Safari_Preview
* Template:Opera_Preview
* Template:Chrome_Preview
===Prefixes===
* Template:Prefix_Everywhere ''Every stable browser this ships in includes the prefix''
* Template:Prefix_Somewhere ''At least one stable browser ships this without a prefix''
* Template:Prefix_Nowhere ''No stable browser ships this with a prefix''






-------

==Design exploration==
===Presentation===
Most warning templates are displayed as a banner, often at the top of a page before the content, but sometimes inline in the content itself. This is eye-catching, but can be distracting.  The goal is to draw attention to the warning without detracting from the use of the page.

====Proposal====
One way to make is easy for people to assess the status easily is by having color-coded flags (e.g. CSS ribbons) with icon arranged along the top edge of the content area, each with a different indicator; mousing over these flags would raise a tooltip indicating the specific message.

(See [http://schepers.cc/wpd/Ribbons_Web_Elements_Preview2.jpg Top Ribbons] for a visual example of this type of flag, and [http://schepers.cc/webplatform/flags.svg Flags Mock] for a mock of what this could look like on this site.)

===User Experience===
Traditionally, these flags are added by using a specific bit of Mediawiki markdown to the page.  However, not everyone is familiar with the way to do this, and discovering the correct types of "content flags" is not obvious.

====Proposal====
Each page could feature a dropdown, with a Semantic Form backend, that automatically adds the appropriate flag template to the content (and also records who flagged it). This could look like a simple button that says "Flag this page", and expands into a set of options when pressed.