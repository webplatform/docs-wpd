==Types of Contributor Recognition Systems==
There are at least three types of recognition systems for community sites:

* Quantitative recognition: Automated tracking and display of contribution statistics, such as (for a wiki) number of edits, number of words, length of membership.
* Achievement recognition: Acknowledgement by some entity (organization, usually) that someone has met defined criteria of achievement. Think: Boy Scout or Girl Scout badges.
* Peer recognition: Acknowledgement by an individual of a contribution (singular or aggregate) by another individual in a community.

===Quantitative Recognition===
MDN has not used quantitative recognition at all; they intend to add such features, but have not yet sketched a design.

The [https://support.mozilla.org/en-US/forums Mozilla Support discussion forums] display the number of posts that a user has made, under their name on a post; their profile shows the number of:
* questions asked
* answers given
* solutions given (i.e., selected by the questioner as the best response)
These are very basic stats, but give an indication of how long/much someone has been around, and how helpful they are. Many other sites use this type of recognition, and may define various user "levels" (e.g., "rookie" up to "MVP") based on contribution stats.

'''''Janet's Opinion:''' Quantitative recognition systems are challenging to design, because you need to be sure that the behaviors you recognize (and therefore implicitly reward) are actually desirable in the community, and not easily "gamed" with non-constructive activity. StackOverflow has an extremely well-designed system in this regard. But I'm highly skeptical of most recognition systems promoted under the buzzword of "gamification".''

A rather elaborate system for quantitative recognition was developed at Sun by Peter Reiser and others, called [http://kenai.com/projects/community-equity "Community Equity"] ([http://www.slideshare.net/peterreiser/community-equity-overview-2419832 slides]). It aggregates various kinds of quantitative measures of contribution into a single score, which is intended to be portable across systems that use the algorithm. Sun both open-sourced the implementation (which is in Java, of course) and patented it. '''''Janet's Opinion:''' I think the patent was intended to be defensive, but I have no idea how Oracle regards it.''

===Achievement Recognition===

Mozilla Foundation supports the development of the [http://www.openbadges.org Open Badges] Infrastructure, which enable issuers to define badges, and individuals to earn badges and display them to others. Badge-earners can collect badges from multiple issuers in a "back pack" to share with whomever is interested.

For WPD, open badges could be used to represent status or roles. In theory, they could also be tied into a quantitative recognition system. (But see Janet's opinion above.

Mozilla Foundation is also working on defining badges to recognize skills and achievements related to [http://erinknight.com/post/29830945702/webmaker-badges "webmaking"]. WPD may want to eventually integrate with these on the content side. However, that doesn't relate directly to how WPD might use badges for community recognition.

===Peer Recognition===
Wikipedia and other wiki communities use [https://en.wikipedia.org/wiki/Wikipedia:Barnstars "barn stars"] for members to recognize good work by other members. See the link for examples of the types used in the Wikipedia community. Presumably, the infrastructure for these already exists in MediaWiki. WPD would need to decide what types of awards to use. 

'''''Janet's Opinion:''' The choice of peer recognition awards is best made by the community as it evolves, not in advance by the Stewards. However, in setting up the site, we can choose to ensure that it supports barnstar-type recognition.''

==Other Resources==
* The book "Building Successful Online Communities" makes a number of "design claims" about feedback and reward systems.