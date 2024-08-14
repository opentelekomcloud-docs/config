:original_name: rms_06_0304.html

.. _rms_06_0304:

Resource Snapshot Storage Notification Model
============================================


Resource Snapshot Storage Notification Model
--------------------------------------------

.. table:: **Table 1** Parameters of the resource snapshot storage notification model

   +----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Type                  | Description                                                                                                                      |
   +============================+=======================+==================================================================================================================================+
   | notification_type          | String                | The type of a notification. For a resource snapshot storage notification, the notification type is **SnapshotArchiveCompleted**. |
   +----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | notification_creation_time | String                | The time when the message was sent.                                                                                              |
   |                            |                       |                                                                                                                                  |
   |                            |                       | The notification creation time is a UTC time (such as 2018-11-14T08:59:14Z) that complies with ISO8601.                          |
   +----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | domain_id                  | String                | Account ID.                                                                                                                      |
   +----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | detail                     | Object                | Notification details.                                                                                                            |
   +----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** detail

   +-------------+-----------------+-----------------------------------------------------------------+
   | Parameter   | Type            | Description                                                     |
   +=============+=================+=================================================================+
   | snapshot_id | String          | Resource snapshot ID.                                           |
   +-------------+-----------------+-----------------------------------------------------------------+
   | region_id   | String          | The ID of the region where resource snapshots reside.           |
   +-------------+-----------------+-----------------------------------------------------------------+
   | bucket_name | String          | The name of the OBS bucket where resource snapshots are stored. |
   +-------------+-----------------+-----------------------------------------------------------------+
   | object_keys | Array of String | Path of the OBS object where resource snapshots are stored.     |
   +-------------+-----------------+-----------------------------------------------------------------+

Notification Example of Resource Snapshot Storage
-------------------------------------------------

.. code-block::

   {
     "detail": {
       "snapshot_id": "474f85e6-72cd-442b-af4e-517120a5c669",
       "region_id": "eu-de",
       "bucket_name": "test",
       "object_keys": [
         "RMSLogs/059b5c937100d3e40ff0c00a7675a0a0/Snapshot/2020/8/11/059b5c937100d3e40ff0c00a7675a0a0_Snapshot_eu-de_ResourceSnapshot_2020-08-10T170901_474f85e6-72cd-442b-af4e-517120a5c669_part-1.json.gz"
       ]
     },
     "notification_type": "SnapshotArchiveCompleted",
     "notification_creation_time": "2020-08-10T17:09:27.314Z",
     "domain_id": "059b5c937100d3e40ff0c00a7675a0a0"
   }
