:original_name: rds_08_0015.html

.. _rds_08_0015:

Resetting a Parameter Template
==============================

**Scenarios**
-------------

You can reset all parameters in a custom parameter template to their default settings.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Parameter Templates** page, click **Custom Templates**. Locate the target parameter template and choose **More** > **Reset** in the **Operation** column.

#. Click **Yes**.

#. The modifications take effect only after you apply the parameter template to DB instances. For details, see :ref:`Applying a Parameter Template <rds_05_0018>`.

#. View the status of the DB instance to which the parameter template is applied.

   If the DB instance status is **Parameter change. Pending reboot**, you need to reboot the DB instance for the modifications to take effect.

   -  The DB instance reboot caused by instance class changes will not make parameter modifications take effect.
   -  If you have modified parameters of a primary DB instance, you need to reboot the primary DB instance for the modifications to take effect. (For primary/standby DB instances, the parameter modifications also apply to the standby DB instance.)
   -  If you have modified parameters of a read replica, you need to reboot the read replica for the modifications to take effect.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
