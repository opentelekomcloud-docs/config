:original_name: rms_04_0200.html

.. _rms_04_0200:

Configuring the Resource Recorder
=================================

Scenarios
---------

You must enable the resource recorder for Config to track changes to your resource configurations.

You can modify or disable the resource recorder at any time.

This section includes the following content:

-  :ref:`Enabling the Resource Recorder <rms_04_0200__en-us_topic_0285045108_section27741923141316>`
-  :ref:`Modifying the Resource Recorder <rms_04_0200__section19816174054918>`
-  :ref:`Disabling the Resource Recorder <rms_04_0200__section189334613020>`
-  :ref:`Cross-Account Authorization <rms_04_0200__section95911732882>`
-  :ref:`Storing Resource Change Notifications and Resource Snapshots to an Encrypted OBS Bucket <rms_04_0200__section1414618337911>`

.. _rms_04_0200__en-us_topic_0285045108_section27741923141316:

Enabling the Resource Recorder
------------------------------

If you have enabled the resource recorder and specified an OBS bucket and an SMN topic when you configure the resource recorder, Config will notify you if there is a change (creation, modification, deletion, relationship change) to the resources within the monitoring scope and periodically store your notifications and resource snapshots.

#. Log in to the management console.

#. Click |image1| in the upper left corner. Under **Management & Deployment**, click **Config**.

#. In the navigation pane on the left, choose **Resource Recorder**.

#. Toggle on the resource recorder. In the dialog box, click **Yes**.


   .. figure:: /_static/images/en-us_image_0000001925023920.png
      :alt: **Figure 1** Enabling the resource recorder

      **Figure 1** Enabling the resource recorder

#. Select the monitoring scope.

   By default, all resources supported by Config will be recorded by the resource recorder. You can specify a resource scope for the resource recorder.


   .. figure:: /_static/images/en-us_image_0000001952303569.png
      :alt: **Figure 2** Specifying the monitoring scope

      **Figure 2** Specifying the monitoring scope

#. .. _rms_04_0200__li1379015271396:

   Specify an OBS bucket.

   Specify an OBS bucket to store notifications of resource changes and resource snapshots.

   To enable the resource recorder, you must configure either an SMN topic or an OBS bucket.

   -  **Select an OBS bucket from the current account**:

      Select **Your bucket** and then select a bucket from the drop-down list to store resource change notifications and resource snapshots. If you need to store the notifications and snapshots to a specific folder in the OBS bucket, enter the folder name after you select a bucket. If there are no OBS buckets in the current account, create one first. For details, see `Creating a Bucket <https://docs.otc.t-systems.com/object-storage-service/umn/obs_console_operation_guide/managing_buckets/creating_a_bucket.html>`__.

   -  **Select an OBS bucket from another account**:

      Select **Other users' bucket** and then configure **Region ID** and **Bucket Name**. If you need to store the notifications and snapshots to a specific folder in the OBS bucket, enter the folder name after you select a bucket. If you select a bucket from another account, you need required permissions granted by the account. For details, see :ref:`Cross-Account Authorization <rms_04_0200__section95911732882>`.

   .. note::

      After you specify an OBS bucket from the current or another account, Config will write an empty file named **ConfigWritabilityCheckFile** to the OBS bucket to verify whether resources can be written to the OBS bucket. If an error is reported, you can resolve related issues based on :ref:`Why Is an Error Reported When Data Is Dumped to the OBS Bucket After the Resource Recorder Is Enabled? <rms_08_0100__section1356812297234>`.


   .. figure:: /_static/images/en-us_image_0000001952304017.png
      :alt: **Figure 3** Configuring an OBS bucket

      **Figure 3** Configuring an OBS bucket

#. .. _rms_04_0200__li9992111220134:

   (Optional) Configure an SMN topic.

   Toggle on **Topic**, then select a region and an SMN topic for receiving notifications of resource changes.

   -  **Select a topic from the current account**:

      Select **Your topic**, then select a region and an SMN topic. If there are no SMN topics available, create one first. For details, see `Creating a Topic <https://docs.otc.t-systems.com/simple-message-notification/umn/topic_management/creating_a_topic.html>`__.

   -  **Select a topic from another account**:

      Select Topic under other account, then enter a topic URN. For more details about topic URN, see `Concepts <https://docs.otc.t-systems.com/simple-message-notification/umn/overview/concepts.html#urn>`__ If you select a topic from another account, you need required permissions granted by the account. For details, see :ref:`Cross-Account Authorization <rms_04_0200__section95911732882>`.

   .. note::

      To send notifications with an SMN topic, you not only need to create the topic, but also need to `add subscriptions <https://docs.otc.t-systems.com/simple-message-notification/umn/subscription_management/adding_a_subscription.html>`__ and `request subscription confirmations <https://docs.otc.t-systems.com/simple-message-notification/umn/subscription_management/requesting_subscription_confirmation.html>`__.


   .. figure:: /_static/images/en-us_image_0000001924866316.png
      :alt: **Figure 4** Configuring an SMN topic

      **Figure 4** Configuring an SMN topic

#. Grant permissions.

   -  **Quick granting**: This option will automatically create an agency named **rms_tracker_agency** to grant the required permissions for the resource recorder to work properly. The agency contains permissions for writing data into an OBS bucket. The agency created by **quick granting** doesn't contain KMS permissions, and the resource recorder is unable to store resource change notifications and snapshots to an OBS bucket that is encrypted using KMS. If you need to use an encrypted bucket, you can add the **KMS Administrator** permission to the agency or use custom authorization. For details, see :ref:`Storing Resource Change Notifications and Resource Snapshots to an Encrypted OBS Bucket <rms_04_0200__section1414618337911>`.

      For details about how to add permissions in an agency, see `Deleting or Modifying Agencies <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/agencies/deleting_or_modifying_agencies.html>`__.

   -  **Custom granting**: You can create an agency using IAM to customize authorization for Config. The agency must include either the permissions for sending notifications using an SMN topic or the permissions for writing data into an OBS bucket. To store resource changes and snapshots to an OBS bucket that is encrypted using KMS, you need the **KMS Administrator** permission. For details, see :ref:`Storing Resource Change Notifications and Resource Snapshots to an Encrypted OBS Bucket <rms_04_0200__section1414618337911>`. For details about how to create an agency, see `Cloud Service Agency <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/agencies/cloud_service_delegation.html>`__.


      .. figure:: /_static/images/en-us_image_0000001952145493.png
         :alt: **Figure 5** Grant Permissions

         **Figure 5** Grant Permissions

#. Click **Save**.

#. In the displayed dialog box, click **Yes**.

.. _rms_04_0200__section19816174054918:

Modifying the Resource Recorder
-------------------------------

You can modify the resource recorder at any time.

#. In the navigation pane on the left, choose **Resource Recorder**.

#. Click **Modify Resource Recorder**.


   .. figure:: /_static/images/en-us_image_0000001952305721.png
      :alt: **Figure 6** Modify Resource Recorder

      **Figure 6** Modify Resource Recorder

#. Modify configurations.

#. Click **Save**.

#. In the displayed dialog box, click **Yes**.

.. _rms_04_0200__section189334613020:

Disabling the Resource Recorder
-------------------------------

You can disable the resource recorder at any time.

#. In the navigation pane on the left, choose **Resource Recorder**.

#. Toggle off the resource recorder.

#. In the displayed dialog box, click **OK**.


   .. figure:: /_static/images/en-us_image_0000001924867128.png
      :alt: **Figure 7** Disabling the resource recorder

      **Figure 7** Disabling the resource recorder

.. _rms_04_0200__section95911732882:

Cross-Account Authorization
---------------------------

-  **Granting SMN topic permissions to another account**

   #. Log in to the management console with the authorizing account and go to the SMN console.
   #. Attach related SMN permissions to target accounts based on `Configuring Topic Policies <https://docs.otc.t-systems.com/simple-message-notification/umn/topic_management/configuring_topic_policies/index.html>`__.

-  **Granting OBS bucket permissions to another account**

   #. Log in to the management console with the authorizing account and go to the OBS console.

   #. Grant related OBS permissions to target accounts based on `Configuring a Custom Bucket Policy (Coding Mode) <https://docs.otc.t-systems.com/object-storage-service/umn/obs_console_operation_guide/permissions_control/configuring_a_bucket_policy/configuring_a_custom_bucket_policy_coding_mode.html>`__.

      The following is an example of a bucket policy. The policy allows the authorized account to store data into a specific object or folder in an OBS bucket. You need to configure the following parameters in a bucket policy:

      -  ${account_id}: The ID of the authorized account.
      -  ${agency_name}: Agency name. If you choose **Quick granting**, this parameter will be set to **rms_tracker_agency**.
      -  ${bucket_name}: The name of an OBS bucket.
      -  ${folder_name}: The name of a folder in an OBS bucket. If you do not need to specify a folder or object in an OBS bucket, you do not need to configure **/${folder_name}**.

      .. code-block::

         {
           "Statement": [
             {
               "Sid": "org-bucket-policy",
               "Effect": "Allow",
               "Principal": {
                 "ID": [
                   "domain/${account_id}:agency/${agency_name}"
                 ]
               },
               "Action": [
                 "PutObject"
               ],
               "Resource": [
                 "${bucket_name}/${folder_name}/RMSLogs/*/Snapshot/*",
                 "${bucket_name}/${folder_name}/RMSLogs/*/Notification/*"
               ]
             }
           ]
         }

.. _rms_04_0200__section1414618337911:

Storing Resource Change Notifications and Resource Snapshots to an Encrypted OBS Bucket
---------------------------------------------------------------------------------------

-  **Using an OBS bucket that is encrypted with a default key of SSE-KMS**

   If you need to store resource change notifications and snapshots to an OBS bucket encrypted using a default key of SSE-KMS, you need to add the **KMS Administrator** permission to the agency assigned to the resource recorder.

-  **Using an OBS bucket that is encrypted with a custom key of SSE-KMS**

   If you need to store resource change notifications and snapshots to an OBS bucket that is encrypted using a custom key of SSE-KMS, you need to add the **KMS Administrator** permission to the agency assigned to the resource recorder.

   If you need to store resource change notifications and snapshots to an OBS bucket that is from another account, and that is encrypted using a custom key of SSE-KMS, you need to add the **KMS Administrator** permission to the agency assigned to the resource recorder, and set the cross-account permission for the key at the same time. The procedure is as follows:

   #. Log in to the management console and go to the **Key Management Service** console.
   #. In the **Custom Keys** tab, click the alias of a target key to go to its details page and create a grant on it.
   #. Grant the account the permission for using the key based on `Creating a Grant <https://docs.otc.t-systems.com/key-management-service/umn/user_guide/key_management/managing_a_grant/creating_a_grant.html>`__.

      -  Enter the ID of the account to be authorized for **Grantee**.
      -  Select **Create Data Key**, **Describe Key**, and **Decrypt Data Key** for **Granted Operations**.

.. |image1| image:: /_static/images/en-us_image_0000001711484518.png
