:original_name: obs_03_0204.html

.. _obs_03_0204:

Related Services
================

.. table:: **Table 1** Related services

   +-------------------------------------------------------------------------------------------------------+--------------------------------------+-------------------------------------------------------------------------------------------+
   | Function                                                                                              | Related Service                      | Reference                                                                                 |
   +=======================================================================================================+======================================+===========================================================================================+
   | IAM provides the following functions:                                                                 | Identity and Access Management (IAM) | :ref:`Permissions Management <obs_03_0045>`                                               |
   |                                                                                                       |                                      |                                                                                           |
   | -  User identity authentication                                                                       |                                      | :ref:`Configuring User Permissions <obs_03_0304>`                                         |
   | -  IAM user permission management                                                                     |                                      |                                                                                           |
   | -  IAM agency configuration                                                                           |                                      |                                                                                           |
   +-------------------------------------------------------------------------------------------------------+--------------------------------------+-------------------------------------------------------------------------------------------+
   | CTS collects records of operations on OBS resources, facilitating querying, audits, and backtracking. | Cloud Trace Service (CTS)            | :ref:`Cloud Trace Service <obs_03_0020>`                                                  |
   +-------------------------------------------------------------------------------------------------------+--------------------------------------+-------------------------------------------------------------------------------------------+
   | SMN sends OBS related alarms and event notifications, and triggers workflows.                         | Simple Message Notification (SMN)    | :ref:`SMN-Enabled Event Notification <en-us_topic_0045853816>`                            |
   +-------------------------------------------------------------------------------------------------------+--------------------------------------+-------------------------------------------------------------------------------------------+
   | Tags are used to label and classify buckets in OBS.                                                   | Tag Management Service (TMS)         | :ref:`Tag Overview <en-us_topic_0059888284>`                                              |
   +-------------------------------------------------------------------------------------------------------+--------------------------------------+-------------------------------------------------------------------------------------------+
   | KMS encrypts files uploaded to the OBS.                                                               | Key Management Service (KMS)         | :ref:`Server-Side Encryption Overview <en-us_topic_0066036553>`                           |
   +-------------------------------------------------------------------------------------------------------+--------------------------------------+-------------------------------------------------------------------------------------------+
   | DNS resolves domain names configured for static website hosting in OBS.                               | Domain Name Service (DNS)            | :ref:`Using a User-Defined Domain Name to Configure Static Website Hosting <obs_03_0338>` |
   +-------------------------------------------------------------------------------------------------------+--------------------------------------+-------------------------------------------------------------------------------------------+

The OBS can serve as a storage resource pool for other cloud services such as Relational Database Service (RDS) and Cloud Trace Service (CTS).
