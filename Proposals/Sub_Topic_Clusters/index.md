=Sub-topic Clusters in WPD=

We have [[WPD:Implementation_Patterns/Templates#Topics.2C_Topic_Clusters.2C_See_Also|topic clusters]], which were designed to automatically generate a section of related pages in the See Also section. The list of topic clusters in [[Property:Topic_Cluster]] is a single-level list that could conceivably grow out of control, given the sheer volume of the content in WPD.

==Problems==

* Too many pages being assigned to the same cluster resulting in overly-long lists of links. 

* There are two basic use cases for topic clusters:
** To group pages of the same type, i.e. css/border-style, css/border-right-style, css/border-left-style, etc.
** To provide a mix of reference, conceptual, and tutorial articles of the same topic.

] Our current implementation does not differentiate between these two use cases, resulting in lists that are a mix of both.