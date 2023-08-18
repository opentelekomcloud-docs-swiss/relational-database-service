:original_name: en-us_topic_scale_cluster.html

.. _en-us_topic_scale_cluster:

Scaling up Storage Space
========================

**Scenarios**
-------------

You can scale up storage space if it is no longer sufficient for your requirements. If the DB instance status is **Storage full** and data cannot be written to databases, you need to scale up storage space.

For details about the causes and solutions of insufficient storage space, see section :ref:`What Should I Do If My Data Exceeds the Available Storage of an RDS DB Instance? <rds_faq_0046>`

RDS allows you to scale up storage space of DB instances but you cannot change the storage type. During the scale-up period, services are not interrupted.

Constraints
-----------

-  The maximum allowed storage is 4,000 GB. There is no limit on the number of scale-ups.
-  The DB instance is in **Scaling up** state when its storage space is being scaled up and the backup services are not affected.
-  For primary/standby DB instances, scaling up the primary DB instance will cause the standby DB instance to also be scaled up accordingly.
-  You cannot reboot or delete a DB instance that is being scaled up.
-  Storage space can only be scaled up, not down.

Scaling up a Primary DB Instance
--------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Scale Storage Space** in the **Operation** column.

   You can also perform the following operations to scale up storage space:

   -  Click the target DB instance to enter the **Basic Information** page. In the **Storage Space** area, click **Scale Storage Space**.

#. On the displayed page, specify the new storage space and click **Next**.

   The minimum start value of each scaling is 10 GB. A read replica can be scaled up only by a multiple of 10 GB. The allowed maximum storage space is 4,000 GB.

#. Confirm specifications.

   -  If you need to modify your settings, click **Previous**.
   -  If you do not need to modify your settings, click **Submit**.

#. View the scale-up result.

   Scaling up storage space takes 3-5 minutes. During the time period, the status of the DB instance on the **Instances** page will be **Scaling up**. Click the DB instance and view the utilization on the displayed **Basic Information** page to verify that the scale-up is successful.

   If the DB instance is running the MySQL DB engine, you can view the detailed progress and result of the task on the **Task Center** page. For details, see section :ref:`Task Center <rds_05_0007>`.

Scaling up a Read Replica
-------------------------

Scaling up the storage space of a read replica does not affect that of the primary DB instance. Therefore, you can separately scale read replicas to meet service requirements. New storage space of read replicas after scaling up must be greater than or equal to that of the primary DB instance.

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and a project.

#. Click |image4| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and click |image5| in front of it. Locate a read replica to be scaled and choose **More** > **Scale Storage Space** in the **Operation** column.

   You can also perform the following operations to scale up storage space:

   -  Click the target DB instance to enter the **Basic Information** page. In the **Storage Space** area, click **Scale Storage Space**.

#. On the displayed page, specify the new storage space and click **Next**.

   The minimum start value of each scaling is 10 GB. A read replica can be scaled up only by a multiple of 10 GB. The allowed maximum storage space is 4,000 GB.

#. Confirm specifications.

   -  If you need to modify your settings, click **Previous**.
   -  If you do not need to modify your settings, click **Submit**.

#. View the scale-up result.

   Scaling up storage space takes 3-5 minutes. During the time period, the status of the read replica on the **Instances** page will be **Scaling up**. Click the read replica and view the utilization on the displayed **Basic Information** page to verify that the scale-up is successful.

   If the read replica is running the MySQL DB engine, you can view the detailed progress and result of the task on the **Task Center** page. For details, see section :ref:`Task Center <rds_05_0007>`.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001166476958.png
.. |image4| image:: /_static/images/en-us_image_0000001212196809.png
.. |image5| image:: /_static/images/en-us_image_0000001212475417.png
