:original_name: rds_06_0003.html

.. _rds_06_0003:

Viewing Monitoring Metrics
==========================

Scenarios
---------

Cloud Eye monitors running statuses of RDS DB instances. You can view the RDS monitoring metrics on the management console.

Monitored data takes some time for transmission and display. The RDS status displayed on the Cloud Eye console is the status of the last 5 to 10 minutes. If your RDS DB instance is newly created, wait for 5 to 10 minutes and then view the monitoring data.

**Prerequisites**
-----------------

-  RDS is running properly.

   Monitoring metrics of the RDS DB instances that are faulty or have been deleted are not displayed on the Cloud Eye console. You can view their monitoring metrics after they are rebooted or restored to normal.

.. note::

   If an RDS DB instance has been faulty for 24 hours, Cloud Eye considers that it does not exist and deletes it from the monitoring object list. You need to manually clear the alarm rules created for the DB instance.

-  RDS keeps running properly for about 10 minutes.

   For a newly created RDS DB instance, you need to wait for a while before viewing the monitoring metrics.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and click **View Metric** in the **Operation** column to go to the Cloud Eye console.

   Alternatively, click the target DB instance. On the displayed page, click **View Metric** in the upper right corner of the page to go to the Cloud Eye console.

#. On the Cloud Eye console, view monitoring metrics of the primary DB instance.

   Cloud Eye can monitor performance metrics from the last 1 hour, 3 hours, 12 hours, 1 day, 7 days.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
