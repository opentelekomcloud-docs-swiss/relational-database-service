:original_name: rds_09_0025.html

.. _rds_09_0025:

Deleting a DB Instance or Read Replica
======================================

**Scenarios**
-------------

You can delete DB instances or read replicas as required on the **Instances** page to release resources.

Constraints
-----------

DB instance deletion has the following constraints:

-  DB instances cannot be deleted when operations are being performed on them. They can be deleted only after the operations are complete.
-  If you delete a DB instance, its automated backups will also be deleted and you will no longer be billed for them. Manual backups, however, will be retained and generate additional costs.

.. important::

   -  If you delete a primary DB instance, its standby DB instance and read replicas (if any) are also deleted automatically. Exercise caution when performing this operation.
   -  Deleted DB instances cannot be recovered and resources are released. Exercise caution when performing this operation. If you want to retain data, :ref:`create a manual backup <rds_09_0028>` first before deleting the DB instance.

Deleting a DB Instance
----------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate the target primary DB instance to be deleted and click **More** > **Delete** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.
#. Refresh the DB instance list later to check that the deletion is successful.

Deleting a Read Replica
-----------------------

#. Log in to the management console.
#. Click |image3| in the upper left corner and select a region and a project.
#. Click |image4| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate the target DB instance and click |image5| in front of it. All the read replicas created for the DB instance are displayed.
#. Locate the target read replicas to be deleted and click **More** > **Delete** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.
#. Refresh the DB instance list later to check that the deletion is successful.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001166476958.png
.. |image4| image:: /_static/images/en-us_image_0000001212196809.png
.. |image5| image:: /_static/images/en-us_image_0000001212355381.png
