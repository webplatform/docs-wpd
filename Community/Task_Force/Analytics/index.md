=Analytics Task Force=

This group will determine the metrics for reporting the success of site visits. At a high level, we're tracking things like:

* Are people visiting?
* Is it site meeting visitor needs
** is content discoverable?
** is content optimized?
* Are people contributing?
* What feedback are they giving us?
* How is social media campaign impacting visits and contributions?

==Meetings==

See [[WPD:Community/Meetings/Analytics|Analytics Task Force meetings]]

==TOPICS==

===TOPIC: Sitemap===

====Location====

http://www.webplatform.org/sitemaps/sitemap-index-wpwiki.xml

====Human-readble version====

In progress: https://docs.google.com/spreadsheet/ccc?key=0AnXre3v9CjJXdHdKRlFZY2lRREkwVDNndDU5RWdzYnc

====Open issues====

http://project.webplatform.org/analytics/issues/3
http://project.webplatform.org/analytics/issues/2
http://project.webplatform.org/analytics/issues/1
http://project.webplatform.org/infrastructure/issues/10

====Discussion====

Submitting a sitemap to Google is dependent on Ryan extracting the portions we want to expose to crawlers, see:

http://project.webplatform.org/infrastructure/issues/10

4, 6, 14, 102, and 3000

We should put map in a user-friendly output and review site map for alignment with architecture


===TOPIC: Topic Clusters===

Topic clusters, for example: 
http://reference.sitepoint.com/css/background-color

Color and Background is topic cluster

shepazu thinks individuals should not create topic clusters and that topic cluster is only for reference pages

We have a mechanism to create a predefined topic cluster, including reference pages; natural categories; 1st we have a list of topic clusters with all the pages that go in that cluster; for each page, which clusters does it belong in?

two issues: another layer of categorization, e.g.: background, list props, box, layout...

2nd any ref or tut or concept page can be attached as well

Isn't See also  mostly a related topic cluster
… for any give topic cluster, it gets into a see-also section

shepazu: to get clarity on how to cluster, don't add more URL nodes

shepazu: it should be fairly easy to do. the actual HTML should come from a special page, when passed parameters

then the parser tag would output the ESI, pointing to the special page

===TOPIC: Analytics report===

A Report / Overview page that bubbles up to general meeting


scottrowe_ wants summary of DocSprints: e.g.: this attendee touch these pages -- what were the individual contributions

Have it be persistent - we lost data because we didn't go to the recent pages changes soon enough

Would be great to have the data grabbed and encapsulated

Also nice to have this in relation to other campaigns

what limits did Scott run into when trying to get the data?

scottrowe: MW only let's you see up to 1000 pages

You can force it to give you 1K by changing the value in the URL

1K was only 3 hours of the Doc Sprint

… Ryan said you could do so with DB queries
… but it's expensive

==TOPIC: campaign tracking & segmentation==

patrickdsouza: add campaign tracking to pages before Doc Sprint, etc.

patrickdsouza: we can compare different campaigns
set a "docsprint" property on a page, and ID that page

==ACTIONS==

* Julee to use sitemap to update [[WPD:Content/Topic_Hierarchy|Topic hierarchy]]
* Make it clear that all promo emails should go out with piwik campaign #
* shepazu: submit Sitemap to google.
* Julee to doc site based on site map in topic_hierarchy page
* scottrowe_to lead review of sitemap as it relates to overall hierarchy, especially as relates to the DOM API and maybe other things like topic clusters
* shepazu & scottrowe_ or organize discussion around topic clusters

==Contributors==
* Doug
* Patrick
* Scott
* Julee

==Projects==
Here's what we're working on.

===Bug Genie and WPDS Dashboard integration===
Need to provide.