---
title: WPD:Site/Technical Requirements
---
<h2><span class="mw-headline" id="A_Note_on_Priorities">A Note on Priorities</span></h2>
<p>Each feature should be marked with a priority, to help determine which features are needed when evaluating a CMS.
</p>
<ul><li> <b>1:</b> Must have</li>
<li> <b>2:</b> Should have</li>
<li> <b>3:</b> Nice to have</li></ul>
<h3><span class="mw-headline" id="Anti-features">Anti-features</span></h3>
<p>If there is a feature that the CMS should not have, that should also be noted, for example:
</p>
<pre>Should not require users to learn a new, unfamiliar markdown syntax <b>(1)</b>
</pre>
<p>Note, though, that most of these could be stated as "positive requirements":
</p>
<pre>If uses markdown syntax, should use a familiar syntax such as MediaWiki's <b>(1)</b>
</pre>
<h2><span class="mw-headline" id="Core_Features">Core Features</span></h2>
<ul><li> Accessible: 
<ul><li> <a rel="nofollow" class="external text" href="http://www.w3.org/TR/WCAG/">WCAG 2.0</a> (content aspect)
<ul><li> Level A <b>(1)</b></li>
<li> Level AA <b>(2)</b></li></ul></li>
<li> <a rel="nofollow" class="external text" href="http://www.w3.org/TR/ATAG20/">ATAG 2.0</a> (authoring tool aspect)
<ul><li> Level A <b>(1)</b></li>
<li> Level AA <b>(2)</b></li></ul></li></ul></li>
<li> Internationalizable
<ul><li> easy to add translations or localizations <b>(1)</b></li>
<li> easy to find available translations and navigate to them <b>(1)</b></li></ul></li>
<li> clean semantic underlying code, as much as possible <b>(2)</b></li>
<li> relatively easy and systemic method for porting well-formed content from multiple origins <b>(2)</b>
<ul><li> <i>Note:</i> This is most important for the launch, less so for continued growth, so the way to do this doesn't have to be exposed to the general public... could be a bespoke workflow</li></ul></li>
<li> Must work equally well across browsers
<ul><li> viewing pages must work in all versions of browsers <b>(1)</b></li>
<li> editing pages must work in all modern browsers <b>(1)</b></li></ul></li>
<li> Customizable UI</li>
<li> Mobile-friendly output <b>(2)</b></li></ul>
<h2><span class="mw-headline" id="Permissions_and_Profiles">Permissions and Profiles</span></h2>
<ul><li> Editable by anyone with account <b>(1)</b>
<ul><li> Should track content contributions <b>(1)</b></li>
<li> Should have profile pages <b>(1)</b></li>
<li> Should allow login through OAuth via other identity providers (including W3C) <b>(2)</b></li></ul></li>
<li> Some pages can be "locked" <b>(1)</b> or have curated changes only <b>(2)</b></li></ul>
<h2><span class="mw-headline" id="Navigation_and_Categorization">Navigation and Categorization</span></h2>
<ul><li> Tagging:
<ul><li> must support the annotation or tagging of content to include it in different structures, rather than organizing it in rigid categories <b>(1)</b></li>
<li> tagging system also needs to support a smart referencing system, to generate most of the references to display/make available within each article. For example: An article on responsive design using media queries and viewport, which also makes use of HTML5 &lt;video&gt; and CSS transitions, should have links to those article automatically generated. <b>(2)</b></li></ul></li>
<li> Customizable sidebar / TOC <b>(1)</b></li>
<li> URIs should be consistent, predictable, and unchanging <b>(1)</b></li>
<li> Should allow multiple ways to find and navigate through content, including:
<ul><li> sequential stepping through related pages <b>(1)</b></li>
<li> links to related topics <b>(1)</b></li>
<li> autocomplete search bar (a la DocHub) <b>(2)</b></li>
<li> drill-downs from general topics to more specific, based on categories <b>(2)</b></li></ul></li></ul>
<h2><span class="mw-headline" id="Editing">Editing</span></h2>
<ul><li> Should have WYSIWYG editing <b>(2)</b></li>
<li> Custom markup and other code that the WYSIWYG doesn't do, for example being able to create a custom CSS layout for a particular article if needed. <b>(1)</b>
<ul><li> CHRIS - Ideally it should be possible to apply custom scripts and stylesheets to pages, although I do accept that in reality this is probably too much of a security hole to have without any limit.</li>
<li> Specific preferences for generated markup <b>(2)</b></li></ul></li>
<li> Template system for different kinds of content (reference pages for elements, attributes, CSS properties, events, APIs, etc.) <b>(2)</b></li></ul>
<h2><span class="mw-headline" id="Code_and_Examples">Code and Examples</span></h2>
<ul><li> Should be possible for the CMS to handle HTML5 as the standard language for all pages <b>(1)</b></li>
<li> embedding of code examples <b>(1)</b></li>
<li> code and example highlighting <b>(1)</b>
<ul><li> start from numbers other than 1, to allow continuations of snippets <b>(2)</b></li></ul></li>
<li> Embedding live demos like Canvas, SVG, HTML5 &lt;video&gt;, etc? <b>(1)</b></li></ul>
<h2><span class="mw-headline" id="Content_Management">Content Management</span></h2>
<ul><li> Include a "last updated" field in each article's footer <b>(1)</b> </li>
<li> Public view of "stale" articles that haven't been updated in a while, and may need review <b>(2)</b></li></ul>
<h2><span class="mw-headline" id="Advanced_Features">Advanced Features</span></h2>
<ul><li> transclusion of content snippets <b>(2)</b>
<ul><li> <i>The ability to define snippets of content to include directly in other pages. In practice this often allows tagging to work well, and makes changes to some kinds of formatting or content easier to accomplish.</i></li>
<li> <i>komoroske: I'd argue that this is a priority 1 feature. Without this feature it's extremely difficult to implement consistent information architecture of pages.</i></li></ul></li>
<li> Videos <b>(1)</b>
<ul><li> Captioning <b>(1)</b></li>
<li> Served from same server (e.g. not YouTube / Vimeo) <b>(3)</b>
<ul><li> <i>komoroske: Serving video also comes with potentially large bandwidth costs, which can be sidestepped by using YouTube/Vimeo</i></li></ul></li></ul></li>
<li> Per-page scripts <b>(2)</b></li></ul>
<h2><span class="mw-headline" id="Extra_Site_Features">Extra Site Features</span></h2>
<ul><li> Executable code example editor (e.g. JSFiddle, JSBin, Dabblet) <b>(1)</b>
<ul><li> Should be able to open all examples in editor <b>(2)</b></li></ul></li>
<li> <a rel="nofollow" class="external text" href="http://en.wikipedia.org/wiki/Pastebin">Pastebin</a>: may be same as code editor <b>(2)</b> </li>
<li> Blog <b>(2)</b></li>
<li> Forums <b>(2)</b></li>
<li> Surveys <b>(3)</b></li></ul>
<h2><span class="mw-headline" id="APIs">APIs</span></h2>
<ul><li> Extractable pages for use remotely <b>(2)</b>
<ul><li> Structured sections of page for customized extraction <b>(2)</b> </li></ul></li>
<li> Allow automated input of browser support based on tests or other external data <b>(2)</b></li></ul>
<h2><span class="mw-headline" id="Metrics">Metrics</span></h2>
<ul><li> Feedback / rating for each article <b>(2)</b></li>
<li> Tracking searches and result selection <b>(3)</b></li>
<li> Usage data per site and per page <b>(2)</b></li>
<li> Tracking should only be in aggregate, not per user <b>(1)</b></li></ul>
<h2><span class="mw-headline" id="Scaling">Scaling</span></h2>
<ul><li> Serving infrastructure can theoretically handle 10 million page views a month without problems <b>(1)</b></li>
<li> Serving infrastructure can easily scale to handle arbitrary load as the site gains in popularity <b>(2)</b></li>
<li> Serving cost scales smoothly with amount of traffic; no price cliffs <b>(2)</b></li>
<li> Cost structure allows 10 million page views for less than $10,000/mo <b>(2)</b>
<ul><li> <i>komoroske: I just picked an arbitrary number here. Just trying to express it should be reasonably cheap.</i></li></ul></li></ul>
<h2><span class="mw-headline" id="Support">Support</span></h2>
<ul><li> Support infrastructure to have site back up within an hour if any outages occur at any time <b>(1)</b></li>
<li> Support infrastructure in place to implement scaling as load increases over time <b>(2)</b></li>
<li> Support infrastructure to provide advice on configuring the site to run smoothly <b>(2)</b></li>
<li> Support infrastructure to consult and/or implement site upgrades over time <b>(3)</b></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:19-0!*!*!!*!*!*!esi=1 and timestamp 20150731181022 and revision id 23067
 -->
