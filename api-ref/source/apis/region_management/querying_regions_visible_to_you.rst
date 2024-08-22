:original_name: rms_04_0601.html

.. _rms_04_0601:

Querying Regions Visible to You
===============================

Function
--------

This API is used to query regions visible to you.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/regions

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

.. table:: **Table 3** Response body parameters

   +-----------+---------------------------------------------------------------+-------------------------------------------+
   | Parameter | Type                                                          | Description                               |
   +===========+===============================================================+===========================================+
   | value     | Array of :ref:`Region <rms_04_0601__response_region>` objects | Specifies the list of region information. |
   +-----------+---------------------------------------------------------------+-------------------------------------------+

.. _rms_04_0601__response_region:

.. table:: **Table 4** Region

   ============ ====== ===========================
   Parameter    Type   Description
   ============ ====== ===========================
   region_id    String Specifies the region ID.
   display_name String Specifies the display name.
   ============ ====== ===========================

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

**Status code: 404**

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

None

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "value" : [ {
       "region_id" : "regionid1",
       "display_name" : "region1"
     }, {
       "region_id" : "regionid2",
       "display_name" : "region2"
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
404         User not found.
500         Server error.
=========== ===========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
