:original_name: rms_04_0113.html

.. _rms_04_0113:

Querying a specific resource recorded by the resource recorder
==============================================================

Function
--------

Querying a specific resource recorded by the resource recorder in the current account

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/tracked-resources/{resource_id}

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

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

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 403**

.. table:: **Table 5** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 500**

.. table:: **Table 6** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

Example Requests
----------------

Querying a specific resource recorded by the resource recorder in the current account

.. code-block:: text

   GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/tracked-resources/{resource_id}

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

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
