---
title: Templates
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - 'Template:Foo Section'
    - 'Template:Foo Form Section'
    - 'Form:Foo'
uri: 'WPD:Implementation Patterns/Templates'

---
**This page is a specific overview of our primary work-horse templates, and complements the more high-level [WPD:Implementation\_Patterns](/WPD:Implementation_Patterns) guide. It assumes you have read and understood that guide.**

## General Organization

Almost every reference page uses one of \~20 major templates/forms. You can view a comprehensive list at [WPD:New\_Page](/WPD:New_Page).

There are many common elements on these reference pages that occur either on all of the major page type templates or occur on more than one. An example is the [summary section template](/Template:Summary_Section). For each of these sections, we create a separate template to do the work. We also create a template of the *form* for that template. Then, in the form for the main page type, we include the sub-form template. This automatically configures the form to deposit the sub-template on the page when it is saved.

The summary section is a good example. We have the [main template](/Template:Summary_Section) that handles the work of taking in parameters and rendering them out in a standard way, as well as setting certain semantic media wiki properties in the right way. If you "Edit Source" on almost any reference page, you'll see that there's an instantiation of this template on the page. We also have the [form template](/Template:Summary_Form_Section) which configures how that part of the form will show up and what fields it will have. If you look at the source of any of the major page-type forms, like [the css property form](/Form:CSS_Property), you'll see that there is a call to this Summary\_Form\_Section template.

Most page-type forms use sub-forms and sub-templates as much as possible, and use the "central" template--the one most specific to this page-type--only for properties and form fields that are specific to this page type and this page type only. That "central" template is often the one that deposits the appropriate category on the page to wire it up to the form. The most simple of these page-type forms is the [one for basic pages](/Form:Basic). There aren't any special parameters to set, so basically that central template *just* sets the Basic Pages category so that in the future when the user hits the Edit button the right form will show.

**TODO**: Represent the information in this page as a diagram

## Template/Form Naming Conventions

In the vast majority of cases, we use consistent naming conventions so it's easy to figure out what the related Form/Template is called without having to investigate it.

For page types:

-   **Core template**: [Template:Foo](/Template:Foo)
-   **Core category**: [[Category:Foos]], where "Foos" is the english plurilization of the core template name.
-   **Core form**: [Form:Foo](/w/index.php?title=Form:Foo&action=edit&redlink=1)

**Note**: Basic page's form is an exception to these rules. The main form is at [Template:Basic\_Page](/Template:Basic_Page) but the form is at [Form:Basic](/Form:Basic)

 For sub-templates and sub-forms:

-   **Template**: [Template:Foo\_Section](/w/index.php?title=Template:Foo_Section&action=edit&redlink=1)
-   **Sub-Form**: [Template:Foo\_Form\_Section](/w/index.php?title=Template:Foo_Form_Section&action=edit&redlink=1) **Note**: the sub-form is implemented as a *template*, not a *form*.

## Specific Sub-Forms

There are many sub-forms and sub-templates that we use very often. These are generally easy to discover by viewing the source of the page-type form you're interested in.

-   [Template:Page\_Title](/Template:Page_Title)
-   [Template:Flags](/Template:Flags)
-   [Template:Standardization\_Status](/Template:Standardization_Status)
-   [Template:API\_Name](/Template:API_Name)
-   [Template:Summary\_Section](/Template:Summary_Section)
-   [Template:Examples\_Section](/Template:Examples_Section)
-   [Template:Notes\_Section](/Template:Notes_Section)
-   [Template:Related\_Specifications\_Section](/Template:Related_Specifications_Section)
-   [Template:Compatibility\_Section](/Template:Compatibility_Section)
-   [Template:See\_Also\_Section](/Template:See_Also_Section)
-   [Template:Topics](/Template:Topics)
-   [Template:External\_Attribution](/Template:External_Attribution)
-   *This list is not comprehensive yet. Please add more sub-forms to it!*

## Page-Type Organization

Again, the common elements of pages (like summaries) are handled in sub-forms and sub-templates that are used the same on every page. Most page-types have a specific "central" template that handles the interesting bits that are specific to this page type. For example, the [css property form](/Form:CSS_Property) defines fields for whether or not the field is inheritable and what its legal values are.

The following sections give a more in-depth overview of how these main page-types are inter-related. Documentation that is mainly about one specific page-type (and not how they inter-relate) should be found on the given Template itself.

**TODO**: A lot of the documentation in the following sections actually should live in the specific documentation sections on each Template's page.

### API Objects, Methods, and Properties

Some of the most common page-types are [Template:API\_Object](/Template:API_Object), [Template:API\_Object\_Method](/Template:API_Object_Method), and [Template:API\_Object\_Property](/Template:API_Object_Property). They are also some of the most confusing when you first look at them.

The API Object template is the one that should be used for the object that contains methods and properties. It will ultimately have an exhaustive list of all of its associated properties, methods, events, constants, etc. However, if you edit a page that uses this template you will see that there isn't much content on the page at all!

The way the API\_Object template works is that all of the applicable API\_Object\_Method and API\_Object\_Property pages set an Applies\_to field that specifies the page they "apply to": the API\_Object. Then, when we generate the text for that page, we use a semantic media wiki query to select all pages that apply to it and print out their information.

Importantly, it's also possible to define the **Subclass\_of** property of API\_Objects. This is the way we formally represent which objects this inherits properties and methods of--something that's critically important for many DOM APIs (for example, the chain for AudioElement looks like: AudioElement --\> MediaElement --\> HTMLElement --\> Element --\> Node). We automatically print out the properties and methods of the immediate parent. For performance reasons we don't print out any methods or properties that come from higher up in the chain, but if you want to, you can manually specify more ancestors in the Subclass\_of field by separating them with commas (most recent ancestor first).

### Summaries, Page\_Title, and API\_Name

As far as MediaWiki is concerned, the "title" of a page is the entirety of the URL after the "<http://docs.webplatform.org/wiki/>" part. This leads to many pages having long names like "css/properties/font-size" when "font-size" is far more appropriate. Also, when we include a link to a page on another page, we often want to provide a bit of context on what the page is about.

We get around this by setting Semantic Media Wiki properties for the Page\_Title, API\_Name, and Summary.

The Summary is simply a property of type Text that is set to contain the Summary field in the form. By setting a property, other pages (like [Template:API\_Listing](/Template:API_Listing)) can automatically pull out that information and display it in a table.

The [page title](/Template:Page_Title) template is how you set the page title. If the editor provided a value, it uses that value. However, it defaults to using the last part of the page-title. So, for example, on "css/properties/font-size", it would default to "font-size".

The [API name](/Template:API_Name) template overlaps in use with the page title template quite a bit, but historically it predates it. Whereas page title is what the page should be called when presented as a link, the API\_Name is the precise text used to invoke that API. The API\_Name is used when generating automatic examples and theoretically for more stuff in the future. For methods and properties, it would be the method/property name. For things like CSS selectors, however, it would be things like "\#" or ".". Pages with weird API\_Names are the cases where the page title might be different than the API\_Name, for example the page might have a title of "Class Selector", but the API\_Name might have a value of ".".

### API Listing

The [API Listing](/Template:API_Listing) template is somewhat confusingly named. Unlike the API\_Object template which is the canonical reference for the methods, properties, and events that apply to a given interface object, the API Listing template is more about just listing all sub-pages that match some criteria.

The API\_Listing page template is used for many pages that are primarily about organization and not about content. For example, the [css/properties](/css/properties) page uses this template to list all css properties.

The listing is powered in one of two ways: the better way and the worse way.

#### The Worse Way

First, the worse way.

It is possible in MediaWiki to enumerate all sub-pages that are descendants of a given page. We implement this in the API Listing template with a parameter to "Print all sub-pages rooted here."

There are two major limitations of this approach. First, it prints out *all descendants* when what you normally want is only the *direct children*. This creates listings that are far too full. Secondly, the listings use the full page name (things like "css/properties/font-size"), which is ugly, and doesn't include the page summary.

The reason we have this is because of a mistake we made in the import. The prettier way of printing sub-pages relies on the "Page\_Title", "Path", and "Summary" properties being set on pages. However, when we did the import, we goofed--we didn't include the templates that set those properties. Thus, most pages imported don't have those properties set until they've been manually edited at least once (we refer to a manual edit without substantive changes, whose only purpose is to make sure all relevant templates and properties are included, a "touch").

We figured at the beginning that it was better to comprehensively list all descendants instead of doing the better listing format but missing some pages seemingly randomly--perhaps forgetting about them for all time.

Over time, as more articles are touched, every API\_Listing page should transition to using the Better Way and stop using this "Print all sub-pages rooted here" checkbox. Note that while we're transitioning, it's best practice to include the better way print out as well as the comprehensive sub-listing (they can coexist on the page). Once we've verified the better listing is comprehensive, we can uncheck the sub-listing option.

#### The Better Way

The better way uses Semantic Media Wiki query syntax to select which pages to show. You can see what syntax is allowed at [this page](http://semantic-mediawiki.org/wiki/Help:Selecting_pages). Basically you write a query that selects pages based on categories they're in or the values of semantic media wiki properties on them.

Note that it's actually kind of difficult to select pages that are only direct children of a page (as opposed to all descendants). We get around this (somewhat) by having every page have a Path property, which is just set to the name of the page (e.g. "css/properties/font-size"). You can then use the like operator in the SMW query to do some matching.

**Note**: Pro tip: you can easily see what properties are currently applied to a page by going to Tools \> Browse Properties

 In practice, the queries you will create will be some combination of a given template type combined with it having a URL of a given form.

### Attributes, properties, and DOM

**Note**: This part gets hairy really fast, and our current information organization for it has known problems (see the notes from the community meeting on 10/30 for just a few examples of things we need to change).

 First of all, most DOM interfaces should use the [API Object template](/Template:API_Object), since they primarily consist of methods/properties on an API interface.

Markup\_Elements should use the DOM\_Interface property to point to the *most specific DOM interface that applies to them.* For example, the \<audio\> markup\_element page would point to the AudioElement page. For many "simple" elements, the most specific DOM interface is simply HTMLElement.

Markup\_Attribute pages should point at the most-specific DOM interface to which they apply (yes, this is conceptually a bit weird). In the future for each markup\_element, we will check to see what its DOM\_Interface is, and then query for all attributes that are associated with that DOM\_Interface and show those.

Attributes are weird for another reason: generally every attribute on a markup element has a corresponding property on associated DOM interface. However, this corresponding property might be slightly different (for example, switching from hyphens to camel casing); we need to update the Markup\_Attribute template to have an often-automatically-generated Associated\_property parameter. There are theoretically some attributes that don't have associated properties (although I can't think of any right now); we need to allow a Markup\_Attribute to specify it doesn't have a corresponding property. We don't think it makes sense to have two pages that would have almost precisely the same content. Generally, the rule of thumb is this: **If the attribute is also a property, create a Markup\_Attribute page and make sure it's pointing at the right DOM interface. If there's a property with no attribute, make it just an API\_Object\_Property**.

Events are weird because they have both an Applies\_to (the types of DOM interfaces they can be fired at), as well as their Subclass\_of. There are many different event types that are interconnected with dependency relationships that it's important to model. Most of these relationships terminate with the vanilla Event object.

### Topics, Topic Clusters, See Also

We use a number of organizing principles, and it's easy to get confused about how they all inter-relate and when you should use each one.

First, **Topics**. Topics are simply special category pages that are common enough that they make sense to show in a form UI on most pages. You can see more information about them at [WPD:Topics](/WPD:Topics). You can think of Topics almost like "tags": if you can imagine more than 20 or so pages using them, and a realistic user scenario where someone would want to find all of those pages as a group, there should be a tag.

Many articles have a See Also section. This section ranges from fully-automatically generated to completely manually generated. The see also sections sometimes include links from within WPD and sometimes include external links. 70 million years from now when we're done documenting everything, pages will use topic clusters, manual links, and external links sections--but not the "Manual Sections".

**Topic clusters** are the way that allows us to automatically generate portions of the See Also section automatically for articles on the WPD. A topic cluster (configured at [Property:Topic\_Cluster](/Property:Topic_Cluster)) should be created whenever there's a grouping of articles that should all be listed on one-another's pages. The CSS Font topic cluster is a canonical example; there are a lot of CSS properties that deal directly with fonts and it makes sense to list all of them on one-another's pages. **If you check off a topic cluster for a page, it will automatically print out links to all other pages in its see also section.** Whereas Topics are designed to be visible to end users and a relatively small list, Topic clusters should be created whenever you want to have an automatically-curated grouping of See Also links.

The See Also section also has three free-form fields: **Manual Links**, **External Links**, and **Manual Sections**.

**Manual links** is a section in the See Also section that should list any articles within WPD that should also be listed but where a Topic Cluster doesn't make sense. Don't include a header (it's automatically generated for you) but do include bullets for each line.

**External Links** is a section in the See Also section that should list links to any external resources (except for specs; those go in the Related Specifications form). Don't include a header (it's automatically generated for you) but do include bullets for each line.

**Manual Sections** is for articles that haven't yet made use of topic clusters appropriately. It's basically an escape hatch where you can just list whatever you want and it will be plopped into the see also section wholesale. 70 million years from now when we're done documenting everything, pages will use topic clusters, manual links, and external links sections--but not the "Manual Sections".
