:original_name: rds_07_0008.html

.. _rds_07_0008:

Obtaining All DB Instance Specifications
========================================

Function
--------

This API is used to obtain all DB instance specifications.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/flavors

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

-  Restrictions

   Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

.. code-block:: text

   GET https://{Endpoint}/v1.0/375d8d8fad1f43039e23d3b6c0f60a19/flavors

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +---------+-----------------------------------------------------------------------------------------+------------------------------------------+
      | Name    | Type                                                                                    | Description                              |
      +=========+=========================================================================================+==========================================+
      | flavors | List data structure. For details, see :ref:`Table 3 <rds_07_0008__table5932144310813>`. | Indicates the specification information. |
      +---------+-----------------------------------------------------------------------------------------+------------------------------------------+

   .. _rds_07_0008__table5932144310813:

   .. table:: **Table 3** flavors field data structure description

      +--------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name   | Type                                                                                    | Description                                                                                                                                                      |
      +========+=========================================================================================+==================================================================================================================================================================+
      | ram    | Int                                                                                     | Indicates the memory specifications in megabytes (MB).                                                                                                           |
      +--------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id     | Int                                                                                     | Indicates the specification ID (Int type). Its default value is **1** because RDS uses UUID to store the specification ID and cannot convert it to the Int type. |
      +--------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | links  | List data structure. For details, see :ref:`Table 4 <rds_07_0008__table2591008910813>`. | Indicates the link address.                                                                                                                                      |
      +--------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name   | String                                                                                  | Indicates the specification item name.                                                                                                                           |
      +--------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | str_id | String                                                                                  | Indicates the specification ID (String type).                                                                                                                    |
      +--------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_07_0008__table2591008910813:

   .. table:: **Table 4** links field data structure description

      ==== ====== ============================================
      Name Type   Description
      ==== ====== ============================================
      rel  String Indicates the link property.
      href String Indicates the API link. Its value is **""**.
      ==== ====== ============================================

-  Response example

   .. code-block:: text

      {
        "flavors": [
          {
            "ram": 4096,
            "id": 1,
            "links": [
              {
                "rel": "self",
                "href": ""
              },
              {
                "rel": "bookmark",
                "href": ""
              }
            ],
            "name": "rds.pg.s3.large.2",
            "str_id": "9ff2a3a5-c859-bbc0-67f7-86ce59432b1d"
          },
          {
            "ram": 32768,
            "id": 1,
            "links": [
              {
                "rel": "self",
                "href": ""
              },
              {
                "rel": "bookmark",
                "href": ""
              }
            ],
            "name": "rds.pg.s3.4xlarge.2",
            "str_id": "b77b5b7e-f572-dfd9-57af-910547fe0883"
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
