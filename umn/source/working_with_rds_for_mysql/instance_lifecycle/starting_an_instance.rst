:original_name: rds_05_0058.html

.. _rds_05_0058:

Starting an Instance
====================

Scenarios
---------

You can stop your instance temporarily to save money. After stopping your instance, you can restart it to begin using it again.

Constraints
-----------

-  If you start a primary instance, read replicas (if there are any) will also be started.
-  Only DB instances in **Stopped** state can be started.
-  When a stopped DB instance is started, a full backup is automatically triggered.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate the primary instance that you want to start and choose **More** > **Start** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.
#. Refresh the instance list and view the status of the instance. If the status is **Available**, the instance is started successfully.

.. |image1| image:: /_static/images/en-us_image_0000001623791558.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
