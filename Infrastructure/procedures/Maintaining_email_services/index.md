{{:WPD:Infrastructure/architecture}}
= Maintaining email services =

Every VM relies on a node to send email for them. The node who’s sole responsibility is to relay emails has "email" in its name, you can read more about that in [[WPD:Infrastructure/architecture/VM_roles#mail|the ''Infrastructure/architecture'' section about the '''"mail" VM role''']].

We are using two email servers ("MTA"):
; Exim: On ''every'' VMs, except the ''mail'' node
; Postfix: '''Only''' on the ''mail'' node

== Postfix ==

@TODO

=== Run basic checks ===

 postfix check

=== Useful links ===

* [https://rtcamp.com/tutorials/mail/postfix-queue/ RTCamp tutorial on Postfix queue]
* Postfix documentation
** [http://www.postfix.org/local.8.html Local delivery]


=== TODO: Read and evaluate ===

* http://rimuhosting.com/support/settingupemail.jsp?mta=postfix&t=users

== Exim ==

@TODO