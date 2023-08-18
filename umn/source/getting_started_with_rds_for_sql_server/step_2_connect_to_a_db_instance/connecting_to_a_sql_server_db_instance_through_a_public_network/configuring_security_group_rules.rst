:original_name: rds_03_0051.html

.. _rds_03_0051:

Configuring Security Group Rules
================================

Scenarios
---------

A security group is a collection of access control rules for ECSs and RDS DB instances that have the same security protection requirements and are mutually trusted in a VPC.

This section describes how to create a security group to enable specific IP addresses and ports to access RDS.

When you attempt to connect to an RDS DB instance through an EIP, you need to configure an **inbound rule** for the security group associated with the DB instance.

Precautions
-----------

The default security group rule allows all outgoing data packets. ECSs and RDS DB instances can access each other if they are deployed in the same security group. After a security group is created, you can configure security group rules to control access from and to the DB instances in the security group.

-  By default, a tenant can create a maximum of 100 security groups.
-  By default, each security group can have a maximum of 50 security group rules.
-  One RDS DB instance can be associated only with one security group.
-  Too many security group rules will increase the first packet latency. You are advised to create no more than 50 rules for each security group.
-  To access an RDS DB instance from resources outside the security group, you need to configure an **inbound rule** for the security group associated with the RDS DB instance.

.. note::

   If you use **0.0.0.0/0**, you enable all IP addresses to access RDS DB instances in the security group.

Procedure
---------

#. Log in to the management console.
#. Under **Network**, click **Virtual Private Cloud**.
#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.
#. On the **Security Groups** page, locate the target security group and click **Manage Rule** in the **Operation** column.
#. On the displayed page, click **Add Rule**.
#. In the displayed dialog box, set required parameters to add an inbound rule.
#. Click **OK**.
