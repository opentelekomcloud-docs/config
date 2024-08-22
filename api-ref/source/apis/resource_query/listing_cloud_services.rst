:original_name: rms_04_0102.html

.. _rms_04_0102:

Listing Cloud Services
======================

Function
--------

Querying cloud services, resources, and regions

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/providers

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------+
   | Parameter       | Mandatory       | Type            | Description     |
   +=================+=================+=================+=================+
   | domain_id       | Yes             | String          | Specifies tags. |
   |                 |                 |                 |                 |
   |                 |                 |                 | Maximum: **36** |
   +-----------------+-----------------+-----------------+-----------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================================================================+
   | offset          | No              | Integer         | Specifies the pagination offset.                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 | Minimum: **1**                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 | Maximum: **1000**                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the maximum number of records to return.                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 | Minimum: **1**                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 | Maximum: **200**                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 | Default: **200**                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | track           | No              | String          | Specifies whether resources are collected by default. **tracked** indicates that resources are collected by default, and **untracked** indicates that resources are not collected by default. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

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

.. table:: **Table 4** Response body parameters

   +--------------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter          | Type                                                                                              | Description                                   |
   +====================+===================================================================================================+===============================================+
   | resource_providers | Array of :ref:`ResourceProviderResponse <rms_04_0102__response_resourceproviderresponse>` objects | Specifies the list of cloud service details.  |
   +--------------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | total_count        | Integer                                                                                           | Specifies the total number of cloud services. |
   +--------------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------+

.. _rms_04_0102__response_resourceproviderresponse:

.. table:: **Table 5** ResourceProviderResponse

   +-----------------------+-------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                      | Description                                                                                                                         |
   +=======================+===========================================================================================+=====================================================================================================================================+
   | provider              | String                                                                                    | Specifies the cloud service name.                                                                                                   |
   +-----------------------+-------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | display_name          | String                                                                                    | Specifies the display name of the cloud service. You can set the language by configuring **X-Language** in the request header.      |
   +-----------------------+-------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | category_display_name | String                                                                                    | Specifies the display name of the cloud service type. You can set the language by configuring **X-Language** in the request header. |
   +-----------------------+-------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | resource_types        | Array of :ref:`ResourceTypeResponse <rms_04_0102__response_resourcetyperesponse>` objects | Specifies the resource type list.                                                                                                   |
   +-----------------------+-------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+

.. _rms_04_0102__response_resourcetyperesponse:

.. table:: **Table 6** ResourceTypeResponse

   +---------------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Type             | Description                                                                                                                                                                                   |
   +=====================+==================+===============================================================================================================================================================================================+
   | name                | String           | Specifies the resource type.                                                                                                                                                                  |
   +---------------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | display_name        | String           | Specifies the display name of the resource type. You can set the language by configuring **X-Language** in the request header.                                                                |
   +---------------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | global              | Boolean          | Specifies whether the resource is a global resource.                                                                                                                                          |
   +---------------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | regions             | Array of strings | Specifies the list of supported regions.                                                                                                                                                      |
   +---------------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | console_endpoint_id | String           | Specifies the console endpoint ID.                                                                                                                                                            |
   +---------------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | console_list_url    | String           | Specifies the URL of the resource list page on the console.                                                                                                                                   |
   +---------------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | console_detail_url  | String           | Specifies the URL of the resource details page on the console.                                                                                                                                |
   +---------------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | track               | String           | Specifies whether resources are collected by default. **tracked** indicates that resources are collected by default, and **untracked** indicates that resources are not collected by default. |
   +---------------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

None

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "total_count" : 2,
     "resource_providers" : [ {
       "provider" : "ecs",
       "display_name" : "ECS",
       "category_display_name" : "Compute",
       "resource_types" : [ {
         "name" : "cloudservers",
         "display_name" : "Cloud servers",
         "global" : false,
         "regions" : [ "regionid1", "regionid2", "regionid3", "regionid4", "regionid5", "regionid6" ],
         "console_endpoint_id" : "ecm",
         "console_list_url" : "#/ecs/manager/vmList",
         "console_detail_url" : "#/ecs/manager/ecsDetail?instanceId={id}",
         "track" : "tracked"
       } ]
     }, {
       "provider" : "vpc",
       "display_name" : "VPC",
       "category_display_name" : "Networking",
       "resource_types" : [ {
         "name" : "vpcs",
         "display_name" : "VPC",
         "global" : false,
         "regions" : [ "regionid1", "regionid2", "regionid3", "regionid4", "regionid5", "regionid6" ],
         "console_endpoint_id" : "vpc",
         "console_list_url" : "#/vpcs",
         "console_detail_url" : "#/vpc/vpcmanager/vpcDetail/subnets?vpcId={id}",
         "track" : "tracked"
       }, {
         "name" : "bandwidths",
         "display_name" : "Shared bandwidth",
         "global" : false,
         "regions" : [ "regionid1", "regionid2", "regionid3", "regionid4", "regionid5", "regionid6" ],
         "console_endpoint_id" : "vpc",
         "console_list_url" : "#/vpc/vpcmanager/shareBandwidth",
         "console_detail_url" : "#/vpc/vpcmanager/shareBandwidth?bandwidthId={id}",
         "track" : "tracked"
       }, {
         "name" : "securityGroups",
         "display_name" : "Security groups",
         "global" : false,
         "regions" : [ "regionid1", "regionid2", "regionid5", "regionid6" ],
         "console_endpoint_id" : "vpc",
         "console_list_url" : "#/secGroups",
         "console_detail_url" : "#/vpc/vpcmanager/sgDetail/sgRules?instanceId={id}",
         "track" : "tracked"
       }, {
         "name" : "publicips",
         "display_name" : "EIPs",
         "global" : false,
         "regions" : [ "regionid1", "regionid2", "regionid3", "regionid4", "regionid6" ],
         "console_endpoint_id" : "vpc",
         "console_list_url" : "#/vpc/vpcmanager/eips",
         "console_detail_url" : "#/vpc/vpcmanager/eipDetailNew?eipId={id}",
         "track" : "tracked"
       } ]
     } ]
   }

Status Codes
------------

=========== ====================
Status Code Description
=========== ====================
200         Operation succeeded.
500         Server error.
=========== ====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
