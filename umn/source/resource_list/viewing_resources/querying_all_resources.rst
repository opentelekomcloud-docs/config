:original_name: rms_03_0101.html

.. _rms_03_0101:

Querying All Resources
======================

Scenarios
---------

On the **Resource List** page, you can view all resources in the current account.

.. important::

   There is a delay in synchronizing resource data to Config, so if there is a resource change, the change may not be updated in the resource list immediately. If the resource recorder is enabled, Config will update resource changes within 24 hours.

   To use the resource list, you must enable the resource recorder. If no resources are displayed on the resource list page, check if the resource recorder is enabled, if the resource type is within the configured monitoring scope, or if the service or resource is supported by Config. For services and resources supported by Config, see :ref:`Supported Resources <rms_01_0017>`. For details about how to configure the resource recorder, see :ref:`Configuring the Resource Recorder <rms_04_0200>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the page. Under **Management & Deployment**, select **Config**.

   By default, the **Resource List** displays the resources that you have and are within the monitoring scope of the resource recorder.


   .. figure:: /_static/images/en-us_image_0000001951956737.png
      :alt: **Figure 1** Resource List

      **Figure 1** Resource List

#. Disable **Only display cloud services and regions that contain resources** and then click **More** to view all services that are supported by Config.


   .. figure:: /_static/images/en-us_image_0000001951957393.png
      :alt: **Figure 2** Viewing all supported services

      **Figure 2** Viewing all supported services

#. To view all supported services and regions, click **Supported Services and Regions**.

.. |image1| image:: /_static/images/en-us_image_0000001501756588.png
