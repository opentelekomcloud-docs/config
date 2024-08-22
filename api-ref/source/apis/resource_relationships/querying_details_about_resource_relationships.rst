:original_name: rms_04_0302.html

.. _rms_04_0302:

Querying Details About Resource Relationships
=============================================

Function
--------

This API is used to query the relationship between a resource and other resources by the resource ID. The relationship direction can be **in** or **out**. An IAM user needs to have the **rms:resources:getRelation** permissions to call this API. Resource relationships depend on enabling resource recorder.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/all-resources/{resource_id}/relations

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+----------------------------+
   | Parameter       | Mandatory       | Type            | Description                |
   +=================+=================+=================+============================+
   | domain_id       | Yes             | String          | Specifies tags.            |
   |                 |                 |                 |                            |
   |                 |                 |                 | Maximum: **36**            |
   +-----------------+-----------------+-----------------+----------------------------+
   | resource_id     | Yes             | String          | Specifies the resource ID. |
   |                 |                 |                 |                            |
   |                 |                 |                 | Maximum: **512**           |
   +-----------------+-----------------+-----------------+----------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                         |
   +=================+=================+=================+=====================================================+
   | direction       | Yes             | String          | Specifies the direction of a resource relationship. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------+
   | limit           | No              | Integer         | Specifies the maximum number of records to return.  |
   |                 |                 |                 |                                                     |
   |                 |                 |                 | Minimum: **1**                                      |
   |                 |                 |                 |                                                     |
   |                 |                 |                 | Maximum: **1000**                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------+
   | marker          | No              | String          | Specifies the pagination parameter.                 |
   |                 |                 |                 |                                                     |
   |                 |                 |                 | Minimum: **4**                                      |
   |                 |                 |                 |                                                     |
   |                 |                 |                 | Maximum: **400**                                    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------+

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

   +-----------+-----------------------------------------------------------------------------------+---------------------------------------------------+
   | Parameter | Type                                                                              | Description                                       |
   +===========+===================================================================================+===================================================+
   | relations | Array of :ref:`ResourceRelation <rms_04_0302__response_resourcerelation>` objects | Specifies the list of the resource relationships. |
   +-----------+-----------------------------------------------------------------------------------+---------------------------------------------------+
   | page_info | :ref:`PageInfo <rms_04_0302__response_pageinfo>` object                           | Specifies the pagination object.                  |
   +-----------+-----------------------------------------------------------------------------------+---------------------------------------------------+

.. _rms_04_0302__response_resourcerelation:

.. table:: **Table 5** ResourceRelation

   +--------------------+--------+-------------------------------------------------+
   | Parameter          | Type   | Description                                     |
   +====================+========+=================================================+
   | relation_type      | String | Specifies the relationship type.                |
   +--------------------+--------+-------------------------------------------------+
   | from_resource_type | String | Specifies the type of the source resource.      |
   +--------------------+--------+-------------------------------------------------+
   | to_resource_type   | String | Specifies the type of the destination resource. |
   +--------------------+--------+-------------------------------------------------+
   | from_resource_id   | String | Specifies the ID of the source resource.        |
   +--------------------+--------+-------------------------------------------------+
   | to_resource_id     | String | Specifies the ID of the destination resource.   |
   +--------------------+--------+-------------------------------------------------+

.. _rms_04_0302__response_pageinfo:

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

**Status code: 404**

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

   GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/all-resources/{resource_id}/relations?direction=out

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "relations" : [ {
       "relation_type" : "isAttachedTo",
       "from_resource_type" : "ecs.cloudservers",
       "to_resource_type" : "evs.volumes",
       "from_resource_id" : "6af96128-d58d-426c-91e0-b38144c0f112",
       "to_resource_id" : "0075ed19-59dd-49be-961d-117bb6fbfd3e"
     }, {
       "relation_type" : "contains",
       "from_resource_type" : "ecs.cloudservers",
       "to_resource_type" : "vpc.publicips",
       "from_resource_id" : "6af96128-d58d-426c-91e0-b38144c0f112",
       "to_resource_id" : "3813d6d3-ef88-47b1-b343-cdf6390c6dcb"
     }, {
       "relation_type" : "isAssociatedWith",
       "from_resource_type" : "ecs.cloudservers",
       "to_resource_type" : "vpc.securityGroups",
       "from_resource_id" : "6af96128-d58d-426c-91e0-b38144c0f112",
       "to_resource_id" : "8cca3002-00af-4812-a853-b7a6fbee06a4"
     }, {
       "relation_type" : "isAttachedTo",
       "from_resource_type" : "ecs.cloudservers",
       "to_resource_type" : "evs.volumes",
       "from_resource_id" : "6af96128-d58d-426c-91e0-b38144c0f112",
       "to_resource_id" : "f4a107eb-4c6d-4dc8-88d8-de337923956f"
     }, {
       "relation_type" : "isContainedIn",
       "from_resource_type" : "ecs.cloudservers",
       "to_resource_type" : "vpc.vpcs",
       "from_resource_id" : "6af96128-d58d-426c-91e0-b38144c0f112",
       "to_resource_id" : "ff13d70d-17e5-4ec8-945a-c874e0db99d3"
     } ],
     "page_info" : {
       "current_count" : 5,
       "next_marker" : null
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
404         Resources not found.
500         Server error.
=========== ===========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
