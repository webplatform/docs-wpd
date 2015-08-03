---
title: WPD:Admin
---
<p>There are several special pages that Stewards should know about:
</p>
<ul><li> <a href="/wiki/Special:ArticleFeedback" class="new" title="Special:ArticleFeedback (page does not exist)">The Article Feedback dashboard</a>, listing pages with highest and lowest ratings, as well as recent lows </li>
<li> <a href="/wiki/Special:AdminLinks" title="Special:AdminLinks">Special:AdminLinks</a>, which functions like a dashboard, with helpful links. This is handy for create templates. </li>
<li> <a href="/wiki/Special:Version" title="Special:Version">The Mediawiki version page</a>, including all information about our current installation, such as extensions</li>
<li> <a href="/wiki/Meta:Deployment" title="Meta:Deployment" class="mw-redirect">Mediawiki Deployment Instructions</a>, for installing extensions, adding software to the site, etc.</li>
<li> <a href="/wiki/WPD:Site_Map" title="WPD:Site Map" class="mw-redirect">Site Map</a>, including site architecture and software requirements</li>
<li> <b>?uselang=qqx</b> appended to any page give you special information about that page</li></ul>
<h2><span class="mw-headline" id="Site_Metrics">Site Metrics</span></h2>
<ul><li> <a href="/wiki/WPD:Admin/Site_Metrics" title="WPD:Admin/Site Metrics">Site Metrics</a></li>
<li> <a href="/wiki/Special:Statistics" title="Special:Statistics">Special:Statistics</a></li>
<li> <a rel="nofollow" class="external text" href="https://meta.wikimedia.org/wiki/Research:Community_portal_redesign">WikiMedia discussion on a useful community portal for Wikipedia editors</a></li></ul>
<h2><span class="mw-headline" id="Account_Creation">Account Creation</span></h2>
<p>Currently, only registered account holders can view pages on the wiki.
</p>
<ul><li> <a href="/wiki/Special:UserLogin" title="Special:UserLogin">UserLogin</a> allows <i>bureaucrats</i> to create accounts</li>
<li> <a href="/wiki/Special:RequestAccount" class="new" title="Special:RequestAccount (page does not exist)">Request Account</a> allows users to ask for an account</li>
<li> <a href="/wiki/Special:ConfirmAccounts" class="new" title="Special:ConfirmAccounts (page does not exist)">Confirm Accounts</a> allows <i>bureaucrats</i> to approve requested accounts</li>
<li> <a href="/w/index.php?title=WPD:Admin/Autoconfirm&amp;action=edit&amp;redlink=1" class="new" title="WPD:Admin/Autoconfirm (page does not exist)">Autoconfirm</a> allows Admins to override spam controls for known users</li></ul>
<h2><span class="mw-headline" id="Content_Management">Content Management</span></h2>
<ul><li> <a href="/wiki/Special:ReplaceText" class="new" title="Special:ReplaceText (page does not exist)">Special:ReplaceText</a> allows admins to search and replace across multiple pages on the wiki using regular expressions. See <a class="external text" href="http://www.mediawiki.org/wiki/Extension:Replace_Text#Usage">usage instructions</a> for more details.</li>
<li> <a href="/wiki/Special:Nuke" title="Special:Nuke">Nuke</a> allows admins to mass delete all edits by a particular user, IP address, etc.
<ul><li> <a href="/wiki/Special:Log/delete" title="Special:Log/delete">Log/delete</a> shows all pages which have been deleted</li></ul></li></ul>
<h2><span class="mw-headline" id="Miscellaneous">Miscellaneous</span></h2>
<h3><span class="mw-headline" id="Debugging">Debugging</span></h3>
<p>You can bypass fastly completely by curling directly to an app server and passing the host header; so rather than just seeing a 500, you can see an actual exception:
</p>
<pre>curl '<a rel="nofollow" class="external free" href="http://15.185.108.248/w/api.php'">http://15.185.108.248/w/api.php'</a> -H 'Host: docs.webplatform.org'
</pre>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:99-0!*!0!!*!*!*!esi=1 and timestamp 20150731181243 and revision id 100276
 -->
