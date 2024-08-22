:original_name: rms_04_0107.html

.. _rms_04_0107:

Querying the Number of Resources
================================

Function
--------

This API is used to query the number of resources.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/all-resources/count

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------+
   | Parameter       | Mandatory       | Type            | Description     |
   +=================+=================+=================+=================+
   | domain_id       | Yes             | String          | Specifies tags. |
   |                 |                 |                 |                 |
   |                 |                 |                 | Maximum: **36** |
   +-----------------+-----------------+-----------------+-----------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                  |
   +=================+=================+=================+==============================================================+
   | id              | No              | String          | Specifies the resource ID.                                   |
   |                 |                 |                 |                                                              |
   |                 |                 |                 | Maximum: **512**                                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------+
   | name            | No              | String          | Specifies the resource name.                                 |
   |                 |                 |                 |                                                              |
   |                 |                 |                 | Maximum: **256**                                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------+
   | type            | No              | Array           | Specifies resource types in the format of **provider.type**. |
   |                 |                 |                 |                                                              |
   |                 |                 |                 | Array Length: **1 - 100**                                    |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------+
   | region_id       | No              | Array           | Specifies the regions.                                       |
   |                 |                 |                 |                                                              |
   |                 |                 |                 | Array Length: **1 - 10**                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------+
   | ep_id           | No              | Array           | Specifies enterprise project IDs.                            |
   |                 |                 |                 |                                                              |
   |                 |                 |                 | Array Length: **1 - 10**                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------+
   | project_id      | No              | Array           | Specifies the project ID.                                    |
   |                 |                 |                 |                                                              |
   |                 |                 |                 | Array Length: **1 - 10**                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------+
   | tags            | No              | Array           | Specifies tags. The format is **key** or **key=value**.      |
   |                 |                 |                 |                                                              |
   |                 |                 |                 | Array Length: **1 - 5**                                      |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type   | Description                                                                                                                                                    |
   +==================+===========+========+================================================================================================================================================================+
   | X-Security-Token | No        | String | Security token (session token) for temporary security credentials. This parameter is mandatory when you make an API call using temporary security credentials. |
   +------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   =========== ======= ========================================
   Parameter   Type    Description
   =========== ======= ========================================
   total_count Integer Specifies the total number of resources.
   =========== ======= ========================================

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 403**

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

.. code-block:: text

   GET https://{endpoint}/v1/resource-manager/domains/059b5c937100d3e40ff0c00a7675a0a0/all-resources/count

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "total_count" : 345
   }

Status Codes
------------

=========== ===========================
Status Code Description
=========== ===========================
200         Operation succeeded.
400         Invalid parameters.
403         User authentication failed.
500         Server error.
=========== ===========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
