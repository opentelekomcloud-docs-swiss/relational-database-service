:original_name: rds_09_0010.html

.. _rds_09_0010:

Restoring Tables to a Specified Point in Time (MySQL)
=====================================================

Function
--------

To ensure data integrity and reduce impact on the original instance performance, the system restores the full and incremental data at the selected time point to a temporary DB instance, automatically exports the tables to be restored, and then restores the tables to the original DB instance.

.. important::

   This operation will generate restored tables on the original DB instance. Ensure that the original DB instance has sufficient storage capacity.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

Constraints
-----------

-  This API is supported for MySQL only.
-  This API is not supported for MySQL 8.0 DB instances.
-  If the database table to be restored does not exist in the DB instance, no exception will occur when this API is called.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/restore/tables

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

      +---------------+-----------+------------------+------------------------------------------------------------------------------------------+
      | Name          | Mandatory | Type             | Description                                                                              |
      +===============+===========+==================+==========================================================================================+
      | restoreTime   | Yes       | Long             | Specifies the backup time point.                                                         |
      +---------------+-----------+------------------+------------------------------------------------------------------------------------------+
      | restoreTables | Yes       | Array of objects | Database information. For details, see :ref:`Table 3 <rds_09_0010__table1545319293199>`. |
      +---------------+-----------+------------------+------------------------------------------------------------------------------------------+

   .. _rds_09_0010__table1545319293199:

   .. table:: **Table 3** restoreTables field data structure description

      +----------+-----------+------------------+-----------------------------------------------------------------------------------------------------+
      | Name     | Mandatory | Type             | Description                                                                                         |
      +==========+===========+==================+=====================================================================================================+
      | database | Yes       | String           | Specifies the database name.                                                                        |
      +----------+-----------+------------------+-----------------------------------------------------------------------------------------------------+
      | tables   | Yes       | Array of objects | Specifies the table information. For details, see :ref:`Table 4 <rds_09_0010__table7718174802217>`. |
      +----------+-----------+------------------+-----------------------------------------------------------------------------------------------------+

   .. _rds_09_0010__table7718174802217:

   .. table:: **Table 4** tables field data structure description

      +---------+-----------+--------+-----------------------------------------------------------+
      | Name    | Mandatory | Type   | Description                                               |
      +=========+===========+========+===========================================================+
      | oldName | Yes       | String | Specifies the original table name before the restoration. |
      +---------+-----------+--------+-----------------------------------------------------------+
      | newName | Yes       | String | Specifies the table name after the restoration.           |
      +---------+-----------+--------+-----------------------------------------------------------+

-  Request example

   .. code-block:: text

      POST https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/restore/tables

   .. code-block:: text

      {
          "restoreTime": 1583720991838,
          "restoreTables": [
              {
                  "database": "restoretest",
                  "tables": [
                      {
                          "oldName": "test",
                          "newName": "test_1583720991838"
                      }
                  ]
              }
          ]
      }

Response
--------

-  Normal response

   ===== ====== ======================
   Name  Type   Description
   ===== ====== ======================
   jobId String Indicates the task ID.
   ===== ====== ======================

-  Example normal response

   .. code-block:: text

      {
          "jobId":"7b55d6ca-dc8e-4844-a9da-6c53a1506db3"
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
