:original_name: rds_01_0001.html

.. _rds_01_0001:

Obtaining a Database List of a Specified DB Instance
====================================================

Function
--------

This API is used to obtain a list of self-built databases of a specified DB instance.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{instanceId}/databases

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

-  Restrictions

   Currently, only the DB engine Microsoft SQL Server is supported by the API.

   The query result indicates the names of databases in the **Running** state.

Request
-------

.. code-block:: text

   GET https://{Endpoint}/rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/instances/02cf1fd7-24ae-4fec-a621-329ec732e4f6/databases

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                                                                                           | Description                                                                                                                  |
      +=======================+================================================================================================+==============================================================================================================================+
      | instanceId            | String                                                                                         | Indicates the primary node ID of the DB instance.                                                                            |
      |                       |                                                                                                |                                                                                                                              |
      |                       |                                                                                                | .. note::                                                                                                                    |
      |                       |                                                                                                |                                                                                                                              |
      |                       |                                                                                                |    This field is not the DB instance ID. You are advised to use API v3 and the DB instance ID to perform related operations. |
      +-----------------------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                                                                                         | Indicates the DB engine. Currently, Microsoft SQL Server is supported.                                                       |
      +-----------------------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | databases             | Dictionary data structure. For details, see :ref:`Table 3 <rds_01_0001__table25388053101549>`. | Indicates the list of database information.                                                                                  |
      +-----------------------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_01_0001__table25388053101549:

   .. table:: **Table 3** databases field data structure description

      +-----------------------+-----------------------+----------------------------------------------+
      | Name                  | Type                  | Description                                  |
      +=======================+=======================+==============================================+
      | name                  | String                | Indicates the database name.                 |
      +-----------------------+-----------------------+----------------------------------------------+
      | status                | String                | Indicates the database status. Valid values: |
      |                       |                       |                                              |
      |                       |                       | Creating                                     |
      |                       |                       |                                              |
      |                       |                       | Running                                      |
      |                       |                       |                                              |
      |                       |                       | Deleting                                     |
      +-----------------------+-----------------------+----------------------------------------------+
      | characterSetName      | String                | Indicates the charset.                       |
      +-----------------------+-----------------------+----------------------------------------------+

-  Response example

   .. code-block:: text

      {
         "instanceId": "69900b70d1f445ca8592278f5ea3ceddno04",
         "type": "SQLServer",
          "databases": [
              {
                  "name": "user01",
                  "status": "Running",
                  "characterSetName": "Chinese_PRC_CI_AS"

              },
              {
                  "name": "user02",
                  "status": "Running",
                  "characterSetName": "Chinese_PRC_CI_AS"

              }
          ]
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
