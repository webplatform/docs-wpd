This is a scratch space for adding annotations to WebPlatform.org and to W3C specifications.

==Requirements==
* Credentials for identity (W3C, WebPlatform.org)
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
** might reuse existing hashtag functionality, with special behavior for certain states