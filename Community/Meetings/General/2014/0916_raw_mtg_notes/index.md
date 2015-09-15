---
title: WebPlatform Docs, weekly telcom meeting 2014-09-16 =
uri: 'WPD:Community/Meetings/General/2014/0916 raw mtg notes'

---
## <span>Presents</span>

Almost-quorum of 4

-   Jen Simmons (jensimmons)
-   Eliot Graff (eliot)
-   Scribe: Amelia Bellamy-Royds (AmeliaBR)
-   Chair: Doug Schepers (shepazu)

## <span>Agenda</span>

-   Update on ongoing projects
-   what's next for compatibility tables

## <span>Log</span>

### <span>Update on ongoing projects</span>

       shepazu (chairing): schedule -- will be away later in the month, vacation
       plus speaking in Sao Paolo; original plan included a DocSprint, but the
       local organization has changed over and it looks like it will be more
       informal

       ...recap from last week: we discussed options for a "mini DocSprint",
       getting people introduced to the concept, some editing, encouraging
       translation into Portuguese

       ...we really want translations for languages in areas where English is not
       a significant second language

       eliot: Russian would be another

       shepazu: translations are something we should put focus on, have a strategy
       around it

       ... last week we also talked about the HTML5 recommendation status
       announcement, considered whether we could have comprehensive HTML docs by
       then, but that doesn't seem likely.  Amelia suggested that we prep things
       so we are ready for new contributors on HTML, and capitalize on the
       announcement to encourage people to document the now-defined standard.

       eliot: Our goal (as organizers) has not been to do the documentation, but
       to create the infrastructure for the community to write docs, so that seems
       like a good strategy

       shepazu: By that time, in less than a few weeks, we should have a
       functional annotation system.

       ... we want people to go through the specs, identify areas that need
       documentation

       AmeliaBR: Clarify: annotations for the specs or annotations for webplatform
       docs?

       shepazu: they are one and the same,

       ...we've been working (with renoirb) and the Hypothesis team on this, and
       there will be a way for you to search all annotations everywhere; e.g., you
       could search "SVG" and "needs example"

       ... the annotation system will be for our pages, on the wiki, but there
       will also be a script on certain W3 specifications, that will be connected
       to our server.

       ... Instead of sending an email, they will make an account on our server
       and create a note there which will tie our docs back into the W3 specs.

       ... It also lets people leave comments on specifications, about what should
       be documented on webplatform docs.

       ... e.g., could identify a specific sentence or detail about an element,
       that comment would show up on the webplatform page about that element as
       well as on the specs.  Then when the documentation is taken care of, that
       comment could be closed in both places.

       ... and vice versa: if someone leaves a comment on our docs, e.g., that
       something is really confusing, that something should be changed in the
       actual specs, that comment can easily be connected back to the actual specs.

       ...we're hoping to get that virtuous cycle going.

       ... Amelia, what else did we do last week?

### <span>Compatibility tables</span>

       AmeliaBR: renoirb gave us an update on compatibility tables, he also sent
       some updates to the email list since then

       shepazu: now we have to decide if we want to work on the caniuse data, or
       focus on the W3 test data

       AmeliaBR: I'd recommend focusing energy on the test suite, rather than
       spending a lot of time on caniuse.com

       jensimmons: but what is the test data like?  I use caniuse all the time,
       that's existing, reliability data

       <+AmeliaBR> http://test.csswg.org/harness/

       <@shepazu> https://github.com/w3c/web-platform-tests

       jensimmons: that link, is that the tests, or is that the data?  it's a
       terrible user interface

       shepazu: it is a terrible user interface, there's lots of data, but it's
       not easily available

       jensimmons: well that could be the differentiator, where we could make a
       difference

       eliot: the data is there, but it's not available in a universal way.  Also,
       while it's great to have tests connected to the specs, it's nice to have a
       more top-level practical synthesis, which is what caniuse does well

       AmeliaBR: In a way, the caniuse data complements the MDN data, because it
       focuses on the top-level, big concepts, while MDN is more
       element-by-element, attribute-by-attribute.  So if we can integrate that
       easily in our structure, that would be beneficial to have compat data on
       top-level pages

       shepazu: I'm kind of on the fence.  We would have to massage the caniuse
       data a lot; but, when we adapted the MDN data, we did use codes and info
       similar to what caniuse uses, for e.g. whether polyfill or prefix is
       required.

       ...but we would have to work on the mapping of their data to our
       categorizations

       ...and it's not just the data, it's whether we would add anything as far as
       making it easier to access

       jensimmons: is the plan to merge all the data into one super data set, or
       are we going to be displaying this side by side?

       shepazu: no, I think we'd have to decide, for any given page, which data to
       use.  Since the caniuse data is based on some testing, it would probably
       replace the MDN data, if there was a one-to-one match.  Then later, if we
       have the W3 data, that could replace

       jensimmons: But we also have to be careful, e.g. tests might not catch all
       the little nuances, where caniuse has notes or explanations that someone
       has gone in and added

       AmeliaBR: The difference is that W3 tests try to represent that with
       multiple tests, each of which catches a different situation or edge case,
       rather than summing it up with one measurement.  But we'd have to decide
       how to display that information.

       jensimmons: The other great thing about caniuse is that they clearly
       display the versions of web browsers, which is much more relevant than just
       saying something "is supported in Chrome"

       shepazu: that's what I was saying, it's not just the data, it's how they
       display it, which caniuse does so well

       ... we really want to get away from the idea of just being another MDN.  We
       want to look at other added benefits.  E.g., caniuse has better compat
       data, but we not the other info

       ... but I still want to be better than "MDN + caniuse data"; which even
       that isn't straightforward, because the level of detail doesn't match up

       ... jen, maybe if you could think, looking at the caniuse data, how would
       that be effectively integrated into a larger page, having all that
       information about current, older and future versions, but display that
       compactly

       ... similarly, another design challenge, is how to integrate the W3 tests;
       when you have 30 tests on a property, and a browser passes 25 of them, how
       do you display that information in a summary level, that someone could
       click on to drill down and discover the specific cases where it is or isn't
       supported.

       ...or, if you want to see how a feature is used, look at how the actual
       tests are written to see that.  Do you want to think about that?

       jensimmons:  On that issue, we could argue about what percentage of tests
       is required for support, but some tests are more important than others, and
       there's no way to program robots to be that smart.  So I think what you're
       saying is good, don't try to convert to a binary supports/doesn't support,
       just display the number of tests passed, and click on it for the details,
       but the trick is to display that extended information in a useful way.

       ...but another thing, is to make sure that there is way for people to come
       along, if they do understand it, to translate it into a human explanation
       for others

       ...they could write "oh this is a little edge case, it's mostly supported",
       or "this is a major problem, don't use this feature yet"

       shepazu: A third, hybrid option, is to add the data to the page, but also
       work to categorize the tests as edge cases vs core features, and feed that
       information back to the test suite.

       ... I think that's what you were getting at, but the next step is to leave
       the data on the tests

       jensimmons: I think most people wouldn't really care about that.

       shepazu: the difference is, that once we've categorized things, then it can
       be updated automatically and affect how we display the information; people
       wouldn't have to read this, but it would affect what they'd see.

       ...somebody could take that data, and update it, for example if things that
       used to be edge cases are now being commonly used

       ...that would be a way of giving feedback to implementers, that this
       specific test is important to us now

       jensimmons: there are these sort of bleeding-edge technologies, like
       viewport units that you can mostly use, but you have to be careful, about
       where you can or can't use them, some are well supported (vh and vw),
       others are buggy (vmin, vmax)

       ...to have someone say, these things are important, they are supported,
       other things maybe it's not clear where they would be used, because they
       don't have the support to actually use them and discover the different ways
       they could be used

       shepazu: either way, we're talking about adding human annotation over the
       test results.  If you can all think about how this could be better
       displayed or integrating, not just better than we're doing now, but better
       than everyone else, to display it more compactly, more accurately, I think
       that would be really useful.

       AmeliaBR: I think, what we want is to have the convenience, the level of
       detail about versions, that caniuse has, but have it at the much more
       detailed level as far as specific features

       shepazu: I think we have to do that, because that's how our site is laid
       out; we can't use it just as caniuse has it, because it doesn't fit in our
       site

       jensimmons: I can definitely start thinking about it

       AmeliaBR: long term, I'd really like to get to know the data on the W3
       tests, and figure out how we can put a decent interface to that