:original_name: rms_01_0100.html

.. _rms_01_0100:

What Is Config?
===============

Description
-----------

Config allows you to search for, record, and continuously evaluate your resource configurations to make sure that your resources are in expected status.

.. important::

   To get full functionality of Config, you need to enable the resource recorder. If the resource recorder is disabled, you may fail to update your resource data or accurately evaluate your resources with rules. For details about how to enable and configure the resource recorder, see :ref:`Configuring the Resource Recorder <rms_04_0200>`

Architecture
------------

Config provides you with resource information, such as resource inventory, details, relationships, and change records. It stores your resource data every 24 hours and notifications of your resource changes every 6 hours. It will also notify you when a change is made to your resources. In addition, it enables you to use Config rules to evaluate your resources.

-  **Viewing resource details**: You can set multiple search options to query your resources on Config console.
-  **Viewing resource relationships**: You can view relationships between resources on Config console.
-  **Viewing resource change records**: You can enable and configure the resource recorder to continuously monitor resource changes.
-  **Sending notifications**: Config will notify you when a change is made to your resources after you have enabled the resource recorder and configured a Simple Message Notification (SMN) topic.
-  **Storing resource change notifications**: Config will store your resource change notifications every 6 hours after you have enabled the resource recorder and configured an SMN topic and an Object Storage Bucket (OBS) bucket.
-  **Storing resource snapshots**: Config will store your resource snapshots into the specified OBS bucket every 24 hours after you have enabled the resource recorder and configured an OBS bucket.
-  **Evaluating resource compliance**: Config evaluates your resources using rules to check whether they are compliant or not.
-  **Advanced query**: Allows you to customize queries with ResourceQL to search for your resources.

Access Methods
--------------

You can use either of the following methods to access Config.

-  **Management Console**

   The console is a web-based UI, where you can perform operations easily. Log in to the management console, click |image1| in the upper left corner, and choose **Management & Deployment** > **Config**.

-  **Application Programming Interfaces (APIs)**

   To integrate Config into a third-party system for secondary development, you need to access the service by calling APIs. For details, see *Config API Reference*.

.. |image1| image:: /_static/images/en-us_image_0000001524289093.png
