:original_name: rds_change_database_port.html

.. _rds_change_database_port:

Changing a Database Port
========================

**Scenarios**
-------------

This section describes how to change the database port of a primary DB instance or a read replica. For primary/standby DB instances, changing the database port of the primary DB instance will cause the database port of the standby DB instance to also be changed.

If specific security group rules have been configured for a DB instance, you need to change the inbound rules of the security group to which the DB instance belongs after changing the database port.

Constraints
-----------

You cannot perform the following operations when the database port of a DB instance is being changed:

-  Bind an EIP to the DB instance.
-  Delete the DB instance.
-  Create a backup for the DB instance.
-  Restore from backup data or from a specific point in time to the original DB instance.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance or click |image3| first and then click the target read replica.
#. In the **Connection Information** area on the **Basic Information** page, click |image4| in the **Database Port** field.

   .. note::

      The MySQL database port ranges from 1024 to 65535, excluding 12017 and 33071, which are occupied by the RDS system.

   -  To submit the change, click |image5|.

      -  In the dialog box, click **Yes**.

         a. If you change the database port of the primary DB instance, that of the standby DB instance will also be changed and both DB instances will be rebooted.
         b. If you change the database port of a read replica, the change will not affect other DB instances. Only the read replica will be rebooted.
         c. This process takes 1-5 minutes.

      -  In the dialog box, click **No** to cancel the modification.

   -  To cancel the change, click |image6|.

#. View the result of the change on the **Basic Information** page.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001166476976.png
.. |image4| image:: /_static/images/en-us_image_0000001212355375.png
.. |image5| image:: /_static/images/en-us_image_0000001212475389.png
.. |image6| image:: /_static/images/en-us_image_0000001212355389.png
