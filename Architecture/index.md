==Site Structure==
The root of the wiki is <code>/docs</code>. This is the wiki where all documentation will exist, and it is collaborative.

The structure of the wiki is broken down into technology, characteristic, and article name. For example, the URL for the <code>href</code> attribute in HTML is <code>[[HTML/Attributes/href|http://webplatform.org/docs/html/attributes/href]]</code>. 

Article names are case-sensitive (e.g. <code>getAttribute</code>), but the proposal is to use lowercase names for the hierarchy (e.g. ''html'' instead of ''HTML''). Alternately, we could use uppercase page titles, such as <code>[[HTML/Attributes/href|http://webplatform.org/docs/HTML/Attributes/href]]</code>, but this seems error-prone. 

===Proposed Site Structure===

* concepts
** concepts / IA
** concepts / accessibility-general-context
** concepts / usability
** concepts / UX
** concepts / user-profiling
** concepts / one-web
** concepts / progressive-enhancement
** concepts / responsive-design
** concepts / ''foo''
* html
** html  / ''foo''
** html  / validation
** html  / quirksmode
** html / data-types
*** html / data-types / ''foo''
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
** css  /  ''foo''
** css  / inheritance
** css  / the-cascade
** css  / vendor-prefixes
** css / data-types
** css / data-types / length
*** css / data-types / ''foo''
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
* svg / ''foo''
** svg / data-types
*** svg / data-types / ''foo''
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
** mathml  / ''foo''
** mathml / data-types
*** mathml / data-types / ''foo''
** mathml / elements
*** mathml / elements / ''foo''
** mathml / attributes
*** mathml / attributes / ''foo''
** mathml / tutorials
*** mathml / tutorials / ''foo'' 
* xml
** xml / ''foo''
** xml / data-types
*** xml / data-types / ''foo''
** xml / elements
*** xml / elements / ''foo''
** xml / attributes
*** xml / attributes / ''foo''
** xml / tutorials
*** xml / tutorials / ''foo'' 
* aria
** aria / ''foo''
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
* dom / ''foo''
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
** js  / feature-detection
** js  / OOP
** js  / apis-general-context
** js  / ''foo''
** js / data-types
*** js / data-types / string
*** js / data-types / number
*** js / data-types / ''foo''
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
* proprietary
** proprietary / microsoft
*** proprietary / microsoft / pinned sites
*** proprietary / microsoft / silverlight
*** proprietary / microsoft / ''foo''
** proprietary / opera
*** proprietary / opera / extensions
*** proprietary / opera / ''foo''
** proprietary / google
*** proprietary / google / NaCl
*** proprietary / google / ''foo''
** proprietary / apple
*** proprietary / apple / ''foo''
** proprietary / mozilla
*** proprietary / mozilla / ''foo''
** proprietary / ''foo''


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

==Article Naming Conventions==
'''Suggested Titling/Naming Convention for Article Types (Dave Gash)'''

For clarity in both creating and reading, article types should be consistently titled at the primary heading level, each according to its content's primary information type. Most content can be assigned one of three information types: task, concept, or reference. Each article type should use a consistent titling scheme so that the author can accurately place it in the information hierarchy and so that the reader can infer its content type from the title without further reading.

I suggest adopting the following title conventions for specific article types:
*'''About''' for articles with concept, background, overview, and similar content
**Examples: "About Audio Types", "About Flexbox", "About Visibility"
*'''Gerunds''' for articles with tutorial, task, procedure, process, and similar content
**Examples: "Using the <audio> Tag", "Drawing on the Canvas", "Calling the getLocation() Function" 
*'''Nouns''' and '''Noun phrases''' for articles with reference, syntactical, validity, and similar content
**Examples: "<audio> Tag Attributes", "Valid .moveTo() Values", "Latitude and Longitude Notation"

Also, I suggest that such a convention, once agreed upon, be added to the [[WPD:Manual_Of_Style|Manual of Style]].

==Notes==
* We want aggregated pages, where content from other related pages is transcluded into a single page
** ''''Example:'''' the page for an interface will contain all the transcluded information from the individual method and property pages
** ''''Example:'''' the page for the '''font''' shorthand property will also contain the pages (or links to) font-family, font-feature-settings, font-kerning, font-language-override, font-size, font-size-adjust, font-stretch, font-style, font-variant, font-variant-ligatures, and font-weight properties
** ''''Example:'''' the page for an element will contain all the information for each of its attributes, which are each a separate page. ('''Note:''' what about the '''href''' attribute, which appears on multiple elements... maybe some thing like a sub-form, for context for each element where it appears?)

* For CSS property values (and other pages), we want not only a linked ''data type'' (e.g. <length>), but also an explanation of what the length means in that context, the range of values, etc. (Some sort of sub-form? see "Multiple-instance templates")