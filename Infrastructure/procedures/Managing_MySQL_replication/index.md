= Managing MySQL Replication =

== Summary ==
How to manage communication and replication between MySQL servers across data centers.

== Checks ==

=== Checking if SSL is supported ===
Connect to the MySQL server in question and check if <code>have_ssl</coce> is to ''YES''

    mysql> SHOW VARIABLES LIKE 'have_ssl';
    +---------------+-------+
    | Variable_name | Value |
    +---------------+-------+
    | have_ssl      | YES   |
    +---------------+-------+


== References ==
* [http://www.howtoforge.com/how-to-set-up-mysql-database-replication-with-ssl-encryption-on-debian-lenny How to setup MySQL Databaes replication with SSL on Debian]
* [http://dev.mysql.com/doc/refman/5.1/en/replication-solutions-ssl.html Oracle reference: MySQL: 16.3.7. Setting Up Replication Using SSL]