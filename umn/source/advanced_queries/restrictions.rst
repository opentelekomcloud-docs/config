:original_name: rms_10_0600.html

.. _rms_10_0600:

Restrictions
============

To prevent a single user from occupying resources for queries for too long, the following constrains are set on advanced queries:

-  If the execution duration of a query statement exceeds 15 seconds, a timeout error will be returned.
-  If the result set to be returned exceeds the size limit, an error will occur. Make sure that the data volume returned by each statement is within the size limit.
-  Up to 4,000 records are returned for a single query.
-  A single query statement can be used to perform a maximum of two join queries for tables.
-  A maximum of 200 advanced queries can be created for each account.

.. important::

   To get full functionality of advanced queries, you need to enable the resource recorder. The following describes how the resource recorder may affect your use of advanced queries.

   -  If you have never enabled the resource recorder, no resources can be queried with an advanced query.
   -  If you have enabled the resource recorder and a monitoring scope is specified, only resources within the monitoring scope can be queried with an advanced query.
   -  If you enable the resource recorder and disable it after a period of time, only resource data collected during the period when the resource recorder was enabled can be queried with an advanced query.

   For details about how to enable and configure the resource recorder, see :ref:`Configuring the Resource Recorder <rms_04_0200>`.
