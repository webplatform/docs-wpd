= Adding to our Docs pages =

== Summary ==

Which MediaWiki templates are involved to display the compatibility tables data.

== What has been done ==

For instructions on how to set in place, refer to [http://docs.webplatform.org/wiki/Template:Compatibility#How_to_use the Compatibility Template] at '''How to use'''. 

* Remove the <nowiki>{{Compatibility_Form_Section}}</nowiki> in the Form view, if you see any.

=== Templates changed ===

* '''CSS_Property''', in [http://docs.webplatform.org/wiki/Template:CSS_Property Template], [http://docs.webplatform.org/wiki/Form:CSS_Property Form]
* '''CSS_Selector''', in [http://docs.webplatform.org/wiki/Template:CSS_Selector Template], [http://docs.webplatform.org/wiki/Form:CSS_Selector Form]
* '''CSS_Function''', in [http://docs.webplatform.org/wiki/Template:CSS_Function Template], [http://docs.webplatform.org/wiki/Form:CSS_Function Form]
* '''CSS_At_Rule''', in [http://docs.webplatform.org/wiki/Template:CSS_At_Rule Template], [http://docs.webplatform.org/wiki/Form:CSS_At_Rule Form]
* '''CSS_Media_Feature''', in [http://docs.webplatform.org/wiki/Template:CSS_Media_Feature Template], [http://docs.webplatform.org/wiki/Form:CSS_Media_Feature Form]
 
=== Templates that has been emptied ===
For possible depreciation.

The [http://docs.webplatform.org/wiki/Template:Compatibility_Section Compatibility_Section template] has been purposefully muted so we can add the compat data only where we want.

See list of pages [http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompatibility+Section&namespace=0 using Template:Compatibility_Section in an hardcoded fashion].

==== Maybe? ====
* [http://docs.webplatform.org/wiki/Template:Compatibility_Form_Section Template:Compatibility_Form_Section] 


== Typical pages per section ==
* [http://docs.webplatform.org/wiki/Category:CSS_At_Rules Category:CSS_At_Rules ]; [[css/atrules/@page]], [[css/atrules/@import]]
* [http://docs.webplatform.org/wiki/Category:CSS_Properties Category:CSS_Properties]; [[css/properties/align-content]], in [[css/properties]]
* [http://docs.webplatform.org/wiki/Category:CSS_Selectors Category:CSS_Selectors]; [[css/selectors/attributes/hyphen]], [[css/selectors/combinators/general_sibling]], [[css/selectors/attributes/existence]]
* [http://docs.webplatform.org/wiki/Category:CSS_Functions Category:CSS_Functions]; [[css/functions/brightness]], [[css/functions]]
* [http://docs.webplatform.org/wiki/Category:CSS_Media_Feature Category CSS_Media_Feature]; [[css/media_queries/device-width]], [[css/media_queries/color]], [[css/media_queries/height]]

== TODO ==

=== Reminders ===
* '''CSS_Media_Feature''', in [http://docs.webplatform.org/wiki/Template:CSS_Media_Feature Template], [http://docs.webplatform.org/wiki/Form:CSS_Media_Feature Form], has feature is hardcoded at "media-queries"

=== Stack in progress ===
* [http://docs.webplatform.org/wiki/Form:API_Object_Method API_Object_Method], [[apis/css-regions/Region/getComputedRegionStyle]], category [http://docs.webplatform.org/wiki/Category:API_Object_Methods Category:API_Object_Methods]
* [http://docs.webplatform.org/wiki/Form:API_Object Form:API_Object], [[apis/css-regions/Region]], category [http://docs.webplatform.org/wiki/Category:API_Objects Category:API_Objects]
* [http://docs.webplatform.org/wiki/Form:CSS_Media_Feature Form:CSS_Media_Feature], [[css/media_queries/height]], [[css/media_queries/orientation]] , category [http://docs.webplatform.org/wiki/Category:CSS_Media_Feature Category:CSS_Media_Feature]


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

* [http://docs.webplatform.org/wiki/Form:CSS_At_Rule Form:CSS_At_Rule],
* [http://docs.webplatform.org/wiki/Form:CSS_Function Form:CSS_Function],
* [http://docs.webplatform.org/wiki/Form:CSS_Selector Form:CSS_Selector]

=== Templates to refactor ===

* [http://docs.webplatform.org/wiki/Form:CSS_At_Rule Form:CSS_At_Rule],
* [http://docs.webplatform.org/wiki/Form:CSS_Function Form:CSS_Function],
* [http://docs.webplatform.org/wiki/Form:CSS_Selector Form:CSS_Selector]

=== Basic pages, do we really want a compat there? ===

[http://docs.webplatform.org/wiki/Form:Basic Form:Basic]

== Special cases ==
=== Multiple forms ===
Pages that has more than one form
* [[css/media_queries/device-height]], listed from [[css/mediaqueries]]