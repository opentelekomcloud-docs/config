:original_name: rms_04_0701.html

.. _rms_04_0701:

Running Advanced Queries
========================

Function
--------

This API is used to run advanced queries.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

POST /v1/resource-manager/domains/{domain_id}/run-query

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

   +-----------------+-----------------+-----------------+--------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                          |
   +=================+=================+=================+======================================+
   | expression      | Yes             | String          | Specifies the ResourceQL expression. |
   |                 |                 |                 |                                      |
   |                 |                 |                 | Minimum: **1**                       |
   |                 |                 |                 |                                      |
   |                 |                 |                 | Maximum: **4096**                    |
   +-----------------+-----------------+-----------------+--------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------+-----------------------------------------------------------+----------------------------------------+
   | Parameter  | Type                                                      | Description                            |
   +============+===========================================================+========================================+
   | query_info | :ref:`QueryInfo <rms_04_0701__response_queryinfo>` object | Specifies the ResourceQL query field.  |
   +------------+-----------------------------------------------------------+----------------------------------------+
   | results    | Array of objects                                          | Specifies the ResourceQL query result. |
   +------------+-----------------------------------------------------------+----------------------------------------+

.. _rms_04_0701__response_queryinfo:

.. table:: **Table 5** QueryInfo

   ============= ================ =====================================
   Parameter     Type             Description
   ============= ================ =====================================
   select_fields Array of strings Specifies the ResourceQL query field.
   ============= ================ =====================================

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

**Status code: 429**

.. table:: **Table 8** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

Example Requests
----------------

-  Querying IDs of all VMs under your account

   .. code-block:: text

      POST https://{endpoint}/v1/resource-manager/domains/{domain_id}/run-query

      {
        "expression" : "select id from resources where provider = 'ecs' and type = 'cloudservers'"
      }

-  Querying 100-GB Elastic Volume Service (EVS) disks under your account

   .. code-block:: text

      POST https://{endpoint}/v1/resource-manager/domains/{domain_id}/run-query

      {
        "expression" : "select * from resources where provider = 'evs' and type = 'volumes' and properties.size = 100"
      }

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "query_info" : {
       "select_fields" : [ "id" ]
     },
     "results" : [ {
       "id" : "91252cc9-bfd9-0709-0912-56b397e0ba3f"
     } ]
   }

Status Codes
------------

=========== ===========================
Status Code Description
=========== ===========================
200         Operation succeeded.
400         Invalid parameters.
403         User authentication failed.
429         Limit exceeded.
500         Server error.
=========== ===========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
