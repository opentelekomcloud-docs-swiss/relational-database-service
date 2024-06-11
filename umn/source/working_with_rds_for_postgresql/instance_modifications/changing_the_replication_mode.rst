:original_name: rds_pg_05_0061.html

.. _rds_pg_05_0061:

Changing the Replication Mode
=============================

Scenarios
---------

RDS allows you to change the replication mode between primary and standby DB instances. Data can be asynchronously or synchronously replicated from the primary instance to the standby instance.

-  **Asynchronous** (default): When an application writes data to the primary instance, the primary instance returns a response to the application immediately without waiting for the standby instance to receive logs.

   -  Advantages: Asynchronous replication involves low overhead and ensures that write operations are not blocked during a failover of your primary/standby instances.
   -  Disadvantages: In rare cases, replication is delayed between the primary and standby instances, and data may be lost after the failover.

-  **Synchronous**: When an application writes data to the primary instance, the primary instance returns a response to the application only after the standby instance receives logs (which are flushed to the disk).

   -  Advantages: Data remains strongly consistent between the primary and standby instances, and no data loss occurs after a failover.
   -  Disadvantages: Synchronous replication involves high overhead and causes write operations to be blocked when the primary or standby instance is faulty.

.. note::

   -  Asynchronous replication is recommended for applications requiring a guarantee of high availability.
   -  Synchronous replication is recommended for applications that require strong data consistency and can tolerate a short-time blocking of write operations.
   -  Write operations refer to non-SELECT operations, such as DDL and DML.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the primary instance name.
#. In the **DB Information** area on the displayed **Basic Information** page, click **Change** next to the **Replication Mode** field. In the displayed dialog box, select a model and click **OK**.
#. On the **Basic Information** page, check for the new replication mode.

.. |image1| image:: /_static/images/en-us_image_0000001942554385.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
