This is a scratch space for adding annotations to WebPlatform.org and to W3C specifications.

 This page is actively being annotated using the existing Hypothes.is annotation extension and server. To see the annotations,  [http://hypothes.is/alpha/ install the extension or bookmarklet].

== Background ==
We want to enable annotations on W3C specifications and on WebPlatform.org, as a way to provide feedback into specs and documentation.

The specific implementation we want to use will be based on the [http://okfnlabs.org/annotator/ Annotator project], as implemented and enhanced by [http://hypothes.is/ Hypothes.is], with an eye towards standardization informed by the [http://w3.org/community/openannotation/ W3C Open Annotation Community Group].

==Requirements==
* Credentials for identity: WebPlatform.org username and password
* Adding and searching custom tags
** typo, request for clarification, bug, suggested replacement text, etc.
* Reflecting comments in the mailing list
** Consider sending a custom headers via email, so replies can be federated, keeping discussion threaded and complete
** If emails responses are sent to mailing list, links to those emails (or body text) should be added to annotation thread
** Consider adding tags in new custom email header
** Allow admin curation of links (adding links, or removing irrelevant links on same thread)
* Annotation server hosted on WebPlatform.org
* Persist annotations across different versions of same spec
** May require "canonical URL"?
** Alert users when they start annotating an older version of a document (requires knowing the current version)
* API so bots can add annotations, change states, etc.

==Interface==
* Toggle annotation functionality on or off
** Can annotations be enabled without an extension, or must the user install an extension? Is there a script that could be hosted to do the same thing?
* Show annotations on demand
* Optional: Add special "classes" of annotation, such as tests results, that display differently in the spec than simple text annotations (perhaps as icons for browser support)
** '''"editorial":''' grammar change, typo, clarification
** '''"normative":''' change to technical requirements of spec
** '''"request":''' suggestion for new feature
** '''"testable":''' marks section of spec as a testable assertion that needs one or more tests
* Provide separate document view of annotations outside sidebar context (e.g. a page that lists all annotations for a site, on a per-page, per-tag basis)
* Provide status states, like:
** '''"new"''' 
** '''"accepted"''' 
** '''"assigned"''' 
** '''"resolved"''' 
** '''"rejected"''' 
** might reuse existing hashtag functionality, with special behavior for certain states
* Provide different "annotation modes" specific to different tasks, filtering/hiding (based on tags) annotations for the other modes:
** '''"spec review"''' 
** '''"testable assertion"''' 
** '''"implementation and test status"''' 
** '''"documentation note or link"'''

==Links==
* [[WPD:Annotations/Scenarios|Scenarios]]
* [[WPD:Annotations/Workflows|Workflows]]