= Managing MySQL Replication =

== Summary ==
How to manage communication and replication between MySQL servers across data centers.

=== Conventions ===
This document will follow those facts as a convention.

* Master MySQL server is known as ''db1'' and the replication is ''db2''

== In a few bullet points ==
# In <code>/etc/mysql/my.cnf</code>, make sure that each node has 'ssl' alone, close to the SSL certificates
# Create CA and self-signed certificates, see Salt TLS module ([http://docs.saltstack.com/ref/modules/all/salt.modules.tls.html salt.modules.tls])
# Remove db2 MySQL entries from MediaWiki configuration files, sync them to <code>app*</code> servers
# On db2,  Lock databases
# On db2,  Dump database tables
# On db2,  Unlock databases

=== Memory dump, using Salt stack ===
* [http://docs.saltstack.com/ref/modules/all/salt.modules.tls.html TLS salt module]

    salt 'db1*' tls.create_ca 'mysql' days=730 CN='db1.webplatform.org' O='W3C' OU='WebPlatform Docs' emailAddress='EMAIL'


== Checks ==

=== Checking if SSL is supported ===
Connect to the MySQL server in question and check if <code>have_ssl</code> is to ''YES''

    mysql> SHOW VARIABLES LIKE 'have_ssl';
    +---------------+-------+
    | Variable_name | Value |
    +---------------+-------+
    | have_ssl      | YES   |
    +---------------+-------+


== References ==
* [http://www.howtoforge.com/how-to-set-up-mysql-database-replication-with-ssl-encryption-on-debian-lenny How to setup MySQL Databaes replication with SSL on Debian]
* [http://dev.mysql.com/doc/refman/5.1/en/replication-solutions-ssl.html Oracle reference: MySQL: 16.3.7. Setting Up Replication Using SSL]
* http://plusbryan.com/mysql-replication-without-downtime
* http://www.rackspace.com/knowledge_center/article/mysql-replication-masterslave
* http://www.howtoforge.com/mysql_database_replication_p2
* http://dev.mysql.com/doc/refman/5.0/en/lock-tables.html
* http://www.mysqlperformanceblog.com/2012/07/31/innodb-table-locks/
* http://dev.mysql.com/doc/refman/5.0/en/replication-howto.html