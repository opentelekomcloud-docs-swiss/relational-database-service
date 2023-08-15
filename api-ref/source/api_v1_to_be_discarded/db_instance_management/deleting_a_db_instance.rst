:original_name: rds_06_0620.html

.. _rds_06_0620:

Deleting a DB Instance
======================

Function
--------

This API is used to delete a DB instance.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{instanceId}

   Method: DELETE

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

   Standby DB instances cannot be deleted.

Request
-------

.. code-block:: text

   DELETE https://{Endpoint}/rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/instances/02cf1fd7-24ae-4fec-a621-329ec732e4f6

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-------------+------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name        | Type                                                                                     | Description                                            |
      +=============+==========================================================================================+========================================================+
      | extendparam | Dictionary data structure. For details, see :ref:`Table 3 <rds_06_0620__table32267243>`. | Indicates the returned **extendparam** key-value pair. |
      +-------------+------------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _rds_06_0620__table32267243:

   .. table:: **Table 3** extendparam field data structure description

      +------+------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name | Type                                                                                     | Description                                            |
      +======+==========================================================================================+========================================================+
      | jobs | List data structure. For details, see :ref:`Table 4 <rds_06_0620__table57556452151811>`. | Indicates the returned **jobs** parameter information. |
      +------+------------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _rds_06_0620__table57556452151811:

   .. table:: **Table 4** jobs field data structure description

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
                   "id":"ff8080815a88d52c015a8a0db2250003"
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
