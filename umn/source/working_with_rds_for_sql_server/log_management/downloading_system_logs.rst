:original_name: rds_sqlserver_01_0002.html

.. _rds_sqlserver_01_0002:

Downloading System Logs
=======================

**Scenarios**
-------------

System logs contain logs generated during the database running. These can help you analyze problems with the database. You can also download system logs for service analysis.

Download a Log
--------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Logs**. On the **System Logs** page, click **Download**.

   a. .. _rds_sqlserver_01_0002__li1121595218910:

      Locate a log to be downloaded and click **Download** in the **Operation** column.

      The system automatically loads the downloading preparation tasks. The loading duration is determined by the log file size and network environment.

      -  During the downloading preparation, the log status is **Preparing**.
      -  After the downloading preparation is complete, the log status is **Preparation completed**.
      -  If the downloading preparation fails, the log status is **Abnormal**.

   b. In the displayed dialog box, click **OK** to download the log whose status is **Preparation completed**. If you click **Cancel**, the system does not download the log and returns to the **Download** page.

      The download link is valid for 5 minutes. After the download link expires, a message is displayed indicating that the download link has expired. You can close the window and repeat the procedure :ref:`5.a <rds_sqlserver_01_0002__li1121595218910>` to try to download a log again.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
