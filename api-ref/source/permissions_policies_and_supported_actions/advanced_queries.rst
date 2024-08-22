:original_name: rms_05_0500.html

.. _rms_05_0500:

Advanced Queries
================

+----------------------------+---------------------------------------------------------------------------+--------------------------+-------------+--------------------+
| Permissions                | API                                                                       | Action                   | IAM Project | Enterprise Project |
+============================+===========================================================================+==========================+=============+====================+
| Running advanced queries   | POST /v1/resource-manager/domains/{domain_id}/run-query                   | rms:resources:runQuery   | Y           | x                  |
+----------------------------+---------------------------------------------------------------------------+--------------------------+-------------+--------------------+
| Creating an advanced query | POST /v1/resource-manager/domains/{domain_id}/stored-queries              | rms:storedQueries:create | Y           | x                  |
+----------------------------+---------------------------------------------------------------------------+--------------------------+-------------+--------------------+
| Querying an advanced query | GET /v1/resource-manager/domains/{domain_id}/stored-queries/{query_id}    | rms:storedQueries:get    | Y           | x                  |
+----------------------------+---------------------------------------------------------------------------+--------------------------+-------------+--------------------+
| Listing advanced queries   | GET /v1/resource-manager/domains/{domain_id}/stored-queries               | rms:storedQueries:list   | Y           | x                  |
+----------------------------+---------------------------------------------------------------------------+--------------------------+-------------+--------------------+
| Updating an advanced query | PUT /v1/resource-manager/domains/{domain_id}/stored-queries/{query_id}    | rms:storedQueries:update | Y           | x                  |
+----------------------------+---------------------------------------------------------------------------+--------------------------+-------------+--------------------+
| Deleting an advanced query | DELETE /v1/resource-manager/domains/{domain_id}/stored-queries/{query_id} | rms:storedQueries:delete | Y           | x                  |
+----------------------------+---------------------------------------------------------------------------+--------------------------+-------------+--------------------+
| Querying schemas           | GET /v1/resource-manager/domains/{domain_id}/schemas                      | rms:schemas:list         | Y           | x                  |
+----------------------------+---------------------------------------------------------------------------+--------------------------+-------------+--------------------+
