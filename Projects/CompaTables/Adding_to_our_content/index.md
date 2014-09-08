= Adding to our Docs pages =

== Summary ==

Which MediaWiki templates are involved to display the compatibility tables data.

== Where it has been done ==
Instructions on how to set in place, refer to [http://docs.webplatform.org/wiki/Template:Compatibility#How_to_use the Compatibility Template] at '''How to use'''. Remove the <nowiki>{{Compatibility_Form_Section}}</nowiki> in the Form view, if you see any.

* '''CSS_Property''', in [http://docs.webplatform.org/wiki/Template:CSS_Property Template], [http://docs.webplatform.org/wiki/Form:CSS_Property Form]
* '''CSS_Selector''', in [http://docs.webplatform.org/wiki/Template:CSS_Selector Template], [http://docs.webplatform.org/wiki/Form:CSS_Selector Form] ''IMPORTANT:'' Refactor the Form and View Templates!
* '''CSS_Function''', in [http://docs.webplatform.org/wiki/Template:CSS_Function Template], [http://docs.webplatform.org/wiki/Form:CSS_Function Form]
* '''CSS_At_Rule''', in [http://docs.webplatform.org/wiki/Template:CSS_At_Rule Template], [http://docs.webplatform.org/wiki/Form:CSS_At_Rule Form]

== Related Templates ==
Other templates that was used to show compatibility tables. So far, only '''Compatibility_Section''' Template has been muted.

== Muted ==
The [http://docs.webplatform.org/wiki/Template:Compatibility_Section Compatibility_Section template] has been purposefully muted so we can add the compat data only where we want.

See list of pages [http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompatibility+Section&namespace=0 using Template:Compatibility_Section in an hardcoded fashion].

== Where we *WANT* them ==
* [http://docs.webplatform.org/wiki/Category:CSS_At_Rules Category:CSS_At_Rules ]; [[css/atrules/@page]], [[css/atrules/@import]]
* [http://docs.webplatform.org/wiki/Category:CSS_Properties Category:CSS_Properties]; [[css/properties/align-content]], in [[css/properties]]
* [http://docs.webplatform.org/wiki/Category:CSS_Selectors Category:CSS_Selectors]; [[css/selectors/attributes/hyphen]], [[css/selectors/combinators/general_sibling]], [[css/selectors/attributes/existence]]
* [http://docs.webplatform.org/wiki/Category:CSS_Functions Category:CSS_Functions]; [[css/functions/brightness]], [[css/functions]]

== In progress ==
* [http://docs.webplatform.org/wiki/Form:API_Object_Method API_Object_Method], [[apis/css-regions/Region/getComputedRegionStyle]], category [http://docs.webplatform.org/wiki/Category:API_Object_Methods Category:API_Object_Methods]
* [http://docs.webplatform.org/wiki/Form:API_Object Form:API_Object], [[apis/css-regions/Region]], category [http://docs.webplatform.org/wiki/Category:API_Objects Category:API_Objects]
* [http://docs.webplatform.org/wiki/Form:CSS_Media_Feature Form:CSS_Media_Feature], [[css/media_queries/height]], [[css/media_queries/orientation]] , category [http://docs.webplatform.org/wiki/Category:CSS_Media_Feature Category:CSS_Media_Feature]

=== Not muted, yet ===
Should we mute them from the template, or their call?
* [[Template:Compatibility_Form_Section]]  
* [[Template:Compatibility_Section]]
* [[Template:Compatibility_Table]]
* [[Template:Compatibility_Section]]
* [[Template:Compat_Unknown]]

=== Where they *might not* make sense to be ===
* In [[guides/advanced_selectors_guide]], via [http://docs.webplatform.org/wiki/Form:Guide Form:Guide], category [http://docs.webplatform.org/wiki/Category:Guides Category:Guides]
* In [[tutorials/inheritance_and_cascade]], via [http://docs.webplatform.org/wiki/Form:Tutorial Form:Tutorial], category [http://docs.webplatform.org/wiki/Category:Tutorials Category:Tutorials]

=== Basic pages, do we really want a compat there? ===

[http://docs.webplatform.org/wiki/Form:Basic Form:Basic]

== Special cases ==
=== Multiple forms ===
Pages that has more than one form
* [[css/media_queries/device-height]], listed from [[css/mediaqueries]]