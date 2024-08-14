:original_name: rms_04_0100.html

.. _rms_04_0100:

Overview
========

Introduction
------------

The resource recorder automatically detects and records changes made to your resources that are supported by Config.

To be specific, the resource recorder:

-  Notifies you using the specified SMN topic if your resources are created, modified, or deleted.
-  Notifies you using the specified SMN topic if there is a change to your resource relationships.
-  Stores notifications of your resource changes every 6 hours if you have configured an OBS bucket and an SMN topic.
-  Stores resource snapshots every 24 hours if you have configured an OBS bucket.

For details about resources supported by the resource recorder, see :ref:`Supported Resources <rms_01_0017>`.

Notes and Constraints
---------------------

-  When enabling and configuring the resource recorder, you must configure :ref:`Topic <rms_04_0200__li9992111220134>` or :ref:`Resource Dump <rms_04_0200__li1379015271396>`. To enable the resource recorder, you must configure either an SMN topic or an OBS bucket.
-  To receive notifications of resource changes with the configured SMN topic, you not only have to create the topic, but also add subscription endpoints and request subscription confirmations for the topic. For details, see `Creating a Topic <https://docs.otc.t-systems.com/simple-message-notification/umn/topic_management/creating_a_topic.html>`__, `Adding a Subscription <https://docs.otc.t-systems.com/simple-message-notification/umn/subscription_management/adding_a_subscription.html>`__, and `Requesting Subscription Confirmation <https://docs.otc.t-systems.com/simple-message-notification/umn/subscription_management/requesting_subscription_confirmation.html>`__.
-  The resource recorder only updates data for the resources within the monitoring scope.
-  The resource recorder retains your resource information for seven years (2,557 days).
-  There is a delay in synchronizing resource data to Config. The delay varies depending on services. If the resource recorder is enabled, Config will update related data for resources that are included in the monitoring scope within 24 hours. If the resource recorder is disabled, Config will not update resource data.

.. important::

   To get full functionality of Config, you need to enable the resource recorder. If the resource recorder is disabled, you may fail to update your resource data or accurately evaluate your resources with rules.
