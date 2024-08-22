:original_name: rms_05_0100.html

.. _rms_05_0100:

Permissions Policies and Supported Actions
==========================================

This chapter describes how to use IAM to implement fine-grained permissions control for your Config resources. If your account does not need individual IAM users, skip this chapter.

A policy is a set of permissions defined in JSON format. By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

Based on authorization granularity, permissions are classified into roles and policies.

-  Roles are a type of service-based, coarse-grained authorization mechanism that defines permissions related to user responsibilities.
-  Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

.. note::

   Policy-based authorization is useful if you want to allow or deny the access to an API.

An account has all the permissions required to call all APIs, but IAM users must be assigned the required permissions. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully. For example, if an IAM user wants to query a resource recorder using an API, the user must have the permissions that allow the **rms:trackerConfig:get** action.

Supported Actions
-----------------

Operations supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permissions: Statements in a policy that allow or deny certain operations.

-  APIs: REST APIs that can be called by a user who has been granted specific permissions.

-  Actions: Specific operations that are allowed or denied.

-  Related actions: Actions on which a specific action depends to take effect. When assigning permissions for the action to a user, you also need to assign permissions for the related actions.

-  IAM projects or enterprise projects: Type of projects in which policies can be used to grant permissions. A policy can be applied to IAM projects, enterprise projects, or both. Policies that contain actions for both IAM and enterprise projects can be used and take effect for both IAM and Enterprise Management. Policies that only contain actions for IAM projects can be used and only take effect for IAM.

   Config supports the following actions that can be defined in custom policies:

   :ref:`Resource Query <rms_05_0200>` describes the actions and corresponding APIs for listing resources and querying details of a resource.

   :ref:`Resource Recorder <rms_05_0300>` describes the actions and corresponding APIs for querying, enabling, and disabling the resource recorder.

   :ref:`Resource Relationships <en-us_topic_0000001991150822>` describes the actions and corresponding APIs for querying resource relationships.

   :ref:`Resource Change Records <en-us_topic_0000002027710481>` describes the actions and corresponding APIs for querying resource changes.

   :ref:`Compliance <rms_05_0400>` describes the actions and corresponding APIs for adding, deleting, modifying, and querying Config rules.

   :ref:`Region Management <en-us_topic_0000002027750033>` describes the actions and corresponding APIs for querying regions that can be viewed.

   :ref:`Advanced Queries <rms_05_0500>` describes the actions and corresponding APIs for adding, deleting, modifying, and querying advanced queries.

   .. note::

      The check mark (Y) indicates that an action takes effect. The cross mark (x) indicates that an action does not take effect.
