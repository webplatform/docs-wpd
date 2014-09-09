= Adding to our Docs pages =

== Change summary note ==

  <nowiki>Installing Compatibility tables, see [[WPD:Projects/CompaTables/Adding_to_our_content]]</nowiki>

== Summary ==

Which MediaWiki templates are involved to display the compatibility tables data.

== What has been done ==

For instructions on how to set in place, refer to [http://docs.webplatform.org/wiki/Template:Compatibility#How_to_use Template:Compatibility] at '''How to use'''.

* Remove the <nowiki>{{Compatibility_Form_Section}}</nowiki> in the Form view, if you see any.

=== Templates changed ===

* '''CSS_Property''', using <code><nowiki>{Compatibility|feature="css"}</nowiki></code>, in [http://docs.webplatform.org/wiki/Template:CSS_Property Template], [http://docs.webplatform.org/wiki/Form:CSS_Property  Form]
** '''category:''' [http://docs.webplatform.org/wiki/Category:CSS_Properties Category:CSS_Properties]
** '''topic page:''' [[css/properties]]
** '''example pages:''' [[css/properties/align-content]]
* '''CSS_Selector''', using <code><nowiki>{{Compatibility|topic="css"}}</nowiki></code>, in [http://docs.webplatform.org/wiki/Template:CSS_Selector Template], [http://docs.webplatform.org/wiki/Form:CSS_Selector Form]
** '''category:'''
** '''topic page:'''
** '''example pages:'''
** [http://docs.webplatform.org/wiki/Category:CSS_Selectors Category:CSS_Selectors]; [[css/selectors/attributes/hyphen]], [[css/selectors/combinators/general_sibling]], [[css/selectors/attributes/existence]]
* '''CSS_Function'', using <code><nowiki>{Compatibility|topic="css"}}</nowiki></code>, in [http://docs.webplatform.org/wiki/Template:CSS_Function Template], [http://docs.webplatform.org/wiki/Form:CSS_Function Form]
** '''category:'''
** '''topic page:'''
** '''example pages:'''
** [http://docs.webplatform.org/wiki/Category:CSS_Functions Category:CSS_Functions]; [[css/functions/brightness]], [[css/functions]]
* '''CSS_At_Rule''', using <code><nowiki>{{Compatibility|topic="css"}}</nowiki></code>, in [http://docs.webplatform.org/wiki/Template:CSS_At_Rule Template], [http://docs.webplatform.org/wiki/Form:CSS_At_Rule Form]
** '''category:'''
** '''topic page:'''
** '''example pages:'''
** [http://docs.webplatform.org/wiki/Category:CSS_At_Rules Category:CSS_At_Rules]; [[css/atrules/@page]], [[css/atrules/@import]]
* '''CSS_Media_Feature''', using <code><nowiki>{{Compatibility|feature="css"}}</nowiki></code>, in [http://docs.webplatform.org/wiki/Template:CSS_Media_Feature Template], [http://docs.webplatform.org/wiki/Form:CSS_Media_Feature Form]
** '''category:'''
** '''topic page:'''
** '''example pages:'''
** [http://docs.webplatform.org/wiki/Category:CSS_Media_Feature Category CSS_Media_Feature]; [[css/media_queries/device-width]], [[css/media_queries/color]], [[css/media_queries/height]]
* '''API_Object_Method'', using <code><nowiki>{{Compatibility|topic="webapi"}}</nowiki></code>, in [http://docs.webplatform.org/wiki/Form:API_Object_Method Form], [http://docs.webplatform.org/wiki/Template:API_Object_Method Template]
** '''category:'''
** '''topic page:'''
** '''example pages:'''
**  [http://docs.webplatform.org/wiki/Category:API_Object_Methods Category:API_Object_Methods]; [[apis/css-regions/Region/getComputedRegionStyle]], [[dom/Document/createTreeWalker]], [[apis/web-messaging/MessagePort/close]], [[apis/file/FileReader/abort]]
* '''API_Object''', using <code><nowiki>{{Compatibility|topic="webapi"}}</nowiki></code>, in [http://docs.webplatform.org/wiki/Form:API_Object Form], [http://docs.webplatform.org/wiki/Template:API_Object Template]
** '''category:'''
** '''topic page:'''
** '''example pages:'''
** [http://docs.webplatform.org/wiki/Category:API_Objects Category:API_Objects]; [[apis/css-regions/Region]], [[dom/EventTarget]], [[dom/Error]]
* '''API_Object_Property''', using <code><nowiki>{{Compatibility|topic="webapi"}}</nowiki></code>, in [http://docs.webplatform.org/wiki/Form:API_Object_Property Form], [http://docs.webplatform.org/wiki/Template:API_Object_Property Template]
** '''category:'''
** '''topic page:'''
** '''example pages:'''
** [http://docs.webplatform.org/wiki/Category:API_Object_Properties Category:API_Object_Properties]; [[apis/css-regions/Region/regionOverset]], [[http://docs.webplatform.org/wiki/apis/webaudio/AudioBufferSourceNode/buffer]]

 
=== Templates that has been emptied ===
For possible depreciation.

The [http://docs.webplatform.org/wiki/Template:Compatibility_Section Compatibility_Section template] has been purposefully muted so we can add the compat data only where we want.

See list of pages [http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompatibility+Section&namespace=0 using Template:Compatibility_Section in an hardcoded fashion].

==== Maybe? ====
* [http://docs.webplatform.org/wiki/Template:Compatibility_Form_Section Template:Compatibility_Form_Section] 


== TODO ==

=== Reminders ===
* '''CSS_Media_Feature''', in [http://docs.webplatform.org/wiki/Template:CSS_Media_Feature Template], [http://docs.webplatform.org/wiki/Form:CSS_Media_Feature Form], has feature hardcoded at "media-queries"

=== Stack in progress ===

== Former Compatibility table template ==
Should we mute them from the template, or their call?
* [[Template:Compatibility_Section]]  '''MUTED'''
* [[Template:Compatibility_Form_Section]]
* [[Template:Compatibility_Table]]
* [[Template:Compat_Unknown]]

== Where they *might not* make sense to have a Compatibility table ==
* In [[guides/advanced_selectors_guide]], via [http://docs.webplatform.org/wiki/Form:Guide Form:Guide], category [http://docs.webplatform.org/wiki/Category:Guides Category:Guides]
* In [[tutorials/inheritance_and_cascade]], via [http://docs.webplatform.org/wiki/Form:Tutorial Form:Tutorial], category [http://docs.webplatform.org/wiki/Category:Tutorials Category:Tutorials]

== Questions ==
=== Do we really want to remove Template:Compatibility_Form_Section? ===

The template [http://docs.webplatform.org/wiki/Template:Compatibility_Form_Section Template:Compatibility_Form_Section] has been removed from 

* '''CSS_Selector''':  [http://docs.webplatform.org/wiki/Form:CSS_Selector Form], [http://docs.webplatform.org/wiki/Template:CSS_Selector Template] +Refactor
* '''CSS_Function''':  [http://docs.webplatform.org/wiki/Form:CSS_Function Form], [http://docs.webplatform.org/wiki/Template:CSS_Function Template] +Refactor
* '''CSS_Media_Feature''':  [http://docs.webplatform.org/wiki/Form:CSS_Media_Feature Form], [http://docs.webplatform.org/wiki/Template:CSS_Media_Feature Template] +Refactor
* '''CSS_At_Rule''':  [http://docs.webplatform.org/wiki/Form:CSS_At_Rule Form], [http://docs.webplatform.org/wiki/Template:CSS_At_Rule Template]  +Refactor

=== Basic pages, do we really want a compat there? ===

[http://docs.webplatform.org/wiki/Form:Basic Form:Basic]

== Special cases ==
=== Multiple forms ===
Pages that has more than one form
* [[css/media_queries/device-height]], listed from [[css/mediaqueries]]