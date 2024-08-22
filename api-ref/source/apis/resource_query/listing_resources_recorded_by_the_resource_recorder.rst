:original_name: rms_04_0109.html

.. _rms_04_0109:

Listing Resources Recorded by the Resource Recorder
===================================================

Function
--------

Querying all resources recorded by the resource recorder. To call this API, you must have the rms:resources:list permission.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/tracked-resources

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
   | region_id        | No              | String          | Specifies the region ID.                                                                             |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Maximum: **36**                                                                                      |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | ep_id            | No              | String          | Specifies the enterprise project ID.                                                                 |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Maximum: **36**                                                                                      |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | type             | No              | String          | Specifies the resource type in the format of **provider.type**.                                      |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Maximum: **40**                                                                                      |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | limit            | No              | Integer         | Specifies the maximum number of resources to return.                                                 |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Minimum: **1**                                                                                       |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Maximum: **200**                                                                                     |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Default: **100**                                                                                     |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | marker           | No              | String          | Specifies the pagination parameter.                                                                  |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Minimum: **4**                                                                                       |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Maximum: **400**                                                                                     |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | id               | No              | String          | Specifies the resource ID.                                                                           |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Maximum: **512**                                                                                     |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | name             | No              | String          | Specifies the resource name.                                                                         |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Maximum: **256**                                                                                     |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | tags             | No              | Array           | Specifies tags. The format is **key** or **key=value**.                                              |
   |                  |                 |                 |                                                                                                      |
   |                  |                 |                 | Array Length: **1 - 5**                                                                              |
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

   +-----------+-------------------------------------------------------------------------------+----------------------------------+
   | Parameter | Type                                                                          | Description                      |
   +===========+===============================================================================+==================================+
   | resources | Array of :ref:`ResourceEntity <rms_04_0109__response_resourceentity>` objects | Specifies the resource list.     |
   +-----------+-------------------------------------------------------------------------------+----------------------------------+
   | page_info | :ref:`PageInfo <rms_04_0109__response_pageinfo>` object                       | Specifies the pagination object. |
   +-----------+-------------------------------------------------------------------------------+----------------------------------+

.. _rms_04_0109__response_resourceentity:

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

.. _rms_04_0109__response_pageinfo:

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

-  Querying all resources in the current account

   .. code-block:: text

      GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/tracked-resources

-  Querying resources in the **default** enterprise project. 100 records are returned by default.

   .. code-block:: text

      GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/tracked-resources?limit=100&ep_id=0

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "resources": [
       {
         "id": "009e9359-70e4-4570-a3a8-69a6c53d5c36",
         "name": "ecs-aziuzko",
         "provider": "evs",
         "type": "volumes",
         "region_id": "eu-de",
         "project_id": "ecabfaea4fd6425ba80d6f8860d8847d",
         "project_name": "eu-de_TSRU",
         "ep_id": "0",
         "ep_name": "default",
         "checksum": "793ebafeb29b2ffdd3df4b018dd9c8e535ea4eba9f19cd6079d7bf998d51c33d",
         "created": "2022-12-21T14:14:43.811Z",
         "updated": "2022-12-21T14:14:50.935Z",
         "provisioning_state": "Succeeded",
         "state": "Normal",
         "tags": {},
         "properties": {
           "shareable": false,
           "volumeType": "SAS",
           "metadata": {
             "readonly": "False",
             "attachedMode": "rw"
           },
           "attachments": [
             {
               "attachedAt": "2022-12-21T14:14:50.879146",
               "volumeId": "009e9359-70e4-4570-a3a8-69a6c53d5c36",
               "id": "009e9359-70e4-4570-a3a8-69a6c53d5c36",
               "attachmentId": "4e84732b-3a7f-43df-9c05-8f5298651ea9",
               "serverId": "d418cc33-dd14-43f7-aa1e-a72ecab1a9b3",
               "device": "/dev/vda"
             }
           ],
           "replicationStatus": "disabled",
           "availabilityZone": "eu-de-01",
           "bootable": "true",
           "userId": "e3b5c19edad843e682a6a21a3b950127",
           "volTenantAttrTenantId": "ecabfaea4fd6425ba80d6f8860d8847d",
           "size": 6,
           "encrypted": false,
           "volumeImageMetadata": {
             "virtualEnvType": "FusionCompute",
             "isregistered": "true",
             "imageSourceType": "uds",
             "supportXenGpuType": "false",
             "minDisk": "6",
             "platform": "Ubuntu",
             "osVersion": "Ubuntu 22.04 server 64bit",
             "minRam": "1024",
             "name": "Standard_Ubuntu_22.04_latest",
             "checksum": "a1733c9887975ed17d6e4a3131f89ab8",
             "osBit": "64",
             "osType": "Linux",
             "containerFormat": "bare",
             "supportXen": "true",
             "id": "e36a291e-5829-470a-9eeb-cb6c31ceddd4",
             "imageSize": "1246982144",
             "supportKvm": "true",
             "diskFormat": "zvhd2",
             "imageType": "gold"
           },
           "volHostAttrHost": "pod01.eu-de-01#1",
           "multiattach": false,
           "status": "in-use"
         }
       }
     ],
     "page_info": {
       "current_count": 1,
       "next_marker": "CAESJgokMDA5ZTkzNTktNzBlNC00NTcwLWEzYTgtNjlhNmM1M2Q1YzM2GgTu_7U_"
     }
   }

Status Codes
------------

=========== ===========================
Status Code Description
=========== ===========================
200         Operation succeeded.
400         Invalid parameter
403         User authentication failed.
500         Server error.
=========== ===========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
