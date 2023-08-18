:original_name: rds_faq_0057.html

.. _rds_faq_0057:

How Can I Create and Connect to an ECS?
=======================================

#. For details about how to create an ECS, see the *Elastic Cloud Server User Guide*.

   -  The ECS is used for connecting to an RDS DB instance and must be located in the same VPC as the RDS DB instance.
   -  Configure a security group to allow the ECS to access the RDS DB instance through the private address.

#. For details on how to connect to the ECS, see "Logging in to an ECS" in the *Elastic Cloud Server User Guide*.
