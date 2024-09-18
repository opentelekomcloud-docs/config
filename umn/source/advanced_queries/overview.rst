:original_name: rms_10_0100.html

.. _rms_10_0100:

Overview
========

Advanced queries allow you to query your resource configuration states for one or more regions using ResourceQL.

You can conveniently use ResourceQL and a query editor to search for and view your resources.

ResourceQL is a subset of structured query language (SQL) SELECT syntax to help you perform property-based queries and aggregations. The query complexity varies. You can query resources by tag or resource identifier, or by using complex SQL statements. For example, you can query an ECS with a specified OS version.

You can use Advanced Queries to:

-  Manage inventory. For example, you can query ECSs with certain specifications.
-  Check security compliance of your resources. For example, you can check if the configurations (public IPs attached or disks encrypted) of your resources meet security requirements.
-  Optimize costs. For example, you can list all EVS disks that have not been attached to any ECS to avoid unnecessary expenditures.

.. note::

   You can only use advanced queries to query, view, or export cloud resources. If you need to modify or delete resources, go to related service consoles.
