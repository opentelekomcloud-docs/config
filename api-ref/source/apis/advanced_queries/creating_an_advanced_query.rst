:original_name: rms_04_0702.html

.. _rms_04_0702:

Creating an Advanced Query
==========================

Function
--------

This API is used to create an advanced query.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

POST /v1/resource-manager/domains/{domain_id}/stored-queries

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

   +-----------------+-----------------+-----------------+---------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                           |
   +=================+=================+=================+=======================================+
   | name            | Yes             | String          | Specifies the ResourceQL name.        |
   |                 |                 |                 |                                       |
   |                 |                 |                 | Minimum: **1**                        |
   |                 |                 |                 |                                       |
   |                 |                 |                 | Maximum: **64**                       |
   +-----------------+-----------------+-----------------+---------------------------------------+
   | description     | No              | String          | Specifies the ResourceQL description. |
   |                 |                 |                 |                                       |
   |                 |                 |                 | Minimum: **0**                        |
   |                 |                 |                 |                                       |
   |                 |                 |                 | Maximum: **512**                      |
   +-----------------+-----------------+-----------------+---------------------------------------+
   | expression      | Yes             | String          | Specifies the ResourceQL expression.  |
   |                 |                 |                 |                                       |
   |                 |                 |                 | Minimum: **1**                        |
   |                 |                 |                 |                                       |
   |                 |                 |                 | Maximum: **4096**                     |
   +-----------------+-----------------+-----------------+---------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                               |
   +=======================+=======================+===========================================================================================================================================================================================================================================================================+
   | id                    | String                | ResourceQL ID.                                                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                           |
   |                       |                       | Maximum: **256**                                                                                                                                                                                                                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the ResourceQL name.                                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                           |
   |                       |                       | Minimum: **1**                                                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                           |
   |                       |                       | Maximum: **64**                                                                                                                                                                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Indicates a customized query type. The options are **account** and **aggregator**. account: customized query statement for a single account; If the value is aggregator, it indicates the customized query statement of the aggregator. The default value is **account**. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Specifies the ResourceQL description.                                                                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                                           |
   |                       |                       | Minimum: **0**                                                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                           |
   |                       |                       | Maximum: **512**                                                                                                                                                                                                                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | expression            | String                | Specifies the ResourceQL expression.                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                           |
   |                       |                       | Minimum: **1**                                                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                           |
   |                       |                       | Maximum: **4096**                                                                                                                                                                                                                                                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created               | String                | Specifies when ResourceQL was created.                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                           |
   |                       |                       | Minimum: **1**                                                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                           |
   |                       |                       | Maximum: **64**                                                                                                                                                                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated               | String                | Specifies when ResourceQL was updated.                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                           |
   |                       |                       | Minimum: **1**                                                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                           |
   |                       |                       | Maximum: **64**                                                                                                                                                                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

Creating an advanced query to query stopped ECSs

.. code-block:: text

   POST https://{endpoint}/v1/resource-manager/domains/{domain_id}/stored-queries

   {
     "name" : "stopped-ecs",
     "description" : "Querying stopped ECSs",
     "expression" : "SELECT id, name FROM resources WHERE provider = 'ecs' AND type = 'cloudservers' AND properties.status = 'SHUTOFF'"
   }

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "id" : "62b9126566d400721efceffa",
     "name" : "stopped-ecs",
     "type": "account",
     "description" : "Querying stopped ECSs",
     "expression" : "SELECT id, name FROM resources WHERE provider = 'ecs' AND type = 'cloudservers' AND properties.status = 'SHUTOFF'",
     "created" : "2022-06-27T02:13:57.107Z",
     "updated" : "2022-06-27T02:13:57.107Z"
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
