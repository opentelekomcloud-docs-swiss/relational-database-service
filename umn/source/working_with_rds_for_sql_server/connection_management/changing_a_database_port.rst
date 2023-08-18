:original_name: rds_sqlserver_change_database_port.html

.. _rds_sqlserver_change_database_port:

Changing a Database Port
========================

**Scenarios**
-------------

This section describes how to change the database port of a primary DB instance or a read replica. For primary/standby DB instances, changing the database port of the primary DB instance will cause the database port of the standby DB instance to also be changed.

If specific security group rules have been configured for a DB instance, you need to change the inbound rules of the security group to which the DB instance belongs after changing the database port.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance or click |image3| first and then click the target read replica.
#. In the **Connection Information** area on the **Basic Information** page, click |image4| in the **Database Port** field.

   .. note::

      The Microsoft SQL Server database port is 1433 (default) or ranges from 2100 to 9500 (excluding 5355 and 5985). For Microsoft SQL Server 2017 Enterprise Edition, the database port is 1433 or ranges from 2100 to 9500, excluding 5050, 5353, and 5986.

   -  To submit the change, click |image5|.

      -  In the dialog box, click **Yes**.

         a. If you change the database port of the primary DB instance, that of the standby DB instance will also be changed and both DB instances will be rebooted.
         b. If you change the database port of a read replica, the change will not affect other DB instances. Only the read replica will reboot.

            .. note::

               For Microsoft SQL Server, only 2017 Enterprise Edition supports read replicas.

         c. This process takes 1-5 minutes.

      -  In the dialog box, click **No** to cancel the modification.

   -  To cancel the change, click |image6|.

#. View the result of the change on the **Basic Information** page.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001166476976.png
.. |image4| image:: /_static/images/en-us_image_0000001212355375.png
.. |image5| image:: /_static/images/en-us_image_0000001166795536.png
.. |image6| image:: /_static/images/en-us_image_0000001212196855.png
