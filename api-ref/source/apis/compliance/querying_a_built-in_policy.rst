:original_name: rms_04_0502.html

.. _rms_04_0502:

Querying a Built-in Policy
==========================

Function
--------

This API is used to query a built-in policy based on the policy ID.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/policy-definitions/{policy_definition_id}

.. table:: **Table 1** Path Parameters

   +----------------------+-----------------+-----------------+--------------------------+
   | Parameter            | Mandatory       | Type            | Description              |
   +======================+=================+=================+==========================+
   | policy_definition_id | Yes             | String          | Specifies the policy ID. |
   |                      |                 |                 |                          |
   |                      |                 |                 | Maximum: **36**          |
   +----------------------+-----------------+-----------------+--------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                                                    |
   +==================+=================+=================+================================================================================================================================================================+
   | X-Auth-Token     | No              | String          | Specifies the invoker's token.                                                                                                                                 |
   +------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Language       | No              | String          | Language of the returned message.                                                                                                                              |
   |                  |                 |                 |                                                                                                                                                                |
   |                  |                 |                 | Default: **en-us**                                                                                                                                             |
   +------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Security-Token | No              | String          | Security token (session token) for temporary security credentials. This parameter is mandatory when you make an API call using temporary security credentials. |
   +------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | Parameter              | Type                                                                                             | Description                                                              |
   +========================+==================================================================================================+==========================================================================+
   | id                     | String                                                                                           | Specifies the policy ID.                                                 |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | name                   | String                                                                                           | Specifies the policy name.                                               |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | display_name           | String                                                                                           | Specifies the policy display name.                                       |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | policy_type            | String                                                                                           | Specifies the policy type.                                               |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | description            | String                                                                                           | Specifies the description of the policy definition.                      |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | policy_rule_type       | String                                                                                           | Specifies the syntax type of the policy.                                 |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | policy_rule            | Object                                                                                           | Specifies the policy rule.                                               |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | trigger_type           | String                                                                                           | Specifies the trigger type. The value can be **resource** or **period**. |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | keywords               | Array of strings                                                                                 | Specifies keywords.                                                      |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | default_resource_types | Array of :ref:`default_resource_types <rms_04_0502__response_default_resource_types>` objects    | Specifies the list of default resource types.                            |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | parameters             | Map<String,\ :ref:`PolicyParameterDefinition <rms_04_0502__response_policyparameterdefinition>`> | Specifies the policy parameter.                                          |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+

.. _rms_04_0502__response_default_resource_types:

.. table:: **Table 4** default_resource_types

   ========= ====== =================================
   Parameter Type   Description
   ========= ====== =================================
   provider  String Specifies the cloud service name.
   type      String Specifies the resource type.
   ========= ====== =================================

.. table:: **Table 5** Parameter description of the example policy

   +-------------------+--------+--------------------------------------------------------------------------------+
   | Parameter         | Type   | Description                                                                    |
   +===================+========+================================================================================+
   | specifiedTagKey   | String | Indicates the tag key.                                                         |
   +-------------------+--------+--------------------------------------------------------------------------------+
   | specifiedTagValue | Array  | Indicates tag values. If the value list is left empty, all values are allowed. |
   +-------------------+--------+--------------------------------------------------------------------------------+

.. _rms_04_0502__response_policyparameterdefinition:

.. table:: **Table 6** PolicyParameterDefinition

   +----------------+------------------+-----------------------------------------------------------------------------+
   | Parameter      | Type             | Description                                                                 |
   +================+==================+=============================================================================+
   | name           | String           | Specifies the name of the policy parameter.                                 |
   +----------------+------------------+-----------------------------------------------------------------------------+
   | description    | String           | Specifies the description of the policy parameter.                          |
   +----------------+------------------+-----------------------------------------------------------------------------+
   | allowed_values | Array of objects | Specifies the allowed values of the policy parameter.                       |
   +----------------+------------------+-----------------------------------------------------------------------------+
   | default_value  | String           | Specifies the default value of the policy parameter.                        |
   +----------------+------------------+-----------------------------------------------------------------------------+
   | minimum        | Float            | Specifies the minimum value of the policy parameter.                        |
   +----------------+------------------+-----------------------------------------------------------------------------+
   | maximum        | Float            | Specifies the maximum value of the policy parameter.                        |
   +----------------+------------------+-----------------------------------------------------------------------------+
   | min_items      | Integer          | Specifies the minimum number of the policy parameter.                       |
   +----------------+------------------+-----------------------------------------------------------------------------+
   | max_items      | Integer          | Specifies the maximum number of the policy parameter.                       |
   +----------------+------------------+-----------------------------------------------------------------------------+
   | min_length     | Integer          | Specifies the minimum string length for policy parameters or for each item. |
   +----------------+------------------+-----------------------------------------------------------------------------+
   | max_length     | Integer          | Specifies the maximum string length for policy parameters or for each item. |
   +----------------+------------------+-----------------------------------------------------------------------------+
   | pattern        | String           | Specifies the pattern for policy parameters or for each item.               |
   +----------------+------------------+-----------------------------------------------------------------------------+
   | type           | String           | Specifies the type of the policy parameter.                                 |
   +----------------+------------------+-----------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 403**

.. table:: **Table 8** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 404**

.. table:: **Table 9** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 500**

.. table:: **Table 10** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

Example Requests
----------------

.. code-block:: text

   GET https://{endpoint}/v1/resource-manager/policy-definitions/5f8d5428ffeecc14f1fb5205

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "id": "5fa9f89b6eed194ccb2c04db",
     "name": "required-tag-check",
     "display_name": "required-tag-check",
     "policy_type": "builtin",
     "description": "If a resource is not attached with the specified tag, this resource is considered noncompliant.",
     "policy_rule_type": "dsl",
     "policy_rule": {
       "anyOf": [
         {
           "value": "${contains(resource().tags, parameters('specifiedTagKey'))}",
           "comparator": "equals",
           "pattern": false
         },
         {
           "allOf": [
             {
               "value": "${length(parameters('specifiedTagValue'))}",
               "comparator": "greater",
               "pattern": 0
             },
             {
               "value": "${getValue(resource().tags, parameters('specifiedTagKey'))}",
               "comparator": "notIn",
               "pattern": "${parameters('specifiedTagValue')}"
             }
           ]
         }
       ]
     },
     "trigger_type": "resource",
     "keywords": [
       "tag"
     ],
     "default_resource_types": [],
     "parameters": {
       "specifiedTagKey": {
         "name": null,
         "description": "The specified tag key.",
         "allowed_values": null,
         "default_value": null,
         "minimum": null,
         "maximum": null,
         "min_items": null,
         "max_items": null,
         "min_length": 1,
         "max_length": 128,
         "pattern": null,
         "type": "String"
       },
       "specifiedTagValue": {
         "name": null,
         "description": "The list of allowed tag value, permit all if empty.",
         "allowed_values": null,
         "default_value": null,
         "minimum": null,
         "maximum": null,
         "min_items": 0,
         "max_items": 40,
         "min_length": 0,
         "max_length": 255,
         "pattern": null,
         "type": "Array"
       }
     }
   }

.. note::

   **allOf** and **anyOf** in the response example are logical operators. The following describes these two operators in detail:

   **allOf** evaluates true only if all included conditions are true, and evaluates false as long as one included condition is false.

   **anyOf** evaluates true as long as one included condition is true, and evaluates false if all included conditions are false.

   **allOf** and **anyOf** both implement short-circuit evaluation. They evaluate the conditions in the subsequent list in sequence.

   If the return result of a condition is false, **allOf** returns false and the subsequent conditions are not calculated.

   If the return result of a condition is true, **anyOf** returns true and the subsequent conditions are not calculated.

Status Codes
------------

+-------------+---------------------------------------------------------------------+
| Status Code | Description                                                         |
+=============+=====================================================================+
| 200         | Operation succeeded.                                                |
+-------------+---------------------------------------------------------------------+
| 400         | Invalid parameters.                                                 |
+-------------+---------------------------------------------------------------------+
| 403         | Authentication failed or you do not have the operation permissions. |
+-------------+---------------------------------------------------------------------+
| 404         | Policy not found.                                                   |
+-------------+---------------------------------------------------------------------+
| 500         | Server error.                                                       |
+-------------+---------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
