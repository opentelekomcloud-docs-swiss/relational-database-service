:original_name: rds_02_0025.html

.. _rds_02_0025:

Binding an EIP
==============

Scenarios
---------

By default, a DB instance is not publicly accessible (not bound with an EIP) after being created. You can bind an EIP to a DB instance for public accessibility and can unbind the EIP from the DB instance as required.

Precautions
-----------

-  You need to configure security groups and enable specific IP addresses and ports to access the target DB instance. Before accessing the DB instance, you need to add an individual IP address or an IP address range that will access the DB instance to the inbound rule. For details, see section :ref:`Configuring Security Group Rules <rds_02_0009>`.
-  Public accessibility reduces the security of DB instances. Therefore, exercise caution when enabling this function. To achieve a higher transmission rate and security level, you are advised to migrate your applications to the ECS that is in the same region as RDS.


Binding an EIP
--------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **Connectivity & Security**. In the **Connection Information** pane on the **Public Connection** page, click **Bind** in the **EIP** field.

#. In the displayed dialog box, select an EIP and click **OK**.

   If no available EIPs are displayed, click **View EIP** to obtain an EIP.

#. On the **Public Connection** page, view the EIP that has been bound to the DB instance.

   You can also view the progress and result of binding an EIP to a DB instance on the **Task Center** page.

.. |image1| image:: /_static/images/en-us_image_0000001212116857.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
