:original_name: rms_04_0501.html

.. _rms_04_0501:

Querying All Built-in Policies
==============================

Function
--------

This API is used to query all built-in policies.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/policy-definitions

Request Parameters
------------------

.. table:: **Table 1** Request header parameters

   +------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                                                    |
   +==================+=================+=================+================================================================================================================================================================+
   | X-Language       | No              | String          | Language of the returned message.                                                                                                                              |
   |                  |                 |                 |                                                                                                                                                                |
   |                  |                 |                 | Default: **en-us**                                                                                                                                             |
   +------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token     | No              | String          | Specifies the invoker's token.                                                                                                                                 |
   +------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Security-Token | No              | String          | Security token (session token) for temporary security credentials. This parameter is mandatory when you make an API call using temporary security credentials. |
   +------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+-----------------------------------------------------------------------------------+---------------------------------------+
   | Parameter | Type                                                                              | Description                           |
   +===========+===================================================================================+=======================================+
   | value     | Array of :ref:`PolicyDefinition <rms_04_0501__response_policydefinition>` objects | Specifies the policy definition list. |
   +-----------+-----------------------------------------------------------------------------------+---------------------------------------+
   | page_info | :ref:`PageInfo <rms_04_0501__response_pageinfo>` object                           | Specifies the pagination object.      |
   +-----------+-----------------------------------------------------------------------------------+---------------------------------------+

.. _rms_04_0501__response_policydefinition:

.. table:: **Table 3** PolicyDefinition

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
   | default_resource_types | Array of :ref:`default_resource_types <rms_04_0501__response_default_resource_types>` objects    | Specifies the list of default resource types.                            |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | parameters             | Map<String,\ :ref:`PolicyParameterDefinition <rms_04_0501__response_policyparameterdefinition>`> | Specifies the policy parameter.                                          |
   +------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+

.. _rms_04_0501__response_default_resource_types:

.. table:: **Table 4** default_resource_types

   ========= ====== =================================
   Parameter Type   Description
   ========= ====== =================================
   provider  String Specifies the cloud service name.
   type      String Specifies the resource type.
   ========= ====== =================================

.. _rms_04_0501__response_policyparameterdefinition:

.. table:: **Table 5** PolicyParameterDefinition

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

.. _rms_04_0501__response_pageinfo:

.. table:: **Table 6** PageInfo

   +-----------------------+-----------------------+------------------------------------------------------+
   | Parameter             | Type                  | Description                                          |
   +=======================+=======================+======================================================+
   | current_count         | Integer               | Specifies the resource quantity on the current page. |
   |                       |                       |                                                      |
   |                       |                       | Minimum: **0**                                       |
   |                       |                       |                                                      |
   |                       |                       | Maximum: **200**                                     |
   +-----------------------+-----------------------+------------------------------------------------------+
   | next_marker           | String                | Specifies the **marker** value of the next page.     |
   |                       |                       |                                                      |
   |                       |                       | Minimum: **4**                                       |
   |                       |                       |                                                      |
   |                       |                       | Maximum: **400**                                     |
   +-----------------------+-----------------------+------------------------------------------------------+

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

   GET https://{endpoint}/v1/resource-manager/policy-definitions

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "value" : [ {
       "id" : "5fa365476eed194ccb2c04d1",
       "name" : "volumes-encrypted-check",
       "display_name" : "Enable encryption for the attached EVS volumes.",
       "policy_type" : "builtin",
       "description" : "An EVS disk is non-compliant if it has been mounted but not encrypted.",
       "policy_rule_type" : "dsl",
       "policy_rule" : {
         "allOf" : [ {
           "value" : "${resource().provider}",
           "comparator" : "equals",
           "pattern" : "evs"
         }, {
           "value" : "${resource().type}",
           "comparator" : "equals",
           "pattern" : "volumes"
         }, {
           "value" : "${resource().properties.status}",
           "comparator" : "equals",
           "pattern" : "in-use"
         }, {
           "anyOf" : [ {
             "value" : "${resource().properties.metadata}",
             "comparator" : "notContainsKey",
             "pattern" : "systemEncrypted"
           }, {
             "value" : "${resource().properties.metadata.systemEncrypted}",
             "comparator" : "equals",
             "pattern" : "0"
           } ]
         } ]
       },
       "keywords" : [ "evs", "ecs" ],
       "parameters" : { }
     } ],
     "page_info" : {
       "current_count" : 1,
       "next_marker" : null
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
| 400         | Invalid parameter.                                                  |
+-------------+---------------------------------------------------------------------+
| 403         | Authentication failed or you do not have the operation permissions. |
+-------------+---------------------------------------------------------------------+
| 404         | Resources not found.                                                |
+-------------+---------------------------------------------------------------------+
| 500         | Server error.                                                       |
+-------------+---------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
