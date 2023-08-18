:original_name: rds_05_0101.html

.. _rds_05_0101:

Enabling or Disabling Event Scheduler
=====================================

Scenarios
---------

Event scheduler manages the scheduling and execution of events. The MySQL built-in event scheduler cannot guarantee the consistency of event statuses between primary and standby DB instances. If a failover or switchover occurs, events will not be scheduled. RDS for MySQL resolves this issue. With RDS for MySQL, even if there is a failover or switchover, event status will still be properly scheduled. You can simply enable or disable the event scheduler on the RDS console.

-  By default, the event scheduler is disabled after a DB instance is created.
-  After a primary/standby failover or switchover, the event status remains unchanged. The **event_scheduler** is **on** for the original primary DB instance and **off** for the original standby DB instance.
-  After a restoration to a new DB instance, the event status is the same as that of the original DB instance.
-  After a single DB instance is changed to primary/standby DB instances, the event status is the same as that of the primary DB instance.

Constraints
-----------

-  Only MySQL kernel 5.6.43.2, 5.7.25.2, 8.0.17.4, and later versions are supported.
-  Event scheduler cannot be enabled for read replicas.

Enabling Event Scheduler
------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target primary/standby DB instances.
#. In the **DB Information** area on the displayed **Basic Information** page, click |image3| in the **Event Scheduler** field.

   .. important::

      After you enable the event scheduler on the RDS console, log in to the DB instance and check that the event status has been set to **enable**.

Disabling Event Scheduler
-------------------------

#. Log in to the management console.
#. Click |image4| in the upper left corner and select a region and a project.
#. Click |image5| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target primary/standby DB instances.
#. In the **DB Information** area on the displayed **Basic Information** page, click |image6| in the **Event Scheduler** field.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001212196819.png
.. |image4| image:: /_static/images/en-us_image_0000001166476958.png
.. |image5| image:: /_static/images/en-us_image_0000001212196809.png
.. |image6| image:: /_static/images/en-us_image_0000001166795498.png
