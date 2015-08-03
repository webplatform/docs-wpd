---
title: WPD:New Page
---
<p>Follow the steps below as you create new <b>content</b> pages. (Content pages are pages that live in the default namespace.) If your page is not a content page (for example, it lives in the <code>WPD:</code> namespace), just visit the URL you would like to exist and hit the 'Create' tab.
</p><p>To create a new page:
</p>
<ol><li> Figure out where the page should live. Consult the <a href="/wiki/WPD:Content/Topic_Hierarchy" title="WPD:Content/Topic Hierarchy" class="mw-redirect"> Topic hierarchy</a> page for an overview of the URL structure of the site.</li>
<li> Identify the most specific form below that fits the type of content you'd like to create.</li>
<li> In the associated input box, type the full name of the page you'd like to create (including slashes if you're creating a sub-page) and hit the "Create foo" button, where "foo" is the name of the form you want to use. For file naming guidelines, consult the <a href="/wiki/WPD:Manual_Of_Style" title="WPD:Manual Of Style" class="mw-redirect"> Style guide</a>.</li></ol>
<p><br />
</p>
<div class="note">
<p><b>Note</b>:  This page lists all page templates that currently exist. As we create more, we'll add them here.
</p>
</div>
<p><br />
</p>
<h2><span class="mw-headline" id="API_Listing">API Listing</span></h2>
<p>For pages that primarily list APIs, like apis/webrtc. See <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a>.
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="apis/foo" name="page_name" />
<input type="hidden" value="API_Listing" name="form" />			<input type="submit" value="Create API Listing Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="API_Object">API Object</span></h2>
<p>If you're documenting an API, like <code>document</code>. Generally all pages in this type have a URL that contains <code>apis</code>, and has method and property pages that are sub-pages. The <b>Bar</b> API object of the <b>foo</b> API list would have the URL shown below. See <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a>.
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="apis/foo/Bar" name="page_name" />
<input type="hidden" value="API_Object" name="form" />			<input type="submit" value="Create API Object Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="API_Object_Method">API Object Method</span></h2>
<p>If you're documenting a <i>method</i> of an API, like <code>appendChild</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object. The <b>fuz</b> method of the <b>Bar</b> API object in the <b>foo</b> API list would have the URL shown below. See <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a>.
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="apis/foo/Bar/fuz" name="page_name" />
<input type="hidden" value="API_Object_Method" name="form" />			<input type="submit" value="Create API Object Method Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="API_Object_Property">API Object Property</span></h2>
<p>If you're documenting a <i>property</i> of an API, like <code>childNodes</code>. Generally all pages in this type have a URL that contains <code>apis</code> and also includes the parent API Object. The <b>baz</b> property of the <b>Bar</b> API object in the <b>foo</b> API list would have the URL shown below. See <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a>.
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="apis/foo/Bar/baz" name="page_name" />
<input type="hidden" value="API_Object_Property" name="form" />			<input type="submit" value="Create API Object Property Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="API_Object_Event">API Object Event</span></h2>
<p>Use the <a href="#Event">Event</a> form, below. The <b>buz</b> event of the <b>Bar</b> API object in the <b>foo</b> API list would have the URL, <b>apis/foo/Bar/buz</b>. See <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a>.
</p>
<h2><span class="mw-headline" id="Concept">Concept</span></h2>
<p>For pages that are overviews of a basic concept, like CSS inheritance or float-based layout.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="concepts/foo" name="page_name" />
<input type="hidden" value="Concept_Page" name="form" />			<input type="submit" value="Create Concept Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Constant">Constant</span></h2>
<p>For pages that document a constant (for CSS, JavaScript, etc).
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="foo" name="page_name" />
<input type="hidden" value="Constant" name="form" />			<input type="submit" value="Create Constant Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="CSS_At_Rule">CSS At Rule</span></h2>
<p>For pages that document a CSS At Rule (like @keyframes).
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="foo" name="page_name" />
<input type="hidden" value="CSS At Rule" name="form" />			<input type="submit" value="Create CSS At Rule Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="CSS_Function">CSS Function</span></h2>
<p>For pages that document a CSS function (like calc()).
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="css/functions/foo" name="page_name" />
<input type="hidden" value="CSS Function" name="form" />			<input type="submit" value="Create CSS Function Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="CSS_Keyword">CSS Keyword</span></h2>
<p>For pages that document a CSS keyword (like <code>inherit</code>).
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="foo" name="page_name" />
<input type="hidden" value="CSS Keyword" name="form" />			<input type="submit" value="Create CSS Keyword Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="CSS_Media_Feature">CSS Media Feature</span></h2>
<p>For pages that document a CSS media feature.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="foo" name="page_name" />
<input type="hidden" value="CSS Media Feature" name="form" />			<input type="submit" value="Create CSS Media Feature Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="CSS_Property">CSS Property</span></h2>
<p>For pages that document a CSS property, like <code>font-size</code>. Generally, all pages that have a URL that begins with <code>/css/properties/</code> should live here.
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="css/properties/foo" name="page_name" />
<input type="hidden" value="CSS_Property" name="form" />			<input type="submit" value="Create CSS Property Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="CSS_Selector">CSS Selector</span></h2>
<p>For pages that document a CSS selector (like the descendant selector). The URL should be a descriptive name since most of the selectors are illegal characters for MediaWiki URLs.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="foo" name="page_name" />
<input type="hidden" value="CSS Selector" name="form" />			<input type="submit" value="Create CSS Selector Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Data_Type">Data Type</span></h2>
<p>For pages that document a data type (for CSS, JavaScript, etc).
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="foo" name="page_name" />
<input type="hidden" value="Data_Type_Page" name="form" />			<input type="submit" value="Create Data Type Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Event">Event</span></h2>
<p>For pages that document a DOM event, like <code>click</code> (dom/events/click) or an API object event like <code>ended</code> (apis/webrtc/MediaStream/ended). For information about documenting API object events, see <a href="/wiki/WPD:Creating_API_pages" title="WPD:Creating API pages">WPD:Creating_API_pages</a>.
			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="faz" name="page_name" />
<input type="hidden" value="Event" name="form" />			<input type="submit" value="Create Event Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Guide">Guide</span></h2>
<p>For pages that are guides to a given complex topic.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="foo" name="page_name" />
<input type="hidden" value="Guide" name="form" />			<input type="submit" value="Create Guide Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Glossary">Glossary</span></h2>
<p>For pages that act as a collection of Glossary Items.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="foo" name="page_name" />
<input type="hidden" value="Glossary" name="form" />			<input type="submit" value="Create Glossary Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Glossary_Item">Glossary Item</span></h2>
<p>For pages that define a single term and its definition.
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Examples of topics and URLS
</p>
</div>
<p>			<form name="createbox" action="/wiki/Special:FormStart" method="get" class="">
</p>
			<p>
	<input size="25" placeholder="" autofocus="" class="formInput mw-ui-input" value="foo" name="page_name" />
<input type="hidden" value="Glossary Item" name="form" />			<input type="submit" value="Create Glossary Item Page" id="input_button_1" class="forminput_button"/></p>
<p>			</form>
</p><p><br />
</p>
<h2><span class="mw-headline" id="JavaScript_Operator">JavaScript Operator</span></h2>
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
</p><p><br />
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Create a Media Content page type
</p>
</div>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Create a Protocol page type
</p>
</div>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Create a Javascript Object page type
</p>
</div>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Create a Javascript Enum page type?
</p>
</div>

<!-- 
NewPP limit report
CPU time usage: 0.137 seconds
Real time usage: 0.142 seconds
Preprocessor visited node count: 418/1000000
Preprocessor generated node count: 1579/1000000
Post‐expand include size: 4077/2097152 bytes
Template argument size: 613/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%   86.935      1 - -total
  9.18%    7.980     17 - Template:TODO
  6.65%    5.783      1 - Template:Note
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:293-0!*!0!!*!*!*!esi=1 and timestamp 20150731045818 and revision id 70825
 -->
