:original_name: rds_07_0006.html

.. _rds_07_0006:

Obtaining a DB Instance List
============================

Function
--------

This API is used to obtain a DB instance list.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/instances

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

-  Restrictions

   Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

.. code-block:: text

   GET https://{Endpoint}/v1.0/375d8d8fad1f43039e23d3b6c0f60a19/instances

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------+------------------------------------------------------------------------------------------+----------------------------------------+
      | Name      | Type                                                                                     | Description                            |
      +===========+==========================================================================================+========================================+
      | instances | List data structure. For details, see :ref:`Table 4 <rds_07_0006__table13892167113923>`. | Indicates the DB instance information. |
      +-----------+------------------------------------------------------------------------------------------+----------------------------------------+

   .. table:: **Table 3** instances field data structure description

      +----------+------------------------------------------------------------------------------------------------+----------------------------------------+
      | Name     | Type                                                                                           | Description                            |
      +==========+================================================================================================+========================================+
      | instance | Dictionary data structure. For details, see :ref:`Table 4 <rds_07_0006__table13892167113923>`. | Indicates the DB instance information. |
      +----------+------------------------------------------------------------------------------------------------+----------------------------------------+

   .. _rds_07_0006__table13892167113923:

   .. table:: **Table 4** instance field data structure description

      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | Name                  | Type                                                                                           | Description                                                             |
      +=======================+================================================================================================+=========================================================================+
      | status                | String                                                                                         | Indicates the DB instance status.                                       |
      |                       |                                                                                                |                                                                         |
      |                       |                                                                                                | Value:                                                                  |
      |                       |                                                                                                |                                                                         |
      |                       |                                                                                                | -  If the value is **BUILD**, the instance is being created.            |
      |                       |                                                                                                | -  If the value is **ACTIVE**, the instance is normal.                  |
      |                       |                                                                                                | -  If the value is **FAILED**, the instance is abnormal.                |
      |                       |                                                                                                | -  If the value is **MODIFYING**, the instance is being scaled up.      |
      |                       |                                                                                                | -  If the value is **REBOOTING**, the instance is being rebooted.       |
      |                       |                                                                                                | -  If the value is **RESTORING**, the instance is being restored.       |
      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | name                  | String                                                                                         | Indicates the DB instance name.                                         |
      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | links                 | List data structure. For details, see :ref:`Table 5 <rds_07_0006__table26919596115413>`.       | Indicates the link address.                                             |
      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | id                    | String                                                                                         | Indicates the DB instance ID.                                           |
      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | volume                | Dictionary data structure. For details, see :ref:`Table 6 <rds_07_0006__table47858865115627>`. | Indicates the volume information.                                       |
      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | flavor                | Dictionary data structure. For details, see :ref:`Table 7 <rds_07_0006__table45121734115759>`. | Indicates the DB instance specifications.                               |
      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | datastore             | Dictionary data structure. For details, see :ref:`Table 8 <rds_07_0006__table25266871114925>`. | Indicates the database information.                                     |
      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | region                | String                                                                                         | Indicates the region where the DB instance is deployed.                 |
      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | ip                    | String                                                                                         | Indicates the DB instance IP address.                                   |
      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | replica_of            | Dictionary data structure. For details, see :ref:`Table 9 <rds_07_0006__table2070063511535>`.  | Indicates the primary DB instance ID corresponding to the read replica. |
      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | hostname              | String                                                                                         | Indicates the domain name. Its value is **null**.                       |
      |                       |                                                                                                |                                                                         |
      |                       |                                                                                                | Currently, this parameter is not supported.                             |
      +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+

   .. _rds_07_0006__table26919596115413:

   .. table:: **Table 5** links field data structure description

      ==== ====== ======================================
      Name Type   Description
      ==== ====== ======================================
      rel  String Its value is **self** or **bookmark**.
      href String Its value is **""**.
      ==== ====== ======================================

   .. _rds_07_0006__table47858865115627:

   .. table:: **Table 6** volume field data structure description

      ==== ====== ==========================
      Name Type   Description
      ==== ====== ==========================
      type String Indicates the volume type.
      size Int    Indicates the volume size.
      ==== ====== ==========================

   .. _rds_07_0006__table45121734115759:

   .. table:: **Table 7** flavor field data structure description

      +-------+------------------------------------------------------------------------------------------+---------------------------------+
      | Name  | Type                                                                                     | Description                     |
      +=======+==========================================================================================+=================================+
      | id    | String                                                                                   | Indicates the specification ID. |
      +-------+------------------------------------------------------------------------------------------+---------------------------------+
      | links | List data structure. For details, see :ref:`Table 5 <rds_07_0006__table26919596115413>`. | Indicates the link address.     |
      +-------+------------------------------------------------------------------------------------------+---------------------------------+

   .. _rds_07_0006__table25266871114925:

   .. table:: **Table 8** datastore field data structure description

      ======= ====== ===============================
      Name    Type   Description
      ======= ====== ===============================
      type    String Indicates the DB engine type.
      version String Indicates the database version.
      ======= ====== ===============================

   .. _rds_07_0006__table2070063511535:

   .. table:: **Table 9** replica_of field data structure description

      +-------+------------------------------------------------------------------------------------------+---------------------------------------+
      | Name  | Type                                                                                     | Description                           |
      +=======+==========================================================================================+=======================================+
      | id    | String                                                                                   | Indicates the primary DB instance ID. |
      +-------+------------------------------------------------------------------------------------------+---------------------------------------+
      | links | List data structure. For details, see :ref:`Table 5 <rds_07_0006__table26919596115413>`. | Indicates the link address.           |
      +-------+------------------------------------------------------------------------------------------+---------------------------------------+

-  Response example

   .. code-block:: text

      {
        "instances": [
          {
            "instance": {
              "status": "ACTIVE",
              "name": "rds-new-channle-read",
              "links": [
                {
                  "rel": "self",
                  "href": ""
                },
                {
                  "rel": "bookmark",
                  "href": ""
                }
              ],
              "id": "37f52707-2fb3-482c-a444-77a70a4eafd6",
              "volume": {
                "type": "ULTRAHIGH",
                "size": 100
              },
              "flavor": {
                "id": "7fbf27c5-07e5-43dc-cf13-ad7a0f1c5d9a",
                "links": [
                  {
                    "rel": "self",
                    "href": ""
                  },
                  {
                    "rel": "bookmark",
                    "href": ""
                  }
                ]
              },
              "datastore": {
                "type": "PostgreSQL",
                "version": "PostgreSQL-12"
              },

              "region": "aaa",
              "ip": "192.168.1.29",
              "replica_of": [
                {
                  "id": "c42cdd29-9912-4b57-91a8-c37a845566b1",
                  "links": [
                    {
                      "rel": "self",
                      "href": ""
                    },
                    {
                      "rel": "bookmark",
                      "href": ""
                    }
                  ]
                }
              ],
              "hostname": null
            }
          }
        ]
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
