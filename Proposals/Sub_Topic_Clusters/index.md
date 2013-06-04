=Sub-topic Clusters in WPD=

We have [[WPD:Implementation_Patterns/Templates#Topics.2C_Topic_Clusters.2C_See_Also|topic clusters]], which were designed to automatically generate a section of related pages in the See Also section. This feature allows an author to create associations between articles without the author having to know about (or where to find) the articles.

==Problems==

* Too many pages being assigned to the same cluster resulting in overly-long lists of links. 
** [[css/selectors/attributes/whitespace]] (An example of a really long list under Selectors.)
* The list of [[Property:Topic_Cluster]] items is getting very long and unwieldy.
* Duplicate pages in topic clusters, and duplicate topic clusters. Examples:
** [[css/properties/font-family]] (Note CSS Fonts and Fonts)
* There are two basic use cases for topic clusters:
** To group pages of the same type, i.e. css/border-style, css/border-right-style, css/border-left-style, etc. (This is more of a navigation use case.)
** To provide a mix of reference, conceptual, and tutorial articles of the same topic. (This is more true to the intent of topic clusters.)
: Our current implementation does not differentiate between these two use cases, resulting in lists that are a mix of both.