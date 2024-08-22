:original_name: rms_04_0201.html

.. _rms_04_0201:

Querying the Resource Recorder
==============================

Function
--------

This API is used to query details about the resource recorder.

Calling Method
--------------

For details, see :ref:`Calling APIs <rms_03_0000>`.

URI
---

GET /v1/resource-manager/domains/{domain_id}/tracker-config

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +--------------------------+-----------------------------------------------------------------------------+---------------------------------------------------+
   | Parameter                | Type                                                                        | Description                                       |
   +==========================+=============================================================================+===================================================+
   | channel                  | :ref:`ChannelConfigBody <rms_04_0201__response_channelconfigbody>` object   | Specifies configurations for the tracker channel. |
   +--------------------------+-----------------------------------------------------------------------------+---------------------------------------------------+
   | selector                 | :ref:`SelectorConfigBody <rms_04_0201__response_selectorconfigbody>` object | Specifies the selector.                           |
   +--------------------------+-----------------------------------------------------------------------------+---------------------------------------------------+
   | retention_period_in_days | Integer                                                                     | Number of days for data storage.                  |
   +--------------------------+-----------------------------------------------------------------------------+---------------------------------------------------+
   | agency_name              | String                                                                      | Specifies the IAM agency name.                    |
   +--------------------------+-----------------------------------------------------------------------------+---------------------------------------------------+

.. _rms_04_0201__response_channelconfigbody:

.. table:: **Table 4** ChannelConfigBody

   +-----------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                                                          | Description                                                                                                                                                                                                                                                                                         |
   +===========+===============================================================================================+=====================================================================================================================================================================================================================================================================================================+
   | smn       | :ref:`TrackerSMNChannelConfigBody <rms_04_0201__response_trackersmnchannelconfigbody>` object | Specifies configurations for the SMN channel. For details about how to grant other accounts the permissions for publishing messages to SMN topics, see **Cross-Account Authorization** (**Resource Recorder** > **Enabling, Configuring, or Modifying the Resource Recorder**) in the *User Guide*. |
   +-----------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs       | :ref:`TrackerOBSChannelConfigBody <rms_04_0201__response_trackerobschannelconfigbody>` object | Specifies configurations for the OBS bucket. For details about how to grant other accounts the permissions for dumping files to OBS buckets, see **Cross-Account Authorization** (**Resource Recorder** > **Enabling, Configuring, or Modifying the Resource Recorder**) in the *User Guide*.       |
   +-----------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _rms_04_0201__response_trackersmnchannelconfigbody:

.. table:: **Table 5** TrackerSMNChannelConfigBody

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   region_id  String Specifies the region ID.
   project_id String Specifies the project ID.
   topic_urn  String Specifies the SMN topic URN.
   ========== ====== ============================

.. _rms_04_0201__response_trackerobschannelconfigbody:

.. table:: **Table 6** TrackerOBSChannelConfigBody

   +-----------------------+-----------------------+--------------------------------+
   | Parameter             | Type                  | Description                    |
   +=======================+=======================+================================+
   | bucket_name           | String                | Specifies the OBS bucket name. |
   |                       |                       |                                |
   |                       |                       | Maximum: **63**                |
   +-----------------------+-----------------------+--------------------------------+
   | bucket_prefix         | String                | OBS bucket prefix              |
   |                       |                       |                                |
   |                       |                       | Maximum: **256**               |
   +-----------------------+-----------------------+--------------------------------+
   | region_id             | String                | Specifies the region ID.       |
   +-----------------------+-----------------------+--------------------------------+

.. _rms_04_0201__response_selectorconfigbody:

.. table:: **Table 7** SelectorConfigBody

   +----------------+------------------+------------------------------------------------------+
   | Parameter      | Type             | Description                                          |
   +================+==================+======================================================+
   | all_supported  | Boolean          | Specifies whether to select all supported resources. |
   +----------------+------------------+------------------------------------------------------+
   | resource_types | Array of strings | Specifies the resource type list.                    |
   +----------------+------------------+------------------------------------------------------+

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

None

Example Responses
-----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "channel": {
       "smn": {
         "region_id": "eu-de",
         "project_id": "ecabfaea4fd6425ba80d6f8860d8847d",
         "topic_urn": "urn:smn:eu-de:ecabfaea4fd6425ba80d6f8860d8847d:obs_testcase"
       },
       "obs": {
         "bucket_name": "resource-dump",
         "bucket_prefix": null,
         "region_id": "eu-de"
       }
     },
     "selector": {
       "all_supported": true,
       "resource_types": []
     },
     "retention_period_in_days": 2557,
     "agency_name": "rms_tracker_agency"
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
| 404         | No resource recorder found.                                         |
+-------------+---------------------------------------------------------------------+
| 500         | Server error.                                                       |
+-------------+---------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
