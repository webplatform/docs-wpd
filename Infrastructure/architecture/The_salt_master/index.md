---
title: 'The Salt Master'
uri: 'WPD:Infrastructure/architecture/The salt master'

---
### [WebPlatform server Infrastructure architecture menu](/WPD:Infrastructure/architecture)

-   [Base configuration of a VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM)
-   [Reports to review status](/WPD:Infrastructure/architecture/Reports_to_review_status)
-   [Roles and environment level](/WPD:Infrastructure/architecture/Roles_and_environment_level)
-   [SSL certificates](/WPD:Infrastructure/architecture/SSL_certificates)
-   **The salt master**
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
-   [Maintaining email services](/WPD:Infrastructure/procedures/Maintaining_email_services)

[Deploying code changes on the site](/WPD:Infrastructure/procedures/Deploying_code_changes) is made through a VM, named "salt" we refer to this machine as the "Salt Master" we generally connect through SSH at the name **salt.webplatform.org**.

**Note** *staging* environment’ *salt master* is accessible as **salt.webplatformstaging.org**

The software we use for configuration management is called **[Salt Stack](http://saltstack.com/)**, we refer to the machine that has a copy of all the configuration files.

Commands that can be done from the *salt* VM in the terminal, but some could also be visualized from within your local web browser through [Read reports from a VM through private network](/WPD:Infrastructure/architecture/Reports_to_review_status#Read_reports_from_a_VM_through_private_network) in [WPD:Infrastructure/architecture/Reports\_to\_review\_status](/WPD:Infrastructure/architecture/Reports_to_review_status).

## Also configured ...

-   Runs fail2ban and *bans* successive unsuccessful login attempts (Possible attacks)

## Centralized logging

The salt master in every environment receives raw logs from all the *minions* it controls. Here are a few log files you can tail.

/var/log/messages
:   local syslog-ng
/mnt/logs/caching.log
:   Sent by Fastly
/mnt/logs/mw-logs/exception.log
:   Sent by MediaWiki
/mnt/logs/mw-logs/memcached-serious.log
:   Sent by MediaWiki
/mnt/logs/error.log
:   Sent through UDP

### Sent by MediaWiki

MediaWiki config has a line **\$wpdUdp2logDest = 'salt:8420';** and other directives. All is setup via salt from the template at **/srv/salt/code/files/docs/Settings.php.jinja** and gets written to the wiki configuration at deploy time.

### Sent through UDP

Each VM, except the salt master itself, should have a file in \`/etc/rsyslog.d/60-local1.conf\` for this purpose. The salt master is using syslog-ng to receive and write the log messages from the minions.

Setup is not fully trusted/reliable yet. I’m affraid we are losing packets due to many factors (if a minion VM doesnt find the salt master for any reason for example). This will be addressed, see *WebPlatform GitHub operations issue tracker*, at **[webplatform/ops\#117](https://github.com/webplatform/ops/issues/117)**

### Sent by Fastly

Each service has a "Logging" setting to send through TCP from their respective services.
