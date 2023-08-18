:original_name: rds_faq_0055.html

.. _rds_faq_0055:

What Is the Maximum Number of Connections to an RDS DB Instance?
================================================================

RDS does not have constraints on the number of connections. This number is determined by the default value and value range of the DB engine. For example, you can set **max_connections** and **max_user_connections** in a parameter template to configure the maximum number of connections for an RDS MySQL DB instance.

About max_connections
---------------------

The max_connections is closely related to storage space (unit: GB) of the DB instance.

Estimated max_connections = Available node memory/Estimated memory occupied by a single connection

.. note::

   -  Available node memory = Total memory - Memory occupied by the buffer pool - 1 GB (mysqld process/OS/monitoring program)
   -  Estimated memory usage of a single connection (single_thread_memory) = thread_stack (256 KB) + binlog_cache_size (32 KB) + join_buffer_size (256 KB) + sort_buffer_size (256 KB) + read_buffer_size (128 KB) + read_rnd_buffer_size (256 KB) ≈ 1 MB

The following table lists the default values of **max_connections** for different memory specifications.

.. table:: **Table 1** Max_connections for different memory specifications

   =========== ===========
   Memory (GB) Connections
   =========== ===========
   512         100,000
   384         80,000
   256         60,000
   128         30,000
   64          18,000
   32          10,000
   16          5,000
   8           2,500
   4           1,500
   2           800
   =========== ===========
