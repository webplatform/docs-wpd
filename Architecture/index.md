==Page Types==
These are types of pages we need for the site's information architecture:
* [[WPD:Architecture/Common_elements|Common page elements]]
* [[WPD:Architecture/API Reference_page|JS Object(/Class) Reference page]]
* [[WPD:Architecture/Function Reference page|JS Function/Method Reference page]]
* [[WPD:Architecture/Object property reference page|JS Object property reference page]]
* [[WPD:Architecture/Element Reference_page|HTML Element/DOM Object Reference page]]
* [[WPD:Architecture/Attribute Reference_page|Attribute Reference page]]
* [[WPD:Architecture/CSS Property Reference_page|CSS Property Reference page]]
* [[WPD:Architecture/Event Property Reference_page|Event Property Reference page]]
* [[WPD:Architecture/Protocol Reference_page|Protocol Reference page]]
* [[WPD:Architecture/Guide_page|Guide page]]
* [[WPD:Architecture/Tutorial_page|Tutorial page]]
* [[WPD:Architecture/Media_Content|Media Content]]

==Notes==
* We want aggregated pages, where content from other related pages is transcluded into a single page
** '''Example:''' the page for an interface will contain all the transcluded information from the individual method and property pages
** '''Example:''' the page for the '''font''' shorthand property will also contain the pages (or links to) font-family, font-feature-settings, font-kerning, font-language-override, font-size, font-size-adjust, font-stretch, font-style, font-variant, font-variant-ligatures, and font-weight properties
** '''Example:''' the page for an element will contain all the information for each of its attributes, which are each a separate page. ('''Note:''' what about the '''href''' attribute, which appears on multiple elements... maybe some thing like a sub-form, for context for each element where it appears?)

* For CSS property values (and other pages), we want not only a linked ''data type'' (e.g. <length>), but also an explanation of what the length means in that context, the range of values, etc. (Some sort of sub-form?)