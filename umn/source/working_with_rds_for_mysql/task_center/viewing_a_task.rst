:original_name: rds_task_0001.html

.. _rds_task_0001:

Viewing a Task
==============

You can view the progress and results of scheduled and instant tasks on the **Task Center** page.

.. note::

   RDS allows you to view and manage the following tasks:

   -  Creating DB instances
   -  Rebooting DB instances
   -  Binding EIPs to DB instances
   -  Unbinding EIPs from DB instances
   -  Switching primary/standby DB instances
   -  Changing single DB instances to primary/standby
   -  Scaling up storage space
   -  Creating read replicas
   -  Migrating a standby MySQL DB instance
   -  Restoring data to new DB instances
   -  Restoring MySQL data to existing DB instances

Viewing an Instant Task
-----------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. Choose **Task Center** in the navigation pane on the left. On the displayed **Instant Tasks** page, locate the target task and view the task details.

   -  To identify the target task, you can use the task name, order ID, or DB instance name/ID, or simply enter the target task name in the search box in the upper right corner.

   -  You can view the progress and status of tasks in a specific period. The default period is seven days.

      The task list shows tasks that have been executed in the past 30 days.

   -  You can view the instant tasks in the following statuses:

      -  Running
      -  Completed
      -  Failed

Viewing a Scheduled Task
------------------------

#. Log in to the management console.
#. Click |image3| in the upper left corner and select a region and a project.
#. Click |image4| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. Choose **Task Center** in the navigation pane on the left. On the **Scheduled Tasks** page, view the task progress and results.

   -  To identify the target task, you can use the DB instance name/ID or enter the target DB instance ID in the search box in the upper right corner.
   -  You can view the scheduled tasks in the following statuses:

      -  Running
      -  Completed
      -  Failed
      -  Canceled
      -  To be executed
      -  To be authorized

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001166476958.png
.. |image4| image:: /_static/images/en-us_image_0000001212196809.png
