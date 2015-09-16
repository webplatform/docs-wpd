---
title: Google Summer of Code 2013
uri: 'WPD:GSoC'

---
WebPlatform.org is a community-based web developer documentation site convened by W3C, the web standards organization, and backed by major Web industry companies.

Students can contact the community for more information through email at public-webplatform@w3.org or Freenode (channel \#webplatform). Ping **shepazu** for details.

## Ideas

### Browser Compatibility Table API

**Brief explanation:** Build an API for use on our site and by the general public for accessing information on browser support for various web programming features, integrating data from multiple different sources, such as CanIUse, Quirksmode, and W3C test suites. See the [Compatibility Info article](/WPD:Compatibility_Info) for more information.

**Expected Results:** All articles on WebPlatform.org, and users on other sites and resources, will have access to fine-grained, test-driven, automated browser support tables for all features of the Web Platform.

**Knowledge Prerequisite:** HTML, CSS, JS, PHP (and MediaWiki extension knowledge) helpful, testing methodology. **Skill level:** medium to high.

**Mentor:** Doug "shepazu" Schepers \<schepers@w3.org\>

### Crowdsourcing Browser Testing

**Brief explanation:** Build a workflow and UI for a specification test management system, including a way to select a spec, define or choose a set of testable assertions from that spec, input a test without needing to add metadata and other automatable information, submit the test for review, and collaborate in the review using a peer-reviewed upvote system. See the [Crowdsourcing Testing article](/WPD:Crowdsourcing_Testing) for more information.

**Expected Results:** Efforts such as [Test the Web Forward](http://testthewebforward.org/) would have access to a systematic, prioritized, low-barrier, and efficient , spec-test crowdsourcing application to manage the creation, review, and community around tests.

**Knowledge Prerequisite:** HTML, CSS, JS, back-end language of choice, testing methodology. **Skill level:** medium to high.

**Mentor:** Doug "shepazu" Schepers \<schepers@w3.org\>, Tobie Langel \<tobie@w3.org\>

### HTML Editing API Shim

**Brief explanation:** The current state of editing functionality in the browser, such as *execCommand* and *content-editable*, are not interoperable, not extensible, and not efficient. This results in multiple editing scripts being deployed over the web. A shim that works across browsers, efficiently and logically, could serve as the basis for a modern specification, and would be useful for WebPlatform.org's editing experience.

**Expected Results:** A modern shim to edit HTML, and maybe SVG and CSS. It would manage content selection, undo and redo, wrapping content in new elements (or removing wrapping elements), and providing an incremental diff for the content to update remotely through XHR.

**Knowledge Prerequisite:** HTML, JS, APIs. **Skill level:** medium to high.

**Mentor:** Doug "shepazu" Schepers \<schepers@w3.org\>, Robin Berjon \<robin@w3.org\>, Dave Raggett \<dave@w3.org\>

### Modern DMS

**Brief explanation:** Most Documentation Management Systems are clumsy and built of custom components, so they suffer from project rot and disorganization. A better solution is a DMS/CMS that uses off-the-shelf components connected together. The server infrastructure would be NodeJS, with a Git-based storage system allowing for transcluded articles and compilations, an HTML Editing JS shim for editing, [elasticsearch](http://www.elasticsearch.org/) for searching, and other individual components to complete the system.

**Expected Results:** A reliable, component-based, simple, FOSS DMS/CMS for WebPlatform.org, which will serve as a model for other similar projects.

**Knowledge Prerequisite:** HTML, JS, APIs. **Skill level:** medium to high.

**Mentor:** Doug "shepazu" Schepers \<schepers@w3.org\>
