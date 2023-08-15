:original_name: rds_09_0305.html

.. _rds_09_0305:

Modifying Parameters of a Specified DB Instance
===============================================

Function
--------

This API is used to modify parameters in the parameter template of a specified DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

Constraints
-----------

-  The following DB engines are supported: MySQL, PostgreSQL, and Microsoft SQL Server.
-  For Microsoft SQL Server, only the following editions are supported: Microsoft SQL Server 2014 SE, 2016 SE, and 2016 EE.

-  The values of the edited parameters must be within the default value range of the specified database version. For details about the range of parameter values, see "Modifying Parameters in a Parameter Template" in the *Relational Database Service User Guide*.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/configurations

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type               | Description                                                                               |
      +=================+=================+====================+===========================================================================================+
      | values          | Yes             | Map<String,String> | Specifies the parameter values defined by users based on the default parameter templates. |
      |                 |                 |                    |                                                                                           |
      |                 |                 |                    | For details, see :ref:`Table 3 <rds_09_0305__table12745180163820>`.                       |
      +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------+

   .. _rds_09_0305__table12745180163820:

   .. table:: **Table 3** values field data structure description

      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+
      | Name  | Mandatory | Type   | Description                                                                                                |
      +=======+===========+========+============================================================================================================+
      | key   | Yes       | String | Specifies the parameter name. For example, in **"max_connections": "10"**, the key is **max_connections**. |
      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+
      | value | Yes       | String | Specifies the parameter value. For example, in **"max_connections": "10"**, the value is **10**.           |
      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      PUT https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/configurations

   .. code-block:: text

      {
          "values": {
             "xxx": "10",
             "yyy": "OFF"
          }
      }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

      +-----------------------+-----------------------+-----------------------------------------+
      | Name                  | Type                  | Description                             |
      +=======================+=======================+=========================================+
      | restart_required      | Boolean               | Indicates whether a reboot is required. |
      |                       |                       |                                         |
      |                       |                       | -  **true**: A reboot is required.      |
      |                       |                       | -  **false**: A reboot is not required. |
      +-----------------------+-----------------------+-----------------------------------------+

-  Example normal response

   .. code-block:: text

      {
        "restart_required": false
      }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <rds_01_0010>`.

Status Code
-----------

-  Normal

   200

-  Abnormal

   For details, see :ref:`Status Codes <rds_10_0200>`.

Error Code
----------

For details, see :ref:`Error Codes <rds_10_0201>`.
