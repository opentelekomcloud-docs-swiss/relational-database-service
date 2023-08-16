:original_name: rds_01_0101.html

.. _rds_01_0101:

Changing DB Instance Specifications
===================================

Function
--------

This API is used to change DB instance specifications.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

.. note::

   Services will be interrupted for 5 to 10 minutes when you change DB instance specifications. Exercise caution when performing this operation.

Constraints
-----------

-  The new DB instance specifications must be different from the original DB instance specifications.
-  The instance specifications can be modified only for DB instances in the **Available** status.
-  The specifications of a DB instance can be changed only to the specifications of the same DB instance type. (For example, the specifications of a single DB instance cannot be changed to those of primary/standby DB instances.)

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/action

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

      +---------------+-----------+--------+------------------------------------------------------------------+
      | Name          | Mandatory | Type   | Description                                                      |
      +===============+===========+========+==================================================================+
      | resize_flavor | Yes       | Object | For details, see :ref:`Table 3 <rds_01_0101__table68501959278>`. |
      +---------------+-----------+--------+------------------------------------------------------------------+

   .. _rds_01_0101__table68501959278:

   .. table:: **Table 3** resize_flavor field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                     |
      +=================+=================+=================+=================================================================================================================================================+
      | spec_code       | Yes             | String          | Specifies the resource specification code.                                                                                                      |
      |                 |                 |                 |                                                                                                                                                 |
      |                 |                 |                 | For details, see **spec_code** in :ref:`Table 3 <rds_06_0002__table66531170>` in section :ref:`Querying Database Specifications <rds_06_0002>`. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

   -  Request example

      .. code-block:: text

         POST https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/action

      **MySQL:**

      .. code-block:: text

         {
             "resize_flavor": {
                 "spec_code": "rds.mysql.s3.xlarge.2"

             }
         }

      **PostgreSQL:**

      .. code-block:: text

         {
             "resize_flavor": {
                 "spec_code": "rds.pg.s3.xlarge.2.ha"

             }
         }

      **Microsoft SQL Server:**

      .. code-block:: text

         {
             "resize_flavor": {
                 "spec_code": "rds.mssql.s3.xlarge"

             }
         }

Response
--------

-  **Pay-per-use**

   -  Normal response

      .. table:: **Table 4** Parameter description

         ====== ====== ======================
         Name   Type   Description
         ====== ====== ======================
         job_id String Indicates the task ID.
         ====== ====== ======================

   -  Example normal response

      .. code-block:: text

         {
             "job_id": "2b414788a6004883a02390e2eb0ea227"
         }

   -  Abnormal response

      For details, see :ref:`Abnormal Request Results <rds_01_0010>`.

Status Code
-----------

-  Normal

   202

-  Abnormal

   For details, see :ref:`Status Codes <rds_10_0200>`.

Error Code
----------

For details, see :ref:`Error Codes <rds_10_0201>`.
