:original_name: rms_04_0401.html

.. _rms_04_0401:

Querying Change Records of a Resource
=====================================

Function
--------

This API is used to query change records of a resource and its relationships with other resources.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/resources/{resource_id}/history

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

   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                                |
   +=====================+=================+=================+============================================================================================================+
   | marker              | No              | String          | Specifies the pagination parameter.                                                                        |
   |                     |                 |                 |                                                                                                            |
   |                     |                 |                 | Minimum: **4**                                                                                             |
   |                     |                 |                 |                                                                                                            |
   |                     |                 |                 | Maximum: **400**                                                                                           |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+
   | limit               | No              | Integer         | Specifies the maximum number of records to return.                                                         |
   |                     |                 |                 |                                                                                                            |
   |                     |                 |                 | Minimum: **1**                                                                                             |
   |                     |                 |                 |                                                                                                            |
   |                     |                 |                 | Maximum: **200**                                                                                           |
   |                     |                 |                 |                                                                                                            |
   |                     |                 |                 | Default: **200**                                                                                           |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+
   | earlier_time        | No              | Long            | Specifies the start time of the query. If this parameter is not set, the earliest time is used by default. |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+
   | later_time          | No              | Long            | Specifies the end time of the query. If this parameter is not set, the current time is used by default.    |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+
   | chronological_order | No              | String          | Specifies the time sequence of the data to be returned. The default value is **Reverse**.                  |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+

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

   +-----------+-------------------------------------------------------------------------+-----------------------------------------+
   | Parameter | Type                                                                    | Description                             |
   +===========+=========================================================================+=========================================+
   | items     | Array of :ref:`HistoryItem <rms_04_0401__response_historyitem>` objects | Specifies the list of resource history. |
   +-----------+-------------------------------------------------------------------------+-----------------------------------------+
   | page_info | :ref:`PageInfo <rms_04_0401__response_pageinfo>` object                 | Specifies the pagination object.        |
   +-----------+-------------------------------------------------------------------------+-----------------------------------------+

.. _rms_04_0401__response_historyitem:

.. table:: **Table 5** HistoryItem

   +---------------+-----------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter     | Type                                                                              | Description                                        |
   +===============+===================================================================================+====================================================+
   | domain_id     | String                                                                            | Specifies the user ID.                             |
   +---------------+-----------------------------------------------------------------------------------+----------------------------------------------------+
   | resource_id   | String                                                                            | Specifies the resource ID.                         |
   +---------------+-----------------------------------------------------------------------------------+----------------------------------------------------+
   | resource_type | String                                                                            | Specifies the resource type.                       |
   +---------------+-----------------------------------------------------------------------------------+----------------------------------------------------+
   | capture_time  | String                                                                            | Specifies the time when the resource was captured. |
   +---------------+-----------------------------------------------------------------------------------+----------------------------------------------------+
   | status        | String                                                                            | Specifies the resource status.                     |
   +---------------+-----------------------------------------------------------------------------------+----------------------------------------------------+
   | relations     | Array of :ref:`ResourceRelation <rms_04_0401__response_resourcerelation>` objects | Specifies the list of the resource relationships.  |
   +---------------+-----------------------------------------------------------------------------------+----------------------------------------------------+
   | resource      | :ref:`ResourceEntity <rms_04_0401__response_resourceentity>` object               | Specifies the resource object.                     |
   +---------------+-----------------------------------------------------------------------------------+----------------------------------------------------+

.. _rms_04_0401__response_resourcerelation:

.. table:: **Table 6** ResourceRelation

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

.. _rms_04_0401__response_resourceentity:

.. table:: **Table 7** ResourceEntity

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
   | osType                | String                | Specifies the OS type of the cloud server. The value can be **Linux** or **Windows**.                                                                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keyName               | String                | Specifies the key pair that is used to authenticate an ECS.                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | schedulerHints        | Object                | Specifies the ECS scheduling information.                                                                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 8** Description of some key ECS attributes

   +----------------+--------+-------------------------------------------------------------+
   | Parameter      | Type   | Description                                                 |
   +================+========+=============================================================+
   | osType         | String | Specifies the OS type. The value can be Linux or Windows.   |
   +----------------+--------+-------------------------------------------------------------+
   | keyName        | String | Specifies the key pair that is used to authenticate an ECS. |
   +----------------+--------+-------------------------------------------------------------+
   | schedulerHints | Object | Specifies the ECS scheduling information.                   |
   +----------------+--------+-------------------------------------------------------------+

.. _rms_04_0401__response_pageinfo:

.. table:: **Table 9** PageInfo

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

.. table:: **Table 10** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 403**

.. table:: **Table 11** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 500**

.. table:: **Table 12** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

Example Requests
----------------

.. code-block:: text

   GET /v1/resource-manager/domains/{domain_id}/resources/{resource_id}/history?earlier_time=1595865600000&later_time=1603875761000&limit=10

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "items": [
      {
       "domain_id": "daf2557fc0de4da09e128441baa71697",
       "resource_id": "d418cc33-dd14-43f7-aa1e-a72ecab1a9b3",
       "resource_type": "ecs.cloudservers",
       "capture_time": "2024-01-30T11:51:30.029Z",
       "status": "ResourceChanged.CREATE",
       "relations": [
        {
         "relation_type": "isAttachedTo",
         "from_resource_type": "ecs.cloudservers",
         "to_resource_type": "vpc.publicips",
         "from_resource_id": "d418cc33-dd14-43f7-aa1e-a72ecab1a9b3",
         "to_resource_id": "f1c02dc1-0127-434d-ab87-7ed623e0229b"
        },
        {
         "relation_type": "isAttachedTo",
         "from_resource_type": "ecs.cloudservers",
         "to_resource_type": "evs.volumes",
         "from_resource_id": "d418cc33-dd14-43f7-aa1e-a72ecab1a9b3",
         "to_resource_id": "009e9359-70e4-4570-a3a8-69a6c53d5c36"
        },
        {
         "relation_type": "isContainedIn",
         "from_resource_type": "ecs.cloudservers",
         "to_resource_type": "vpc.vpcs",
         "from_resource_id": "d418cc33-dd14-43f7-aa1e-a72ecab1a9b3",
         "to_resource_id": "574967f6-17f0-49f2-bec0-ecc6736b2d8b"
        },
        {
         "relation_type": "isAssociatedWith",
         "from_resource_type": "ecs.cloudservers",
         "to_resource_type": "vpc.securityGroups",
         "from_resource_id": "d418cc33-dd14-43f7-aa1e-a72ecab1a9b3",
         "to_resource_id": "c33525f6-e38b-4c92-8ad6-c12453e3123c"
        }
       ],
       "resource": {
        "id": "d418cc33-dd14-43f7-aa1e-a72ecab1a9b3",
        "name": "ecs-aziuzko",
        "provider": "ecs",
        "type": "cloudservers",
        "region_id": "eu-de",
        "project_id": "ecabfaea4fd6425ba80d6f8860d8847d",
        "project_name": "eu-de_TSRU",
        "ep_id": "0",
        "ep_name": "default",
        "checksum": "7ad9076c6d08decd7185d271e45e8908c3901a732f2a19fc4429e54cf9b58029",
        "created": "2022-12-21T14:14:41Z",
        "updated": "2024-01-30T11:51:24Z",
        "provisioning_state": "Succeeded",
        "state": null,
        "tags": {},
        "properties": {
         "accessIpv4": "",
         "hostName": "ecs-aziuzko",
         "addresses": [
          {
           "OsExtIpsType": "fixed",
           "OsExtIpsPortId": "0aa69070-db1e-45b6-92cc-834094a11205",
           "addr": "192.168.0.60",
           "version": 4,
           "OsExtIpsMacAddr": "fa:16:3e:13:6a:a6"
          },
          {
           "OsExtIpsType": "floating",
           "OsExtIpsPortId": "0aa69070-db1e-45b6-92cc-834094a11205",
           "addr": "80.158.1.160",
           "version": 4,
           "OsExtIpsMacAddr": "fa:16:3e:13:6a:a6"
          }
         ],
         "accessIpv6": "",
         "metadata": {
          "chargingMode": "0",
          "meteringImageType": "gold",
          "imageName": "Standard_Ubuntu_22.04_latest",
          "meteringImageId": "e36a291e-5829-470a-9eeb-cb6c31ceddd4",
          "meteringResourcesPerCode": "s2.medium.1.linux",
          "vpcId": "574967f6-17f0-49f2-bec0-ecc6736b2d8b",
          "osBit": "64",
          "osType": "Linux"
         },
         "OsExtStsVmState": "active",
         "configDrive": "",
         "OsExtStsPowerState": 1,
         "keyName": "KeyPair-aziuzko",
         "hostId": "0734968b9c1964107d56ba088571a7cb0f2ec7287f2f1d63632e3efb",
         "securityGroup": [
          {
           "name": "default",
           "id": "c33525f6-e38b-4c92-8ad6-c12453e3123c"
          }
         ],
         "ExtVolumesAttached": [
          {
           "bootIndex": "0",
           "id": "009e9359-70e4-4570-a3a8-69a6c53d5c36",
           "device": "/dev/vda"
          }
         ],
         "userId": "e3b5c19edad843e682a6a21a3b950127",
         "flavor": {
          "disk": "0",
          "name": "s2.medium.1",
          "id": "s2.medium.1",
          "vcpus": "1",
          "ram": "1024"
         },
         "osextsrvattr": {
          "hostName": "ecs-aziuzko",
          "kernelId": "",
          "ramdiskId": "",
          "reservationId": "r-t09j8st1",
          "instanceName": "instance-003bddff",
          "host": "734968b9c1964107d56ba088571a7cb0f2ec7287f2f1d63632e3efb",
          "rootDeviceName": "/dev/vda",
          "hypervisorHostName": "804f5144c8aac87590118896ba9aa6068d902e3b8f96a4d3f9e2fa0b",
          "launchIndex": 0
         },
         "OsDcfDiskConfig": "MANUAL",
         "hostStatus": "UP",
         "OsSrvUsgLaunchedAt": "2022-12-21T14:14:55.000000",
         "OsExtAz": "eu-de-01",
         "progress": 0,
         "locked": false,
         "OS-EXT-SRV-ATTR": {
          "hostName": "ecs-aziuzko",
          "kernelId": "",
          "ramdiskId": "",
          "reservationId": "r-t09j8st1",
          "instanceName": "instance-003bddff",
          "host": "734968b9c1964107d56ba088571a7cb0f2ec7287f2f1d63632e3efb",
          "rootDeviceName": "/dev/vda",
          "hypervisorHostName": "804f5144c8aac87590118896ba9aa6068d902e3b8f96a4d3f9e2fa0b",
          "launchIndex": 0
         },
         "status": "ACTIVE",
         "schedulerHints": {}
        }
       }
      }
     ],
     "page_info": {
      "current_count": 1,
      "next_marker": null
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
