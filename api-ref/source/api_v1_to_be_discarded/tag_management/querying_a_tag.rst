:original_name: rds_01_0007.html

.. _rds_01_0007:

Querying a Tag
==============

Function
--------

This API is used to query the tag associated with a DB instance.

URI
---

-  URI format

   PATH: /v1/{project_id}/rds/{instanceId}/tags

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      instanceId Yes       Specifies the primary node ID of the DB instance.
      ========== ========= =================================================

-  Restrictions

   Standby DB instances do not support tag queries.

Request
-------

.. code-block:: text

   GET https://{Endpoint}/v1/375d8d8fad1f43039e23d3b6c0f60a19/rds/02cf1fd7-24ae-4fec-a621-329ec732e4f6/tags

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +------+--------------------------------------------------------------------------------------------------------+--------------------------------+
      | Name | Type                                                                                                   | Description                    |
      +======+========================================================================================================+================================+
      | tags | List data structure. For details, see :ref:`Table 3 <rds_01_0007__t8538b53f8f2141978a5bf8ef5606bf24>`. | Specifies the tag information. |
      +------+--------------------------------------------------------------------------------------------------------+--------------------------------+

   .. _rds_01_0007__t8538b53f8f2141978a5bf8ef5606bf24:

   .. table:: **Table 3** tags field data structure description

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                      |
      +=======================+=======================+==================================================================================================================================================================================+
      | key                   | String                | Specifies the tag key.                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                  |
      |                       |                       | Its value cannot be empty and must be 1 to 36 Unicode characters in length. It cannot contain nonprintable ASCII characters (0-31) and the following special characters: \*<>\\= |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value                 | String                | Specifies the tag value.                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                  |
      |                       |                       | Its value can be empty or 1 to 43 Unicode characters in length. It cannot contain nonprintable ASCII characters (0-31) and the following special characters: \*<>\\=             |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
             "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key2",
                  "value": "value3"
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
