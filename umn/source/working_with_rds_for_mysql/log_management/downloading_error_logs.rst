:original_name: rds_mysql_error_log.html

.. _rds_mysql_error_log:

Downloading Error Logs
======================

RDS log management allows you to view database-level logs, including error logs and slow SQL query logs.

Downloading an Error Log
------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Logs**. On the **Error Logs** page, locate a log whose status is **Preparation completed** and click **Download** in the **Operation** column.

   -  The system automatically loads the downloading preparation tasks. The loading duration is determined by the log file size and network environment.

      -  During the downloading preparation, the log status is **Preparing**.
      -  After the downloading preparation is complete, the log status is **Preparation completed**.
      -  If the downloading preparation fails, the log status is **Abnormal**.

      Logs in the **Preparing** or **Abnormal** status cannot be downloaded.

   -  If the size of a log to be downloaded is greater than 40 MB, you need to use OBS Browser to download it.

   -  The download link is valid for 5 minutes. After the download link expires, a message is displayed indicating that the download link has expired. If you need to download the log, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
