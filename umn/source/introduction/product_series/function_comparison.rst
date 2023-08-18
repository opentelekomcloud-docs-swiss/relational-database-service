:original_name: rds_00_0011.html

.. _rds_00_0011:

Function Comparison
===================

Single DB instances use a single-node architecture. Different from the primary/standby DB instances, a single DB instance contains only one node and has no slave node for fault recovery.

Advantage Comparison
--------------------

-  Single DB instances: support the creation of read replicas and support the queries of error logs and slow query logs. Different from primary/standby DB instances that have two database nodes, a single DB instance has only one node. If a node fails, the restoration will take a long time. Therefore, single DB instances are not recommended for sensitive services that have high requirements on database availability.
-  Primary/Standby DB instances: use the slave database node only for failover and restoration. The slave database node does not provide services. The performance of single DB instances is similar to or even higher than the primary/standby DB instances.
-  Cluster instances: use the Microsoft Always On architecture with one master node, one slave node, and up to five read-only nodes. It features higher availability, reliability, and scalability.

.. table:: **Table 1** Function comparisons

   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Function                               | Single                         | Primary/Standby                | Cluster                     |
   +========================================+================================+================================+=============================+
   | Number of nodes                        | 1                              | 2                              | 2                           |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Specifications                         | vCPUs: a maximum of 32         | vCPUs: a maximum of 32         | vCPUs: a maximum of 64      |
   |                                        |                                |                                |                             |
   |                                        | Memory: a maximum of 128 GB    | Memory: a maximum of 128 GB    | Memory: a maximum of 512 GB |
   |                                        |                                |                                |                             |
   |                                        | Storage: a maximum of 4,000 GB | Storage: a maximum of 4,000 GB | Storage: a maximum of 4 TB  |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Monitoring and alarms                  | Supported                      | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Security group                         | Supported                      | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Backups and restorations               | Supported                      | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Recycle bin                            | Supported                      | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Parameter settings                     | Supported                      | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | SSL                                    | Supported                      | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Log management                         | Supported                      | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Read replicas (need to be created)     | Supported                      | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | High-frequency monitoring              | Supported                      | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Primary/standby switchover or failover | Not supported                  | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Standby DB instance migration          | Not supported                  | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Manual primary/standby switchover      | Not supported                  | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
   | Instance class change                  | Supported                      | Supported                      | Supported                   |
   +----------------------------------------+--------------------------------+--------------------------------+-----------------------------+
