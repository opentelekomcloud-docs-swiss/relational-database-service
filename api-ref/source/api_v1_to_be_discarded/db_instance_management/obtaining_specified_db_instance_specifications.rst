:original_name: rds_06_0624.html

.. _rds_06_0624:

Obtaining Specified DB Instance Specifications
==============================================

Function
--------

This API is used to obtain DB instance specifications of a specified specification ID.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/flavors/{flavorId}

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                        |
      +=======================+=======================+====================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                  |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavorId              | Yes                   | Specifies the specification ID compliant with the UUID format.                                                                                                     |
      |                       |                       |                                                                                                                                                                    |
      |                       |                       | For details about how to obtain this parameter value, see **flavors.id** in the response message in :ref:`Obtaining All DB Instance Specifications <rds_06_0623>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

.. code-block:: text

   GET https://{Endpoint}/rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/flavors/bf07a6d4-844a-4023-a776-fc5c5fb71fb4

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------+------------------------------------------------------------------------------------+------------------------------------------------------------+
      | Name   | Type                                                                               | Description                                                |
      +========+====================================================================================+============================================================+
      | flavor | List data structure. For details, see :ref:`Table 3 <rds_06_0624__table64140254>`. | Indicates the DB instance specifications information list. |
      +--------+------------------------------------------------------------------------------------+------------------------------------------------------------+

   .. _rds_06_0624__table64140254:

   .. table:: **Table 3** flavor field data structure description

      ======== ====== ====================================================
      Name     Type   Description
      ======== ====== ====================================================
      id       String Indicates the specification ID. Its value is unique.
      name     String Indicates the specification item name.
      ram      Int    Indicates the memory size in megabytes (MB).
      specCode String Indicates the resource specifications code.
      ======== ====== ====================================================

-  Response example

   .. code-block:: text

      {
          "flavor": {
              "id": "f7f51f85-cfcd-4409-ae91-b3eae186d0ea",
              "name": "RDS_MYLM_XLARGE",
              "ram": 32768,
              "specCode": "rds.mysql.s3.4xlarge.2"
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
