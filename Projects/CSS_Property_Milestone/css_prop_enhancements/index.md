---
title: Suggested design enhancements for CSS properties
summary: "This page is a suggested mockup of how a CSS property page should look.\nCompared to the original font-size property page, there are several enhancements that would need to be implemented, and here is a list of the most significant. They're broken down into 3 basic categories: SKIN requiring mostly modified CSS, TEMPLATE requiring a change in how content is generated and flows onto the final HTML page, and FORM for changes in the text-input UI.\n"
tags:
  - Basic
  - Pages
uri: 'WPD:Projects/CSS Property Milestone/css prop enhancements'

---
## <span>Summary</span>

This page is a suggested mockup of how a CSS property page should look. Compared to the original font-size property page, there are several enhancements that would need to be implemented, and here is a list of the most significant. They're broken down into 3 basic categories: SKIN requiring mostly modified CSS, TEMPLATE requiring a change in how content is generated and flows onto the final HTML page, and FORM for changes in the text-input UI.

1.  **[SKIN]** Page title & summary are on the same line in this example; formatted as left/right justification with negative margin for overlay; this is fragile for cases where text in either runs too long.
2.  **[TEMPLATE]** Removed hard-coded "W3C Recommendation" text. If necessary, use a graphic to represent options or otherwise push it out of the main text flow.
3.  **[FORM]** "Specifies the size of text" is currently called a "summary", hopefully a simple sentence reflected in CSS property listings. The "This property sets the..." text offers more fleshed-out expository context not intended for listings. New field needed in template. What to call it? Summary-listing/Summary-extended?
4.  **[TEMPLATE]** Removed the implicit "Summary" & "Overview table" headings.
5.  **[TEMPLATE]** Under "Values", each \<dt\>/\<dd\> pair generate incorrectly in its own \<dl\>, which also produces unnecessary rules. Regardless, Suggest removing the rule formatting altogether as too busy.
6.  **[TEMPLATE/SKIN]** Heavily reformatted the property value overview table. Suggest shading all rows white here.
7.  **[TEMPLATE]** Each cell title ("Computed value"/"Initial value") should link to a concept page.
8.  **[TEMPLATE]** Inherited/Animatable use check/X icons rather than Yes/No text.
9.  **[FORM]** Current template only allows one media type, but property may well apply to more.
10. **[FORM]** Added an extra "Shorthand" field to overview table. Suggest a field in e.g. template for font-size to specify "font". Then font-size page would display "Shorthand: font" and font page would display "Shorthand for: font-family, font-size, font-weight" ... etc. for all properties that share the same shorthand.
11. **[TEMPLATE]** If property is marked as "inherited", should a syntax line & value description be automatically generated, or is it implicit, and is link to the "inherited" concept sufficient? Authors should not have to redundantly hard-code the "inherit" value at any rate.
12. **[FORM]** Fixed keyword values are bold, while variables are italic. The template provides no way to make that important distinction.
13. **[TEMPLATE/SKIN]** Default text for \<dd\> text in "Values" section should not be italic.
14. **[TEMPLATE]** Heavily reformatted & merged the compatibility table.
15. **[TEMPLATE]** Separated sub-issues in compatibility table (e.g. "vw/vh/vmin viewport units") with col-spanned table headings.
16. **[FORM]** Under compatibility notes, added less-than/greater-than/equals for explicit relation to version numbers.
17. **[TEMPLATE]** Removed redundant "See Also" head; used "Related Articles" instead.
18. **[TEMPLATE]** Pushed Specification info into "Related Articles" area
19. **[SKIN]** Reformatted most related-article links as 3-column to save space. (Can CSS formatting kick in after \# of list items exceeds a threshold? For 3-col format, should kick in with \>6 items to prevent orphans.)
20. **[FORM]** Directly embedded a sample page as an \<iframe\>. This is only a suggested UI. Hopefully dabblet sample pages can be presented this way, directly available on the page next to doc that describes it.
21. **[FORM]** Suggest adding explicit "example" template options for embedded samples, and for images showing the result of CSS formatting described in other code examples. (Suggest support for \>1 inline image, useful to clarify before/after scenarios.)
22. **[FORM]** Unclear what "Percentages" template option is intended for "Top-Level Summary", but it is not reflected in the resulting overview table.
23. **[TEMPLATE]** Headings may be reshuffled in output.
24. **[TEMPLATE]** If only one "Basic support" feature is considered in compatibility table, do not include explicit column span heading. If other sub-features are included, include explicit column spans.
25. **[TEMPLATE]** If appropriate to include explicit "inherit" or "initial" values within "Values" listing (not sure if it is), generate it from supplied metadata, and append it.
26. **[FORM]** Should there be a compatibility-table row for tablet-class browsers?
27. **[TEMPLATE]** When both prefix & unprefixed support is specified, include them in the same cell (e.g.: "5.0\<br/\>\<span class="tinyWebkitPrefix"\>3.0\</span\>"). Support is the crucial info to convey; having to implement redundant property prefixes is relatively trivial.
28. **[FORM]** Option to include sample syntax with each syntax item. E.g., along with variable "length" syntax item, a quick sample would be "1.5em" as it appears in the sample.
29. **[FORM]** Clarify the expected scope of each input field. What's the difference between "Usage" and "Notes"?
30. **[SKIN]** On basic principle, increase line-height within UL/OL/DL lists to match body text. I mean, just look at this page.

