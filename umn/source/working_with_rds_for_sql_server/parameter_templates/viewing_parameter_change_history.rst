:original_name: rds_sqlserver_05_0099.html

.. _rds_sqlserver_05_0099:

Viewing Parameter Change History
================================

Scenarios
---------

You can view the change history of DB instance parameters or custom parameter templates.

.. note::

   An exported or custom parameter template has initially a blank change history.

Viewing Change History of a DB Instance
---------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, click **Change History**.

   You can view the parameter name, original parameter value, new parameter value, modification status, modification time, application status, and application time.

   You can apply the parameter template to DB instances as required by referring to section :ref:`Applying a Parameter Template <rds_sqlserver_05_0018>`.

Viewing Change History of a Parameter Template
----------------------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and a project.

#. Click |image4| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. Choose **Parameter Templates** in the navigation pane on the left. On the **Custom Templates** page, click the target parameter template.

#. On the displayed page, choose **Change History** in the navigation pane on the left.

   You can view the parameter name, original parameter value, new parameter value, modification status, and modification time.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001166476958.png
.. |image4| image:: /_static/images/en-us_image_0000001212196809.png
