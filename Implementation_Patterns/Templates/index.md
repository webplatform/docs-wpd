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

===Summaries, Page_Title, and API_Name===
As far as MediaWiki is concerned, the "title" of a page is the entirety of the URL after the "http://docs.webplatform.org/wiki/" part. This leads to many pages having long names like "css/properties/font-size" when "font-size" is far more appropriate. Also, when we include a link to a page on another page, we often want to provide a bit of context on what the page is about.

We get around this by setting Semantic Media Wiki properties for the Page_Title, API_Name, and Summary.

The Summary is simply a property of type Text that is set to contain the Summary field in the form. By setting a property, other pages (like [[Template:API_Listing]]) can automatically pull out that information and display it in a table.

The [[Template:Page_Title|page title]] template is how you set the page title. If the editor provided a value, it uses that value. However, it defaults to using the last part of the page-title. So, for example, on "css/properties/font-size", it would default to "font-size".

The [[Template:API_Name|API name]] template overlaps in use with the page title template quite a bit, but historically it predates it. Whereas page title is what the page should be called when presented as a link, the API_Name is the precise text used to invoke that API. The API_Name is used when generating automatic examples and theoretically for more stuff in the future. For methods and properties, it would be the method/property name. For things like CSS selectors, however, it would be things like "#" or ".". Pages with weird API_Names are the cases where the page title might be different than the API_Name, for example the page might have a title of "Class Selector", but the API_Name might have a value of ".".

===API Listing===

The [[Template:API_Listing|API Listing]] template is somewhat confusingly named. Unlike the API_Object template which is the canonical reference for the methods, properties, and events that apply to a given interface object, the API Listing template is more about just listing all sub-pages that match some criteria.

The API_Listing page template is used for many pages that are primarily about organization and not about content. For example, the [[css/properties]] page uses this template to list all css properties.

The listing is powered in one of two ways: the better way and the worse way.

The better way uses Semantic Media Wiki query syntax to select which pages to show. You can see what syntax is allowed at [http://semantic-mediawiki.org/wiki/Help:Selecting_pages this page]. Basically you write a query that selects pages based on categories they're in or the values of semantic media wiki properties on them.

{{TODO | Continue filling in this section, including using the SMW property for page name. }}

===Attributes, properties, and DOM===

{{TODO | Fill this part in}}

===Topics, Topic Clusters, See Also===

{{TODO | Fill this in}}