{{:WPD:Infrastructure/architecture}}
= The Salt Master =

[[WPD:Infrastructure/procedures/Deploying_code_changes|Deploying code changes on the site]] is made through a VM, named "salt" we refer to this machine as the "Salt Master" we generally connect through SSH at the name '''salt.webplatform.org'''.

'''Note''' ''staging'' environment’ ''salt master'' is accessible as '''salt.webplatformstaging.org'''

The software we use for configuration management is called '''[http://saltstack.com/ Salt Stack]''', we refer to the machine that has a copy of all the configuration files.

Commands that can be done from the ''salt'' VM in the terminal, but some could also be visualized from within your local web browser through [[WPD:Infrastructure/architecture/Reports_to_review_status#Read reports from a VM through private network|Read reports from a VM through private network]] in [[WPD:Infrastructure/architecture/Reports_to_review_status]].

== Also configured ... ==

* Runs fail2ban and ''bans'' successive unsuccessful login attempts (Possible attacks)


== Centralized logging ==

The salt master in every environment receives raw logs from all the ''minions'' it controls. Here are a few log files you can tail.

;/var/log/messages: local syslog-ng
;/mnt/logs/caching.log: Sent by Fastly
;/mnt/logs/mw-logs/exception.log: Sent by MediaWiki
;/mnt/logs/mw-logs/memcached-serious.log: Sent by MediaWiki
;/mnt/logs/error.log: Sent through UDP

=== Sent by MediaWiki ===

MediaWiki config has a line '''$wpdUdp2logDest = 'salt:8420';''' and other directives. All is setup via salt from the template at '''/srv/salt/code/files/docs/Settings.php.jinja''' and gets written to the wiki configuration at deploy time.


=== Sent through UDP ===

Each VM, except the salt master itself, should have a file in `/etc/rsyslog.d/60-local1.conf` for this purpose.
The salt master is using syslog-ng to receive and write the log messages from the minions.

Setup is not fully trusted/reliable yet. I’m affraid we are losing packets due to many factors (if a minion VM doesnt find the salt master for any reason for example). This will be addressed in [https://github.com/webplatform/ops/issues/117 webplatform/ops#117].


=== Sent by Fastly ===

Each service has a "Logging" setting to send through TCP from their respective services.