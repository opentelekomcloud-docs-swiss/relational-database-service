:original_name: rds_faq_0042.html

.. _rds_faq_0042:

How Can I Back Up an RDS Database to an ECS?
============================================

You can back up data to an ECS the same way you export SQL statements. The ECS service does not have restrictions on the types of data to be backed up as long as the data complies with local laws and regulations. You can store RDS backup data on an ECS. However, you are advised not to use an ECS as the database backup space. You are advised to store RDS backup data to OBS for higher data reliability and service assurance.
