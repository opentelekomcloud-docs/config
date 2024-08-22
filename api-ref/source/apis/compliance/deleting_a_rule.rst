:original_name: rms_04_0507.html

.. _rms_04_0507:

Deleting a Rule
===============

Function
--------

This API is used to delete a rule based on the rule ID. Only rules in the disabled state can be deleted.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

DELETE /v1/resource-manager/domains/{domain_id}/policy-assignments/{policy_assignment_id}

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

**Status code: 400**

.. table:: **Table 3** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 403**

.. table:: **Table 4** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 404**

.. table:: **Table 5** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 500**

.. table:: **Table 6** Response body parameters

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

None

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
