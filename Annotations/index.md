= Annotations =

This is a scratch space for adding annotations to WebPlatform.org and to W3C specifications.

== Background ==
We want to enable annotations on W3C specifications and on WebPlatform.org, as a way to provide feedback into specs and documentation.

The specific implementation we want to use will be based on the [http://okfnlabs.org/annotator/ Annotator project], as implemented and enhanced by [http://hypothes.is/ Hypothes.is], with an eye towards standardization informed by the [http://w3.org/community/openannotation/ W3C Open Annotation Community Group].

==Status==
* [https://notes.webplatform.org/ Notes.WebPlatform.org] (a.k.a. "annotator") is deployed and running
* Accounts server who’s taking care of authentication and OAuth authorizations is deployed and running
* Annotations is enabled on those W3C specs:
** [http://www.w3.org/TR/annotation-model/ Annotation Model]

===Email Notifications===
* E-mail notifications of annotations sent to W3C archive mailing list would work only when annotator is loaded on "w3.org" and "specs.webplatform.org".


===Current issues===
Refer to [https://github.com/webplatform/annotation-service/issues webplatform/annotation-service issue tracker]

==Requirements to make annotations on specs==
* Credentials for identity on '''accounts.webplatform.org''' username and password
* To get Mailing list archive
** Documents must be hosted on "w3.org" or "specs.webplatform.org'"
** Must contain <syntaxHighlight><a href="mailto:public-listname@w3.org" rel="reply-to">list name label</a></syntaxHighlight>
* To make annotations on more than one URI but for the same spec, use canonical ''link'' tag in ''head'' of Document, e.g. <syntaxHighlight><link rel="canonical" href="http://www.w3.org/TR/annotation-model/"></syntaxHighlight>

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