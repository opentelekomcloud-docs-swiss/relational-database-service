:original_name: rds_08_0002.html

.. _rds_08_0002:

Obtaining Task Information of a Specified SQL Server DB Instance in a Specified Time Range
==========================================================================================

Function
--------

This API is used to obtain the task information list of a specified SQL Server DB instance ID within a specified time range.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required region and endpoint.

Constraints
-----------

-  This API is used to query asynchronous tasks of the last one month in the task center.
-  Information of the following asynchronous tasks can be obtained: creating single or primary/standby DB instances, creating read replicas, changing single DB instances to primary/standby instances, switching primary/standby DB instances, scaling up storage space, creating automated or manual backups, restoring data to original, existing, or new DB instances.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/tasklist/detail?start_time={start_time}&end_time={end_time}

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
      | start_time            | Yes                   | Specifies the start time in the UTC timestamp format.                                            |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | end_time              | No                    | Specifies the end time in the UTC timestamp format.                                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

.. code-block:: text

   GET https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/a48e43ff268f4c0e879652d65e63d0fbin01/tasklist/detail?start_time=1533423274000&end_time=1533823274000

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +------+--------+-----------------------------------------------------------------------------------------------------+
      | Name | Type   | Description                                                                                         |
      +======+========+=====================================================================================================+
      | jobs | Object | Indicates the task information. For details, see :ref:`Table 3 <rds_08_0002__table54571314103317>`. |
      +------+--------+-----------------------------------------------------------------------------------------------------+

   .. _rds_08_0002__table54571314103317:

   .. table:: **Table 3** jobs field data structure description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                               |
      +=======================+=======================+===========================================================================================================================+
      | id                    | String                | Indicates the task ID.                                                                                                    |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the task name.                                                                                                  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the task execution status.                                                                                      |
      |                       |                       |                                                                                                                           |
      |                       |                       | Value:                                                                                                                    |
      |                       |                       |                                                                                                                           |
      |                       |                       | -  **Running**: The task is being executed.                                                                               |
      |                       |                       | -  **Completed**: The task is successfully executed.                                                                      |
      |                       |                       | -  **Failed**: The task fails to be executed.                                                                             |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | created               | String                | Indicates the creation time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                         |
      |                       |                       |                                                                                                                           |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | process               | String                | Indicates the task execution progress.                                                                                    |
      |                       |                       |                                                                                                                           |
      |                       |                       | .. note::                                                                                                                 |
      |                       |                       |                                                                                                                           |
      |                       |                       |    The execution progress (such as 60%) is displayed only when the task is being executed. Otherwise, **""** is returned. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | instance              | Object                | Indicates information of the DB instance on which the task is executed.                                                   |
      |                       |                       |                                                                                                                           |
      |                       |                       | For details, see :ref:`Table 4 <rds_08_0002__table4062895917262>`.                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | task_detail           | Object                | The displayed information varies depending on the tasks.                                                                  |
      |                       |                       |                                                                                                                           |
      |                       |                       | For details, see the following:                                                                                           |
      |                       |                       |                                                                                                                           |
      |                       |                       | -  :ref:`Table 5 <rds_08_0002__table975183423611>`                                                                        |
      |                       |                       | -  :ref:`Table 6 <rds_08_0002__table1014617554138>`                                                                       |
      |                       |                       |                                                                                                                           |
      |                       |                       | .. note::                                                                                                                 |
      |                       |                       |                                                                                                                           |
      |                       |                       |    This field is not displayed for asynchronous tasks that do not contain the **task_detail** field.                      |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | fail_reason           | String                | Indicates the error information displayed when a task failed.                                                             |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+

   .. _rds_08_0002__table4062895917262:

   .. table:: **Table 4** instance field data structure description

      ==== ====== ===============================
      Name Type   Description
      ==== ====== ===============================
      id   String Indicates the DB instance ID.
      name String Indicates the DB instance name.
      ==== ====== ===============================

   .. _rds_08_0002__table975183423611:

   .. table:: **Table 5** task_detail field data structure description (restoring data to original, existing, or new DB instances, or restoring table-level data to a specified time point)

      +------------------+--------------+--------------------------------------------------------------------------------+
      | Name             | Type         | Description                                                                    |
      +==================+==============+================================================================================+
      | sourceInstanceId | String       | Indicates the ID of the original DB instance to which backup data is restored. |
      +------------------+--------------+--------------------------------------------------------------------------------+
      | targetInstanceId | String       | Indicates the ID of the target DB instance to which backup data is restored.   |
      +------------------+--------------+--------------------------------------------------------------------------------+
      | backupId         | String       | Indicates the backup file ID.                                                  |
      +------------------+--------------+--------------------------------------------------------------------------------+
      | restoreTime      | String       | Indicates the time point to which table-level data is restored.                |
      +------------------+--------------+--------------------------------------------------------------------------------+
      | type             | String       | Indicates the task type.                                                       |
      +------------------+--------------+--------------------------------------------------------------------------------+
      | dbNames          | List<String> | Indicates the database name.                                                   |
      +------------------+--------------+--------------------------------------------------------------------------------+

   .. _rds_08_0002__table1014617554138:

   .. table:: **Table 6** task_detail field data structure description (creating automated or manual backups)

      =========== ====== ====================================================
      Name        Type   Description
      =========== ====== ====================================================
      instanceId  String Indicates the ID of the DB instance to be backed up.
      name        String Indicates the task name.
      description String Indicates the task description.
      dbNames     String Indicates the name of the data to be backed up.
      =========== ====== ====================================================

   .. note::

      In the response example, some returned task details are used as examples.

-  Example normal response

   Creating automated or manual backups:

   .. code-block:: text

      {
        "jobs": [
                  {
                      "id": "aa4e3386-af27-436e-99f5-7cfefa21c37a",
                      "name": "BackupDbSqlserverInInstance",
                      "status": "Completed",
                      "created": "2020-07-20T16:10:07+0000",
                      "ended": "2020-07-20T16:14:39+0000",
                      "process": "",
                      "instance": {
                          "id": "9a09052dfa824caea36f583bc3e5684ein04",
                          "name": "rds-8d43-0004"
                      },
                      "task_detail": "{\"instanceId\":\"9a09052dfa824caea36f583bc3e5684ein04\",\"name\":\"sqlserver-rds-8d43-0004-20200719161130675\"}"
                  }
                ],
        "count":1
      }

   Restoring data to original, existing, or new DB instances, or restoring table-level data to a specified time point:

   .. code-block:: text

      {
        "jobs": [
                  {
                      "id": "11bef2cb-2924-4727-a9c2-b6fec61fc03a",
                      "name": "SingleDbRestoreSqlserverInInstance",
                      "status": "Failed",
                      "created": "2020-07-21T01:38:00+0000",
                      "ended": "2020-07-21T01:39:59+0000",
                      "process": "",
                      "instance": {
                          "id": "9a09052dfa824caea36f583bc3e5684ein04",
                          "name": "rds-8d43-0004"
                      },
                      "task_detail": "{\"backupId\":\"83c76e6852c145779dc153d8299ee0e1br04\",\"dbNames\":\"backeeeeee\",\"sourceInstanceId\":\"9a09052dfa824caea36f583bc3e5684ein04\",\"targetInstanceId\":\"9a09052dfa824caea36f583bc3e5684ein04\"}"
                  }
                ],
        "count":1
      }

   Other task types:

   .. code-block:: text

      {
          "jobs":[
              {
                  "id":"11bef2cb-2924-4727-a9c2-b6fec61fc03a",
                  "name":"SingleDbRestoreSqlserverInInstance",
                  "status":"Complete",
                  "created":"2020-07-21T01:38:00+0000",
                  "ended":"2020-07-21T01:39:59+0000",
                  "process":"",
                  "instance":{
                      "id":"9a09052dfa824caea36f583bc3e5684ein04",
                      "name":"rds-8d43-0004"
                  }
          ],
          "count":1
      }

   Task being executed:

   .. code-block:: text

      {
          "jobs":[
              {
                  "id": "32291a2e-882b-4266-b7c0-89dae34d2a9d",
                  "name": "CreateSqlserverSingleHAInstance",
                  "status": "Running",
                  "created": "2020-07-14T15:02:29+0000",
                  "ended": "2020-07-14T15:16:18+0000",
                  "process": "50",
                  "instance": {
                      "id": "9a09052dfa824caea36f583bc3e5684ein04",
                      "name": "rds-8d43-0004"
                  }
              }
          ],
          "count":1
      }

   Task fails to be executed:

   .. code-block:: text

      {
          "jobs":[
              {
                  "id": "32291a2e-882b-4266-b7c0-89dae34d2a9d",
                  "name": "CreateSqlserverSingleHAInstance",
                  "status": "Failed",
                  "created": "2020-07-14T15:02:29+0000",
                  "ended": "2020-07-14T15:16:18+0000",
                  "process": "50",
                  "instance": {
                      "id": "9a09052dfa824caea36f583bc3e5684ein04",
                      "name": "rds-8d43-0004"
                  }
              }
          ],
          "fail_reason": "createVM failed.",
          "count":1
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
