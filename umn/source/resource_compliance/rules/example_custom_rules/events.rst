:original_name: rms_05_0506.html

.. _rms_05_0506:

Events
======

Example Event for Evaluations Triggered by Configuration Changes
----------------------------------------------------------------

When a custom rule is triggered, Config will send an event to invoke the FunctionGraph function associated with the rule. The following example shows an event sent by Config when a custom rule was triggered by a configuration change for **ecs.cloudservers**.

.. code-block::

   {
     "domain_id": "domain_id",
     "policy_assignment_id": "637c6b2e6b647c4d313d9719",
     "policy_assignment_name": "period-policy-period",
     "function_urn": "urn:fss:region_1:123456789:function:default:test-custom-policyassignment:latest",
     "trigger_type": "resource",
     "evaluation_time": 1669098286719,
     "evaluation_hash": "3bf8ecaeb0864feb98639080aea5c7d9",
     "rule_parameter": {
       "vpcId": {
         "value": "fake_id"
       }
     },
     "invoking_event": {
       "id": "5e0d49c8-7ce0-4c31-9d92-28b05200b838",
       "name": "default",
       "provider": "vpc",
       "type": "securityGroups",
       "tags": {},
       "created": "2022-11-07T12:58:46.000+00:00",
       "updated": "2022-11-07T12:58:46.000+00:00",
       "properties": {
         "description": "Default security group",
         "security_group_rules": [
           {
             "remote_group_id": "5e0d49c8-7ce0-4c31-9d92-28b05200b838",
             "ethertype": "IPv6",
             "security_group_id": "5e0d49c8-7ce0-4c31-9d92-28b05200b838",
             "port_range_max": 0,
             "id": "19f581bc-08a7-4037-ae59-9a6838c43709",
             "direction": "ingress",
             "port_range_min": 0
           },
           {
             "ethertype": "IPv6",
             "security_group_id": "5e0d49c8-7ce0-4c31-9d92-28b05200b838",
             "port_range_max": 0,
             "id": "75dae7b6-0b71-496f-8f11-87fb30300e18",
             "direction": "egress",
             "port_range_min": 0
           }
         ]
       },
       "ep_id": "0",
       "project_id": "vpc",
       "region_id": "region_1",
       "provisioning_state": "Succeeded"
     }
   }

Example Event for Evaluations Triggered by Periodic Execution
-------------------------------------------------------------

Config publishes an event when it evaluates your resources at a frequency that you specify, such as every 24 hours. The following example shows an event sent by Config when a custom rule was triggered at a specific frequency.

.. code-block::

   {
     "domain_id": "domain_id",
     "policy_assignment_id": "637c6b2e6b647c4d313d9719",
     "policy_assignment_name": "period-policy-assignment",
     "function_urn": "urn:fss:region_1:123456789:function:default:test-custom-policyassignment:latest",
     "trigger_type": "period",
     "evaluation_time": 1669098286719,
     "evaluation_hash": "3bf8ecaeb0864feb98639080aea5c7d9",
     "rule_parameter": {},
     "invoking_event": {
       "id": "domain_id",
       "name": "Account",
       "provider": null,
       "type": null,
       "tags": null,
       "created": null,
       "updated": null,
       "properties": null,
       "ep_id": null,
       "project_id": null,
       "region_id": "global",
       "provisioning_state": null
     }
   }
