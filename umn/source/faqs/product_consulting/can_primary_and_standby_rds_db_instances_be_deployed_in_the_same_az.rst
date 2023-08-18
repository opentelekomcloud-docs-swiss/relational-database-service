:original_name: rds_faq_0170.html

.. _rds_faq_0170:

Can Primary and Standby RDS DB Instances Be Deployed in the Same AZ?
====================================================================

An AZ is a physical region where resources use independent power supply and networks. AZs are physically isolated but interconnected through an internal network.

RDS allows you to deploy primary/standby DB instances in an AZ or across AZs. You can determine whether the standby AZ is the same as the primary AZ.

-  If they are the same (default setting), the primary and standby DB instances are deployed in the same AZ.
-  If they are different, the primary and standby DB instances are deployed in different AZs to ensure failover support and high availability.
