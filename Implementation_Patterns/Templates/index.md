---
title: WPD:Implementation Patterns/Templates
---
<p><b>This page is a specific overview of our primary work-horse templates, and complements the more high-level <a href="/wiki/WPD:Implementation_Patterns" title="WPD:Implementation Patterns">WPD:Implementation_Patterns</a> guide. It assumes you have read and understood that guide.</b>
</p>
<h2><span class="mw-headline" id="General_Organization">General Organization</span></h2>
<p>Almost every reference page uses one of ~20 major templates/forms. You can view a comprehensive list at <a href="/wiki/WPD:New_Page" title="WPD:New Page">WPD:New_Page</a>.
</p><p>There are many common elements on these reference pages that occur either on all of the major page type templates or occur on more than one. An example is the <a href="/wiki/Template:Summary_Section" title="Template:Summary Section">summary section template</a>. For each of these sections, we create a separate template to do the work. We also create a template of the <i>form</i> for that template. Then, in the form for the main page type, we include the sub-form template. This automatically configures the form to deposit the sub-template on the page when it is saved.
</p><p>The summary section is a good example. We have the <a href="/wiki/Template:Summary_Section" title="Template:Summary Section">main template</a> that handles the work of taking in parameters and rendering them out in a standard way, as well as setting certain semantic media wiki properties in the right way. If you "Edit Source" on almost any reference page, you'll see that there's an instantiation of this template on the page. We also have the <a href="/wiki/Template:Summary_Form_Section" title="Template:Summary Form Section">form template</a> which configures how that part of the form will show up and what fields it will have. If you look at the source of any of the major page-type forms, like <a href="/wiki/Form:CSS_Property" title="Form:CSS Property">the css property form</a>, you'll see that there is a call to this Summary_Form_Section template.
</p><p>Most page-type forms use sub-forms and sub-templates as much as possible, and use the "central" template--the one most specific to this page-type--only for properties and form fields that are specific to this page type and this page type only. That "central" template is often the one that deposits the appropriate category on the page to wire it up to the form. The most simple of these page-type forms is the <a href="/wiki/Form:Basic" title="Form:Basic">one for basic pages</a>. There aren't any special parameters to set, so basically that central template <i>just</i> sets the Basic Pages category so that in the future when the user hits the Edit button the right form will show.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Represent the information in this page as a diagram 
</p>
</div>
<h2><span class="mw-headline" id="Template.2FForm_Naming_Conventions">Template/Form Naming Conventions</span></h2>
<p>In the vast majority of cases, we use consistent naming conventions so it's easy to figure out what the related Form/Template is called without having to investigate it.
</p><p>For page types:
</p>
<ul><li> <b>Core template</b>: <a href="/wiki/Template:Foo" title="Template:Foo">Template:Foo</a> </li>
<li> <b>Core category</b>: [[Category:Foos]], where "Foos" is the english plurilization of the core template name.</li>
<li> <b>Core form</b>: <a href="/w/index.php?title=Form:Foo&amp;action=edit&amp;redlink=1" class="new" title="Form:Foo (page does not exist)">Form:Foo</a></li></ul>
<p><br />
</p>
<div class="note">
<p><b>Note</b>:  Basic page's form is an exception to these rules. The main form is at <a href="/wiki/Template:Basic_Page" title="Template:Basic Page">Template:Basic_Page</a> but the form is at <a href="/wiki/Form:Basic" title="Form:Basic">Form:Basic</a> 
</p>
</div>
<p><br />
For sub-templates and sub-forms:
</p>
<ul><li> <b>Template</b>: <a href="/w/index.php?title=Template:Foo_Section&amp;action=edit&amp;redlink=1" class="new" title="Template:Foo Section (page does not exist)">Template:Foo_Section</a></li>
<li> <b>Sub-Form</b>: <a href="/w/index.php?title=Template:Foo_Form_Section&amp;action=edit&amp;redlink=1" class="new" title="Template:Foo Form Section (page does not exist)">Template:Foo_Form_Section</a> <b>Note</b>: the sub-form is implemented as a <i>template</i>, not a <i>form</i>.</li></ul>
<h2><span class="mw-headline" id="Specific_Sub-Forms">Specific Sub-Forms</span></h2>
<p>There are many sub-forms and sub-templates that we use very often. These are generally easy to discover by viewing the source of the page-type form you're interested in.
</p>
<ul><li> <a href="/wiki/Template:Page_Title" title="Template:Page Title">Template:Page_Title</a></li>
<li> <a href="/wiki/Template:Flags" title="Template:Flags">Template:Flags</a></li>
<li> <a href="/wiki/Template:Standardization_Status" title="Template:Standardization Status">Template:Standardization_Status</a></li>
<li> <a href="/wiki/Template:API_Name" title="Template:API Name">Template:API_Name</a></li>
<li> <a href="/wiki/Template:Summary_Section" title="Template:Summary Section">Template:Summary_Section</a></li>
<li> <a href="/wiki/Template:Examples_Section" title="Template:Examples Section">Template:Examples_Section</a></li>
<li> <a href="/wiki/Template:Notes_Section" title="Template:Notes Section">Template:Notes_Section</a></li>
<li> <a href="/wiki/Template:Related_Specifications_Section" title="Template:Related Specifications Section">Template:Related_Specifications_Section</a></li>
<li> <a href="/wiki/Template:Compatibility_Section" title="Template:Compatibility Section">Template:Compatibility_Section</a></li>
<li> <a href="/wiki/Template:See_Also_Section" title="Template:See Also Section">Template:See_Also_Section</a></li>
<li> <a href="/wiki/Template:Topics" title="Template:Topics">Template:Topics</a></li>
<li> <a href="/wiki/Template:External_Attribution" title="Template:External Attribution">Template:External_Attribution</a></li>
<li> <i>This list is not comprehensive yet. Please add more sub-forms to it!</i></li></ul>
<h2><span class="mw-headline" id="Page-Type_Organization">Page-Type Organization</span></h2>
<p>Again, the common elements of pages (like summaries) are handled in sub-forms and sub-templates that are used the same on every page. Most page-types have a specific "central" template that handles the interesting bits that are specific to this page type. For example, the <a href="/wiki/Form:CSS_Property" title="Form:CSS Property">css property form</a> defines fields for whether or not the field is inheritable and what its legal values are.
</p><p>The following sections give a more in-depth overview of how these main page-types are inter-related. Documentation that is mainly about one specific page-type (and not how they inter-relate) should be found on the given Template itself.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  A lot of the documentation in the following sections actually should live in the specific documentation sections on each Template's page.
</p>
</div>
<h3><span class="mw-headline" id="API_Objects.2C_Methods.2C_and_Properties">API Objects, Methods, and Properties</span></h3>
<p>Some of the most common page-types are <a href="/wiki/Template:API_Object" title="Template:API Object">Template:API_Object</a>, <a href="/wiki/Template:API_Object_Method" title="Template:API Object Method">Template:API_Object_Method</a>, and <a href="/wiki/Template:API_Object_Property" title="Template:API Object Property">Template:API_Object_Property</a>. They are also some of the most confusing when you first look at them.
</p><p>The API Object template is the one that should be used for the object that contains methods and properties. It will ultimately have an exhaustive list of all of its associated properties, methods, events, constants, etc. However, if you edit a page that uses this template you will see that there isn't much content on the page at all!
</p><p>The way the API_Object template works is that all of the applicable API_Object_Method and API_Object_Property pages set an Applies_to field that specifies the page they "apply to": the API_Object. Then, when we generate the text for that page, we use a semantic media wiki query to select all pages that apply to it and print out their information.
</p><p>Importantly, it's also possible to define the <b>Subclass_of</b> property of API_Objects. This is the way we formally represent which objects this inherits properties and methods of--something that's critically important for many DOM APIs (for example, the chain for AudioElement looks like: AudioElement --&gt; MediaElement --&gt; HTMLElement --&gt; Element --&gt; Node). We automatically print out the properties and methods of the immediate parent.  For performance reasons we don't print out any methods or properties that come from higher up in the chain, but if you want to, you can manually specify more ancestors in the Subclass_of field by separating them with commas (most recent ancestor first).
</p>
<h3><span class="mw-headline" id="Summaries.2C_Page_Title.2C_and_API_Name">Summaries, Page_Title, and API_Name</span></h3>
<p>As far as MediaWiki is concerned, the "title" of a page is the entirety of the URL after the "<a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/">http://docs.webplatform.org/wiki/</a>" part. This leads to many pages having long names like "css/properties/font-size" when "font-size" is far more appropriate. Also, when we include a link to a page on another page, we often want to provide a bit of context on what the page is about.
</p><p>We get around this by setting Semantic Media Wiki properties for the Page_Title, API_Name, and Summary.
</p><p>The Summary is simply a property of type Text that is set to contain the Summary field in the form. By setting a property, other pages (like <a href="/wiki/Template:API_Listing" title="Template:API Listing">Template:API_Listing</a>) can automatically pull out that information and display it in a table.
</p><p>The <a href="/wiki/Template:Page_Title" title="Template:Page Title">page title</a> template is how you set the page title. If the editor provided a value, it uses that value. However, it defaults to using the last part of the page-title. So, for example, on "css/properties/font-size", it would default to "font-size".
</p><p>The <a href="/wiki/Template:API_Name" title="Template:API Name">API name</a> template overlaps in use with the page title template quite a bit, but historically it predates it. Whereas page title is what the page should be called when presented as a link, the API_Name is the precise text used to invoke that API. The API_Name is used when generating automatic examples and theoretically for more stuff in the future. For methods and properties, it would be the method/property name. For things like CSS selectors, however, it would be things like "#" or ".". Pages with weird API_Names are the cases where the page title might be different than the API_Name, for example the page might have a title of "Class Selector", but the API_Name might have a value of ".".
</p>
<h3><span class="mw-headline" id="API_Listing">API Listing</span></h3>
<p>The <a href="/wiki/Template:API_Listing" title="Template:API Listing">API Listing</a> template is somewhat confusingly named. Unlike the API_Object template which is the canonical reference for the methods, properties, and events that apply to a given interface object, the API Listing template is more about just listing all sub-pages that match some criteria.
</p><p>The API_Listing page template is used for many pages that are primarily about organization and not about content. For example, the <a href="/wiki/css/properties" title="css/properties">css/properties</a> page uses this template to list all css properties.
</p><p>The listing is powered in one of two ways: the better way and the worse way.
</p>
<h4><span class="mw-headline" id="The_Worse_Way">The Worse Way</span></h4>
<p>First, the worse way.
</p><p>It is possible in MediaWiki to enumerate all sub-pages that are descendants of a given page. We implement this in the API Listing template with a parameter to "Print all sub-pages rooted here."
</p><p>There are two major limitations of this approach. First, it prints out <i>all descendants</i> when what you normally want is only the <i>direct children</i>. This creates listings that are far too full. Secondly, the listings use the full page name (things like "css/properties/font-size"), which is ugly, and doesn't include the page summary.
</p><p>The reason we have this is because of a mistake we made in the import. The prettier way of printing sub-pages relies on the "Page_Title", "Path", and "Summary" properties being set on pages. However, when we did the import, we goofed--we didn't include the templates that set those properties. Thus, most pages imported don't have those properties set until they've been manually edited at least once (we refer to a manual edit without substantive changes, whose only purpose is to make sure all relevant templates and properties are included, a "touch"). 
</p><p>We figured at the beginning that it was better to comprehensively list all descendants instead of doing the better listing format but missing some pages seemingly randomly--perhaps forgetting about them for all time.
</p><p>Over time, as more articles are touched, every API_Listing page should transition to using the Better Way and stop using this "Print all sub-pages rooted here" checkbox. Note that while we're transitioning, it's best practice to include the better way print out as well as the comprehensive sub-listing (they can coexist on the page). Once we've verified the better listing is comprehensive, we can uncheck the sub-listing option.
</p>
<h4><span class="mw-headline" id="The_Better_Way">The Better Way</span></h4>
<p>The better way uses Semantic Media Wiki query syntax to select which pages to show. You can see what syntax is allowed at <a rel="nofollow" class="external text" href="http://semantic-mediawiki.org/wiki/Help:Selecting_pages">this page</a>. Basically you write a query that selects pages based on categories they're in or the values of semantic media wiki properties on them.
</p><p>Note that it's actually kind of difficult to select pages that are only direct children of a page (as opposed to all descendants).  We get around this (somewhat) by having every page have a Path property, which is just set to the name of the page (e.g. "css/properties/font-size"). You can then use the like operator in the SMW query to do some matching.
</p><p><br />
</p>
<div class="note">
<p><b>Note</b>:  Pro tip: you can easily see what properties are currently applied to a page by going to Tools &gt; Browse Properties 
</p>
</div>
<p><br />
In practice, the queries you will create will be some combination of a given template type combined with it having a URL of a given form.
</p>
<h3><span class="mw-headline" id="Attributes.2C_properties.2C_and_DOM">Attributes, properties, and DOM</span></h3>
<div class="note">
<p><b>Note</b>:  This part gets hairy really fast, and our current information organization for it has known problems (see the notes from the community meeting on 10/30 for just a few examples of things we need to change). 
</p>
</div>
<p><br />
First of all, most DOM interfaces should use the <a href="/wiki/Template:API_Object" title="Template:API Object">API Object template</a>, since they primarily consist of methods/properties on an API interface.
</p><p>Markup_Elements should use the DOM_Interface property to point to the <i>most specific DOM interface that applies to them.</i> For example, the &lt;audio&gt; markup_element page would point to the AudioElement page. For many "simple" elements, the most specific DOM interface is simply HTMLElement.
</p><p>Markup_Attribute pages should point at the most-specific DOM interface to which they apply (yes, this is conceptually a bit weird). In the future for each markup_element, we will check to see what its DOM_Interface is, and then query for all attributes that are associated with that DOM_Interface and show those.
</p><p>Attributes are weird for another reason: generally every attribute on a markup element has a corresponding  property on associated DOM interface. However, this corresponding property might be slightly different (for example, switching from hyphens to camel casing); we need to update the Markup_Attribute template to have an often-automatically-generated Associated_property parameter. There are theoretically some attributes that don't have associated properties (although I can't think of any right now); we need to allow a Markup_Attribute to specify it doesn't have a corresponding property. We don't think it makes sense to have two pages that would have almost precisely the same content. Generally, the rule of thumb is this: <b>If the attribute is also a property, create a Markup_Attribute page and make sure it's pointing at the right DOM interface. If there's a property with no attribute, make it just an API_Object_Property</b>.
</p><p>Events are weird because they have both an Applies_to (the types of DOM interfaces they can be fired at), as well as their Subclass_of. There are many different event types that are interconnected with dependency relationships that it's important to model. Most of these relationships terminate with the vanilla Event object.
</p>
<h3><span class="mw-headline" id="Topics.2C_Topic_Clusters.2C_See_Also">Topics, Topic Clusters, See Also</span></h3>
<p>We use a number of organizing principles, and it's easy to get confused about how they all inter-relate and when you should use each one.
</p><p>First, <b>Topics</b>. Topics are simply special category pages that are common enough that they make sense to show in a form UI on most pages. You can see more information about them at <a href="/wiki/WPD:Topics" title="WPD:Topics" class="mw-redirect">WPD:Topics</a>.  You can think of Topics almost like "tags": if you can imagine more than 20 or so pages using them, and a realistic user scenario where someone would want to find all of those pages as a group, there should be a tag.
</p><p>Many articles have a See Also section. This section ranges from fully-automatically generated to completely manually generated. The see also sections sometimes include links from within WPD and sometimes include external links. 70 million years from now when we're done documenting everything, pages will use topic clusters, manual links, and external links sections--but not the "Manual Sections".
</p><p><b>Topic clusters</b> are the way that allows us to automatically generate portions of the See Also section automatically for articles on the WPD. A topic cluster (configured at <a href="/wiki/Property:Topic_Cluster" title="Property:Topic Cluster">Property:Topic_Cluster</a>) should be created whenever there's a grouping of articles that should all be listed on one-another's pages. The CSS Font topic cluster is a canonical example; there are a lot of CSS properties that deal directly with fonts and it makes sense to list all of them on one-another's pages. <b>If you check off a topic cluster for a page, it will automatically print out links to all other pages in its see also section.</b> Whereas Topics are designed to be visible to end users and a relatively small list, Topic clusters should be created whenever you want to have an automatically-curated grouping of See Also links. 
</p><p>The See Also section also has three free-form fields: <b>Manual Links</b>, <b>External Links</b>, and <b>Manual Sections</b>. 
</p><p><b>Manual links</b> is a section in the See Also section that should list any articles within WPD that should also be listed but where a Topic Cluster doesn't make sense. Don't include a header (it's automatically generated for you) but do include bullets for each line.
</p><p><b>External Links</b> is a section in the See Also section that should list links to any external resources (except for specs; those go in the Related Specifications form). Don't include a header (it's automatically generated for you) but do include bullets for each line.
</p><p><b>Manual Sections</b> is for articles that haven't yet made use of topic clusters appropriately. It's basically an escape hatch where you can just list whatever you want and it will be plopped into the see also section wholesale. 70 million years from now when we're done documenting everything, pages will use topic clusters, manual links, and external links sections--but not the "Manual Sections".
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:6395-0!*!0!!*!*!*!esi=1 and timestamp 20150731183042 and revision id 17022
 -->
