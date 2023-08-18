:original_name: en-us_topic_add_read_replica.html

.. _en-us_topic_add_read_replica:

Creating a Read Replica
=======================

**Scenarios**
-------------

Read replicas are used to enhance the read capabilities and reduce the load on primary DB instances.

After DB instances are created, you can create read replicas for them.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Create Read Replica** in the **Operation** column.

   Alternatively, click the target DB instance. In the DB instance topology, click |image3| under the primary DB instance to create read replicas.

#. On the displayed page, configure information about the DB instance and click **Next**.

   .. table:: **Table 1** Basic information

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                |
      +===================================+============================================================================================================================================================================+
      | Region                            | By default, read replicas are in the same region as the primary DB instance.                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Instance Name                  | Must start with a letter and consist of 4 to 64 characters. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Engine                         | Same as the DB engine version of the primary DB instance by default and cannot be changed.                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Engine Version                 | Same as the DB engine version of the primary DB instance by default and cannot be changed.                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | RDS allows you to deploy primary DB instances and read replicas in a single AZ or across AZs. You can determine whether the read replica AZ is the same as the primary AZ. |
      |                                   |                                                                                                                                                                            |
      |                                   | -  If they are the same, the read replica and primary DB instance are deployed in the same AZ.                                                                             |
      |                                   | -  If they are different, the read replica and primary DB instance are deployed in different AZs to ensure data reliability.                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** Instance specifications

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================+
      | Instance Class                    | Refers to the CPU and memory of a DB instance. Different instance classes have different numbers of database connections and maximum IOPS.                                |
      |                                   |                                                                                                                                                                           |
      |                                   | For details about instance classes, see section :ref:`DB Instance Classes <rds_01_0029>`.                                                                                 |
      |                                   |                                                                                                                                                                           |
      |                                   | After a DB instance is created, you can change its instance class (CPU and memory). For details, see section :ref:`Changing a DB Instance Class <en-us_topic_scale_rds>`. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Type                      | Determines the DB instance read/write speed. The higher the maximum throughput is, the higher the DB instance read/write speed can be.                                    |
      |                                   |                                                                                                                                                                           |
      |                                   | -  **Ultra-high I/O**: uses the SSD disk type that supports a maximum throughput of 350 MB/s.                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Space                     | Contains the file system overhead required for inode, reserved block, and database operation.                                                                             |
      |                                   |                                                                                                                                                                           |
      |                                   | By default, storage space of a read replica is the same as that of the primary DB instance.                                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Disk Encryption                   | -  **Disabled**: indicates the encryption function is disabled.                                                                                                           |
      |                                   |                                                                                                                                                                           |
      |                                   | -  **Enabled**: indicates the encryption function is enabled, improving data security but affecting system performance.                                                   |
      |                                   |                                                                                                                                                                           |
      |                                   |    **Key Name**: indicates the tenant key. You can create or select a key.                                                                                                |
      |                                   |                                                                                                                                                                           |
      |                                   |    .. note::                                                                                                                                                              |
      |                                   |                                                                                                                                                                           |
      |                                   |       -  Once the DB instance is created, you cannot modify the disk encryption status or change the key. The backup data stored in OBS is not encrypted.                 |
      |                                   |       -  After an RDS DB instance is created, do not disable or delete the key that is being used. Otherwise, RDS will be unavailable and data cannot be restored.        |
      |                                   |       -  For details about how to create a key, see the "Creating a CMK" section in the *Key Management Service User Guide*.                                              |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 3** Network

      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter      | Description                                                                                                                                                                                                                                                                     |
      +================+=================================================================================================================================================================================================================================================================================+
      | VPC            | Same as the primary DB instance's VPC.                                                                                                                                                                                                                                          |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subnet         | Same as the primary DB instance's subnet. A floating IP address is automatically assigned when you create a read replica. You can also enter an unused floating IP address in the subnet CIDR block. After the read replica is created, you can change the floating IP address. |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Security Group | Same as the primary DB instance's security group.                                                                                                                                                                                                                               |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm specifications.

   -  If you need to modify your settings, click **Previous**.
   -  If you do not need to modify your settings, click **Submit**.

#. After a read replica is created, you can view and manage it.

   For details about how to manage read replicas, see :ref:`Managing a Read Replica <rds_11_0015>`.

   You can view the detailed progress and result of the task on the **Task Center** page.

Follow-up Operations
--------------------

:ref:`Managing a Read Replica <rds_11_0015>`

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001671329561.png
