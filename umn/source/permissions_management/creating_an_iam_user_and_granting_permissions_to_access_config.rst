:original_name: rms_01_0022.html

.. _rms_01_0022:

Creating an IAM User and Granting Permissions to Access Config
==============================================================

You can use `Identity and Access Management (IAM) <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__ to implement fine-grained permissions control for your Config resources. With IAM, you can:

-  Create IAM users or user groups for personnel based on your enterprise's organizational structure. Each IAM user has their own identity credentials for accessing Config resources.
-  Grant users only the permissions required to perform a given task based on their job responsibilities.
-  Entrust an account or a cloud service to perform efficient O&M on your Config resources.

If your account meets your permissions requirements, you can skip this section.

:ref:`Figure 1 <rms_01_0022__fig33941114133916>` shows the process flow of granting Config permissions.

Prerequisites
-------------

Before granting permissions, learn about :ref:`permissions <rms_01_0600>` for Config. To grant permissions for other services, see `permissions <https://docs.otc.t-systems.com/identity-access-management/permissions/permissions.html>`__.

Process Flow
------------

.. _rms_01_0022__fig33941114133916:

.. figure:: /_static/images/en-us_image_0000001842296713.png
   :alt: **Figure 1** Process of granting Config permissions

   **Figure 1** Process of granting Config permissions

#. On the IAM console, `create a user group and assign permissions to it <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__ (**Config ReadOnlyAccess** as an example).

#. `Create an IAM user and add it to the created group <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__.

#. `Log in as the IAM user <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__ and verify permissions.

   In the authorized region, perform the following operations:

   -  Choose **Service List** > **Config**. In the navigation pane on the left, click **Resource Compliance**. On the displayed page, click **Add Rule** under the **Rules** tab. If a message appears indicating that you have insufficient permissions to perform the operation, the **Config ReadOnlyAccess** policy is in effect.
   -  Choose another service from **Service List**. If a message appears indicating that you have insufficient permissions to access the service, the **Config ReadOnlyAccess** policy is in effect.
   -  Choose **Service List** > **Config** and check if you can view queries in the **Advanced Queries** page. If yes, the **Config ReadOnlyAccess** policy is in effect.
