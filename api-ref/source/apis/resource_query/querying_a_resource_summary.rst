:original_name: rms_04_0108.html

.. _rms_04_0108:

Querying a Resource Summary
===========================

Function
--------

This API is used to query a resource summary.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/all-resources/summary

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

   +-----------+---------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | Parameter | Type                                                                                                    | Description                                         |
   +===========+=========================================================================================================+=====================================================+
   | [items]   | Array of :ref:`ResourceSummaryResponseItem <rms_04_0108__response_resourcesummaryresponseitem>` objects | Specifies the list of resource summary information. |
   +-----------+---------------------------------------------------------------------------------------------------------+-----------------------------------------------------+

.. _rms_04_0108__response_resourcesummaryresponseitem:

.. table:: **Table 5** ResourceSummaryResponseItem

   +-----------+-------------------------------------------------------------+-----------------------------------+
   | Parameter | Type                                                        | Description                       |
   +===========+=============================================================+===================================+
   | provider  | String                                                      | Specifies the cloud service name. |
   +-----------+-------------------------------------------------------------+-----------------------------------+
   | types     | Array of :ref:`types <rms_04_0108__response_types>` objects | Specifies the resource type list. |
   +-----------+-------------------------------------------------------------+-----------------------------------+

.. _rms_04_0108__response_types:

.. table:: **Table 6** types

   +-----------+-----------------------------------------------------------------+------------------------------+
   | Parameter | Type                                                            | Description                  |
   +===========+=================================================================+==============================+
   | type      | String                                                          | Specifies the resource type. |
   +-----------+-----------------------------------------------------------------+------------------------------+
   | regions   | Array of :ref:`regions <rms_04_0108__response_regions>` objects | Specifies the regions.       |
   +-----------+-----------------------------------------------------------------+------------------------------+

.. _rms_04_0108__response_regions:

.. table:: **Table 7** regions

   +-----------+--------+-----------------------------------------------------------------------+
   | Parameter | Type   | Description                                                           |
   +===========+========+=======================================================================+
   | region_id | String | Specifies the region ID.                                              |
   +-----------+--------+-----------------------------------------------------------------------+
   | count     | Long   | Specifies the number of resources of this type in the current region. |
   +-----------+--------+-----------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 8** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 403**

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

.. code-block:: text

   GET https://{endpoint}/v1/resource-manager/domains/059b5c937100d3e40ff0c00a7675a0a0/all-resources/summary

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   [ {
     "provider" : "obs",
     "types" : [ {
       "type" : "buckets",
       "regions" : [ {
         "region_id" : "regionid1",
         "count" : 5
       } ]
     } ]
   }, {
     "provider" : "ecs",
     "types" : [ {
       "type" : "cloudservers",
       "regions" : [ {
         "region_id" : "regionid2",
         "count" : 1
       } ]
     } ]
   } ]

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
