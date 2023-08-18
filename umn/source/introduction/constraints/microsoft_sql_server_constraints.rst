:original_name: rds_03_0003.html

.. _rds_03_0003:

Microsoft SQL Server Constraints
================================

RDS for SQL Server only supports DB instances under the License Included model and does not support "bring your own license" (BYOL). After a DB instance is created, it contains the Microsoft SQL Server software license.

:ref:`Table 1 <rds_03_0003__table459454418106>` shows the constraints designed to ensure the stability and security of RDS for SQL Server.

Microsoft SQL Server DB instances are classified into three types: single, primary/standby, and cluster. Different types support different functions. For details, see :ref:`Function Comparison <rds_00_0011>`.

.. _rds_03_0003__table459454418106:

.. table:: **Table 1** Function constraints

   +----------------------------------------+------------------------+------------------------+------------------------+
   | Function Item                          | Single                 | Primary/Standby        | Cluster                |
   +========================================+========================+========================+========================+
   | Maximum number of databases            | 100 (can be increased) | 100 (can be increased) | 100 (can be increased) |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Number of database accounts            | Unlimited              | Unlimited              | Unlimited              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Creation of user, LOGIN, or database   | Supported              | Supported              | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Database-level DDL trigger             | Supported              | Supported              | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Database permission authorization      | Supported              | Supported              | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | KILL permission                        | Supported              | Supported              | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | LinkServer                             | Not supported          | Not supported          | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Distributed transaction                | Not supported          | Not supported          | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | SQL Profiler                           | Supported              | Supported              | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Tuning Adviser                         | Supported              | Supported              | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Change Data Capture (CDC)              | Supported              | Supported              | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Change tracking                        | Supported              | Supported              | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Windows domain account login           | Supported              | Supported              | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Email                                  | Not supported          | Not supported          | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | SQL Server Integration Services (SSIS) | Not supported          | Not supported          | Not supported          |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | SQL Server Analysis Services (SSAS)    | Not supported          | Not supported          | Not supported          |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | SQL Server Reporting Services (SSRS)   | Not supported          | Not supported          | Supported              |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | R Services                             | Not supported          | Not supported          | Not supported          |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Common Language Runtime (CLR)          | Not supported          | Not supported          | SAFE supported         |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Asynchronous communication             | Not supported          | Not supported          | Not supported          |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Replication subscription               | Not supported          | Not supported          | Not supported          |
   +----------------------------------------+------------------------+------------------------+------------------------+
   | Policy management                      | Not supported          | Not supported          | Not supported          |
   +----------------------------------------+------------------------+------------------------+------------------------+
