:original_name: rms_04_0511.html

.. _rms_04_0511:

Querying the Evaluation Status of a Rule
========================================

Function
--------

This API is used to query the evaluation status of a rule by rule ID.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/policy-assignments/{policy_assignment_id}/policy-states/evaluation-state

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +----------------------+--------+---------------------------------------------------------+
   | Parameter            | Type   | Description                                             |
   +======================+========+=========================================================+
   | policy_assignment_id | String | Specifies the rule ID.                                  |
   +----------------------+--------+---------------------------------------------------------+
   | state                | String | Specifies the evaluation status.                        |
   +----------------------+--------+---------------------------------------------------------+
   | start_time           | String | Specifies the evaluation start time.                    |
   +----------------------+--------+---------------------------------------------------------+
   | end_time             | String | Specifies the evaluation end time.                      |
   +----------------------+--------+---------------------------------------------------------+
   | error_message        | String | Specifies the error message for the evaluation failure. |
   +----------------------+--------+---------------------------------------------------------+

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 403**

.. table:: **Table 5** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 404**

.. table:: **Table 6** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 500**

.. table:: **Table 7** Response body parameters

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
     "state" : "Succeeded",
     "policy_assignment_id" : "5fb6292765ee7f5e92a7ca4b",
     "start_time" : "2020-11-19T08:13:27.441Z",
     "end_time" : "2020-11-19T08:13:27.485Z",
     "error_message" : null
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
