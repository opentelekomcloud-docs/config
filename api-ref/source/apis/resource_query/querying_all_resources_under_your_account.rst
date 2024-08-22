:original_name: rms_04_0104.html

.. _rms_04_0104:

Querying All Resources Under Your Account
=========================================

Function
--------

This API is used to query all resources under your account and you must have the \**rms:resources:list \**permission.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/all-resources

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------+
   | Parameter       | Mandatory       | Type            | Description     |
   +=================+=================+=================+=================+
   | domain_id       | Yes             | String          | Specifies tags. |
   |                 |                 |                 |                 |
   |                 |                 |                 | Maximum: **36** |
   +-----------------+-----------------+-----------------+-----------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                     |
   +=================+=================+=================+=================================================================+
   | region_id       | No              | String          | Specifies the region ID.                                        |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | Maximum: **36**                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
   | ep_id           | No              | String          | Specifies the enterprise project ID.                            |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | Maximum: **36**                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
   | type            | No              | String          | Specifies the resource type in the format of **provider.type**. |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | Maximum: **40**                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the maximum number of resources to return.            |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | Minimum: **1**                                                  |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | Maximum: **200**                                                |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | Default: **100**                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
   | marker          | No              | String          | Specifies the pagination parameter.                             |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | Minimum: **4**                                                  |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | Maximum: **400**                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
   | id              | No              | String          | Specifies the resource ID.                                      |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | Maximum: **512**                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
   | name            | No              | String          | Specifies the resource name.                                    |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | Maximum: **256**                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
   | tags            | No              | Array           | Specifies tags. The format is **key** or **key=value**.         |
   |                 |                 |                 |                                                                 |
   |                 |                 |                 | Array Length: **1 - 5**                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------+

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
   | resources | Array of :ref:`ResourceEntity <rms_04_0104__response_resourceentity>` objects | Specifies the resource list.     |
   +-----------+-------------------------------------------------------------------------------+----------------------------------+
   | page_info | :ref:`PageInfo <rms_04_0104__response_pageinfo>` object                       | Specifies the pagination object. |
   +-----------+-------------------------------------------------------------------------------+----------------------------------+

.. _rms_04_0104__response_resourceentity:

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

.. _rms_04_0104__response_pageinfo:

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

-  Querying all resources under your account

   .. code-block:: text

      GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/all-resources

-  Querying your resources in the **default** enterprise project and setting to return the first 100 records

   .. code-block:: text

      GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/all-resources?limit=100&ep_id=0

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "resources" : [ {
       "id" : "3ccd9191-6a5e-4939-a971-4652db18b370",
       "name" : "elb-265a",
       "provider" : "elb",
       "type" : "loadbalancers",
       "region_id" : "regionid1",
       "project_id" : "05498e12458025102ff5c0061a584a9f",
       "project_name" : "regionid1_region_service",
       "ep_id" : "0",
       "ep_name" : "default",
       "checksum" : "6e0271b107b764b19acb235f45c0d852f72104fe1d4b32970686e7eae8e87bf4",
       "created" : "2020-02-29T09:39:19Z",
       "updated" : "2020-02-29T09:39:19Z",
       "provisioning_state" : "Succeeded",
       "tags" : { },
       "properties" : {
         "tenant_id" : "05498e12458025102ff5c0061a584a9f",
         "listeners" : [ {
           "id" : "37de3be0-1803-43e2-9bb5-243b4b30b771"
         } ],
         "provisioning_status" : "ACTIVE",
         "description" : ""
       }
     }, {
       "id" : "a6e56d05501944d3b2507ba506a43744",
       "name" : "console",
       "provider" : "cdn",
       "type" : "domains",
       "region_id" : "global",
       "project_id" : "",
       "project_name" : "",
       "ep_id" : "0",
       "ep_name" : "default",
       "checksum" : "56afa8b76428f90e9abfbe5cbf33535d8816166114d32eeb119658d6c59eceda",
       "created" : "2020-01-04T13:42:37Z",
       "updated" : "2020-01-15T04:23:01Z",
       "provisioning_state" : "Succeeded",
       "tags" : { },
       "properties" : {
         "domain_name" : "console",
         "domain_status" : "offline",
         "business_type" : "WEB",
         "modify_time" : 1579062181463,
         "cname" : "console"
       }
     } ],
     "page_info" : {
       "current_count" : 2,
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
403         User Authentication failed.
500         Server error.
=========== ===========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
