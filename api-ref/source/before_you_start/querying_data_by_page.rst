:original_name: rms_01_0600.html

.. _rms_01_0600:

Querying Data by Page
=====================

Some Config APIs support pagination query if you add **limit** and **marker** to the request URL. The value of **marker** must be the same as that returned in the last pagination query.

.. table:: **Table 1** Config parameter description

   +-----------+---------+-----------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type    | Mandatory | Description                                                                                                                      |
   +===========+=========+===========+==================================================================================================================================+
   | limit     | Integer | No        | Restricts the number of records displayed on each page. If **limit** is invalid, error code 400 will be returned.                |
   +-----------+---------+-----------+----------------------------------------------------------------------------------------------------------------------------------+
   | marker    | String  | No        | Specifies the **marker** value returned in the last pagination query. If **marker** is invalid, error code 400 will be returned. |
   +-----------+---------+-----------+----------------------------------------------------------------------------------------------------------------------------------+
