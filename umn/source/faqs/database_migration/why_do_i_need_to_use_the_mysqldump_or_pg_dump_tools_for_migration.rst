:original_name: rds_faq_0026.html

.. _rds_faq_0026:

Why Do I Need to Use the mysqldump or pg_dump Tools for Migration?
==================================================================

The mysqldump or pg_dump tool is easy to use for data migration. However, when you use this tool, the server is stopped for a long period of time during data migration. Therefore, use these tools when the data amount is small or if the server is allowed to stop for a long period of time, during which the data can be migrated.

RDS is compatible with original database services. The procedure for migrating data from your database to RDS is similar to the procedure for migrating data from one database server to another.
