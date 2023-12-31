:original_name: rds_05_0004.html

.. _rds_05_0004:

Obtaining the Link for Downloading an Audit Log
===============================================

Function
--------

This API is used to obtain the link for downloading an audit log.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

Constraints
-----------

This API is supported for MySQL only.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/auditlog-links

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the ID of the queried DB instance.                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +------+-----------+------------------+------------------------------------------------------------------------------------------+
      | Name | Mandatory | Type             | Description                                                                              |
      +======+===========+==================+==========================================================================================+
      | ids  | Yes       | Array of strings | Specifies the list of audit logs. A maximum of 50 audit log IDs are allowed in the list. |
      +------+-----------+------------------+------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      POST https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/cee5265e1e5845649e354841234567dfin01/auditlog-links

   .. code-block:: text

      {
          "ids": ["fa163e9970a3t11e9d834e122fdceb1d6br01", "fa163ea0e2bet11e9d8364943103c94c5br01"]
      }

Response
--------

-  Normal response

   .. table:: **Table 3** Parameter description

      +-------+------------------+-----------------------------------------------------------------------------------+
      | Name  | Type             | Description                                                                       |
      +=======+==================+===================================================================================+
      | links | Array of strings | Indicates the list of audit log download links. The validity period is 5 minutes. |
      +-------+------------------+-----------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "links": ["https://obs.domainname.com/rdsbucket.username.1/xxxxxx", "https://obs.domainname.com/rdsbucket.username.2/xxxxxx"]
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
