:original_name: rms_06_0701.html

.. _rms_06_0701:

Overview
========

ResourceQL provides SQL-like functions, allowing you to flexibly query your cloud resources.

.. code-block::

   SELECT name, created, updated FROM resources WHERE region_id = 'regionid1'

The statement is case insensitive. SELECT COUNT(``*``) and select CoUnT(``*``) are the same. Use single quotation marks to represent the literal of a string.

The following are data types supported by ResourceQL. For the array type, [] is used to index a position, and the number starts from 1.

.. table:: **Table 1** Supported data types

   ========== ============
   Type Name  Type
   ========== ============
   Integer    Int/Integer
   Float      Float/Double
   Boolean    Boolean
   Array      Array
   String     String
   Dictionary Object
   Timestamp  Date
   ========== ============

All your cloud resources are included in a table. The table name is fixed to **resources**. The resources under your aggregator account forms a table. The table name is fixed to **aggregator_resources**. Each row in the table records a piece of data. The conventions of each column are as follows.

.. table:: **Table 2** Parameter descriptions in table **resources**

   +--------------------+---------------------------+----------------------------------------------------+
   | Parameter          | Type                      | Description                                        |
   +====================+===========================+====================================================+
   | id                 | String                    | Specifies the resource ID.                         |
   +--------------------+---------------------------+----------------------------------------------------+
   | name               | String                    | Specifies the resource name.                       |
   +--------------------+---------------------------+----------------------------------------------------+
   | provider           | String                    | Specifies the cloud service name.                  |
   +--------------------+---------------------------+----------------------------------------------------+
   | type               | String                    | Specifies the resource type.                       |
   +--------------------+---------------------------+----------------------------------------------------+
   | region_id          | String                    | Specifies the region ID.                           |
   +--------------------+---------------------------+----------------------------------------------------+
   | project_id         | String                    | Specifies the project ID.                          |
   +--------------------+---------------------------+----------------------------------------------------+
   | ep_id              | String                    | Specifies the enterprise project ID.               |
   +--------------------+---------------------------+----------------------------------------------------+
   | checksum           | String                    | Specifies the resource checksum.                   |
   +--------------------+---------------------------+----------------------------------------------------+
   | created            | Date                      | Specifies the time when the resource was created.  |
   +--------------------+---------------------------+----------------------------------------------------+
   | updated            | Date                      | Specifies the time when the resource was updated.  |
   +--------------------+---------------------------+----------------------------------------------------+
   | provisioning_state | String                    | Specifies the result of an operation on resources. |
   +--------------------+---------------------------+----------------------------------------------------+
   | tag                | Array(Map<String,String>) | Specifies the resource tag.                        |
   +--------------------+---------------------------+----------------------------------------------------+
   | properties         | Map<String,Object>        | Specifies the resource attribute details.          |
   +--------------------+---------------------------+----------------------------------------------------+

**aggregator_resources** contains **domain_id** that indicates the account ID. The type of a domain ID is a string.

**provider** and **type** represent a unique resource. For different resources, **properties** varies. For example, for an ECS, the **provider** and **type** are **ecs** and **cloudservers**, and the **properties** contains **flavor**. For a VPC, the **provider** and **type** are **vpc** and **publicips**, and the **properties** contains **bandwidth**.

You can obtain resource attributes that can be included in the **properties** element for each resource on Config console or by calling the related API. For more details, see :ref:`How Can I Obtain Resource Attributes Reported to Config? <rms_08_0100__section1077795954511>`.

**properties** supports nested queries. The following shows an example of how to query the **addresses** parameter under **properties** for the running ECS.

.. code-block::

   SELECT name, created, updated, properties.addresses FROM resources
       WHERE provider = 'ecs' AND type = 'cloudservers' AND properties.status = 'ACTIVE'
