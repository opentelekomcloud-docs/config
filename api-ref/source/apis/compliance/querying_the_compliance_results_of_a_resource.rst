:original_name: rms_04_0512.html

.. _rms_04_0512:

Querying the Compliance Results of a Resource
=============================================

Function
--------

This API is used to query all compliance results of a resource evaluated by rules. The resource is searched by resource ID.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/resources/{resource_id}/policy-states

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

   +------------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                        |
   +==================+=================+=================+====================================================+
   | compliance_state | No              | String          | Specifies the compliance status.                   |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Maximum: **16**                                    |
   +------------------+-----------------+-----------------+----------------------------------------------------+
   | limit            | No              | Integer         | Specifies the maximum number of records to return. |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Minimum: **1**                                     |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Maximum: **200**                                   |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Default: **200**                                   |
   +------------------+-----------------+-----------------+----------------------------------------------------+
   | marker           | No              | String          | Specifies the pagination parameter.                |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Minimum: **4**                                     |
   |                  |                 |                 |                                                    |
   |                  |                 |                 | Maximum: **400**                                   |
   +------------------+-----------------+-----------------+----------------------------------------------------+

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

   +-----------+-------------------------------------------------------------------------+---------------------------------------------------------------+
   | Parameter | Type                                                                    | Description                                                   |
   +===========+=========================================================================+===============================================================+
   | value     | Array of :ref:`PolicyState <rms_04_0512__response_policystate>` objects | Specifies the return value of querying the compliance result. |
   +-----------+-------------------------------------------------------------------------+---------------------------------------------------------------+
   | page_info | :ref:`PageInfo <rms_04_0512__response_pageinfo>` object                 | Specifies the pagination object.                              |
   +-----------+-------------------------------------------------------------------------+---------------------------------------------------------------+

.. _rms_04_0512__response_policystate:

.. table:: **Table 5** PolicyState

   +------------------------+--------+--------------------------------------------------------------------------+
   | Parameter              | Type   | Description                                                              |
   +========================+========+==========================================================================+
   | domain_id              | String | Specifies the user ID.                                                   |
   +------------------------+--------+--------------------------------------------------------------------------+
   | region_id              | String | Specifies the ID of the region the resource belongs to.                  |
   +------------------------+--------+--------------------------------------------------------------------------+
   | resource_id            | String | Specifies the resource ID.                                               |
   +------------------------+--------+--------------------------------------------------------------------------+
   | resource_name          | String | Specifies the resource name.                                             |
   +------------------------+--------+--------------------------------------------------------------------------+
   | resource_provider      | String | Specifies the cloud service name.                                        |
   +------------------------+--------+--------------------------------------------------------------------------+
   | resource_type          | String | Specifies the resource type.                                             |
   +------------------------+--------+--------------------------------------------------------------------------+
   | trigger_type           | String | Specifies the trigger type. The value can be **resource** or **period**. |
   +------------------------+--------+--------------------------------------------------------------------------+
   | compliance_state       | String | Specifies the compliance status.                                         |
   +------------------------+--------+--------------------------------------------------------------------------+
   | policy_assignment_id   | String | Specifies the rule ID.                                                   |
   +------------------------+--------+--------------------------------------------------------------------------+
   | policy_assignment_name | String | Specifies the rule name.                                                 |
   +------------------------+--------+--------------------------------------------------------------------------+
   | policy_definition_id   | String | Specifies the policy ID.                                                 |
   +------------------------+--------+--------------------------------------------------------------------------+
   | evaluation_time        | String | Specifies the evaluation time of compliance status.                      |
   +------------------------+--------+--------------------------------------------------------------------------+

.. _rms_04_0512__response_pageinfo:

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

None

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "value": [
       {
         "domain_id": "daf2557fc0de4da09e128441baa71697",
         "region_id": "eu-de",
         "resource_id": "d418cc33-dd14-43f7-aa1e-a72ecab1a9b3",
         "resource_name": "ecs-aziuzko",
         "resource_provider": "ecs",
         "resource_type": "cloudservers",
         "trigger_type": "resource",
         "compliance_state": "NonCompliant",
         "policy_assignment_id": "6672d6b0354ba95beef328d1",
         "policy_assignment_name": "allowed-ecs-flavors",
         "policy_definition_id": "5f8d549bffeecc14f1fb522a",
         "evaluation_time": "1720441778399"
       },
       {
         "domain_id": "daf2557fc0de4da09e128441baa71697",
         "region_id": "eu-de",
         "resource_id": "d418cc33-dd14-43f7-aa1e-a72ecab1a9b3",
         "resource_name": "ecs-aziuzko",
         "resource_provider": "ecs",
         "resource_type": "cloudservers",
         "trigger_type": "resource",
         "compliance_state": "NonCompliant",
         "policy_assignment_id": "6672d83777c56f4aeb50b892",
         "policy_assignment_name": "allowed-ecs-flavorss3",
         "policy_definition_id": "5f8d549bffeecc14f1fb522a",
         "evaluation_time": "1720441808621"
       }
     ],
     "page_info": {
       "current_count": 2,
       "next_marker": null
     }
   }

Status Codes
------------

+-------------+---------------------------------------------------------------------+
| Status Code | Description                                                         |
+=============+=====================================================================+
| 200         | Operation succeeded.                                                |
+-------------+---------------------------------------------------------------------+
| 400         | Invalid parameters.                                                 |
+-------------+---------------------------------------------------------------------+
| 403         | Authentication failed or you do not have the operation permissions. |
+-------------+---------------------------------------------------------------------+
| 404         | Resources not found.                                                |
+-------------+---------------------------------------------------------------------+
| 500         | Server error.                                                       |
+-------------+---------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
