:original_name: rds_05_0038.html

.. _rds_05_0038:

Changing the Maintenance Window
===============================

Scenarios
---------

The maintenance window is 19:00-23:00 by default and you can change it as required. To prevent service interruption, you are advised to set the maintenance window to off-peak hours.

Precautions
-----------

-  During the maintenance window, the DB instance will be intermittently disconnected for one or two times. Ensure that your applications support automatic reconnection.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance. In the **DB Information** area on the **Basic Information** page, click **Change** in the **Maintenance Window** field.
#. In the displayed dialog box, select a maintenance window and click OK.

   .. note::

      Changing the maintenance window does not affect the execution time of the scheduled tasks in the original maintenance period.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
