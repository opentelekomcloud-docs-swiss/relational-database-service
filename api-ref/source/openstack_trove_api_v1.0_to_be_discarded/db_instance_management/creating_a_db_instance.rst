:original_name: rds_07_0001.html

.. _rds_07_0001:

Creating a DB Instance
======================

Function
--------

This API is used to create a single RDS DB instance or a read replica.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/instances

   Method: POST

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

-  Restrictions

   Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
      | Name                  | Type                                                                                                                      | Description                                     |
      +=======================+===========================================================================================================================+=================================================+
      | instance              | Dictionary data structure.                                                                                                | Specifies the detailed DB instance information. |
      |                       |                                                                                                                           |                                                 |
      |                       | For details on the field description when creating a single DB instance, see :ref:`Table 3 <rds_07_0001__table11236435>`. |                                                 |
      |                       |                                                                                                                           |                                                 |
      |                       | For details on the field description when creating a read replica, see :ref:`Table 4 <rds_07_0001__table32692621183156>`. |                                                 |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+

   .. _rds_07_0001__table11236435:

   .. table:: **Table 3** instance field data structure (creating a single DB instance)

      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name              | Mandatory       | Type                                                                                            | Description                                                                                                                                                                                                                                                |
      +===================+=================+=================================================================================================+============================================================================================================================================================================================================================================================+
      | datastore         | Yes             | Dictionary data structure. For details, see :ref:`Table 5 <rds_07_0001__table1282893518295>`.   | Specifies the database information.                                                                                                                                                                                                                        |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name              | Yes             | String                                                                                          | Specifies the DB instance name.                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | The DB instance name of the same type must be unique for the same tenant.                                                                                                                                                                                  |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | Valid value:                                                                                                                                                                                                                                               |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | The value must be 4 to 64 characters in length and start with a letter. It can contain only uppercase letters, lowercase letters, digits, underscores (_), and hyphens (-).                                                                                |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavorRef         | Yes             | String                                                                                          | Specifies the specification ID (**str_id** in the response message in :ref:`Table 3 <rds_07_0008__table5932144310813>` in section :ref:`Obtaining All DB Instance Specifications <rds_07_0008>`).                                                          |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | Valid value:                                                                                                                                                                                                                                               |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                                                                                                                             |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | users             | Yes             | List data structure. For details, see :ref:`Table 6 <rds_07_0001__table52086869182956>`.        | Specifies the user information.                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | It must contain the administrator username (for mysql and postgres, the administrator username is **root**) and the administrator password.                                                                                                                |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | volume            | Yes             | Dictionary data structure. For details, see :ref:`Table 7 <rds_07_0001__table812499818308>`.    | Specifies the volume information.                                                                                                                                                                                                                          |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | configuration     | No              | String                                                                                          | Specifies the configuration parameter set used for initializing the database. For details about how to obtain this parameter value, see **configurations.id** in the response message in section :ref:`Obtaining a Parameter Template List <rds_07_0013>`. |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | Valid value: The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                                                                                                                |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | databases         | No              | List data structure. For details, see :ref:`Table 8 <rds_07_0001__table10656503>`.              | Currently, this parameter is not supported.                                                                                                                                                                                                                |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | modules           | No              | Array                                                                                           | Currently, this parameter is not supported.                                                                                                                                                                                                                |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | nics              | No              | Array. For details, see :ref:`Table 9 <rds_07_0001__table2179128>`.                             | Specifies the nics information. For details about how to obtain this parameter value, see section "Subnet" in the *Virtual Private Cloud API Reference*.                                                                                                   |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | If this parameter is not specified, RDS will query the VPC, subnet, and security group of the tenant. By default, the first query result is the parameter value.                                                                                           |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone | No              | String                                                                                          | Specifies the AZ ID.                                                                                                                                                                                                                                       |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | Valid value:                                                                                                                                                                                                                                               |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | Obtain the parameter value from the enterprise administrator.                                                                                                                                                                                              |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc               | No              | String                                                                                          | Specifies the VPC ID. For details about how to obtain this parameter value, see section "Virtual Private Cloud" in the *Virtual Private Cloud API Reference*.                                                                                              |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | Valid value:                                                                                                                                                                                                                                               |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                                                                                                                             |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | restorePoint      | No              | Dictionary data structure. For details, see :ref:`Table 10 <rds_07_0001__table41613092172617>`. | Specifies the configuration parameter for restoring data to a new DB instance.                                                                                                                                                                             |
      |                   |                 |                                                                                                 |                                                                                                                                                                                                                                                            |
      |                   |                 |                                                                                                 | Currently, this parameter is not supported.                                                                                                                                                                                                                |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | cluster_config    | No              | Dictionary data structure. For details, see :ref:`Table 11 <rds_07_0001__table19785388173024>`. | Currently, this parameter is not supported.                                                                                                                                                                                                                |
      +-------------------+-----------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_07_0001__table32692621183156:

   .. table:: **Table 4** instance field data structure description (creating a read replica)

      +-----------------+-----------------+-----------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type                                                                                          | Description                                                                                                                                                                                       |
      +=================+=================+===============================================================================================+===================================================================================================================================================================================================+
      | datastore       | Yes             | Dictionary data structure. For details, see :ref:`Table 5 <rds_07_0001__table1282893518295>`. | Specifies the database information. Its value must be the same as the primary DB instance.                                                                                                        |
      +-----------------+-----------------+-----------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name            | Yes             | String                                                                                        | Specifies the DB instance name.                                                                                                                                                                   |
      |                 |                 |                                                                                               |                                                                                                                                                                                                   |
      |                 |                 |                                                                                               | The DB instance name of the same type must be unique for the same tenant.                                                                                                                         |
      |                 |                 |                                                                                               |                                                                                                                                                                                                   |
      |                 |                 |                                                                                               | Valid value:                                                                                                                                                                                      |
      |                 |                 |                                                                                               |                                                                                                                                                                                                   |
      |                 |                 |                                                                                               | The value must be 4 to 64 characters in length and start with a letter. It can contain only letters, digits, underscores (_), and hyphens (-).                                                    |
      +-----------------+-----------------+-----------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavorRef       | Yes             | String                                                                                        | Specifies the specification ID (**str_id** in the response message in :ref:`Table 3 <rds_07_0008__table5932144310813>` in section :ref:`Obtaining All DB Instance Specifications <rds_07_0008>`). |
      |                 |                 |                                                                                               |                                                                                                                                                                                                   |
      |                 |                 |                                                                                               | Valid value:                                                                                                                                                                                      |
      |                 |                 |                                                                                               |                                                                                                                                                                                                   |
      |                 |                 |                                                                                               | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                                                                    |
      +-----------------+-----------------+-----------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | volume          | Yes             | Dictionary data structure. For details, see :ref:`Table 7 <rds_07_0001__table812499818308>`.  | Specifies the volume information. The volume information must be the same as that of the primary DB instance.                                                                                     |
      +-----------------+-----------------+-----------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | slave_of        | No              | String                                                                                        | Specifies the read replica configuration parameter. It is used to create a read replica of a primary DB instance specified by **slave_of**.                                                       |
      |                 |                 |                                                                                               |                                                                                                                                                                                                   |
      |                 |                 |                                                                                               | Valid value: The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified. Only the primary DB instance ID is valid.             |
      +-----------------+-----------------+-----------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | replica_of      | Yes             | String                                                                                        | Specifies the read replica configuration parameter. It is used to create a read replica of a primary DB instance specified by **replica_of**.                                                     |
      |                 |                 |                                                                                               |                                                                                                                                                                                                   |
      |                 |                 |                                                                                               | Valid value: The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified. Only the primary DB instance ID is valid.             |
      |                 |                 |                                                                                               |                                                                                                                                                                                                   |
      |                 |                 |                                                                                               | If both **slave_of** and **replica_of** exist, use **replica_of** first.                                                                                                                          |
      +-----------------+-----------------+-----------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | replica_count   | No              | Int                                                                                           | Specifies the number of read replicas.                                                                                                                                                            |
      |                 |                 |                                                                                               |                                                                                                                                                                                                   |
      |                 |                 |                                                                                               | Currently, creating multiple read replicas at a time is not supported.                                                                                                                            |
      |                 |                 |                                                                                               |                                                                                                                                                                                                   |
      |                 |                 |                                                                                               | Valid value: **1** or not contained in the request.                                                                                                                                               |
      +-----------------+-----------------+-----------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_07_0001__table1282893518295:

   .. table:: **Table 5** datastore field data structure description

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                               |
      +=================+=================+=================+===========================================================================================================+
      | type            | Yes             | String          | Specifies the DB engine.                                                                                  |
      |                 |                 |                 |                                                                                                           |
      |                 |                 |                 | Currently, the DB engines MySQL and PostgreSQL are supported.                                             |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
      | version         | Yes             | String          | Specifies the database version.                                                                           |
      |                 |                 |                 |                                                                                                           |
      |                 |                 |                 | -  MySQL databases support 5.6, 5.7 and 8.0. Example value: MySQL-5.7                                     |
      |                 |                 |                 | -  PostgreSQL databases support 16, 15, 14, 13, 12, and 11. Example value: PostgreSQL-12                  |
      |                 |                 |                 |                                                                                                           |
      |                 |                 |                 | For details about supported database versions, see section :ref:`Database Version Queries <rds_06_0610>`. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+

   .. _rds_07_0001__table52086869182956:

   .. table:: **Table 6** users field data structure description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                |
      +=================+=================+=================+============================================================================================================================================================================+
      | name            | Yes             | String          | Specifies the database username. Currently, the database username for mysql and postgres is **root**.                                                                      |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | password        | Yes             | String          | Specifies the password of the database user.                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                            |
      |                 |                 |                 | The value cannot be empty and should contain 8 to 32 characters, including uppercase and lowercase letters, digits, and the following special characters: ``~!@#%^*-_=+?`` |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | databases       | No              | Array           | Currently, this parameter is not supported.                                                                                                                                |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_07_0001__table812499818308:

   .. table:: **Table 7** volume field data structure description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                      |
      +=================+=================+=================+==================================================================================+
      | type            | No              | String          | Specifies the volume type.                                                       |
      |                 |                 |                 |                                                                                  |
      |                 |                 |                 | Its value can be any of the following and is case-sensitive:                     |
      |                 |                 |                 |                                                                                  |
      |                 |                 |                 | -  **ULTRAHIGH**: indicates the SSD type.                                        |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+
      | size            | Yes             | Int             | Specifies the volume size in gigabytes (GB).                                     |
      |                 |                 |                 |                                                                                  |
      |                 |                 |                 | Its value must be a multiple of 10 and the value range is from 40 GB to 4000 GB. |
      |                 |                 |                 |                                                                                  |
      |                 |                 |                 | .. note::                                                                        |
      |                 |                 |                 |                                                                                  |
      |                 |                 |                 |    If the size is a decimal value, the system will round it down.                |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+

   .. _rds_07_0001__table10656503:

   .. table:: **Table 8** databases field data structure description (not supported currently)

      ============ ========= ====== ============================
      Name         Mandatory Type   Description
      ============ ========= ====== ============================
      name         Yes       String Specifies the database name.
      collate      No        String Specifies the database code.
      characterSet No        String Specifies the database code.
      ============ ========= ====== ============================

   .. _rds_07_0001__table2179128:

   .. table:: **Table 9** nics field data structure description

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                       |
      +=================+=================+=================+===================================================================================================================================================================================================+
      | net-id          | No              | String          | Specifies the subnet ID obtained from the VPC.                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                   |
      |                 |                 |                 | Valid value:                                                                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                                   |
      |                 |                 |                 | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                   |
      |                 |                 |                 | .. note::                                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                   |
      |                 |                 |                 |    RDS will query the VPC associated with the specified net-id, associate the VPC with the DB instance, and query the security group based on the VPC. Then, RDS sets the queried security group. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | securityGroupId | No              | String          | Valid value:                                                                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                                   |
      |                 |                 |                 | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                                                                    |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_07_0001__table41613092172617:

   .. table:: **Table 10** restorePoint field data structure description (not supported currently)

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                 |
      +=================+=================+=================+=============================================================================================================================================+
      | backupRef       | Yes             | String          | Specifies the full backup file.                                                                                                             |
      |                 |                 |                 |                                                                                                                                             |
      |                 |                 |                 | Valid value: The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_07_0001__table19785388173024:

   .. table:: **Table 11** cluster_config field data structure description (not supported currently)

      ==== ========= ====== =========================
      Name Mandatory Type   Description
      ==== ========= ====== =========================
      id   Yes       String Specifies the cluster ID.
      ==== ========= ====== =========================

-  Request example

   .. code-block:: text

      POST https://{Endpoint}/v1.0/375d8d8fad1f43039e23d3b6c0f60a19/instances

   Creating a single DB instance:

   .. code-block:: text

      {
          "instance": {
              "datastore": {
                             "type": "MySQL",
                             "version": "MySQL-5.7"
                           },
              "name": "json-rack-instance",
              "flavorRef": "123",
              "users": [
                          {
                            "name": "root",
                            "password": "Demo@12345678"
                          }
                       ],
              "volume": {
                          "size": 100
                        },
              "configuration" : "ft26458f-d9f8-4cab-8fe1-cb8704fbo9bp",
              "nics":[
                      {
                       "net-id": "3226458f-d9f8-4cab-8fe1-cb8704fb9fb8",
                       "securityGroupId":"fpo6458f-d9f8-4cab-8fe1-cb8704fb9fb8"
                       }
                     ],
              "availability_zone": "az1pod1",
              "vpc":"98ik458f-d9f8-4cab-8fe1-cb8704fb9fbb"
             }
       }

   Creating a read replica:

   .. code-block:: text

      {
          "instance": {
              "datastore": {
                  "type": "MySQL",
                  "version": "MySQL-5.7"
              },
              "name": "json-rack-instance",
              "flavorRef": "123",
              "volume": {
                  "size": 100
              },
              "replica_of": "123",
              "replica_count":1
          }
      }

Normal Response
---------------

-  Parameter description

   .. table:: **Table 12** Parameter description

      +----------+---------------------------+----------------------------------------+
      | Name     | Type                      | Description                            |
      +==========+===========================+========================================+
      | instance | Dictionary data structure | Indicates the DB instance information. |
      +----------+---------------------------+----------------------------------------+

   .. table:: **Table 13** instance field data structure description

      +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name      | Type                                                                                           | Description                                                                                                                                                            |
      +===========+================================================================================================+========================================================================================================================================================================+
      | status    | String                                                                                         | Indicates the DB instance status.                                                                                                                                      |
      +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | updated   | String                                                                                         | Indicates the DB instance updated time.                                                                                                                                |
      +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name      | String                                                                                         | Instances the DB instance name. When a single DB instance is created, its name is automatically added with the suffix "_node0", for example, rds-test-openstack_node0. |
      +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | links     | List data structure. For details, see :ref:`Table 14 <rds_07_0001__table35796249181358>`.      | Indicates the DB instance information link.                                                                                                                            |
      +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created   | String                                                                                         | Indicates the DB instance creation time.                                                                                                                               |
      +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id        | String                                                                                         | Indicates the DB instance ID.                                                                                                                                          |
      +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | volume    | Dictionary data structure. For details, see :ref:`Table 15 <rds_07_0001__table5589436418437>`. | Indicates the DB instance volume information.                                                                                                                          |
      +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavor    | Dictionary data structure. For details, see :ref:`Table 16 <rds_07_0001__table4806207618447>`. | Indicates the DB instance specifications.                                                                                                                              |
      +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore | Dictionary data structure. For details, see :ref:`Table 17 <rds_07_0001__table629209691859>`.  | Indicates the DB engine information.                                                                                                                                   |
      +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_07_0001__table35796249181358:

   .. table:: **Table 14** links field data structure description

      ==== ====== ================================================
      Name Type   Description
      ==== ====== ================================================
      href String Indicates the link address. Its value is **""**.
      rel  String Its value is **self** or **bookmark**.
      ==== ====== ================================================

   .. _rds_07_0001__table5589436418437:

   .. table:: **Table 15** volume field data structure description

      ==== ==== ================================
      Name Type Description
      ==== ==== ================================
      size Int  Indicates the volume size in GB.
      ==== ==== ================================

   .. _rds_07_0001__table4806207618447:

   .. table:: **Table 16** flavor field data structure description

      +-------+-------------------------------------------------------------------------------------------+-----------------------------------------------+
      | Name  | Type                                                                                      | Description                                   |
      +=======+===========================================================================================+===============================================+
      | id    | String                                                                                    | Indicates the specification ID.               |
      +-------+-------------------------------------------------------------------------------------------+-----------------------------------------------+
      | links | List data structure. For details, see :ref:`Table 14 <rds_07_0001__table35796249181358>`. | Indicates the DB instance specification link. |
      +-------+-------------------------------------------------------------------------------------------+-----------------------------------------------+

   .. _rds_07_0001__table629209691859:

   .. table:: **Table 17** datastore field data structure description

      ======= ====== =====================================================
      Name    Type   Description
      ======= ====== =====================================================
      type    String Indicates the DB engine.
      version String Indicates the database version, such as MySQL-5.6.33.
      ======= ====== =====================================================

-  Response example

   .. code-block:: text

      {
        "instance": {
          "status": "BUILD",
          "updated": "2017-05-06T05:55:03",
          "name": "creat-trove-instance-28-MySQL-1-1",
          "links": [
            {
              "href": "",
              "rel": "self"
            },
            {
              "href": "",
              "rel": "bookmark"
            }
          ],
          "created": "2017-05-06T05:55:03",
          "id": "c90c1234-f687-462a-a6bd-cec35919c096",
          "volume": {
            "size": 100
          },
          "flavor": {
            "id": "99001234-dfc2-4418-b224-fea05d358ce3",
            "links": [
              {
                "href": "",
                "rel": "self"
              },
              {
                "href": "",
                "rel": "bookmark"
              }
            ]
          },
          "datastore": {
            "type": "MySQL",
            "version": "MySQL-5.7"
          }
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
