:original_name: rds_06_0621.html

.. _rds_06_0621:

Obtaining a DB Instance List
============================

Function
--------

This API is used to obtain a DB instance list.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances

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

.. code-block:: text

   GET https://{Endpoint}/rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/instances

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                  |
      +=======================+=======================+==============================================================================================================================+
      | instanceId            | String                | Indicates the primary node ID of the DB instance.                                                                            |
      |                       |                       |                                                                                                                              |
      |                       |                       | .. note::                                                                                                                    |
      |                       |                       |                                                                                                                              |
      |                       |                       |    This field is not the DB instance ID. You are advised to use API v3 and the DB instance ID to perform related operations. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the DB instance status.                                                                                            |
      |                       |                       |                                                                                                                              |
      |                       |                       | Value:                                                                                                                       |
      |                       |                       |                                                                                                                              |
      |                       |                       | -  If the value is **BUILD**, the instance is being created.                                                                 |
      |                       |                       | -  If the value is **ACTIVE**, the instance is normal.                                                                       |
      |                       |                       | -  If the value is **FAILED**, the instance is abnormal.                                                                     |
      |                       |                       | -  If the value is **MODIFYING**, the instance is being scaled up.                                                           |
      |                       |                       | -  If the value is **REBOOTING**, the instance is being rebooted.                                                            |
      |                       |                       | -  If the value is **RESTORING**, the instance is being restored.                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | instanceName          | String                | Indicates the created DB instance name.                                                                                      |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      The values of **region** and **availabilityZone** are used as examples.

-  Response example

   .. code-block:: text

      {
          "instance": {
              "instanceId": "252f11f1-2912-4c06-be55-1999bde659c5",
              "status": "BUILD",
              "instanceName": "rds-instance-test01"
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
