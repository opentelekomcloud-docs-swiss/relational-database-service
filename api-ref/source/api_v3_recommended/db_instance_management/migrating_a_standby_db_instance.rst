:original_name: rds_05_0015.html

.. _rds_05_0015:

Migrating a Standby DB Instance
===============================

Function
--------

This API is used to migrate a standby DB instance based on service requirements.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

Constraints
-----------

-  Only primary/standby DB instances running MySQL 5.6 or 5.7 support standby DB instance migration to another AZ.
-  The standby DB instance cannot be migrated if the primary DB instance is in any of the following statuses: creating, rebooting, upgrading, changing instance class, changing port, creating users, or deleting users.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/migrateslave

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

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------+-----------+--------+----------------------------------------------------------------------------------+
      | Name   | Mandatory | Type   | Description                                                                      |
      +========+===========+========+==================================================================================+
      | nodeId | Yes       | String | Specifies the ID of the standby node.                                            |
      +--------+-----------+--------+----------------------------------------------------------------------------------+
      | azCode | Yes       | String | Specifies the code of the AZ to which the standby DB instance is to be migrated. |
      +--------+-----------+--------+----------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      POST https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/migrateslave

   .. code-block:: text

      {
          "nodeId": "0119b1068b874cb4a5202989a06b6094no01",
          "azCode": "az2xahz"
      }

Response
--------

-  Normal response

   ========== ======================
   Name       Description
   ========== ======================
   workflowId Indicates the task ID.
   ========== ======================

-  Example normal response

   .. code-block:: text

      {
          "workflowId":"7b55d6ca-dc8e-4844-a9da-6c53a1506db3"
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
