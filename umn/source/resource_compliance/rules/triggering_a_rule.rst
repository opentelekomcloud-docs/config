:original_name: rms_05_0200.html

.. _rms_05_0200:

Triggering a Rule
=================

Scenarios
---------

Rules can be triggered automatically or manually.

-  **Automatic**

   -  A rule will be automatically triggered after it is created.
   -  A rule will be automatically triggered after it is updated.
   -  A rule will be automatically triggered after it is enabled.
   -  If the **Trigger type** is set to **Configuration change** for a rule, the rule will be automatically triggered when there is a change to the resources within the monitoring scope.
   -  If the **Trigger Type** to **Periodic execution** for a rule, the rule will be automatically triggered at the configured frequency.

-  **Manual**

   You can manually initiate rule evaluation at any time. For details, see :ref:`Procedure <rms_05_0200__section176905161418>`.

Constraints and Limitations
---------------------------

-  You can add up to 500 rules in an account.

.. important::

   To evaluate resources with rules, you need to enable the resource recorder. Resource evaluation is subject to the following rules:

   -  If the resource recorder is disabled, no resources will be available for evaluation. You can still view historical evaluation results.
   -  If the resource recorder is enabled and a monitoring scope is configured, only resources within the monitoring scope can be evaluated.

   For details about how to enable and configure the resource recorder, see :ref:`Configuring the Resource Recorder <rms_04_0200>`.

.. _rms_05_0200__section176905161418:

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner. Under **Management & Deployment**, click **Config**.

#. In the navigation pane on the left, choose **Resource Compliance**.

#. Locate a target rule and click **Evaluate** in the **Operation** column.

   Alternatively, you can click **Evaluate** in the upper right corner of the rule details page.

#. In the displayed dialog box, click **OK**.


   .. figure:: /_static/images/en-us_image_0000001952149149.png
      :alt: **Figure 1** Manually triggering a rule

      **Figure 1** Manually triggering a rule

.. |image1| image:: /_static/images/en-us_image_0000001711484518.png
