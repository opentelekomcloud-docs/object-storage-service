:original_name: obs_40_0011.html

.. _obs_40_0011:

Typical Permissions Scenarios
=============================

The permissions settings for typical scenarios are provided to facilitate permissions management.

You need to consider the following factors before configuring permissions:

#. **Who are granted access**: A single IAM user, multiple IAM users or user groups, other accounts, or anonymous users
#. **What resources will be accessed**: All OBS resources (service-level permissions), specified buckets, or specified objects
#. **What permissions are granted**: Basic permissions, such as read and read/write permissions, or customized permissions

OBS provides various permission control methods for different scenarios. The following figure can help you quickly find the best method for your needs.


.. figure:: /_static/images/en-us_image_0000001254687479.png
   :alt: **Figure 1** Typical permissions scenarios

   **Figure 1** Typical permissions scenarios

The following table lists the typical scenarios for your reference.

.. table:: **Table 1** Typical permission configuration scenarios

   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Scenario                                                                            | Quick Links for Permission Configuration                                                                |
   +=====================================================================================+=========================================================================================================+
   | Granting permissions to a single IAM user under the current account                 | :ref:`Granting an IAM User the Permissions to Create and List Buckets <obs_40_0014>`                    |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting an IAM User the Read/Write Permission on a Bucket <obs_40_0015>`                         |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting an IAM User the Specified Permissions for a Bucket <obs_40_0016>`                        |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting an IAM User the Read Permissions on Specific Objects <obs_40_0017>`                      |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting an IAM User the Specific Permissions on Specific Objects <obs_40_0018>`                  |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Granting permissions to multiple IAM users or user groups under the current account | :ref:`Granting IAM User Groups All Permissions on All OBS Resources <obs_40_0020>`                      |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting IAM User Groups Basic Permissions on All OBS Resources <obs_40_0021>`                    |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting IAM User Groups Specific Permissions for All OBS Resources <obs_40_0022>`                |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting IAM User Groups Specific Permissions on Specific OBS Resources <obs_40_0023>`            |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Granting permissions to other accounts                                              | :ref:`Granting Other Accounts the Read/Write Permission for a Bucket <obs_40_0025>`                     |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting Other Accounts the Specified Permissions for a Bucket <obs_40_0026>`                     |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting IAM Users Under an Account the Access to a Bucket and the Resources in It <obs_40_0027>` |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting Other Accounts the Read Permission for Certain Objects <obs_40_0028>`                    |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting Other Accounts Specific Permissions for Specific Objects <obs_40_0029>`                  |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Granting permissions to anonymous users                                             | :ref:`Granting Anonymous Users the Public Read Permission for a Bucket <obs_40_0031>`                   |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting Anonymous Users the Read Permission for a Directory <obs_40_0032>`                       |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting Anonymous Users the Read Permission for Certain Objects <obs_40_0033>`                   |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Temporarily Sharing Objects with Anonymous Users <obs_40_0034>`                                   |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Granting temporary permissions                                                      | :ref:`Granting Temporary Access to OBS <obs_40_0037>`                                                   |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Restricting access to specified IP addresses                                        | :ref:`Restricting Access to a Bucket for Specific IP Addresses <obs_40_0036>`                           |
   +-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
