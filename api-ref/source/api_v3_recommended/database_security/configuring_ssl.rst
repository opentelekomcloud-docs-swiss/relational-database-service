:original_name: rds_05_0017.html

.. _rds_05_0017:

Configuring SSL
===============

Function
--------

This API is used to configure SSL to encrypt connections.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

Constraints
-----------

SSL cannot be configured when a DB instance is being created, rebooted, or upgraded, its specifications are being modified, or database users are being created or deleted.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/ssl

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

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------+
      | Name            | Mandatory       | Type            | Description                      |
      +=================+=================+=================+==================================+
      | ssl_option      | Yes             | boolean         | Specifies whether to enable SSL. |
      |                 |                 |                 |                                  |
      |                 |                 |                 | -  **true**: SSL is enabled.     |
      |                 |                 |                 | -  **false**: SSL is disabled.   |
      +-----------------+-----------------+-----------------+----------------------------------+

-  Request example

   .. code-block:: text

      PUT https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/ssl

   .. code-block:: text

      {
           "ssl_option": true
      }

Response
--------

-  Example normal response

   .. code-block:: text

      {}

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
