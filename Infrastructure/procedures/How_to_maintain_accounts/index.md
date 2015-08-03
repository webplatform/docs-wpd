---
title: WPD:Infrastructure/procedures/How to maintain accounts
---
<h1><span class="mw-headline" id="How_to_maintain_accounts">How to maintain accounts</span></h1>
<p>Here are a few commands we can do to check what’s happening in the accounts system
</p>
<h2><span class="mw-headline" id="Database_queries">Database queries</span></h2>
<h3><span class="mw-headline" id="Is_a_user_activated.3F">Is a user activated?</span></h3>
<pre> SELECT HEX(uid),HEX(emailCode),email,fullName FROM accounts WHERE emailVerified = 0 AND email LIKE '%@w3.org%';
</pre>
<h3><span class="mw-headline" id="Force_activation">Force activation</span></h3>
<p>This can be done by going to a specific link;
</p>
<pre> SELECT CONCAT('<a rel="nofollow" class="external free" href="https://accounts.webplatform.org/verify_email?uid='">https://accounts.webplatform.org/verify_email?uid='</a>, HEX(uid), '&amp;code=',HEX(emailCode)) FROM accounts WHERE  emailVerified = 0 AND email LIKE '%@w3.org%';
</pre>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:40737-0!*!*!!*!*!*!esi=1 and timestamp 20150731185639 and revision id 82021
 -->
