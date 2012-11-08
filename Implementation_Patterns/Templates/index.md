This page is a specific overview of our primary work-horse templates, and complements the more high-level [[WPD:Implementation_Patterns]] guide. It assumes you have read and understood that guide.

==General Organization==
Almost every reference page uses one of ~20 major templates/forms. You can view a comprehensive list at [[WPD:New_Page]].

There are many common elements on these reference pages that occur either on all of the major page type templates or occur on more than one. An example is the [[Template:Summary_Section|summary section template]]. For each of these sections, we create a separate template to do the work. We also create a template of the ''form'' for that template. Then, in the form for the main page type, we include the sub-form template. This automatically configures the form to deposit the sub-template on the page when it is saved.

The summary section is a good example. We have the [[Template:Summary_Section|main template]] that handles the work of taking in parameters and rendering them out in a standard way, as well as setting certain semantic media wiki properties in the right way. If you "Edit Source" on almost any reference page, you'll see that there's an instantiation of this template on the page. We also have the [[Template:Summary_Form_Section|form template]] which configures how that part of the form will show up and what fields it will have. If you look at the source of any of the major page-type forms, like [[Form:CSS_Property|the css property form]], you'll see that there is a call to this Summary_Form_Section template.

Most page-type forms use sub-forms and sub-templates as much as possible, and use the "central" template--the one most specific to this page-type--only for properties and form fields that are specific to this page type and this page type only. That "central" template is often the one that deposits the appropriate category on the page to wire it up to the form. The most simple of these page-type forms is the [[Form:Basic|one for basic pages]]. There aren't any special parameters to set, so basically that central template ''just'' sets the Basic Pages category so that in the future when the user hits the Edit button the right form will show.

==Specific Sub-Forms==

There are many sub-forms and sub-templates that we use very often. These are generally easy to discover by viewing the source of the page-type form you're interested in.

{{TODO | Fill in a list of the main sub-form templates }}

==Page-Type Organization==
Again, the common elements of pages (like summaries) are handled in sub-forms and sub-templates that are used the same on every page. Most page-types have a specific "central" template that handles the interesting bits that are specific to this page type. For example, the [[Form:CSS_Property|css property form]] defines fields for whether or not the field is inheritable and what its legal values are.

The following sections give a more in-depth overview of how these main page-types are inter-related. Documentation that is mainly about one specific page-type (and not how they inter-relate) should be found on the given Template itself.

===API Objects, Methods, and Properties ===

Some of the most common page-types are [[Template:API_Object]], [[Template:API_Object_Method]], and [[Template:API_Object_Property]]. They are also some of the most confusing when you first look at them.

The API Object template is the one that should be used for the object that contains methods and properties. It will ultimately have an exhaustive list of all of its associated properties, methods, events, constants, etc. However, if you edit a page that uses this template you will see that there isn't much content on the page at all!

The way the API_Object template works is that all of the applicable API_Object_Method and API_Object_Property pages set an Applies_to field that specifies the page they "apply to": the API_Object. Then, when we generate the text for that page, we use a semantic media wiki query to select all pages that apply to it and print out their information.