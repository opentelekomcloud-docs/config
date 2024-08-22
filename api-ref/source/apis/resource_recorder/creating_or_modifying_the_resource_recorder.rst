:original_name: rms_04_0203.html

.. _rms_04_0203:

Creating or Modifying the Resource Recorder
===========================================

Function
--------

This API is used to create or modify the resource recorder. Only one resource recorder can be configured.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

PUT /v1/resource-manager/domains/{domain_id}/tracker-config

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------+
   | Parameter       | Mandatory       | Type            | Description     |
   +=================+=================+=================+=================+
   | domain_id       | Yes             | String          | Specifies tags. |
   |                 |                 |                 |                 |
   |                 |                 |                 | Maximum: **36** |
   +-----------------+-----------------+-----------------+-----------------+

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

.. table:: **Table 3** Request body parameters

   +--------------------------+-----------+----------------------------------------------------------------------------+---------------------------------------------------+
   | Parameter                | Mandatory | Type                                                                       | Description                                       |
   +==========================+===========+============================================================================+===================================================+
   | channel                  | Yes       | :ref:`ChannelConfigBody <rms_04_0203__request_channelconfigbody>` object   | Specifies configurations for the tracker channel. |
   +--------------------------+-----------+----------------------------------------------------------------------------+---------------------------------------------------+
   | selector                 | Yes       | :ref:`SelectorConfigBody <rms_04_0203__request_selectorconfigbody>` object | Specifies the selector.                           |
   +--------------------------+-----------+----------------------------------------------------------------------------+---------------------------------------------------+
   | retention_period_in_days | No        | Integer                                                                    | Number of days for data storage.                  |
   +--------------------------+-----------+----------------------------------------------------------------------------+---------------------------------------------------+
   | agency_name              | Yes       | String                                                                     | Specifies the IAM agency name.                    |
   +--------------------------+-----------+----------------------------------------------------------------------------+---------------------------------------------------+

.. _rms_04_0203__request_channelconfigbody:

.. table:: **Table 4** ChannelConfigBody

   +-----------+-----------+----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                                         | Description                                                                                                                                                                                                                                                                                         |
   +===========+===========+==============================================================================================+=====================================================================================================================================================================================================================================================================================================+
   | smn       | No        | :ref:`TrackerSMNChannelConfigBody <rms_04_0203__request_trackersmnchannelconfigbody>` object | Specifies configurations for the SMN channel. For details about how to grant other accounts the permissions for publishing messages to SMN topics, see **Cross-Account Authorization** (**Resource Recorder** > **Enabling, Configuring, or Modifying the Resource Recorder**) in the *User Guide*. |
   +-----------+-----------+----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs       | No        | :ref:`TrackerOBSChannelConfigBody <rms_04_0203__request_trackerobschannelconfigbody>` object | Specifies configurations for the OBS bucket. For details about how to grant other accounts the permissions for dumping files to OBS buckets, see **Cross-Account Authorization** (**Resource Recorder** > **Enabling, Configuring, or Modifying the Resource Recorder**) in the *User Guide*.       |
   +-----------+-----------+----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _rms_04_0203__request_trackersmnchannelconfigbody:

.. table:: **Table 5** TrackerSMNChannelConfigBody

   ========== ========= ====== ============================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ============================
   region_id  Yes       String Specifies the region ID.
   project_id Yes       String Specifies the project ID.
   topic_urn  Yes       String Specifies the SMN topic URN.
   ========== ========= ====== ============================

.. _rms_04_0203__request_trackerobschannelconfigbody:

.. table:: **Table 6** TrackerOBSChannelConfigBody

   +-----------------+-----------------+-----------------+--------------------------------+
   | Parameter       | Mandatory       | Type            | Description                    |
   +=================+=================+=================+================================+
   | bucket_name     | Yes             | String          | Specifies the OBS bucket name. |
   |                 |                 |                 |                                |
   |                 |                 |                 | Maximum: **63**                |
   +-----------------+-----------------+-----------------+--------------------------------+
   | bucket_prefix   | No              | String          | OBS bucket prefix              |
   |                 |                 |                 |                                |
   |                 |                 |                 | Maximum: **256**               |
   +-----------------+-----------------+-----------------+--------------------------------+
   | region_id       | Yes             | String          | Specifies the region ID.       |
   +-----------------+-----------------+-----------------+--------------------------------+

.. _rms_04_0203__request_selectorconfigbody:

.. table:: **Table 7** SelectorConfigBody

   +----------------+-----------+------------------+------------------------------------------------------+
   | Parameter      | Mandatory | Type             | Description                                          |
   +================+===========+==================+======================================================+
   | all_supported  | Yes       | Boolean          | Specifies whether to select all supported resources. |
   +----------------+-----------+------------------+------------------------------------------------------+
   | resource_types | Yes       | Array of strings | Specifies the resource type list.                    |
   +----------------+-----------+------------------+------------------------------------------------------+

Response Parameters
-------------------

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

**Status code: 404**

.. table:: **Table 10** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 500**

.. table:: **Table 11** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

Example Requests
----------------

Creating the resource recorder and enabling message pushing and dumping

.. code-block:: text

   PUT /v1/resource-manager/domains/{domain_id}/tracker-config

   {
     "channel" : {
       "smn" : {
         "region_id" : "regionid1",
         "project_id" : "39c2af998c334ed6bcbb75b27318f7b5",
         "topic_urn" : "urn:smn:regionid1:39c2af998c334ed6bcbb75b27318f7b5:resource-manager-test"
       },
       "obs" : {
         "bucket_name" : "config-snapshot",
         "region_id" : "regionid1"
       }
     },
     "selector" : {
       "all_supported" : true,
       "resource_types" : [ ]
     },
     "agency_name" : "rms_tracker_agency"
   }

Example Responses
-----------------

None

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
