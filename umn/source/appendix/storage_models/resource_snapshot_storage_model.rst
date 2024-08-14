:original_name: rms_06_0400.html

.. _rms_06_0400:

Resource Snapshot Storage Model
===============================


Resource Snapshot Storage Model
-------------------------------

.. table:: **Table 1** Resource snapshot storage model

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                        |
   +=======================+=======================+====================================================================================================================+
   | snapshot_id           | String                | Specifies the resource snapshot ID.                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | items                 | Array of Object       | Specifies the list of the resource snapshot items.                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | snapshot_time         | String                | Specifies the time when the resource snapshot was stored.                                                          |
   |                       |                       |                                                                                                                    |
   |                       |                       | **snapshot_time** is a UTC time in a fixed format complying with ISO-8601 (for example, **2018-11-14T08:59:14Z**). |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Items parameters

   +-----------+-----------------+-------------------------------------------------------+
   | Parameter | Type            | Description                                           |
   +===========+=================+=======================================================+
   | resource  | Object          | Specifies the resource.                               |
   +-----------+-----------------+-------------------------------------------------------+
   | relations | Array of Object | Specifies the item list of the resource relationship. |
   +-----------+-----------------+-------------------------------------------------------+

.. table:: **Table 3** **resource** parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                  |
   +=======================+=======================+==============================================================================================================+
   | id                    | String                | Specifies the resource ID.                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the resource name.                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | provider              | String                | Specifies the cloud service name.                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Specifies the cloud resource type.                                                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | region_id             | String                | Specifies the ID of the region where the resource is located.                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | project_id            | String                | Specifies the IAM project ID.                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | project_name          | String                | Specifies the IAM project name.                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | ep_id                 | String                | Specifies the enterprise project ID.                                                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | ep_name               | String                | Specifies the enterprise project name.                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | checksum              | String                | Specifies the checksum.                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | created               | String                | Specifies the time when the cloud resource was created.                                                      |
   |                       |                       |                                                                                                              |
   |                       |                       | **created** is a UTC time in a fixed format complying with ISO-8601 (for example, **2018-11-14T08:59:14Z**). |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | updated               | String                | The time when the resource was last updated.                                                                 |
   |                       |                       |                                                                                                              |
   |                       |                       | **updated** is a UTC time in a fixed format complying with ISO-8601 (for example, **2018-11-14T08:59:14Z**). |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | provisioning_state    | String                | Specifies the result of an operation on resources.                                                           |
   |                       |                       |                                                                                                              |
   |                       |                       | The value can be:                                                                                            |
   |                       |                       |                                                                                                              |
   |                       |                       | -  Succeeded: The operation is successful.                                                                   |
   |                       |                       | -  Failed: The operation fails.                                                                              |
   |                       |                       | -  Canceled: The operation is canceled.                                                                      |
   |                       |                       | -  Processing: The operation is in progress.                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | tags                  | Map                   | Specifies the cloud resource tags.                                                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | properties            | Map                   | Specifies the cloud resource attributes.                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** Relations parameters

   ================== ====== ==============================================
   Parameter          Type   Description
   ================== ====== ==============================================
   from_resource_id   String Specifies the ID of the source resource.
   to_resource_id     String Specifies the ID of the associated resource.
   from_resource_type String Specifies the type of the source resource.
   to_resource_type   String Specifies the type of the associated resource.
   relation_type      String Specifies the resource relationship type.
   ================== ====== ==============================================

Resource Snapshot Storage Example
---------------------------------

.. code-block::

   {
     "items": [
       {
         "resource": {
           "id": "c25ee8b3-c907-4cd4-9869-6c4b07c61a0b",
           "name": "rse-cdk-07-cdk-3sbz",
           "provider": "vpc",
           "type": "securityGroups",
           "region_id": "eu-de",
           "project_id": "fc6d40abe7e54492b7c7aa5a29d6cbab",
           "project_name": "demo_project",
           "ep_id": "0",
           "ep_name": "default",
           "checksum": "4098715092c762b3eafe25be8eeda33a10b547033f9d59b6e18f5a960a1f805d",
           "updated": "2020-05-25T10:27:17.000Z",
           "created": "2020-05-25T10:27:17.000Z",
           "provisioning_state": "Succeeded",
           "tags": {},
           "properties": {}
         },
         "relations": [
           {
             "from_resource_id": "c25ee8b3-c907-4cd4-9869-6c4b07c61a0b",
             "to_resource_id": "0088a276-162b-4f07-aa40-f6ed8b801ca1",
             "from_resource_type": "vpc.securityGroups",
             "to_resource_type": "ecs.cloudservers",
             "relation_type": "isAssociatedWith"
           }
         ]
       }
     ],
     "snapshot_id": "6e40483d-5499-4440-a369-284e528f3d85",
     "snapshot_time": "2020-06-30T06:56:00.018Z"
   }
