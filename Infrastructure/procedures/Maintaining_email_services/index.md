{{:WPD:Infrastructure/architecture}}
= Maintaining email services =

Every VM relies on a node to send email for them. The node who’s sole responsibility is to relay emails has "email" in its name, you can read more about that in [[WPD:Infrastructure/architecture/VM_roles#mail|the ''Infrastructure/architecture'' section about the '''"mail" VM role''']].

We are using two email servers ("MTA"):
; Exim: On ''every'' VMs, except the ''mail'' node
; Postfix: '''Only''' on the ''mail'' node

== Postfix ==

@TODO

=== Useful commands ===

; mailq: List messages in queue, bounces, frozen, deferred, etc along with an identifier
; postqueue -p: same as ''mailq'' but specific to Postfix
; postcat -q FOO: Display an email, use in conjunction with ''mailq'' to get "FOO" identifier
; postfix check: Runs basic installation checks
; postconf: List all currently loaded configurations from ''main.cf''
;<nowiki>postmap -q 'root' hash:/etc/postfix/virtual && echo OK || echo 'No match found'</nowiki>: Test if an email alias (e.g. root@webplatform.org) works (e.g. `root@webplatform.org` to send to `team-webplatform-foo@w3.org`)


==== Purge messages according to a known pattern ====

Not something to do liberally, only to known email messages patterns that you know are obsolete.

A good time to use such command would be after a work session on a flapping service and all messages you see in the queue are byproduct of the issue you just fixed.

  postqueue -p | grep ubuntu@webplatform.org | awk '{print $1}' | tr -d '*' | while read mid ; do postsuper -d $mid ; done


=== Useful links ===

* [https://rtcamp.com/tutorials/mail/postfix-queue/ RTCamp tutorial on Postfix queue]
* [http://tecadmin.net/setup-catch-all-email-account-in-postfix/ Setup catch-all accounts in Postfix] (useful for ''webplatformstaging.org'')
* [http://www.postfix.org/postfix-manuals.html Postfix documentation]
** [http://www.postfix.org/OVERVIEW.html '''Overview'''] — a ''MUST READ'', summarizes well how Postfix is designed
** [http://www.postfix.org/local.8.html Local delivery]
** [http://www.postfix.org/FILTER_README.html Filter]

=== TODO: Read and evaluate ===

* http://www.akadia.com/services/postfix_mta.html
* http://rimuhosting.com/support/settingupemail.jsp?mta=postfix&t=users
* http://stackoverflow.com/questions/979320/postfix-virtual-parent-domain-matches-subdomains-i-dont-want-it/980382#980382
* http://www.rwahyudi.com/linux/postfix-for-dev-setup-%E2%80%93-catch-all-email-and-forward-it-to-a-specific-address/
* http://www.linuxquestions.org/questions/linux-server-73/email-forwarding-in-postfix-mail-server-4175414855/

== Exim ==

@TODO

;mailq: List the mail queue
;exim -Mvb FOO: Read email body of email with id ''FOO''
;exim -Mvh FOO: Read email header
;exim -Mrm FOO: Delete email from queue
; exim -q:Reprocess the queue
;exim -qf:Reprocess the queue that has frozen messages


==== Purge messages according to a known pattern ====

Not something to do liberally, but can be handy.

  exiqgrep -i | xargs exim -Mrm

=== Useful links ===

* http://www.electrictoolbox.com/exim-delete-message/