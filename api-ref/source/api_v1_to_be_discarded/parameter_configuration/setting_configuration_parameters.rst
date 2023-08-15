:original_name: rds_06_0627.html

.. _rds_06_0627:

Setting Configuration Parameters
================================

Function
--------

This API is used to set DB instance parameters.

.. note::

   A parameter template (with same name as the DB instance) will be created if needed.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{instanceId}/parameters

   Method: PUT

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                  |
      +=======================+=======================+==============================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | nodeId                | Yes                   | Specifies the primary node ID of the DB instance.                                                                            |
      |                       |                       |                                                                                                                              |
      |                       |                       | .. note::                                                                                                                    |
      |                       |                       |                                                                                                                              |
      |                       |                       |    This field is not the DB instance ID. You are advised to use API v3 and the DB instance ID to perform related operations. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

-  Constraints

   -  The values of the edited parameters must be within the default value range of the specified database version. For details about the range of parameter values, see "Modifying Parameters in a Parameter Template" in the *Relational Database Service User Guide*.
   -  If a parameter of the primary DB instance is modified, the corresponding parameter of the standby DB instance is modified simultaneously. You cannot modify the parameters of the standby DB instance. You can modify the parameters of read replicas.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+---------------------------+--------------------------------------------------------------------------------+
      | Name                  | Type                      | Description                                                                    |
      +=======================+===========================+================================================================================+
      | values                | Dictionary data structure | Specifies the parameter value list.                                            |
      |                       |                           |                                                                                |
      |                       |                           | **key** specifies the parameter name. **value** specifies the parameter value. |
      +-----------------------+---------------------------+--------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      PUT https://{Endpoint}/rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/instances/02cf1fd7-24ae-4fec-a621-329ec732e4f6/parameters

   .. code-block:: text

      {
          "values": {
               "connect_timeout": 17,
               "sync_binlog": 1
          }
      }

Normal Response
---------------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                          |
      +=======================+=======================+======================================================================================================================================+
      | shouldRestart         | String                | Indicates whether the parameter needs to be restarted for the modifications to take effect.                                          |
      |                       |                       |                                                                                                                                      |
      |                       |                       | -  The value **1** indicates that the parameter needs to be restarted for the modifications to take effect.                          |
      |                       |                       | -  The value **0** indicates that the parameter does not need to be restarted for the modifications to take effect                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | setParameteResult     | String                | Indicates the parameter modification result.                                                                                         |
      |                       |                       |                                                                                                                                      |
      |                       |                       | -  The value **1** indicates that the modifications are successful on the primary DB instance but failed on the standby DB instance. |
      |                       |                       | -  **0** indicates that the modifications are successful on every DB instance.                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
           "shouldRestart": "0",
           "setParameteResult": "0"
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
