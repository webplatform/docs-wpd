---
title: WPD:Infrastructure/procedures/When The Bug Genie mailing queue is broken
---
<h1><span class="mw-headline" id="When_The_Bug_Genie_mailing_queue_is_broken">When The Bug Genie mailing queue is broken</span></h1>
<h2><span class="mw-headline" id="Issue_1:_When_message_arent_sent_due_to_unserialize.28.29">Issue 1: When message arent sent due to unserialize()</span></h2>
<h3><span class="mw-headline" id="Finding_the_issue">Finding the issue</span></h3>
<p>The mailing queue from TheBugGenie happened to be broken. The issue was not noticed until a maintenance check made me run the cronjob and to see an error message such as.
</p><p><code>
</p>
<pre> renoirb@project5:~$ php /srv/webplatform/buggenie/tbg_cli mailing:process_mail_queue --limit=20
 Processing mail queue ... 
 The following notice has stopped further execution:
 
 unserialize(): Error at offset 1931 of 1938 bytes
 occured in
 /srv/webplatform/buggenie/modules/mailing/classes/B2DB/TBGMailQueueTable.class.php, line 61
 
 Backtrace:
 unserialize() /srv/webplatform/buggenie/modules/mailing/classes/B2DB/TBGMailQueueTable.class.php, line 61
 TBGMailQueueTable-&gt;getQueuedMessages()
 /srv/webplatform/buggenie/modules/mailing/classes/cli/CliMailingProcessMailQueue.class.php, line 50
 CliMailingProcessMailQueue-&gt;do_execute()
 /srv/webplatform/buggenie/core/classes/TBGCliCommand.class.php, line 52
 TBGCliCommand-&gt;execute()
 /srv/webplatform/buggenie/tbg_cli, line 102
 
 SQL queries:
 (1) [1.6ms] from /srv/webplatform/buggenie/core/classes/B2DB/TBGScopesTable.class.php, line 100:
</code>
</pre>
<p>The error lies in:
</p><p><code>
</p>
<pre> unserialize(): Error at offset 1931 of 1938 bytes
</pre>
<p></code>
</p><p>The code in <tt>/srv/webplatform/buggenie/modules/mailing/classes/B2DB/TBGMailQueueTable.class.php</tt> at line 61 says is within a <tt>while</tt> loop:
</p><p><code>
</p>
<pre> if($res)
 {
   while ($row = $res-&gt;getNextRow())
   {
       $message = $row-&gt;get(self::MESSAGE);
       $messages[$row-&gt;get(self::ID)] = unserialize($message);  // &lt;-- HERE
   }
 }
</pre>
<p></code>
</p><p>After checking the database server and reading queries, I could see the serialization from the database column in question:
</p><p><code>
    O:11:&quot;TBGMimemail&quot;:24:{s:10:&quot; * charset&quot;;s:5:&quot;utf-8&quot;;s:18:&quot; * default_message&quot;;s:138:&quot;&lt;!DOCTYPE HTML PUBLIC &quot;-//W3C//DTD HTML 4.0 Transitional//EN&quot;&gt;&lt;html&gt;&lt;title&gt;The Bug Genie email&lt;/title&gt;&lt;body&gt;Empty message...&lt;/body&gt;&lt;/html&gt;&quot;;s:7:&quot; * from&quot;;a:2 {s:4:&quot;name&quot;;s:32:&quot;WebPlatform Docs Project manager&quot;;s:7:&quot;address&quot;;s:31:&quot;aaaaaaaaaaaaaaaaaaaaaaa@aa.org&quot;;}s:5:&quot; * to&quot;;a:1:{i:0;a:2 {s:4:&quot;name&quot;;s:5:&quot;Aaaaa&quot;;s:7:&quot;address&quot;;s:15:&quot;jjjjj@bbbbb.jjj&quot;;}}s:5:&quot; * cc&quot;;a:0:{}s:6:&quot; * bcc&quot;;a:0:{}s:15:&quot; * replacements&quot;;a:5 {s:17:&quot;%thebuggenie_url%&quot;;s:30:&quot;http://project.webplatform.org&quot;;s:24:&quot;%link_to_reset_password%&quot;;s:0:&quot;&quot;;s:18:&quot;%link_to_activate%&quot;;s:0:&quot;&quot;;s:16:&quot;%user_buddyname%&quot;;s:5:&quot;Aaaaa&quot;;s:15:&quot;%user_username%&quot;;s:5:&quot;Aaaaa&quot;;}s:7:&quot; * sep1&quot;;s:23:&quot;_1_3233387863387136356c&quot;;s:7:&quot; * sep2&quot;;s:23:&quot;_2_75617135695636503979&quot;;s:10:&quot; * headers&quot;;a:8:{s:8:&quot;X-Mailer&quot;;s:3:&quot;TBG&quot;;s:7:&quot;Subject&quot;;s:73:&quot;Re: [dabblet] Bug report #8 - Cannot save nor save-as gists (500s &amp; 422s)&quot;;s:4:&quot;Date&quot;;s:31:&quot;Wed, 02 Oct 2013 19:25:15 +0000&quot;;s:12:&quot;MIME-Version&quot;;s:3:&quot;1.0&quot;;s:10:&quot;Message-ID&quot;;s:49:&quot;&lt;_1_3233387863387136356c@project.webplatform.org&gt;&quot;;s:4:&quot;From&quot;;s:66:&quot;WebPlatform Docs Project manager &lt;aaaaaaaaaaaaaaaaaaaaaaa@aa.org&gt;&quot;;s:11:&quot;Return-Path&quot;;s:33:&quot;&lt;aaaaaaaaaaaaaaaaaaaaaaa@aa.org&gt;&quot;;s:2:&quot;To&quot;;s:25:&quot;&quot;Aaaaa&quot; &lt;jjjjj@bbbbb.jjj&gt;&quot;;}s:10:&quot; * subject&quot;;s:73:&quot;Re: [dabblet] Bug report #8 - Cannot save nor save-as gists (500s &amp; 422s)&quot;;s:21:&quot; * subject_translated&quot;;N;s:11:&quot; * template&quot;;s:11:&quot;issueupdate&quot;;s:22:&quot; * template_parameters&quot;;a:3:{s:5:&quot;issue&quot;;O:8:&quot;TBGIssue&quot;:72:{s:9:&quot; * _title&quot;;s:43:&quot;Cannot save nor save-as gists (500s &amp; 422s)&quot;;s:9:&quot; * _links&quot;;N;s:9:&quot; * _files&quot;;a:1:{i:14;O:7:&quot;TBGFile&quot;:10:{s:16:&quot; * _content_type&quot;;s:9:&quot;image/png&quot;;s:15:&quot; * _uploa
ded_by&quot;;N;s:15:&quot; * _uploaded_at&quot;;s:10:&quot;1380741825&quot;;s:17:&quot; * _real_filename&quot;;s:55:&quot;116_1380741825_Screen Shot 2013-10-02 at 3.28.14 PM.png&quot;;s:8:&quot; * _name&quot;;s:40:&quot;Screen Shot 2013-10-02 at 3.28.14 PM.png&quot;;s:11:&quot; * _content&quot;;s:77032:&quot;
</code>
</p><p><b>NOTE</b>: The data shown here has been anonymized. But the length of the values were kept intact.
</p><p>While trying to use PHP unserialize the field we get the same error we had in the previous stack trace:
</p><p><code>
</p>
<pre> unserialize(): Error at offset 1931 of 1938 bytes
</pre>
<p></code>
</p><p>This means that the class <tt>TBGMimemail</tt> will be unserialized with this data but the unserialized data seems to have something broken.
</p><p><br />
</p>
<h3><span class="mw-headline" id="To_fix_the_issue">To fix the issue</span></h3>
<ol><li> Ensure no cron job will be running on server running The Bug Genie</li>
<li> Run manually the <tt>mailing:process_mail_queue</tt> command until you are sure the next message is the broken one</li></ol>
<p><code>
</p>
<pre>   php /srv/webplatform/buggenie/tbg_cli mailing:process_mail_queue --limit=20
</pre>
<p></code>
</p>
<ol><li> When you are at <tt>--limit=1</tt> and it breaks, it means its the broken one</li>
<li> Add those lines before the loop, before <tt>if($res){</tt>:</li></ol>
<p><code>
</p>
<pre>   $hack = TBGMimemail::createNewFromMessage('Borken message hack', 'passing around, sorry for that', null, array('my_own@gmail.com'));
   $hack-&gt;setFrom('renoirb@project1.dho.wpdn');
</pre>
<p></code>
</p>
<ol><li> Replace the part <tt>unserialize($message); </tt> with <tt>$hack</tt></li></ol>
<p><code>
</p>
<pre> // Put the hack like so:
 $hack = TBGMimemail::createNewFromMessage('Borken message hack', 'passing around, sorry for that', null, array('my_own@gmail.com'));
 $hack-&gt;setFrom('renoirb@project1.dho.wpdn');
 if($res)
 {
   while ($row = $res-&gt;getNextRow())
   {
       $message = $row-&gt;get(self::MESSAGE);
       $messages[$row-&gt;get(self::ID)] = $hack;
       //$messages[$row-&gt;get(self::ID)] = unserialize($message);
   }
 }
</pre>
<p></code>
</p>
<ol><li> Run the <tt>mailing:process_mail_queue</tt> manually, the email should pass</li>
<li> Comment the <tt>$hack</tt> and uncomment the real code.</li>
<li> Make sure all the queue is processed</li></ol>

<!-- 
NewPP limit report
CPU time usage: 0.016 seconds
Real time usage: 0.017 seconds
Preprocessor visited node count: 23/1000000
Preprocessor generated node count: 40/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:16016-0!*!*!!*!*!*!esi=1 and timestamp 20150731041513 and revision id 46760
 -->
