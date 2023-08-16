:original_name: rds_07_0004.html

.. _rds_07_0004:

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

   PATH: /v1.0/{project_id}/instances/{instanceId}/action

   Method: POST

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      instanceId Yes       Specifies the DB instance ID.
      ========== ========= =================================================

-  Restrictions

   The DB instance cannot reboot when it is being created, scaled, backed up, restored, or its instance class is being changed.

   Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      ======= ========= ====== =============================
      Name    Mandatory Type   Description
      ======= ========= ====== =============================
      restart Yes       String This parameter is left blank.
      ======= ========= ====== =============================

-  Request example

   .. code-block:: text

      POST https://{Endpoint}/v1.0/375d8d8fad1f43039e23d3b6c0f60a19/instances/c90c1234-f687-462a-a6bd-cec35919c096/action

   .. code-block:: text

      {
            "restart": {}
      }

Normal Response
---------------

None

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <rds_01_0010>`.

Status Code
-----------

For details, see :ref:`Status Codes <rds_10_0200>`.

Error Code
----------

For details, see :ref:`Error Codes <rds_10_0201>`.
