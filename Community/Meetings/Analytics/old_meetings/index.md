---
title: 'old meetings'
uri: 'WPD:Community/Meetings/Analytics/old meetings'

---
## Agenda 2013-04-26

-   Collapse search project into this one?
-   Are these all the projects we're working on: [Projects](/WPD:Community/Task_Force/Analytics#Projects)

## Agenda 2013-04-19

## DISCUSSION

### TOPIC: topic hierarchy

Did a sitemap inventory here: <https://docs.google.com/spreadsheet/ccc?key=0AnXre3v9CjJXdHdKRlFZY2lRREkwVDNndDU5RWdzYnc>

CORS is not supported. Will try JSONP

### TOPIC: how do we address bad URLs?

Can't do it in the MW.

 Original vision: if user types keyword, and keyword isn't in system, prompts user for better options; a manner of spell checker, even soft matches; Can't do it in the MW.

 patrickdsouza: can run xml files through a spell checker

ACTION: patrickdsouza to file a bug and test this theory

What about the new URL structure?

 we need to define a new taxonomy

… currently no differentiation, but wouldn't be reflected in URL

There's a bug for ryan to do a chron job which would update the site map. When we fix the page, the sitemap will be correct.

When will Ryan get to it?

 ACTION: Julee to follow up with Ryan on chron job.

### TOPIC: Update piwik?

when can piwik update happen?

Boston's locked down, so Denis may not be available.

 Make it clear that all promo emails should go out with piwik campaign \#

 patrickdsouza: we have two campaigns set up: html5weekly and adobe dev connection.

### TOPIC: google sitemap

did you look at google webmaster to see if site map is being indexed?

35K impressions! 2500 clicks

shepazu: sitemap is pending

<https://www.google.com/webmasters/tools/user-admin?hl=en&siteUrl=http://webplatform.org/>

<https://www.google.com/webmasters/tools/dashboard?hl=en&siteUrl=http://webplatform.org/>

… give access to webmaster.google when someone asks

… promo when page view numbers jump to 5K

### TOPIC: ads?

for preferred landing pages...

evergreen content (evergreen: like the questions asked in an interview. so it's always going to be searched. But if you have a specific need to promo it, then pay for it)

Do do social media campaigns for Seasonal is hot topics, buzz words, new features doc'd or implemented

But we should work on organic first.

## TOPIC: Doug's great idea=

DNTrack -\> site -\> notice to join JS project.

This topic moved to communications & recruiting

 1. blog re: MSDN JS;

… 2. pop-up or drop down -- our our alpha alert: here's the current project and read this blog post for more info

… 3. "do not track" and DRM tech page

… 4. post it on reddit

They'll get the pop-up for JS and get involved!

...3.a.: blog post: count on us to be neutral

    vet with key stakeholders

### TOPIC: Search results are improved!

search results are looking better; denis did some work

Whoa!! <http://docs.webplatform.org/w/index.php?search=font-size&fulltext=+&title=Special%3ASearch>

## ACTION ITEMS

-   email doug with our google id
-   shepazu: submit Sitemap to google. [DONE]
-   Julee to use sitemap to update Topic hierarchy (in progress: <http://docs.webplatform.org/wiki/WPD:Editors_Guide/Topic_Hierarchy>)
-   shepazu to follow up with Denis on piwik update, and update bug with completion date.
-   Julee to update bug to ryan: site map can't have \*.gz, master must point to xml files (DONE)
-   Make it clear that all promo emails should go out with piwik campaign \#
-   in Piwik: remove ADC and keep html5weekly; add university, "news" email list, and for each social media channel, our blog, steward co. site posts, doc sprints, to id docs that were edited
-   shepazu: JS post Monday, alert update, drm content, then notify patrick

## Agenda 2013-04-12

## TOPICS

### TOPIC: Sitemap

#### Location

<http://www.webplatform.org/sitemaps/sitemap-index-wpwiki.xml>

#### Human-readble version

In progress: <https://docs.google.com/spreadsheet/ccc?key=0AnXre3v9CjJXdHdKRlFZY2lRREkwVDNndDU5RWdzYnc>

#### Open issues

<http://project.webplatform.org/analytics/issues/3> <http://project.webplatform.org/analytics/issues/2> <http://project.webplatform.org/analytics/issues/1> <http://project.webplatform.org/infrastructure/issues/10>

#### Discussion

Submitting a sitemap to Google is dependent on Ryan extracting the portions we want to expose to crawlers, see:

<http://project.webplatform.org/infrastructure/issues/10>

sitemap-wpwiki-NS\_0-0, sitemap-wpwiki-NS\_6-0, sitemap-wpwiki-NS\_14-0, sitemap-wpwiki-NS\_102-0, and sitemap-wpwiki-NS\_3000-0

We should put map in a user-friendly output and review site map for alignment with architecture

### TOPIC: Topic Clusters

Topic clusters, for example: <http://reference.sitepoint.com/css/background-color>

Color and Background is topic cluster

shepazu thinks individuals should not create topic clusters and that topic cluster is only for reference pages

We have a mechanism to create a predefined topic cluster, including reference pages; natural categories; 1st we have a list of topic clusters with all the pages that go in that cluster; for each page, which clusters does it belong in?

two issues: another layer of categorization, e.g.: background, list props, box, layout...

2nd any ref or tut or concept page can be attached as well

Isn't See also mostly a related topic cluster … for any give topic cluster, it gets into a see-also section

shepazu: to get clarity on how to cluster, don't add more URL nodes

shepazu: it should be fairly easy to do. the actual HTML should come from a special page, when passed parameters

then the parser tag would output the ESI, pointing to the special page

### TOPIC: Analytics report

A Report / Overview page that bubbles up to general meeting

 scottrowe\_ wants summary of DocSprints: e.g.: this attendee touch these pages -- what were the individual contributions

Have it be persistent - we lost data because we didn't go to the recent pages changes soon enough

Would be great to have the data grabbed and encapsulated

Also nice to have this in relation to other campaigns

what limits did Scott run into when trying to get the data?

scottrowe: MW only let's you see up to 1000 pages

You can force it to give you 1K by changing the value in the URL

1K was only 3 hours of the Doc Sprint

… Ryan said you could do so with DB queries … but it's expensive

## TOPIC: campaign tracking & segmentation

patrickdsouza: add campaign tracking to pages before Doc Sprint, etc.

patrickdsouza: we can compare different campaigns set a "docsprint" property on a page, and ID that page

## ACTIONS

-   Julee to use sitemap to update [Topic hierarchy](/WPD:Content/Topic_Hierarchy)
-   Make it clear that all promo emails should go out with piwik campaign \#
-   shepazu: submit Sitemap to google.
-   scottrowe\_to lead review of sitemap as it relates to overall hierarchy, especially as relates to the DOM API and maybe other things like topic clusters
-   shepazu & scottrowe\_ or organize discussion around topic clusters
