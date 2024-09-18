:original_name: rms_05_0100.html

.. _rms_05_0100:

Adding a Rule with a Predefined Policy
======================================

Scenarios
---------

You can create a rule to evaluate your resource compliance. When you create a rule, you can select a built-in policy or custom policy, specify a monitoring scope, and specify the trigger type. Evaluation results are provided for you to check compliance data.

This section describes how to add predefined rules.

Constraints and Limitations
---------------------------

-  You can add up to 500 rules in an account.

.. important::

   To evaluate resources with rules, you need to enable the resource recorder. Resource evaluation is subject to the following rules:

   -  If the resource recorder is disabled, no resources will be available for evaluation. You can still view historical evaluation results.
   -  If the resource recorder is enabled and a monitoring scope is configured, only resources within the monitoring scope can be evaluated.

   For details about how to enable and configure the resource recorder, see :ref:`Configuring the Resource Recorder <rms_04_0200>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner. Under **Management & Deployment**, click **Config**.

#. In the navigation pane on the left, choose **Resource Compliance**.

#. In the **Rules** tab, click **Add Rule**.


   .. figure:: /_static/images/en-us_image_0000001924293592.png
      :alt: **Figure 1** Adding a rule

      **Figure 1** Adding a rule

#. Configure basic details, and click **Next**.


   .. figure:: /_static/images/en-us_image_0000001924867752.png
      :alt: **Figure 2** Basic Configurations

      **Figure 2** Basic Configurations

   .. table:: **Table 1** Parameters of basic configurations

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                        |
      +===================================+====================================================================================================================================================================+
      | Policy Type                       | Select **Built-in policy**.                                                                                                                                        |
      |                                   |                                                                                                                                                                    |
      |                                   | Built-in policies are provided by Config. You can select a built-in policy to quickly add a rule. You can also search for a built-in policy by policy name or tag. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rule Name                         | By default, the rule name is consistent with the predefined policy name. Rule names must be unique.                                                                |
      |                                   |                                                                                                                                                                    |
      |                                   | A rule name can contain digits, letters, underscores (_), and hyphens (-) and cannot exceed 64 characters.                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | By default, the rule description is the same as the selected predefined policy description. You can also customize the rule description.                           |
      |                                   |                                                                                                                                                                    |
      |                                   | A rule description can contain any types of characters and cannot exceed 512 characters.                                                                           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. On the displayed **Configure Rule Parameters** page, configure required parameters and click **Next**.


   .. figure:: /_static/images/en-us_image_0000001952307129.png
      :alt: **Figure 3** Configure Rule Parameters

      **Figure 3** Configure Rule Parameters

   .. table:: **Table 2** Parameter descriptions

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================+
      | Trigger Type                      | Specifies the conditions under which rules are triggered.                                                                                                               |
      |                                   |                                                                                                                                                                         |
      |                                   | Possible values are:                                                                                                                                                    |
      |                                   |                                                                                                                                                                         |
      |                                   | -  **Configuration change**: The rule is triggered when a specific cloud resource is changed.                                                                           |
      |                                   | -  **Periodic execution**: The rule is triggered at a specific frequency.                                                                                               |
      |                                   |                                                                                                                                                                         |
      |                                   |    .. note::                                                                                                                                                            |
      |                                   |                                                                                                                                                                         |
      |                                   |       You cannot modify the **Trigger Type** of predefined policies. The **Trigger Type** varies depending on different predefined policies.                            |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Filter Type                       | Specifies the resources to be evaluated.                                                                                                                                |
      |                                   |                                                                                                                                                                         |
      |                                   | Possible types are:                                                                                                                                                     |
      |                                   |                                                                                                                                                                         |
      |                                   | -  **Specific resources**: Resources of a specific type will be evaluated.                                                                                              |
      |                                   | -  **All resources**: All resources from your account will be evaluated.                                                                                                |
      |                                   |                                                                                                                                                                         |
      |                                   | This parameter is mandatory only when **Trigger Type** is set to **Configuration change**.                                                                              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource Scope                    | If you set **Filter Type** to **Specific resources**, you need to specify a resource scope.                                                                             |
      |                                   |                                                                                                                                                                         |
      |                                   | -  **Service**: The service that the resource belongs to.                                                                                                               |
      |                                   | -  **Resource type**: The resource type                                                                                                                                 |
      |                                   | -  **Region**: The region where the resource resides.                                                                                                                   |
      |                                   |                                                                                                                                                                         |
      |                                   | You only need to configure this parameter when **Trigger Type** is set to **Configuration change** and **Filter Type** is set to **Specific resources**.                |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | (Optional) Filter Scope           | After you enable **Filter Scope**, you can filter resources by resource ID or tag.                                                                                      |
      |                                   |                                                                                                                                                                         |
      |                                   | You can specify a specific resource for compliance evaluation.                                                                                                          |
      |                                   |                                                                                                                                                                         |
      |                                   | This parameter is optional for a rule whose trigger type is configuration change.                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Execute Every                     | Indicates how often a rule is triggered.                                                                                                                                |
      |                                   |                                                                                                                                                                         |
      |                                   | Available options: 1 hour, 3 hours, 6 hours, 12 hours, 24 hours.                                                                                                        |
      |                                   |                                                                                                                                                                         |
      |                                   | This parameter is mandatory only when **Trigger Type** is set to **Periodic execution**.                                                                                |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Configure Rule Parameters         | Parameters of a built-in policy.                                                                                                                                        |
      |                                   |                                                                                                                                                                         |
      |                                   | For example, if you select the **required-tag-check** policy, you need to specify a tag, so that resources that do not have the tag will be determined as noncompliant. |
      |                                   |                                                                                                                                                                         |
      |                                   | Some default policies, such as **volumes-encrypted-check**, do not require **Configure Rule Parameters**.                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. On the **Confirm** page displayed, confirm the rule information and click **Submit**.


   .. figure:: /_static/images/en-us_image_0000001925027932.png
      :alt: **Figure 4** Confirming rule configurations

      **Figure 4** Confirming rule configurations

   .. note::

      After you add a rule, the first evaluation is automatically triggered immediately.

.. |image1| image:: /_static/images/en-us_image_0000001711484518.png
