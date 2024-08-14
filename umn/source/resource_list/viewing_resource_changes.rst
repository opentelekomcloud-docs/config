:original_name: rms_03_0300.html

.. _rms_03_0300:

Viewing Resource Changes
========================

Prerequisites
-------------

Resource changes that are reported to Config are recorded only after the resource recorder is enabled. For details about the resource recorder, see :ref:`Resource Recorder <rms_04_0000>`.

Scenarios
---------

You can view resource changes over a time period. A record will be added to the resource timeline when the related service reports a resource attribute or relationship change to Config and the record will be retained for seven years by default.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner. Under **Management & Deployment**, click **Config**.

#. On the **Resource List** page, click the name of a target resource.

#. Choose the **Resource Timeline** tab to view the resource changes.

#. In the upper right corner of the **Resource Timeline** tab, set a time range to filter records.

   By default, resource changes of the latest three months are displayed.

   You can also click **View JSON File** to view the resource attributes reported to Config.


   .. figure:: /_static/images/en-us_image_0000001925023720.png
      :alt: **Figure 1** Resource timeline

      **Figure 1** Resource timeline

.. |image1| image:: /_static/images/en-us_image_0000001711484518.png
