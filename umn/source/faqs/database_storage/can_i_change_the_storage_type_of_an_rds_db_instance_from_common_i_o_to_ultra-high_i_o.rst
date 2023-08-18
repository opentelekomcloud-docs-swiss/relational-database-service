:original_name: rds_faq_0076.html

.. _rds_faq_0076:

Can I Change the Storage Type of an RDS DB Instance from Common I/O to Ultra-high I/O?
======================================================================================

No. After an RDS DB instance is created, the storage type cannot be changed.

.. table:: **Table 1** Items that cannot be changed

   +-----------------------------------+-----------------------------------------------------------------------------------+
   | Item                              | Change Direction                                                                  |
   +===================================+===================================================================================+
   | Storage type                      | -  From common I/O to ultra-high I/O                                              |
   |                                   | -  From ultra-high I/O to common I/O                                              |
   |                                   | -  From high I/O to common I/O                                                    |
   |                                   |                                                                                   |
   |                                   | The preceding descriptions are examples only. The storage type cannot be changed. |
   +-----------------------------------+-----------------------------------------------------------------------------------+
