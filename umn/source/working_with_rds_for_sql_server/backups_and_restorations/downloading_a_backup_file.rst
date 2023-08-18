:original_name: rds_11_0013.html

.. _rds_11_0013:

Downloading a Backup File
=========================

Scenarios
---------

This section describes how to download a manual backup or an automated backup to a local device and restore data from the backup file.

Constraints
-----------

-  If the size of backup files to be downloaded is greater than 400 MB, you are advised to use OBS Browser to download them.

Method 1: Using OBS Browser
---------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Backup Management** page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

   Alternatively, click the target DB instance. In the navigation pane on the left, choose **Backups & Restorations**. On the displayed page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

#. In the displayed dialog box, select **Use OBS Browser** for **Download Method** and click **OK**.

   a. Download OBS Browser

   b. Decompress and install OBS Browser.

   c. Log in to OBS Browser.

   d. Disable certificate verification on OBS Browser.

      For details on how to configure OBS Browser, see section "Configuring the System" in the *OBS Browser Operation Guide*.

      .. note::

         The OBS bucket name displayed in the **Download Backup File** pane on the RDS console does not support certificate verification. Therefore, you need to disable OBS Browser certificate verification before adding the external bucket and then enable it after the backup file is downloaded.

   e. Add an external bucket.

      In the **Add Bucket** dialog box of OBS Browser, select **Add external bucket** and enter the bucket name provided in step 2 "Add an External Bucket" of the RDS console.

   f. Download the backup file.

      On the OBS Browser page, click the bucket that has been successfully added. In the search box on the right of OBS Browser, enter the backup file name displayed on **Download the Backup File** of the RDS console. In the search result, locate the target backup and download it.

      Microsoft SQL Server allows you to download backup files of a specific database.

   g. After the backup file is downloaded, enable OBS Browser certificate verification.

#. Follow the instructions provided in :ref:`Restoring from Backup Files to a Self-Built SQL Server Database <rds_05_0044>` to restore data locally as required.

Method 2: Using Current Browser
-------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and a project.

#. Click |image4| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Backup Management** page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

   Alternatively, click the target DB instance. In the navigation pane on the left, choose **Backups & Restorations**. On the displayed page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

#. In the displayed dialog box, select **Use Current Browser** for **Download Method** and click **OK**.

#. Follow the instructions provided in :ref:`Restoring from Backup Files to a Self-Built SQL Server Database <rds_05_0044>` to restore data locally as required.

Method 3: Using Download URL
----------------------------

#. Log in to the management console.

#. Click |image5| in the upper left corner and select a region and a project.

#. Click |image6| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Backup Management** page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

   Alternatively, click the target DB instance. In the navigation pane on the left, choose **Backups & Restorations**. On the displayed page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

#. In the displayed dialog box, select a method to download backup data.

   In the displayed dialog box, select **Use Download URL** for **Download Method**, click |image7| to copy the URL, and click **OK**.

   For Microsoft SQL Server DB instances, the URLs of all the backup files are displayed. You can download the backup files of a specific database.

   -  You can use other download tools to download backup files.

   -  You can also run the following command to download backup files:

      **wget -O** *FILE_NAME* **--no-check-certificate** **"**\ *DOWNLOAD_URL*\ **"**

      Variables in the commands are described as follows:

      *FILE_NAME*: indicates the new backup file name after the download is successful. The original backup file name may be too long and exceed the maximum characters allowed by the client file system. You are advised to add -O in the wget command to rename the backup file name.

      *DOWNLOAD_URL*: indicates the path of the backup file to be downloaded. If the path contains special characters, escape is required.

#. Follow the instructions provided in :ref:`Restoring from Backup Files to a Self-Built SQL Server Database <rds_05_0044>` to restore data locally as required.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001166476958.png
.. |image4| image:: /_static/images/en-us_image_0000001212196809.png
.. |image5| image:: /_static/images/en-us_image_0000001166476958.png
.. |image6| image:: /_static/images/en-us_image_0000001212196809.png
.. |image7| image:: /_static/images/en-us_image_0000001212117063.png
