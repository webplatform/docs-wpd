---
title: 'WPD:New Page'
uri: 'WPD:New Page'

---
Follow the steps below as you create new **content** pages. (Content pages are pages that live in the default namespace.) If your page is not a content page (for example, it lives in the `WPD:` namespace), just visit the URL you would like to exist and hit the 'Create' tab.

To create a new page:

1.  Figure out where the page should live. Consult the [Topic hierarchy](/WPD:Content/Topic_Hierarchy) page for an overview of the URL structure of the site.
2.  Identify the most specific form below that fits the type of content you'd like to create.
3.  In the associated input box, type the full name of the page you'd like to create (including slashes if you're creating a sub-page) and hit the "Create foo" button, where "foo" is the name of the form you want to use. For file naming guidelines, consult the [Style guide](/WPD:Manual_Of_Style).

**Note**: This page lists all page templates that currently exist. As we create more, we'll add them here.

## API Listing

For pages that primarily list APIs, like apis/webrtc. See [WPD:Creating\_API\_pages](/WPD:Creating_API_pages).

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="apis/foo" name="page_name"></input><input type="hidden" value="API_Listing" name="form"></input><input type="submit" value="Create API Listing Page" id="input_button_1" class="forminput_button"></input>

</form>

## API Object

If you're documenting an API, like `document`. Generally all pages in this type have a URL that contains `apis`, and has method and property pages that are sub-pages. The **Bar** API object of the **foo** API list would have the URL shown below. See [WPD:Creating\_API\_pages](/WPD:Creating_API_pages).

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="apis/foo/Bar" name="page_name"></input><input type="hidden" value="API_Object" name="form"></input><input type="submit" value="Create API Object Page" id="input_button_1" class="forminput_button"></input>

</form>

## API Object Method

If you're documenting a *method* of an API, like `appendChild`. Generally all pages in this type have a URL that contains `apis` and also includes the parent API Object. The **fuz** method of the **Bar** API object in the **foo** API list would have the URL shown below. See [WPD:Creating\_API\_pages](/WPD:Creating_API_pages).

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="apis/foo/Bar/fuz" name="page_name"></input><input type="hidden" value="API_Object_Method" name="form"></input><input type="submit" value="Create API Object Method Page" id="input_button_1" class="forminput_button"></input>

</form>

## API Object Property

If you're documenting a *property* of an API, like `childNodes`. Generally all pages in this type have a URL that contains `apis` and also includes the parent API Object. The **baz** property of the **Bar** API object in the **foo** API list would have the URL shown below. See [WPD:Creating\_API\_pages](/WPD:Creating_API_pages).

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="apis/foo/Bar/baz" name="page_name"></input><input type="hidden" value="API_Object_Property" name="form"></input><input type="submit" value="Create API Object Property Page" id="input_button_1" class="forminput_button"></input>

</form>

## API Object Event

Use the [Event](#Event) form, below. The **buz** event of the **Bar** API object in the **foo** API list would have the URL, **apis/foo/Bar/buz**. See [WPD:Creating\_API\_pages](/WPD:Creating_API_pages).

## Concept

For pages that are overviews of a basic concept, like CSS inheritance or float-based layout.

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="concepts/foo" name="page_name"></input><input type="hidden" value="Concept_Page" name="form"></input><input type="submit" value="Create Concept Page" id="input_button_1" class="forminput_button"></input>

</form>

## Constant

For pages that document a constant (for CSS, JavaScript, etc).

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="foo" name="page_name"></input><input type="hidden" value="Constant" name="form"></input><input type="submit" value="Create Constant Page" id="input_button_1" class="forminput_button"></input>

</form>

## CSS At Rule

For pages that document a CSS At Rule (like @keyframes).

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="foo" name="page_name"></input><input type="hidden" value="CSS At Rule" name="form"></input><input type="submit" value="Create CSS At Rule Page" id="input_button_1" class="forminput_button"></input>

</form>

## CSS Function

For pages that document a CSS function (like calc()).

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="css/functions/foo" name="page_name"></input><input type="hidden" value="CSS Function" name="form"></input><input type="submit" value="Create CSS Function Page" id="input_button_1" class="forminput_button"></input>

</form>

## CSS Keyword

For pages that document a CSS keyword (like `inherit`).

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="foo" name="page_name"></input><input type="hidden" value="CSS Keyword" name="form"></input><input type="submit" value="Create CSS Keyword Page" id="input_button_1" class="forminput_button"></input>

</form>

## CSS Media Feature

For pages that document a CSS media feature.

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="foo" name="page_name"></input><input type="hidden" value="CSS Media Feature" name="form"></input><input type="submit" value="Create CSS Media Feature Page" id="input_button_1" class="forminput_button"></input>

</form>

## CSS Property

For pages that document a CSS property, like `font-size`. Generally, all pages that have a URL that begins with `/css/properties/` should live here.

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="css/properties/foo" name="page_name"></input><input type="hidden" value="CSS_Property" name="form"></input><input type="submit" value="Create CSS Property Page" id="input_button_1" class="forminput_button"></input>

</form>

## CSS Selector

For pages that document a CSS selector (like the descendant selector). The URL should be a descriptive name since most of the selectors are illegal characters for MediaWiki URLs.

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="foo" name="page_name"></input><input type="hidden" value="CSS Selector" name="form"></input><input type="submit" value="Create CSS Selector Page" id="input_button_1" class="forminput_button"></input>

</form>

## Data Type

For pages that document a data type (for CSS, JavaScript, etc).

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="foo" name="page_name"></input><input type="hidden" value="Data_Type_Page" name="form"></input><input type="submit" value="Create Data Type Page" id="input_button_1" class="forminput_button"></input>

</form>

## Event

For pages that document a DOM event, like `click` (dom/events/click) or an API object event like `ended` (apis/webrtc/MediaStream/ended). For information about documenting API object events, see [WPD:Creating\_API\_pages](/WPD:Creating_API_pages).

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="faz" name="page_name"></input><input type="hidden" value="Event" name="form"></input><input type="submit" value="Create Event Page" id="input_button_1" class="forminput_button"></input>

</form>

## Guide

For pages that are guides to a given complex topic.

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="foo" name="page_name"></input><input type="hidden" value="Guide" name="form"></input><input type="submit" value="Create Guide Page" id="input_button_1" class="forminput_button"></input>

</form>

## Glossary

For pages that act as a collection of Glossary Items.

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="foo" name="page_name"></input><input type="hidden" value="Glossary" name="form"></input><input type="submit" value="Create Glossary Page" id="input_button_1" class="forminput_button"></input>

</form>

## Glossary Item

For pages that define a single term and its definition.

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="foo" name="page_name"></input><input type="hidden" value="Glossary Item" name="form"></input><input type="submit" value="Create Glossary Item Page" id="input_button_1" class="forminput_button"></input>

</form>

## JavaScript Operator

For pages that document a JavaScript operator, for example `+` or `.`. These normally live at URLs that begin with `js/operators/`. Note that you must use a readable long-form name as many of the actual values are illegal in URLs.

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="js/operators/foo" name="page_name"></input><input type="hidden" value="JavaScript_Operator" name="form"></input><input type="submit" value="Create JavaScript Operator Page" id="input_button_1" class="forminput_button"></input>

</form>

## JavaScript Statement

For pages that document a JavaScript statement, for example `for`, or `var`. Normally their URLs begin with `js/statements/`

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="js/statements/foo" name="page_name"></input><input type="hidden" value="JavaScript_Statement" name="form"></input><input type="submit" value="Create JavaScript Statement Page" id="input_button_1" class="forminput_button"></input>

</form>

## Markup Attribute

For pages that document a Markup attribute (of HTML, SVG, MathML or XML), for example `class` or `href`. These normally live at URLs with a prefix of `{xml,html,mathml,svg}/attributes/`.

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="html/attributes/foo" name="page_name"></input><input type="hidden" value="Markup_Attribute" name="form"></input><input type="submit" value="Create Markup Attribute Page" id="input_button_1" class="forminput_button"></input>

</form>

## Markup Element

For pages that document a Markup Element (of HTML, SVG, MathML, or XML). For example, `canvas`, `div`, `circle`. These articles normally live at URLs with a prefix of `{xml,svg,html,mathml}/elements/`

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="html/elements/foo" name="page_name"></input><input type="hidden" value="Markup_Element" name="form"></input><input type="submit" value="Create Markup Element Page" id="input_button_1" class="forminput_button"></input>

</form>

## Markup Structure

For pages that document a Markup structure (of HTML, SVG, or other types). For example, `CDATA`.

**TODO**: Where *do* these live in the URL structure?

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="foo" name="page_name"></input><input type="hidden" value="Markup_Structure" name="form"></input><input type="submit" value="Create Markup Structure Page" id="input_button_1" class="forminput_button"></input>

</form>

## Regex Metacharacter

For pages that document a regex metacharacter, like `*` or `.`. Make sure to use a descriptive name, not the literal character (as those are often illegal page names).

**TODO**: Examples of topics and URLS

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="foo" name="page_name"></input><input type="hidden" value="Regex_Metacharacter" name="form"></input><input type="submit" value="Create Regex Metacharacter Page" id="input_button_1" class="forminput_button"></input>

</form>

## Tutorial

For pages that cover a tutorial that walks users through a practical sequence of steps. Generally, these pages live at URLs that begin with `/tutorials`, although there may be redirects to them from other URLs in other sections.

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" value="tutorials/foo" name="page_name"></input><input type="hidden" value="Tutorial" name="form"></input><input type="submit" value="Create Tutorial Page" id="input_button_1" class="forminput_button"></input>

</form>

## Other/Basic

For content pages (that is, pages in the default namespace) that do not have a more specific form to use.

<form name="createbox" action="/wiki/Special:FormStart" method="get" class>
<input size="25" placeholder autofocus class="formInput mw-ui-input" name="page_name"></input><input type="hidden" value="Basic" name="form"></input><input type="submit" value="Create Basic Page" id="input_button_1" class="forminput_button"></input>

</form>

**TODO**: Create a Media Content page type

**TODO**: Create a Protocol page type

**TODO**: Create a Javascript Object page type

**TODO**: Create a Javascript Enum page type?

