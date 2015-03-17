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
; postcat -q FOO: Display an email, use in conjunction with ''mailq'' to get "FOO" identifier
; postfix check: Runs basic installation checks
; postconf: List all currently loaded configurations from ''main.cf''


=== Useful links ===

* [https://rtcamp.com/tutorials/mail/postfix-queue/ RTCamp tutorial on Postfix queue]
* [http://tecadmin.net/setup-catch-all-email-account-in-postfix/ Setup catch-all accounts in Postfix] (useful for ''webplatformstaging.org'')
* [http://www.postfix.org/postfix-manuals.html Postfix documentation]
** [http://www.postfix.org/local.8.html Local delivery]


=== TODO: Read and evaluate ===

* http://www.akadia.com/services/postfix_mta.html
* http://rimuhosting.com/support/settingupemail.jsp?mta=postfix&t=users
* http://stackoverflow.com/questions/979320/postfix-virtual-parent-domain-matches-subdomains-i-dont-want-it/980382#980382

== Exim ==

@TODO