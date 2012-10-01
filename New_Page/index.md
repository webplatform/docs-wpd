This page is the way that you create new '''content''' pages. (Content pages are pages that live in the default namespace.) If your page is not a content page (for example, it lives in the <code>WPD:</code> namespace), just visit the URL you would like to exist and hit the 'Create' tab.

To create a new page:
# Figure out where the page should live. Consult the [[WPD:Architecture | architecture]] page for an overview of the URL structure of the site.
# Identify the most specific form below that fits the type of content you'd like to create. The forms are listed in decreasing order of specificity.
# In the associated input box, type the full name of the page you'd like to create (including slashes if you're creating a sub-page) and hit the "Create foo" button, where "foo" is the name of the form you want to use.

{{Note| This page lists all page templates that currently exist. As we create more, we'll add them here.}}


==API Listing==
For pages that primarily list APIs, like css/properties.
{{#forminput:form=API_Listing|default value=foo|button text=Create API Listing Page}}

==API Object==
If you're documenting an API, like <code>document</code>. Generally all pages in this type have a URL that contains <code>apis</code>, and has method and property pages that are sub-pages.
{{#forminput:form=API_Object|default value=apis/foo|button text=Create API Object Page}}

==API Object Method==
If you're documenting a ''method'' of an API, like <code>appendChild</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object.
{{#forminput:form=API_Object_Method|default value=apis/foo/bar|button text=Create API Object Method Page}}

==API Object Property==
If you're documenting a ''property'' of an API, like <code>childNodes</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object.
{{#forminput:form=API_Object_Property|default value=apis/foo/baz|button text=Create API Object Property Page}}

==Concept==
For pages that are overviews of a basic concept, like CSS inheritance or float-based layout.
{{TODO | Examples of topics and URLS}}
{{#forminput:form=Concept_Page|default value=concepts/foo|button text=Create Concept Page}}

==Constant==
For pages that document a constant (for CSS, JavaScript, etc).
{{TODO | Examples of topics and URLS}}
{{#forminput:form=Constant|default value=foo|button text=Create Constant Page}}

==CSS At Rule==
For pages that document a CSS At Rule (like @keyframes).
{{TODO | Examples of topics and URLS}}
{{#forminput:form=CSS At Rule|default value=foo|button text=Create CSS At Rule Page}}

==CSS Function==
For pages that document a CSS function (like calc).
{{TODO | Examples of topics and URLS}}
{{#forminput:form=CSS Function|default value=foo|button text=Create CSS Function Page}}

==CSS Keyword==
For pages that document a CSS keyword (like <code>inherit</code>).
{{TODO | Examples of topics and URLS}}
{{#forminput:form=CSS Keyword|default value=foo|button text=Create CSS Keyword Page}}

==CSS Media Feature==
For pages that document a CSS media feature.
{{TODO | Examples of topics and URLS}}
{{#forminput:form=CSS Media Feature|default value=foo|button text=Create CSS Media Feature Page}}

==CSS Property==
For pages that document a CSS property, like <code>font-size</code>. Generally, all pages that have a URL that begins with <code>/css/properties/</code> should live here.
{{#forminput:form=CSS_Property|default value=css/properties/foo|button text=Create CSS Property Page}}

==CSS Selector==
For pages that document a CSS selector (like the descendant selector). The URL should be a descriptive name since most of the selectors are illegal characters for MediaWiki URLs.
{{TODO | Examples of topics and URLS}}
{{#forminput:form=CSS Selector|default value=foo|button text=Create CSS Selector Page}}

==Data Type==
For pages that document a data type (for CSS, JavaScript, etc).
{{TODO | Examples of topics and URLS}}
{{#forminput:form=Data_Type_Page|default value=foo|button text=Create Data Type Page}}

==Event==
For pages that document a DOM event, like <code>click</code>
{{TODO | Examples of topics and URLS}}
{{#forminput:form=Event|default value=foo|button text=Create Event Page}}

==Guide==
For pages that are guides to a given complex topic.
{{TODO | Examples of topics and URLS}}
{{#forminput:form=Guide|default value=foo|button text=Create Guide Page}}

==Glossary==
For pages that act as a collection of Glossary Items.
{{TODO | Examples of topics and URLS}}
{{#forminput:form=Glossary|default value=foo|button text=Create Glossary Page}}

==Glossary Item==
For pages that define a single term and its definition.
{{TODO | Examples of topics and URLS}}
{{#forminput:form=Glossary Item|default value=foo|button text=Create Glossary Item Page}}

==JavaScript Operator==
For pages that document a JavaScript operator, for example <code>+</code> or <code>.</code>. These normally live at URLs that begin with <code>js/operators/</code>. Note that you must use a readable long-form name as many of the actual values are illegal in URLs.
{{#forminput:form=JavaScript_Operator|default value=js/operators/foo|button text=Create JavaScript Operator Page}}

==JavaScript Statement==
For pages that document a JavaScript statement, for example <code>for</code>, or <code>var</code>. Normally their URLs begin with <code>js/statements/</code>
{{#forminput:form=JavaScript_Statement|default value=js/statements/foo|button text=Create JavaScript Statement Page}}

==Markup Attribute==
For pages that document a Markup attribute (of HTML, SVG, MathML or XML), for example <code>class</code> or <code>href</code>. These normally live at URLs with a prefix of <code>{xml,html,mathml,svg}/attributes/</code>.
{{#forminput:form=Markup_Attribute|default value=html/attributes/foo|button text=Create Markup Attribute Page}}

==Markup Element==
For pages that document a Markup Element (of HTML, SVG, MathML, or XML). For example, <code>canvas</code>, <code>div</code>, <code>circle</code>. These articles normally live at URLs with a prefix of <code>{xml,svg,html,mathml}/elements/</code>
{{#forminput:form=Markup_Element|default value=html/elements/foo|button text=Create Markup Element Page}}

==Markup Structure==
For pages that document a Markup structure (of HTML, SVG, or other types). For example, <code>CDATA</code>.
{{TODO | Where ''do'' these live in the URL structure?}}
{{#forminput:form=Markup_Structure|default value=foo|button text=Create Markup Structure Page}}

==Regex Metacharacter==
For pages that document a regex metacharacter, like <code>*</code> or <code>.</code>. Make sure to use a descriptive name, not the literal character (as those are often illegal page names).
{{TODO | Examples of topics and URLS}}
{{#forminput:form=Regex_Metacharacter|default value=foo|button text=Create Regex Metacharacter Page}}

==Tutorial==
For pages that cover a tutorial that walks users through a practical sequence of steps. Generally, these pages live at URLs that begin with <code>/tutorials</code>, although there may be redirects to them from other URLs in other sections.
{{#forminput:form=Tutorial|default value=tutorials/foo|button text=Create Tutorial Page}}

==Other/Basic==
For content pages (that is, pages in the default namespace) that do not have a more specific form to use.
{{#forminput:form=Basic|button text=Create Basic Page}}

{{TODO | Create a Media Content page type}}
{{TODO | Create a Protocol page type}}