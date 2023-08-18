:original_name: rds_sqlserver_tag.html

.. _rds_sqlserver_tag:

Managing Tags
=============

Scenarios
---------

Tag Management Service (TMS) enables you to use tags on the management console to manage resources. TMS works with other cloud services to manage tags. TMS manages tags globally, and other cloud services manage their own tags.

-  You are advised to set predefined tags on the TMS console.
-  A tag consists of a key and value. You can add only one value for each key.
-  A maximum of 20 tags can be added for each DB instance.

Adding a Tag
------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. On the **Tags** page, click **Add Tag**. In the displayed dialog box, enter a tag key and a tag value, and click **OK**.

   -  The tag key must be unique and must consist of 1 to 36 characters. Each tag key allows letters, numbers, spaces, and the following characters: \_ . : = + - @. It cannot start or endwith a space, or start with \_sys_.
   -  The tag value (optional) can consist of up to 43 characters. Each tag value allows letters, numbers, spaces, and the following characters: \_ . : / = + - @.

#. After a tag has been added, you can view and manage it on the **Tags** page.

Editing a Tag
-------------

#. Log in to the management console.
#. Click |image3| in the upper left corner and select a region and a project.
#. Click |image4| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. On the **Tags** page, locate the tag to be edited and click **Edit** in the **Operation** column. In the displayed dialog box, change the tag value and click **OK**.

   -  Only the tag value can be edited.
   -  The tag value (optional) can consist of up to 43 characters. Each tag value allows letters, numbers, spaces, and the following characters: \_ . : / = + - @.

#. After a tag has been edited, you can view and manage it on the **Tags** page.

Deleting a Tag
--------------

#. Log in to the management console.
#. Click |image5| in the upper left corner and select a region and a project.
#. Click |image6| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. On the **Tags** page, locate the tag to be deleted and click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes**.
#. After a tag has been deleted, it will no longer be displayed on the **Tags** page.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001166476958.png
.. |image4| image:: /_static/images/en-us_image_0000001212196809.png
.. |image5| image:: /_static/images/en-us_image_0000001166476958.png
.. |image6| image:: /_static/images/en-us_image_0000001212196809.png
