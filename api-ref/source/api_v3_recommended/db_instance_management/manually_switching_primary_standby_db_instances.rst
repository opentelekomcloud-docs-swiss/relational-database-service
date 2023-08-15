:original_name: rds_05_0013.html

.. _rds_05_0013:

Manually Switching Primary/Standby DB Instances
===============================================

Function
--------

This API is used to manually switch primary/standby DB instances as required.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

Constraints
-----------

-  This API is supported for MySQL and PostgreSQL.
-  This API is supported for primary/standby DB instances only.
-  Primary/standby DB instances cannot be manually switched if they are in any of the following statuses:

   -  For MySQL and PostgreSQL: creating, rebooting, upgrading, changing instance class, restoring, changing port, or creating database account

   -  For MySQL: deleting database account

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/failover

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Request example

   .. code-block:: text

      PUT https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/failover

   .. code-block:: text

      {}

Response
--------

-  Normal response

   ========== =============================
   Name       Description
   ========== =============================
   workflowId Indicates the task ID.
   instanceId Indicates the DB instance ID.
   nodeId     Indicates the node ID.
   ========== =============================

-  Example normal response

   .. code-block:: text

      {
          "workflowId":"072beb09-0573-40bf-bfe8-4be5cec9e85a",
          "instanceId":"794c38e5309344818f4b33b86ebce9b4in03",
          "nodeId":"b94ba815747040f1b0d641cd13364a06no03"
      }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <rds_01_0010>`.

Status Code
-----------

-  Normal

   200

-  Abnormal

   For details, see :ref:`Status Codes <rds_10_0200>`.

Error Code
----------

For details, see :ref:`Error Codes <rds_10_0201>`.
