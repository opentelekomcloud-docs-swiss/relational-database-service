:original_name: rds_07_0018.html

.. _rds_07_0018:

Adding Custom Parameters
========================

Function
--------

This API is used to add parameter information to a parameter template identified by a specified ID.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/configurations/{id}

   Method: PATCH

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      id         Yes       Specifies the parameter template ID.
      ========== ========= =================================================

-  Restrictions

   -  Currently, the DB engines MySQL and PostgreSQL support modifying parameter templates.
   -  The values of the newly added parameters must be within the default value range of the specified database version. For details about the range of parameter values, see section "Modifying Parameters in a Parameter Template" in the *Relational Database Service User Guide*.
   -  Parameter template modifications will take effect for DB instances to which the parameter template applies. Some modifications take effect only after the DB instance reboots.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +---------------+-----------+------------------------------------------------------------------------------------------------+------------------------------------------+
      | Name          | Mandatory | Type                                                                                           | Description                              |
      +===============+===========+================================================================================================+==========================================+
      | configuration | Yes       | Dictionary data structure. For details, see :ref:`Table 3 <rds_07_0018__table23308179103438>`. | Specifies the parameter template object. |
      +---------------+-----------+------------------------------------------------------------------------------------------------+------------------------------------------+

   .. _rds_07_0018__table23308179103438:

   .. table:: **Table 3** configuration field data structure description

      +--------+-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+
      | Name   | Mandatory | Type                                                                                           | Description                                                                              |
      +========+===========+================================================================================================+==========================================================================================+
      | values | No        | Dictionary data structure. For details, see :ref:`Table 4 <rds_07_0018__table25655849103438>`. | Specifies the parameter values defined by users based on the default parameter template. |
      +--------+-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+

   .. _rds_07_0018__table25655849103438:

   .. table:: **Table 4** values field data structure description

      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+
      | Name  | Mandatory | Type   | Description                                                                                                |
      +=======+===========+========+============================================================================================================+
      | key   | No        | String | Specifies the parameter name. For example, in **"max_connections": "10"**, the key is **max_connections**. |
      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+
      | value | No        | String | Specifies the parameter value. For example, in **"max_connections": "10"**, the value is **10**.           |
      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      PATCH https://{Endpoint}/v1.0/375d8d8fad1f43039e23d3b6c0f60a19/configurations/07fc12a8e0e94df7a3fcf53d0b5e1605pr01

   .. code-block:: text

      {
        "configuration": {
          "values": {
             "max_connections": "10",
             "autocommit": "OFF"
          }
        }
      }

Normal Response
---------------

.. code-block:: text

   {
     "errCode": "RDS.0041",
     "externalMessage": "Operation successful."
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
