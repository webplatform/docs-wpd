---
title: WPD:Implementation Patterns
---
<h1><span class="mw-headline" id="Implementation_patterns">Implementation patterns</span></h1>
<p>Web Platform Docs is currently built on MediaWiki (the same piece of software that Wikipedia is built on) and makes extensive use of two extensions, Semantic MediaWiki (SMW) and Semantic Forms, to organize information in a structured way, help make sure that articles have a consistent organization, and make it easier for mere mortals to edit articles.
</p><p>This guide reviews a number of concepts related to these software packages, as well as how we use them to implement our organization on WPD, to help give the fledgling editor a good place to get started. This guide is <i>not</i> designed to be a comprehensive manual of style (we've already <a href="/wiki/WPD:Manual_Of_Style" title="WPD:Manual Of Style" class="mw-redirect">got one</a>), but rather a guide to how all of these concepts are implemented.
</p><p>The vast majority of editors will only have to use the (relatively) easy-to-use New Page forms. A small number of you, however, may want to understand how everything is wired together so you can help modify or add to the information structure. 
</p>
<h2><span class="mw-headline" id="Normal_Editing">Normal Editing</span></h2>
<h3><span class="mw-headline" id="Editing_pages">Editing pages</span></h3>
<p>If you are editing a page that has already been created, the process is generally quite simple.
</p><p>First, sign in. A number of editorial notes and action items are automatically hidden for logged-out users to avoid cluttering the interface. Logging in will enable you to see these editorial notes.
</p><p><br />
</p>
<div class="note">
<p><b>Note</b>:  This hiding of editorial notes for non-logged-in users is not yet implemented. Editorial notes show for both logged in and logged out users.
</p>
</div>
<p><br />
Logging in will also give you edit access to articles. In normal MediaWiki, the <b>Edit</b> button would show you the raw source of the page. That still exists for us, but it's hidden behind a drop down and called <b>Edit source</b>. The reason is that you should be using the <b>Edit</b> button, which we've changed to bring you to the edit-with-form editing experience. That button will use Semantic Forms to present a structured form for you to fill in instead of trying to create the page structure yourself. If you were to click Edit Source, you'd see the raw template calls that make up the page. You'd also be able to wreak more havoc if you changed some of the markup.
</p><p>The templates are set up to handle things like blank form fields in an appropriate way--something that would be hard to do without Semantic Forms.
</p>
<h3><span class="mw-headline" id="Creating_new_pages">Creating new pages</span></h3>
<p>Different page types have different forms. This makes sense--a page on a CSS property will have a different structure than a page on a DOM method. When you create a brand new page, however, by default there's no form type assigned. Is it up to you to figure out the correct form type to use from the list presented and create the stub based on that form. We have a listing of all pages at <a href="/wiki/WPD:New_Page" title="WPD:New Page">WPD:New_Page</a>.
</p><p>It is important that you use the correct form, as that will control what form everyone <i>else</i> will see afterwards, and it requires some manually mucking in the source of the page to undo.
</p>
<h3><span class="mw-headline" id="Using_templates">Using templates</span></h3>
<p>Templates are an incredibly important concept in MediaWiki, and we use them <i>all</i> the time. Unlike Semantic MediaWiki or Semantic Forms, Templates are a core feature of the base install of MediaWiki. They're complicated and powerful, but this section will tell you all you need to know to <i>use</i> them.
</p>
<h4><span class="mw-headline" id="Basic_template_use">Basic template use</span></h4>
<p>Templates, at their simplest, are just automatic text substitution. When MediaWiki is converting a page's MediaWiki markup into HTML to display, when it encounters a template tag, it will simply replace that text with the content of the template.
</p><p>In MediaWiki markup, templates look like this:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"> {{TODO}}</pre></div></div>
<p>The double-curly brace is the way that you instantly know that you are dealing with a template.
</p><p>By default, templates all live in the Template namespace. If you see a template in the code and want to know how it works, open a new browser window and navigate to http://docs.webplatform.org/wiki/Template:Foo, where Foo is the template name you want to investigate. <b>Note that underscores and spaces are exactly equivalent in page names and template names.</b>
</p><p>Knowing this fact will help you dig into what is going wrong, or what a template does, if you don't know.
</p><p>There are some special template types; if you see something like this:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{#if: foo | first | second}}</pre></div></div>
<p>that is, a # at the front, that's a special template that is built in, and thus does not have a Template: page.
</p>
<h4><span class="mw-headline" id="Investigating_how_templates_work">Investigating how templates work</span></h4>
<p>Again, templates are just like normal pages, except that when you invoke a template, their contents replace the template call (they are <i>transcluded</i>).
</p><p>A template's definition page, by convention, gives a short overview of what the template is for and what arguments (see the next sub-section) it takes. However, at first glance it's hard to figure out how the template <b>works</b>. This is because many templates use &lt;includeonly&gt; and &lt;noinclude&gt; tags to control which pieces of the template are the real business end, and which pieces are just documentation. If you want to see how a template actually works, <b>click the edit button to see the raw markup.</b>
</p>
<h4><span class="mw-headline" id="Passing_arguments_to_templates">Passing arguments to templates</span></h4>
<p>Templates are not very useful if they're just static text to use. That's where parameters come in. They are just like passing arguments to a method call.
</p><p>Arguments can be passed in two ways, depending on how the template is defined: positional parameters or named parameters.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{Foo|This is the first positional parameter | This is the second positional parameter }}
&#160;
{{Bar |title = This will be passed as the title parameter }}
&#160;
{{Baz | This is a positional parameter | message= And this is a named parameter. They can be mixed.}}</pre></div></div>
<p>Again, different templates will expect either named or positional parameters. Check out the template's documentation (at <a href="/wiki/Template:Foo" title="Template:Foo">Template:Foo</a>) to see what arguments it expects.
</p><p>Importantly, you <b>can pass complicated MediaWiki markup as arguments</b> to other templates, including <i>other</i> template calls. MediaWiki can handle nested templates.
</p><p><br />
</p>
<div class="note">
<p><b>Note</b>:  One of the most common gotchas is if you use a pipe character (a |) in the parameter value. This will break many pages in hard-to-diagnose ways. Importantly, almost everything you fill into a form field when editing a page will be passed into a template, and thus should not include any unescaped pipes. Find out more at <a href="/wiki/WPD:Manual_Of_Style/Gotchas" title="WPD:Manual Of Style/Gotchas" class="mw-redirect">WPD:Manual_Of_Style/Gotchas</a> 
</p>
</div>
<p><br />
</p>
<h4><span class="mw-headline" id="How_templates_use_parameters">How templates use parameters</span></h4>
<p>This section is not required to know how to use parameters, but may help you figuring out what a template is doing if you peek underneath the covers.
</p><p>Inside of a template, it can use parameters with code like this: 
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">My title is: {{{title}}}
&#160;
My first parameter is: {{{1}}}</pre></div></div>
<p>That is, with <i>three</i> curly braces instead of two. The first example shows how a named parameter would be used, whereas the second example shows how a positional parameter would be used.
</p><p>But this is not how most parameter uses look. The reason is that when written this way, if the value is empty, MediaWiki will print that call literally to the screen: {{{title}}}. That's bogus. So, in practice, we use a default feature to specify what value should be printed if the parameter is null:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">My title is {{{title | non-existent}}}.
&#160;
{{{message|}}}</pre></div></div>
<p>As you can see, it is a vertical pipe character after the parameter name. You can either provide a value or leave it totally blank like in the last example. If you leave it blank, sometimes it's hard to see--that's why I'm explaining it here.
</p>
<h4><span class="mw-headline" id="Common_templates">Common templates</span></h4>
<ul><li> <a href="/wiki/Template:TODO" title="Template:TODO">Template:TODO</a> is for action items or <i>implementation</i> things that need to be changed in the page.</li>
<li> <a href="/wiki/Template:Editorial" title="Template:Editorial">Template:Editorial</a> is for <i>editorial</i> action items that need to be fixed on the page. For example, if a page has the top-level "Flag" for "Examples need work" set, you could include this tag next to the specific example that needs help. These blocks don't show up to non-editors. Most often you'll actually use one of the sub-templates (which are listed from the <a href="/wiki/Template:Editorial" title="Template:Editorial">Template:Editorial</a> page).</li>
<li> <i>And many more</i>. We use templates for many things.</li></ul>
<p><br />
</p>
<div class="note">
<p><b>Note</b>:  You can find a more in-depth overview of how our work-horse templates are set up at <a href="/wiki/WPD:Implementation_Patterns/Templates" title="WPD:Implementation Patterns/Templates">the templates sub-page of this guide</a>.
</p>
</div>
<p><br />
</p>
<h2><span class="mw-headline" id="Behind_the_scenes">Behind the scenes</span></h2>
<p><b>There is <i>no need</i> to read this section unless you want to really roll up your sleeves and muck with our existing structure. This part gets messy. You have been warned.</b>
</p><p>If you're still here, go through and read and understand the whole section above.
</p>
<h3><span class="mw-headline" id="Major_concepts">Major concepts</span></h3>
<p>There are a number of core concepts that we use in our implementation. They're all kind of loosely (and sometimes oddly) related, and at first it looks like a hopeless mess. But once you understand how they work, it makes a weird kind of sense.
</p>
<h4><span class="mw-headline" id="Templates">Templates</span></h4>
<p>Templates are the single most important concept. They're built directly into MediaWiki. They're explained in the first section of this article. 
</p><p>We use templates all over the place. In fact, if you hit the <i>Edit source</i> button (as opposed to the "Edit" button) you'll see that most of our page types are just big templates with a large number of parameters. (For those of you familiar with Semantic Forms, our Edit button would normally be called "Edit with Form", and our "Edit source" button would normally be called "Edit".)
</p><p>Templates are useful for imposing structure on your content. It allows us to make changes that affect lots of pages at once. For example, if we decided that the Values section should come before the Syntax section in CSS Property articles, we could make one change to the CSS Property template and it would automatically change all CSS property articles.
</p><p>Templates are also required if you want to create a user-friendly form to edit a page.
</p><p>Templates are also useful because it's possible to find all pages that include a template. This is why templates are great for TODOs, since we can list all of them. If you want to find all of the articles that include a template, visit the template's page, then click 'What links here' in Tools.  You may want to select 'Hide links' if you only want to see pages that use (or <i>transclude</i>) the template.
</p><p>Finally, templates are great because they allow us to hide some of the ugly guts of setting properties or doing weird table formatting. 
</p><p>There are some built-in templates, like #if. You can find out more here: <a class="external free" href="https://www.mediawiki.org/wiki/Help:Extension:ParserFunctions">https://www.mediawiki.org/wiki/Help:Extension:ParserFunctions</a> . Note there's a gotcha around doing table syntax in these; see at the bottom of this article.
</p><p><br />
</p>
<div class="note">
<p><b>Note</b>:  There's a potential gotcha with these special "templates": after the name, you have a <b>colon</b>, not a pipe. 
</p>
</div>
<p><br />
</p>
<h4><span class="mw-headline" id="Categories">Categories</span></h4>
<p>Categories are also built into MediaWiki. They're used extensively in Wikipedia, for example. By default a list of categories a page belongs to is listed at the bottom of the page.
</p><p>If you find a category, you can view its documentation (including a page that lists all of the pages in that category) at <a rel="nofollow" class="external free" href="http://webplatform.org/docs/Category:Foo">http://webplatform.org/docs/Category:Foo</a> (replace "Foo" with the category name in question).
</p><p>We use categories for a special purpose in our implementation: <b>categories are how Semantic Forms knows which form to present to a user to edit the page.</b> If you look at a category's documentation page (for example <a rel="nofollow" class="external free" href="http://webplatform.org/docs/Category:CSS_Properties">http://webplatform.org/docs/Category:CSS_Properties</a>) you'll see that it includes markup that specifies which form those pages should use. 
</p><p>Without markup on a page to specify that it's in a category (and if that category didn't have that markup to wire it to a specific form) then the "Edit" button would just take you directly to the scary, confusing edit source view
</p><p>In our implementation, the category is set within the template call. For example, if you inspect how <a href="/wiki/Template:CSS_Property" title="Template:CSS Property">Template:CSS_Property</a> is implemented, at the very end of the template is a call to add the CSS Properties category to the page. Thus, anyone who puts a call to {{CSS_Property}} on the page will now have the page wired up to use the CSS Property Form from now on.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Document how to switch a page type. 
</p>
</div>
<h4><span class="mw-headline" id="Forms">Forms</span></h4>
<p>Forms are the way that the "Edit" button knows what UI to show to the user when they hit that button.
</p><p>Again, in general the way that forms are tied to a specific page is because that page belongs to a category, which itself specifies which form to use.
</p><p>Forms, surprisingly enough, live in the Form namespace: <a href="/wiki/Form:CSS_Property" title="Form:CSS Property">Form:CSS_Property</a> . Like templates, they often keep much of their implementation hidden in &lt;includeonly&gt; blocks, so you'll have to hit <i>Edit</i> to see how they work.
</p><p>Basically forms are just special templates that define how to build a page for editing. Forms generally have a one-to-one correspondence with templates. Note that many page types we use actually use many templates under the covers so that we can re-use sections of forms (Iike summaries) across many page types.
</p><p>Forms consist of a number of fields. These fields define input boxes and controls that users will fill in. When the user submits, the values for those fields will then be passed directly as parameters to the associated template. In fact, after editing with a form, if you hit the normal Edit button on the page, you can see that basically the output is just a template call with all of the arguments set up in the way the user did it in the form.
</p><p>Note that creating sub-sections of forms that repeat (like the list of related specifications in the CSS Property form) or sections of form that you want to reuse in other forms are advanced topics covered below.
</p><p>You can see more documentation on how to configure forms here: <a class="external free" href="https://www.mediawiki.org/wiki/Extension:Semantic_Forms/Defining_forms">https://www.mediawiki.org/wiki/Extension:Semantic_Forms/Defining_forms</a>
</p>
<h4><span class="mw-headline" id="Properties">Properties</span></h4>
<p>Properties are one of the main features that <i>Semantic</i> MediaWiki provides. Properties allow you to attach structured data to a page that can be queried in interesting places later.
</p><p>Properties are very rarely set by hand; often they are automatically written out inside of a template call based on a parameter passed in.
</p><p>Properties are good for a few use cases:
</p>
<ul><li> If the information is small, structured, and you can imagine wanting to query for it later.</li>
<li> If you want to include that information onto other pages automatically.</li></ul>
<p>A good example of the first use case is whether or not a CSS property is animatable. You could conceivably want to create a page that lists all of the CSS properties are animatable, and to do that you'd need the information in a structured format that you could query on.
</p><p>A good example of the second use case is the Summary property. By defining it as a property, we make it possible to auto-generate pages that are listings of properties and include their summaries.
</p>
<h5><span class="mw-headline" id="Configuration">Configuration</span></h5>
<p>Properties are defined in, you guessed it, the Property namespace: <a href="/wiki/Property:Summary" title="Property:Summary">Property:Summary</a>. Those definition pages include bits of configuration, and also list all of the pages that include that property.
</p><p>Properties have a type. In practice we use strings (limited to 255 characters, but queryable) and text (no length limit, but can't be included as a query parameter, only <i>output</i> as the result of queries).
</p><p>By default properties can take any value. However, you can use the Allows_type configuration property to limit the possible values to only specific types. If you do this, Semantic Forms will automatically create checkboxes for you in your form.
</p><p>More information: <a rel="nofollow" class="external free" href="http://semantic-mediawiki.org/wiki/Help:Properties_and_types">http://semantic-mediawiki.org/wiki/Help:Properties_and_types</a>
</p>
<h5><span class="mw-headline" id="Property_use">Property use</span></h5>
<p>Properties can be applied to a page in handful of ways. The first is via a special link-like syntax: 
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">The property is animatable: [[Animatable::value]]</pre></div></div>
<p>This syntax will apply the property to the page, but also print out the value and link to the property definition.
</p><p>Sometimes you don't want that, either because you don't want the value to be visible, or because the property value is too long to be a link (for example I found that the Summary, which is of type text, wouldn't print correctly in this syntax).
</p><p>For that, you can use this syntax: 
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{#set:Animatable=Yes}}</pre></div></div>
<p><br />
</p>
<div class="note">
<p><b>Note</b>:  As with other built-in "templates" that start with a #, that's a <b>colon</b>, not a pipe after "set" 
</p>
</div>
<p><br />
In practice you'll often see property calls inside of template definitions, and so often the value will be set via a parameter call.
</p>
<h4><span class="mw-headline" id="Queries">Queries</span></h4>
<p>Queries are how you select pages via properties and then print out some of their property-values in some form.
</p><p>We use them quite a bit, for example to automatically generate the listing of methods/properties on the <a href="/wiki/Template:API_Object" title="Template:API Object">API Object template</a> and for listings of pages in <a href="/wiki/Template:API_Listing" title="Template:API Listing">API Listing pages</a>.
</p><p>More info: <a rel="nofollow" class="external free" href="http://semantic-mediawiki.org/wiki/Help:Inline_queries">http://semantic-mediawiki.org/wiki/Help:Inline_queries</a>
</p>
<h2><span class="mw-headline" id="Other_stuff">Other stuff</span></h2>
<h3><span class="mw-headline" id="How_everything_is_wired_together">How everything is wired together</span></h3>
<p>Here's how we use those patterns described above to implement our site so far.
</p><p>We'll walk through the CSS Property template, via the sample page of <a href="/wiki/css/properties/font-size" title="css/properties/font-size">css/properties/font-size</a>.
</p>
<h4><span class="mw-headline" id="The_CSS_Property_page">The CSS Property page</span></h4>
<p>If you go to that page and hit "Edit Source", you'll see that basically it's a number of templates being called: Flags, Summary, CSS_Property and more.  If you were to "Edit" on the page you'd see that the form basically has one-to-one correspondence with those parameters. (This is only obvious for the templates that are configured directly in the form. More on that in a bit).
</p><p>If you scroll down in the source, you'll see the CSS_Property template being called. CSS_Property is just a normal template (we can tell that based on the double-curly brace syntax), so that means we can see its definition at <a href="/wiki/Template:CSS_Property" title="Template:CSS Property">Template:CSS_Property</a>. When we go there, we get a brief overview of what the parameters <i>are</i>, but not how it <i>works</i>. To do that, we'll need to hit "Edit".
</p><p>When we do that, we skip to the &lt;includeonly&gt; section to see the actual implementation. It's pretty simple--mainly we just print a header for each section and then dump whatever was passed in via the parameter.
</p>
<h3><span class="mw-headline" id="Multiple_templates_on_a_form">Multiple templates on a form</span></h3>
<p>There are many common elements on these reference pages that occur either on all of the major page type templates or occur on more than one. An example is the <a href="/wiki/Template:Summary_Section" title="Template:Summary Section">summary section template</a>. For each of these sections, we create a separate template to do the work. We also create a template of the <i>form</i> for that template. Then, in the form for the main page type, we include the sub-form template. This automatically configures the form to deposit the sub-template on the page when it is saved.
</p><p>The summary section is a good example. We have the <a href="/wiki/Template:Summary_Section" title="Template:Summary Section">main template</a> that handles the work of taking in parameters and rendering them out in a standard way, as well as setting certain semantic media wiki properties in the right way. If you "Edit Source" on almost any reference page, you'll see that there's an instantiation of this template on the page. We also have the <a href="/wiki/Template:Summary_Form_Section" title="Template:Summary Form Section">form template</a> which configures how that part of the form will show up and what fields it will have. If you look at the source of any of the major page-type forms, like <a href="/wiki/Form:CSS_Property" title="Form:CSS Property">the css property form</a>, you'll see that there is a call to this Summary_Form_Section template.
</p><p>Most page-type forms use sub-forms and sub-templates as much as possible, and use the "central" template--the one most specific to this page-type--only for properties and form fields that are specific to this page type and this page type only. That "central" template is often the one that deposits the appropriate category on the page to wire it up to the form. The most simple of these page-type forms is the <a href="/wiki/Form:Basic" title="Form:Basic">one for basic pages</a>. There aren't any special parameters to set, so basically that central template <i>just</i> sets the Basic Pages category so that in the future when the user hits the Edit button the right form will show.
</p><p>If you want to figure out how a given page type works, you'll need to dig into the main templates as well as the other templates being used on the page.
</p><p><b>You should see the <a href="/wiki/WPD:Implementation_Patterns/Templates" title="WPD:Implementation Patterns/Templates">templates implementation guide</a> for a better overview of how our main work-horse templates are wired together.</b>
</p>
<h3><span class="mw-headline" id="Common_Patterns">Common Patterns</span></h3>
<p>If you dig into the various templates and sub-patterns, you'll see some interesting patterns. Below we explore a few of them.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">==Summary==
{{{Summary}}}
{{#set:Summary={{{Summary}}} }}</pre></div></div>
<p>In the <a href="/wiki/Template:Summary_Section" title="Template:Summary Section">summary section template</a> we're printing out the value, but after that we're also manually setting the property value. This is because we don't want the normal linkified display of the text when you set a property inline, but we do want to register that property value with the page.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{#if: {{{Usage|}}}|
==Usage==
{{{Usage|}}}
&#160;
|}}</pre></div></div>
<p>In this pattern (from the <a href="/wiki/Template:Notes_Section" title="Template:Notes Section">notes section template</a>) we can see that we use the #if directive to either print out the Usage section if the user provided a value, or skip the entire section if the user didn't provide anything.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{#if: {{{Examples|}}}|
==Examples==
{{{Examples|}}}
&#160;
| {{Editorial | This section should include examples. |type=Needs Examples}} }}</pre></div></div>
<p>This example (from the <a href="/wiki/Template:Examples_Section" title="Template:Examples Section">examples section template</a>) is basically the same, but slightly more complicated. We want to ensure that the examples section is always included in this article type. So if it's not, instead of not printing anything we print an editorial note (basically a TODO) to the screen.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{#if: {{{Specifications|}}} | 
==Related Specifications==
{{{!}} class=&quot;wikitable&quot;
{{!}}-
! Specification&#160;!! Status&#160;!! Related Changes
{{{Specifications|}}}
{{!}}} | }}</pre></div></div>
<p>The rest of these template examples come from the <a href="/wiki/Template:CSS_Property" title="Template:CSS Property">css property template</a>.
</p><p>This is one of the more complicated pieces. It's where we print out the specifications table. A few things to note: 
</p>
<ul><li> {{!}} is a weird hack necessary to print out table syntax inside of #if parser functions (see Tables with Rows, below). Basically that template is just a single pipe character. </li></ul>
<ul><li> This section should be a table. First, we check if we should even show the section. If we should, we print out the header row of the table. The Specifications parameter will consist of all of the rows of the table glommed together--that's just how semantic forms does it. We'll investigate how that's set up in a bit.</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">[[Category:CSS Properties|{{#titleparts:{{PAGENAME}}||-1}}]]</pre></div></div>
<p>This last piece is very important: it's the thing that applies the category to the page. Remember, this is how we specify which form to use. If we investigate the category page: <a rel="nofollow" class="external free" href="http://webplatform.org/docs/Category:CSS_Properties">http://webplatform.org/docs/Category:CSS_Properties</a> we'll see that on that page a default form is defined. Following <i>that</i> to the form definition will help us see how the form is hooked up. (Yes, this all seems like a rube goldberg device).
</p>
<h4><span class="mw-headline" id="The_CSS_Property_form">The CSS Property form</span></h4>
<p>Let's dive into the definition of the accompanying form, which we discovered by going to the category page: <a href="/wiki/Form:CSS_Property" title="Form:CSS Property">Form:CSS_Property</a>.
</p><p>Again, like templates, most of the implementation is hidden in &lt;includeonly&gt; blocks. Click edit to see how it all works.
</p><p>At the beginning there's a bunch of boiler plate that's not important to understand (you can just copy and paste it when you create new forms). Basically what it does is just defines that this form is attached to the CSS Property template. (You'll notice the Flags_form_section template as well as a large number of other ones. That's an interesting pattern to re-use pieces of forms. See the "Re-usable form components", below).
</p><p>If you scroll down to the section that deals with the CSS Property template, you'll see the meat of this form. Most of this page is just normal wiki syntax. The important bits look like:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{{field|Inherited}}}</pre></div></div>
<p>This is how you register form inputs and define which parameters of the associated template they should dump their results to.  Normally all you need is something simple like this, because the Inherited form field should just dump directly into the Inherited parameter of the CSS Property template.
</p><p>There are all kinds of configuration things you can do here, like defining what values are allowed, different input types, etc. See <a class="external free" href="https://www.mediawiki.org/wiki/Extension:Semantic_Forms/Defining_forms">https://www.mediawiki.org/wiki/Extension:Semantic_Forms/Defining_forms</a> for more.
</p><p>Here's an example of changing the input type (from the <a href="/wiki/Template:Examples_Form_Section" title="Template:Examples Form Section">examples form section template</a>):
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">==Examples==
{{{field|Examples|input type=textarea|rows=10}}}</pre></div></div>
<p>This overrides the default textinput to use a text area.
</p><p>But wait--the summary block in <a href="/wiki/Template:Summary_Form_Section" title="Template:Summary Form Section">Template:Summary_Form_Section</a> gets a text area, too--but we didn't override it. How does that work?  Semantic Forms is kind of smart: it can figure out what kind of form input to display based on how the Property is configured. Recall that Summary is configured as a property because we need to be able to extract that information from a page and display it elsewhere. In fact, if you go to <a href="/wiki/Property:Summary" title="Property:Summary">Property:Summary</a> you can see we've defined it as type text, which is why Semantic Forms automatically shows it as a textarea. Semantic Forms figures all of this out because you've linked the template to the category to the form (to be honest, I'm not sure <i>exactly</i> how it does it).
</p><p>But Examples is <i>not</i> a property (at least not at this moment). That's because we don't have any need to extract examples and display them elsewhere, so we just print examples out normally. This means there's no property associated with Examples, so Semantic Forms can't configure the form input automatically, and we have to do it ourselves.
</p><p>Later, in <a href="/wiki/Template:Compatibility_Form_Section" title="Template:Compatibility Form Section">the compatibility form section template</a> we see things like: 
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{{field|Compatibility_desktop_rows|holds template}}}
{{{field|Compatibility_mobile_rows|holds template}}}
{{{field|Compatibility_notes_rows|holds template}}}</pre></div></div>
<p>These are the sections that allow users to add between 0 and n rows. We'll dig into those in the sub-forms section.
</p>
<h3><span class="mw-headline" id="Design_Patterns">Design Patterns</span></h3>
<h4><span class="mw-headline" id="New_pages">New pages</span></h4>
<p>Above we talked about the fact that the "Edit" button knows which form to use because the page includes a category which has a default form defined.
</p><p>But wait--what about the very first time you edit a page? How does SMW know which form to use?
</p><p>It doesn't.
</p><p>It's weird, I know.
</p><p>Basically, until you plop a (perhaps empty) template call on the page that prints out the category, SMW doesn't know what page type it is.
</p><p>There are two ways to mitigate this. The first is that the Form: pages include a helpful input at the top to create a new page using that form.
</p><p>The second is that we have a helpful page, <a href="/wiki/WPD:New_Page" title="WPD:New Page">WPD:New_Page</a> that lists all the common page-type forms you might want to use in one place.
</p>
<h4><span class="mw-headline" id="Building_new_page_types">Building new page types</span></h4>
<p>Building a new page type is <i>very</i> rare. Please ask others who know about our template infrastructure before you create a new one.
</p><p>When you go to build a new page type, you generally are going to need four pieces:
</p>
<ul><li> The main template, which will print out all the values and also print out the category.</li>
<li> The category that we'll use to associated with the form.</li>
<li> The form itself.</li>
<li> An example page to use the form and debug with.</li></ul>
<p>In practice, what you'll do is have four tabs open and be edit/save/refreshing all of them piece by piece to build out your form.
</p><p>When you create your form, it's important to follow the best practices of including all of the sub-forms that are applicable (see below)
</p>
<h4><span class="mw-headline" id="Only_including_some_sections_if_there.27s_content_to_show">Only including some sections if there's content to show</span></h4>
<p>This is a pattern to use in the definition of a template. This pattern is done like this:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{#if: {{{Specifications|}}} | 
==Related Specifications==
{{{!}} class=&quot;wikitable&quot;
{{!}}-
! Specification&#160;!! Status&#160;!! Related Changes
{{{Specifications|}}}
{{!}}} | }}</pre></div></div>
<p>This is a complicated example because it has a conditional table (the specifications parameter will be filled with rows of data glommed together).  See the deep dive above for more discussion of this pattern.
</p>
<h4><span class="mw-headline" id="Re-usable_form_components">Re-usable form components</span></h4>
<p>There are many pieces of forms that we'll want to re-use in other forms. Examples include the Flags section, the Attribution section, and many, many other.
</p><p>The pattern to do this is kind of weird: we just create a simple template to contain the bit of form we want to reuse.
</p><p>In the main form we include it with:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{Flags form section}}
//Normal template begins below
{{{for template|CSS Property}}}
...</pre></div></div>
<p>just like any other template.
</p><p>The contents look like this:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"><span class="sc2">&lt;nowiki&gt;</span>{{{for template|Flags}}}<span class="sc2">&lt;<span class="sy0">/</span>nowiki&gt;</span>
'''Please enter below any issues that apply to this page.'''
{| class=&quot;formtable&quot; style=&quot;border: 1px solid black; background: #fe9; font-size: smaller;&quot;
! High-level issues:
| <span class="sc2">&lt;nowiki&gt;</span>{{{field|High-level issues|property=High-level issue|list}}}<span class="sc2">&lt;<span class="sy0">/</span>nowiki&gt;</span>
|-
! Content:
| <span class="sc2">&lt;nowiki&gt;</span>{{{field|Content|property=Content quality flag|list}}}<span class="sc2">&lt;<span class="sy0">/</span>nowiki&gt;</span>
|-
! Compatibility:
| <span class="sc2">&lt;nowiki&gt;</span>{{{field|Compatibility|property=Compatibility quality flag|list}}}<span class="sc2">&lt;<span class="sy0">/</span>nowiki&gt;</span>
|-
! Examples:
| <span class="sc2">&lt;nowiki&gt;</span>{{{field|Examples|property=Examples quality flag|list}}}<span class="sc2">&lt;<span class="sy0">/</span>nowiki&gt;</span>
|-
! Accessibility:
| <span class="sc2">&lt;nowiki&gt;</span>{{{field|Accessibility|property=Accessibility flag|list}}}<span class="sc2">&lt;<span class="sy0">/</span>nowiki&gt;</span>
|}
<span class="sc2">&lt;nowiki&gt;</span>{{{end template}}}<span class="sc2">&lt;<span class="sy0">/</span>nowiki&gt;</span></pre></div></div>
<p>Basically, it's just the sub-piece of the form we need.
</p><p><br />
</p>
<div class="note">
<p><b>Note</b>:  The factored-out form segment needs to have all field/for template syntax wrapped in nowiki 
</p>
</div>
<p><br />
We use this pattern <b>a lot</b>. 
</p>
<h5><span class="mw-headline" id="Sub-forms_within_the_main_template_and_outside">Sub-forms within the main template and outside</span></h5>
<p>There are two times you might need this pattern: for things whose parameters should be passed to <i>another</i> template, like Flags (which prints its contents out <i>outside</i> of the main template, like CSS Property), or for things that should be included in the <i>same</i> template.
</p><p>The example above is for the former case. That's why the form template instantiation goes <i>outside</i> the main {{{for|template-name}}} block, and the template itself has the weird {{{for template|flags}}}, wrapped in nowiki tags.
</p><p>However, if you're doing the latter, it's easier. The form template doesn't need that special for block above and below the template, and you should instantiate your template <i>inside</i> the main {{for template}} block.
</p>
<h4><span class="mw-headline" id="Sub-forms">Sub-forms</span></h4>
<p>In the <a href="/wiki/Template:Compatibility_Section" title="Template:Compatibility Section">Template:Compatibility_Section</a> sub-form, we have a few sections that allow you to add 0 or more sub-sections. Examples are the browser compatibility rows and the related specifications.
</p><p>These basically use sub-forms and sub-templates to allow this to happen. Here's how the related specifications section works:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{{field|Specifications|holds template}}}</pre></div></div>
<p>This part is included in the main form where we want the sub-form to show up. It says that we should look elsewhere for where this form section is defined.
</p><p>Below, outside of the {{{end template}}} call, we see:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1"><span class="sc-1">&lt;!-- Begin template for Related specfications --&gt;</span>
{{{for template|Related Specification|multiple|label=Related Specifications|embed in field=CSS Property[Specifications]}}}
{| class=&quot;formtable&quot;
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
<span class="sc-1">&lt;!-- End template for Related Specifications --&gt;</span></pre></div></div>
<p>Basically, we're defining another form template in the same page that we'll use in the main form.
</p><p>Notice that the beginning of the block says it's for a template called Related Specifications. Indeed, if you go to <a href="/w/index.php?title=Template:Related_Specifications&amp;action=edit&amp;redlink=1" class="new" title="Template:Related Specifications (page does not exist)">Template:Related_Specifications</a>, you'll see that we've defined a simple template that takes in four parameter and then outputs a table row.
</p><p>Inside of the form definition we just define a simple form just like normal, that allows users to specify the four inputs to fill into that sub-template.
</p><p>When the user hits submit on the main form, the form will automatically go through and stamp out an instance of the sub-template (with correct arguments) for each sub-form section the user created. It will then concatenate them together and pass them into the top-level template with the name we defined in the main body of the form, in this case "Specifications."
</p><p>That's it!
</p>
<h4><span class="mw-headline" id="Tables_with_rows">Tables with rows</span></h4>
<p>In some cases we want form users to define multiple rows of a table, like in Related Specifications.
</p><p>We do this by defining a Sub-form (see the section immediately above).  The result of that sub-form is a concatenation of all of sub-templates filled in with their values.
</p><p>In the case of <a href="/w/index.php?title=Template:Related_Specifications&amp;action=edit&amp;redlink=1" class="new" title="Template:Related Specifications (page does not exist)">Template:Related_Specifications</a> you can see that the template just outputs a single row in MediaWiki table syntax. In the main <a href="/wiki/Template:CSS_Property" title="Template:CSS Property">Template:CSS_Property</a> template, we output a header row and then just dump all of the contents of the Specifications parameter (which, again, is just a concatenation of those table rows from the Related Specifications template) right there.
</p><p>One thing to be aware of when you're building up tables like this is that we need to be aware of the Table Gotcha (see next section) if we're using #if blocks.
</p><p>See <a class="external free" href="https://www.mediawiki.org/wiki/Help:Tables">https://www.mediawiki.org/wiki/Help:Tables</a> for more information.
</p>
<h4><span class="mw-headline" id="Gotcha:_Table_syntax">Gotcha: Table syntax</span></h4>
<p>We use tables a lot. Some parts of the page should have tables if there's rows of content to show, and no table if not. There's a weird gotcha to be aware of.
</p><p>Here's the normal #if syntax:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{#if: condition | value | else-value}}</pre></div></div>
<p>Here's normal syntax for a table: 
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{| class=&quot;wikitable&quot;
! Header-value 1&#160;!! Header-value-2
|-
| Row-value 1 || Row-value-2
|}</pre></div></div>
<p>The problem is that in the #if block, every pipe character it encounters will be interpreted literally. So if you try to include pipe characters for the table syntax as part of the value or else-value, it just won't work.
</p><p>This is weird. The solution is even weirder.
</p><p>Basically, the hack is that we have a special template defined: <a href="/wiki/Template:!" title="Template:!">Template:!</a>. This template does precisely one thing: it prints out a pipe character. This hack gets around the weird limitation of #if blocks and allows you to conditionally include parts of tables. Here's an example where we use the hack:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{{#if: {{{Specifications|}}} | 
==Related Specifications==
{{{!}} class=&quot;wikitable&quot;
{{!}}-
! Specification&#160;!! Status&#160;!! Related Changes
{{{Specifications|}}}
{{!}}} | }}</pre></div></div>
<p>More information on this pattern (no, I did not come up with this crazy solution), see <a rel="nofollow" class="external text" href="http://meta.wikimedia.org/wiki/Help:Table#Producing_table_syntax_using_templates_and.2For_parser_functions">Parser functions</a>.
</p><p>For general information about the problems with pipe characters, see <a href="/wiki/WPD:Manual_Of_Style/Gotchas#The_dreaded_pipe_character" title="WPD:Manual Of Style/Gotchas" class="mw-redirect">The dreaded pipe character</a>.
</p>
<h4><span class="mw-headline" id="Gotcha:Spaces_in_template_calls">Gotcha:Spaces in template calls</span></h4>
<p>MediaWiki is very weird about spaces. In particular, a line that starts with a single space is automatically formatted as a &lt;pre&gt; block. This can bite you in template calls where you might have added spaces for readability. Most of the times they get trimmed off, but sometimes they don't. In general <b>do not use spaces</b> around parameter values. Most of the times everything will work fine, but other times it will break without warning. See the <a href="/wiki/Template:External_Attribution_Block" title="Template:External Attribution Block">External Attribution Block template</a> for an example.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Document the partial-pre hack
</p>
</div>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Document the slightly-different-template-name-to-avoid-hoisting hack
</p>
</div>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Document the summary-table pattern: <a rel="nofollow" class="external free" href="http://smw.referata.com/wiki/Use_the_ask_template_format_to_create_tabular_output">http://smw.referata.com/wiki/Use_the_ask_template_format_to_create_tabular_output</a>
</p>
</div>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  When you move a page that has properties, you must "touch" the new one to get the properties set correctly.
</p>
</div>

<!-- 
NewPP limit report
CPU time usage: 0.248 seconds
Real time usage: 0.287 seconds
Preprocessor visited node count: 541/1000000
Preprocessor generated node count: 1139/1000000
Post‐expand include size: 2320/2097152 bytes
Template argument size: 1328/2097152 bytes
Highest expansion depth: 3/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%  139.534      1 - -total
  6.24%    8.701      6 - Template:Note
  3.60%    5.030      5 - Template:TODO
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:239-0!*!0!!*!*!*!esi=1 and timestamp 20150731173701 and revision id 30424
 -->
