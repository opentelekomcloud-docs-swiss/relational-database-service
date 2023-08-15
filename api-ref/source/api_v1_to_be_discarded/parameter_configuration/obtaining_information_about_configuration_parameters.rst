:original_name: rds_06_0626.html

.. _rds_06_0626:

Obtaining Information About Configuration Parameters
====================================================

Function
--------

This API is used to obtain information about parameters that can be modified of a specified database version.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/datastores/versions/{datastore_version_id}/parameters/{parameter_name}

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

Request
-------

.. code-block:: text

   GET https://{Endpoint}/rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/datastores/versions/e8a8b8cc-63f8-4fb5-8d4a-24c502317a62/parameters/connect_timeout

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | Name                 | Type    | Description                                                                                                          |
      +======================+=========+======================================================================================================================+
      | name                 | String  | Indicates the parameter name.                                                                                        |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | min                  | String  | Indicates the minimum value of the parameter. Returned only when **type** is **integer** or **float**.               |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | max                  | String  | Indicates the maximum value of the parameter. Returned only when **type** is **integer** or **float**.               |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | restart_required     | Boolean | Indicates whether the instance needs to reboot for the parameter to take effect. The value is **true** or **false**. |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | type                 | String  | Indicates the parameter type. The value can be **integer**, **string**, **boolean**, **float**, or **list**.         |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | value_range          | String  | Specifies the parameter value range and enumerated value.                                                            |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | description          | String  | Indicates the parameter description.                                                                                 |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | datastore_version_id | String  | Indicates the database version ID.                                                                                   |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
          "name": "connect_timeout",
          "min": "2",
          "max": "31536000",
          "restart_required": false,
          "type": "integer",
          "value_range": "2-31536000",
          "description": " Number of seconds that the mysqld server waits for a connect packet before responding with "Bad handshake".
          "datastore_version_id": "f8e67741-e767-4137-b394-3fb8a3fafd2f"
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
