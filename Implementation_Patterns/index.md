Web Platform Docs is currently built on MediaWiki (the same piece of software that Wikipedia is built on) and makes extensive use of two extensions, Semantic MediaWiki (SMW) and Semantic Forms, to organize information in a structured way, help make sure that articles have a consistent organization, and make it easier for mere mortals to edit articles.

This guide reviews a number of concepts related to these software packages, as well as how we use them to implement our organization on WPD, to help give the fledgling editor a good place to get started. This guide is ''not'' designed to be a comprehensive manual of style (we've already [[WPD:Manual_Of_Style|got one]]), but rather a guide to how all of these concepts are implemented.

The vast majority of editors will only have to use the (relatively) easy-to-use forms that we've created. A small number of editors, however, may want to understand how we've wired everything together so they can help modify or add to the information structure. We'll cover those two classes of use in two sections.

==Normal Editing==

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

By default, templates all live in the Template namespace. If you see a template in the code and want to know how it works, open a new browser window and navigate to http://webplatform.org/docs/Template:Foo , where Foo is the template name you want to investigate.

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

Again, different templates will expect either named or positional parameters. Check out the template's documentation (at http://webplatform.org/docs/Template:Foo) to see what arguments it expects.

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

====Categories====

Categories are also built into MediaWiki. They're used extensively in Wikipedia, for example. By default a list of categories a page belongs to is listed at the bottom of the page.

If you find a category, you can view its documentation (including a page that lists all of the pages in that category) at http://webplatform.org/docs/Category:Foo

We use categories for a special purpose in our implementation: '''categories are how Semantic Forms knows which form to present to a user to edit the page.''' If you look at a category's documentation page (for example [[Category:CSS_Properties|CSS_Properties]] ) you'll see that it includes markup that specifies which form those pages should use. 

Without markup on a page to specify that it's in a category (and if that category didn't have that markup to wire it to a specific form) then the "Edit with form" button wouldn't do anything.

====Forms====

====Properties====

==Other stuff==

===How everything is wired together===
===Design Patterns===
====Sub-forms====
====Re-usable form components====
====Table syntax====