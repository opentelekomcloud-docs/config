:original_name: rms_06_0305.html

.. _rms_06_0305:

Notification Model of Resource Change Notification Storage
==========================================================


Notification Model of Resource Change Notification Storage
----------------------------------------------------------

.. table:: **Table 1** Parameters of the notification model of resource change notification storage

   +----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Type                  | Description                                                                                                                      |
   +============================+=======================+==================================================================================================================================+
   | notification_type          | String                | The type of a notification. For resource change notification storage, the notification type is **NotificationArchiveCompleted**. |
   +----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | notification_creation_time | String                | The time when the message was sent.                                                                                              |
   |                            |                       |                                                                                                                                  |
   |                            |                       | The notification creation time is a UTC time (such as 2018-11-14T08:59:14Z) that complies with ISO8601.                          |
   +----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | domain_id                  | String                | Account ID.                                                                                                                      |
   +----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | detail                     | Object                | Notification details.                                                                                                            |
   +----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **detail** parameters

   +-------------+--------+-----------------------------------------------------------------------------------+
   | Parameter   | Type   | Description                                                                       |
   +=============+========+===================================================================================+
   | region_id   | String | The ID of the region where resource change notifications are stored.              |
   +-------------+--------+-----------------------------------------------------------------------------------+
   | bucket_name | String | The name of the OBS bucket where resource change notifications are stored.        |
   +-------------+--------+-----------------------------------------------------------------------------------+
   | object_key  | String | The path of an object in an OBS bucket for storing resource change notifications. |
   +-------------+--------+-----------------------------------------------------------------------------------+

Notification Example of Resource Change Notification Storage
------------------------------------------------------------

.. code-block::

   {
       "detail": {
           "region_id": "eu-de",
           "bucket_name": "test",
           "object_key": "RMSLogs/059b5c937100d3e40ff0c00a7675a0a0/Notification/2020/12/10/NotificationChunk/059b5c937100d3e40ff0c00a7675a0a0_Notification_eu-de_NotificationChunk_VPC_VPCS_2020-12-10T024612Z_2020-12-10T050621Z.json.gz"
       },
       "notification_type": "NotificationArchiveCompleted",
       "notification_creation_time": "2020-12-10T05:09:28.002Z",
       "domain_id": "059b5c937100d3e40ff0c00a7675a0a0"
   }
