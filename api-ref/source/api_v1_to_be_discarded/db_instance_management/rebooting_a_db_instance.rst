:original_name: rds_06_0619.html

.. _rds_06_0619:

Rebooting a DB Instance
=======================

Function
--------

This API is used to reboot a DB instance.

.. important::

   The RDS DB instance will be unavailable during the reboot process. Exercise caution when performing this operation.

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

-  Restrictions

   The DB instance cannot reboot when it is being created, scaled, backed up, restored, or its instance class is being changed.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      ======= ========= ==== =============================
      Name    Mandatory Type Description
      ======= ========= ==== =============================
      restart Yes       None This parameter is left blank.
      ======= ========= ==== =============================

-  Request example

   .. code-block:: text

      POST https://{Endpoint}/rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/instances/02cf1fd7-24ae-4fec-a621-329ec732e4f6/action

   .. code-block:: text

      {
            "restart": {}
      }

Normal Response
---------------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +-------------+------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name        | Type                                                                                     | Description                                            |
      +=============+==========================================================================================+========================================================+
      | extendparam | Dictionary data structure. For details, see :ref:`Table 4 <rds_06_0619__table52869820>`. | Indicates the returned **extendparam** key-value pair. |
      +-------------+------------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _rds_06_0619__table52869820:

   .. table:: **Table 4** extendparam field data structure description

      +------+------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name | Type                                                                               | Description                                            |
      +======+====================================================================================+========================================================+
      | jobs | List data structure. For details, see :ref:`Table 5 <rds_06_0619__table32267243>`. | Indicates the returned **jobs** parameter information. |
      +------+------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _rds_06_0619__table32267243:

   .. table:: **Table 5** jobs field data structure description

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
                      "id": "2b414788-a600-4883-a023-90e2eb0ea227"
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
