:original_name: rds_09_0003.html

.. _rds_09_0003:

Obtaining an Automated Backup Policy
====================================

Function
--------

This API is used to obtain an automated backup policy.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/backups/policy

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

.. code-block:: text

   GET https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/backups/policy

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                              |
      +=======================+=======================+==========================================================================================================+
      | backup_policy         | Object                | Indicates the backup policy objects, including the backup retention period (days) and backup start time. |
      |                       |                       |                                                                                                          |
      |                       |                       | For details, see :ref:`Table 3 <rds_09_0003__table163715367507>`.                                        |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+

   .. _rds_09_0003__table163715367507:

   .. table:: **Table 3** backup_policy field data structure description

      +------------+---------+-----------------------------------------------------------------------------------------------------------------+
      | Name       | Type    | Description                                                                                                     |
      +============+=========+=================================================================================================================+
      | keep_days  | Integer | Indicates the number of days to retain the backup files.                                                        |
      +------------+---------+-----------------------------------------------------------------------------------------------------------------+
      | start_time | String  | Indicates the backup time window. Automated backups will be triggered during the backup time window.            |
      +------------+---------+-----------------------------------------------------------------------------------------------------------------+
      | period     | String  | Indicates the backup cycle configuration. Data will be automatically backed up on the selected days every week. |
      +------------+---------+-----------------------------------------------------------------------------------------------------------------+

-  Example normal response

   When the automated backup policy is disabled:

   .. code-block:: text

      {
          "backup_policy": {
              "keep_days": 0
          }
      }

   When the automated backup policy is enabled:

   .. code-block:: text

      {
          "backup_policy": {
              "keep_days": 7,
              "start_time": "19:00-20:00",
              "period": "1,2"
          }
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
