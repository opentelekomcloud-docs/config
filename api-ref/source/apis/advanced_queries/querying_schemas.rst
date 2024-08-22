:original_name: rms_04_0707.html

.. _rms_04_0707:

Querying Schemas
================

Function
--------

This API is used to query schemas used by advanced queries.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/schemas

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------+
   | Parameter       | Mandatory       | Type            | Description     |
   +=================+=================+=================+=================+
   | domain_id       | Yes             | String          | Specifies tags. |
   |                 |                 |                 |                 |
   |                 |                 |                 | Maximum: **36** |
   +-----------------+-----------------+-----------------+-----------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                        |
   +=================+=================+=================+====================================================+
   | limit           | No              | Integer         | Specifies the maximum number of records to return. |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Minimum: **1**                                     |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Maximum: **200**                                   |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Default: **200**                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | marker          | No              | String          | Specifies the pagination parameter.                |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Minimum: **4**                                     |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Maximum: **400**                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

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

   +-----------+-----------------------------------------------------------------------------------------------+----------------------------------+
   | Parameter | Type                                                                                          | Description                      |
   +===========+===============================================================================================+==================================+
   | value     | Array of :ref:`ResourceSchemaResponse <rms_04_0707__response_resourceschemaresponse>` objects | schemas object.                  |
   +-----------+-----------------------------------------------------------------------------------------------+----------------------------------+
   | page_info | :ref:`PageInfo <rms_04_0707__response_pageinfo>` object                                       | Specifies the pagination object. |
   +-----------+-----------------------------------------------------------------------------------------------+----------------------------------+

.. _rms_04_0707__response_resourceschemaresponse:

.. table:: **Table 5** ResourceSchemaResponse

   ========= ====== =============================
   Parameter Type   Description
   ========= ====== =============================
   type      String Specifies the resource type.
   schema    Object Specifies the schema content.
   ========= ====== =============================

.. _rms_04_0707__response_pageinfo:

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

None

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "value": [
       {
         "type": "aad.instances",
         "schema": {
           "vips": {
             "__array": {
               "ipId": "string",
               "ip": "string"
             }
           },
           "expireTime": "int",
           "ispSpec": "string",
           "specType": "int",
           "basicBandwidth": "int",
           "elasticBandwidth": "int",
           "serviceBandwidth": "int",
           "isAutoRenew": "int"
         }
       }
     ],
     "page_info": {
       "current_count": 1,
       "next_marker": "MDAwMDY2ODM5NjUy"
     }
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
