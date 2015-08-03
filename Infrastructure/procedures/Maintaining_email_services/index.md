---
title: WPD:Infrastructure/procedures/Maintaining email services
---
<div style="float:right;width:33%;word-wrap:break-word;clear:both;">
<h3><span class="mw-headline" id="WebPlatform_server_Infrastructure_architecture_menu"><a href="/wiki/WPD:Infrastructure/architecture" title="WPD:Infrastructure/architecture">WebPlatform server Infrastructure architecture menu</a></span></h3>
<div class="subpagelist">
<ul><li> <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM" title="WPD:Infrastructure/architecture/Base configuration of a VM">Base configuration of a VM</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status" title="WPD:Infrastructure/architecture/Reports to review status">Reports to review status</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Roles_and_environment_level" title="WPD:Infrastructure/architecture/Roles and environment level">Roles and environment level</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/SSL_certificates" title="WPD:Infrastructure/architecture/SSL certificates">SSL certificates</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/The_salt_master" title="WPD:Infrastructure/architecture/The salt master">The salt master</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish" title="WPD:Infrastructure/architecture/Things to consider when we expose service via Fastly and Varnish">Things to consider when we expose service via Fastly and Varnish</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Useful_commands" title="WPD:Infrastructure/architecture/Useful commands">Useful commands</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/VM_roles" title="WPD:Infrastructure/architecture/VM roles">VM roles</a></div></li></ul>
<p><b>See also</b>
</p>
<ul><li> <a href="/wiki/WPD:Infrastructure/procedures/Deploying_code_changes" title="WPD:Infrastructure/procedures/Deploying code changes">Deploying code changes</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Replacing_a_VM" title="WPD:Infrastructure/procedures/Replacing a VM">Replacing a VM</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration" title="WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration">Maintaining Fastly configuration</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Managing_MySQL_replication" title="WPD:Infrastructure/procedures/Managing MySQL replication">Managing MySQL replication</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it" title="WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it">Create new database credentials and configure a web application to use it</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">Maintaining ElasticSearch cluster</a></li>
<li> <strong class="selflink">Maintaining email services</strong></li></ul>
</div>
<h1><span class="mw-headline" id="Maintaining_email_services">Maintaining email services</span></h1>
<p>Every VM relies on a node to send email for them. The node who’s sole responsibility is to relay emails has "email" in its name, you can read more about that in <a href="/wiki/WPD:Infrastructure/architecture/VM_roles#mail" title="WPD:Infrastructure/architecture/VM roles">the <i>Infrastructure/architecture</i> section about the <b>"mail" VM role</b></a>.
</p><p>We are using two email servers ("MTA"):
</p>
<dl><dt> Exim</dt>
<dd> On <i>every</i> VMs, except the <i>mail</i> node</dd>
<dt> Postfix</dt>
<dd> <b>Only</b> on the <i>mail</i> node</dd></dl>
<h2><span class="mw-headline" id="Postfix">Postfix</span></h2>
<p>@TODO
</p>
<h3><span class="mw-headline" id="Useful_commands">Useful commands</span></h3>
<dl><dt> mailq</dt>
<dd> List messages in queue, bounces, frozen, deferred, etc along with an identifier</dd>
<dt> postqueue -p</dt>
<dd> same as <i>mailq</i> but specific to Postfix</dd>
<dt> postcat -q FOO</dt>
<dd> Display an email, use in conjunction with <i>mailq</i> to get "FOO" identifier</dd>
<dt> postfix check</dt>
<dd> Runs basic installation checks</dd>
<dt> postconf</dt>
<dd> List all currently loaded configurations from <i>main.cf</i></dd>
<dt>postmap -q 'root' hash:/etc/postfix/virtual &amp;&amp; echo OK || echo 'No match found'</dt>
<dd> Test if an email alias (e.g. root@webplatform.org) works (e.g. `root@webplatform.org` to send to `team-webplatform-foo@w3.org`)</dd></dl>
<p><br />
</p>
<h4><span class="mw-headline" id="Purge_messages_according_to_a_known_pattern">Purge messages according to a known pattern</span></h4>
<p>Not something to do liberally, only to known email messages patterns that you know are obsolete.
</p><p>A good time to use such command would be after a work session on a flapping service and all messages you see in the queue are byproduct of the issue you just fixed.
</p>
<pre> postqueue -p | grep ubuntu@webplatform.org | awk '{print $1}' | tr -d '*' | while read mid&#160;; do postsuper -d $mid&#160;; done
</pre>
<p><br />
</p>
<h3><span class="mw-headline" id="Useful_links">Useful links</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="https://rtcamp.com/tutorials/mail/postfix-queue/">RTCamp tutorial on Postfix queue</a></li>
<li> <a rel="nofollow" class="external text" href="http://tecadmin.net/setup-catch-all-email-account-in-postfix/">Setup catch-all accounts in Postfix</a> (useful for <i>webplatformstaging.org</i>)</li>
<li> <a rel="nofollow" class="external text" href="http://www.postfix.org/postfix-manuals.html">Postfix documentation</a>
<ul><li> <a rel="nofollow" class="external text" href="http://www.postfix.org/OVERVIEW.html"><b>Overview</b></a> — a <i>MUST READ</i>, summarizes well how Postfix is designed</li>
<li> <a rel="nofollow" class="external text" href="http://www.postfix.org/local.8.html">Local delivery</a></li>
<li> <a rel="nofollow" class="external text" href="http://www.postfix.org/FILTER_README.html">Filter</a></li></ul></li></ul>
<h3><span class="mw-headline" id="TODO:_Read_and_evaluate">TODO: Read and evaluate</span></h3>
<ul><li> <a rel="nofollow" class="external free" href="http://www.akadia.com/services/postfix_mta.html">http://www.akadia.com/services/postfix_mta.html</a></li>
<li> <a rel="nofollow" class="external free" href="http://rimuhosting.com/support/settingupemail.jsp?mta=postfix&amp;t=users">http://rimuhosting.com/support/settingupemail.jsp?mta=postfix&amp;t=users</a></li>
<li> <a rel="nofollow" class="external free" href="http://stackoverflow.com/questions/979320/postfix-virtual-parent-domain-matches-subdomains-i-dont-want-it/980382#980382">http://stackoverflow.com/questions/979320/postfix-virtual-parent-domain-matches-subdomains-i-dont-want-it/980382#980382</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.rwahyudi.com/linux/postfix-for-dev-setup-%E2%80%93-catch-all-email-and-forward-it-to-a-specific-address/">http://www.rwahyudi.com/linux/postfix-for-dev-setup-%E2%80%93-catch-all-email-and-forward-it-to-a-specific-address/</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.linuxquestions.org/questions/linux-server-73/email-forwarding-in-postfix-mail-server-4175414855/">http://www.linuxquestions.org/questions/linux-server-73/email-forwarding-in-postfix-mail-server-4175414855/</a></li></ul>
<h2><span class="mw-headline" id="Exim">Exim</span></h2>
<p>@TODO
</p>
<dl><dt>mailq</dt>
<dd> List the mail queue</dd>
<dt>exim -Mvb FOO</dt>
<dd> Read email body of email with id <i>FOO</i></dd>
<dt>exim -Mvh FOO</dt>
<dd> Read email header</dd>
<dt>exim -Mrm FOO</dt>
<dd> Delete email from queue</dd>
<dt> exim -q</dt>
<dd>Reprocess the queue</dd>
<dt>exim -qf</dt>
<dd>Reprocess the queue that has frozen messages</dd></dl>
<p><br />
</p>
<h4><span class="mw-headline" id="Purge_messages_according_to_a_known_pattern_2">Purge messages according to a known pattern</span></h4>
<p>Not something to do liberally, but can be handy.
</p>
<pre> exiqgrep -i | xargs exim -Mrm
</pre>
<h3><span class="mw-headline" id="Useful_links_2">Useful links</span></h3>
<ul><li> <a rel="nofollow" class="external text" href="https://github.com/Exim/exim/wiki">Wiki pages on the Exim GitHub project</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.electrictoolbox.com/exim-delete-message/">http://www.electrictoolbox.com/exim-delete-message/</a></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:58630-0!*!0!!*!*!*!esi=1 and timestamp 20150731185919 and revision id 101380
 -->
