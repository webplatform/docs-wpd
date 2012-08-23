==Site Structure==
The root of the wiki is <code>/docs</code>. This is the wiki where all documentation will exist, and it is collaborative.

The structure of the wiki is broken down into technology, characteristic, and article name. For example, the URL for the <code>href</code> attribute in HTML is <code>[[HTML/Attributes/href|http://webplatform.org/docs/html/attributes/href]]</code>. 

Article names are case-sensitive (e.g. <code>getAttribute</code>), but the proposal is to use lowercase names for the hierarchy (e.g. ''html'' instead of ''HTML''). Alternately, we could use uppercase page titles, such as <code>[[HTML/Attributes/href|http://webplatform.org/docs/HTML/Attributes/href]]</code>, but this seems error-prone. 

===Proposed Site Structure===
{{TODO|Other sections to add: css/concepts/ (e.g. inheritance, initial-value, etc), css/data-types/length, etc}}

{{TODO| Should there be a sub-page structure for methods and properties of an interface? like DOM/interfaces/HTMLElement/properties/children ?}}

{{TODO | Where would proprietary information live, if it were to be included? E.g. how to write a Mozilla extension.}}

* html
** html / elements
*** html / elements / ''foo''
** html / attributes
*** html / attributes / ''foo''
** html / apis
*** html / apis / ''foo''
*** html / apis / methods
**** html / apis / methods / ''foo''
*** html / apis / properties
**** html / apis / properties / ''foo''
** html / tutorials
*** html / tutorials / ''foo''
* css
** css / properties
*** css / properties / ''foo''
** css / functions
*** css / functions / "foo"
** css / keywords
*** css / keywords / "foo"
** css / selectors
*** css / selectors / ''foo''
** css / atrules
*** css / atrules / "foo"
** css / apis
*** css / apis / ''foo''
*** css / apis / methods
**** css / apis / methods / ''foo''
*** css / apis / properties
**** css / apis / properties / ''foo''
** css / tutorials
*** css / tutorials / ''foo'' 
* svg
** svg / elements
*** svg / elements / ''foo''
** svg / attributes
*** svg / attributes / ''foo''
** svg / apis
*** svg / apis / ''foo''
*** svg / apis / methods
**** svg / apis / methods / ''foo''
*** svg / apis / properties
**** svg / apis / properties / ''foo''
** svg / tutorials
*** svg / tutorials / ''foo''
* mathml
** mathml / elements
*** mathml / elements / ''foo''
** mathml / attributes
*** mathml / attributes / ''foo''
** mathml / tutorials
*** mathml / tutorials / ''foo'' 
* aria
** aria / attributes
*** aria / attributes / ''foo''
** aria / tutorials
*** aria / tutorials / ''foo'' 
* apis
** apis / ''foo''
*** apis / ''foo'' / ''foobar'' (interface)
**** apis / ''foo'' / ''foobar'' / ''baz'' method
**** apis / ''foo'' / ''foobar'' / ''baz'' property
** apis / ''quux'' (the Quux API has only one interface)
*** apis / ''quux'' / ''quux'' method
*** apis / ''quux'' / ''quux'' property
* dom
** dom / apis
*** dom / apis / ''foo''
*** dom / apis / methods
**** dom / apis / methods / ''foo''
*** dom / apis / properties
**** dom / apis / properties / ''foo''
** dom / tutorials / ''foo'' 
* events
** events / ''foo''
** events / apis
*** events / apis / methods
**** events / apis / methods / ''foo''
*** events / apis / properties
**** events / apis / properties / ''foo''
* js
** js / syntax
*** js / syntax / ''foo''
** js / objects
*** js / objects / ''foo''
** js / functions
*** js / functions / ''foo''
** js / statements
*** js / statements / ''foo''
** js / operators
*** js / operators / ''foo''
** js / tutorials
*** js / tutorials / ''foo''
** js / libraries
*** js / libraries / ''foo''
* glossary
* guides
* tutorials (links to tech-specific tutorials)
** tutorials / web standards curriculum
** tutorials / responsive web design
** tutorials / accessibility
** tutorials / ''foo''

===Content Requirements===
See also the [[WPD:Content_Requirements|Content Requirements]] page.

==Page Types==
These are types of reference pages we need for the site's information architecture.

'''Note:''' These are basic primitives that need unique templates in MediaWiki; having a unique template allows us to perform queries and aggregations, and supplements the page hierarchy architecture structure as a method of categorization; another way of categorizing them is through MediaWiki categories that can be added to each page. There may be some templates that only reuse the same basic elements as other pages, such as page name, summary, syntax, and example; it is still useful to have unique templates for them for purposes of organization and querying.

* [[WPD:Architecture/Common Aspects|Common Aspects]] which are included in all reference pages (transclusion?)
* [[WPD:Architecture/Element Reference|Markup Element Reference]]
** Examples: elements for HTML, SVG, MathML
* [[WPD:Architecture/Attribute Reference|Attribute Reference]]
** Examples: attributes for HTML, SVG, and MathML elements
* [[WPD:Architecture/Markup Structure|Markup Structure]]
** Examples: Doctypes, comments, CDATA sections, entities (?)
* [[WPD:Architecture/JavaScript Statements|JavaScript Statements]]
** Subcategories: Control structures, declarations
* [[WPD:Architecture/JavaScript Operator|JavaScript Operator]]
* [[WPD:Architecture/Regex metacharacter|Regex metacharacter]]
** Subcategories: Expressions (character classes, grouping etc), Quantifiers, Anchors, Assertions, Flags
* [[WPD:Architecture/Object|API Object Reference]]
** [[WPD:Architecture/Object Method Reference|API Object Method Reference]]
** [[WPD:Architecture/Object property Reference|API Object Property Reference]]
* [[WPD:Architecture/Data type|Data type Reference]]
** CSS Property types, HTML and SVG attribute value types
** In JS, every primitive also corresponds to an object. E.g. there are numbers and Number objects. Will they both be described by the same page or different pages?
* [[WPD:Architecture/Constants|Constants]]
** This might be for constants in APIs, but also might include things like a table of color names, ascii entity codes, etc.
* [[WPD:Architecture/CSS @rule Reference|CSS @rule Reference]]
* [[WPD:Architecture/CSS Selector Reference|CSS Selector Reference]]
** Note: Pseudo-classes and pseudo-elements and other selectors will all use the same template but we should have tags to differentiate them.
* [[WPD:Architecture/CSS Property Reference|CSS Property Reference]]
* [[WPD:Architecture/CSS Function Reference|CSS Function Reference]]
* [[WPD:Architecture/CSS Keyword Reference|CSS Keyword Reference]]
* [[WPD:Architecture/CSS Media Features|CSS Media Features]]
** for media queries, import rules, style declarations
* [[WPD:Architecture/Event Reference|Event Reference]]
* [[WPD:Architecture/Protocol Reference|Protocol Reference]]
* [[WPD:Architecture/Guide|Guide]]
* [[WPD:Architecture/Tutorial|Tutorial]]
* [[WPD:Architecture/Media_Content|Media Content]]

=== Notes ===
* Should attributes in the same language that apply to different elements with different values for each have a different page, or should there be an aggregate page with multiple sections?

==Notes==
* We want aggregated pages, where content from other related pages is transcluded into a single page
** ''''Example:'''' the page for an interface will contain all the transcluded information from the individual method and property pages
** ''''Example:'''' the page for the '''font''' shorthand property will also contain the pages (or links to) font-family, font-feature-settings, font-kerning, font-language-override, font-size, font-size-adjust, font-stretch, font-style, font-variant, font-variant-ligatures, and font-weight properties
** ''''Example:'''' the page for an element will contain all the information for each of its attributes, which are each a separate page. ('''Note:''' what about the '''href''' attribute, which appears on multiple elements... maybe some thing like a sub-form, for context for each element where it appears?)

* For CSS property values (and other pages), we want not only a linked ''data type'' (e.g. <length>), but also an explanation of what the length means in that context, the range of values, etc. (Some sort of sub-form? see "Multiple-instance templates")