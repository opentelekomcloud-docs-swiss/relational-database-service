:original_name: rds_sqlserver_05_0024.html

.. _rds_sqlserver_05_0024:

Configuring and Changing a Floating IP Address
==============================================

Scenarios
---------

You can plan and change floating IP addresses after migrating on-premises databases or other cloud databases to RDS.

Constraints
-----------

After a floating IP address is changed, the domain name needs to be resolved again. This operation takes several minutes and may interrupt database connections. Therefore, you are advised to change a floating IP address during off-peak hours.

Changing a Floating IP Address
------------------------------

To change the floating IP address of a created DB instance, perform the following steps:

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the **Connection Information** area on the **Basic Information** page, click **Change** in the **Floating IP Address** field.

#. In the displayed dialog box, enter a new floating IP address. Click **OK**.

   An in-use IP address cannot be used as the new floating IP address of the DB instance.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
