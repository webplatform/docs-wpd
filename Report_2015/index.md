The WebPlatform project has thus far enjoyed a variety of important successes, through guidance from the WebPlatform project stewards and through support from the community. WebPlatform.org has made itself known to the community as ''the'' place where large-scale collaborative participation in documenting and discussing the Web platform is going to be happening—and has already successfully generated a tremendous amount good will within the community that will sustain it as it moves along to the next steps.

So it's now time to really build further on the success the project has had in the steps taken thus far—and to now take it to the next steps. And as we do that, to meet the mutual goals all its stakeholders have had since its inception, we look forward to the continued active involvement and financial support of the WebPlatform stewards—and to emerging opportunities for the stewards to become even more engaged.

We also have emerging opportunities for more direct participation from W3C members, working groups, and community participants—to leverage the close association between Web-standards specification development and technical documentation. The close tie among those is a unique advantage that the WebPlatform project provides relative to other efforts, and while we have yet to fully realize the enormous potential in that, we are poised to bring it to reality with the next steps the project will take.

== Highlights ==
The following are some highlights of successes the WebPlatform has had thus far.

* Laid the foundation for key parts of the W3C Modern Tooling effort, which will include making use of Webplatform.org as a space for experimenting with new modes of discussion around Web-platform feature development—in ways that reward more civil discussion
* Integrated and updated substantial documentation from multiple sources, and created many new articles
* Built a committed community of contributors, including new stewards who committed valuable resources
* Stabilized and expanded our server and software infrastructure, with GitHub integration and deployment

== Content ==
WebPlatform Docs set out with a goal of documenting all standardized features of the Web Platform. This is an ambitious task, but we have already tackled a significant portion of the documentation, with over 3700 reference articles and tutorials devoted exclusively to client-side technologies. There have been over 100K edits refining these articles, mostly from volunteers, but also from steward-sponsored contributors.

These topics cover every major area of the Web Platform: HTML, CSS, DOM, SVG, MathML, JavaScript, and various client-side APIs. Our approach has largely been breadth-first, with significant efforts on depth for CSS properties. The quality improvements to CSS are reflected in the traffic, with about half of the unique visits being to CSS pages.

Many of our articles originated at other sites, such as MSDN or HTML5 Rocks; most have been created or edited by our community. To address issues of quality and datedness, we have deployed a "ready-to-use" gauge for each article, called "readiness markers". We are building on this with a similar project to automatically add a notification to reference pages whenever new version of the specification it documents has been published, so readers and contributors are aware that it may need to be updated. 

We already have active editors working on basic and advanced tutorials for HTML and DOM. We also have plans for extensive SVG documentation. SVG is increasing in popularity, but it is not yet well-documented on the Web, which offers an advantage in search engine results over more mature topics.

Going forward, we plan to work more closely with W3C working groups and their mailing list participants to document features as they are being specified. By systematically identifying each new feature that is published as part of a W3C specification, we can efficiently establish what needs to be documented before the need is recognized elsewhere.

== Community ==

WebPlatform.org has established an active community, with over 250 high-volume contributors (those contributors who have each made at least 15 edits), and 42 active editors (those contributors who have contributed over the last month with little supervision). We have over 170K registered users in total.

We have been successful in our WebPlatform Doc Sprints, a series of dedicated meetups for onboarding contributors and creating or improving documentation on the site. Several community members have even held their own unsponsored Doc Sprints. We would like to continue and increase this effort.

While the contributing community is maintaining itself, the quantity and quality of contributions is better when we have a focused. We have identified a community member who will be joining our team to facilitate and increase contributor engagement.

We've developed safeguards to limit spam accounts, without compromising  ease of contribution. This has resulted in a 90% decrease in spam accounts and content, which is a serious issue for wikis.

We negotiated the contribution of the WebPlatform.com domain name from a community member, to strengthen our branding and serve as a possible additional venue, while removing a potential competitive distraction.

=== New Stewards ===

We are bringing on two new stewards, DreamHost and Internet Academy. 

Dreamhost is providing our hosting infrastructure, and technical support to develop and maintain our infrastructure. 

Internet Academy is providing not only content from their educational curriculum, but a dedicated staff member, Nishanth Babu, who is working on content creation and curation and on social media outreach.

== Infrastructure ==

In the early months of the project, the community was disrupted by frequent and lasting outages. We have solved these site stability and uptime issues, and now have greater than 99.8% uptime, due to the changes described below.

Primarily, our full-time dev-op engineer, Renoir Boulanger, has worked for the past 1.5 years on the site, and his activity has been crucial.

DreamHost has committed stable server resources for the long-term. We have migrated to these dedicated server resources, including a dedicated email relay server.

In this new home, we completely reconfigured the server infrastructure. From the ad-hoc arrangement we had before, we have created a site management system with automated and scripted deployments and problem notifications. We've developed a methodolgy for keeping our software up to date, including automatic security updates. 

Status updates are now available through Status.WebPlatform.org, and issues and priorities are now exposed through a public kanban dashboard tied to GitHub.

We also decreased impedance on community-based software contributions and upgrades. We created a staging server, with automated deployment scripts that allow community code contributions via GitHub for almost every aspect of the site, while maintaining security and privacy controls (e.g. passwords and admin privileges).

With this new infrastructure in place, we've been able to deploy site improvements much more rapidly. The site is now running under HTTPS and SSL, with advanced caching through Fastly. We have deployed a centralized accounts system (Firefox Accounts), to enable single-sign-on for our various software and services. 

Some of our major services include an automated "browser support" table generator, and an annotation system.

The browser support tables (also called "compatibility tables" are a crucial feature for a documentation site; they indicate how well a developer can expect any documented feature to work across browsers. Some documentation sites rely on hand-edited claims based on arbitrary distinctions; we have put into place an automated system that will integrate with W3C's comprehensive test-suite implementation reports. This data is also hand-editable through GitHub, for edge cases, and deploys automatically to the relevant page. We also offer an API for this information. We are continuing to work with W3C teams to closely integrate test-suite data in the near future.


== Site Traffic ==

Traffic is the biggest challenge for WebPlaform Docs.

We have fallen short of our aspirations, with the average monthly unique visitors at only 43.5K, and monthly unique pageviews at 111.6K. About half of these pageviews are for CSS topics, which we have put most of our energy into improving. Most of the rest of the traffic has been in HTML and tutorials. Notably, about 10% of our traffic has been on the well-crafted SVG tutorials. 

There are many excellent competitors, such as MDN, and many sites with long-standing SEO on mature topics such as HTML and CSS. We have not invested in any advertising or other proactive SEO, and our page-rank is not nearly as high as more mature sites.

There are two main differentiators that we need to optimize: quality of content; and scarity of content. With limited resources, we need to pick a narrow set of topics that we can excel in, and which don't have much competition. Again, we believe that SVG is one such topic, and emerging standards is another. We plan to more closely traffic patterns, and adjust our content to play to the interests of our visitors.

But beyond that, we need the advice and help of the stewards to help increase our site's traffic. 

Steward activity and community curation has dramatically decreased since October 2014. We have registered a corresponding decrease in traffic and contribution since that time, showing how important the participation of the stewards is. We did notice a strong upward trend since May 2015, increasing about 15% over the previous months, so we hope to continue that trend, and with the help of the stewards, we think we can.

== Integration with Standards ==

We are making good progress to build services that increase and tighten the relationship between technical documentation, standards work, and discussion with the development and design community.

The new [https://Specs.WebPlatform.org Specs.WebPlatform.org] subdomain meets a pressing need to provide a "working space" for lightweight experimental standards development. This provides a live view of specs from GitHub, and can be used by working groups, community groups, and individuals for early stage drafts and editor's drafts of specs on GitHub. By providing this specification hosting service, we intend to increase awareness and participation with all of WebPlatform's content and services

We have also deployed an advanced annotation system, at [https://Notes.WebPlatform.org Notes.WebPlatform.org], which lets users not only annotate the documentation, but also to annotate standards specifications (even on W3.org), to tighten the loop between the development of standards and the accessibility of documentation for those standards.

A concrete challenge in engaging developers in standards has been a friendly place to ask questions, propose features, and discuss the Web Platform. Robin Berjon, from the W3C team, launched an experimental [http://specifiction.org/ Discourse discussion forum at Specifiction.org] for this purpose, and it has been very successful in bringing new people to the table. We are migrating this service and its community to [https://Discuss.WebPlatform.org Discuss.WebPlatform.org]. This will allow the community to suggest and discuss new features for the Web Platform itself, helping increase the relevance and influence of WebPlatform.org.

== Next Steps ==

We have briefly outlined our current directions and plans, but we want to hear from the stewards what direction we should take the project. This project will not succeed without your ongoing participation. Together, we have laid solid foundations, and learned many lessons, and we hope you continue to build on that investment.

Our concrete needs for continuing at our current pace are small. We only need funding for the full-time site dev-op, and for our part-time community manager. 

However, we hope you will consider the potential benefits to increased participation. The site will grow and improve more quickly if we have additional funding for more Doc Sprints, and for advertising and SEO.

Even more important would be the active participation of tech writers, subject-matter experts, standards participants, and other staff from our stewards.