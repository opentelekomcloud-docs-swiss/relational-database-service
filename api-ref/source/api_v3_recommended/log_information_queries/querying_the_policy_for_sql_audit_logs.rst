:original_name: rds_05_0002.html

.. _rds_05_0002:

Querying the Policy for SQL Audit Logs
======================================

Function
--------

This API is used to query the policy for SQL audit logs.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

Constraints
-----------

This API is supported for MySQL only.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/auditlog-policy

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

.. code-block:: text

   GET https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/cee5265e1e5845649e354841234567dfin01/auditlog-policy

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------+---------+-----------------------------------------------------------------------------------------------------+
      | Name      | Type    | Description                                                                                         |
      +===========+=========+=====================================================================================================+
      | keep_days | Integer | Specifies the number of days for storing audit logs. The value is **0** when SQL audit is disabled. |
      +-----------+---------+-----------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "keep_days":7
      }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <rds_01_0010>`.

Status Code
-----------

-  Normal

   200

-  Abnormal

   For details, see :ref:`Status Codes <rds_10_0200>`.

Error Code
----------

For details, see :ref:`Error Codes <rds_10_0201>`.
