= Adding to our Docs pages =

== Change summary note ==

  <nowiki>Installing Compatibility tables, see [[WPD:Projects/CompaTables/Adding_to_our_content]]</nowiki>

== Summary ==

Which MediaWiki templates are involved to display the compatibility tables data.

== What has been done ==

For instructions on how to set in place, refer to [http://docs.webplatform.org/wiki/Template:Compatibility#How_to_use Template:Compatibility] at '''How to use'''.

=== To do ===
* Remove the <nowiki>{{Compatibility_Form_Section}}</nowiki> in the Form view, if you see any.

=== Templates changed ===
Each of them has <nowiki>{{Compatibility_Form_Section}}</nowiki> replaced by the new '''Compatibility''' template in both ''Form'' and ''Template'' ... templates.

You should see a block similar to the following on each sections:

  <nowiki>{{Compatibility</nowiki>
  |topic=webapi
  |feature=<nowiki>{{#titleparts:{{PAGENAME}}||-1}}</nowiki>
  |format=table
  <nowiki>}}</nowiki>

* '''CSS_Property''', using ''topic="css"'', in [http://docs.webplatform.org/wiki/Template:CSS_Property Template], [http://docs.webplatform.org/wiki/Form:CSS_Property  Form]
** '''category:''' [http://docs.webplatform.org/wiki/Category:CSS_Properties Category:CSS_Properties]
** '''topic page:''' [[css/properties]]
** '''example pages:''' [[css/properties/align-content]],  [[css/properties/border-radius]]

* '''CSS_Selector''', using ''topic="css"'', in [http://docs.webplatform.org/wiki/Template:CSS_Selector Template], [http://docs.webplatform.org/wiki/Form:CSS_Selector Form]
** '''category:''' [http://docs.webplatform.org/wiki/Category:CSS_Selectors Category:CSS_Selectors]
** '''topic page:'''
** '''example pages:''' [[css/selectors/attributes/hyphen]], [[css/selectors/combinators/general_sibling]], [[css/selectors/attributes/existence]]

* '''CSS_Function''', using ''topic="css"'', in [http://docs.webplatform.org/wiki/Template:CSS_Function Template], [http://docs.webplatform.org/wiki/Form:CSS_Function Form]
** '''category:''' [http://docs.webplatform.org/wiki/Category:CSS_Functions Category:CSS_Functions]
** '''topic page:'''
** '''example pages:''' [[css/functions/brightness]], [[css/functions]]

* '''CSS_At_Rule''', using ''topic="css"'', in [http://docs.webplatform.org/wiki/Template:CSS_At_Rule Template], [http://docs.webplatform.org/wiki/Form:CSS_At_Rule Form]
** '''category:''' [http://docs.webplatform.org/wiki/Category:CSS_At_Rules Category:CSS_At_Rules]
** '''topic page:'''
** '''example pages:''' [[css/atrules/@page]], [[css/atrules/@import]]

* '''CSS_Media_Feature''', using ''topic="css"'', in [http://docs.webplatform.org/wiki/Template:CSS_Media_Feature Template], [http://docs.webplatform.org/wiki/Form:CSS_Media_Feature Form]
** '''category:''' [http://docs.webplatform.org/wiki/Category:CSS_Media_Feature Category CSS_Media_Feature]
** '''topic page:'''
** '''example pages:''' [[css/media_queries/device-width]], [[css/media_queries/color]], [[css/media_queries/height]]

* '''API_Object_Method''', using ''topic="webapi"'', in [http://docs.webplatform.org/wiki/Form:API_Object_Method Form], [http://docs.webplatform.org/wiki/Template:API_Object_Method Template]
** '''category:'''  [http://docs.webplatform.org/wiki/Category:API_Object_Methods Category:API_Object_Methods]
** '''topic page:'''
** '''example pages:''' [[apis/css-regions/Region/getComputedRegionStyle]], [[dom/Document/createTreeWalker]], [[apis/web-messaging/MessagePort/close]], [[apis/file/FileReader/abort]]

* '''API_Object''', using ''topic="webapi"'', in [http://docs.webplatform.org/wiki/Form:API_Object Form], [http://docs.webplatform.org/wiki/Template:API_Object Template]
** '''category:''' [http://docs.webplatform.org/wiki/Category:API_Objects Category:API_Objects]
** '''topic page:'''
** '''example pages:''' [[apis/css-regions/Region]], [[dom/EventTarget]], [[dom/Error]]

* '''API_Object_Property''', using ''topic="webapi"'', in [http://docs.webplatform.org/wiki/Form:API_Object_Property Form], [http://docs.webplatform.org/wiki/Template:API_Object_Property Template]
** '''category:''' [http://docs.webplatform.org/wiki/Category:API_Object_Properties Category:API_Object_Properties]
** '''topic page:'''
** '''example pages:''' [[apis/css-regions/Region/regionOverset]], [[apis/webaudio/AudioBufferSourceNode/buffer]]

* '''JS_Basic''', using ''topic="javascript"'', in [http://docs.webplatform.org/wiki/Template:JS_Object_Listing JS_Object_Listing template] and JavaScript global [http://docs.webplatform.org/wiki/Form:JS_Basic JS_Basic form template]
** '''category:''' [http://docs.webplatform.org/wiki/Category:JS_Method Category:JS_Method], [http://docs.webplatform.org/wiki/Category:JS_Object Category:JS_Object], [http://docs.webplatform.org/wiki/Category:JS_Function Category:JS_Function], [http://docs.webplatform.org/wiki/Category:JS_Property Category:JS_Property]
** '''topic page:''' [[javascript]]
** '''example pages:''' [[javascript/Date/getSeconds]], [[javascript/Array]], [[javascript/Uint16Array/set]], [[javascript/unescape]]
 
=== Templates that has been emptied ===
For depreciation.

The [http://docs.webplatform.org/wiki/Template:Compatibility_Section Compatibility_Section template] has been purposefully muted so we can add the compat data only where we want.

See list of pages [http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompatibility+Section&namespace=0 using Template:Compatibility_Section in an hardcoded fashion].

The [http://docs.webplatform.org/wiki/Template:Compatibility_Form_Section Template:Compatibility_Form_Section] should be removed from all templates as they are being replaced with the new [http://docs.webplatform.org/wiki/Template:Compatibility Compatibility template] 



== TODO ==

=== Reminders ===
* '''CSS_Media_Feature''', in [http://docs.webplatform.org/wiki/Template:CSS_Media_Feature Template], [http://docs.webplatform.org/wiki/Form:CSS_Media_Feature Form], has feature hardcoded at "media-queries"

=== Stack in progress ===

== Former Compatibility table template ==
Should we mute them from the template, or their call?
* [http://docs.webplatform.org/wiki/Template:Compatibility_Section Template:Compatibility_Section]  '''MUTED'''
* [http://docs.webplatform.org/wiki/Template:Compatibility_Form_Section Template:Compatibility_Form_Section] ''REMOVED from Form Templates''
* [http://docs.webplatform.org/wiki/Template:Compatibility_Table Template:Compatibility_Table]
* [http://docs.webplatform.org/wiki/Template:Compat_Unknown Template:Compat_Unknown]

== Where they *might not* make sense to have a Compatibility table ==
* In [[guides/advanced_selectors_guide]], via [http://docs.webplatform.org/wiki/Form:Guide Form:Guide], category [http://docs.webplatform.org/wiki/Category:Guides Category:Guides]
* In [[tutorials/inheritance_and_cascade]], via [http://docs.webplatform.org/wiki/Form:Tutorial Form:Tutorial], category [http://docs.webplatform.org/wiki/Category:Tutorials Category:Tutorials]

== Questions ==

=== Things to improve ===

* '''CSS_Selector''':  [http://docs.webplatform.org/wiki/Form:CSS_Selector Form], [http://docs.webplatform.org/wiki/Template:CSS_Selector Template], need improvements in template+form
* '''CSS_Function''':  [http://docs.webplatform.org/wiki/Form:CSS_Function Form], [http://docs.webplatform.org/wiki/Template:CSS_Function Template], need improvements in template+form
* '''CSS_Media_Feature''':  [http://docs.webplatform.org/wiki/Form:CSS_Media_Feature Form], [http://docs.webplatform.org/wiki/Template:CSS_Media_Feature Template], need improvements in template+form
* '''CSS_At_Rule''':  [http://docs.webplatform.org/wiki/Form:CSS_At_Rule Form], [http://docs.webplatform.org/wiki/Template:CSS_At_Rule Template], need improvements in template+form
* In [[html/apis]], the APIs subsection is hardcoded and doesn’t list what we have. Should we just move that to JavaScript?


=== Basic pages, do we really want a compat there? ===

[http://docs.webplatform.org/wiki/Form:Basic Form:Basic]

== Special cases ==
=== Multiple forms ===
Pages that has more than one form
* [[css/media_queries/device-height]], listed from [[css/mediaqueries]]