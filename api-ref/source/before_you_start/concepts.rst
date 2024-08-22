:original_name: rms_01_0500.html

.. _rms_01_0500:

Concepts
========

-  Account

   An account has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant user permissions. The account should not be used directly to perform routine management. For security purposes, create Identity and Access Management (IAM) users and grant them permissions for routine management.

-  User

   An IAM user is created by an account through IAM to use cloud services. Each IAM user has its own identity credentials (password and access keys).

   The account name, username, and password will be required for API authentication.

-  Region

   A region is a geographic area in which cloud resources are deployed. Availability zones (AZs) in the same region can communicate with each other over an intranet, while AZs in different regions are isolated from each other. Deploying cloud resources in different regions can better suit certain user requirements or comply with local laws or regulations.

-  AZ

   An AZ comprises of one or more physical data centers equipped with independent ventilation, fire, water, and electricity facilities. Computing, network, storage, and other resources in an AZ are logically divided into multiple clusters. AZs within a region are interconnected using high-speed optical fibers to allow you to build cross-AZ high-availability systems.

-  Project

   A project corresponds to a region. Default projects are defined to group and physically isolate resources (including compute, storage, and network resources) across regions. You can grant users permissions by project, so that authorized users can access all resources in the project. If you need more refined access control, create subprojects under a default project and create resources in subprojects. Then you can assign users the permissions required to access only the resources in the specific subprojects.


   .. figure:: /_static/images/en-us_image_0000001466731780.png
      :alt: **Figure 1** Project isolation model

      **Figure 1** Project isolation model
