:original_name: rms_04_0500.html

.. _rms_04_0500:

Storing Resource Change Notifications
=====================================

After you enable the resource recorder and specify an SMN topic and an OBS bucket, Config stores your resource change notifications to the OBS bucket every 6 hours. If no topics are available, you need to create a topic, add subscription endpoints, and request subscription confirmations for the topic.

The path of in an OBS bucket where the resource recorder stores your resource change notifications takes the form of **${bucket_name}/${bucket_prefix}/RMSLogs/${account_id}/Notification/${year}/${month}/\*** The fields before each slash in the path indicate different layers of folders, and **\*** indicates the name of a file. You can go to the **Objects** page on the OBS console and find your resource change notification files based on the paths.

The name of the file for storing your resource change notifications consists of the account ID, storage file type, ID of the region where the OBS bucket resides, service type, resource type, and storage duration. Each file contains change notifications of only one type of resource. **.json.gz** indicates that the file is stored as a JSON package.

The following shows an example name of a resource change notification file: 0926901ef980f2150fbdc001fdd23e80_Notification_eu-de_NotificationChunk_OBS_BUCKETS_2024-07-24T214735Z_2024-07-24T214759Z.json.gz

For more details, see `Searching for an Object or Folder <https://docs.otc.t-systems.com/object-storage-service/umn/obs_console_operation_guide/managing_objects/searching_for_an_object_or_folder.html>`__.

For details, see `Simple Message Notification User Guide <https://docs.otc.t-systems.com/simple-message-notification/umn/overview/simple_message_notification.html>`__.

For details about example code for storing resource change notifications, see :ref:`Storage Model of Resource Change Notifications <rms_06_0600>`.
