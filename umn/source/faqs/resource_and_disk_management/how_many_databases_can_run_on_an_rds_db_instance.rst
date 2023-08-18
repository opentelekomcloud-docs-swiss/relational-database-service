:original_name: rds_faq_0007.html

.. _rds_faq_0007:

How Many Databases Can Run on an RDS DB Instance?
=================================================

The maximum number of databases that can run on an RDS DB instance depends on the DB engine settings.

If there are enough CPU, memory, and storage resources, there are no limitations to the number of databases running on a DB instance. A maximum of 0.5 million tables can be backed up. Excessive tables will generate errors. The backup speed is affected by the number of tables in a database.

-  MySQL allows you to create numerous databases and tables. For details, see the official MySQL documentation.
-  PostgreSQL allows you to create numerous databases and database accounts.
-  Microsoft SQL Server allows you to create a maximum of 100 databases and numerous database accounts.
