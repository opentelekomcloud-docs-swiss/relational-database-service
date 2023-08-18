:original_name: slow_query_log-sqlserver.html

.. _slow_query_log-sqlserver:

Downloading Slow Query Logs
===========================

Scenarios
---------

Slow query logs record statements that exceed **long_query_time** (1 second by default). You can view log details to identify statements that are executing slowly and optimize the statements. You can also download slow query logs for service analysis.

Parameter Description
---------------------

.. table:: **Table 1** Parameters related to Microsoft SQL Server slow queries

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                               |
   +===================================+===========================================================================================================================================================================================================================================================================+
   | long_query_time                   | Specifies the time greater than or equal to which slow query logs are recorded. The precision is microsecond. The default value is 1s. When the execution time of an SQL statement exceeds the value of this parameter, the SQL statement is recorded in slow query logs. |
   |                                   |                                                                                                                                                                                                                                                                           |
   |                                   | You can modify the slow log threshold as required.                                                                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                                           |
   |                                   | #. Log in to the management console.                                                                                                                                                                                                                                      |
   |                                   | #. Click |image1| in the upper left corner and select a region and a project.                                                                                                                                                                                             |
   |                                   | #. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.                                                                                                                           |
   |                                   | #. On the **Instances** page, click the target DB instance.                                                                                                                                                                                                               |
   |                                   | #. In the navigation pane on the left, choose **Logs**. On the **Slow Query Logs** page, click |image3| in the **Threshold of Slow Query Log (long_query_time)** field to change the threshold.                                                                           |
   |                                   |                                                                                                                                                                                                                                                                           |
   |                                   |    -  To submit the change, click |image4|.                                                                                                                                                                                                                               |
   |                                   |    -  To cancel the change, click |image5|.                                                                                                                                                                                                                               |
   |                                   |                                                                                                                                                                                                                                                                           |
   |                                   |    .. note::                                                                                                                                                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                                                           |
   |                                   |       The recommended value is **1s**. The lock wait time is not calculated into the query time.                                                                                                                                                                          |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Downloading a Log
-----------------

#. Log in to the management console.

#. Click |image6| in the upper left corner and select a region and a project.

#. Click |image7| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **Logs**. On the **Slow Query Logs** page, click |image8| to enable the slow query log function.

   .. note::

      Enabling slow query log slightly affects DB instance performance.

#. .. _slow_query_log-sqlserver__en-us_topic_0171818656_li121912551908:

   Locate a log to be downloaded and click **Download** in the **Operation** column.

   a. The system automatically loads the downloading preparation tasks. The loading duration is determined by the log file size and network environment.

      -  During the downloading preparation, the log status is **Preparing**.
      -  After the downloading preparation is complete, the log status is **Preparation completed**.
      -  If the downloading preparation fails, the log status is **Abnormal**.

   b. In the displayed dialog box, click **OK** to download the log whose status is **Preparation completed**. If you click **Cancel**, the system does not download the log.

      The download link is valid for 5 minutes. After the download link expires, a message is displayed indicating that the download link has expired. You can close the window and repeat the procedure :ref:`6 <slow_query_log-sqlserver__en-us_topic_0171818656_li121912551908>` to try to download a log again.

      .. note::

         After downloading slow query logs to a local PC, you can use SSMS to connect to the local database and run the following SQL statement to view the slow query log details:

         **select \* from ::fn_trace_gettable('XXX', default)**

         In the preceding command, *XXX* indicates the local path for storing slow query logs.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001252696347.png
.. |image4| image:: /_static/images/en-us_image_0000001208420452.png
.. |image5| image:: /_static/images/en-us_image_0000001252457151.png
.. |image6| image:: /_static/images/en-us_image_0000001166476958.png
.. |image7| image:: /_static/images/en-us_image_0000001212196809.png
.. |image8| image:: /_static/images/en-us_image_0000001212196911.png
