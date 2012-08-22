Web Platform Docs is currently built on MediaWiki (the same piece of software that Wikipedia is built on) and makes extensive use of two extensions, Semantic MediaWiki (SMW) and Semantic Forms, to organize information in a structured way, help make sure that articles have a consistent organization, and make it easier for mere mortals to edit articles.

This guide reviews a number of concepts related to these software packages, as well as how we use them to implement our organization on WPD, to help give the fledgling editor a good place to get started. This guide is ''not'' designed to be a comprehensive manual of style (we've already [[WPD:Manual_Of_Style|got one]]), but rather a guide to how all of these concepts are implemented.

The vast majority of editors will only have to use the (relatively) easy-to-use forms that we've created. A small number of editors, however, may want to understand how we've wired everything together so they can help modify or add to the information structure. We'll cover those two classes of use in two sections.

==Normal Editing==

{{Note | The WPD skin is under construction, and doesn't have an "Edit With Form" button. Switch to using the Vector skin instead to see it (for now).}}

===Editing pages===
If you're editing a page that's already been created, it's generally quite simple.

First, just make sure you're signed in. We've structured our content so that a number of editorial notes and action items are automatically hidden for logged-out users to avoid cluttering the interface. Logging in will display these for you.

Logging in will also give you edit access to articles. In normal MediaWiki, you would use the "Edit" button. That still exists for us, but it's hidden behind a drop down. The reason is that you should be using the '''Edit with form''' button. That button will use Semantic Forms to present a structured form for you to fill in instead of trying to create the page structure yourself. If you were to click Edit, you'd see the raw template calls that make up the page. You'd also be able to wreak more havoc if you changed some of the markup.

We've set up our templates so that we handle things like blank form fields in an appropriate way--something that would be hard to do without Semantic Forms.

===Creating New Pages===

Different page types have different forms. This makes sense--a page on a CSS property will have a different structure than a page on a DOM method. When you create a brand new page, however, by default here's no form type assigned. Is it up to you to figure out the correct form type to use from the list presented and create the stub based on that form.

{{Note | This create new page experience is not yet implemented.}}

It is important that you use the correct form, as that will control what form everyone ''else'' will see afterwards, and requires some manually mucking in the source of the page to undo.

===Using Templates===

Templates are an incredibly important concept in MediaWiki, and we use them ''all'' the time. Unlike Semantic MediaWiki or Semantic Forms, Templates are a core feature of the base install of MediaWiki. They're complicated and powerful, but this section will tell you all you need to know to ''use'' them.

====Basic Template Use====

Templates, at their simplest, are just automatic text substitution. When MediaWiki is converting a page's MediaWiki markup into HTML to display, when it encounters a template tag, it will simply replace that text with the content of the template.

In MediaWiki markup, templates look like this:

<syntaxhighlight>
 {{Foo}}
</syntaxhighlight>

The double-curly brace is the way that you instantly know that you're dealing with a template.

By default, templates all live in the Template namespace. If you see a template in the code and want to know how it works, open a new browser window and navigate to http://webplatform.org/docs/Template:Foo , where Foo is the template name you want to investigate. '''Note that underscores and spaces are exactly equivalent in page names and template names.'''

Knowing this fact will help you dig into what's going wrong, or what a template does, if you don't know.

There are some special template types; if you see something like

<syntaxhighlight>
{{#if: foo | first | second}}
</syntaxhighlight>

, that is, a # at the front, that's a special template that is built in, and thus does not have a Template: page.

====Investigating how templates work====

Again, templates are just like normal pages, except that when you invoke a template, their contents replace the template call (they're ''transcluded'').

A template's definition page, by convention, gives a short overview of what the template is for and what arguments (see the next sub-section) it takes. However, at first glance it's hard to figure out how the template '''works'''. This is because many templates use <nowiki><includeonly> and <noinclude></nowiki> tags to control which pieces of the template are the real business end, and which pieces are just documentation. If you want to see how a template actually works, '''click the edit button to see the raw markup.'''

====Passing arguments to templates====
Templates aren't very useful if they're just static text to use. That's where parameters come in. They're just like passing arguments to a method call.

Arguments can be passed in two ways, depending on how the template is defined: positional parameters or named parameters.

<syntaxhighlight>
{{Foo|This is the first positional parameter | This is the second positional parameter }}

{{Bar |title = This will be passed as the title parameter }}

{{Baz | This is a positional parameter | message= And this is a named parameter. They can be mixed.}}
</syntaxhighlight>

Again, different templates will expect either named or positional parameters. Check out the template's documentation (at [[Template:Foo]]) to see what arguments it expects.

Importantly, you '''can pass complicated MediaWiki markup as arguments''' to other templates, including ''other'' template calls. MediaWiki can handle nested templates.

====How templates use parameters====
This section isn't required to know how to use parameters, but may help in figuring out what a template's doing if you peek underneath the covers.

Inside of a template, it can use parameters with code like this: 
<syntaxhighlight>
My title is: {{{title}}}

My first parameter is: {{{1}}}
</syntaxhighlight>

That is, with ''three'' curly braces instead of two. The first example shows how a named parameter would be used, whereas the second example shows how a positional parameter would be used.

But this is not how most parameter uses look. The reason is that when written this way, if the value is empty, MediaWiki will print that call literally to the screen: <nowiki>{{{title}}}</nowiki>. That's bogus. So, in practice, we use a default feature to specify what value should be printed if the parameter is null:

<syntaxhighlight>
My title is {{{title | non-existent}}}.

{{{message|}}}
</syntaxhighlight>

As you can see, it's a vertical pipe character after the parameter name. You can either provide a value or leave it totally blank like in the last example. If you leave it blank, sometimes it's hard to see--that's why I'm explaining it here.

====Common templates====

* [[Template:TODO]] is for action items or ''implementation'' things that need to be changed in the page.
* [[Template:Editorial]] is for ''editorial'' action items that need to be fixed on the page. For example, if a page has the top-level "Flag" for "Examples need work" set, you could include this tag next to the specific example that needs help. These blocks don't show up to non-editors.

==Behind the Scenes==

There is ''no need'' to read this section unless you want to really roll up your sleeves and muck with our existing structure. This part gets messy. You have been warned.

If you're still here, go through and read and understand the whole section above.

===Major concepts===

There are a number of core concepts that we use in our implementation. They're all kind of loosely (and sometimes oddly) related, and at first it looks like a hopeless mess. But once you understand how they work, it makes a weird kind of sense.

====Templates====
Templates are the single most important concept. They're built directly into MediaWiki. They're explained in the first section of this article. 

We use templates all over the place. In fact, if you hit the ''Edit'' button (as opposed to the "Edit with form" button) you'll see that most of our page types are just big templates with a large number of parameters.

Templates are useful for imposing structure on your content. It allows us to make changes that affect lots of pages at once. For example, if we decided that the Values section should come before the Syntax section in CSS Property articles, we could make one change to the CSS Property template and it would automatically change all CSS property articles.

Templates are also required if you want to create a user-friendly form to edit a page.

Templates are also useful because it's possible to find all pages that include a template. This is why templates are great for TODOs, since we can list all of them.

{{TODO | Document how to construct links to find all instances of a template.}}

Finally, templates are great because they allow us to hide some of the ugly guts of setting properties or doing weird table formatting. 

{{TODO | Include links to template documentation }}

There are some built-in templates, like #if. You can find out more here: http://www.mediawiki.org/wiki/Help:Extension:ParserFunctions . Note there's a gotcha around doing table syntax in these; see at the bottom of this article.

{{Note | There's a potential gotcha with these special "templates": after the name, you have a '''colon''', not a pipe. }}

====Categories====

Categories are also built into MediaWiki. They're used extensively in Wikipedia, for example. By default a list of categories a page belongs to is listed at the bottom of the page.

If you find a category, you can view its documentation (including a page that lists all of the pages in that category) at http://webplatform.org/docs/Category:Foo

We use categories for a special purpose in our implementation: '''categories are how Semantic Forms knows which form to present to a user to edit the page.''' If you look at a category's documentation page (for example http://webplatform.org/docs/Category:CSS_Properties) you'll see that it includes markup that specifies which form those pages should use. 

Without markup on a page to specify that it's in a category (and if that category didn't have that markup to wire it to a specific form) then the "Edit with form" button wouldn't do anything.

In our implementation, the category is set within the template call. For example, if you inspect how [[/Template:CSS_Property]] is implemented, at the very end of the template is a call to add the CSS Properties category to the page. Thus, anyone who puts a call to <nowiki>{{CSS_Property}}</nowiki> on the page will now have the page wired up to use the CSS Property Form from now on.

====Forms====

Forms are the way that the "Edit with Form" button knows what UI to show to the user when they hit that button.

Again, in general the way that forms are tied to a specific page is because that page belongs to a category, which itself specifies which form to use.

Forms, surprisingly enough, live in the Form namespace: [[Form:CSS_Property]] . Like templates, they often keep much of their implementation hidden in <nowiki><includeonly></nowiki> blocks, so you'll have to hit ''Edit'' to see how they work.

Basically forms are just special templates that define how to build a page for editing. Forms generally have a one-to-one correspondence with templates.

Forms consist of a number of fields. These fields define input boxes and controls that users will fill in. When the user submits, the values for those fields will then be passed directly as parameters to the associated template. In fact, after editing with a form, if you hit the normal Edit button on the page, you can see that basically the output is just a template call with all of the arguments set up in the way the user did it in the form.

Note that creating sub-sections of forms that repeat (like the list of related specifications in the CSS Property form) or sections of form that you want to reuse in other forms, are advanced topics covered below.

You can see more documentation on how to configure forms here: http://www.mediawiki.org/wiki/Extension:Semantic_Forms/Defining_forms

====Properties====

Properties are one of the main features that ''Semantic'' MediaWiki provides. Properties allow you to attach structured data to a page that can be queried in interesting places later.

Properties are very rarely set by hand; often they are automatically written out inside of a template call based on a parameter passed in.

Properties are good for a few use cases:
* If the information is small, structured, and you can imagine wanting to query for it later.
* If you want to include that information onto other pages automatically.

A good example of the first use case is whether or not a CSS property is animatable. You could conceivably want to create a page that lists all of the CSS properties are animatable, and to do that you'd need the information in a structured format that you could query on.

A good example of the second use case is the Summary property. By defining it as a property, we make it possible to auto-generate pages that are listings of properties and include their summaries.

=====Configuration=====
Properties are defined in, you guessed it, the Property namespace: [[Property:Summary]]. Those definition pages include bits of configuration, and also list all of the pages that include that property.

Properties have a type. In practice we use strings (limited to 255 characters, but queryable) and text (no length limit, but can't be included as a query parameter, only ''output'' as the result of queries).

By default properties can take any value. However, you can use the <nowiki>Allows_type</nowiki> configuration property to limit the possible values to only specific types. If you do this, Semantic Forms will automatically create checkboxes for you in your form.

More information: http://semantic-mediawiki.org/wiki/Help:Properties_and_types

=====Property use=====

Properties can be applied to a page in handful of ways. The first is via a special link-like syntax: 
<syntaxhighlight>
The property is animatable: [[Animatable::value]]
</syntaxhighlight>

This syntax will apply the property to the page, but also print out the value and link to the property definition.

Sometimes you don't want that, either because you don't want the value to be visible, or because the property value is too long to be a link (for example I found that the Summary, which is of type text, wouldn't print correctly in this syntax).

For that, you can use this syntax: 

<syntaxhighlight>
{{#set:Animatable=Yes}}
</syntaxhighlight>

{{Note | As with other built-in "templates" that start with a #, that's a '''colon''', not a pipe after "set" }}

In practice you'll often see property calls inside of template definitions, and so often the value will be set via a parameter call.

====Queries====

Queries are how you select pages via properties and then print out some of their property-values in some form.

At the moment we don't use them, but soon we will use them to create method-listing pages, using inline queries.

More info: http://semantic-mediawiki.org/wiki/Help:Inline_queries

==Other stuff==

===How everything is wired together===

Here's how we use those patterns described above to implement our site so far.

We'll walk through the CSS Property template, via the sample page of [[css/properties/font-size]].

====The CSS Property page====

If you go to that page and hit edit, you'll see that basically it's just two templates: Flags and CSS_Property. If you were to edit with form you'd see that the form basically has one-to-one correspondence with those parameters.

CSS_Property is just a normal template (we can tell that based on the double-curly brace syntax), so that means we can see its definition at [[Template:CSS_Property]]. When we go there, we get a brief overview of what the parameters ''are'', but not how it ''works''. To do that, we'll need to hit "Edit".

When we do that, we skip to the <nowiki><includeonly></nowiki> section to see the actual implementation. It's pretty simple--mainly we just print a header for each section and then dump whatever was passed in via the parameter.

But here are some interesting patterns:

<syntaxhighlight>
==Summary==
{{{Summary}}}
{{#set:Summary={{{Summary}}} }}
</syntaxhighlight>

In the summary section we're printing out the value, but after that we're also manually setting the property value. This is because we don't want the normal linkified display of the text when you set a property inline, but we do want to register that property value with the page.

<syntaxhighlight>
{{#if: {{{Usage|}}}|
==Usage==
{{{Usage|}}}

|}}
</syntaxhighlight>

In this pattern we can see that we use the #if directive to either print out the Usage section if the user provided a value, or skip the entire section if the user didn't provide anything.

<syntaxhighlight>
{{#if: {{{Examples|}}}|
==Examples==
{{{Examples|}}}

| {{Editorial | This section should include examples. |type=Needs Examples}} }}
</syntaxhighlight>

This is basically the same, but slightly more complicated. We want to ensure that the examples section is always included in this article type. So if it's not, instead of not printing anything we print an editorial note (basically a TODO) to the screen.

<syntaxhighlight>
{{#if: {{{Specifications|}}} | 
==Related Specifications==
{{{!}} class="wikitable"
{{!}}-
! Specification !! Status !! Related Changes
{{{Specifications|}}}
{{!}}} | }}
</syntaxhighlight>

This is one of the more complicated pieces. It's where we print out the specifications table. A few things to note: <nowiki>{{!}}</nowiki> is a weird hack necessary to print out table syntax inside of #if parser functions (see Tables with Rows, below). Basically that template is just a single pipe character. Also, this section should be a table. First, we check if we should even show the section. If we should, we print out the header row of the table. The Specifications parameter will consist of all of the rows of the table glommed together--that's just how semantic forms does it. We'll investigate how that's set up in a bit.

<syntaxhighlight>
[[Category:CSS Properties|{{#titleparts:{{PAGENAME}}||-1}}]]
</syntaxhighlight>

This last piece is very important: it's the thing that applies the category to the page. Remember, this is how we specify which form to use. If we investigate the category page: http://webplatform.org/docs/Category:CSS_Properties we'll see that on that page a default form is defined. Following ''that'' to the form definition will help us see how the form is hooked up. (Yes, this all seems like a rube goldberg device).

====The CSS Property form====
Let's dive into the definition of the accompanying form, which we discovered by going to the category page: [[Form:CSS_Property]].

Again, like templates, most of the implementation is hidden in <nowiki><includeonly></nowiki> blocks. Click edit to see how it all works.

At the beginning there's a bunch of boiler plate that's not important to understand (you can just copy and paste it when you create new forms). Basically what it does is just defines that this form is attached to the CSS Property template. (You'll notice the Flags_form_section template. That's an interesting pattern to re-use pieces of forms. See the "Re-usable form components", below).

Most of this page is just normal wiki syntax. The important bits look like:

<syntaxhighlight>
{{{field|Summary}}}
</syntaxhighlight>

This is how you register form inputs and define which parameters of the associated template they should dump their results to.  Normally all you need is something simple like this, because the Summary form field should just dump directly into the Summary parameter of the CSS Property template.

There are all kinds of configuration things you can do here, like defining what values are allowed, different input types, etc. See http://www.mediawiki.org/wiki/Extension:Semantic_Forms/Defining_forms for more.

Here's an example of changing the input type:

<syntaxhighlight>
==Examples==
{{{field|Examples|input type=textarea|rows=10}}}
</syntaxhighlight>

This overrides the default textinput to use a text area.

But wait--the summary block gets a text area, too--but we didn't override it. How does that work?  Semantic Forms is kind of smart: it can figure out what kind of form input to display based on how the Property is configured. Recall that Summary is configured as a property because we need to be able to extract that information from a page and display it elsewhere. In fact, if you go to [[Property:Summary]] you can see we've defined it as type text, which is why Semantic Forms automatically shows it as a textarea. Semantic Forms figures all of this out because you've linked the template to the category to the form (to be honest, I'm not sure ''exactly'' how it does it).

But Examples is ''not'' a property (at least not at this moment). That's because we don't have any need to extract examples and display them elsewhere, so we just print examples out normally. This means there's no property associated with Examples, so Semantic Forms can't configure the form input automatically, and we have to do it ourselves.

Later, we see things like: 

<syntaxhighlight>
{{{field|Compatibility_desktop_rows|holds template}}}
{{{field|Compatibility_mobile_rows|holds template}}}
{{{field|Compatibility_notes_rows|holds template}}}
</syntaxhighlight>

These are the sections that allow users to add between 0 and n rows. We'll dig into those in the sub-forms section.

===Design Patterns===
====New pages====

Above we talked about the fact that the "Edit with form" button knows which form to use because the page includes a category which has a default form defined.

But wait--what about the very first time you edit a page? How does SMW know which form to use?

It doesn't.

It's weird, I know.

Basically, until you plop a (perhaps empty) template call on the page that prints out the category, SMW doesn't know what page type it is.

There are two ways to mitigate this. The first is that the Form: pages include a helpful input at the top to create a new page using that form.

The second is that we can change the Default form for the entire wiki.  What we'll do is create a default form that basically just contains links to the other forms. So when a user goes to a non-existent page they'll see a form that asks them to pick which form they actually want to use, which will forward them to the right form to use.

{{Note | We haven't implemented this default form thing yet. }}

====Building new page types====

When you go to build a new page type, you generally are going to need four pieces:
* The main template, which will print out all the values and also print out the category.
* The category that we'll use to associated with the form.
* The form itself.
* An example page to use the form and debug with.

In practice, what you'll do is have four tabs open and be edit/save/refreshing all of them piece by piece to build out your form.

When you create your form, it's important to follow the best practices of including the Flags and Attribution sections (see below).

====Only including some sections if there's content to show====

This pattern is done like this:

<syntaxhighlight>
{{#if: {{{Specifications|}}} | 
==Related Specifications==
{{{!}} class="wikitable"
{{!}}-
! Specification !! Status !! Related Changes
{{{Specifications|}}}
{{!}}} | }}
</syntaxhighlight>

This is a complicated example because it has a conditional table (the specifications parameter will be filled with rows of data glommed together).  See the deep dive above for more discussion of this pattern.

====Re-usable form components====

There are some pieces of forms that we'll want to re-use in other forms. Examples include the Flags section, the Attribution section, and others.

{{Note | We've only done the Flags section like this so far.}}

The pattern to do this is kind of weird: we just create a simple template to contain the bit of form we want to reuse.

In the main form we include it with:

<syntaxhighlight>
{{Flags form section}}
//Normal template begins below
{{{for template|CSS Property}}}
...
</syntaxhighlight>

just like any other template.

The contents look like this:

<syntaxhighlight>
<nowiki>{{{for template|Flags}}}</nowiki>
'''Please enter below any issues that apply to this page.'''
{| class="formtable" style="border: 1px solid black; background: #fe9; font-size: smaller;"
! High-level issues:
| <nowiki>{{{field|High-level issues|property=High-level issue|list}}}</nowiki>
|-
! Content:
| <nowiki>{{{field|Content|property=Content quality flag|list}}}</nowiki>
|-
! Compatibility:
| <nowiki>{{{field|Compatibility|property=Compatibility quality flag|list}}}</nowiki>
|-
! Examples:
| <nowiki>{{{field|Examples|property=Examples quality flag|list}}}</nowiki>
|-
! Accessibility:
| <nowiki>{{{field|Accessibility|property=Accessibility flag|list}}}</nowiki>
|}
<nowiki>{{{end template}}}</nowiki>
</syntaxhighlight>

Basically, it's just the sub-piece of the form we need.

=====Sub-forms within the main template and outside=====
There are two times you might need this pattern: for things whose parameters should be passed to ''another'' template, like Flags (which prints its contents out ''outside'' of the main template, like CSS Property), or for things that should be included in the ''same'' template.

The example above is for the former case. That's why the form template instantiation goes ''outside'' the main <nowiki>{{{for|template-name}}}</nowiki> block, and the template itself has the weird <nowiki>{{{for template|flags}}}</nowiki>, wrapped in nowiki tags.

However, if you're doing the latter, it's easier. The form template doesn't need that special for block above and below the template, and you should instantiate your template ''inside'' the main <nowiki>{{for template}}</nowiki> block.

====Sub-forms====

In the [[Form:CSS_Property]] form, we have a few sections that allow you to add 0 or more sub-sections. Examples are the browser compatibility rows and the related specifications.

These basically use sub-forms and sub-templates to allow this to happen. Here's how the related specifications section works:

<syntaxhighlight>
{{{field|Specifications|holds template}}}
</syntaxhighlight>

This part is included in the main form where we want the sub-form to show up. It says that we should look elsewhere for where this form section is defined.

Below, outside of the <nowiki>{{{end template}}}</nowiki> call, we see:

<syntaxhighlight>
<!-- Begin template for Related specfications -->
{{{for template|Related Specification|multiple|label=Related Specifications|embed in field=CSS Property[Specifications]}}}
{| class="formtable"
! Name:
| {{{field|Name}}}
|-
! URL:
| {{{field|URL}}}
! Status:
| {{{field|Status}}}
! Relevant changes:
! {{{field|Relevant_changes}}}
|}
{{{end template}}}
<!-- End template for Related Specifications -->
</syntaxhighlight>

Basically, we're defining another form template in the same page that we'll use in the main form.

Notice that the beginning of the block says it's for a template called Related Specifications. Indeed, if you go to [[Template:Related_Specifications]], you'll see that we've defined a simple template that takes in four parameter and then outputs a table row.

Inside of the form definition we just define a simple form just like normal, that allows users to specify the four inputs to fill into that sub-template.

When the user hits submit on the main form, the form will automatically go through and stamp out an instance of the sub-template (with correct arguments) for each sub-form section the user created. It will then concatenate them together and pass them into the top-level template with the name we defined in the main body of the form, in this case "Specifications."

That's it!

====Tables with rows====

In some cases we want form users to define multiple rows of a table, like in Related Specifications.

We do this by defining a Sub-form (see the section immediately above).  The result of that sub-form is a concatenation of all of sub-templates filled in with their values.

In the case of [[Template:Related_Specifications]] you can see that the template just outputs a single row in MediaWiki table syntax. In the main [[Template:CSS_Property]] template, we output a header row and then just dump all of the contents of the Specifications parameter (which, again, is just a concatenation of those table rows from the Related Specifications template) right there.

One thing to be aware of when you're building up tables like this is that we need to be aware of the Table Gotcha (see next section) if we're using #if blocks.

See http://www.mediawiki.org/wiki/Help:Tables for more information.

====Gotcha: Table syntax====

We use tables a lot. Some parts of the page should have tables if there's rows of content to show, and no table if not. There's a weird gotcha to be aware of.

Here's the normal #if syntax:

<syntaxhighlight>
{{#if: condition | value | else-value}}
</syntaxhighlight>

Here's normal syntax for a table: 

<syntaxhighlight>
{| class="wikitable"
! Header-value 1 !! Header-value-2
|-
| Row-value 1 || Row-value-2
|}
</syntaxhighlight>

The problem is that in the #if block, every pipe character it encounters will be interpreted literally. So if you try to include pipe characters for the table syntax as part of the value or else-value, it just won't work.

This is weird. The solution is even weirder.

Basically, the hack is that we have a special template defined: [[Template:!]]. This template does precisely one thing: it prints out a pipe character. This hack gets around the weird limitation of #if blocks and allows you to conditionally include parts of tables. Here's an example where we use the hack:

<syntaxhighlight>
{{#if: {{{Specifications|}}} | 
==Related Specifications==
{{{!}} class="wikitable"
{{!}}-
! Specification !! Status !! Related Changes
{{{Specifications|}}}
{{!}}} | }}
</syntaxhighlight>

More information on this pattern (no, I did not come up with this crazy solution): http://meta.wikimedia.org/wiki/Help:Table#Producing_table_syntax_using_templates_and.2For_parser_functions