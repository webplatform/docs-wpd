---
title: Maintaining email services
uri: 'WPD:Infrastructure/procedures/Maintaining email services'

---
### [WebPlatform server Infrastructure architecture menu](/WPD:Infrastructure/architecture)

-   [Base configuration of a VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM)
-   [Reports to review status](/WPD:Infrastructure/architecture/Reports_to_review_status)
-   [Roles and environment level](/WPD:Infrastructure/architecture/Roles_and_environment_level)
-   [SSL certificates](/WPD:Infrastructure/architecture/SSL_certificates)
-   [The salt master](/WPD:Infrastructure/architecture/The_salt_master)
-   [Things to consider when we expose service via Fastly and Varnish](/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish)
-   [Useful commands](/WPD:Infrastructure/architecture/Useful_commands)
-   [VM roles](/WPD:Infrastructure/architecture/VM_roles)

**See also**

-   [Deploying code changes](/WPD:Infrastructure/procedures/Deploying_code_changes)
-   [Replacing a VM](/WPD:Infrastructure/procedures/Replacing_a_VM)
-   [Maintaining Fastly configuration](/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration)
-   [Managing MySQL replication](/WPD:Infrastructure/procedures/Managing_MySQL_replication)
-   [Create new database credentials and configure a web application to use it](/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it)
-   [Maintaining ElasticSearch cluster](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster)
-   **Maintaining email services**

Every VM relies on a node to send email for them. The node who’s sole responsibility is to relay emails has "email" in its name, you can read more about that in [the *Infrastructure/architecture* section about the **"mail" VM role**](/WPD:Infrastructure/architecture/VM_roles#mail).

We are using two email servers ("MTA"):

 Exim
:   On *every* VMs, except the *mail* node
 Postfix
:   **Only** on the *mail* node

## Postfix

@TODO

### Useful commands

 mailq
:   List messages in queue, bounces, frozen, deferred, etc along with an identifier
 postqueue -p
:   same as *mailq* but specific to Postfix
 postcat -q FOO
:   Display an email, use in conjunction with *mailq* to get "FOO" identifier
 postfix check
:   Runs basic installation checks
 postconf
:   List all currently loaded configurations from *main.cf*
postmap -q 'root' hash:/etc/postfix/virtual && echo OK || echo 'No match found'
:   Test if an email alias (e.g. root@webplatform.org) works (e.g. \`root@webplatform.org\` to send to \`team-webplatform-foo@w3.org\`)

#### Purge messages according to a known pattern

Not something to do liberally, only to known email messages patterns that you know are obsolete.

A good time to use such command would be after a work session on a flapping service and all messages you see in the queue are byproduct of the issue you just fixed.

     postqueue -p | grep ubuntu@webplatform.org | awk '{print $1}' | tr -d '*' | while read mid ; do postsuper -d $mid ; done

### Useful links

-   [RTCamp tutorial on Postfix queue](https://rtcamp.com/tutorials/mail/postfix-queue/)
-   [Setup catch-all accounts in Postfix](http://tecadmin.net/setup-catch-all-email-account-in-postfix/) (useful for *webplatformstaging.org*)
-   [Postfix documentation](http://www.postfix.org/postfix-manuals.html)
    -   [**Overview**](http://www.postfix.org/OVERVIEW.html) — a *MUST READ*, summarizes well how Postfix is designed
    -   [Local delivery](http://www.postfix.org/local.8.html)
    -   [Filter](http://www.postfix.org/FILTER_README.html)

### TODO: Read and evaluate

-   <http://www.akadia.com/services/postfix_mta.html>
-   <http://rimuhosting.com/support/settingupemail.jsp?mta=postfix&t=users>
-   <http://stackoverflow.com/questions/979320/postfix-virtual-parent-domain-matches-subdomains-i-dont-want-it/980382#980382>
-   <http://www.rwahyudi.com/linux/postfix-for-dev-setup-%E2%80%93-catch-all-email-and-forward-it-to-a-specific-address/>
-   <http://www.linuxquestions.org/questions/linux-server-73/email-forwarding-in-postfix-mail-server-4175414855/>

## Exim

@TODO

mailq
:   List the mail queue
exim -Mvb FOO
:   Read email body of email with id *FOO*
exim -Mvh FOO
:   Read email header
exim -Mrm FOO
:   Delete email from queue
 exim -q
:   Reprocess the queue
exim -qf
:   Reprocess the queue that has frozen messages

#### Purge messages according to a known pattern

Not something to do liberally, but can be handy.

     exiqgrep -i | xargs exim -Mrm

### Useful links

-   [Wiki pages on the Exim GitHub project](https://github.com/Exim/exim/wiki)
-   <http://www.electrictoolbox.com/exim-delete-message/>
