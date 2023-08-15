:original_name: rds_07_0010.html

.. _rds_07_0010:

Obtaining a Parameter List
==========================

Function
--------

This API is used to obtain all the parameters that can be modified of the current database version.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/datastores/versions/{datastore_version_id}/parameters

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

-  Restrictions

   Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

.. code-block:: text

   GET https://{Endpoint}/v1.0/375d8d8fad1f43039e23d3b6c0f60a19/datastores/versions/87620726-6802-46c0-9028-a8785e1f1922/parameters

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+
      | Name                     | Type                                                                                     | Description                                                                |
      +==========================+==========================================================================================+============================================================================+
      | configuration-parameters | List data structure. For details, see :ref:`Table 3 <rds_07_0010__table31447783102154>`. | Indicates all the parameters that can be modified of the database version. |
      +--------------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+

   .. _rds_07_0010__table31447783102154:

   .. table:: **Table 3** configuration-parameters field data structure description

      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | Name                 | Type    | Description                                                                                                          |
      +======================+=========+======================================================================================================================+
      | name                 | String  | Indicates the parameter name.                                                                                        |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | min                  | String  | Indicates the minimum value. Returned only when **type** is **integer** or **float**.                                |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | max                  | String  | Indicates the maximum value. Returned only when **type** is **integer** or **float**.                                |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | type                 | String  | Indicates the parameter type, which can be **integer**, **string**, **boolean**, **list**, or **float**.             |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | restart_required     | Boolean | Indicates whether the instance needs to reboot for the parameter to take effect. The value is **true** or **false**. |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | datastore_version_id | String  | Indicates the database version ID.                                                                                   |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "configuration-parameters" : [ {
          "name" : "autocommit",
          "type" : "boolean",
          "restart_required" : false,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
        }, {
          "name" : "auto_increment_increment",
          "min" : "1",
          "max" : "65535",
          "type" : "integer",
          "restart_required" : false,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
        }, {
          "name" : "auto_increment_offset",
          "min" : "1",
          "max" : "65535",
          "type" : "integer",
          "restart_required" : false,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
        }, {
          "name" : "back_log",
          "min" : "1",
          "max" : "65535",
          "type" : "integer",
          "restart_required" : true,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
          } ]
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
