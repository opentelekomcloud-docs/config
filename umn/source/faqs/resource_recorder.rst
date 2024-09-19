:original_name: rms_08_0100.html

.. _rms_08_0100:

Resource Recorder
=================

Are Resource Snapshots and Resource Change Notifications Stored into the Same OBS Bucket?
-----------------------------------------------------------------------------------------

Yes, they are stored into the same OBS bucket.

If you specified an OBS bucket and an SMN topic when you configured the resource recorder, resource snapshots and resource change notifications are periodically stored in the OBS bucket.

How Often Are Resource Snapshots and Resource Change Notifications Stored, Respectively?
----------------------------------------------------------------------------------------

After you enable the resource recorder and specify an SMN topic and an OBS bucket, Config will store your resource snapshots to the OBS bucket every 24 hours and your resource change notifications every 6 hours.

Do I Need to Configure Both Topic and Resource Dump When I Enable and Configure the Resource Recorder?
------------------------------------------------------------------------------------------------------

No. However, you need to configure either **Topic** or **Resource Dump**. To enable the resource recorder, you must configure either an SMN topic or an OBS bucket.

Why Are There No Notifications of Resource Changes Even When the Resource Recorder Has Been Enabled?
----------------------------------------------------------------------------------------------------

The possible causes are as follows:

-  You didn't specify an SMN topic when you configured the resource recorder. To receive resource change notifications, modify the resource recorder to configure an SMN topic.
-  You did not `add subscriptions <https://docs.otc.t-systems.com/simple-message-notification/umn/subscription_management/adding_a_subscription.html>`__ or `request subscription confirmations <https://docs.otc.t-systems.com/simple-message-notification/umn/subscription_management/requesting_subscription_confirmation.html>`__ for the specified SMN topic.
-  Resource changes were not reported to Config.
-  There was a delay in synchronizing or sending the notification.

Why Are Resource Change Notifications Not Stored into the Configured OBS Bucket?
--------------------------------------------------------------------------------

To store resource change notifications, you need to configure both an SMN topic and an OBS bucket.

To make an SMN topic effective, you not only need to create a topic, but add subscription endpoints and request subscription confirmation.

Why Do I Receive a Notification When I Did Nothing with a Resource?
-------------------------------------------------------------------

If you have specified an effective SMN topic when you enabled the resource recorder, Config will send notifications of resource changes that are resulted from both user operations and non-user operations. For more details, see :ref:`Notifications <rms_04_0300>`. You are advised to use HTTPS or FunctionGraph (functions) instead of SMS messages or emails to receive notifications from Config.

.. _rms_08_0100__section1077795954511:

How Can I Obtain Resource Attributes Reported to Config?
--------------------------------------------------------

You can obtain resource attributes reported to Config in either of the following ways:

-  Go to Config console and open the **Query Editor**. Resource attributes that are reported to Config are displayed on the left side of the **Query Editor**. The following procedure shows how to open the **Query Editor**.

   #. Log in to the management console.

   #. Click |image1| in the upper left corner of the page. In the service list that is displayed, under **Management & Deployment**, select **Config**.

   #. In the navigation pane on the left, choose **Advanced Queries**.

   #. On the **Default Queries** tab, click **Query** in the **Operation** column of any rows.


      .. figure:: /_static/images/en-us_image_0000002001635001.png
         :alt: **Figure 1** Using a query

         **Figure 1** Using a query

   #. View resource attributes on the left side of the **Query Editor**. You can also enter a resource type to search for resource attributes.


      .. figure:: /_static/images/en-us_image_0000001964993150.png
         :alt: **Figure 2** Viewing resource attributes

         **Figure 2** Viewing resource attributes

-  Alternatively, you can call the the querying schema API (GET /v1/resource-manager/domains/{domain_id}/schemas) to obtain resource attributes. In the response, the **type** field indicates the resource type, and the **schema** field indicates resource attributes that are reported to Config. For more details, see *Config API Reference*.

.. _rms_08_0100__section1356812297234:

Why Is an Error Reported When Data Is Dumped to the OBS Bucket After the Resource Recorder Is Enabled?
------------------------------------------------------------------------------------------------------

If the message "Failed to write the ConfigWritabilityCheckFile file to the OBS bucket because the OBS bucket or the IAM agency is invalid" is displayed, the possible reasons are as follows:

#. The IAM agency assigned to the resource recorder does not contain the permission, **obs:object:PutObject**.
#. If an OBS bucket from the current account was used, the reason may be that the bucket policy explicitly denies the **PutObject** action from the IAM agency. If an OBS bucket from another account was used, the reason may be that the bucket policy does not explicitly allow the **PutObject** action from the IAM agency. For more details, see :ref:`Cross-Account Authorization <rms_04_0200__section95911732882>` and `Effect <https://docs.otc.t-systems.com/object-storage-service/umn/obs_console_operation_guide/permissions_control/bucket_policy_parameters/effect.html>`__.
#. You used an encrypted OBS bucket, but the agency assigned to the resource recorder did not contain related KMS permissions. For more details, see :ref:`Storing Resource Change Notifications and Resource Snapshots to an Encrypted OBS Bucket <rms_04_0200__section1414618337911>`.

.. |image1| image:: /_static/images/en-us_image_0000001978727588.png
