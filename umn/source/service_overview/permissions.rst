:original_name: rms_01_0600.html

.. _rms_01_0600:

Permissions
===========

If you need to assign different permissions to employees in your enterprise, Identity and Access Management (IAM) is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you flexibly manage resource access.

You can create users using IAM and grant users permissions to implement access control.

If your account does not need individual IAM users for permissions management, skip this chapter.

System-Defined Permissions for Config
-------------------------------------

By default, new IAM users do not have permissions. You need to add a user to one or more groups and attach policies to the user groups. Users in a group inherit permissions from the group, so that they can perform operations on cloud services based on the permissions.

Config is a global service. You do not need to repeat Config authorization for different regions or switch regions for accessing Config.

A user with Config read-only permissions can view all resources on the **Resource List** page.

Policy: A type of fine-grained authorization method that defines permissions required to perform operations on specific cloud resources under certain conditions. Authorization using policies is more flexible and help you implement least privilege. Most policies define permissions based on APIs. API actions are the minimum granularity of permissions. For API actions supported by Config, see the **Permissions Policies and Supported Actions** section in *Config API Reference*. For details about fine-grained permissions and their dependencies for Config, see :ref:`Fine-Grained Permissions for Config <rms_01_0600__section1491005953113>`.

:ref:`Table 1 <rms_01_0600__table298132619114>` lists all the system-defined permissions supported by Config.

.. _rms_01_0600__table298132619114:

.. table:: **Table 1** System-defined permissions supported by Config.

   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | Policy                | Description                                                                                                                                                                     | Dependencies                         |
   +=======================+=================================================================================================================================================================================+======================================+
   | Config FullAccess     | Grants full access to Config. This policy grants you the permissions to perform all actions on the resource list, resource recorder, resource compliance, and advanced queries. | -  iam:agencies:listAgencies         |
   |                       |                                                                                                                                                                                 | -  iam:roles:listRoles               |
   |                       |                                                                                                                                                                                 | -  iam:permissions:grantRoleToAgency |
   |                       |                                                                                                                                                                                 | -  smn:topic:list                    |
   |                       |                                                                                                                                                                                 | -  obs:bucket:ListAllMyBuckets       |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | Config ReadOnlyAccess | Grants read-only access to Config. This policy grants you read access to the resource list, resource recorder, and resource compliance.                                         | None                                 |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+

:ref:`Table 2 <rms_01_0600__table14568142618518>` lists the common operations and the system-defined permissions of Config. Y indicates that an operation is supported, and x indicates not supported.

.. _rms_01_0600__table14568142618518:

.. table:: **Table 2** Common operations supported by system-defined permissions

   +-----------------------------------------------------------+-------------------+-----------------------+
   | Operation                                                 | Config FullAccess | Config ReadOnlyAccess |
   +===========================================================+===================+=======================+
   | Querying all resources                                    | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Query details about a resource.                           | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Filtering resources                                       | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Exporting resources                                       | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Viewing resource compliance data                          | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Viewing relationships of a resource                       | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Viewing resource change history                           | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Querying the resource recorder                            | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Enabling, configuring, or modifying the resource recorder | Y                 | x                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Disabling the resource recorder                           | Y                 | x                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Querying a compliance policy                              | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Modifying rules                                           | Y                 | x                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Adding rules                                              | Y                 | x                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Querying rules                                            | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Deleting rules                                            | Y                 | x                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Viewing resource compliance evaluation results            | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Triggering a resource compliance evaluation               | Y                 | x                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Running advanced queries                                  | Y                 | x                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Creating advanced queries                                 | Y                 | x                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Querying advanced queries                                 | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Listing advanced queries                                  | Y                 | Y                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Updating advanced queries                                 | Y                 | x                     |
   +-----------------------------------------------------------+-------------------+-----------------------+
   | Deleting advanced queries                                 | Y                 | x                     |
   +-----------------------------------------------------------+-------------------+-----------------------+

.. _rms_01_0600__section1491005953113:

Fine-Grained Permissions for Config
-----------------------------------

If predefined permissions cannot meet your requirements, you can create custom policies. Custom policies allow you to perform fine-grained access control flexibly. For details about how to create a custom policy, see `Creating a Custom Policy <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0016.html>`__. For details about example custom policies, see :ref:`Creating a Custom Policy <rms_01_0023>`.

The following table lists the actions and dependencies for Config.

.. table:: **Table 3** Actions and dependencies for the resource list

   +---------------------------+--------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+---------------------------------------------------------+
   | Action                    | Description                                                                    | Dependencies                                                                             | Applicable Scenario                                     |
   +===========================+================================================================================+==========================================================================================+=========================================================+
   | rms:resources:getHistory  | Grants the permission to view resource history.                                | -  rms:resources:list                                                                    | Viewing resource history.                               |
   |                           |                                                                                | -  rms:resources:getRelation                                                             |                                                         |
   |                           |                                                                                | -  rms:resources:get                                                                     |                                                         |
   +---------------------------+--------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+---------------------------------------------------------+
   | rms:resources:getRelation | Grants the permission to view resource relationships and relationship details. | -  rms:resources:list                                                                    | Viewing resource relationships and relationship details |
   |                           |                                                                                | -  rms:resources:get                                                                     |                                                         |
   +---------------------------+--------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+---------------------------------------------------------+
   | rms:resources:list        | Grants the permission to view resources.                                       | To filter resources by enterprise project, **eps:enterpriseProjects:list** is required.  | Viewing, filtering, and exporting resources.            |
   +---------------------------+--------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+---------------------------------------------------------+
   | rms:resources:get         | Grants the permission to view resource details.                                | -  rms:resources:list                                                                    | Viewing resource details                                |
   |                           |                                                                                | -  To view resource compliance information, **rms:policyAssignments:get** is required.   |                                                         |
   |                           |                                                                                | -  To view resource relationship information, **rms:resources:getRelation** is required. |                                                         |
   |                           |                                                                                | -  To view resource history, **rms:resources:getHistory** is required.                   |                                                         |
   +---------------------------+--------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+---------------------------------------------------------+

.. table:: **Table 4** Actions and dependencies for the resource recorder

   +--------------------------+-------------------------------------------------------------------+--------------------------------------+-------------------------------------------------------------+
   | Action                   | Description                                                       | Dependencies                         | Applicable Scenario                                         |
   +==========================+===================================================================+======================================+=============================================================+
   | rms:trackerConfig:get    | Grants the permission to query the resource recorder.             | -  iam:agencies:listAgencies         | Viewing resource recorder configurations                    |
   |                          |                                                                   | -  smn:topic:list                    |                                                             |
   |                          |                                                                   | -  obs:bucket:ListAllMyBuckets       |                                                             |
   +--------------------------+-------------------------------------------------------------------+--------------------------------------+-------------------------------------------------------------+
   | rms:trackerConfig:put    | Grants the permission to create and modify the resource recorder. | -  iam:agencies:listAgencies         | Enabling, configuring, and modifying the resource recorder. |
   |                          |                                                                   | -  iam:roles:listRoles               |                                                             |
   |                          |                                                                   | -  iam:permissions:grantRoleToAgency |                                                             |
   |                          |                                                                   | -  iam:agencies:createAgency         |                                                             |
   +--------------------------+-------------------------------------------------------------------+--------------------------------------+-------------------------------------------------------------+
   | rms:trackerConfig:delete | Grants the permission to disable the resource recorder.           | rms:trackerConfig:get                | Disabling the resource recorder.                            |
   +--------------------------+-------------------------------------------------------------------+--------------------------------------+-------------------------------------------------------------+

.. table:: **Table 5** Actions and dependencies for resource compliance

   +--------------------------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Action                         | Description                                                               | Dependencies                                                                             | Applicable Scenario                                                                                                                                                                                         |
   +================================+===========================================================================+==========================================================================================+=============================================================================================================================================================================================================+
   | rms:policyDefinitions:get      | Grants the permission to view built-in policies.                          | None                                                                                     | Viewing built-in policies                                                                                                                                                                                   |
   +--------------------------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rms:policyAssignments:update   | Grants the permission to update rules.                                    | -  rms:policyDefinitions:get                                                             | Modifying, enabling, and disabling rules                                                                                                                                                                    |
   |                                |                                                                           | -  rms:policyAssignments:create                                                          |                                                                                                                                                                                                             |
   +--------------------------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rms:policyAssignments:create   | Grants the permission to create rules.                                    | -  To create a rule with a predefined policy, **rms:policyDefinitions:get** is required. | Adding rules.                                                                                                                                                                                               |
   |                                |                                                                           | -  To create a custom rule, the following permissions are required:                      |                                                                                                                                                                                                             |
   |                                |                                                                           |                                                                                          |                                                                                                                                                                                                             |
   |                                |                                                                           |    -  iam:agencies:listAgencies                                                          |                                                                                                                                                                                                             |
   |                                |                                                                           |    -  iam:roles:listRoles                                                                |                                                                                                                                                                                                             |
   |                                |                                                                           |    -  iam:permissions:grantRoleToAgency                                                  |                                                                                                                                                                                                             |
   |                                |                                                                           |    -  iam:agencies:createAgency                                                          |                                                                                                                                                                                                             |
   +--------------------------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rms:policyAssignments:get      | Grants the permission to view rules                                       | None                                                                                     | Viewing rules and their details.                                                                                                                                                                            |
   +--------------------------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rms:policyAssignments:delete   | Grants the permission to delete rules.                                    | rms:policyAssignments:get                                                                | Deleting rules.                                                                                                                                                                                             |
   +--------------------------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rms:policyStates:get           | Grants the permission to query the state and evaluation result of a rule. | rms:policyAssignments:get                                                                | Querying the state and evaluation result of a rule. If you call an API to query the state and evaluation result of a rule, this action is required. If you use Config console, this action is not required. |
   +--------------------------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rms:policyStates:runEvaluation | Grants the permission to run rules.                                       | rms:policyAssignments:get                                                                | Manually triggering a rule.                                                                                                                                                                                 |
   +--------------------------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 6** Actions and dependencies for advanced queries

   +--------------------------+--------------------------------------------------+---------------------------+-----------------------------------------------------+
   | Action                   | Description                                      | Dependencies              | Applicable Scenario                                 |
   +==========================+==================================================+===========================+=====================================================+
   | rms:resources:runQuery   | Grants the permission to run advanced queries.   | -  rms:storedQueries:list | Running advanced queries                            |
   |                          |                                                  | -  rms:storedQueries:get  |                                                     |
   +--------------------------+--------------------------------------------------+---------------------------+-----------------------------------------------------+
   | rms:storedQueries:create | Grants the permission to create queries.         | None                      | Creating queries                                    |
   +--------------------------+--------------------------------------------------+---------------------------+-----------------------------------------------------+
   | rms:storedQueries:get    | Grants the permission to view query statements.  | rms:storedQueries:list    | Viewing query statements                            |
   +--------------------------+--------------------------------------------------+---------------------------+-----------------------------------------------------+
   | rms:storedQueries:list   | Grants the permission to list queries.           | None                      | Listing queries.                                    |
   +--------------------------+--------------------------------------------------+---------------------------+-----------------------------------------------------+
   | rms:storedQueries:update | Grants the permission to update query statements | -  rms:storedQueries:list | Modifying custom queries                            |
   |                          |                                                  | -  rms:storedQueries:get  |                                                     |
   +--------------------------+--------------------------------------------------+---------------------------+-----------------------------------------------------+
   | rms:storedQueries:delete | Grants the permission to deleting queries.       | rms:storedQueries:list    | Deleting custom queries                             |
   +--------------------------+--------------------------------------------------+---------------------------+-----------------------------------------------------+
   | rms:schemas:list         | Listing advanced query schemas                   | None                      | Viewing resource attributes synchronized to Config. |
   +--------------------------+--------------------------------------------------+---------------------------+-----------------------------------------------------+
