:original_name: rds_06_0623.html

.. _rds_06_0623:

Obtaining All DB Instance Specifications
========================================

Function
--------

This API is used to obtain all instance specifications of a specified database version ID in a specified region.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/flavors?dbId={db_version_id}&region={region}

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                 |
      +=======================+=======================+=============================================================================================================================================+
      | dbId                  | Yes                   | Specifies the database version ID (**dataStores.id** in the response message in :ref:`Database Version Queries <rds_06_0610>`).             |
      |                       |                       |                                                                                                                                             |
      |                       |                       | Valid value: The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | region                | Yes                   | Specifies the region where the DB instance is deployed.                                                                                     |
      |                       |                       |                                                                                                                                             |
      |                       |                       | Valid value:                                                                                                                                |
      |                       |                       |                                                                                                                                             |
      |                       |                       | The value cannot be empty. Obtain the parameter value from the enterprise administrator.                                                    |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. note::

      The value of **region** in the following is used as an example.

   .. code-block:: text

      GET https://{Endpoint}/rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/flavors?dbId=e8a8b8cc-63f8-4fb5-8d4a-24c502317a6&region=aaa

Normal Response
---------------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +---------+------------------------------------------------------------------------------------+------------------------------------------------------------+
      | Name    | Type                                                                               | Description                                                |
      +=========+====================================================================================+============================================================+
      | flavors | List data structure. For details, see :ref:`Table 4 <rds_06_0623__table34207804>`. | Indicates the DB instance specifications information list. |
      +---------+------------------------------------------------------------------------------------+------------------------------------------------------------+

   .. _rds_06_0623__table34207804:

   .. table:: **Table 4** flavors field data structure description

      ======== ====== ====================================================
      Name     Type   Description
      ======== ====== ====================================================
      id       String Indicates the specification ID. Its value is unique.
      name     String Indicates the specification item name.
      ram      Int    Indicates the memory size in megabytes (MB).
      specCode String Indicates the resource specification code.
      ======== ====== ====================================================

-  Response example

   .. code-block:: text

      {
          "flavors": [
              {
                  "id": "bf07a6d4-844a-4023-a776-fc5c5fb71fb4",
                  "name": "RDS_MYHP_LARGE",
                  "ram": 4096,
                  "specCode": "rds.mysql.s3.large.2"
              },
              {
                  "id": "f7f51f85-cfcd-4409-ae91-b3eae186d0ea",
                  "name": "RDS_MYLM_XLARGE",
                  "ram": 32768,
                  "specCode": "rds.mysql.s3.4xlarge.2"
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
