:original_name: rms_08_0800.html

.. _rms_08_0800:

Resource List
=============

Why Can't I Delete Resources on the **Resource List** Page?
-----------------------------------------------------------

On the **Resource List** page, you can only view resources and export resource details. To delete a resource, you need to click **View Details** in the **Operation** column to go to the corresponding service page.


.. figure:: /_static/images/en-us_image_0000001952314057.png
   :alt: **Figure 1** Viewing resource details

   **Figure 1** Viewing resource details

Why Does Resource Information Remain Unchanged on the Resource List Page After a Change Has Been Made to My Resources?
----------------------------------------------------------------------------------------------------------------------

One possible reason is that there was a delay in synchronizing related resource information to Config.

Another reason may be the disabled resource recorder. If the resource recorder was disabled, Config would not update resource data. If the resource recorder is enabled, Config will update related data for resources that are included in the monitoring scope within 24 hours.

It may also be that the resource change was not reported to Config. The services are not supposed to report all resource data to Config, just some of it. For example, Document Database Service (DDS) is not supposed to report security groups to Config, and Config will not display security group data for DDS instances.
