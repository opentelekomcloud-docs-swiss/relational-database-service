:original_name: rds_01_0010.html

.. _rds_01_0010:

Abnormal Request Results
========================

v3 APIs
-------

**Abnormal response description**

.. table:: **Table 1** Abnormal response description

   +------------+--------+------------------------------------------------------------------------------------------+
   | Name       | Type   | Description                                                                              |
   +============+========+==========================================================================================+
   | error_code | String | Specifies the error returned when a task submission exception occurs.                    |
   +------------+--------+------------------------------------------------------------------------------------------+
   | error_msg  | String | Specifies the description of the error returned when a task submission exception occurs. |
   +------------+--------+------------------------------------------------------------------------------------------+

**Response example**

.. code-block:: text

   {
       "error_code": "DBS.200022",
       "error_msg": "The DB instance name already exists."
   }

v1 APIs
-------

**Abnormal response description**

.. table:: **Table 2** Abnormal response description

   +-----------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Type   | Description                                                                                                                                                  |
   +=================+========+==============================================================================================================================================================+
   | errCode         | String | Specifies the error code returned when a task submission exception occurs. For details, see :ref:`Table 2 <rds_10_0201__td93aca0e44834bb3939478d798feb72e>`. |
   +-----------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | externalMessage | String | Specifies the description of the error returned when a task submission exception occurs.                                                                     |
   +-----------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Response example**

.. code-block:: text

   {
       "errCode": "RDS.1102",
       "externalMessage": "The DB instance name already exists."
   }

OpenStack Trove API v1.0 APIs
-----------------------------

**Abnormal response description**

.. table:: **Table 3** Abnormal response description (using itemNotFound as an example)

   +--------------+-----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Name         | Type                                                                                    | Description                                                                                                                           |
   +==============+=========================================================================================+=======================================================================================================================================+
   | itemNotFound | List data structure. For details, see :ref:`Table 4 <rds_01_0010__table6204277318822>`. | Specifies the error type when a task submission exception occurs. For details, see :ref:`Table 3 <rds_10_0201__table57182163211057>`. |
   +--------------+-----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+

.. _rds_01_0010__table6204277318822:

.. table:: **Table 4** Error type parameter data structure description

   +---------+--------+------------------------------------------------------------------------------------------+
   | Name    | Type   | Description                                                                              |
   +=========+========+==========================================================================================+
   | code    | String | Specifies the response code returned when a task submission exception occurs.            |
   +---------+--------+------------------------------------------------------------------------------------------+
   | message | String | Specifies the description of the error returned when a task submission exception occurs. |
   +---------+--------+------------------------------------------------------------------------------------------+

**Response example**

.. code-block:: text

   {
     "itemNotFound": {
       "code": 404,
       "message": "The resource could not be found."
     }
   }
