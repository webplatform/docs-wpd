---
title: 'Managing MySQL Replication over SSL'
uri: 'WPD:Infrastructure/procedures/Managing MySQL replication'

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
-   **Managing MySQL replication**
-   [Create new database credentials and configure a web application to use it](/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it)
-   [Maintaining ElasticSearch cluster](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster)
-   [Maintaining email services](/WPD:Infrastructure/procedures/Maintaining_email_services)

## Summary

How to manage communication and replication between MySQL servers across data-centers.

### Conventions

This document will follow those facts as a convention.

-   Master MySQL server is known as *db1* and the replication is *db2*

## In a few bullet points

1.  In `/etc/mysql/my.cnf`, make sure that each node has 'ssl' alone, close to the SSL certificates
2.  Create CA and self-signed certificates, see Salt TLS module ([salt.modules.tls](http://docs.saltstack.com/ref/modules/all/salt.modules.tls.html))
3.  Remove db2 MySQL entries from MediaWiki configuration files, sync them to `app*` servers
4.  On db2, Lock databases
5.  On db2, Dump database tables
6.  On db2, Unlock databases

### Memory dump, using Salt stack

-   [TLS salt module](http://docs.saltstack.com/ref/modules/all/salt.modules.tls.html)

<!-- -->

       salt 'db1*' tls.create_ca 'mysql' days=730 CN='db1-masterdb.production.wpdn' O='W3C' OU='WebPlatform Docs' emailAddress='EMAIL'

## Checks

### Checking if SSL is supported

Connect to the MySQL server in question and check if `have_ssl` is to *YES*

       mysql> SHOW VARIABLES LIKE 'have_ssl';
       +---------------+-------+
       | Variable_name | Value |
       +---------------+-------+
       | have_ssl      | YES   |
       +---------------+-------+

## Procedures

### Changing MariaDB replication master

Quoting what I wrote on [a blog post I wrote on January 2015: Create a MariaDB cluster with replication over SSL](https://renoirboulanger.com/blog/2015/01/create-mariadb-cluster-replication-ssl-salt-stack/):

-   From the masterdb MySQL server, in a command line session
-   Lock writes on masterdb databases `FLUSH TABLES WITH READ LOCK;` (make sure this session stays open, the lock only lasts with the session you used to write it. See [MariaDB flush tables pages](https://mariadb.com/kb/en/mariadb/flush-tables-for-export/))
-   From a secondary MySQL server; Wait replication to catch up `SHOW SLAVE STATUS\G`
-   Remove replication configuration
-   Tell all web apps to use new database master (from the salt master, change the **infra:hosts\_entries:masterdb** key in **/srv/pillar/infra/production.sls** (or **/srv/pillar/infra/staging.sls** for staging).
-   From the masterdb; remove database lock by closing the session opened earlier
-   Setup new replication configuration to use new master

@@TODO, Make a more precise procedure with new setup and how to manage.

## References

-   [How to setup MySQL Databaes replication with SSL on Debian](http://www.howtoforge.com/how-to-set-up-mysql-database-replication-with-ssl-encryption-on-debian-lenny)
-   [Oracle reference: MySQL: 16.3.7. Setting Up Replication Using SSL](http://dev.mysql.com/doc/refman/5.1/en/replication-solutions-ssl.html)
-   <http://plusbryan.com/mysql-replication-without-downtime>
-   <http://www.rackspace.com/knowledge_center/article/mysql-replication-masterslave>
-   <http://www.howtoforge.com/mysql_database_replication_p2>
-   <http://dev.mysql.com/doc/refman/5.0/en/lock-tables.html>
-   <http://www.mysqlperformanceblog.com/2012/07/31/innodb-table-locks/>
-   <http://dev.mysql.com/doc/refman/5.0/en/replication-howto.html>
