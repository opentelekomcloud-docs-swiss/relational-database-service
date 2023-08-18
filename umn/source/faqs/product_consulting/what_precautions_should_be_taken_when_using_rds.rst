:original_name: rds_faq_0001.html

.. _rds_faq_0001:

What Precautions Should Be Taken When Using RDS?
================================================

#. DB instance operating systems (OSs) are invisible to you. Your applications can access a database only through the IP address and port.

#. The backup files stored in OBS and the ECS used by RDS are invisible to you. They are visible only in the RDS instance management system.

#. Precautions after purchasing RDS:

   After purchasing RDS DB instances, you do not need to perform basic database O&M operations, such as applying HA and security patches. However, you must still pay attention to:

   a. Whether the CPU, input/output operations per second (IOPS), and space are insufficient for the RDS DB instances. If any of these becomes insufficient, you will need to change the CPU/memory or scale up the DB instance.
   b. Whether the performance of the RDS DB instances is adequate, a large number of slow query SQL statements exist, SQL statements need to be optimized, or any indexes are redundant or missing.
