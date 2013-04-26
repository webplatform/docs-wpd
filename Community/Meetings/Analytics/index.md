=Analytics Task Force Meeting=

'''Time:''' Fridays, 19:00 UTC / 14:00 ET / 11:00 PT. 

'''Zakim Bridge:''' +1.617.761.6200

'''Conference code:''' 3627 ("DOCS") 

'''VOIP:'''  sip:zakim@w3.org

'''IRC Channel:''' webplatform-site

See [[WPD:Community/Task_Force/Analytics|Anaytics]] task force page for more information.

==Agenda 2013-04-26==

* Collapse search project into this one?

==Agenda 2013-04-19==
==DISCUSSION==

===TOPIC: topic hierarchy===

Did a sitemap inventory here: https://docs.google.com/spreadsheet/ccc?key=0AnXre3v9CjJXdHdKRlFZY2lRREkwVDNndDU5RWdzYnc

CORS is not supported. Will try JSONP

===TOPIC: how do we address bad URLs?===

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

===TOPIC: Update piwik?===

when can piwik update happen?

Boston's locked down, so Denis may not be available.


Make it clear that all promo emails should go out with piwik campaign #


patrickdsouza: we have two campaigns set up: html5weekly and adobe dev connection.

===TOPIC: google sitemap===

did you look at google webmaster to see if site map is being indexed?

35K impressions! 2500 clicks

shepazu: sitemap is pending

https://www.google.com/webmasters/tools/user-admin?hl=en&siteUrl=http://webplatform.org/

https://www.google.com/webmasters/tools/dashboard?hl=en&siteUrl=http://webplatform.org/

… give access to webmaster.google when someone asks

… promo when page view numbers jump to 5K

===TOPIC: ads?===

for preferred landing pages...

evergreen content (evergreen: like the questions asked in an interview. so it's always going to be searched. But if you have a specific need to promo it, then pay for it)

Do do social media campaigns for Seasonal is hot topics, buzz words, new features doc'd or implemented

But we should work on organic first.

==TOPIC: Doug's great idea===

DNTrack -> site -> notice to join JS project.

This topic moved to communications & recruiting


1. blog re: MSDN JS;

… 2. pop-up or drop down -- our our alpha alert: here's the current project and read this blog post for more info

… 3. "do not track" and DRM tech page

… 4. post it on reddit

They'll get the pop-up for JS and get involved!

...3.a.: blog post: count on us to be neutral

 vet with key stakeholders

===TOPIC: Search results are improved!===

search results are looking better; 
denis did some work

Whoa!! http://docs.webplatform.org/w/index.php?search=font-size&fulltext=+&title=Special%3ASearch


==ACTION ITEMS==
* email doug with our google id
* shepazu: submit Sitemap to google. [DONE]
* Julee to use sitemap to update Topic hierarchy (in progress: http://docs.webplatform.org/wiki/WPD:Editors_Guide/Topic_Hierarchy)
* shepazu to follow up with Denis on piwik update, and update bug with completion date.
* Julee to update bug to ryan: site map can't have *.gz, master must point to xml files (DONE)
* Make it clear that all promo emails should go out with piwik campaign #
* in Piwik: remove ADC and keep html5weekly; add university, "news" email list, and for each social media channel, our blog, steward co. site posts, doc sprints, to id docs that were edited
*  shepazu: JS post Monday, alert update, drm content, then notify patrick