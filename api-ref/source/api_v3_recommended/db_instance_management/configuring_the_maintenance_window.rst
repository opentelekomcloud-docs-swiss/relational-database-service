:original_name: rds_05_0016.html

.. _rds_05_0016:

Configuring the Maintenance Window
==================================

Function
--------

This API is used to change the maintenance window as required. To prevent service interruption, the maintenance window should fall within the off-peak hours.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/ops-window

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

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                             |
      +=================+=================+=================+=========================================================================+
      | start_time      | Yes             | String          | Specifies the start time (UTC).                                         |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------+
      | end_time        | Yes             | String          | Specifies the end time (UTC).                                           |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 | .. note::                                                               |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 |    The interval between the start time and end time must be four hours. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      PUT https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/ops-window

   .. code-block:: text

      {
           "start_time": "22:00",
           "end_time":"02:00"
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
