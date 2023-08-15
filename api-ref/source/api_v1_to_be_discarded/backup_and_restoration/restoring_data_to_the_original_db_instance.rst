:original_name: rds_06_0426.html

.. _rds_06_0426:

Restoring Data to the Original DB Instance
==========================================

Function
--------

This API is used to restore data to the original DB instance.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{instanceId}/action

   Method: POST

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

-  Parameter description

   .. table:: **Table 2** Parameter description

      +---------+-----------+----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name    | Mandatory | Type                                                                                         | Description                                                                                                                                                                             |
      +=========+===========+==============================================================================================+=========================================================================================================================================================================================+
      | restore | Yes       | Dictionary data structure. For details, see :ref:`Table 3 <rds_06_0426__table634280816954>`. | Specifies the restore information, including **backupRef** and **restoreTime**. At least one of them must be specified. If both of them are specified, only **backupRef** takes effect. |
      +---------+-----------+----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_06_0426__table634280816954:

   .. table:: **Table 3** restore field data structure description

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                           |
      +=================+=================+=================+=======================================================================================================================================+
      | backupRef       | No              | String          | Specifies the full backup file ID.                                                                                                    |
      |                 |                 |                 |                                                                                                                                       |
      |                 |                 |                 | .. important::                                                                                                                        |
      |                 |                 |                 |                                                                                                                                       |
      |                 |                 |                 |    NOTICE:                                                                                                                            |
      |                 |                 |                 |    If **backupRef** is empty, **restoreTime** is mandatory. Otherwise, an error is reported.                                          |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | restoreTime     | No              | Long            | Specifies the time point to which the DB instance is restored. The value is a UNIX timestamp, in milliseconds. Example: 1637607605000 |
      |                 |                 |                 |                                                                                                                                       |
      |                 |                 |                 | .. important::                                                                                                                        |
      |                 |                 |                 |                                                                                                                                       |
      |                 |                 |                 |    NOTICE:                                                                                                                            |
      |                 |                 |                 |    If **restoreTime** is empty, **backupRef** is mandatory. Otherwise, an error is reported.                                          |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      POST https://{Endpoint}/rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/instances/02cf1fd7-24ae-4fec-a621-329ec732e4f6/action

   .. code-block:: text

      {
      "restore": {
              "backupRef":"a9832168-7541-4536-b8d9-a8a9b79cf1b4"
          }
      }

Normal Response
---------------

-  Parameter description

   .. table:: **Table 4** Parameter description

      +-------------+------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name        | Type                                                                                     | Description                                            |
      +=============+==========================================================================================+========================================================+
      | extendparam | Dictionary data structure. For details, see :ref:`Table 5 <rds_06_0426__table52869820>`. | Indicates the returned **extendparam** key-value pair. |
      +-------------+------------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _rds_06_0426__table52869820:

   .. table:: **Table 5** extendparam field data structure description

      +------+------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name | Type                                                                               | Description                                            |
      +======+====================================================================================+========================================================+
      | jobs | List data structure. For details, see :ref:`Table 6 <rds_06_0426__table32267243>`. | Indicates the returned **jobs** parameter information. |
      +------+------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _rds_06_0426__table32267243:

   .. table:: **Table 6** jobs field data structure description

      ==== ====== ======================
      Name Type   Description
      ==== ====== ======================
      id   String Indicates the task ID.
      ==== ====== ======================

-  Response example

   .. code-block:: text

      {
          "extendparam": {
              "jobs": [
                  {
                      "id": "ff80808156fa51c50156fa7c20210bc9"
                  }
              ]
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
