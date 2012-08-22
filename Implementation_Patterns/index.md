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

==Behind the Scenes==

{{TODO | Fill in the behind the scenes section}}