:original_name: rms_04_0513.html

.. _rms_04_0513:

Querying All Compliance Results of Resources Evaluated by a Rule
================================================================

Function
--------

This API is used to query all compliance results of resources evaluated by a rule. The rule is searched by rule ID.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/policy-assignments/{policy_assignment_id}/policy-states

.. table:: **Table 1** Path Parameters

   +----------------------+-----------------+-----------------+------------------------+
   | Parameter            | Mandatory       | Type            | Description            |
   +======================+=================+=================+========================+
   | domain_id            | Yes             | String          | Specifies tags.        |
   |                      |                 |                 |                        |
   |                      |                 |                 | Maximum: **36**        |
   +----------------------+-----------------+-----------------+------------------------+
   | policy_assignment_id | Yes             | String          | Specifies the rule ID. |
   |                      |                 |                 |                        |
   |                      |                 |                 | Maximum: **36**        |
   +----------------------+-----------------+-----------------+------------------------+

.. table:: **Table 2** Query Parameters

   +------------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                        |
   +==================+=================+=================+====================================================+
   | compliance_state | No              | String          | Specifies the compliance status.                   |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Maximum: **16**                                    |
   +------------------+-----------------+-----------------+----------------------------------------------------+
   | resource_id      | No              | String          | Specifies the resource ID.                         |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Maximum: **512**                                   |
   +------------------+-----------------+-----------------+----------------------------------------------------+
   | resource_name    | No              | String          | Specifies the resource name.                       |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Maximum: **256**                                   |
   +------------------+-----------------+-----------------+----------------------------------------------------+
   | limit            | No              | Integer         | Specifies the maximum number of records to return. |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Minimum: **1**                                     |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Maximum: **200**                                   |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Default: **200**                                   |
   +------------------+-----------------+-----------------+----------------------------------------------------+
   | marker           | No              | String          | Specifies the pagination parameter.                |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Minimum: **4**                                     |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Maximum: **400**                                   |
   +------------------+-----------------+-----------------+----------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type   | Description                                                                                                                                                    |
   +==================+===========+========+================================================================================================================================================================+
   | X-Auth-Token     | No        | String | Specifies the invoker's token.                                                                                                                                 |
   +------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Security-Token | No        | String | Security token (session token) for temporary security credentials. This parameter is mandatory when you make an API call using temporary security credentials. |
   +------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+-------------------------------------------------------------------------+---------------------------------------------------------------+
   | Parameter | Type                                                                    | Description                                                   |
   +===========+=========================================================================+===============================================================+
   | value     | Array of :ref:`PolicyState <rms_04_0513__response_policystate>` objects | Specifies the return value of querying the compliance result. |
   +-----------+-------------------------------------------------------------------------+---------------------------------------------------------------+
   | page_info | :ref:`PageInfo <rms_04_0513__response_pageinfo>` object                 | Specifies the pagination object.                              |
   +-----------+-------------------------------------------------------------------------+---------------------------------------------------------------+

.. _rms_04_0513__response_policystate:

.. table:: **Table 5** PolicyState

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

.. _rms_04_0513__response_pageinfo:

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

None

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "value" : [ {
       "domain_id" : "059b5c937100d3e40ff0c00a7675a0a0",
       "region_id" : "eu-de",
       "resource_id" : "010d95bd-87cd-4f22-ac00-db7fba7d927e",
       "resource_name" : "ecs-cc-image-test1",
       "resource_provider" : "ecs",
       "resource_type" : "cloudservers",
       "trigger_type" : "resource",
       "compliance_state" : "NonCompliant",
       "policy_assignment_id" : "5fb618a726a24c53767fa049",
       "policy_assignment_name" : "policy-assignment-test1",
       "policy_definition_id" : "5fa265c0aa1e6afc05a0ff07",
       "evaluation_time" : 1605776482523
     } ],
     "page_info" : {
       "current_count" : 1,
       "next_marker" : null
     }
   }

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
| 404         | No rules found.                                                     |
+-------------+---------------------------------------------------------------------+
| 500         | Server error.                                                       |
+-------------+---------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
