:original_name: rds_07_0019.html

.. _rds_07_0019:

Deleting a Parameter Template
=============================

Function
--------

This API is used to delete a specified parameter template.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/configurations/{id}

   Method: DELETE

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      id         Yes       Specifies the parameter template ID.
      ========== ========= =================================================

-  Restrictions

   -  Currently, the DB engines MySQL and PostgreSQL support deleting parameter templates.
   -  Parameter templates being applied to DB instances cannot be deleted.
   -  Default parameter templates cannot be deleted.

Request
-------

.. code-block:: text

   DELETE https://{Endpoint}/v1.0/375d8d8fad1f43039e23d3b6c0f60a19/configurations/07fc12a8e0e94df7a3fcf53d0b5e1605pr01

Normal Response
---------------

.. code-block:: text

   {
     "errCode": "RDS.0041",
     "externalMessage": "Operation successful."
   }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <rds_01_0010>`.

Status Code
-----------

For details, see :ref:`Status Codes <rds_10_0200>`.

Error Code
----------

For details, see :ref:`Error Codes <rds_10_0201>`.
