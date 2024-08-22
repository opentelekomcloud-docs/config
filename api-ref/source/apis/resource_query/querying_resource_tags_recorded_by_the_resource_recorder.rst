:original_name: rms_04_0111.html

.. _rms_04_0111:

Querying resource tags recorded by the resource recorder
========================================================

Function
--------

Querying resource tags recorded by the resource recorder in the current account

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/tracked-resources/tags

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------+
   | Parameter       | Mandatory       | Type            | Description     |
   +=================+=================+=================+=================+
   | domain_id       | Yes             | String          | Specifies tags. |
   |                 |                 |                 |                 |
   |                 |                 |                 | Maximum: **36** |
   +-----------------+-----------------+-----------------+-----------------+

.. table:: **Table 2** Query Parameters

   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                          |
   +==================+=================+=================+======================================================================================================+
   | key              | No              | String          | Specifies the name of the tag key.                                                                   |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Maximum: **128**                                                                                     |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | marker           | No              | String          | Specifies the pagination parameter.                                                                  |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Minimum: **4**                                                                                       |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Maximum: **400**                                                                                     |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | limit            | No              | Integer         | Specifies the maximum number of resources to return.                                                 |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Minimum: **1**                                                                                       |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Maximum: **200**                                                                                     |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Default: **100**                                                                                     |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | resource_deleted | No              | Boolean         | Indicating whether deleted resources need to be returned. This parameter is set to false by default. |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Default: **false**                                                                                   |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+

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

   +-----------+---------------------------------------------------------------------+----------------------------------+
   | Parameter | Type                                                                | Description                      |
   +===========+=====================================================================+==================================+
   | tags      | Array of :ref:`TagEntity <rms_04_0111__response_tagentity>` objects | Specifies tags.                  |
   +-----------+---------------------------------------------------------------------+----------------------------------+
   | page_info | :ref:`PageInfo <rms_04_0111__response_pageinfo>` object             | Specifies the pagination object. |
   +-----------+---------------------------------------------------------------------+----------------------------------+

.. _rms_04_0111__response_tagentity:

.. table:: **Table 5** TagEntity

   ========= ================ ======================
   Parameter Type             Description
   ========= ================ ======================
   key       String           Specifies the tag key.
   value     Array of strings Specifies tag values.
   ========= ================ ======================

.. _rms_04_0111__response_pageinfo:

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

Querying resource tags recorded by the resource recorder in the current account

.. code-block:: text

   GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/tracked-resources/tags

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "tags" : [ {
       "key" : "chloe",
       "value" : [ "a", "b" ]
     } ]
   }

Status Codes
------------

=========== ===========================
Status Code Description
=========== ===========================
200         Operation succeeded.
400         Invalid parameter.
403         User authentication failed.
500         Server error.
=========== ===========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
