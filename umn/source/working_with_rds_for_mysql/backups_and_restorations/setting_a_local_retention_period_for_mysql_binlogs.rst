:original_name: rds_05_0037.html

.. _rds_05_0037:

Setting a Local Retention Period for MySQL Binlogs
==================================================

Scenarios
---------

RDS for MySQL deletes local binlogs after they are backed up to OBS. You can set the local retention period for binlogs as required.

.. note::

   Binlog is enabled for RDS by default and uses the row-based logging.

Binlogs can be retained from 0 to 168 (7x24) hours locally.

The rules for deleting local binlogs are as follows:

#. The binlogs used for replication between primary DB instances and standby DB instances or read replicas are not deleted, even when the retention period is set to 0.
#. To avoid full disk space, you can submit a service ticket to enable the forceful binlog deletion function. If the local space usage exceeds 80%, local binlogs (excluding those used for primary/standby replication) will be deleted forcibly regardless of the retention period configured for local binlogs. If the local space usage exceeds 90%, local binlogs (including those used for primary/standby replication) will be deleted forcibly regardless of the local retention period.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Backups & Restorations**. On the **Binlog Backups** page, click **Set Binlog Retention Period**.
#. In the displayed dialog box, set the local retention period and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
