:original_name: rds_06_0002.html

.. _rds_06_0002:

Querying Database Specifications
================================

Function
--------

This API is used to query the database specifications of a specified DB engine version.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/flavors/{database_name}?version_name={version_name}&spec_code={spec_code}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                            |
      +=======================+=======================+========================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                      |
      |                       |                       |                                                                                                                                                                        |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | database_name         | Yes                   | Specifies the DB engine name. Its value can be any of the following and is case-insensitive:                                                                           |
      |                       |                       |                                                                                                                                                                        |
      |                       |                       | -  MySQL                                                                                                                                                               |
      |                       |                       | -  PostgreSQL                                                                                                                                                          |
      |                       |                       | -  SQLServer                                                                                                                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | version_name          | No                    | Specifies the database version. For details about how to obtain the database version, see section :ref:`Querying Version Information About a DB Engine <rds_06_0001>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | spec_code             | No                    | Specifies the specification code.                                                                                                                                      |
      |                       |                       |                                                                                                                                                                        |
      |                       |                       | .. important::                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                        |
      |                       |                       |    NOTICE:                                                                                                                                                             |
      |                       |                       |    For Microsoft SQL Server, only 2017 EE supports cluster instances and read replicas.                                                                                |
      |                       |                       |                                                                                                                                                                        |
      |                       |                       | The format of the specification code is: {*spec code*}{*instance mode*}.                                                                                               |
      |                       |                       |                                                                                                                                                                        |
      |                       |                       | -  *spec code* can be obtained from :ref:`Table 1 <rds_10_0004__table3999164019138>`.                                                                                  |
      |                       |                       | -  *instance mode* can be any of the following:                                                                                                                        |
      |                       |                       |                                                                                                                                                                        |
      |                       |                       |    -  For single DB instances, the value is **null**. Example spe_code: rds.mysql.s3.large.2                                                                           |
      |                       |                       |    -  For primary/standby DB instances, the value is **.ha**. Example spe_code: rds.mysql.s3.large.2.ha                                                                |
      |                       |                       |    -  For read replicas, the value is **.rr**. Example spe_code: rds.mysql.s3.large.2.rr                                                                               |
      |                       |                       |    -  For cluster instances, the value is **.ha**. Example specification code: rds.mssql.s3.large.ha                                                                   |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

.. code-block:: text

   GET https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/flavors/mysql?version_name=5.7&spec_code=rds.mysql.s3.large.2.rr

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------+
      | Name                  | Type                  | Description                                                   |
      +=======================+=======================+===============================================================+
      | flavors               | Array of objects      | Indicates the DB instance specifications information list.    |
      |                       |                       |                                                               |
      |                       |                       | For details, see :ref:`Table 3 <rds_06_0002__table66531170>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------+

   .. _rds_06_0002__table66531170:

   .. table:: **Table 3** flavors field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                         |
      +=======================+=======================+=====================================================================================+
      | vcpus                 | String                | Indicates the CPU size. For example, the value **1** indicates 1 vCPU.              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
      | ram                   | Integer               | Indicates the memory size in GB.                                                    |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
      | spec_code             | String                | Indicates the resource specification code, for example, rds.mysql.s3.large.2.       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
      | instance_mode         | String                | Indicates the DB instance type. Its value can be any of the following:              |
      |                       |                       |                                                                                     |
      |                       |                       | -  **ha**: indicates primary/standby or cluster instances.                          |
      |                       |                       |                                                                                     |
      |                       |                       | -  **replica**: indicates read replicas.                                            |
      |                       |                       |                                                                                     |
      |                       |                       | -  **single**: indicates single DB instances.                                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
      | az_status             | Map<String, String>   | Indicates the specification status in an AZ. Its value can be any of the following: |
      |                       |                       |                                                                                     |
      |                       |                       | -  **normal**: indicates that the specifications in the AZ are available.           |
      |                       |                       | -  **unsupported**: indicates that the specifications are not supported by the AZ.  |
      |                       |                       | -  **sellout**: indicates that the specifications in the AZ are sold out.           |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "flavors": [{
              "vcpus": "2",
              "ram": 4,
              "spec_code": "rds.mysql.s3.large.2.ha",
              "instance_mode": "ha",
              "az_status": {
                  "az1": "normal",
                  "az2": "normal"
              }
          }, {
              "vcpus": "2",
              "ram": 4,
              "spec_code": "rds.mysql.s3.large.2.rr",
              "instance_mode": "replica",
              "az_status": {
                  "az1": "normal",
                  "az2": "normal"
              }
          }]
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
