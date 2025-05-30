:original_name: rds_14_0001.html

.. _rds_14_0001:

Modifying Recycling Policy
==========================

Function
--------

This API is used to modify the recycling policy for the recycle bin.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{project_id}/instances/recycle-policy

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                  |
      +=================+=================+=================+==============================================================================================+
      | recycle_policy  | Yes             | Object          | Each element is associated with the recycle bin.                                             |
      |                 |                 |                 |                                                                                              |
      |                 |                 |                 | For details on the element structure, see :ref:`Table 3 <rds_14_0001__table20307125662116>`. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+

   .. _rds_14_0001__table20307125662116:

   .. table:: **Table 3** recycle_policy elements

      +--------------------------+-----------------+-----------------+-----------------------------------------------------------------------------+
      | Name                     | Mandatory       | Type            | Description                                                                 |
      +==========================+=================+=================+=============================================================================+
      | retention_period_in_days | No              | String          | Period of retaining deleted DB instances from 1 day to 7 days.              |
      |                          |                 |                 |                                                                             |
      |                          |                 |                 | If this parameter is left blank, the retention period is 7 days by default. |
      +--------------------------+-----------------+-----------------+-----------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      PUT https://{Endpoint}/v3/054ea741f700d4a32f1bc00f5c80dd4c/instances/recycle-policye

   .. code-block:: text

      {
           "recycle_policy":
                    {
                       "retention_period_in_days":"1"
                     }
      }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

      ====== ====== ==================================================
      Name   Type   Description
      ====== ====== ==================================================
      result String Returns **success** if the invoking is successful.
      ====== ====== ==================================================

-  Example normal response

   .. code-block:: text

      {
          "result": "success"
      }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <rds_01_0010>`.

Status Code
-----------

For details, see :ref:`Status Codes <rds_10_0200>`.

Error Code
----------

For details, see :ref:`Error Codes <rds_10_0201>`.
