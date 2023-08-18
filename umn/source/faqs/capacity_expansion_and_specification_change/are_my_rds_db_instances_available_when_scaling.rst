:original_name: rds_faq_0016.html

.. _rds_faq_0016:

Are My RDS DB Instances Available When Scaling?
===============================================

Currently, you can scale up storage space and change the CPU or memory of a DB instance.

-  When scaling storage space, RDS DB instances are available and services are not affected. However, you cannot delete or reboot DB instances that are being scaled.
-  When changing the CPU or memory of DB instances, the network is intermittently disconnected once or twice within a few seconds. (For Microsoft SQL Server 2017 Enterprise Edition, you need to stop services first and then change the CPU or memory of DB instances.) For primary/standby DB instances, a failover may occur and services may be interrupted for a short period of time.
