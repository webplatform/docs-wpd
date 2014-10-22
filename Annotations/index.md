= Annotations =

This is a scratch space for adding annotations to WebPlatform.org and to W3C specifications.

''This page is itself actively being annotated using the existing Hypothes.is annotation extension and server. To see the annotations,  [http://hypothes.is/alpha/ install the extension or bookmarklet].''

== Current deliverables ==

Agreed by Dan W., Doug S., Randall L., Renoir B., expected to be delivered by Oct. 23 2014

# Make it work under IE 
## '''DONE''' Ability to make an annotation
## '''DONE''' Ability to login, we don’t even see "Sign in" ([https://docs.webplatform.org/wiki/File:20141022-IE11-cannot-login.png see screenshot])
##  Do not see speech bubble and tools ([https://docs.webplatform.org/wiki/File:20141022-IE11-cannot-login.png see screenshot])
# Public annotation should show up, even when visitor isn’t logged in  
# On a spec, when there’s an annotation, send an email to the archive  
## Use email specified in the HTML, e.g. <code><a rel="reply-to"  href="mailto:public-audio-comments@w3.org">foo</a></code>
# Safari, on a spec, when init SSO, if a cookie is already set; do not to try recover session. (temporary solution)  


== Background ==
We want to enable annotations on W3C specifications and on WebPlatform.org, as a way to provide feedback into specs and documentation.

The specific implementation we want to use will be based on the [http://okfnlabs.org/annotator/ Annotator project], as implemented and enhanced by [http://hypothes.is/ Hypothes.is], with an eye towards standardization informed by the [http://w3.org/community/openannotation/ W3C Open Annotation Community Group].

==Status==
* [https://notes.webplatform.org/stream Notes.WebPlatform.org] is deployed with latest version (df4392a)
* Accounts server is deployed and working

===SSO===
* Basic architecture done?
* Mixed results:
** Works in wiki by itself on Chrome, Opera, and mostly in Firefox
** Does not work in Safari, even with HTTPS and SSL; doesn't retain session when navigating to new page (maybe needs HTTPS, not HTTP in a hidden iframe)
* In combination with Wiki and Annotator:
** '''Blocking Issue:''' In Firefox, causes wiki (and browser) to lock up when authenticating (see [http://docs.webplatform.org/test/Main_Page Test wiki])

===Specs===
* Seems to work, except for IE

====Email Notifications====
* E-mail notifications of annotations are currently disabled, and should be enabled before deployment for W3C specs

===Wiki===
* Annotator works in wiki on Chrome, Opera
* '''Blocking Issue:''' Causes wiki (and browser) to lock up when authenticating (see [http://docs.webplatform.org/test/Main_Page Test wiki])

===Internet Explorer===
* Once connected to accounts; Wiki, notes, session state don’t sync
* Annotation sidebar buttons aren’t shown properly
* Cannot add/see annotations on a page
* Accounts server communication takes time. ''This is specific to Mozilla FxA and not the accounts server. Renoir will do that right after webplatformstaging.org is ready.''

Randall has provided a script "patch", but we're not sure how and where to deploy it.

<syntaxHighlight lang="javascript">
 window.hypothesisConfig = function () {
   return {
     app: jQuery('link[type="application/annotator+html"]').attr('href'),
     Heatmap: {container: '.annotator-frame'},
     Toolbar: {container: '.annotator-frame'},
     DomTextMapper: {skip: true}
   };
 };
</syntaxHighlight>

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