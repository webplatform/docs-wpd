---
title: Contributor Recognition
uri: 'WPD:Community/Contributor Recognition'

---
## <span>Types of Contributor Recognition Systems</span>

There are at least three types of recognition systems for community sites:

-   Quantitative recognition: Automated tracking and display of contribution statistics, such as (for a wiki) number of edits, number of words, length of membership.
-   Achievement recognition: Acknowledgement by some entity (organization, usually) that someone has met defined criteria of achievement. Think: Boy Scout or Girl Scout badges.
-   Peer recognition: Acknowledgement by an individual of a contribution (singular or aggregate) by another individual in a community.

### <span>Quantitative Recognition</span>

MDN has not used quantitative recognition at all; they intend to add such features, but have not yet sketched a design.

The [Mozilla Support discussion forums](https://support.mozilla.org/en-US/forums) display the number of posts that a user has made, under their name on a post; their profile shows the number of:

-   questions asked
-   answers given
-   solutions given (i.e., selected by the questioner as the best response)

These are very basic stats, but give an indication of how long/much someone has been around, and how helpful they are. Many other sites use this type of recognition, and may define various user "levels" (e.g., "rookie" up to "MVP") based on contribution stats.

    Janet's Opinion: Quantitative recognition systems are challenging to
    design, because you need to be sure that the behaviors you recognize (and
    therefore implicitly reward) are actually desirable in the community, and not
    easily "gamed" with non-constructive activity. StackOverflow has an extremely
    well-designed system in this regard. But I'm highly skeptical of most
    recognition systems promoted under the buzzword of "gamification".

A rather elaborate system for quantitative recognition was developed at Sun by Peter Reiser and others, called ["Community Equity"](http://kenai.com/projects/community-equity) ([slides](http://www.slideshare.net/peterreiser/community-equity-overview-2419832)). It aggregates various kinds of quantitative measures of contribution into a single score, which is intended to be portable across systems that use the algorithm. Sun both open-sourced the implementation (which is in Java, of course) and patented it. ***Janet's Opinion:** I think the patent was intended to be defensive, but I have no idea how Oracle regards it.*

    Peter's Opinion: There are good systems in place for forums that
    award for posting answers and we can get an off-the-shelf solution or
    extension for that if we have a forum on webplatform.org (are we going to?).
    In addition, rewards for other categories can be added. For an example of the
    different activities and associated awards, take a look at
    http://www.dotnetnuke.com/Community/Community-Recognition.aspx. The list
    includes some manual entries for special events and evangelism and also
    supports wiki edits (something we can probably track easily ). I agree it will
    be hard to design a system that can't be gamed, but for starters we can create
    an auto-generated top-100 contributors list without specific endorsements from
    the stewards. We can monitor it over time to see if it reflects the behavior
    we want to award.

A large part of our recognition will be around the upcoming doc sprints. We should put in place an easy system for swag for major contributions (MDN does a great job with this). Besides that, the idea of some exclusive swag and an annual awards ceremony is also good as a long-term motivator. From talking to many possible contributors, it is clear that reputation and "soft" recognition is the most valuable. An example of that is to list all contributors in a blog post that recaps a doc sprint. Do we have a blog on the site?

### <span>Achievement Recognition</span>

People should be given recognition for the skills they possess, as well as the contributions they have made to the site. So for contributions, you could have badges for

-   Q&A moderator
-   Numbers of answers in Q&A
-   IRC moderator
-   Number of new articles
-   Number of edits
-   Number of template updates
-   Translations contributed

And then for skills, you could have

-   Editor
-   Writer
-   Template expert
-   Design expert (for those like Seb and Lea, who have contributed styling)
-   International expert: Germany, or France, etc. (awarded for certain language contributions)
-   Domain expert: HTML, or CSS (you have certain specific knowledge of different subjects)
-   Doc sprint organizer / participant

This would act as recognition, as well as letting others know what skills you have, so they can determine who best to approach if they have a query or problem.

Mozilla Foundation supports the development of the [Open Badges](http://www.openbadges.org) Infrastructure, which enable issuers to define badges, and individuals to earn badges and display them to others. Badge-earners can collect badges from multiple issuers in a "back pack" to share with whomever is interested.

For WPD, open badges could be used to represent status or roles. In theory, they could also be tied into a quantitative recognition system. (But see Janet's opinion above.

Mozilla Foundation is also working on defining badges to recognize skills and achievements related to ["webmaking"](http://erinknight.com/post/29830945702/webmaker-badges). WPD may want to eventually integrate with these on the content side. However, that doesn't relate directly to how WPD might use badges for community recognition.

### <span>Peer Recognition</span>

Wikipedia and other wiki communities use ["barn stars"](https://en.wikipedia.org/wiki/Wikipedia:Barnstars) for members to recognize good work by other members. See the link for examples of the types used in the Wikipedia community. Presumably, the infrastructure for these already exists in MediaWiki. WPD would need to decide what types of awards to use.

    Janet's Opinion: The choice of peer recognition awards is best made by
    the community as it evolves, not in advance by the Stewards. However, in
    setting up the site, we can choose to ensure that it supports barnstar-type
    recognition.

    Peter's Opinion:If we have the Barnstar system in Media Wiki we
    should turn that on (who will do that?). This will encourage people creating a
    personal profile (image, about, etc.) and that is something we should probably
    encourage because contributors will then more likely return.

## <span>Other Resources</span>

-   The book "Building Successful Online Communities" makes a number of "design claims" about feedback and reward systems. *([See notes](https://www.w3.org/2011/docs/wiki/Book_Notes))*
