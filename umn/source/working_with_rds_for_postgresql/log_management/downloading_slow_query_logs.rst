:original_name: slow_query_log-pg.html

.. _slow_query_log-pg:

Downloading Slow Query Logs
===========================

**Scenarios**
-------------

Slow query logs record statements that exceed the **log_min_duration_statement** value. You can download slow query logs for service analysis.

RDS supports the following statement types:

-  SELECT
-  INSERT
-  UPDATE
-  DELETE
-  CREATE
-  DROP
-  ALTER
-  DO
-  CALL
-  COPY

Parameter Description
---------------------

.. table:: **Table 1** Parameters related to PostgreSQL slow queries

   +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Description                                                                                                                                     |
   +============================+=================================================================================================================================================+
   | log_min_duration_statement | Specifies the minimum execution time. The statements whose execution time is greater than or equal to the value of this parameter are recorded. |
   +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

Downloading a Log
-----------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Logs**. On the **Slow Query Logs** page, locate a log whose status is **Preparation completed** and click **Download** in the **Operation** column.

   -  The system automatically loads the downloading preparation tasks. The loading duration is determined by the log file size and network environment.

      -  During the downloading preparation, the log status is **Preparing**.
      -  After the downloading preparation is complete, the log status is **Preparation completed**.
      -  If the downloading preparation fails, the log status is **Abnormal**.

      Logs in the **Preparing** or **Abnormal** status cannot be downloaded.

   -  If the size of a log to be downloaded is greater than 40 MB, you need to use OBS Browser to download it.

   -  The download link is valid for 5 minutes. After the download link expires, a message is displayed indicating that the download link has expired. If you need to download the log, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
