:original_name: rds_07_0015.html

.. _rds_07_0015:

Obtaining the DB Instances to Which a Parameter Template Applies
================================================================

Function
--------

This API is used to obtain the DB instances to which a specified parameter template applies.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/configurations/{id}/instances

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      id         Yes       Specifies the parameter template ID.
      ========== ========= =================================================

-  Restrictions

   Currently, the DB engines MySQL and PostgreSQL support obtaining DB instances to which the specified parameter template applies.

Request
-------

.. code-block:: text

   GET https://{Endpoint}/v1.0/375d8d8fad1f43039e23d3b6c0f60a19/configurations/07fc12a8e0e94df7a3fcf53d0b5e1605pr01/instances

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------+------------------------------------------------------------------------------------------+---------------------------------------------+
      | Name      | Type                                                                                     | Description                                 |
      +===========+==========================================================================================+=============================================+
      | instances | List data structure. For details, see :ref:`Table 3 <rds_07_0015__table47861511102930>`. | Indicates the DB instance list information. |
      +-----------+------------------------------------------------------------------------------------------+---------------------------------------------+

   .. _rds_07_0015__table47861511102930:

   .. table:: **Table 3** instances field data structure description

      ==== ====== ===============================
      Name Type   Description
      ==== ====== ===============================
      id   String Indicates the DB instance ID.
      name String Indicates the DB instance name.
      ==== ====== ===============================

-  Response example

   .. code-block:: text

      {
        "instances": [
          {
            "id": "53754eff-3f95-4da8-a908-a88e6ea2f65a",
            "name": "instances_test_1"
      },
      {
            "id": "53754eff-3f95-4da8-a908-a88e6ea2f65b",
            "name": "instances_test_2"
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
