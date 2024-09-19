:original_name: rms_01_0023.html

.. _rms_01_0023:

Creating a Custom Policy
========================

You can use IAM to create custom policies to supplement system-defined policies of Config. For more details, see the section "Permissions Policies and Supported Actions" in *Config API Reference* or :ref:`Fine-Grained Permissions for Config <rms_01_0600__section1491005953113>`.

To create a custom policy, choose either visual editor or JSON.

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Create a JSON policy or edit an existing one.

For details, see `Creating a Custom Policy <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/permissions/creating_a_custom_policy.html>`__. The following lists an example of an Config custom policy.

Example Custom Policy
---------------------

-  Example 1: Grant permissions to add a rule

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "rms:policyAssignments:create"
                  ]
              }
          ]
      }

-  Example 2: Grant permission to deny a user to run an advanced query

   A policy with only "Deny" permissions must be used together with other policies. If the permissions granted to an IAM user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   Assume that you want to grant the permissions of the **Config FullAccess** policy to a user but do not want the user to have the permission to delete rules. You can create a custom policy that denies rule deletion, and then attach this policy together with the **Config FullAccess** policy to the user. As an explicit deny in any policy overrides any allows, the user can perform all operations on Config rules excepting deleting them.

   The following shows an example of a deny policy:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Deny",
                  "Action": [
                      "rms:policyAssignments:delete"
                  ]
              }
          ]
      }

-  Example 3: Create a custom policy containing multiple actions.

   A custom policy can contain the actions of one or multiple services that are of the same type (global or project-level).

   Example policy containing multiple actions:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "rms:policyAssignments:create",
                      "rms:policyAssignments:delete"
                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "tms:predefineTags:create",
                      "tms:predefineTags:delete"
                  ]
              }
          ]
      }
