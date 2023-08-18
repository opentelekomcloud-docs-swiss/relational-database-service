:original_name: rds_pg_stop.html

.. _rds_pg_stop:

Stopping an Instance
====================

Scenarios
---------

If you use DB instances only for routine development, you can temporarily stop pay-per-use instances to save money. You can stop an instance for up to seven days.

Billing
-------

After a DB instance is stopped, the ECS where the DB instance is located is no longer billed. Other resources, including EIPs, storage resources, and backups, are still billed.

Constraints
-----------

-  If you stop a primary instance, read replicas (if there are any) will also be stopped. They are stopped for up to seven days. You cannot stop a read replica without stopping the primary instance.
-  A stopped instance cannot be deleted through the console.
-  Stopping a DB instance will also stop its automated backups. After the DB instance is started, a full backup is automatically triggered.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate the primary instance that you want to stop and choose **More** > **Stop** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.
#. Refresh the instance list and view the status of the instance. If the status is **Stopped**, the instance is stopped successfully.

.. |image1| image:: /_static/images/en-us_image_0000001623471654.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
