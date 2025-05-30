:original_name: rds_06_0616.html

.. _rds_06_0616:

Creating a DB Instance
======================

Function
--------

This API is used to create a single DB instance, primary/standby DB instances, or a read replica.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances

   Method: POST

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
      | Name                  | Type                                                                                                                                        | Description                                                              |
      +=======================+=============================================================================================================================================+==========================================================================+
      | instance              | Dictionary data structure.                                                                                                                  | Specifies the detailed DB instance information.                          |
      |                       |                                                                                                                                             |                                                                          |
      |                       | For details on the field description when creating single or primary/standby DB instances, see :ref:`Table 3 <rds_06_0616__table11236435>`. | .. important::                                                           |
      |                       |                                                                                                                                             |                                                                          |
      |                       | For details on the field description when creating a read replica, see :ref:`Table 4 <rds_06_0616__table228903751753>`.                     |    NOTICE:                                                               |
      |                       |                                                                                                                                             |    RDS for Microsoft SQL Server does not support creating read replicas. |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+

   .. _rds_06_0616__table11236435:

   .. table:: **Table 3** instance field data structure (creating single or primary/standby DB instances)

      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name             | Mandatory       | Type                                                                                          | Description                                                                                                                                                                |
      +==================+=================+===============================================================================================+============================================================================================================================================================================+
      | name             | Yes             | String                                                                                        | Specifies the DB instance name.                                                                                                                                            |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | The DB instance name of the same type must be unique for the same tenant.                                                                                                  |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | Valid value:                                                                                                                                                               |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | The parameter must be 4 to 64 characters long, start with a letter, and contain only letters (case-insensitive), digits, hyphens (-), and underscores (_).                 |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore        | Yes             | Dictionary data structure. For details, see :ref:`Table 5 <rds_06_0616__table64243102>`.      | Specifies the database information.                                                                                                                                        |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavorRef        | Yes             | String                                                                                        | Specifies the specification ID (**flavors.id** in the response message in section :ref:`Obtaining All DB Instance Specifications <rds_06_0623>`).                          |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | Valid value:                                                                                                                                                               |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                                             |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | volume           | Yes             | Dictionary data structure. For details, see :ref:`Table 6 <rds_06_0616__table10656503>`.      | Specifies the volume information.                                                                                                                                          |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region           | Yes             | String                                                                                        | Specifies the region ID.                                                                                                                                                   |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | Valid value:                                                                                                                                                               |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | The value cannot be empty. Obtain the parameter value from the enterprise administrator.                                                                                   |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availabilityZone | Yes             | String                                                                                        | Specifies the AZ ID.                                                                                                                                                       |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | Valid value:                                                                                                                                                               |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | The value cannot be empty. Obtain the parameter value from the enterprise administrator.                                                                                   |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc              | Yes             | String                                                                                        | Specifies the VPC ID. For details about how to obtain this parameter value, see section "Virtual Private Cloud" in the *Virtual Private Cloud API Reference*.              |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | Valid value:                                                                                                                                                               |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                                             |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | nics             | Yes             | Dictionary data structure. For details, see :ref:`Table 7 <rds_06_0616__table2179128>`.       | Specifies the nics information. For details about how to obtain this parameter value, see section "Subnet" in the *Virtual Private Cloud API Reference*.                   |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | securityGroup    | Yes             | Dictionary data structure. For details, see :ref:`Table 8 <rds_06_0616__table4150710>`.       | Specifies the security group which the RDS DB instance belongs to.                                                                                                         |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | For details about how to obtain this parameter value, see section "Security Group" in the *Virtual Private Cloud API Reference*.                                           |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | dbPort           | No              | Int                                                                                           | Specifies the database port information.                                                                                                                                   |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | -  The MySQL database port ranges from 1024 to 65535 (excluding 12017 and 33071, which are occupied by the RDS system and cannot be used).                                 |
      |                  |                 |                                                                                               | -  The PostgreSQL database port ranges from 2100 to 9500.                                                                                                                  |
      |                  |                 |                                                                                               | -  The Microsoft SQL Server database port can be 1433 or ranges from 2100 to 9500, excluding 5355 and 5985.                                                                |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | If this parameter is not set, the default value is as follows:                                                                                                             |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | -  For MySQL databases, the default value is **3306**.                                                                                                                     |
      |                  |                 |                                                                                               | -  For PostgreSQL databases, the default value is **5432**.                                                                                                                |
      |                  |                 |                                                                                               | -  For Microsoft SQL Server, the default value is **1433**.                                                                                                                |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backupStrategy   | No              | Dictionary data structure. For details, see :ref:`Table 9 <rds_06_0616__table49774232>`.      | Specifies the advanced backup policy.                                                                                                                                      |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | dbRtPd           | Yes             | String                                                                                        | Specifies the password for user **root** of the database.                                                                                                                  |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | Valid value:                                                                                                                                                               |
      |                  |                 |                                                                                               |                                                                                                                                                                            |
      |                  |                 |                                                                                               | The value cannot be empty and should contain 8 to 32 characters, including uppercase and lowercase letters, digits, and the following special characters: ``~!@#%^*-_=+?`` |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ha               | No              | Dictionary data structure. For details, see :ref:`Table 10 <rds_06_0616__table622861661833>`. | Specifies the HA configuration parameters, which are used when creating primary/standby DB instances.                                                                      |
      +------------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_06_0616__table228903751753:

   .. table:: **Table 4** instance field data structure description (creating a read replica)

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                |
      +=================+=================+=================+============================================================================================================================================================+
      | name            | Yes             | String          | Specifies the DB instance name.                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                            |
      |                 |                 |                 | The DB instance name of the same type must be unique for the same tenant.                                                                                  |
      |                 |                 |                 |                                                                                                                                                            |
      |                 |                 |                 | Valid value:                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                            |
      |                 |                 |                 | The parameter must be 4 to 64 characters long, start with a letter, and contain only letters (case-insensitive), digits, hyphens (-), and underscores (_). |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavorRef       | Yes             | String          | Specifies the specification ID (**flavors.id** in the response message in section :ref:`Obtaining All DB Instance Specifications <rds_06_0623>`).          |
      |                 |                 |                 |                                                                                                                                                            |
      |                 |                 |                 | Valid value:                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                            |
      |                 |                 |                 | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                             |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | replicaOf       | Yes             | String          | Specifies the read replica configuration parameter. It is used to create a read replica of a primary DB instance specified by **replicaOf**                |
      |                 |                 |                 |                                                                                                                                                            |
      |                 |                 |                 | Valid value:                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                            |
      |                 |                 |                 | Only the primary DB instance ID is valid.                                                                                                                  |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_06_0616__table64243102:

   .. table:: **Table 5** datastore field data structure description

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                               |
      +=================+=================+=================+===========================================================================================================+
      | type            | Yes             | String          | Specifies the DB engine. Currently, the following DB engines are supported:                               |
      |                 |                 |                 |                                                                                                           |
      |                 |                 |                 | -  MySQL                                                                                                  |
      |                 |                 |                 | -  PostgreSQL                                                                                             |
      |                 |                 |                 | -  SQLServer                                                                                              |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
      | version         | Yes             | String          | Specifies the database version.                                                                           |
      |                 |                 |                 |                                                                                                           |
      |                 |                 |                 | -  MySQL databases support 5.6 and 5.7. Example value: 5.7                                                |
      |                 |                 |                 | -  PostgreSQL databases support 16, 15, 14, 13, 12, and 11. Example value: 12                             |
      |                 |                 |                 |                                                                                                           |
      |                 |                 |                 | For details about supported database versions, see section :ref:`Database Version Queries <rds_06_0610>`. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+

   .. _rds_06_0616__table10656503:

   .. table:: **Table 6** volume field data structure description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                              |
      +=================+=================+=================+==========================================================================================================+
      | type            | Yes             | String          | Specifies the volume type.                                                                               |
      |                 |                 |                 |                                                                                                          |
      |                 |                 |                 | Its value can be any of the following and is case-sensitive:                                             |
      |                 |                 |                 |                                                                                                          |
      |                 |                 |                 | -  **ULTRAHIGH**: indicates the SSD type.                                                                |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
      | size            | Yes             | Int             | Specifies the volume size.                                                                               |
      |                 |                 |                 |                                                                                                          |
      |                 |                 |                 | Its value range is from 40 GB to 4,000 GB. The value must be a multiple of 10.                           |
      |                 |                 |                 |                                                                                                          |
      |                 |                 |                 | .. important::                                                                                           |
      |                 |                 |                 |                                                                                                          |
      |                 |                 |                 |    NOTICE:                                                                                               |
      |                 |                 |                 |    The volume size of the read replica must be greater than or equal to that of the primary DB instance. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+

   .. _rds_06_0616__table2179128:

   .. table:: **Table 7** nics field data structure description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                    |
      +=================+=================+=================+================================================================================================================================+
      | subnetId        | Yes             | String          | Specifies the network ID of the subnet obtained from VPC.                                                                      |
      |                 |                 |                 |                                                                                                                                |
      |                 |                 |                 | Valid value:                                                                                                                   |
      |                 |                 |                 |                                                                                                                                |
      |                 |                 |                 | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_06_0616__table4150710:

   .. table:: **Table 8** securityGroup field data structure description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                    |
      +=================+=================+=================+================================================================================================================================+
      | id              | Yes             | String          | Valid value:                                                                                                                   |
      |                 |                 |                 |                                                                                                                                |
      |                 |                 |                 | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_06_0616__table49774232:

   .. table:: **Table 9** backupStrategy field data structure description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                                      |
      +=================+=================+=================+==================================================================================================================================================================================================================================================+
      | startTime       | Yes             | String          | Specifies the backup start time that has been set.                                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                  |
      |                 |                 |                 | Valid value:                                                                                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                  |
      |                 |                 |                 | The value cannot be empty. It must use the hh:mm:ss format and must be valid. The time is in the UTC format.                                                                                                                                     |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | keepDays        | No              | Int             | Specifies the number of days to retain the generated backup files.                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                  |
      |                 |                 |                 | The value range is from 0 to 732. If this parameter is not specified or set to **0**, the automated backup policy is disabled. To extend the retention period, contact the administrator. Automated backups can be retained for up to 2562 days. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_06_0616__table622861661833:

   .. table:: **Table 10** ha field data structure description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                          |
      +=================+=================+=================+======================================================================================================================================================================+
      | enable          | Yes             | Boolean         | Specifies the HA configuration parameter.                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                      |
      |                 |                 |                 | Valid value:                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                      |
      |                 |                 |                 | The value is **true** or **false**. The value **true** indicates creating primary/standby DB instances. The value **false** indicates creating a single DB instance. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | replicationMode | Yes             | String          | Specifies the replication mode for the standby DB instance.                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                      |
      |                 |                 |                 | The value cannot be empty.                                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                                      |
      |                 |                 |                 | -  For MySQL, the value is **async** or **semisync**.                                                                                                                |
      |                 |                 |                 | -  For PostgreSQL, the value is **async** or **sync**.                                                                                                               |
      |                 |                 |                 | -  For Microsoft SQL Server, the value is **sync**.                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                      |
      |                 |                 |                 | .. note::                                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                      |
      |                 |                 |                 |    -  **async** indicates the asynchronous replication mode.                                                                                                         |
      |                 |                 |                 |    -  **semisync** indicates the semi-synchronous replication mode.                                                                                                  |
      |                 |                 |                 |    -  **sync** indicates the synchronous replication mode.                                                                                                           |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   The values of **region** and **availabilityZone** are used as examples.

-  Request example

   .. code-block:: text

      POST https://{Endpoint}/rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/instances

   Creating a single DB instance:

   .. code-block:: text

      {
          "instance": {
              "name": "trove-instance-rep2",
              "datastore": {
                  "type": "MySQL",
                  "version": "5.7"
              },
              "flavorRef": "bf07a6d4-844a-4023-a776-fc5c5fb71fb4",
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "region": "aaa",
              "availabilityZone": "bbb",
              "vpc": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
              "nics": {
                "subnetId": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f"
              },
              "securityGroup": {
                  "id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5"
              },
              "dbPort": 3306,
              "backupStrategy": {
                  "startTime": "01:00:00",
                  "keepDays": 3
              },
              "dbRtPd": "Test@123"
          }
      }

   Creating primary/standby DB instances:

   .. code-block:: text

      {
          "instance": {
              "name": "trove-instance-ha",
              "datastore": {
                  "type": "MySQL",
                  "version": "5.7"
              },
              "flavorRef": "bf07a6d4-844a-4023-a776-fc5c5fb71fb4",
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "region": "aaa",
              "availabilityZone": "bbb",
              "vpc": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
              "nics": {
                "subnetId": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f"
              },
              "securityGroup": {
                  "id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5"
              },
              "dbPort": 3306,
              "backupStrategy": {
                  "startTime": "01:00:00",
                  "keepDays": 3
              },
              "dbRtPd": "Test@123",
              "ha": {
                  "enable": true,
                  "replicationMode": "async"
              }
          }
      }

   Creating a read replica:

   .. code-block:: text

      {
          "instance": {
              "name": "trove-instance-replica2",
              "flavorRef": "bf07a6d4-844a-4023-a776-fc5c5fb71fb4",
              "replicaOf": "373af3b8-8f44-44f6-bb90-85f1c32c50d6"
          }
      }

Normal Response
---------------

-  Parameter description

   .. table:: **Table 11** Parameter description

      +----------+-------------------------------------------------------------------------------------------+----------------------------------------+
      | Name     | Type                                                                                      | Description                            |
      +==========+===========================================================================================+========================================+
      | instance | Dictionary data structure. For details, see :ref:`Table 12 <rds_06_0616__table27245651>`. | Indicates the DB instance information. |
      +----------+-------------------------------------------------------------------------------------------+----------------------------------------+

   .. _rds_06_0616__table27245651:

   .. table:: **Table 12** instance field data structure description

      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                                                                                            | Description                                                                                                                  |
      +=======================+=================================================================================================+==============================================================================================================================+
      | id                    | String                                                                                          | Indicates the primary node ID of the DB instance.                                                                            |
      |                       |                                                                                                 |                                                                                                                              |
      |                       |                                                                                                 | .. note::                                                                                                                    |
      |                       |                                                                                                 |                                                                                                                              |
      |                       |                                                                                                 |    This field is not the DB instance ID. You are advised to use API v3 and the DB instance ID to perform related operations. |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                                                                                          | Indicates the DB instance status. The value is **BUILD**.                                                                    |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                                                                                          | Indicates the created DB instance name.                                                                                      |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | created               | String                                                                                          | Indicates the creation time in the "yyyy-mm-dd Thh:mm:ssZ" format.                                                           |
      |                       |                                                                                                 |                                                                                                                              |
      |                       |                                                                                                 | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.           |
      |                       |                                                                                                 |                                                                                                                              |
      |                       |                                                                                                 | .. note::                                                                                                                    |
      |                       |                                                                                                 |                                                                                                                              |
      |                       |                                                                                                 |    The value is empty when the DB instance is being created. After the DB instance is created, the value is not empty.       |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | hostname              | String                                                                                          | Indicates the DB instance connection address. It is a blank string.                                                          |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                                                                                          | Indicates the DB instance type, which can be **master** or **readreplica**.                                                  |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | region                | String                                                                                          | Same as the request parameter.                                                                                               |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | updated               | String                                                                                          | Indicates the updated time, which is the same as **created**.                                                                |
      |                       |                                                                                                 |                                                                                                                              |
      |                       |                                                                                                 | .. note::                                                                                                                    |
      |                       |                                                                                                 |                                                                                                                              |
      |                       |                                                                                                 |    The value is empty when the DB instance is being created. After the DB instance is created, the value is not empty.       |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | availabilityZone      | String                                                                                          | Same as the request parameter.                                                                                               |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | vpc                   | String                                                                                          | Same as the request parameter.                                                                                               |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | nics                  | Dictionary data structure. For details, see :ref:`Table 13 <rds_06_0616__table41614513165139>`. | Indicates the nics information.                                                                                              |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | securityGroup         | Dictionary data structure. For details, see :ref:`Table 14 <rds_06_0616__table255609017350>`.   | Indicates the security group information.                                                                                    |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | flavor                | Dictionary data structure. For details, see :ref:`Table 15 <rds_06_0616__table223791861780>`.   | Indicates the DB instance specifications.                                                                                    |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | volume                | String                                                                                          | Same as the request parameter.                                                                                               |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | dbPort                | Int                                                                                             | Same as the request parameter.                                                                                               |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | extendparam           | Dictionary data structure. For details, see :ref:`Table 16 <rds_06_0616__table3492062317170>`.  | Indicates the returned **extendparam** key-value pair.                                                                       |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | backupStrategy        | Dictionary data structure. For details, see :ref:`Table 18 <rds_06_0616__table18267654155052>`. | Indicates the backup policy.                                                                                                 |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | slaveId               | String                                                                                          | It is returned only when you create primary/standby DB instances.                                                            |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | ha                    | Dictionary data structure. For details, see :ref:`Table 19 <rds_06_0616__table16318932171721>`. | Indicates the primary/standby DB instance information. It is returned only when you create primary/standby DB instances.     |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | replica_of            | String                                                                                          | Same as the request parameter. It is returned only when you create a read replica.                                           |
      +-----------------------+-------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_06_0616__table41614513165139:

   .. table:: **Table 13** nics field data structure description

      ======== ====== =======================================
      Name     Type   Description
      ======== ====== =======================================
      subnetId String Indicates the network ID of the subnet.
      ======== ====== =======================================

   .. _rds_06_0616__table255609017350:

   .. table:: **Table 14** securityGroup field data structure description

      ==== ====== ================================
      Name Type   Description
      ==== ====== ================================
      id   String Indicates the security group ID.
      ==== ====== ================================

   .. _rds_06_0616__table223791861780:

   .. table:: **Table 15** flavor field data structure description

      ==== ====== ===============================
      Name Type   Description
      ==== ====== ===============================
      id   String Indicates the specification ID.
      ==== ====== ===============================

   .. _rds_06_0616__table3492062317170:

   .. table:: **Table 16** extendparam field data structure description

      +------+-------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name | Type                                                                                      | Description                                            |
      +======+===========================================================================================+========================================================+
      | jobs | List data structure. For details, see :ref:`Table 17 <rds_06_0616__table66691786171712>`. | Indicates the returned **jobs** parameter information. |
      +------+-------------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _rds_06_0616__table66691786171712:

   .. table:: **Table 17** jobs field data structure description

      ==== ====== ======================
      Name Type   Description
      ==== ====== ======================
      id   String Indicates the task ID.
      ==== ====== ======================

   .. _rds_06_0616__table18267654155052:

   .. table:: **Table 18** backupStrategy field data structure description

      +-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Name      | Type   | Description                                                                                                                       |
      +===========+========+===================================================================================================================================+
      | startTime | String | Indicates the backup start time that has been set. The backup task will be triggered within one hour after the backup start time. |
      +-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+
      | keepDays  | Int    | Indicates the number of days to retain the generated backup files.                                                                |
      +-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_06_0616__table16318932171721:

   .. table:: **Table 19** ha field data structure description

      +-----------------+--------+--------------------------------------------------------------------------------------------+
      | Name            | Type   | Description                                                                                |
      +=================+========+============================================================================================+
      | replicationMode | String | Indicates the replication mode for the standby DB instance. Same as the request parameter. |
      +-----------------+--------+--------------------------------------------------------------------------------------------+

.. note::

   The values of **region** and **availabilityZone** are used as examples.

-  Response example

   Creating a single DB instance:

   .. code-block:: text

      {
          "instance": {
              "id": "252f11f1-2912-4c06-be55-1999bde659c5",
              "status": "BUILD",
              "name": "trove-instance-rep3",
              "created": "",
              "hostname": "",
              "type": "master",
              "region": "aaa",
              "updated": "",
              "availabilityZone": "bbb",
              "vpc": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
              "nics": {
                "subnetId": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f"
              },
              "securityGroup": {
                  "id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5"
              },
              "flavor": {
                  "id": "bf07a6d4-844a-4023-a776-fc5c5fb71fb4"
              },
              "dbPort": 3306,
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "extendparam": {
                  "jobs": [
                      {
                          "id": "ff8080815564ddf5015564f64a560024"
                      }
                  ]
              },
              "backupStrategy": {
                  "startTime": "01:00:00",
                  "keepDays": 3
              }
          }
      }

   Creating primary/standby DB instances:

   .. code-block:: text

      {
          "instance": {
              "id": "252f11f1-2912-4c06-be55-1999bde659c5",
              "status": "BUILD",
              "name": "trove-instance-rep3",
              "created": "",
              "hostname": "",
              "type": "master",
              "region": "aaa",
              "updated": "",
              "availabilityZone": "bbb",
              "vpc": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
              "nics": {
                "subnetId": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f"
              },
              "securityGroup": {
                  "id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5"
              },
              "flavor": {
                  "id": "bf07a6d4-844a-4023-a776-fc5c5fb71fb4"
              },
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "dbPort": 3306,
              "extendparam": {
                  "jobs": [
                      {
                          "id": "ff8080815564ddf5015564f64a560024"
                      },
                      {
                          "id": "ae3081675564ddf5357564f64a560025"
                      }
                  ]
              },
              "backupStrategy": {
                  "startTime": "01:00:00",
                  "keepDays": 3
              },
              "slaveId": "9405d8b8-a87d-4531-bd3a-e504c8434281",
              "ha": {
                  "replicationMode": "async"
              }
          }
      }

   Creating a read replica:

   .. code-block:: text

      {
          "instance": {
              "id": "252f11f1-2912-4c06-be55-1999bde659c5",
              "status": "BUILD",
              "name": "trove-instance-rep3",
              "created": "",
              "hostname": "",
              "type": "readreplica",
              "region": "aaa",
              "updated": "",
              "availabilityZone": "bbb",
              "vpc": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
              "nics": {
                "subnetId": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f"
              },
              "securityGroup": {
                  "id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5"
              },
              "flavor": {
                  "id": "bf07a6d4-844a-4023-a776-fc5c5fb71fb4"
              },
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "dbPort": 3306,

              "extendparam": {
                  "jobs": [
                      {
                          "id": "ff8080815564ddf5015564f64a560024"
                      }
                  ]
              },
              "replica_of": "252f11f1-2912-4c06-be55-1999bde659c5"
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
