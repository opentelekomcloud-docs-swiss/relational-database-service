:original_name: rds_05_0030.html

.. _rds_05_0030:

Changing the Replication Mode
=============================

Scenarios
---------

You can change the replication mode for primary/standby DB instances to **Asynchronous** or **Semi-synchronous**.

-  **Asynchronous**:

   -  When applications update data, the primary DB instance responds to the applications immediately after data is updated. This mode provides better performance than the semi-synchronous mode.

-  **Semi-synchronous** (default value):

   -  When applications update data, the primary DB instance responds to the applications only after the standby DB instance receives logs, which affects database performance.
   -  If the standby DB instance is abnormal, the primary DB instance waits for the response of the standby DB instance for several seconds and does not respond to write operations during this period.

      -  If the standby DB instance is recovered during the waiting period, the primary DB instance starts to respond to write operations normally.
      -  If the standby DB instance is not recovered during the waiting period, the replication mode is automatically switched to asynchronous. After the switchover is complete, the primary DB instance starts to respond to write operations.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the primary instance name.
#. In the **DB Information** area on the displayed **Basic Information** page, click **Change** next to the **Replication Mode** field. In the displayed dialog box, select a model and click **OK**.
#. On the **Basic Information** page, check for the new replication mode.

.. |image1| image:: /_static/images/en-us_image_0000001671328445.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
