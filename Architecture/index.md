==Site Structure==
The root of the wiki is <code>/docs</code>. This is the wiki where all documentation will exist, and it is collaborative.

The structure of the wiki is broken down into technology, characteristic, and article name. For example, the URL for the <code>href</code> attribute in HTML is <code>[[HTML/Attributes/href|http://webplatform.org/docs/html/attributes/href]]</code>. 

Article names are case-sensitive (e.g. <code>getAttribute</code>), but the proposal is to use lowercase names for the hierarchy (e.g. ''html'' instead of ''HTML''). Alternately, we could use uppercase page titles, such as <code>[[HTML/Attributes/href|http://webplatform.org/docs/HTML/Attributes/href]]</code>, but this seems error-prone. 

===Proposed Site Structure===

{{TODO| Should there be a sub-page structure for methods and properties of an interface? like DOM/interfaces/HTMLElement/properties/children ?}}
CHRIS - yes, I think there should be, but I'm not 100% sure of the best way to express this below.

{{TODO | Where would proprietary information live, if it were to be included? E.g. how to write a Mozilla extension.
CHRIS - the following is from Doug Schepers, and I think it ncely illustrates the conundrum we have here:

&lt;DOUG&gt;

I think there are 3 kinds of proprietary features:

#Content-based standards extensions: these are based on some technology, like CSS or DOM or HTML, usually with a well-defined extension mechanism (e.g., vendor prefixes, or namespaces), and which authors can be expected to include as content; these have an affect on how the content is rendered in the browser, and so are candidates for standardization, and should go in the typical hierarchy.  For example, '-webkit-radial-gradient' would go in 'docs/css/properties/-webkit-radial-gradient', and would be tagged as proprietary, and if standardized, might later be redirected to 'docs/css/properties/radial-gradient'.
#Non-standard content extensions: these are things that might be added to code, but which are unlikely to be standardized; typically, these will be server-side features, not client-side, or they only affect how the content is handled on the underlying platform, in which case they don't actually affect cross-browser compatibility. IE's Pinned Sites, which add values to the <meta> tags that only affect the way these sites are used on the Windows platform, are an example of this. These could be put under something like 'proprietary / vendor / product-name', and might very well simply have links to MSDN, MDN, Google, Facebook, Opera, or wherever.
#Framework extensions: These are things that have little or nothing to do with content, but rather things that let you extend the browser or browser engine. The only connection to the Web Platform is that it renders or otherwise uses the same kind of content code.  As I understand Google NaCl ("Native Client"), this would fall into that. These things could also be in 'proprietary / vendor / product-name', with external links. This stuff is pretty peripheral to what we're focused on, but since it's part of the ecosystem, and of interest to many of the same people, I wouldn't personally object to it being there.

BTW, 'browsers' is not a good topic name, because it might also hold stuff for authoring tools like DreamWeaver or Illustrator or Inkscape... but 'vendor' is also suboptimal, because multiple vendors might be involved (and OSS projects aren't "vendors"). 

I could easily see tutorials on how to create SVG including specific instructions about tool use...

&lt;/DOUG&gt;

CHRIS - How about this?

1. Inside each technology specific section, include ''tools'' and ''extensions'' sections, which could account for documents about tools related to the technology, and the content-based standards extensions Doug describes above. So we could have things like

css / extensions / sass
css / tools / style-master
css / tools / prefixr

js / extensions / jquery
js / extensions / node
js / extensions / dojo
js / tools / jslint
js / tools / jquery-UI
js / tools / jsdoc

svg / tools / inkscape

We could also have a ''tools'' and an ''extensions'' top level section to provide an alternative access point for these articles, in the same way we do for ''tutorials''. And some of the tools may well be related to different technologies, so would have to be tagged with multiple technology tags. For example, Dreamweaver relates to HTML, CSS, JS, PHP, etc.

In my mind, extensions are developments that result in you being able to write different code syntaxes to the standard technology they are based on, even if they might actually be compiles down to the standard behind the scenes. Tools are developments that just allow you to write the standard technology, but more easily/more effectively.

Of course, such definitions could easily become skewed and difficult to choose between for some developments, but we can work on this as we go.

2. For proprietary content and framework extensions, we should have these in a complete separate section - let's call it ''proprietary'' for now. I think ''vendor / product-name'' is actually ok - we can surely have the same page tagged with multiple vendors, causing them to appear on all the vendor's product lists. So we'd have

* proprietry
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

A couple more notes:

# I don't think prefixed properties such as '-webkit-radial-gradient' would have separate entries, e.g.  'docs/css/properties/-webkit-radial-gradient'. Rather, '-webkit-radial-gradient' is part of the browser support information for 'radial-gradient', so should be included as part of that document.
# I am not sure where tools and other technologies by non-browser vendors should exactly fit in. I guess this depends on what technology they are related to. For example, Adobe browser labs would perhaps go in the standards-related tools section, and be referenced from the html/css/js etc sections, as it does help with all of those. But there are probably more difficult examples to contend with.}}

* general-concepts
** general-concepts / IA
** general-concepts / accessibility-general-context
** general-concepts / usability
** general-concepts / UX
** general-concepts / user-profiling
** general-concepts / one-web
** general-concepts / progressive-enhancement
** general-concepts / responsive-design
** general-concepts / ''foo''
* html
** html / concepts
*** html / concepts / validation
*** html / concepts /quirksmode
*** html / concepts / ''foo''
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
** css / concepts
*** css / concepts / inheritance
*** css / concepts / the-cascade
*** css / concepts / vendor-prefixes
*** css / concepts /  ''foo''
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
** svg / concepts
*** svg / concepts / ''foo''
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
** mathml / concepts
*** mathml / concepts / ''foo''
** mathml / data-types
*** mathml / data-types / ''foo''
** mathml / elements
*** mathml / elements / ''foo''
** mathml / attributes
*** mathml / attributes / ''foo''
** mathml / tutorials
*** mathml / tutorials / ''foo'' 
* aria
** aria / concepts
*** aria / concepts / ''foo''
** aria / attributes
*** aria / attributes / ''foo''
** aria / tutorials
*** aria / tutorials / ''foo'' 
* apis
** apis / ''foo''
** apis / concepts
*** apis / concepts / ''foo''
*** apis / ''foo'' / ''foobar'' (interface)
**** apis / ''foo'' / ''foobar'' / ''baz'' method
**** apis / ''foo'' / ''foobar'' / ''baz'' property
** apis / ''quux'' (the Quux API has only one interface)
*** apis / ''quux'' / ''quux'' method
*** apis / ''quux'' / ''quux'' property
* dom
** dom / concepts
*** dom / concepts / ''foo''
** dom / apis
*** dom / apis / ''foo''
*** dom / apis / methods
**** dom / apis / methods / ''foo''
*** dom / apis / properties
**** dom / apis / properties / ''foo''
** dom / tutorials / ''foo'' 
* events
** events / ''foo''
** events / concepts
*** events / concepts / ''foo''
** events / apis
*** events / apis / methods
**** events / apis / methods / ''foo''
*** events / apis / properties
**** events / apis / properties / ''foo''
* js
** js / concepts
*** js / concepts / feature-detection
*** js / concepts / OOP
*** js / concepts / apis-general-context
*** js / concepts / ''foo''
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

==Alternative proposal (Alex)==

Basically, remove all "constants" from the URL, except for the top-level. All types of pages coexist within those top-level categories, and automatic listing pages are created via judicious use of SMW, categories, and queries.

* concepts/
* html/
** html / validation
** html /quirksmode
** html / ''foo'' (a concept)
** html/ ''bar'' (a data type)
** html / ''baz'' (an element)
** html  / ''foo2'' (an attribute)
* css/
** css / inheritance
** css / length (a datatype)
** css / font-size (a property)
** css / calc (a function)
** css / inherit (a keyword)
** css / sibling (a selector)
** css / keyframes (an atrule)
** css / properties (an auto-generated listing of all properties)
* apis/
** apis / ''foo'' (an interface)
** apis / ''foo'' / ''bar'' (a method or property on the interface
* svg/ ''you get the idea...''
* mathml/
* aria/
* dom/
* events/
* js/
* glossary/
* guides/
* tutorials/ (links to tech-specific tutorials)

==Alternative proposal (Peter)==

Using high-level grouping already in use:
* http://www.w3.org/html/logo/#the-technology
* http://goo.gl/L6sfa

Groupings
* Symantic markup
* CSS
* JavaScript
* Graphics and 3D
* Performance and Integration
* Offline and Storage
* Device Access
* Multimedia
* Mobile

This could look like this (with short category names):
* markup/
** markup / foo
** markup/ bar
* css/
** css / foo
** css / bar
* javascript/
** javascript / foo
** javascript / bar
* graphics
** graphics / foo
** graphics / bar
* connectivity
** connectivity/foo
** connectivity/foo
* performance
** performance / foo
** performance / bar
* storage
** storage
** storage / foo
** storage / bar
* device
** device / foo
** device / bar
* multimedia
* multimedia / foo
* multimedia / bar
* mobile
** mobile/ foo
** mobile / bar

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