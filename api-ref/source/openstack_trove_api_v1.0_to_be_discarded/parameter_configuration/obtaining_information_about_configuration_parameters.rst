:original_name: rds_07_0011.html

.. _rds_07_0011:

Obtaining Information About Configuration Parameters
====================================================

Function
--------

This API is used to obtain information about parameters that can be modified of a specified database version.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/datastores/versions/{datastore_version_id}/parameters/{parameter_name}

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      +----------------------+-----------+---------------------------------------------------------------------------------------------------------------------------------+
      | Name                 | Mandatory | Description                                                                                                                     |
      +======================+===========+=================================================================================================================================+
      | project_id           | Yes       | Specifies the project ID of a tenant in a region.                                                                               |
      +----------------------+-----------+---------------------------------------------------------------------------------------------------------------------------------+
      | datastore_version_id | Yes       | Specifies the database version ID (**dataStores.id** in the response message in :ref:`Database Version Queries <rds_06_0610>`). |
      +----------------------+-----------+---------------------------------------------------------------------------------------------------------------------------------+
      | parameter_name       | Yes       | Specifies the parameter name.                                                                                                   |
      +----------------------+-----------+---------------------------------------------------------------------------------------------------------------------------------+

-  Restrictions

   Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

.. code-block:: text

   GET https://{Endpoint}/v1.0/375d8d8fad1f43039e23d3b6c0f60a19/datastores/versions/87620726-6802-46c0-9028-a8785e1f1922/parameters/connect_timeout

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+
      | Name                     | Type                                                                                     | Description                                                                |
      +==========================+==========================================================================================+============================================================================+
      | configuration-parameters | List data structure. For details, see :ref:`Table 3 <rds_07_0011__table29072240102314>`. | Indicates all the parameters that can be modified of the database version. |
      +--------------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+

   .. _rds_07_0011__table29072240102314:

   .. table:: **Table 3** configuration-parameters field data structure description

      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | Name                 | Type    | Description                                                                                                          |
      +======================+=========+======================================================================================================================+
      | name                 | String  | Indicates the parameter name.                                                                                        |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | type                 | String  | Indicates the parameter type, which can be **integer**, **string**, **boolean**, **list**, or **float**.             |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | max                  | String  | Indicates the maximum value of the parameter. Returned only when **type** is **integer** or **float**.               |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | min                  | String  | Indicates the minimum value of the parameter. Returned only when **type** is **integer** or **float**.               |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | datastore_version_id | String  | Indicates the database version ID.                                                                                   |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | restart_required     | Boolean | Indicates whether the instance needs to reboot for the parameter to take effect. The value is **true** or **false**. |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
      "configuration-parameters": [
       {
         "name": "connect_timeout",
         "type": "integer",
         "max": "31536000",
         "min": "2",
         "datastore_version_id": "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61",
         "restart_required": "false"
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
