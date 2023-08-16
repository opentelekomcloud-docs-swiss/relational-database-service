:original_name: rds_06_0421.html

.. _rds_06_0421:

Obtaining an Automated Backup Policy
====================================

Function
--------

This API is used to obtain an automated backup policy information.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{instanceId}/backups/policy

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                  |
      +=======================+=======================+==============================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | instanceId            | Yes                   | Specifies the primary node ID of the DB instance.                                                                            |
      |                       |                       |                                                                                                                              |
      |                       |                       | .. note::                                                                                                                    |
      |                       |                       |                                                                                                                              |
      |                       |                       |    This field is not the DB instance ID. You are advised to use API v3 and the DB instance ID to perform related operations. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

Request
-------

.. code-block:: text

   GET https://{Endpoint}/rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/instances/02cf1fd7-24ae-4fec-a621-329ec732e4f6/backups/policy

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------+------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
      | Name   | Type                                                                                           | Description                                                                                              |
      +========+================================================================================================+==========================================================================================================+
      | policy | Dictionary data structure. For details, see :ref:`Table 3 <rds_06_0421__table35260043174853>`. | Indicates the backup policy objects, including the backup retention period (days) and backup start time. |
      +--------+------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+

   .. _rds_06_0421__table35260043174853:

   .. table:: **Table 3** policy field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                                             |
      +=======================+=======================+=========================================================================================================================================================================================================================+
      | keepday               | Int                   | Indicates the number of days to retain the generated backup files.                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | The value range is from 0 to 732. If this parameter is **0**, the automated backup policy is not set. To extend the retention period, contact the administrator. Automated backups can be retained for up to 2562 days. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | starttime             | String                | Indicates the backup start time that has been set. The backup task will be triggered within one hour after the backup start time.                                                                                       |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | Valid value:                                                                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | The value cannot be empty. The format can be hh:mm:ss or hh:mm and must be valid. The time is in the UTC format.                                                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "policy": {
        "keepday": 7,
        "starttime": "00:00:00"
       }
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <rds_01_0010>`.

Status Code
-----------

For details, see :ref:`Status Codes <rds_10_0200>`.

Error Code
----------

For details, see :ref:`Error Codes <rds_10_0201>`.
