:original_name: rms_04_0706.html

.. _rms_04_0706:

Deleting an Advanced Query
==========================

Function
--------

This API is used to delete an advanced query.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

DELETE /v1/resource-manager/domains/{domain_id}/stored-queries/{query_id}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-------------------------+
   | Parameter       | Mandatory       | Type            | Description             |
   +=================+=================+=================+=========================+
   | domain_id       | Yes             | String          | Specifies tags.         |
   |                 |                 |                 |                         |
   |                 |                 |                 | Maximum: **36**         |
   +-----------------+-----------------+-----------------+-------------------------+
   | query_id        | Yes             | String          | Specifies the query ID. |
   |                 |                 |                 |                         |
   |                 |                 |                 | Maximum: **36**         |
   +-----------------+-----------------+-----------------+-------------------------+

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

=========== ===========================
Status Code Description
=========== ===========================
204         Operation succeeded.
400         Invalid parameters.
403         User authentication failed.
404         No resource found.
500         Server error.
=========== ===========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
