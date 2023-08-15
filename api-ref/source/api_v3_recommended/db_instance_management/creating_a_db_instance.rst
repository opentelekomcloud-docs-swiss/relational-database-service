:original_name: rds_01_0002.html

.. _rds_01_0002:

Creating a DB Instance
======================

Function
--------

This API is used to create a single RDS DB instance, primary/standby DB instance, or read replica.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

.. table:: **Table 2** Parameter description (creating single, primary/standby, and cluster instances)

   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name              | Mandatory       | Type            | Description                                                                                                                                                                                                                                       |
   +===================+=================+=================+===================================================================================================================================================================================================================================================+
   | name              | Yes             | String          | Specifies the DB instance name.                                                                                                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | DB instances of the same type can have same names under the same tenant. Its value can be any of the following:                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | The DB instance name must be 4 to 64 characters long, start with a letter, and contain only letters (case-sensitive), digits, hyphens (-), and underscores (_).                                                                                   |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | datastore         | Yes             | Object          | Specifies the database information.                                                                                                                                                                                                               |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | For details, see :ref:`Table 4 <rds_01_0002__table64243102>`.                                                                                                                                                                                     |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ha                | No              | Object          | Specifies the HA configuration, which is used when you create primary/standby or cluster instances.                                                                                                                                               |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | For details, see :ref:`Table 5 <rds_01_0002__table13260175614296>`.                                                                                                                                                                               |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | configuration_id  | No              | String          | Specifies the parameter template ID.                                                                                                                                                                                                              |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | For details, see **id** in :ref:`Table 3 <rds_09_0301__table1324110018258>` in section :ref:`Obtaining a Parameter Template List <rds_09_0301>`.                                                                                                  |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port              | No              | String          | Specifies the database port information.                                                                                                                                                                                                          |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | -  The MySQL database port ranges from 1024 to 65535 (excluding 12017 and 33071, which are occupied by the RDS system and cannot be used).                                                                                                        |
   |                   |                 |                 | -  The PostgreSQL database port ranges from 2100 to 9500.                                                                                                                                                                                         |
   |                   |                 |                 | -  The Microsoft SQL Server database port is 1433 or ranges from 2100 to 9500 (excluding 5355 and 5985). For Microsoft SQL Server 2017 Enterprise Edition, the database port is 1433 or ranges from 2100 to 9500, excluding 5050, 5353, and 5986. |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | If this parameter is not set, the default value is as follows:                                                                                                                                                                                    |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | -  For MySQL, the default value is **3306**.                                                                                                                                                                                                      |
   |                   |                 |                 | -  For PostgreSQL, the default value is **5432**.                                                                                                                                                                                                 |
   |                   |                 |                 | -  For Microsoft SQL Server, the default value is **1433**.                                                                                                                                                                                       |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | password          | No              | String          | Specifies the database password.                                                                                                                                                                                                                  |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | Valid value:                                                                                                                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | A database password must be 8 to 32 characters long and contain at least three types of the following characters: uppercase letters, lowercase letters, digits, and special characters.                                                           |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | Different DB engines support different special characters.                                                                                                                                                                                        |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | -  MySQL: ``~!@#$%^*-_=+?,``                                                                                                                                                                                                                      |
   |                   |                 |                 | -  Microsoft SQL Server: ``~!@#$%^*-_+?,``                                                                                                                                                                                                        |
   |                   |                 |                 | -  PostgreSQL: ``~!@#%^*-_=+?,``                                                                                                                                                                                                                  |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | You are advised to enter a strong password to improve security, preventing security risks such as brute force cracking.                                                                                                                           |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | backup_strategy   | No              | Object          | Specifies the advanced backup policy.                                                                                                                                                                                                             |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | For details, see :ref:`Table 6 <rds_01_0002__table0863181193416>`.                                                                                                                                                                                |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor_ref        | Yes             | String          | Specifies the specification code. The value cannot be empty.                                                                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | For details, see **spec_code** in :ref:`Table 3 <rds_06_0002__table66531170>` in section :ref:`Querying Database Specifications <rds_06_0002>`.                                                                                                   |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume            | Yes             | Object          | Specifies the volume information.                                                                                                                                                                                                                 |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | For details, see :ref:`Table 7 <rds_01_0002__table10656503>`.                                                                                                                                                                                     |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | region            | Yes             | String          | Specifies the region ID.                                                                                                                                                                                                                          |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | The value cannot be empty. Obtain the parameter value from the enterprise administrator.                                                                                                                                                          |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone | Yes             | String          | Specifies the AZ ID. If the DB instance is not a single instance, you need to specify an AZ for each node of the instance and separate the AZs with commas (,). For details, see the example.                                                     |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | The value cannot be empty. Obtain the parameter value from the enterprise administrator.                                                                                                                                                          |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id            | Yes             | String          | Specifies the VPC ID. To obtain this parameter value, use either of the following methods:                                                                                                                                                        |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | -  Method 1: Log in to VPC console and view the VPC ID in the VPC details.                                                                                                                                                                        |
   |                   |                 |                 | -  Method 2: See the "Querying VPCs" section in the *Virtual Private Cloud API Reference*.                                                                                                                                                        |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id         | Yes             | String          | Specifies the network ID. To obtain this parameter value, use either of the following methods:                                                                                                                                                    |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | -  Method 1: Log in to VPC console and click the target subnet on the **Subnets** page. You can view the network ID on the displayed page.                                                                                                        |
   |                   |                 |                 | -  Method 2: See the "Querying Subnets" section in the *Virtual Private Cloud API Reference*.                                                                                                                                                     |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_vip          | No              | String          | Specifies the floating IP address of a DB instance. To obtain this parameter value, use either of the following methods:                                                                                                                          |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | -  Method 1: Log in to VPC console and click the target subnet on the **Subnets** page. You can view the subnet CIDR block on the displayed page.                                                                                                 |
   |                   |                 |                 | -  Method 2: See the "Querying Subnets" section in the *Virtual Private Cloud API Reference*.                                                                                                                                                     |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id | Yes             | String          | Specifies the security group which the RDS DB instance belongs to. To obtain this parameter value, use either of the following methods:                                                                                                           |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | -  Method 1: Log in to VPC console. Choose **Access Control** > **Security Groups** in the navigation pane on the left. On the displayed page, click the target security group. You can view the security group ID on the displayed page.         |
   |                   |                 |                 | -  Method 2: See the "Querying Security Groups" section in the *Virtual Private Cloud API Reference*.                                                                                                                                             |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | charge_info       | No              | Object          | Specifies the billing information.                                                                                                                                                                                                                |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | For details, see :ref:`Table 8 <rds_01_0002__table992615211258>`.                                                                                                                                                                                 |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_zone         | No              | String          | Specifies the UTC time zone.                                                                                                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | -  If this parameter is not specified, the time zone of each engine is as follows:                                                                                                                                                                |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 |    -  MySQL: uses UTC by default.                                                                                                                                                                                                                 |
   |                   |                 |                 |    -  PostgreSQL: uses UTC by default.                                                                                                                                                                                                            |
   |                   |                 |                 |    -  Microsoft SQL Server: uses UTC by default.                                                                                                                                                                                                  |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | -  If this parameter is specified for MySQL or PostgreSQL, the value range is from UTC-12:00 to UTC+12:00 on the hour. For example, the parameter can be UTC+08:00 rather than UTC+08:30.                                                         |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | collation         | No              | String          | This parameter applies only to Microsoft SQL Server DB instances.                                                                                                                                                                                 |
   |                   |                 |                 |                                                                                                                                                                                                                                                   |
   |                   |                 |                 | Value range: character sets queried in :ref:`Querying the Available SQL Server Character Set <rds_05_0010>`.                                                                                                                                      |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Parameter description (For Microsoft SQL Server, only 2017 EE supports read replicas)

   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name               | Mandatory       | Type            | Description                                                                                                                                              |
   +====================+=================+=================+==========================================================================================================================================================+
   | name               | Yes             | String          | Specifies the DB instance name.                                                                                                                          |
   |                    |                 |                 |                                                                                                                                                          |
   |                    |                 |                 | The DB instance name of the same type must be unique for the same tenant.                                                                                |
   |                    |                 |                 |                                                                                                                                                          |
   |                    |                 |                 | Valid value:                                                                                                                                             |
   |                    |                 |                 |                                                                                                                                                          |
   |                    |                 |                 | The parameter must be 4 to 64 characters long, start with a letter, and contain only letters (case-sensitive), digits, hyphens (-), and underscores (_). |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | replica_of_id      | Yes             | String          | Specifies the primary DB instance ID for creating a read replica.                                                                                        |
   |                    |                 |                 |                                                                                                                                                          |
   |                    |                 |                 | For details, see **id** in :ref:`Table 3 <rds_01_0004__table2058713718267>` in section :ref:`Querying Details About DB Instances <rds_01_0004>`.         |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | disk_encryption_id | No              | String          | Specifies the key ID for disk encryption. The default value is empty.                                                                                    |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor_ref         | Yes             | String          | Specifies the specification code. The value cannot be empty.                                                                                             |
   |                    |                 |                 |                                                                                                                                                          |
   |                    |                 |                 | For details, see **spec_code** in :ref:`Table 3 <rds_06_0002__table66531170>` in section :ref:`Querying Database Specifications <rds_06_0002>`.          |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume             | Yes             | Object          | Specifies the volume information.                                                                                                                        |
   |                    |                 |                 |                                                                                                                                                          |
   |                    |                 |                 | For details, see :ref:`Table 7 <rds_01_0002__table10656503>`.                                                                                            |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | region             | No              | String          | Specifies the region ID. Currently, read replicas can be created only in the same region as that of the primary DB instance.                             |
   |                    |                 |                 |                                                                                                                                                          |
   |                    |                 |                 | The value cannot be empty. Obtain the parameter value from the enterprise administrator.                                                                 |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone  | Yes             | String          | Specifies the AZ ID.                                                                                                                                     |
   |                    |                 |                 |                                                                                                                                                          |
   |                    |                 |                 | The value cannot be empty. Obtain the parameter value from the enterprise administrator.                                                                 |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | charge_info        | No              | Object          | Specifies the billing information.                                                                                                                       |
   |                    |                 |                 |                                                                                                                                                          |
   |                    |                 |                 | For details, see :ref:`Table 8 <rds_01_0002__table992615211258>`.                                                                                        |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _rds_01_0002__table64243102:

.. table:: **Table 4** datastore field data structure description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================+
   | type            | Yes             | String          | Specifies the DB engine. Value:                                                                                                 |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 | -  MySQL                                                                                                                        |
   |                 |                 |                 | -  PostgreSQL                                                                                                                   |
   |                 |                 |                 | -  SQLServer                                                                                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | version         | Yes             | String          | Specifies the database version.                                                                                                 |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 | -  MySQL databases support 5.6, 5.7, and 8.0. Example value: 5.7                                                                |
   |                 |                 |                 | -  PostgreSQL databases support PostgreSQL 9.5, 9.6, 10, 11, and 12. Example value: 9.6                                         |
   |                 |                 |                 | -  Microsoft SQL Server databases only support 2014 SE, 2016 SE, 2016 EE, 2017 SE, and 2017 EE. Example value: 2014_SE          |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 | For details about supported database versions, see section :ref:`Querying Version Information About a DB Engine <rds_06_0001>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+

.. _rds_01_0002__table13260175614296:

.. table:: **Table 5** ha field data structure description

   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------+
   | Name             | Mandatory       | Type            | Description                                                                                     |
   +==================+=================+=================+=================================================================================================+
   | mode             | Yes             | String          | Specifies the primary/standby or cluster instance type. The value is **Ha** (case-insensitive). |
   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------+
   | replication_mode | Yes             | String          | Specifies the replication mode for the standby DB instance.                                     |
   |                  |                 |                 |                                                                                                 |
   |                  |                 |                 | Value:                                                                                          |
   |                  |                 |                 |                                                                                                 |
   |                  |                 |                 | -  For MySQL, the value is **async** or **semisync**.                                           |
   |                  |                 |                 | -  For PostgreSQL, the value is **async** or **sync**.                                          |
   |                  |                 |                 | -  For Microsoft SQL Server, the value is **sync**.                                             |
   |                  |                 |                 |                                                                                                 |
   |                  |                 |                 | .. note::                                                                                       |
   |                  |                 |                 |                                                                                                 |
   |                  |                 |                 |    -  **async** indicates the asynchronous replication mode.                                    |
   |                  |                 |                 |    -  **semisync** indicates the semi-synchronous replication mode.                             |
   |                  |                 |                 |    -  **sync** indicates the synchronous replication mode.                                      |
   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------+

.. _rds_01_0002__table0863181193416:

.. table:: **Table 6** backup_strategy field data structure description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================+
   | start_time      | Yes             | String          | Specifies the backup time window. Automated backups will be triggered during the backup time window.                            |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 | The value cannot be empty. It must be a valid value in the "hh:mm-HH:MM" format. The current time is in the UTC format.         |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 | -  The **HH** value must be 1 greater than the **hh** value.                                                                    |
   |                 |                 |                 | -  The values of **mm** and **MM** must be the same and must be set to any of the following: **00**, **15**, **30**, or **45**. |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 | Example value:                                                                                                                  |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 | -  08:15-09:15                                                                                                                  |
   |                 |                 |                 | -  23:00-00:00                                                                                                                  |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | keep_days       | No              | Integer         | Specifies the retention days for specific backup files.                                                                         |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 | The value range is from 0 to 732. If this parameter is not specified or set to **0**, the automated backup policy is disabled.  |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 | .. important::                                                                                                                  |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 |    NOTICE:                                                                                                                      |
   |                 |                 |                 |    Primary/standby DB instances of Microsoft SQL Server do not support disabling the automated backup policy.                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+

.. _rds_01_0002__table10656503:

.. table:: **Table 7** volume field data structure description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================+
   | type            | Yes             | String          | Specifies the volume type.                                                                                                  |
   |                 |                 |                 |                                                                                                                             |
   |                 |                 |                 | Its value can be any of the following and is case-sensitive:                                                                |
   |                 |                 |                 |                                                                                                                             |
   |                 |                 |                 | -  **ULTRAHIGH**: indicates the SSD type.                                                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | size            | Yes             | Integer         | Specifies the volume size.                                                                                                  |
   |                 |                 |                 |                                                                                                                             |
   |                 |                 |                 | Its value must be a multiple of 10 and the value range is from 40 GB to 4,000 GB.                                           |
   |                 |                 |                 |                                                                                                                             |
   |                 |                 |                 | .. note::                                                                                                                   |
   |                 |                 |                 |                                                                                                                             |
   |                 |                 |                 |    For read replicas, this parameter is invalid. The volume size is the same as that of the primary DB instance by default. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+

.. _rds_01_0002__table992615211258:

.. table:: **Table 8** charge_info field data structure description

   +-----------------+-----------------+-----------------+-----------------------------+
   | Name            | Mandatory       | Type            | Description                 |
   +=================+=================+=================+=============================+
   | charge_mode     | Yes             | String          | Specifies the billing mode. |
   |                 |                 |                 |                             |
   |                 |                 |                 | Value: **postPaid**         |
   +-----------------+-----------------+-----------------+-----------------------------+

.. note::

   The values of **region** and **availability_zone** are used as examples.

-  Request example

   .. code-block:: text

      POST https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances

   Creating a single DB instance:

   .. code-block:: text

      {
          "name": "rds-instance-rep2",
          "datastore": {
              "type": "MySQL",
              "version": "5.6"
          },
          "flavor_ref": "rds.mysql.s3.large.2",
          "volume": {
              "type": "ULTRAHIGH",
              "size": 100
          },
          "region": "aaa",
          "availability_zone": "bbb",
          "vpc_id": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
          "subnet_id": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f",
          "data_vip": "192.168.0.147",
          "security_group_id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5",
          "port": 8635,
          "backup_strategy": {
              "start_time": "08:15-09:15",
              "keep_days": 12
          },
          "charge_info": {
              "charge_mode": "postPaid"
          },
          "password": "Test@12345678",
          "configuration_id": "452408-ef4b-44c5-94be-305145fg"
      ,
      }

   Creating primary/standby DB instances:

   .. code-block:: text

      {
          "name": "rds-instance-rep2",
          "datastore": {
              "type": "MySQL",
              "version": "5.6"
          },
          "ha": {
              "mode": "ha",
              "replication_mode": "semisync"
          },
          "flavor_ref": "rds.mysql.s3.large.2.ha",
          "volume": {
              "type": "ULTRAHIGH",
              "size": 100
          },
          "region": "aaa",
          "availability_zone": "bbb,ccc",
          "vpc_id": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
          "subnet_id": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f",
          "data_vip": "192.168.0.147",
          "security_group_id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5",
          "port": 8635,
          "backup_strategy": {
              "start_time": "08:15-09:15",
              "keep_days": 12
          },
          "charge_info": {
              "charge_mode": "postPaid"
          },
          "password": "Test@12345678",
          "configuration_id": "452408-ef4b-44c5-94be-305145fg"
      }

   Creating a Microsoft SQL Server cluster instance:

   .. code-block:: text

      {
          "name": "rds-2017EE-backup",
          "availability_zone": "bbb,ccc",
          "ha": {
              "mode": "ha",
              "replication_mode": "sync"
          },
              "region": "aaa",
          "flavor_ref": "rds.mssql.s3.large.ha",
          "volume": {
              "type": "ULTRAHIGH",
              "size": 100
          },
          "disk_encryption_id": "",
          "vpc_id": "1fed5f32-3a8d-4385-84f4-aab78892f08b",
          "subnet_id": "1ceadde4-04c7-4b68-8b15-8683b03755df",
          "security_group_id": "bcbdf361-7cc2-4b8e-ace3-45f09187c326",
          "backup_strategy": {
              "keep_days": 7,
              "start_time": "01:00-02:00"
          },
          "datastore": {
              "type": "sqlserver",
              "version": "2017_EE"
          },
          "password": "Test@12345678",
          "enterprise_project_id": "",
          "time_zone": "UTC+08:00"
      }

   Creating a read replica:

   .. code-block:: text

      {
          "name": "rds-instance-rep2",
          "replica_of_id": "afdsad-fds-fdsagin01",
          "flavor_ref": "rds.mysql.s3.large.2.rr",
          "volume": {
              "type": "ULTRAHIGH"
          },
          "region": "aaa",
          "availability_zone": "bbb"
      }

Response
--------

-  Normal response

   .. table:: **Table 9** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                        |
      +=======================+=======================+====================================================================+
      | instance              | Object                | Indicates the DB instance information.                             |
      |                       |                       |                                                                    |
      |                       |                       | For details, see :ref:`Table 10 <rds_01_0002__table175305610274>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | job_id                | String                | Indicates the ID of the DB instance creation task.                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------+

   .. _rds_01_0002__table175305610274:

   .. table:: **Table 10** instance field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                                                               |
      +=======================+=======================+===========================================================================================================================================================================================================================================+
      | id                    | String                | Indicates the DB instance ID.                                                                                                                                                                                                             |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | .. note::                                                                                                                                                                                                                                 |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       |    The v3 DB instance ID is incompatible with the v1 DB instance ID.                                                                                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the DB instance name. Indicates the DB instance name. DB instances of the same type can have same names under the same tenant.                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | Valid value:                                                                                                                                                                                                                              |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | -  For MySQL databases, the parameter must be 4 to 64 characters long, start with a letter, and contain only letters (case-sensitive), digits, hyphens (-), and underscores (_).                                                          |
      |                       |                       | -  For PostgreSQL and Microsoft SQL Server databases, the parameter must be 4 to 64 characters long, start with a letter, and contain only letters (case-sensitive), digits, hyphens (-), and underscores (_).                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the DB instance status. For example, **BUILD** indicates that the DB instance is being created.                                                                                                                                 |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see **status** in :ref:`Table 3 <rds_01_0004__table2058713718267>`.                                                                                                                                                          |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore             | Object                | Indicates the database information.                                                                                                                                                                                                       |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see :ref:`Table 11 <rds_01_0002__table766045720277>`.                                                                                                                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ha                    | Object                | Indicates the HA configuration parameters.                                                                                                                                                                                                |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see :ref:`Table 12 <rds_01_0002__table15899105722713>`.                                                                                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | configuration_id      | String                | Indicates the parameter template ID. This parameter is returned only when a custom parameter template is used during DB instance creation.                                                                                                |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | port                  | String                | Indicates the database port, which is the same as the request parameter.                                                                                                                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_strategy       | Object                | Indicates the automated backup policy.                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see :ref:`Table 13 <rds_01_0002__table81249589270>`.                                                                                                                                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavor_ref            | String                | Indicates the specification code. The value cannot be empty.                                                                                                                                                                              |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see **spec_code** in :ref:`Table 3 <rds_06_0002__table66531170>` in section :ref:`Querying Database Specifications <rds_06_0002>`.                                                                                           |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | volume                | Object                | Indicates the volume information.                                                                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see :ref:`Table 14 <rds_01_0002__table5324165817272>`.                                                                                                                                                                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region                | String                | Indicates the region ID.                                                                                                                                                                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone     | String                | Indicates the AZ ID.                                                                                                                                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id                | String                | Indicates the VPC ID. To obtain this parameter value, use either of the following methods:                                                                                                                                                |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | -  Method 1: Log in to VPC console and view the VPC ID in the VPC details.                                                                                                                                                                |
      |                       |                       | -  Method 2: See the "Querying VPCs" section in the *Virtual Private Cloud API Reference*.                                                                                                                                                |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id             | String                | Indicates the network ID. To obtain this parameter value, use either of the following methods:                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | -  Method 1: Log in to VPC console and click the target subnet on the **Subnets** page. You can view the network ID on the displayed page.                                                                                                |
      |                       |                       | -  Method 2: See the "Querying Subnets" section in the *Virtual Private Cloud API Reference*.                                                                                                                                             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id     | String                | Indicates the security group which the RDS DB instance belongs to. To obtain this parameter value, use either of the following methods:                                                                                                   |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | -  Method 1: Log in to VPC console. Choose **Access Control** > **Security Groups** in the navigation pane on the left. On the displayed page, click the target security group. You can view the security group ID on the displayed page. |
      |                       |                       | -  Method 2: See the "Querying Security Groups" section in the *Virtual Private Cloud API Reference*.                                                                                                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | charge_info           | Object                | Indicates the billing information.                                                                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see :ref:`Table 15 <rds_01_0002__table207147873611>`.                                                                                                                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | collation             | String                | Indicates the collation set for Microsoft SQL Server.                                                                                                                                                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_01_0002__table766045720277:

   .. table:: **Table 11** datastore field data structure description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                     |
      +=======================+=======================+=================================================================================================================================+
      | type                  | String                | Indicates the DB engine. Value:                                                                                                 |
      |                       |                       |                                                                                                                                 |
      |                       |                       | -  MySQL                                                                                                                        |
      |                       |                       | -  PostgreSQL                                                                                                                   |
      |                       |                       | -  SQLServer                                                                                                                    |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
      | version               | String                | Indicates the database version.                                                                                                 |
      |                       |                       |                                                                                                                                 |
      |                       |                       | For details about supported database versions, see section :ref:`Querying Version Information About a DB Engine <rds_06_0001>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_01_0002__table15899105722713:

   .. table:: **Table 12** ha field data structure description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                      |
      +=======================+=======================+==================================================================================================================+
      | mode                  | String                | Indicates the primary/standby or cluster instance type. The value is **Ha**.                                     |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | replication_mode      | String                | Indicates the replication mode for the standby DB instance. This parameter is valid when the **mode** is **Ha**. |
      |                       |                       |                                                                                                                  |
      |                       |                       | Value:                                                                                                           |
      |                       |                       |                                                                                                                  |
      |                       |                       | -  For MySQL, the value is **async** or **semisync**.                                                            |
      |                       |                       | -  For PostgreSQL, the value is **async** or **sync**.                                                           |
      |                       |                       | -  For Microsoft SQL Server, the value is **sync**.                                                              |
      |                       |                       |                                                                                                                  |
      |                       |                       | .. note::                                                                                                        |
      |                       |                       |                                                                                                                  |
      |                       |                       |    -  **async** indicates the asynchronous replication mode.                                                     |
      |                       |                       |    -  **semisync** indicates the semi-synchronous replication mode.                                              |
      |                       |                       |    -  **sync** indicates the synchronous replication mode.                                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+

   .. _rds_01_0002__table81249589270:

   .. table:: **Table 13** backupStrategy field data structure description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                     |
      +=======================+=======================+=================================================================================================================================+
      | start_time            | String                | Specifies the backup time window. Automated backups will be triggered during the backup time window.                            |
      |                       |                       |                                                                                                                                 |
      |                       |                       | The value cannot be empty. It must be a valid value in the "hh:mm-HH:MM" format. The current time is in the UTC format.         |
      |                       |                       |                                                                                                                                 |
      |                       |                       | -  The **HH** value must be 1 greater than the **hh** value.                                                                    |
      |                       |                       | -  The values of **mm** and **MM** must be the same and must be set to any of the following: **00**, **15**, **30**, or **45**. |
      |                       |                       |                                                                                                                                 |
      |                       |                       | Example value:                                                                                                                  |
      |                       |                       |                                                                                                                                 |
      |                       |                       | -  08:15-09:15                                                                                                                  |
      |                       |                       | -  23:00-00:00                                                                                                                  |
      |                       |                       |                                                                                                                                 |
      |                       |                       | If **backup_strategy** in the request body is empty, **02:00-03:00** is returned for **start_time** by default.                 |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
      | keep_days             | Integer               | Indicates the retention days for specific backup files.                                                                         |
      |                       |                       |                                                                                                                                 |
      |                       |                       | The value range is from 0 to 732. If this parameter is not specified or set to **0**, the automated backup policy is disabled.  |
      |                       |                       |                                                                                                                                 |
      |                       |                       | If **backup_strategy** in the request body is empty, **7** is returned for **keep_days** by default.                            |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_01_0002__table5324165817272:

   .. table:: **Table 14** volume field data structure description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                    |
      +=======================+=======================+================================================================================+
      | type                  | String                | Indicates the volume type.                                                     |
      |                       |                       |                                                                                |
      |                       |                       | Its value can be any of the following and is case-sensitive:                   |
      |                       |                       |                                                                                |
      |                       |                       | -  **ULTRAHIGH**: indicates the SSD type.                                      |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------+
      | size                  | Integer               | Indicates the volume size.                                                     |
      |                       |                       |                                                                                |
      |                       |                       | Its value range is from 40 GB to 4,000 GB. The value must be a multiple of 10. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------+

   .. _rds_01_0002__table207147873611:

   .. table:: **Table 15** chargeInfo field data structure description

      +-----------------------+-----------------------+-----------------------------+
      | Name                  | Type                  | Description                 |
      +=======================+=======================+=============================+
      | charge_mode           | String                | Indicates the billing mode. |
      |                       |                       |                             |
      |                       |                       | Value: postPaid             |
      +-----------------------+-----------------------+-----------------------------+

.. note::

   The values of **region** and **availability_zone** are used as examples.

-  Example normal response

   Creating a single MySQL DB instance:

   .. code-block:: text

      {
          "instance": {
              "id": "dsfae23fsfdsae3435in01",
              "name": "trove-instance-rep2",
              "datastore": {
                  "type": "MySQL",
                  "version": "5.6"
              },
              "flavor_ref": "rds.mysql.s3.large.2",
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
                      "region": "aaa",
              "availability_zone": "bbb",
              "vpc_id": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
              "subnet_id": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f",
              "security_group_id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5",
              "port": "8635",
              "backup_strategy": {
                  "start_time": "08:15-09:15",
                  "keep_days": 3
              },
              "configuration_id": "452408-44c5-94be-305145fg",
              "charge_info": {
                  "charge_mode": "postPaid"
              }
          },
          "job_id": "dff1d289-4d03-4942-8b9f-463ea07c000d"
      }

   Creating primary/standby DB instances:

   .. code-block:: text

      {
        "instance":{
                 "id": "dsfae23fsfdsae3435in01",
                 "name": "trove-instance-rep2",
                 "datastore": {
                   "type": "MySQL",
                   "version": "5.6"
                  },
                 "ha": {
                   "mode": "ha",
                   "replication_mode": "semisync"
                 },
                 "flavor_ref": "rds.mysql.s3.large.2.ha",
                 "volume": {
                     "type": "ULTRAHIGH",
                     "size": 100
                   },
                 "region": "aaa",
                 "availability_zone": "bbb,ccc",
                 "vpc_id": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
                 "subnet_id": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f",
                 "security_group_id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5",
                 "port": "8635",
                 "backup_strategy": {
                   "start_time": "08:15-09:15",
                   "keep_days": 3
                  },
                 "configuration_id": "452408-44c5-94be-305145fg",
                 "charge_info": {
                         "charge_mode": "postPaid"
                                     },
               },
        "job_id": "dff1d289-4d03-4942-8b9f-463ea07c000d"
      }

   Creating a Microsoft SQL Server cluster instance:

   .. code-block:: text

      {
          "instance": {
              "id": "5e6724ebd1d242d2a5540e52a97886eain04",
              "name": "rds-2017EE-backup",
              "status": "BUILD",
              "datastore": {
                  "type": "SQLServer",
                  "version": "2017_EE"
              },
              "ha": {
                  "mode": "Ha",
                  "replication_mode": "sync"
              },
              "port": "1433",
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "region": "aaa",
              "backup_strategy": {
                  "start_time": "01:00-02:00",
                  "keep_days": 7
              },
              "disk_encryption_id": "",
              "flavor_ref": "rds.mssql.s3.large.ha",
              "availability_zone": "bbb,ccc",
              "vpc_id": "1fed5f32-3a8d-4385-84f4-aab78892f08b",
              "subnet_id": "1ceadde4-04c7-4b68-8b15-8683b03755df",
              "security_group_id": "bcbdf361-7cc2-4b8e-ace3-45f09187c326",
              "charge_info": {
                  "charge_mode": "postPaid"
              }
          },
          "job_id": "5ac7d0cf-7dd2-457b-bf32-1475c426f2e5"
      }

   Creating a read replica:

   .. code-block:: text

      {
        "instance":{
                  "id": "dsfae23fsfdsae3435in01",
                  "name": "trove-instance-rep2",
                  "flavor_ref": "rds.mysql.s3.large.2.rr",
                   "volume": {
                     "type": "ULTRAHIGH",
                     "size": 100
                   },
                 "region": "aaa",
                 "availability_zone": "bbb",
                 "vpc_id": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
                 "subnet_id": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f",
                 "security_group_id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5",
                 "port": "8635",
                 "configuration_id": "452408-44c5-94be-305145fg"
               },
       "job_id": "dff1d289-4d03-4942-8b9f-463ea07c000d"
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
