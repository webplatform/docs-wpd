---
title: WPD:GSoC
---
<h1><span class="mw-headline" id="Google_Summer_of_Code_2013">Google Summer of Code 2013</span></h1>
<p>WebPlatform.org is a community-based web developer documentation site convened by W3C, the web standards organization, and backed by major Web industry companies.
</p><p>Students can contact the community for more information through  email at public-webplatform@w3.org or  Freenode (channel #webplatform). Ping <b>shepazu</b> for details.
</p>
<h2><span class="mw-headline" id="Ideas">Ideas</span></h2>
<h3><span class="mw-headline" id="Browser_Compatibility_Table_API">Browser Compatibility Table API</span></h3>
<p><b>Brief explanation:</b> Build an API for use on our site and by the general public for accessing information on browser support for various web programming features, integrating data from multiple different sources, such as CanIUse, Quirksmode, and W3C test suites. See the <a href="/wiki/WPD:Compatibility_Info" title="WPD:Compatibility Info">Compatibility Info article</a> for more information.
</p><p><b>Expected Results:</b> All articles on WebPlatform.org, and users on other sites and resources, will have access to fine-grained, test-driven, automated browser support tables for all features of the Web Platform.
</p><p><b>Knowledge Prerequisite:</b> HTML, CSS, JS, PHP (and MediaWiki extension knowledge) helpful, testing methodology. <b>Skill level:</b> medium to high.
</p><p><b>Mentor:</b> Doug "shepazu" Schepers &lt;schepers@w3.org&gt;
</p>
<h3><span class="mw-headline" id="Crowdsourcing_Browser_Testing">Crowdsourcing Browser Testing</span></h3>
<p><b>Brief explanation:</b> Build a workflow and UI for a specification test management system, including a way to select a spec, define or choose a set of testable assertions from that spec, input a test without needing to add metadata and other automatable information, submit the test for review, and collaborate in the review using a peer-reviewed upvote system. See the <a href="/wiki/WPD:Crowdsourcing_Testing" title="WPD:Crowdsourcing Testing">Crowdsourcing Testing article</a> for more information.
</p><p><b>Expected Results:</b> Efforts such as <a rel="nofollow" class="external text" href="http://testthewebforward.org/">Test the Web Forward</a> would have access to a systematic, prioritized, low-barrier, and efficient , spec-test crowdsourcing application to manage the creation, review, and community around tests.
</p><p><b>Knowledge Prerequisite:</b> HTML, CSS, JS, back-end language of choice, testing methodology. <b>Skill level:</b> medium to high.
</p><p><b>Mentor:</b> Doug "shepazu" Schepers &lt;schepers@w3.org&gt;, Tobie Langel &lt;tobie@w3.org&gt;
</p>
<h3><span class="mw-headline" id="HTML_Editing_API_Shim">HTML Editing API Shim</span></h3>
<p><b>Brief explanation:</b> The current state of editing functionality in the browser, such as <i>execCommand</i> and <i>content-editable</i>, are not interoperable, not extensible, and not efficient. This results in multiple editing scripts being deployed over the web. A shim that works across browsers, efficiently and logically, could serve as the basis for a modern specification, and would be useful for WebPlatform.org's editing experience.
</p><p><b>Expected Results:</b> A modern shim to edit HTML, and maybe SVG and CSS. It would manage content selection, undo and redo, wrapping content in new elements (or removing wrapping elements), and providing an incremental diff for the content to update remotely through XHR. 
</p><p><b>Knowledge Prerequisite:</b> HTML, JS, APIs. <b>Skill level:</b> medium to high.
</p><p><b>Mentor:</b> Doug "shepazu" Schepers &lt;schepers@w3.org&gt;, Robin Berjon &lt;robin@w3.org&gt;, Dave Raggett &lt;dave@w3.org&gt;
</p>
<h3><span class="mw-headline" id="Modern_DMS">Modern DMS</span></h3>
<p><b>Brief explanation:</b> Most Documentation Management Systems are clumsy and built of custom components, so they suffer from project rot and disorganization. A better solution is a DMS/CMS that uses off-the-shelf components connected together. The server infrastructure would be NodeJS, with a Git-based storage system allowing for transcluded articles and compilations, an HTML Editing JS shim for editing, <a rel="nofollow" class="external text" href="http://www.elasticsearch.org/">elasticsearch</a> for searching, and other individual components to complete the system.
</p><p><b>Expected Results:</b> A reliable, component-based, simple, FOSS DMS/CMS for WebPlatform.org, which will serve as a model for other similar projects. 
</p><p><b>Knowledge Prerequisite:</b> HTML, JS, APIs. <b>Skill level:</b> medium to high.
</p><p><b>Mentor:</b> Doug "shepazu" Schepers &lt;schepers@w3.org&gt;
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:7988-0!*!0!!*!*!*!esi=1 and timestamp 20150731184003 and revision id 29837
 -->
