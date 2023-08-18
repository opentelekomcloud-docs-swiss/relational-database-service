:original_name: rds_faq_0022.html

.. _rds_faq_0022:

What Should I Do If an RDS Database Problem Causes a Connection Failure?
========================================================================

Check whether any of the following problems have occurred on the RDS DB instance.

#. The RDS DB instance is not properly connected.

   Solution: Check the connection. The RDS DB instance can only be accessed through an ECS in the same VPC.

#. The maximum number of connections has been reached.

   Solution: Use RDS resource monitoring to check if the CPU usage and the number of current connections are abnormal. If either of them has reached the maximum supported, reboot, disconnect, or scale up the specifications of the DB instance.

#. DB instance is abnormal. For example, the RDS DB instance fails to be rebooted, the system is faulty, or the instance or table is locked.

   Solution: Reboot the RDS DB instance to see if the problem is resolved. If the problem persists, contact post-sales technical support.
