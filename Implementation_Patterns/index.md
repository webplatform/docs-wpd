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

==Behind the Scenes==

{{TODO | Fill in the behind the scenes section}}