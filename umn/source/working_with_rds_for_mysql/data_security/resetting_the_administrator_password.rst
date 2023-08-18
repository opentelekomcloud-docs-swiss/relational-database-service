:original_name: rds_reset_password.html

.. _rds_reset_password:

Resetting the Administrator Password
====================================

**Scenarios**
-------------

You can reset the administrator password of a primary instance.

If you forget the password of the administrator account **root** when using RDS, you can reset the password.

Precautions
-----------

-  If you have changed the administrator password of the primary DB instance, the administrator passwords of the standby DB instance and read replicas (if any) will also be changed accordingly.
-  The time required for the new password to take effect depends on the amount of service data currently being processed by the primary DB instance.
-  To prevent brute force cracking and ensure system security, change your password periodically.

Method 1
--------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click |image2| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Reset Password** in the **Operation** column.

#. Enter a new password and confirm the password.

   .. important::

      Keep this password secure. The system cannot retrieve it.

   The new password must consist of 8 to 32 characters and contain at least three types of the following characters: uppercase letters, lowercase letters, digits, and special characters (``~!@#%^*-_=+?``). Enter a strong password and periodically change it for security reasons.

   -  To submit the new password, click **OK**.
   -  To cancel the reset operation, click **Cancel**.

Method 2
--------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and a project.

#. Click |image4| in the upper left corner of the page and choose **Database** > **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the **DB Information** area on the **Basic Information** page, click **Reset Password** in the **Administrator** field.

#. Enter a new password and confirm the password.

   .. important::

      Keep this password secure. The system cannot retrieve it.

   The new password must consist of 8 to 32 characters and contain at least three types of the following characters: uppercase letters, lowercase letters, digits, and special characters (``~!@#%^*-_=+?``). Enter a strong password and periodically change it for security reasons.

   -  To submit the new password, click **OK**.
   -  To cancel the reset operation, click **Cancel**.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196809.png
.. |image3| image:: /_static/images/en-us_image_0000001166476958.png
.. |image4| image:: /_static/images/en-us_image_0000001212196809.png
