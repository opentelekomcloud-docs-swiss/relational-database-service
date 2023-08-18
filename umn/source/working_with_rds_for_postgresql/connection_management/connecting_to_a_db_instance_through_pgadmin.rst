:original_name: rds_pg_11_0005.html

.. _rds_pg_11_0005:

Connecting to a DB Instance Through pgAdmin
===========================================

You can use the pgAdmin client to connect to an RDS DB instance.

.. important::

   -  The pgAdmin client only supports access through EIPs.
   -  The pgAdmin version must be 4 or later.

**Preparations**
----------------

#. Prepare a device that can access RDS DB instances.

   To connect to a DB instance through an EIP, you must:

   a. Bind the EIP to the DB instance. For details, see :ref:`Binding an EIP <rds_02_0015>`.
   b. Ensure that the local device can access the EIP that has been bound to the DB instance.

#. Install the pgAdmin client on the prepared device.

Procedure
---------

#. Start pgAdmin.

#. In the displayed login window, choose **Servers** > **Create** > **Server**.


   .. figure:: /_static/images/en-us_image_0000001166955478.png
      :alt: **Figure 1** Creation

      **Figure 1** Creation

#. On the **General** page, specify **Name**. On the **Connection** page, specify information about the DB instance to be connected. Then, click **Save**.


   .. figure:: /_static/images/en-us_image_0000001166636974.png
      :alt: **Figure 2** General page

      **Figure 2** General page


   .. figure:: /_static/images/en-us_image_0000001212475421.png
      :alt: **Figure 3** Connection page

      **Figure 3** Connection page

   Parameter description:

   -  **Host name/address**: indicates the EIP of the DB instance to be connected.
   -  **Port**: indicates the database port. By default, the value is **5432**.
   -  **User name**: indicates the username. By default, the value is **root**.
   -  **Password**: indicates the password of the target database username.

#. In the login window, check that the connection information is correct. The target DB instance is successfully connected.
