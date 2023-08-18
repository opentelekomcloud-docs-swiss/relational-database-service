:original_name: rds_pg_recycle.html

.. _rds_pg_recycle:

Recycling a DB Instance
=======================

You can recycle deleted DB instances within the configured retention period to rebuild DB instances from the recycle bin.

Read replicas cannot be recycled.

The recycle bin is enabled by default and cannot be disabled.

Modifying Recycling Policy
--------------------------

.. important::

   The new recycling policy takes effect only for DB instances that are put into the recycle bin after the modification. For DB instances that already exist in the recycle bin before the modification, the original recycling policy takes effect.

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. In the navigation pane on the left, choose **Recycle Bin**.
#. On the **Recycle Bin** page, click **Modify Recycling Policy**. In the displayed dialog box, set the retention period for the deleted DB instances from 1 day to 7 days.
#. Then, click **OK**.

Rebuilding a DB Instance
------------------------

You can rebuild DB instances in the recycle bin within the retention period.

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. In the navigation pane on the left, choose **Recycle Bin**.
#. On the **Recycle Bin** page, locate the target DB instance to be rebuilt and click **Rebuild** in the **Operation** column.
#. On the **Rebuild DB Instance** page, configure required information and submit the rebuild task. For details, see :ref:`Restoring from Backup Files to DB Instances <rds_08_0007>`.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001166476958.png
