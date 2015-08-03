---
title: WPD:Community/Contributor Recognition
---
<h2><span class="mw-headline" id="Types_of_Contributor_Recognition_Systems">Types of Contributor Recognition Systems</span></h2>
<p>There are at least three types of recognition systems for community sites:
</p>
<ul><li> Quantitative recognition: Automated tracking and display of contribution statistics, such as (for a wiki) number of edits, number of words, length of membership.</li>
<li> Achievement recognition: Acknowledgement by some entity (organization, usually) that someone has met defined criteria of achievement. Think: Boy Scout or Girl Scout badges.</li>
<li> Peer recognition: Acknowledgement by an individual of a contribution (singular or aggregate) by another individual in a community.</li></ul>
<h3><span class="mw-headline" id="Quantitative_Recognition">Quantitative Recognition</span></h3>
<p>MDN has not used quantitative recognition at all; they intend to add such features, but have not yet sketched a design.
</p><p>The <a rel="nofollow" class="external text" href="https://support.mozilla.org/en-US/forums">Mozilla Support discussion forums</a> display the number of posts that a user has made, under their name on a post; their profile shows the number of:
</p>
<ul><li> questions asked</li>
<li> answers given</li>
<li> solutions given (i.e., selected by the questioner as the best response)</li></ul>
<p>These are very basic stats, but give an indication of how long/much someone has been around, and how helpful they are. Many other sites use this type of recognition, and may define various user "levels" (e.g., "rookie" up to "MVP") based on contribution stats.
</p>
<pre><i><b>Janet's Opinion:</b> Quantitative recognition systems are challenging to </i>
design, because you need to be sure that the behaviors you recognize (and 
therefore implicitly reward) are actually desirable in the community, and not 
easily "gamed" with non-constructive activity. StackOverflow has an extremely 
well-designed system in this regard. But I'm highly skeptical of most 
recognition systems promoted under the buzzword of "gamification".
</pre>
<p>A rather elaborate system for quantitative recognition was developed at Sun by Peter Reiser and others, called <a rel="nofollow" class="external text" href="http://kenai.com/projects/community-equity">"Community Equity"</a> (<a rel="nofollow" class="external text" href="http://www.slideshare.net/peterreiser/community-equity-overview-2419832">slides</a>). It aggregates various kinds of quantitative measures of contribution into a single score, which is intended to be portable across systems that use the algorithm. Sun both open-sourced the implementation (which is in Java, of course) and patented it. <i><b>Janet's Opinion:</b> I think the patent was intended to be defensive, but I have no idea how Oracle regards it.</i>
</p>
<pre><i><b>Peter's Opinion</b></i>: There are good systems in place for forums that 
award for posting answers and we can get an off-the-shelf solution or 
extension for that if we have a forum on webplatform.org (are we going to?). 
In addition, rewards for other categories can be added. For an example of the  
different activities and associated awards, take a look at 
<a rel="nofollow" class="external free" href="http://www.dotnetnuke.com/Community/Community-Recognition.aspx">http://www.dotnetnuke.com/Community/Community-Recognition.aspx</a>. The list 
includes some manual entries for special events and evangelism and also 
supports wiki edits (something we can probably track easily ). I agree it will 
be hard to design a system that can't be gamed, but for starters we can create 
an auto-generated top-100 contributors list without specific endorsements from 
the stewards. We can monitor it over time to see if it reflects the behavior 
we want to award.
</pre>
<p>A large part of our recognition will be around the upcoming doc sprints. We should put in place an easy system for swag for major contributions (MDN does a great job with this). Besides that, the idea of some exclusive swag and an annual awards ceremony is also good as a long-term motivator. From talking to many possible contributors, it is clear that reputation and "soft" recognition is the most valuable. An example of that is to list all contributors in a blog post that recaps a doc sprint. Do we have a blog on the site?
</p>
<h3><span class="mw-headline" id="Achievement_Recognition">Achievement Recognition</span></h3>
<p>People should be given recognition for the skills they possess, as well as the contributions they have made to the site. So for contributions, you could have badges for 
</p>
<ul><li> Q&amp;A moderator</li>
<li> Numbers of answers in Q&amp;A</li>
<li> IRC moderator</li>
<li> Number of new articles</li>
<li> Number of edits</li>
<li> Number of template updates</li>
<li> Translations contributed</li></ul>
<p>And then for skills, you could have
</p>
<ul><li> Editor</li>
<li> Writer</li>
<li> Template expert</li>
<li> Design expert (for those like Seb and Lea, who have contributed styling)</li>
<li> International expert: Germany, or France, etc. (awarded for certain language contributions)</li>
<li> Domain expert: HTML, or CSS (you have certain specific knowledge of different subjects)</li>
<li> Doc sprint organizer / participant</li></ul>
<p>This would act as recognition, as well as letting others know what skills you have, so they can determine who best to approach if they have a query or problem.
</p><p>Mozilla Foundation supports the development of the <a rel="nofollow" class="external text" href="http://www.openbadges.org">Open Badges</a> Infrastructure, which enable issuers to define badges, and individuals to earn badges and display them to others. Badge-earners can collect badges from multiple issuers in a "back pack" to share with whomever is interested.
</p><p>For WPD, open badges could be used to represent status or roles. In theory, they could also be tied into a quantitative recognition system. (But see Janet's opinion above.
</p><p>Mozilla Foundation is also working on defining badges to recognize skills and achievements related to <a rel="nofollow" class="external text" href="http://erinknight.com/post/29830945702/webmaker-badges">"webmaking"</a>. WPD may want to eventually integrate with these on the content side. However, that doesn't relate directly to how WPD might use badges for community recognition.
</p>
<h3><span class="mw-headline" id="Peer_Recognition">Peer Recognition</span></h3>
<p>Wikipedia and other wiki communities use <a rel="nofollow" class="external text" href="https://en.wikipedia.org/wiki/Wikipedia:Barnstars">"barn stars"</a> for members to recognize good work by other members. See the link for examples of the types used in the Wikipedia community. Presumably, the infrastructure for these already exists in MediaWiki. WPD would need to decide what types of awards to use. 
</p>
<pre><i><b>Janet's Opinion:</b> The choice of peer recognition awards is best made by </i>
the community as it evolves, not in advance by the Stewards. However, in 
setting up the site, we can choose to ensure that it supports barnstar-type 
recognition.
</pre>
<pre><i><b>Peter's Opinion</b></i>:If we have the Barnstar system in Media Wiki we 
should turn that on (who will do that?). This will encourage people creating a 
personal profile (image, about, etc.) and that is something we should probably 
encourage because contributors will then more likely return.
</pre>
<h2><span class="mw-headline" id="Other_Resources">Other Resources</span></h2>
<ul><li> The book "Building Successful Online Communities" makes a number of "design claims" about feedback and reward systems. <i>(<a rel="nofollow" class="external text" href="https://www.w3.org/2011/docs/wiki/Book_Notes">See notes</a>)</i></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.019 seconds
Real time usage: 0.020 seconds
Preprocessor visited node count: 18/1000000
Preprocessor generated node count: 24/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:319-0!*!*!!*!*!*!esi=1 and timestamp 20150731103902 and revision id 23010
 -->
