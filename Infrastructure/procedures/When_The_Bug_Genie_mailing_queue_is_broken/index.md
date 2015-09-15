---
title: When The Bug Genie mailing queue is broken
uri: 'WPD:Infrastructure/procedures/When The Bug Genie mailing queue is broken'

---
## <span>Issue 1: When message arent sent due to unserialize()</span>

### <span>Finding the issue</span>

The mailing queue from TheBugGenie happened to be broken. The issue was not noticed until a maintenance check made me run the cronjob and to see an error message such as.

     renoirb@project5:~$ php /srv/webplatform/buggenie/tbg_cli mailing:process_mail_queue --limit=20
     Processing mail queue ...
     The following notice has stopped further execution:

     unserialize(): Error at offset 1931 of 1938 bytes
     occured in
     /srv/webplatform/buggenie/modules/mailing/classes/B2DB/TBGMailQueueTable.class.php, line 61

     Backtrace:
     unserialize() /srv/webplatform/buggenie/modules/mailing/classes/B2DB/TBGMailQueueTable.class.php, line 61
     TBGMailQueueTable->getQueuedMessages()
     /srv/webplatform/buggenie/modules/mailing/classes/cli/CliMailingProcessMailQueue.class.php, line 50
     CliMailingProcessMailQueue->do_execute()
     /srv/webplatform/buggenie/core/classes/TBGCliCommand.class.php, line 52
     TBGCliCommand->execute()
     /srv/webplatform/buggenie/tbg_cli, line 102

     SQL queries:
     (1) [1.6ms] from /srv/webplatform/buggenie/core/classes/B2DB/TBGScopesTable.class.php, line 100:

The error lies in:

     unserialize(): Error at offset 1931 of 1938 bytes

The code in `/srv/webplatform/buggenie/modules/mailing/classes/B2DB/TBGMailQueueTable.class.php` at line 61 says is within a `while` loop:

     if($res)
     {
       while ($row = $res->getNextRow())
       {
           $message = $row->get(self::MESSAGE);
           $messages[$row->get(self::ID)] = unserialize($message);  // <-- HERE
       }
     }

After checking the database server and reading queries, I could see the serialization from the database column in question:

`     O:11:"TBGMimemail":24:{s:10:" * charset";s:5:"utf-8";s:18:" * default_message";s:138:"<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN"><html><title>The Bug Genie email</title><body>Empty message...</body></html>";s:7:" * from";a:2 {s:4:"name";s:32:"WebPlatform Docs Project manager";s:7:"address";s:31:"aaaaaaaaaaaaaaaaaaaaaaa@aa.org";}s:5:" * to";a:1:{i:0;a:2 {s:4:"name";s:5:"Aaaaa";s:7:"address";s:15:"jjjjj@bbbbb.jjj";}}s:5:" * cc";a:0:{}s:6:" * bcc";a:0:{}s:15:" * replacements";a:5 {s:17:"%thebuggenie_url%";s:30:"http://project.webplatform.org";s:24:"%link_to_reset_password%";s:0:"";s:18:"%link_to_activate%";s:0:"";s:16:"%user_buddyname%";s:5:"Aaaaa";s:15:"%user_username%";s:5:"Aaaaa";}s:7:" * sep1";s:23:"_1_3233387863387136356c";s:7:" * sep2";s:23:"_2_75617135695636503979";s:10:" * headers";a:8:{s:8:"X-Mailer";s:3:"TBG";s:7:"Subject";s:73:"Re: [dabblet] Bug report #8 - Cannot save nor save-as gists (500s & 422s)";s:4:"Date";s:31:"Wed, 02 Oct 2013 19:25:15 +0000";s:12:"MIME-Version";s:3:"1.0";s:10:"Message-ID";s:49:"<_1_3233387863387136356c@project.webplatform.org>";s:4:"From";s:66:"WebPlatform Docs Project manager <aaaaaaaaaaaaaaaaaaaaaaa@aa.org>";s:11:"Return-Path";s:33:"<aaaaaaaaaaaaaaaaaaaaaaa@aa.org>";s:2:"To";s:25:""Aaaaa" <jjjjj@bbbbb.jjj>";}s:10:" * subject";s:73:"Re: [dabblet] Bug report #8 - Cannot save nor save-as gists (500s & 422s)";s:21:" * subject_translated";N;s:11:" * template";s:11:"issueupdate";s:22:" * template_parameters";a:3:{s:5:"issue";O:8:"TBGIssue":72:{s:9:" * _title";s:43:"Cannot save nor save-as gists (500s & 422s)";s:9:" * _links";N;s:9:" * _files";a:1:{i:14;O:7:"TBGFile":10:{s:16:" * _content_type";s:9:"image/png";s:15:" * _uploa ded_by";N;s:15:" * _uploaded_at";s:10:"1380741825";s:17:" * _real_filename";s:55:"116_1380741825_Screen Shot 2013-10-02 at 3.28.14 PM.png";s:8:" * _name";s:40:"Screen Shot 2013-10-02 at 3.28.14 PM.png";s:11:" * _content";s:77032:"`

**NOTE**: The data shown here has been anonymized. But the length of the values were kept intact.

While trying to use PHP unserialize the field we get the same error we had in the previous stack trace:

     unserialize(): Error at offset 1931 of 1938 bytes

This means that the class `TBGMimemail` will be unserialized with this data but the unserialized data seems to have something broken.

### <span>To fix the issue</span>

1.  Ensure no cron job will be running on server running The Bug Genie
2.  Run manually the `mailing:process_mail_queue` command until you are sure the next message is the broken one

       php /srv/webplatform/buggenie/tbg_cli mailing:process_mail_queue --limit=20

1.  When you are at `--limit=1` and it breaks, it means its the broken one
2.  Add those lines before the loop, before `if($res){`:

       $hack = TBGMimemail::createNewFromMessage('Borken message hack', 'passing around, sorry for that', null, array('my_own@gmail.com'));
       $hack->setFrom('renoirb@project1.dho.wpdn');

1.  Replace the part `unserialize($message); ` with `$hack`

     // Put the hack like so:
     $hack = TBGMimemail::createNewFromMessage('Borken message hack', 'passing around, sorry for that', null, array('my_own@gmail.com'));
     $hack->setFrom('renoirb@project1.dho.wpdn');
     if($res)
     {
       while ($row = $res->getNextRow())
       {
           $message = $row->get(self::MESSAGE);
           $messages[$row->get(self::ID)] = $hack;
           //$messages[$row->get(self::ID)] = unserialize($message);
       }
     }

1.  Run the `mailing:process_mail_queue` manually, the email should pass
2.  Comment the `$hack` and uncomment the real code.
3.  Make sure all the queue is processed
