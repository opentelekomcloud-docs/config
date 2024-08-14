:original_name: rms_05_3000.html

.. _rms_05_3000:

Viewing a Rule
==============

Scenario
--------

After you add a rule, you can view all rules in the rule list and view evaluation results and configurations of a rule on the rule details page.

You can export all evaluation results. On the upper right corner of the rule details page, multiple buttons are provided for you to trigger, modify, enable, disable, or delete a rule.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner. Under **Management & Deployment**, click **Config**.

#. In the navigation pane on the left, choose **Resource Compliance**.

#. On the **Rules** tab, view rules, rule status, and evaluation results.

#. Click the name of the target rule to go to the **Rule Details** page.

   On the left of the **Basic Information** page, evaluation results are displayed, and on the right, rule details are displayed. Above the evaluation result list, you can filter evaluation results by resource name and ID. You can also export the list.


   .. figure:: /_static/images/en-us_image_0000001924869504.png
      :alt: **Figure 1** Rule Details

      **Figure 1** Rule Details

   .. note::

      A rule may be in one of the following statuses:

      -  **Enabled**: The rule is available.
      -  **Disabled**: The rule is disabled.
      -  **Evaluating**: The rule is evaluating resources.
      -  **Submitting**: The rule is submitting an evaluation task to the associated FunctionGraph function.

      During the evaluation, the rule is in the **Evaluating** state. After the evaluation is complete, the rule status changes to **Enabled**, and then, you can view the evaluation results.

.. |image1| image:: /_static/images/en-us_image_0000001711484518.png
