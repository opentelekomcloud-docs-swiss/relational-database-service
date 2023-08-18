:original_name: rds_mysql_0001.html

.. _rds_mysql_0001:

Configuring an SSL Connection
=============================

Secure Socket Layer (SSL) is an encryption-based Internet security protocol for establishing an encrypted link between a server and a client. It provides privacy, authentication, and integrity to Internet communications. It has the following functions:

-  Authenticates users and servers, ensuring that data is sent to the correct clients and servers.
-  Encrypts data, preventing it from being intercepted during transmission.
-  Ensures data integrity during transmission.

SSL is disabled by default for MySQL DB instances. You can enable SSL by referring to :ref:`Enabling SSL <rds_mysql_0001__section52887001420>`. SSL encrypts connections to databases but it increases the connection response time and CPU usage. Therefore, you are advised not to enable SSL.

You can connect to a DB instance through a common connection or an SSL connection.

-  If SSL is enabled, you can connect to a database using SSL, which is more secure.
-  If SSL is disabled, you can connect to a database using a common connection.

.. important::

   Enabling or disabling SSL will cause DB instances to reboot and interrupt connections. Exercise caution when performing this operation.

.. _rds_mysql_0001__section52887001420:

Enabling SSL
------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the **DB Information** area on the **Basic Information** page, click |image2| in the **SSL** field.
#. In the displayed dialog box, click **Yes**.
#. Wait for some seconds and check that SSL has been enabled on the **Basic Information** page.

Disabling SSL
-------------

#. Log in to the management console.
#. Click |image3| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the **DB Information** area on the **Basic Information** page, click |image4| in the **SSL** field.
#. In the displayed dialog box, click **Yes**.
#. Wait for some seconds and check that SSL has been disabled on the **Basic Information** page.

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
.. |image2| image:: /_static/images/en-us_image_0000001212196819.png
.. |image3| image:: /_static/images/en-us_image_0000001166476958.png
.. |image4| image:: /_static/images/en-us_image_0000001166795498.png
