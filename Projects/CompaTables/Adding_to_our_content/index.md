= Adding to our Docs pages =

== Change summary note ==

  <nowiki>Installing Compatibility tables, see [[WPD:Projects/CompaTables/Adding_to_our_content]]</nowiki>

== Summary ==

Which MediaWiki templates are involved to display the compatibility tables data.

== What has been done ==

For instructions on how to set in place, refer to [http://docs.webplatform.org/wiki/Template:Compatibility#How_to_use Template:Compatibility] at '''How to use'''.

* Remove the <nowiki>{{Compatibility_Form_Section}}</nowiki> in the Form view, if you see any.

=== Templates changed ===
a
 
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
* '''API_Object_Property''', [http://docs.webplatform.org/wiki/Form:API_Object_Property Form], [http://docs.webplatform.org/wiki/Template:API_Object_Property Template], [[Category:API_Object_Properties]]; [[apis/css-regions/Region/regionOverset]]

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