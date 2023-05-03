:original_name: obs_40_0011.html

.. _obs_40_0011:

Typical Permission Control Scenarios
====================================

The following typical scenarios are provided to help you better configure OBS permission control.

Factors to consider before configuring permission control:

#. **Who are granted**: Grantees can be a single IAM user, multiple IAM users or user groups, other accounts, and anonymous users.
#. **What resources will be accessed**: Such resources can be all OBS resources (requiring service-level permissions), specified buckets, and specified objects.
#. **What permissions are granted**: In addition to configure basic permissions, such as read and read/write permissions, you can also customize permissions based on your needs.

OBS provides various permission control mechanisms for different scenarios. The following figure can help you quickly find the best method that matches your requirements.


.. figure:: /_static/images/en-us_image_0000001254687479.png
   :alt: **Figure 1** Typical permission scenarios

   **Figure 1** Typical permission scenarios

The following table lists the permission control cases in typical scenarios for your reference.

.. table:: **Table 1** Configuration cases in typical scenarios

   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | Scenario                                                                            | Configuration Case                                                                                                     |
   +=====================================================================================+========================================================================================================================+
   | Granting permissions to an IAM user under the current account                       | :ref:`Granting an IAM User the Permissions Required to List and Create Buckets <obs_40_0014>`                          |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting an IAM User the Read and Write Permissions on a Bucket <obs_40_0015>`                                   |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting an IAM User the Permissions Required to Perform Specific Operations on a Specific Bucket <obs_40_0016>` |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting an IAM User the Read Permission on a Specific Object <obs_40_0017>`                                     |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting an IAM User the Permissions Required to Perform Specific Operations on Certain Objects <obs_40_0018>`   |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | Granting permissions to multiple IAM users or user groups under the current account | :ref:`Granting IAM User Groups All Permissions on All OBS Resources <obs_40_0020>`                                     |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting IAM User Groups Basic Permissions on All OBS Resources <obs_40_0021>`                                   |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting IAM User Groups Specified Permissions on All OBS Resources <obs_40_0022>`                               |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting IAM User Groups Specified Permissions on Certain OBS Resources <obs_40_0023>`                           |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | Granting permissions to other accounts                                              | :ref:`Granting an Account the Read and Write Permissions on a Bucket <obs_40_0025>`                                    |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting an Account the Specified Permissions on a Bucket <obs_40_0026>`                                         |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting IAM Users Under an Account the Access to a Bucket and Resources in the Bucket <obs_40_0027>`            |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting an Account Read Permissions on Certain Objects <obs_40_0028>`                                           |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting an Account the Specified Permissions on Certain Objects <obs_40_0029>`                                  |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | Granting permissions to anonymous users                                             | :ref:`Granting Anonymous Users Public Read Permissions on a Bucket <obs_40_0031>`                                      |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting Anonymous Users Public Read Permissions on a Directory <obs_40_0032>`                                   |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Granting Anonymous Users Public Read Permissions on Certain Objects <obs_40_0033>`                               |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   |                                                                                     | :ref:`Temporarily Sharing Objects with Anonymous Users <obs_40_0034>`                                                  |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | Granting temporary permissions                                                      | :ref:`Granting Temporary Access to OBS <obs_40_0037>`                                                                  |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | Restricting access to specified IP addresses                                        | :ref:`Preventing Specific IP Addresses from Accessing a Bucket <obs_40_0036>`                                          |
   +-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
