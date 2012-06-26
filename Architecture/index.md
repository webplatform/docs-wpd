==Site Structure==
The root of the wiki is <code>/docs</code>. This is the wiki where all documentation will exist, and it is collaborative.

The structure of the wiki is broken down into technology, characteristic, and article name. For example, the URL for the <code>href</code> attribute in HTML is <code>[[HTML/Attributes/href|http://webplatform.org/docs/HTML/Attributes/href]]</code>. 

===Proposed Categories===
* HTML
** HTML/Elements/foo
** HTML/Attributes/foo
** HTML/Objects/foo or HTML/APIs/foo
** HTML/Objects/Methods/foo
** HTML/APIs/Properties/foo
** HTML/Tutorials/Foo
** HTML/Events/foo
* CSS
** CSS/Properties/foo
** CSS/Selectors/foo
** CSS/APIs/foo
** CSS/APIs/Methods/foo
** CSS/APIs/Properties/foo
** CSS/Tutorials/Foo
*SVG
** SVG/Elements/foo
** SVG/Attributes/foo
** SVG/APIs/foo
** SVG/APIs/Methods/foo
** SVG/APIs/Properties/foo
** SVG/Tutorials/Foo
** SVG/Events/foo
* MathML
** MathML/Elements/foo
** MathML/Attributes/foo
** MathML/Tutorials/Foo
* ARIA
** ARIA/Attributes/foo
** ARIA/Tutorials/Foo
* DOM
** DOM/APIs/foo
** DOM/APIs/Methods/foo
** DOM/Events/foo
** DOM/Tutorials/Foo
* JavaScript
** JavaScript/Methods/foo
** JavaScript/Properties/foo
** JavaScript/Tutorials/Foo

===Content Requirements===
See also the [[WPD:Content_Requirements Content Requirements]] page.

==Page Types==
These are types of reference pages we need for the site's information architecture:
* [[WPD:Architecture/Common Aspects|Common Aspects]] which are included in all reference pages (transclusion?)
* [[WPD:Architecture/Object|API Object Reference]]
** [[WPD:Architecture/Object Method Reference|API Object Method Reference]]
** [[WPD:Architecture/Object property Reference|Object Object Property Reference]]
* [[WPD:Architecture/Element Reference|Markup Element Reference]]
* [[WPD:Architecture/Attribute Reference|Attribute Reference]]
* [[WPD:Architecture/CSS Selector Reference|CSS Selector Reference]]
* [[WPD:Architecture/CSS Property Reference|CSS Property Reference]]
* [[WPD:Architecture/Event Reference|Event Reference]]
* [[WPD:Architecture/Protocol Reference|Protocol Reference]]
* [[WPD:Architecture/Guide|Guide]]
* [[WPD:Architecture/Tutorial|Tutorial]]
* [[WPD:Architecture/Media_Content|Media Content]]

==Notes==
* We want aggregated pages, where content from other related pages is transcluded into a single page
** ''''Example:'''' the page for an interface will contain all the transcluded information from the individual method and property pages
** ''''Example:'''' the page for the '''font''' shorthand property will also contain the pages (or links to) font-family, font-feature-settings, font-kerning, font-language-override, font-size, font-size-adjust, font-stretch, font-style, font-variant, font-variant-ligatures, and font-weight properties
** ''''Example:'''' the page for an element will contain all the information for each of its attributes, which are each a separate page. ('''Note:''' what about the '''href''' attribute, which appears on multiple elements... maybe some thing like a sub-form, for context for each element where it appears?)

* For CSS property values (and other pages), we want not only a linked ''data type'' (e.g. <length>), but also an explanation of what the length means in that context, the range of values, etc. (Some sort of sub-form? see "Multiple-instance templates")