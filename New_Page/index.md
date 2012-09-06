This page is the way that you create new '''content''' pages. (Content pages are pages that live in the default namespace.) If your page is not a content page (for example, it lives in the <code>WPD:</code> namespace), just visit the URL you would like to exist and hit the 'Create' tab.

To create a new page:
# Figure out where the page should live. Consult the [[WPD:Architecture | architecture]] page for an overview of the URL structure of the site.
# Identify the most specific form below that fits the type of content you'd like to create. The forms are listed in decreasing order of specificity.
# In the associated input box, type the full name of the page you'd like to create (including slashes if you're creating a sub-page) and hit the "Create foo" button, where "foo" is the name of the form you want to use.

{{Note| This page lists all page templates that currently exist. As we create more, we'll add them here.}}

==Markup Element==
For pages that document a Markup Element (of HTML, SVG, or other types).
{{TODO | Examples of topics and URLS}}
{{#forminput:form=Markup_Element|default value=foo|button text=Create Markup Element Page}}

==Markup Structure==
For pages that document a Markup structure (of HTML, SVG, or other types).
{{TODO | Examples of topics and URLS}}
{{#forminput:form=Markup_Structure|default value=foo|button text=Create Markup Structure Page}}

==JavaScript Statement==
For pages that document a JavaScript statement.
{{TODO | Examples of topics and URLS}}
{{#forminput:form=JavaScript_Statement|default value=foo|button text=Create JavaScript Statement Page}}

==JavaScript Operator==
For pages that document a JavaScript operator.
{{TODO | Examples of topics and URLS}}
{{#forminput:form=JavaScript_Operator|default value=foo|button text=Create JavaScript Operator Page}}

==CSS Property==
For pages that document a CSS property, like <code>font-size</code>. Generally, all pages that have a URL that begins with <code>/css/properties/</code> should live here.
{{#forminput:form=CSS_Property|default value=css/properties/foo|button text=Create CSS Property Page}}

==API Object==
If you're documenting an API, like <code>document</code>. Generally all pages in this type have a URL that contains <code>apis</code>, and has method and property pages that are sub-pages.
{{#forminput:form=API_Object|default value=apis/foo|button text=Create API Object Page}}

==API Object Method==
If you're documenting a ''method'' of an API, like <code>appendChild</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object.
{{#forminput:form=API_Object_Method|default value=apis/foo/bar|button text=Create API Object Method Page}}

==API Object Property==
If you're documenting a ''property'' of an API, like <code>childNodes</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object.
{{#forminput:form=API_Object_Property|default value=apis/foo/baz|button text=Create API Object Property Page}}

==Tutorial==
For pages that cover a tutorial that walks users through a practical sequence of steps. Generally, these pages live at URLs that begin with <code>/tutorials</code>, although there may be redirects to them from other URLs in other sections.
{{#forminput:form=Tutorial|default value=tutorials/foo|button text=Create Tutorial Page}}

==Basic==
For content pages (that is, pages in the default namespace) that do not have a more specific form to use.
{{#forminput:form=Basic|button text=Create Basic Page}}