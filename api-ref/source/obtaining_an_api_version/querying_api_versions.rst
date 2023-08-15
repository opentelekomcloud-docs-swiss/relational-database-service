:original_name: rds_04_0006.html

.. _rds_04_0006:

Querying API Versions
=====================

Function
--------

This API is used to query the supported RDS API versions.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

URI
---

-  URI format

   GET https://{*Endpoint*}/rds/

-  Parameter description

   None

Request
-------

.. code-block:: text

   GET https://{Endpoint}/rds/

Response
--------

-  Normal response

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                         |
      +=======================+=======================+=====================================================================+
      | versions              | Array of objects      | Indicates the list of detailed API version information.             |
      |                       |                       |                                                                     |
      |                       |                       | For details, see :ref:`Table 2 <rds_04_0006__table37479565104653>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------------+

   .. _rds_04_0006__table37479565104653:

   .. table:: **Table 2** versions field data structure description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                        |
      +=======================+=======================+====================================================================================================================================+
      | id                    | String                | Indicates the API version.                                                                                                         |
      |                       |                       |                                                                                                                                    |
      |                       |                       | -  **v1**: indicates the API v1 version.                                                                                           |
      |                       |                       | -  **v1.0**: indicates the OpenStack trove API v1.0.                                                                               |
      |                       |                       | -  **v3**: indicates the API v3 version.                                                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | links                 | Array of objects      | Indicates the API link information. The value is empty when the version is v1 or v3.                                               |
      |                       |                       |                                                                                                                                    |
      |                       |                       | For details, see :ref:`Table 3 <rds_04_0006__table630875915440>`.                                                                  |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the version status.                                                                                                      |
      |                       |                       |                                                                                                                                    |
      |                       |                       | **CURRENT**: indicates that the version is recommended.                                                                            |
      |                       |                       |                                                                                                                                    |
      |                       |                       | **DEPRECATED**: indicates a deprecated version which may be deleted later.                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Indicates the version update time.                                                                                                 |
      |                       |                       |                                                                                                                                    |
      |                       |                       | The format is yyyy-mm-dd Thh:mm:ssZ.                                                                                               |
      |                       |                       |                                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the Coordinated Universal Time (UTC). |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_04_0006__table630875915440:

   .. table:: **Table 3** links field data structure description (dedicated for OpenStack v1.0)

      +------+--------+------------------------------------------------------------------+
      | Name | Type   | Description                                                      |
      +======+========+==================================================================+
      | href | String | Indicates the API URL and the value is **""**.                   |
      +------+--------+------------------------------------------------------------------+
      | rel  | String | Its value is **self**, indicating that **href** is a local link. |
      +------+--------+------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "versions": [{
              "id": "v1",
              "links": [],
              "status": "CURRENT",
              "updated": "2017-02-07T17:34:02Z"
          }, {
              "id": "v1.0",
              "links": [{
                  "href": "",
                  "rel": "self"
              }],
              "status": "CURRENT",
              "updated": "2017-03-23T17:34:02Z"
          }, {
              "id": "v3",
              "links": [],
              "status": "CURRENT",
              "updated": "2019-01-15T12:00:00Z"
          }]
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
