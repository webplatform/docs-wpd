---
title: New Page
---

Follow the steps below as you create new <b>content</b> pages. (Content pages are pages that live in the default namespace.) If your page is not a content page (for example, it lives in the <code>WPD:</code> namespace), just visit the URL you would like to exist and hit the 'Create' tab.

To create a new page:

* Figure out where the page should live. Consult the [Topic hierarchy](/wiki/WPD:Content/Topic_Hierarchy) page for an overview of the URL structure of the site
* Identify the most specific form below that fits the type of content you'd like to create

For file naming guidelines, consult [the Style guide](/WPD/Manual_Of_Style).


## API Listing

For pages that primarily list APIs, like apis/webrtc. See <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a>.

## API Object

If you're documenting an API, like <code>document</code>. Generally all pages in this type have a URL that contains <code>apis</code>, and has method and property pages that are sub-pages. The <b>Bar</b> API object of the <b>foo</b> API list would have the URL shown below. See [WPD/Creating_API_pages](/WPD/Creating_API_pages).


## API Object Method</span></h2>

If you're documenting a <i>method</i> of an API, like <code>appendChild</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object. The <b>fuz</b> method of the <b>Bar</b> API object in the <b>foo</b> API list would have the URL shown below. See [/WPD/Creating_API_pages](/WPD/Creating_API_pages)


## API Object Property

If you're documenting a <i>property</i> of an API, like <code>childNodes</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object. The <b>baz</b> property of the <b>Bar</b> API object in the <b>foo</b> API list would have the URL shown below. See [WPD/Creating_API_pages](/WPD/Creating_API_pages)



## API Object Event

The <b>buz</b> event of the <b>Bar</b> API object in the <b>foo</b> API list would have the URL, <b>apis/foo/Bar/buz</b>. See [WPD/Creating_API_pages](/WPD/Creating_API_pages)



## Concept

For pages that are overviews of a basic concept, like CSS inheritance or float-based layout.



## Constant

For pages that document a constant (for CSS, JavaScript, etc).



## CSS

### CSS At Rule

For pages that document a CSS At Rule (like @keyframes).



## CSS Function

For pages that document a CSS function (like calc()). Use path similar to `css/functions/foo`



### CSS Keyword

For pages that document a CSS keyword (like <code>inherit</code>). Use path similar to `css/foo`.



### CSS Media Feature

For pages that document a CSS media feature.



### CSS Property

For pages that document a CSS property, like <code>font-size</code>. Generally, all pages that have a URL that begins with <code>/css/properties/</code> should live here. Use path similar to `css/properties/foo`


### CSS Selector

For pages that document a CSS selector (like the descendant selector). The URL should be a descriptive name but yet with legal URL characters. In order to let the page have the same name as a property you can have the front matter use a different name.

1. Example, we’ll create the `:target` pseudo class documentation page in path `css/selectors/pseudo-classes/target/index.md`
1. In the front matter (what’s between the two `---`) we’ll add our desired title.


  ```yaml
  # file css/selectors/pseudo-classes/target/index.md
  ---
  title: css/selectors/pseudo-classes/:target
  ---
  ... rest of Mixed Markdown/HTML document
  ```



## Data Type

For pages that document a data type (for CSS, JavaScript, etc).


## Event

For pages that document a DOM event, like <code>click</code> (dom/events/click) or an API object event like <code>ended</code> (apis/webrtc/MediaStream/ended). For information about documenting API object events, see [WPD/Creating_API_pages](/WPD/Creating_API_pages)



## Guide

For pages that are guides to a given complex topic.


## Glossary

For pages that act as a collection of Glossary Items.



### Glossary Item</span></h2>

For pages that define a single term and its definition.


## JavaScript Operator

<p>For pages that document a JavaScript operator, for example <code>+</code> or <code>.</code>. These normally live at URLs that begin with <code>js/operators/</code>. Note that you must use a readable long-form name as many of the actual values are illegal in URLs.
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="js/operators/foo" name="page_name" />
<input type="hidden" value="JavaScript_Operator" name="form" />			<input type="submit" value="Create JavaScript Operator Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="JavaScript_Statement">JavaScript Statement</span></h2>
<p>For pages that document a JavaScript statement, for example <code>for</code>, or <code>var</code>. Normally their URLs begin with <code>js/statements/</code>
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="js/statements/foo" name="page_name" />
<input type="hidden" value="JavaScript_Statement" name="form" />			<input type="submit" value="Create JavaScript Statement Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Markup_Attribute">Markup Attribute</span></h2>
<p>For pages that document a Markup attribute (of HTML, SVG, MathML or XML), for example <code>class</code> or <code>href</code>. These normally live at URLs with a prefix of <code>{xml,html,mathml,svg}/attributes/</code>.
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="html/attributes/foo" name="page_name" />
<input type="hidden" value="Markup_Attribute" name="form" />			<input type="submit" value="Create Markup Attribute Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Markup_Element">Markup Element</span></h2>
<p>For pages that document a Markup Element (of HTML, SVG, MathML, or XML). For example, <code>canvas</code>, <code>div</code>, <code>circle</code>. These articles normally live at URLs with a prefix of <code>{xml,svg,html,mathml}/elements/</code>
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="html/elements/foo" name="page_name" />
<input type="hidden" value="Markup_Element" name="form" />			<input type="submit" value="Create Markup Element Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Markup_Structure">Markup Structure</span></h2>
<p>For pages that document a Markup structure (of HTML, SVG, or other types). For example, <code>CDATA</code>.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Where <i>do</i> these live in the URL structure?
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="foo" name="page_name" />
<input type="hidden" value="Markup_Structure" name="form" />			<input type="submit" value="Create Markup Structure Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Regex_Metacharacter">Regex Metacharacter</span></h2>
<p>For pages that document a regex metacharacter, like <code>*</code> or <code>.</code>. Make sure to use a descriptive name, not the literal character (as those are often illegal page names).
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="foo" name="page_name" />
<input type="hidden" value="Regex_Metacharacter" name="form" />			<input type="submit" value="Create Regex Metacharacter Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Tutorial">Tutorial</span></h2>
<p>For pages that cover a tutorial that walks users through a practical sequence of steps. Generally, these pages live at URLs that begin with <code>/tutorials</code>, although there may be redirects to them from other URLs in other sections.
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="tutorials/foo" name="page_name" />
<input type="hidden" value="Tutorial" name="form" />			<input type="submit" value="Create Tutorial Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Other.2FBasic">Other/Basic</span></h2>
<p>For content pages (that is, pages in the default namespace) that do not have a more specific form to use.
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" name="page_name" />
<input type="hidden" value="Basic" name="form" />			<input type="submit" value="Create Basic Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p>

