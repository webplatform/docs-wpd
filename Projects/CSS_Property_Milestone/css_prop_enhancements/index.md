{{Page_Title|Suggested design enhancements for CSS properties}}
{{Flags}}
{{Summary_Section|[http://letmespellitoutforyou.com/x/webplatform/font_size.html This page] is a suggested mockup of how a CSS property page should look.
Compared to the [[css/properties/font-size|original font-size property page]], there are several enhancements that would need to be implemented, and here is a list of the most significant. They're broken down into 3 basic categories: '''SKIN''' requiring mostly modified CSS, '''TEMPLATE''' requiring a change in how content is generated and flows onto the final HTML page, and '''FORM''' for changes in the text-input UI.
}}
{{Basic Page}}
# [SKIN] Page title & summary are on the same line in this example; formatted as left/right justification with negative margin for overlay; this is fragile for cases where text in either runs too long.
# [TEMPLATE] Removed hard-coded "W3C Recommendation" text. If necessary, use a graphic to represent options or otherwise push it out of the main text flow.
# [FORM] "Specifies the size of text" is currently called a "summary", hopefully a simple sentence reflected in CSS property listings.  The "This property sets the..." text offers more fleshed-out expository context not intended for listings. New field needed in template. What to call it?
# [TEMPLATE] Removed the implicit "Summary" & "Overview table" headings.
# [TEMPLATE] Under "Values", each &lt;dt&gt;/&lt;dd&gt; pair generate incorrectly in its own &lt;dl&gt;, which also produces unnecessary rules. Regardless, Suggest removing the rule formatting altogether as too busy.
# [TEMPLATE/SKIN] Heavily reformatted the property value overview table. Suggest shading all rows white here.
# [TEMPLATE] Each cell title ("Computed value"/"Initial value") should link to a concept page.
# [TEMPLATE] Inherited/Animatable use check/X icons rather than Yes/No text.
# [FORM] Current template only allows one media type, but property may well apply to more.
# [FORM] Added an extra "Shorthand" field to overview table. Suggest a field in e.g. template for font-size to specify "font". Then font-size page would display "Shorthand: font" and font page would display "Shorthand for: font-family, font-size, font-weight" ... etc. for all properties that share the same shorthand.
# [TEMPLATE] If property is marked as "inherited", should a syntax line & value description be automatically generated, or is it implicit, and is link to the "inherited" concept sufficient? Authors should not have to redundantly hard-code the "inherit" value at any rate.
# [FORM] Fixed keyword values are bold, while variables are italic. The template provides no way to make that important distinction.
# [TEMPLATE/SKIN] Default text for &lt;dd&gt; text in "Values" section should not be italic.
# [TEMPLATE] Heavily reformatted & merged the compatibility table.
# [TEMPLATE] Separated sub-issues in compatibility table (e.g. "vw/vh/vmin viewport units") with col-spanned table headings.
# [FORM] Under compatibility notes, added less-than/greater-than/equals for explicit relation to version numbers.
# [TEMPLATE] Removed redundant "See Also" head; used "Related Articles" instead. 
# [TEMPLATE] Pushed Specification info into "Related Articles" area
# [SKIN] Reformatted most related-article links as 3-column to save space. (Can CSS formatting kick in after # of list items exceeds a threshold?)
# [FORM] Directly embedded a sample page as an &lt;iframe&gt;. This is only a suggested UI. Hopefully dabblet sample pages can be presented this way, directly available on the page next to doc that describes it.
# [FORM] Suggest adding explicit "example" template options for embedded samples, and for images showing the result of CSS formatting described in other code examples. (Suggest support for >1 inline image, useful to clarify before/after scenarios.)
# [FORM] Unclear what "Percentages" template option is intended for "Top-Level Summary", but it is not reflected in the resulting overview table.
# [TEMPLATE] Headings may be reshuffled in output.
# [TEMPLATE] If only one "Basic support" feature is considered in compatibility table, do not include explicit column span heading. If other sub-features are included, include explicit column spans.
# [TEMPLATE] If appropriate to include explicit "inherit"  or "initial" values within "Values" listing (not sure if it is), generate it from supplied metadata, and append it.
# [FORM] Should there be a compatibility-table row for tablet-class browsers?
# [TEMPLATE] When both prefix & unprefixed support is specified, include them in the same cell (e.g.: "5.0&lt;br/>&lt;span class="tinyWebkitPrefix">3.0&lt;/span>"). Support is the crucial info; having to add redundant property prefixes is relatively trivial.
# [SKIN] Increase line-height within lists to match body text. I mean, just look at this page.
{{Notes_Section}}
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}