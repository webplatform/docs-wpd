One of the core concepts that we embraced early on was the idea of flagging content that is somehow controversial, whether it is out-of-date, missing information, factually incorrect, or specific to a particular vendor.

MediaWiki uses templates to provide these error messages.  For example see [http://www.mediawiki.org/wiki/Template:Warning Template:Warning]. This has the advantage that all pages that include a template are listed on a page for that template, so flagged content is more easily identified, and fixed if necessary (some flags may be intended as permanent, such as vendor-specific experiments).

Alex made demos of this functionality, and demoed it during a [https://www.w3.org/2012/06/18-webdoc-minutes.html#item01 telcon]. You can see an example of such a template ('''[[Template:Major_Style_Issue|"Major Style Issue"]]'''), how it is used on a '''[[CSS/Properties/border-radius|page that needs attention]]''', and the '''[[Special:WhatLinksHere/Template:Major_Style_Issue|list of pages]]''' that have that same issue (e.g. use that same template).

==Presentation==
Most warning templates are displayed as a banner, often at the top of a page before the content, but sometimes inline in the content itself. This is eye-catching, but can be distracting.  The goal is to draw attention to the warning without detracting from the use of the page.

===Proposal===
One way to make is easy for people to assess the status easily is by having color-coded flags (e.g. CSS ribbons) with icon arranged along the top edge of the content area, each with a different indicator; mousing over these flags would raise a tooltip indicating the specific message.

(See [http://schepers.cc/wpd/Ribbons_Web_Elements_Preview2.jpg Top Ribbons] for a visual example of this type of flag, and [http://schepers.cc/webplatform/flags.svg Flags Mock] for a mock of what this could look like on this site.)

==User Experience==
Traditionally, these flags are added by using a specific bit of Mediawiki markdown to the page.  However, not everyone is familiar with the way to do this, and discovering the correct types of "content flags" is not obvious.

===Proposal===
Each page could feature a dropdown, with a Semantic Form backend, that automatically adds the appropriate flag template to the content (and also records who flagged it). This could look like a simple button that says "Flag this page", and expands into a set of options when pressed.

==List of Flags==
(Many of these flags are directly inspired by points in the [[WPD:Manual_Of_Style|Manual Of Style]].)

===Content Quality (High-Level)===
* Template:Stub
* Template:Spam
* Template:Content_Not_Relevant
* Template:Content_Duplicated
* Template:Content_Copyright_Issue
* Template:Nondescriptive_Title
* Template:Needs_Tags
* Template:Merge_Candidate
* Template:Deletion_Candidate

===Content Quality (Low-Level)===

====Content Quality====
* Template:Outdated_Content
* Template:Content_Errors
* Template:Content_Not_Vendor_Neutral
* Template:Missing_Specification_Links
* Template:Content_Incomplete
* Template:Content_Biased_Voice
* Template:Content_Grammar_Spelling_Guidelines
* Template:Content_Out_Of_Date
* Template:Content_Browser_Specific (name browser)
* Template:Content_Needs_Best_Practices
* Template:Needs_Citations
* Template:API_Documentation_Incomplete
* Template:Content_Includes_Discussion

====Compatibility Quality====
* Template:Compatibility_Outdated
* Template:Compatibility_Incomplete
* Template:Compatibility_Missing

====Examples Quality====
* Template:Needs_Examples
* Template:Code_Errors
* Template:Examples_Need_Best_Practices

===Content Quality (Accessibility)===
* Template:Needs_Translation (missing language)
* Template:Needs_Accessibility
* Template:Outdated_Translation