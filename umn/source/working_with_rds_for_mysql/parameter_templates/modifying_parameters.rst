:original_name: rds_configuration.html

.. _rds_configuration:

Modifying Parameters
====================

You can modify parameters in a custom parameter template to optimize RDS database performance.

You can change parameter values in custom parameter templates only and cannot change parameter values in default parameter templates. When you change parameter values in a custom parameter template, the changes take effect for all DB instances to which the parameter template applies.

In conclusion, after you modify a parameter, the time when the modification takes effect is determined by the type of the parameter.

The RDS console displays the statuses of DB instances to which the parameter template applies. For example, if the DB instance has not used the latest modifications made to its parameter template, its status is **Parameter change. Pending reboot**. You need to manually reboot the DB instance for the latest modifications to take effect for that DB instance.

.. note::

   RDS has default parameter templates whose parameter values cannot be changed. You can view these parameter values by clicking the default parameter templates. If a custom parameter template is set incorrectly, the database startup may fail. You can re-configure the custom parameter template according to the configurations of the default parameter template.

Modifying Parameter Template Parameters
---------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. Choose **Parameter Templates** in the navigation pane on the left. On the **Custom Templates** page, click the target parameter template.

#. On the **Parameters** page, modify parameters as required.

   For parameter description details, see :ref:`Suggestions on Tuning MySQL Parameters <rds_08_00001>`.

   Available operations are as follows:

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

#. After the parameter values are modified, you can click **Change History** to view the modification details.

#. The modifications take effect only after you apply the parameter template to DB instances. For details, see :ref:`Applying a Parameter Template <rds_05_0018>`.

#. View the status of the DB instance to which the parameter template is applied.

   If the DB instance status is **Parameter change. Pending reboot**, you need to reboot the DB instance for the modifications to take effect.

   -  The DB instance reboot caused by instance class changes will not make parameter modifications take effect.
   -  If you have modified parameters of a primary DB instance, you need to reboot the primary DB instance for the modifications to take effect. (For primary/standby DB instances, the parameter modifications also apply to the standby DB instance.)
   -  If you have modified parameters of a read replica, you need to reboot the read replica for the modifications to take effect.

Modifying Instance Parameters
-----------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and a project.

#. Click |image4| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, modify parameters as required.

   .. important::

      Check the value in the **Effective upon Reboot** column.

      -  If the value is **Yes** and the DB instance status on the **Instances** page is **Parameter change. Pending reboot**, you must reboot the DB instance for the modifications to take effect.

         -  If you have modified parameters of a primary DB instance, you need to reboot the primary DB instance for the modifications to take effect. (For primary/standby DB instances, the parameter modifications also apply to the standby DB instance.)
         -  If you have modified parameters of a read replica, you need to reboot the read replica for the modifications to take effect.

      -  If the value is **No**, the modifications take effect immediately.

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

   After parameters are modified, you can click **Change History** to view parameter modification details.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001166476958.png
.. |image4| image:: /_static/images/en-us_image_0000001212196809.png
