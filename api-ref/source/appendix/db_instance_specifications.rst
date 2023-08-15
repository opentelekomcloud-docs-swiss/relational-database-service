:original_name: rds_10_0004.html

.. _rds_10_0004:

DB Instance Specifications
==========================

The format of the specification code is: {*spec code*}{*instance mode*}.

-  *spec code* can be obtained from :ref:`Table 1 <rds_10_0004__table3999164019138>`.
-  *instance mode* can be any of the following:

   -  For single DB instances, the value is **null**. Example specification code: rds.mysql.s3.large.2
   -  For primary/standby DB instances, the value is **.ha**. Example specification code: rds.mysql.s3.large.2.ha
   -  For read replicas, the value is **.rr**. Example specification code: rds.mysql.s3.large.2.rr
   -  For cluster instances, the value is **.ha**. Example specification code: rds.mssql.s3.large.ha

Constraints
-----------

Only DB instances running Microsoft SQL Server 2017 EE support the creation of read replicas. Microsoft SQL Server 2017 EE does not support the creation of single DB instances.

.. _rds_10_0004__table3999164019138:

.. table:: **Table 1** Single DB instance specifications

   +------------------------+----------------------+------------------------+-------+-------------+
   | Instance Class         | DB Engine            | Spec Code              | vCPUs | Memory (GB) |
   +========================+======================+========================+=======+=============+
   | General computing-plus | MySQL                | rds.mysql.s3.large.2   | 2     | 4           |
   +------------------------+----------------------+------------------------+-------+-------------+
   |                        |                      | rds.mysql.s3.xlarge.2  | 4     | 8           |
   +------------------------+----------------------+------------------------+-------+-------------+
   |                        |                      | rds.mysql.s3.2xlarge.2 | 8     | 16          |
   +------------------------+----------------------+------------------------+-------+-------------+
   |                        |                      | rds.mysql.s3.4xlarge.2 | 16    | 32          |
   +------------------------+----------------------+------------------------+-------+-------------+
   |                        | PostgreSQL           | rds.pg.s3.large.2      | 2     | 4           |
   +------------------------+----------------------+------------------------+-------+-------------+
   |                        |                      | rds.pg.s3.xlarge.2     | 4     | 8           |
   +------------------------+----------------------+------------------------+-------+-------------+
   |                        |                      | rds.pg.s3.2xlarge.2    | 8     | 16          |
   +------------------------+----------------------+------------------------+-------+-------------+
   |                        |                      | rds.pg.s3.4xlarge.2    | 16    | 32          |
   +------------------------+----------------------+------------------------+-------+-------------+
   |                        | Microsoft SQL Server | rds.mssql.s3.large     | 2     | 4           |
   +------------------------+----------------------+------------------------+-------+-------------+
   |                        |                      | rds.mssql.s3.xlarge    | 4     | 8           |
   +------------------------+----------------------+------------------------+-------+-------------+
   |                        |                      | rds.mssql.s3.2xlarge   | 8     | 16          |
   +------------------------+----------------------+------------------------+-------+-------------+
   |                        |                      | rds.mssql.s3.4xlarge   | 16    | 32          |
   +------------------------+----------------------+------------------------+-------+-------------+
