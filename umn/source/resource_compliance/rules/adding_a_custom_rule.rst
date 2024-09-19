:original_name: rms_05_0404.html

.. _rms_05_0404:

Adding a Custom Rule
====================

Scenario
--------

You can create custom rules to supplement predefined rules.

.. note::

   Currently, only the **eu-de** region supports FunctionGraph, so you can only create custom policies for the **eu-de** region.

To create a custom rule, you need to use FunctionGraph functions. Each rule is associated with a Function Graph function. Config reports events to the function. The function collects rule parameters and resource attributes from the events; evaluates whether your resources comply with the rule; and returns evaluation results using Open APIs of Config. Config sends events based on the trigger type (configuration changes or periodic) of a rule. For details about how to use FunctionGraph, see `FunctionGraph User Guide <https://docs.otc.t-systems.com/function-graph/umn/before_you_start/use_of_functiongraph.html>`__.

This section describes how to create a custom rule by performing the following two procedures:

#. :ref:`Creating a Function with FunctionGraph <rms_05_0404__section14111111694611>`
#. :ref:`Adding a Custom Rule <rms_05_0404__section211214354715>`

Constraints and Limitations
---------------------------

-  You can add up to 500 rules in an account.

.. important::

   To evaluate resources with rules, you need to enable the resource recorder. Resource evaluation is subject to the following rules:

   -  If the resource recorder is disabled, no resources will be available for evaluation. You can still view historical evaluation results.
   -  If the resource recorder is enabled and a monitoring scope is configured, only resources within the monitoring scope can be evaluated.

   For details about how to enable and configure the resource recorder, see :ref:`Configuring the Resource Recorder <rms_04_0200>`.

.. _rms_05_0404__section14111111694611:

Creating a Function with FunctionGraph
--------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the page. In the service list that is displayed, under **Compute**, select **FunctionGraph**.

#. In the navigation pane on the left, choose **Functions** > **Function List**.

#. In the upper right corner, click **Create Function**. The **Create from scratch** tab is displayed by default.

#. Set **Function Type** to **Event Function** and configure the required IAM agency. The agency grants the function required permissions and must include the **rms:policyStates:update** permission.

#. Click **Create Function**.

#. In the code box, enter a function and click **Deploy**.

   For details about example code, see :ref:`Example Functions (Python) <rms_05_0504>`.

#. Click **Configurations**, modify **Execution Timeout (s)** and **Memory (MB)** in the **Basic Settings** area as required. Configure **Concurrency**.

#. Click **Save**.

   For more details, see `Creating an Event Function <https://docs.otc.t-systems.com/function-graph/umn/building_functions/creating_a_function_from_scratch/creating_an_event_function.html>`__.

.. _rms_05_0404__section211214354715:


Adding a Custom Rule
--------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner. Under **Management & Deployment**, click **Config**.

#. In the navigation pane on the left, choose **Resource Compliance**.

#. Click **Add Rule** in the middle of the page.

#. Set **Policy Type** to **Custom policy**, complete related configurations and authorization, and click **Next**.

   .. table:: **Table 1** Parameters of basic configurations

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================================================================================================================================+
      | Policy Type                       | Select **Custom policy**.                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   | You can use custom policies to create rules.                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rule Name                         | The name of the rule. A rule name must be unique.                                                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   | A rule name can contain digits, letters, underscores (_), and hyphens (-) and cannot exceed 64 characters.                                                                                                                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A rule description can contain any types of characters and cannot exceed 512 characters.                                                                                                                                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | FunctionGraph Function            | The URN of the function.                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   | For details about how to create a FunctionGraph function, see :ref:`Creating a Function with FunctionGraph <rms_05_0404__section14111111694611>`.                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   |    You can use either of the following methods to obtain the URN of a function:                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   |    -  On the FunctionGraph console, choose **Functions** > **Function List** in the navigation pane on the left and click **Copy URN** in the **Operation** column for the target function.                                                                                                                                   |
      |                                   |    -  Return to the FunctionGraph console, choose **Functions** > **Function List** in the navigation pane on the left, click the name of the target function, then obtain the function URN in the **Function Info** area.                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Grant Permissions                 | This agency grants Config the read-only and call permissions of FunctionGraph. These permissions allow you to customize rules to query and send events to FunctionGraph functions.                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   |    -  **Quick granting**: Quickly grants you permissions of the **rms_custom_policy_agency** agency. The permissions ensure proper functioning of a custom rule and allow a custom rule to obtain and asynchronously execute a FunctionGraph function.                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   |    -  **Custom granting**: Allows you to create an agency using Identity and Access Management (IAM) and assign permissions. The agency must contain the permissions for calling and asynchronously executing FunctionGraph functions. The authorization object must be Config. The following shows an authorization example. |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   |       .. code-block::                                                                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   |            {                                                                                                                                                                                                                                                                                                                  |
      |                                   |                "Version": "1.1",                                                                                                                                                                                                                                                                                              |
      |                                   |                "Statement": [                                                                                                                                                                                                                                                                                                 |
      |                                   |                    {                                                                                                                                                                                                                                                                                                          |
      |                                   |                        "Effect": "Allow",                                                                                                                                                                                                                                                                                     |
      |                                   |                        "Action": [                                                                                                                                                                                                                                                                                            |
      |                                   |                            "functiongraph:function:invokeAsync",                                                                                                                                                                                                                                                              |
      |                                   |                            "functiongraph:function:getConfig"                                                                                                                                                                                                                                                                 |
      |                                   |                        ]                                                                                                                                                                                                                                                                                                      |
      |                                   |                    }                                                                                                                                                                                                                                                                                                          |
      |                                   |                ]                                                                                                                                                                                                                                                                                                              |
      |                                   |            }                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                               |
      |                                   |       For details about how to create an agency, see `Cloud Service Delegation <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/agencies/cloud_service_delegation.html>`__.                                                                                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


   .. figure:: /_static/images/en-us_image_0000001925028472.png
      :alt: **Figure 1** Basic Configurations

      **Figure 1** Basic Configurations

#. On the displayed **Configure Rule Parameters** page, configure required parameters and click **Next**.

   .. table:: **Table 2** Rule parameters

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                         |
      +===================================+=====================================================================================================================================================+
      | Trigger Type                      | The condition under which a rule will be triggered.                                                                                                 |
      |                                   |                                                                                                                                                     |
      |                                   | Trigger types are as follows:                                                                                                                       |
      |                                   |                                                                                                                                                     |
      |                                   | -  **Configuration change**: A rule is triggered when there is a change in resource configurations.                                                 |
      |                                   | -  **Periodic execution**: A rule is triggered at a specific frequency.                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Filter Type                       | The type of resources to be evaluated.                                                                                                              |
      |                                   |                                                                                                                                                     |
      |                                   | Filter types are as follows:                                                                                                                        |
      |                                   |                                                                                                                                                     |
      |                                   | -  **Specific resources**: Resources of a specific type.                                                                                            |
      |                                   | -  **All resources**: All resources from your account.                                                                                              |
      |                                   |                                                                                                                                                     |
      |                                   | This parameter is mandatory only when **Trigger Type** is set to **Configuration change**.                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource Scope                    | If you set **Filter Type** to **Specific resources**, you need to specify a resource scope.                                                         |
      |                                   |                                                                                                                                                     |
      |                                   | -  **Service**: The service that the resource belongs to.                                                                                           |
      |                                   | -  **Resource type**: The resource type                                                                                                             |
      |                                   | -  **Region**: The region where the resource resides.                                                                                               |
      |                                   |                                                                                                                                                     |
      |                                   | This parameter is mandatory only when **Trigger Type** is set to **Configuration change** and the **Filter Type** is set to **Specific resources**. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | (Optional) Filter Scope           | After you enable **Filter Scope**, you can filter resources by resource ID or tag.                                                                  |
      |                                   |                                                                                                                                                     |
      |                                   | You can specify a specific resource for compliance evaluation.                                                                                      |
      |                                   |                                                                                                                                                     |
      |                                   | This parameter is optional for a rule whose trigger type is configuration change.                                                                   |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Execute Every                     | How often a rule will be triggered.                                                                                                                 |
      |                                   |                                                                                                                                                     |
      |                                   | Available options: 1 hour, 3 hours, 6 hours, 12 hours, 24 hours.                                                                                    |
      |                                   |                                                                                                                                                     |
      |                                   | This parameter is mandatory only when **Trigger Type** is set to **Periodic execution**.                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Configure Rule Parameters         | You can set up to 10 rule parameters for a custom rule.                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

#. On the **Confirm** page, confirm the rule information and click **Submit**.

   .. note::

      After you add a rule, the first evaluation is automatically triggered immediately.

.. |image1| image:: /_static/images/en-us_image_0000002015407113.png
.. |image2| image:: /_static/images/en-us_image_0000001711484518.png
