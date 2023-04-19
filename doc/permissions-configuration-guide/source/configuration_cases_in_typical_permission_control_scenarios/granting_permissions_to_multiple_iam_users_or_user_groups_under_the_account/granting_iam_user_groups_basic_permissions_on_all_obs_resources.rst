:original_name: obs_40_0021.html

.. _obs_40_0021:

Granting IAM User Groups Basic Permissions on All OBS Resources
===============================================================

Scenario
--------

This topic describes how to use the OBS-related system roles and policies preset in IAM to grant basic operation permissions on all OBS resources to multiple IAM users or user groups. The following table lists the permissions supported by preset system roles and policies.

.. table:: **Table 1** OBS system permissions

   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Role/Policy Name      | Description                                                                                                                                                                                                                                                                                        | Type                  |
   +=======================+====================================================================================================================================================================================================================================================================================================+=======================+
   | Tenant Administrator  | Users with this permission can perform all operations on all services except IAM.                                                                                                                                                                                                                  | System-defined role   |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Tenant Guest          | Users with this permission can perform read-only operations on all services except IAM.                                                                                                                                                                                                            | System-defined role   |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | OBS Administrator     | Users with this permission are OBS administrators and can perform any operations on all OBS resources under the account.                                                                                                                                                                           | System-defined policy |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | OBS Buckets Viewer    | Users with this permission can list buckets, obtain basic bucket information, and obtain bucket metadata.                                                                                                                                                                                          | System-defined role   |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | OBS ReadOnlyAccess    | Users with this permission can list buckets, obtain basic bucket information, obtain bucket metadata, and list objects (not the objects that have been versioned).                                                                                                                                 | System-defined policy |
   |                       |                                                                                                                                                                                                                                                                                                    |                       |
   |                       | .. note::                                                                                                                                                                                                                                                                                          |                       |
   |                       |                                                                                                                                                                                                                                                                                                    |                       |
   |                       |    If a user with this permission fails to list objects on OBS Console, there may be multiple versions of objects in the bucket. In this case, you need to grant the user the **obs:bucket:ListBucketVersions** permission so that the user can view different versions of objects on OBS Console. |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | OBS OperateAccess     | Users with this permission can perform all OBS ReadOnlyAccess operations and perform basic object operations, such as uploading objects, downloading objects, deleting objects, and obtaining object ACLs.                                                                                         | System-defined policy |
   |                       |                                                                                                                                                                                                                                                                                                    |                       |
   |                       | .. note::                                                                                                                                                                                                                                                                                          |                       |
   |                       |                                                                                                                                                                                                                                                                                                    |                       |
   |                       |    If a user with this permission fails to list objects on OBS Console, there may be multiple versions of objects in the bucket. In this case, you need to grant the user the **obs:bucket:ListBucketVersions** permission so that the user can view different versions of objects on OBS Console. |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Recommended Configuration
-------------------------

IAM system roles and policies

Configuration Precautions
-------------------------

After a system role or policy is configured according to this case, if you log in to the system using OBS Console or OBS Browser+, a message may be displayed indicating that you do not have the permission.

Authorized permissions are valid, though operations on the console or client are restricted. You can call the APIs directly.

With **OBS OperateAccess** configured, you can upload or download objects on OBS Console or OBS Browser+.

Procedure
---------

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**. The IAM console is displayed.

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Add system roles or policies that meet the service scenario requirements to the user group by following the instructions provided in the IAM document.

#. Add the IAM user you want to authorize to the created user group by referring to `Creating a User and Adding the User to a User Group <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__.

   .. note::

      Due to data caching, it takes about 10 to 15 minutes for the configured permissions to take effect.
