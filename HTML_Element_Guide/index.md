---
title: WPD:HTML Element Guide
---
<h1><span class="mw-headline" id="HTML_Element_Guide">HTML Element Guide</span></h1>
<h3><span class="mw-headline" id="Before_you_begin">Before you begin</span></h3>
<p>Before you begin, you already should have:
</p>
<ul><li> taken the steps to register for this site, communicate with the team, and work with the wiki. (Select <a href="/wiki/WPD:Editors_Guide" title="WPD:Editors Guide" class="mw-redirect">"Editing"</a> from any page on the site.)</li>
<li> ran through at least one basic contribution. (See how to <a href="/wiki/WPD:Getting_Started" title="WPD:Getting Started">start contributing content</a>, and cycle through one basic task, such as fixing a link or adding a summary to a page.)</li></ul>
<h3><span class="mw-headline" id="High-level_steps">High-level steps</span></h3>
<p>Below, Chris Mills runs through updating a property. But basically, you:
</p>
<ul><li> pick a property from the HTML elements list at <a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/html/elements">http://docs.webplatform.org/wiki/html/elements</a>. Tell us about what you want to do.</li>
<li> read the HTML element page through, if it already exists. If not, tell a steward and we will create it for you.</li>
<li> compare it to its spec(s).</li>
<li> compare the content to other reputable sites, such as Mozilla Developer Network.</li>
<li> play around with the elements documented – you can use our playground <a rel="nofollow" class="external free" href="http://code.webplatform.org">http://code.webplatform.org</a>.</li>
<li> update the page based on your findings</li>
<li> remove any flags you think are no longer necessary</li>
<li> let us know you've done a page and if you'd like a review</li></ul>
<h2><span class="mw-headline" id="Choosing_an_element_to_work_on">Choosing an element to work on</span></h2>
<p>So the first step is to have a look at which properties you would like to work on. I would suggest grabbing a group of related properties that would work well as unit to work on. So for example:
</p>
<ul><li> table</li>
<li> tr</li>
<li> td</li>
<li> th</li></ul>
<h2><span class="mw-headline" id="Assigning_you_to_work_on_your_chosen_properties">Assigning you to work on your chosen properties</span></h2>
<p>Once you have grabbed some properties to work on, let us know, so we can track who is working on what, then work through each property until you have completed your set.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Entering_data_on_the_page">Entering data on the page</span></h2>
<p>Now you are ready to start gathering the data to enter into your page. I'd advise that you gather the data and record it offline first, just in case something stupid happens and you lose your edits. I'm not saying it <i>will</i> happen, but you never know with Wikis! So copy the following headings, put them into your text editor, then read below on how to fill them in.
</p>
<ul><li> Custom page title: usually just the name of the element</li>
<li> Standardization status: what standardization stage is the element in? If it appears in multiple specs, then choose the most mature status, provided the element hasn't been massively repurposed in HTML5</li>
<li> API Name: if there is an associated API for the element, e.g. in the case of <code>&lt;canvas&gt;</code></li>
<li> Article summary: provide a one line summary of what the element does. What is its purpose?</li>
<li> DOM Interface: what is the element's DOM interface?</li>
<li> Main content: provided detailed content on how the element works, what it does, use cases, attributes.</li>
<li> Examples: provide a useful working example if the element. It is best to use our codelet tool, found at <a rel="nofollow" class="external free" href="http://code.webplatform.org/">http://code.webplatform.org/</a></li>
<li> Notes and usage: this is a good place to add real world examples if quirks and annoyances with using the element, along with real world solutions. This is the real valuable stuff that isn't generally picked up easily. For example, browser specific bugs, limitations in usage, comment mistakes, limitations in CSS styling on form elements. Ignore the import notes section.</li>
<li> Related specifications: list the name, URL, W3C standardization status and relevant changes for the element. The last couple of specs will do in most cases. Relevant changes is for recording anything significant that has changed about the element's purpose in that spec. For example, in HTML definition list was changed to description list. You can provide more details in the main content or usage sections above if needed. </li>
<li> Compatibility sections: ignore these. We are currently in the process of automating browser support data.</li>
<li> See also section: Provide useful links to related ref docs, tutorials, etc.</li></ul>
<p>After collecting all the information, you'll then need to go through the different form fields in the edit page and fill each one in.
</p>
<h3><span class="mw-headline" id="Researching_information">Researching information</span></h3>
<p>You should research the information for your article and how to verify its correct, using trustworthy sites like MDN, caniuse, quirksmode and relevant HTML specs. Review existing documentation from other sources and then read the relevant specs. If the sources all agree then you can accept the information as correct, but if they disagree you should do original research or ask for help from more knowledgeable members.
</p><p>When you have finished writing a page, you should get someone else to review it to verify its quality.
</p>
<h3><span class="mw-headline" id="Putting_information_that_applies_to_multiple_elements_in_separate_pages">Putting information that applies to multiple elements in separate pages</span></h3>
<p>NOTE: One important thing you should consider when entering information into your property pages is whether any of that information also applies to other HTML elements. If it does, then you should consider putting that information into a separate page, whether it is a concept, attribute or whatever. This way, you can save others a lot of time and repetition.
</p><p>So for example, you would cover a universal attribute in its own page, and not talk about it separately on each page that covers it. For example, the <code>class</code> attribute is covered at <a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/html/attributes/class">http://docs.webplatform.org/wiki/html/attributes/class</a>
</p><p>If you were describing the high level usage of tables and showing a quick guide, you would probably do this in the "concepts" tree, along with, "viewport," "vendor prefixes," and "standards
mode." Readers may benefit from links to tutorials on the subject available as "HTML learning material."
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:9528-0!*!0!!*!*!*!esi=1 and timestamp 20150731184547 and revision id 35888
 -->
