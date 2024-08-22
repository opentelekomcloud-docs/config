:original_name: rms_04_0515.html

.. _rms_04_0515:

Updating the Compliance Result
==============================

Function
--------

This API is used to update the compliance result of a custom rule.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

PUT /v1/resource-manager/domains/{domain_id}/policy-states

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------+
   | Parameter       | Mandatory       | Type            | Description     |
   +=================+=================+=================+=================+
   | domain_id       | Yes             | String          | Specifies tags. |
   |                 |                 |                 |                 |
   |                 |                 |                 | Maximum: **36** |
   +-----------------+-----------------+-----------------+-----------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type   | Description                                                                                                                                                    |
   +==================+===========+========+================================================================================================================================================================+
   | X-Auth-Token     | No        | String | Specifies the invoker's token.                                                                                                                                 |
   +------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Security-Token | No        | String | Security token (session token) for temporary security credentials. This parameter is mandatory when you make an API call using temporary security credentials. |
   +------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +------------------------+-----------+--------------------------------------------------------------------+--------------------------------------------------------------------------+
   | Parameter              | Mandatory | Type                                                               | Description                                                              |
   +========================+===========+====================================================================+==========================================================================+
   | policy_resource        | Yes       | :ref:`PolicyResource <rms_04_0515__request_policyresource>` object | Specifies the resource.                                                  |
   +------------------------+-----------+--------------------------------------------------------------------+--------------------------------------------------------------------------+
   | trigger_type           | Yes       | String                                                             | Specifies the trigger type. The value can be **resource** or **period**. |
   +------------------------+-----------+--------------------------------------------------------------------+--------------------------------------------------------------------------+
   | compliance_state       | Yes       | String                                                             | Specifies the compliance status.                                         |
   +------------------------+-----------+--------------------------------------------------------------------+--------------------------------------------------------------------------+
   | policy_assignment_id   | Yes       | String                                                             | Specifies the policy rule id.                                            |
   +------------------------+-----------+--------------------------------------------------------------------+--------------------------------------------------------------------------+
   | policy_assignment_name | No        | String                                                             | Specifies the policy rule name.                                          |
   +------------------------+-----------+--------------------------------------------------------------------+--------------------------------------------------------------------------+
   | evaluation_time        | Yes       | String                                                             | Specifies when a rule is used to evaluate the resource compliance.       |
   +------------------------+-----------+--------------------------------------------------------------------+--------------------------------------------------------------------------+
   | evaluation_hash        | Yes       | String                                                             | Specifies the evaluation verification code.                              |
   +------------------------+-----------+--------------------------------------------------------------------+--------------------------------------------------------------------------+

.. _rms_04_0515__request_policyresource:

.. table:: **Table 4** PolicyResource

   +-------------------+-----------+--------+-------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                 |
   +===================+===========+========+=============================================================+
   | resource_id       | No        | String | Specifies the resource ID.                                  |
   +-------------------+-----------+--------+-------------------------------------------------------------+
   | resource_name     | No        | String | Specifies the resource name.                                |
   +-------------------+-----------+--------+-------------------------------------------------------------+
   | resource_provider | No        | String | Specifies the cloud service name.                           |
   +-------------------+-----------+--------+-------------------------------------------------------------+
   | resource_type     | No        | String | Specifies the resource type.                                |
   +-------------------+-----------+--------+-------------------------------------------------------------+
   | region_id         | No        | String | Specifies the region ID.                                    |
   +-------------------+-----------+--------+-------------------------------------------------------------+
   | domain_id         | No        | String | Specifies the ID of the user to which the resource belongs. |
   +-------------------+-----------+--------+-------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +------------------------+--------+--------------------------------------------------------------------------+
   | Parameter              | Type   | Description                                                              |
   +========================+========+==========================================================================+
   | domain_id              | String | Specifies the user ID.                                                   |
   +------------------------+--------+--------------------------------------------------------------------------+
   | region_id              | String | Specifies the ID of the region the resource belongs to.                  |
   +------------------------+--------+--------------------------------------------------------------------------+
   | resource_id            | String | Specifies the resource ID.                                               |
   +------------------------+--------+--------------------------------------------------------------------------+
   | resource_name          | String | Specifies the resource name.                                             |
   +------------------------+--------+--------------------------------------------------------------------------+
   | resource_provider      | String | Specifies the cloud service name.                                        |
   +------------------------+--------+--------------------------------------------------------------------------+
   | resource_type          | String | Specifies the resource type.                                             |
   +------------------------+--------+--------------------------------------------------------------------------+
   | trigger_type           | String | Specifies the trigger type. The value can be **resource** or **period**. |
   +------------------------+--------+--------------------------------------------------------------------------+
   | compliance_state       | String | Specifies the compliance status.                                         |
   +------------------------+--------+--------------------------------------------------------------------------+
   | policy_assignment_id   | String | Specifies the rule ID.                                                   |
   +------------------------+--------+--------------------------------------------------------------------------+
   | policy_assignment_name | String | Specifies the rule name.                                                 |
   +------------------------+--------+--------------------------------------------------------------------------+
   | policy_definition_id   | String | Specifies the policy ID.                                                 |
   +------------------------+--------+--------------------------------------------------------------------------+
   | evaluation_time        | String | Specifies the evaluation time of compliance status.                      |
   +------------------------+--------+--------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

Example Requests
----------------

The reported compliance result by functionGraph is **NonCompliant**.

.. code-block:: text

   PUT https://{endpoint}/v1/resource-manager/domains/{domain_id}/policy-states

   {
     "policy_resource" : {
       "domain_id" : "d0123456789",
       "region_id" : "global",
       "resource_id" : "abc0123456789",
       "resource_name" : "test_user",
       "resource_provider" : "iam",
       "resource_type" : "users"
     },
     "trigger_type" : "resource",
     "compliance_state" : "NonCompliant",
     "policy_assignment_id" : "abc0123456789abc",
     "policy_assignment_name" : "custom_policy",
     "evaluation_time" : 1667374060248,
     "evaluation_hash" : "89342b8f338165651991afb8bd471396"
   }

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "domain_id" : "d0123456789",
     "region_id" : "global",
     "resource_id" : "abc0123456789",
     "resource_name" : "test_user",
     "resource_provider" : "iam",
     "resource_type" : "users",
     "trigger_type" : "resource",
     "compliance_state" : "NonCompliant",
     "policy_assignment_id" : "abc0123456789abc",
     "policy_assignment_name" : "custom_policy",
     "policy_definition_id" : null,
     "evaluation_time" : 1667374060248
   }

**Status code: 400**

Operation failed.

The following error code and message do not indicate any exceptions if they are displayed when you invoke the API based on the example request.

.. code-block::

   {
     "error_code": "invalid_parameters",
     "error_msg": "evaluationHash should not be customized"
   }

.. note::

   A FunctionGraph function of a Config rule requires a valid **evaluation_hash** for it to operate normally. After a custom Config rule is triggered, Config sends an event to call the corresponding FunctionGraph function. And the FunctionGraph function obtains the **evaluation_hash** from the event. After obtaining the **evaluation_hash**, the function sends evaluation results to Config using the API.

   In general, this API is not intended for users, but for FunctionGraph functions of Config rules. If the preceding error message is displayed when you call this API, it indicates that the FunctionGraph function has the permission to send evaluation results to Config.

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
| 500         | Server error.                                                       |
+-------------+---------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
