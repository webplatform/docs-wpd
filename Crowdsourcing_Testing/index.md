---
title: 'WPD:Crowdsourcing Testing'
uri: 'WPD:Crowdsourcing Testing'

---
This idea was developed over the last few years, and briefly discussed after Adobe's [Test the Web Forward](http://testthewebforward.org/) event (see [blog report](http://blogs.adobe.com/webplatform/2012/06/20/test-the-web-forward-weekend/)). That event showed that we have some opportunity around this, and a few challenges.

Opportunities:

-   Demonstrated interest by participants
-   Enlightened self-interest for developers

Challenges:

-   How to train enough people to scale this up?
-   How to get people (in whom we invest training) to persist in participating and contributing beyond the event itself?
-   How to make the process simpler, to lower the barriers?
-   How to vet the tests, and reward reviewers (everyone hates to review)?

This is a basic sketch-out of an idea for a crowdsourcing infrastructure (e.g. webapp), detailed in the form of a user-interface workflow (since that's the way I think). This would remove much of the administrivia and non-useful details (e.g. the metadata format), and concentrate on the skills that developers already have, or could learn or reuse:

-   HTML, CSS, SVG, JS, APIs, etc.
-   General unit testing
-   Reading and understanding specifications, and extracting testable assertions (they may have to learn this)
-   the particular W3C spec-testing methodology above and beyond unit testing skills (they will have to learn this)

I estimate this will take 2 people 6 weeks to build, with 0.5 FTE ongoing for future development and maintenance, decreasing over time, but required periodically. So, that means that it will take 4 people 12 weeks to build. But we can start simple and see how the prototyping goes.

## Specification and Testable Assertions page

List of all relevant specifications

-   each spec expands out into a list of all testable assertions and other testable characteristics, with indicator of number of tests on that assertion (submitted, reviewed, accepted)
    -   clicking on a testable assertion navigates to Testable Assertions page

## Testable Assertion page

Info on a specific testable assertion, including:

-   excerpt of spec, in context
-   spec chapter, section, URL, etc.
-   relative difficulty of testing (5-star)
-   discussion forum, where people can clarify (or question) what is being tested, how to test it, and so on
-   button to create test for that assertion (navigates to Test Creation page)
-   button to file bug on that testable assertion (navigates to Bug Report page)

## Test Creation page

JSFiddle-like interface, with sections for markup (HTML, SVG, MathML, etc.), Javascript, CSS, and output

-   Can spawn more input areas (e.g. for testing external SVG file references in SVG or HTML)
-   Metadata is already filled out for user, including author, spec URL and section, keywords, etc.
    -   Most metadata can be edited
-   Any spec-specific test framework code included in input areas
-   Once test is completed, user clicks button to submit test for review
    -   Code is validated on submit, no vendor prefixes allowed
    -   Successful submission navigates to Test Review page

## Test Review page

Q&A forum (StackOverflow-like)

-   allows comments and discussion on test
-   Voting
    -   can vote test up or down
    -   can vote comments up or down
    -   can fork and refine test, all discussion stays on this page
        -   test can have multiple authors
    -   karma is assigned to authors and good commenters
        -   more user karma gives more weight to review, weighted by test difficulty
    -   once test reaches certain review threshold, submitted to WG for review and approval

## All Tests page

List of all submitted tests and their status

-   sorted by technology, spec, date
-   clicking on a non-accepted test navigates to Test Review page
-   clicking on an accepted test navigates to Accepted Test page

## Accepted Test page

Shows test

-   Shows test metadata, status, implementation report
-   button to file bug on test (navigates to Test Review page)
-   button to file bug on implementation (navigates to Bug Report page)

## Bug Report page

-   Allows user to coment or file bug on spec, linking to testable assertion page
-   Allows user to file bug on one or more implementations, by linking to a test

## User Profile page

-   list of links to all activity for tests, wiki, forums, bug reports, maybe W3C activity
-   karma rating
-   badges, so on

## Notes

-   Same kind of people who are likely to contribute to Web Platform Docs are likely to contribute tests or file bug reports
-   See where we can integrate into Shepherd
-   Maybe use Browserscope integration for reporting?
-   Test Challenges: have limited-time events where specific conformance criteria are put forward, and the most innovative and comprehensive test wins a prize. These can start small, and continue as a series of events.
