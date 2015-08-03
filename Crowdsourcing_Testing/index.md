---
title: WPD:Crowdsourcing Testing
---
<p>This idea was developed over the last few years, and briefly discussed after Adobe's <a rel="nofollow" class="external text" href="http://testthewebforward.org/">Test the Web Forward</a> event (see <a rel="nofollow" class="external text" href="http://blogs.adobe.com/webplatform/2012/06/20/test-the-web-forward-weekend/">blog report</a>). That event showed that we have some opportunity around this, and a few challenges.
</p><p>Opportunities:
</p>
<ul><li> Demonstrated interest by participants</li>
<li> Enlightened self-interest for developers</li></ul>
<p>Challenges:
</p>
<ul><li> How to train enough people to scale this up?</li>
<li> How to get people (in whom we invest training) to persist in participating and contributing beyond the event itself?</li>
<li> How to make the process simpler, to lower the barriers?</li>
<li> How to vet the tests, and reward reviewers (everyone hates to review)?</li></ul>
<p>This is a basic sketch-out of an idea for a crowdsourcing infrastructure (e.g. webapp), detailed in the form of a user-interface workflow (since that's the way I think). This would remove much of the administrivia and non-useful details (e.g. the metadata format), and concentrate on the skills that developers already have, or could learn or reuse:
</p>
<ul><li> HTML, CSS, SVG, JS, APIs, etc.</li>
<li> General unit testing</li>
<li> Reading and understanding specifications, and extracting testable assertions (they may have to learn this)</li>
<li> the particular W3C spec-testing methodology above and beyond unit testing skills (they will have to learn this)</li></ul>
<p>I estimate this will take 2 people 6 weeks to build, with 0.5 FTE ongoing for future development and maintenance, decreasing over time, but required periodically. So, that means that it will take 4 people 12 weeks to build. But we can start simple and see how the prototyping goes.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Specification_and_Testable_Assertions_page">Specification and Testable Assertions page</span></h2>
<p>List of all relevant specifications
</p>
<ul><li> each spec expands out into a list of all testable assertions and other testable characteristics, with indicator of number of tests on that assertion (submitted, reviewed, accepted)
<ul><li> clicking on a testable assertion navigates to Testable Assertions page</li></ul></li></ul>
<h2><span class="mw-headline" id="Testable_Assertion_page">Testable Assertion page</span></h2>
<p>Info on a specific testable assertion, including:
</p>
<ul><li> excerpt of spec, in context</li>
<li> spec chapter, section, URL, etc.</li>
<li> relative difficulty of testing (5-star)</li>
<li> discussion forum, where people can clarify (or question) what is being tested, how to test it, and so on</li>
<li> button to create test for that assertion (navigates to Test Creation page)</li>
<li> button to file bug on that testable assertion (navigates to Bug Report page)</li></ul>
<h2><span class="mw-headline" id="Test_Creation_page">Test Creation page</span></h2>
<p>JSFiddle-like interface, with sections for markup (HTML, SVG, MathML, etc.), Javascript, CSS, and output
</p>
<ul><li> Can spawn more input areas (e.g. for testing external SVG file references in SVG or HTML)</li>
<li> Metadata is already filled out for user, including author, spec URL and section, keywords, etc.
<ul><li> Most metadata can be edited</li></ul></li>
<li> Any spec-specific test framework code included in input areas</li>
<li> Once test is completed, user clicks button to submit test for review
<ul><li> Code is validated on submit, no vendor prefixes allowed</li>
<li> Successful submission navigates to Test Review page</li></ul></li></ul>
<h2><span class="mw-headline" id="Test_Review_page">Test Review page</span></h2>
<p>Q&amp;A forum (StackOverflow-like) 
</p>
<ul><li> allows comments and discussion on test</li>
<li> Voting
<ul><li> can vote test up or down</li>
<li> can vote comments up or down</li>
<li> can fork and refine test, all discussion stays on this page
<ul><li> test can have multiple authors</li></ul></li>
<li> karma is assigned to authors and good commenters
<ul><li> more user karma gives more weight to review, weighted by test difficulty</li></ul></li>
<li> once test reaches certain review threshold, submitted to WG for review and approval</li></ul></li></ul>
<h2><span class="mw-headline" id="All_Tests_page">All Tests page</span></h2>
<p>List of all submitted tests and their status
</p>
<ul><li> sorted by technology, spec, date</li>
<li> clicking on a non-accepted test navigates to Test Review page</li>
<li> clicking on an accepted test navigates to Accepted Test page</li></ul>
<h2><span class="mw-headline" id="Accepted_Test_page">Accepted Test page</span></h2>
<p>Shows test
</p>
<ul><li> Shows test metadata, status, implementation report</li>
<li> button to file bug on test (navigates to Test Review page)</li>
<li> button to file bug on implementation (navigates to Bug Report page)</li></ul>
<h2><span class="mw-headline" id="Bug_Report_page">Bug Report page</span></h2>
<ul><li> Allows user to coment or file bug on spec, linking to testable assertion page</li>
<li> Allows user to file bug on one or more implementations, by linking to a test</li></ul>
<h2><span class="mw-headline" id="User_Profile_page">User Profile page</span></h2>
<ul><li> list of links to all activity for tests, wiki, forums, bug reports, maybe W3C activity </li>
<li> karma rating</li>
<li> badges, so on</li></ul>
<h2><span class="mw-headline" id="Notes">Notes</span></h2>
<ul><li> Same kind of people who are likely to contribute to Web Platform Docs are likely to contribute tests or file bug reports </li>
<li> See where we can integrate into Shepherd</li>
<li> Maybe use Browserscope integration for reporting?</li>
<li> Test Challenges: have limited-time events where specific conformance criteria are put forward, and the most innovative and comprehensive test wins a prize. These can start small, and continue as a series of events.</li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:7936-0!*!*!!*!*!*!esi=1 and timestamp 20150731183930 and revision id 29247
 -->
