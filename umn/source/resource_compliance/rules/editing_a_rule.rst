:original_name: rms_05_0300.html

.. _rms_05_0300:

Editing a Rule
==============

Scenario
--------

You can modify, enable, disable, or delete a rule at any time.

You can perform these operations in the rule list or on the **Rules Details** page. This section describes how to modify, enable, disable, or delete a rule through the rule list.

-  :ref:`Disabling a Rule <rms_05_0300__section189571246164014>`
-  :ref:`Enabling a Rule <rms_05_0300__section171591054152418>`
-  :ref:`Modifying a Rule <rms_05_0300__section1495815469407>`
-  :ref:`Deleting a Rule <rms_05_0300__section8960746204018>`

.. _rms_05_0300__section189571246164014:

Disabling a Rule
----------------

#. Log in to the management console.

#. Click |image1| in the upper left corner. Under **Management & Deployment**, click **Config**.

#. In the navigation pane on the left, choose **Resource Compliance**.

#. On the **Rules** tab, locate a target rule and click **Disable** in the **Operation** column.

#. In the displayed dialog box, click **OK**.


   .. figure:: /_static/images/en-us_image_0000001952149449.png
      :alt: **Figure 1** Disabling a rule

      **Figure 1** Disabling a rule

.. _rms_05_0300__section171591054152418:

Enabling a Rule
---------------

#. Log in to the management console.

#. Click |image2| in the upper left corner. Under **Management & Deployment**, click **Config**.

#. In the navigation pane on the left, choose **Resource Compliance**.

#. On the **Rules** tab, locate a target rule and click **Enable** in the **Operation** column.

#. In the displayed dialog box, click **OK**.

   .. note::

      After a rule is enabled, it will be automatically triggered immediately.


   .. figure:: /_static/images/en-us_image_0000001925030152.png
      :alt: **Figure 2** Enabling a rule

      **Figure 2** Enabling a rule

.. _rms_05_0300__section1495815469407:

Modifying a Rule
----------------

#. Log in to the management console.

#. Click |image3| in the upper left corner. Under **Management & Deployment**, click **Config**.

#. In the navigation pane on the left, choose **Resource Compliance**.

#. On the **Rules** tab, locate a target rule and click **More** > **Modify** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000001924870980.png
      :alt: **Figure 3** Modifying a rule

      **Figure 3** Modifying a rule

#. On **Basic Configurations** page, modify the rule description and click **Next**.

#. On the **Configure Rule Parameters** page, configure required parameters and click **Next**.

   The configuration items that you can modify vary for different policies.

   -  **Filter Type**: Can be modified when **Trigger Type** is set to **Configuration change**
   -  **Resource Scope**: Can be modified when **Trigger Type** is set to **Configuration change**
   -  **Filter Scope**: Can be modified when **Trigger Type** is set to **Configuration change**.
   -  **Execute Every**: Can be modified when **Trigger Type** is set to **Periodic execution**.
   -  **Configure Rule Parameters**: For a rule created with a predefined policy, you can only modify the values of parameters for **Configure Rule Parameters**. For a custom rule, you can add, delete, and modify parameters.

#. Confirm the modifications and click **Submit.**

   .. note::

      After a rule is modified, it will be automatically triggered.

.. _rms_05_0300__section8960746204018:

Deleting a Rule
---------------

Before deleting a rule, you need to disable the rule.

#. Log in to the management console.

#. Click |image4| in the upper left corner. Under **Management & Deployment**, click **Config**.

#. In the navigation pane on the left, choose **Resource Compliance**.

#. On the **Rules** tab, locate a target rule and click **More** > **Delete** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000001952150149.png
      :alt: **Figure 4** Deleting a rule

      **Figure 4** Deleting a rule

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001711484518.png
.. |image2| image:: /_static/images/en-us_image_0000001711484518.png
.. |image3| image:: /_static/images/en-us_image_0000001711484518.png
.. |image4| image:: /_static/images/en-us_image_0000001711484518.png
