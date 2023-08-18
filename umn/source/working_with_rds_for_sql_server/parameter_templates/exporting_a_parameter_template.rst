:original_name: rds_sqlserver_08_0042.html

.. _rds_sqlserver_08_0042:

Exporting a Parameter Template
==============================

Scenarios
---------

Exporting instance parameters:

-  You can export parameters of a DB instance as a new parameter template for future use. To apply the exported parameter template to new DB instances, see :ref:`Applying a Parameter Template <rds_sqlserver_05_0018>`.
-  You can also export the parameter information (including parameter names, values, and descriptions) of a DB instance to a CSV file for viewing and analyzing details.

Exporting Instance Parameters
-----------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Parameters**. On the displayed page, click **Export** above the parameter list.

   -  Exporting to a custom template

      In the displayed dialog box, configure required information and click **OK**.

      .. note::

         -  The template name must consist of 1 to 64 characters. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.).
         -  The description consists of a maximum of 256 characters and cannot contain carriage return characters or the following special characters: >!<"&'=

      After the parameter template is exported, a new template is generated in the list in the **Custom Templates** tab on the **Parameter Templates** page.

   -  Exporting to a file

      The parameter template information (parameter names, values, and descriptions) of the DB instance is exported to a CSV file. In the displayed dialog box, enter the file name and click **OK**.

      .. note::

         The file name must start with a letter and consist of 4 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.


Exporting a Parameter Template
------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and a project.

#. Click |image4| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Parameter Templates** page, click **Default Templates** or **Custom Templates** as needed. On the displayed page, locate the target template and choose **More** > **Export** in the **Operation** column.

#. In the displayed dialog box, enter a file name and click **OK**.

   The file name can contain 4 to 81 characters.

.. |image1| image:: /_static/images/en-us_image_0000001672578153.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001624178242.png
.. |image4| image:: /_static/images/en-us_image_0000001212196809.png
