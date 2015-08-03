---
title: WPD:Projects/spec status representation
---
<h1><span class="mw-headline" id="Representing_the_status_of_a_spec">Representing the status of a spec</span></h1>
<p>One problem we currently have on WebPlatform is that we lack a decent representation of how usable a feature is in the real world. Currently we show an entry for W3C spec status at the top of each feature's page, and we also have a section further down called "Related specifications", which shows what specifications the feature is defined in, what W3C rec level these are at, etc. See <a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/css/properties/font-size">http://docs.webplatform.org/wiki/css/properties/font-size</a> for an example
</p><p>The problem is that recommendation status is not immediately useful to the average developer on the street, who just wants to know if they can use this feature in their real world projects now. There are plenty of features defined in W3C recommendations that are not supported across all browsers! The current way  of doing things is also repetitious.
</p><p>These pieces of data are related, but definitely separate.
</p>
<h2><span class="mw-headline" id="A_potential_solution">A potential solution</span></h2>
<p>So we need a solution that will fulfil both aims:
</p>
<ol><li> Give developers a definite measure of whether they can use a feature now in their production work</li>
<li> Inform developers as to what specs the feature is defined in, so they can find out more information from the specs if needed</li></ol>
<p>I think the current page features we have in place solve number 2 nicely, but I think we should get rid of the W3C spec status that appears at the top of the page. It is repetitious, and looks fugly!
</p><p>For number 1, I think we should have an easily defined metric that indicates whether developers should and could use each feature now. This should go up the top of each page, in the same place that the W3C rec status currently is (or perhaps as an entry in the details table just below that). We should use a nice bedging system like they use on <a rel="nofollow" class="external free" href="http://html5please.com/">http://html5please.com/</a>
</p><p>I would call it something like
</p>
<ul><li> canuse?</li>
<li> stability</li>
<li> production ready?</li></ul>
<p>And the values I'd give it are as follows:
</p>
<ul><li> "Proprietary: Used in XXXX" (where XXXX is the proprietary browser feature. So for example "Used in Chrome extensions" or "Used in styling Windows 8 apps")</li>
<li> "Avoid" (where the feature is only supported across one or two browsers, and/or no easy way of Polyfilling or fallback exists and/or the spec is unstable so the syntax is likely to change 4 times in the next 3 months)</li>
<li> "Use with polyfill" (where the feature is supported across all modern browsers, and polyfills exist for providing support in older browsers)</li>
<li> "Use with fallback" (where the feature is supported across all modern browsers, and it is easy to create a fallback for older browsers, and/or the feature gracefully degrades)</li>
<li> "Use" (the feature is as old as the hills, and supported everywhere)</li></ul>
<p>So in this classification, we are not explicitly saying anything about a feature's spec status or stability, just if it is usable now or not. Stability, etc. can be gotten from the related specs. If we wanted to give more details, we could give a further info box where we can say why the feature is "Avoid" or "Use with Polyfill". A link to the Polyfill might be nice in the latter case. 
</p><p>Related bug: <a rel="nofollow" class="external free" href="https://www.w3.org/Bugs/Public/show_bug.cgi?id=20386">https://www.w3.org/Bugs/Public/show_bug.cgi?id=20386</a>
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:7565-0!*!*!!*!*!*!esi=1 and timestamp 20150731183708 and revision id 29272
 -->
