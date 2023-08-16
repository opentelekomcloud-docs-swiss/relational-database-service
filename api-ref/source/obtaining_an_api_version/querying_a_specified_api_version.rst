:original_name: rds_04_0005.html

.. _rds_04_0005:

Querying a Specified API Version
================================

Function
--------

This API is used to query the specified API version.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

URI
---

-  URI format

   GET https://{*Endpoint*}/rds/{*version*}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================+
      | version               | Yes                   | Specifies the API version. It is case-sensitive.                                                                                    |
      |                       |                       |                                                                                                                                     |
      |                       |                       | For details, see **id** in :ref:`Table 2 <rds_04_0006__table37479565104653>` in section :ref:`Querying API Versions <rds_04_0006>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

.. code-block:: text

   GET https://{Endpoint}/rds/v3

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                         |
      +=======================+=======================+=====================================================================+
      | versions              | Object                | Indicates the list of detailed API version information.             |
      |                       |                       |                                                                     |
      |                       |                       | For details, see :ref:`Table 3 <rds_04_0005__table57914909154838>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | version               | Object                | Indicates the list of detailed API version information.             |
      |                       |                       |                                                                     |
      |                       |                       | For details, see :ref:`Table 3 <rds_04_0005__table57914909154838>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------------+

   .. _rds_04_0005__table57914909154838:

   .. table:: **Table 3** versions field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                           |
      +=======================+=======================+=======================================================================================================+
      | id                    | String                | Indicates the API version.                                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | links                 | Array                 | Indicates the API version link information. Its value is empty.                                       |
      |                       |                       |                                                                                                       |
      |                       |                       | For details, see :ref:`Table 4 <rds_04_0005__table630875915440>`.                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the version status.                                                                         |
      |                       |                       |                                                                                                       |
      |                       |                       | **CURRENT**: indicates that the version is recommended.                                               |
      |                       |                       |                                                                                                       |
      |                       |                       | **DEPRECATED**: indicates a deprecated version which may be deleted later.                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | updated               | String                | Indicates the version update time.                                                                    |
      |                       |                       |                                                                                                       |
      |                       |                       | The format is yyyy-mm-dd Thh:mm:ssZ.                                                                  |
      |                       |                       |                                                                                                       |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the UTC. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+

   .. _rds_04_0005__table630875915440:

   .. table:: **Table 4** links field data structure description

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
        "version": {
          "id": "v3",
          "links": [],
          "status": "CURRENT",
          "updated": "2017-02-07T17:34:02Z"
        },
        "versions": {
          "id": "v3",
          "links": [],
          "status": "CURRENT",
          "updated": "2017-02-07T17:34:02Z"
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
