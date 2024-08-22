:original_name: rms_04_0101.html

.. _rms_04_0101:

Querying Resources of a Specific Type
=====================================

Function
--------

This API is used to query specified resources.To call this API, you must have the **rms:resources:list** permission. For example,if you need to query the ecs.cloudservers resource type, set the **provider** to **ecs**, and **type** to **cloudservers** in the API request. For details about the cloud services (provider) and resource types (type), see the Supported Services and Resource Types section in the appendix.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/provider/{provider}/type/{type}/resources

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------------------------+
   | Parameter       | Mandatory       | Type            | Description                       |
   +=================+=================+=================+===================================+
   | domain_id       | Yes             | String          | Specifies tags.                   |
   |                 |                 |                 |                                   |
   |                 |                 |                 | Maximum: **36**                   |
   +-----------------+-----------------+-----------------+-----------------------------------+
   | provider        | Yes             | String          | Specifies the cloud service name. |
   |                 |                 |                 |                                   |
   |                 |                 |                 | Maximum: **20**                   |
   +-----------------+-----------------+-----------------+-----------------------------------+
   | type            | Yes             | String          | Specifies the resource type.      |
   |                 |                 |                 |                                   |
   |                 |                 |                 | Maximum: **32**                   |
   +-----------------+-----------------+-----------------+-----------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+--------------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type               | Description                                        |
   +=================+=================+====================+====================================================+
   | region_id       | No              | String             | Specifies the region ID.                           |
   |                 |                 |                    |                                                    |
   |                 |                 |                    | Maximum: **36**                                    |
   +-----------------+-----------------+--------------------+----------------------------------------------------+
   | ep_id           | No              | String             | Specifies the enterprise project ID.               |
   |                 |                 |                    |                                                    |
   |                 |                 |                    | Maximum: **36**                                    |
   +-----------------+-----------------+--------------------+----------------------------------------------------+
   | tag             | No              | Map<String,String> | Specifies the tag.                                 |
   +-----------------+-----------------+--------------------+----------------------------------------------------+
   | limit           | No              | Integer            | Specifies the maximum number of records to return. |
   |                 |                 |                    |                                                    |
   |                 |                 |                    | Minimum: **1**                                     |
   |                 |                 |                    |                                                    |
   |                 |                 |                    | Maximum: **200**                                   |
   |                 |                 |                    |                                                    |
   |                 |                 |                    | Default: **200**                                   |
   +-----------------+-----------------+--------------------+----------------------------------------------------+
   | marker          | No              | String             | Specifies the pagination parameter.                |
   |                 |                 |                    |                                                    |
   |                 |                 |                    | Minimum: **4**                                     |
   |                 |                 |                    |                                                    |
   |                 |                 |                    | Maximum: **400**                                   |
   +-----------------+-----------------+--------------------+----------------------------------------------------+

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

   +-----------+-------------------------------------------------------------------------------+----------------------------------+
   | Parameter | Type                                                                          | Description                      |
   +===========+===============================================================================+==================================+
   | resources | Array of :ref:`ResourceEntity <rms_04_0101__response_resourceentity>` objects | Specifies the resource list.     |
   +-----------+-------------------------------------------------------------------------------+----------------------------------+
   | page_info | :ref:`PageInfo <rms_04_0101__response_pageinfo>` object                       | Specifies the pagination object. |
   +-----------+-------------------------------------------------------------------------------+----------------------------------+

.. _rms_04_0101__response_resourceentity:

.. table:: **Table 5** ResourceEntity

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                   |
   +=======================+=======================+===============================================================================================================================================================+
   | id                    | String                | Specifies the resource ID.                                                                                                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the resource name.                                                                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | provider              | String                | Specifies the cloud service name.                                                                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Specifies the resource type.                                                                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | region_id             | String                | Specifies the region ID.                                                                                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                | Specifies the project ID in IaaS OpenStack.                                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_name          | String                | Specifies the project name in IaaS OpenStack.                                                                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ep_id                 | String                | Specifies the enterprise project ID.                                                                                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ep_name               | String                | Specifies the name of an enterprise project.                                                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | checksum              | String                | Specifies the resource checksum.                                                                                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created               | String                | Specifies the time when the resource was created.                                                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated               | String                | Specifies the time when the resource was updated.                                                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | provisioning_state    | String                | Specifies the status of a resource operation.                                                                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | state                 | String                | Resource state. The value can be normal or deleted.                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Map<String,String>    | Specifies the resource tag.                                                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | properties            | Map<String,Object>    | Specifies the detailed properties of the resource.                                                                                                            |
   |                       |                       |                                                                                                                                                               |
   |                       |                       | Resource attributes vary based on different resources. For details about resource attribute parameter description, see the documentation of related services. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _rms_04_0101__response_pageinfo:

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

Querying all VMs in current account

.. code-block:: text

   GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/provider/ecs/type/cloudServers/resources

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "page_info" : {
       "current_count" : 2,
       "next_marker" : null
     },
     "resources" : [ {
       "checksum" : "89ca775e88e04b2c200ccbf9e219ad0d7da42e3f446e5c953d443288134eec41",
       "created" : "2020-02-21T08:41:05Z",
       "ep_id" : "0",
       "ep_name" : "default",
       "id" : "7ffd8564-d88a-4bc9-ab51-d8b79a57d0e6",
       "name" : "ecs-test-1",
       "project_id" : "059b5e0a2500d5552fa1c00adada8c06",
       "project_name" : "project_name",
       "properties" : {
         "status" : "ACTIVE"
       },
       "provider" : "ecs",
       "provisioning_state" : "Succeeded",
       "region_id" : "regionid1",
       "tags" : {
         "use" : "test"
       },
       "type" : "cloudServers",
       "updated" : "2020-02-21T08:41:05Z"
     }, {
       "checksum" : "db2aad42804951c03a724b7501da9b6b4c14d319dd319d76bb7c658f256a37b0",
       "created" : "2020-02-24T08:43:05Z",
       "ep_id" : "0",
       "ep_name" : "default",
       "id" : "b63b33b7-f48c-4048-995b-0445d124a445",
       "name" : "ecs-test-2",
       "project_id" : "059b5e0a2500d5552fa1c00adada8c06",
       "project_name" : "project_name_1",
       "properties" : {
         "status" : "ACTIVE"
       },
       "provider" : "ecs",
       "provisioning_state" : "Succeeded",
       "region_id" : "regionid1",
       "tags" : {
         "use" : "test1"
       },
       "type" : "cloudServers",
       "updated" : "2020-08-11T11:55:08Z"
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
500         Sever error.
=========== ===========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
