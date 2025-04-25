:original_name: obs_40_0003.html

.. _obs_40_0003:

IAM Permissions
===============

IAM Permissions Overview
------------------------

By default, newly created IAM users do not have any permissions. You need to add the user to one or more groups, and attach permission policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

IAM permissions apply to all OBS buckets and objects. To grant an IAM user the permission to operate OBS resources, you need to assign one or more OBS permission sets to the user group that the user belongs to.

OBS is a global service because it is available in all physical regions. If users in the global project are assigned IAM permissions, they do not need to switch regions to access OBS.

You can grant permissions to users by roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism only provides a limited number of service-level roles for authorization. When using roles to grant permissions, you also need to assign other dependency roles. However, roles are not the best choice for fine-grained authorization and secure access control.
-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant OBS users only the permissions to manage a certain type of OBS resources.

.. note::

   Due to data caching, a role and policy involving OBS actions will take effect 10 to 15 minutes after it is attached to a user or a user group.

IAM presets system permissions for each cloud service so that you can quickly configure basic permissions. :ref:`Table 1 <obs_40_0003__table143320246431>` describes all system permissions of OBS.

Custom policies can be created to supplement the system-defined policies of OBS.

.. _obs_40_0003__table143320246431:

.. table:: **Table 1** OBS system permissions

   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------+
   | Role/Policy Name     | Description                                                                                                                                                                                                                                                                                        | Type                  | Dependency      |
   +======================+====================================================================================================================================================================================================================================================================================================+=======================+=================+
   | Tenant Administrator | Users with this permission can perform all operations on all services except IAM.                                                                                                                                                                                                                  | System-defined role   | N/A             |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------+
   | Tenant Guest         | Users with this permission can perform read-only operations on all services except IAM.                                                                                                                                                                                                            | System-defined role   | N/A             |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------+
   | OBS Administrator    | Users with this permission are OBS administrators and can perform any operations on all OBS resources under the account.                                                                                                                                                                           | System-defined role   | N/A             |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------+
   | OBS Buckets Viewer   | Users with this permission can list buckets, obtain basic information about buckets, and obtain bucket metadata.                                                                                                                                                                                   | System-defined role   | N/A             |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------+
   | OBS ReadOnlyAccess   | Users with this permission can list buckets, obtain basic information about buckets, obtain bucket metadata, and list objects (not the objects that have been versioned).                                                                                                                          | System-defined policy | N/A             |
   |                      |                                                                                                                                                                                                                                                                                                    |                       |                 |
   |                      | .. note::                                                                                                                                                                                                                                                                                          |                       |                 |
   |                      |                                                                                                                                                                                                                                                                                                    |                       |                 |
   |                      |    If a user with this permission fails to list objects on OBS Console, there may be multiple versions of objects in the bucket. In this case, you need to grant the user the **obs:bucket:ListBucketVersions** permission so that the user can view different versions of objects on OBS Console. |                       |                 |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------+
   | OBS OperateAccess    | Users with this permission can perform all OBS ReadOnlyAccess operations and perform basic operations on objects, such as uploading, downloading, and deleting objects, and obtaining object ACLs.                                                                                                 | System-defined policy | N/A             |
   |                      |                                                                                                                                                                                                                                                                                                    |                       |                 |
   |                      | .. note::                                                                                                                                                                                                                                                                                          |                       |                 |
   |                      |                                                                                                                                                                                                                                                                                                    |                       |                 |
   |                      |    If a user with this permission fails to list objects on OBS Console, there may be multiple versions of objects in the bucket. In this case, you need to grant the user the **obs:bucket:ListBucketVersions** permission so that the user can view different versions of objects on OBS Console. |                       |                 |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------+

The following table lists the common operations supported by system-defined permissions for OBS. You can refer to this table to select the permissions as required.

.. table:: **Table 2** Permissions and allowed operations on OBS resources

   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Operation                                            | Tenant Administrator | Tenant Guest | OBS Administrator | OBS Buckets Viewer | OBS ReadOnlyAccess | OBS OperateAccess |
   +======================================================+======================+==============+===================+====================+====================+===================+
   | Listing buckets                                      | Yes                  | Yes          | Yes               | Yes                | Yes                | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Creating buckets                                     | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Deleting buckets                                     | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Obtaining basic information about buckets            | Yes                  | Yes          | Yes               | Yes                | Yes                | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Controlling bucket access                            | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing bucket policies                             | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Modifying bucket storage classes                     | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Listing objects                                      | Yes                  | Yes          | Yes               | No                 | Yes                | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Listing versioned objects                            | Yes                  | Yes          | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Uploading a file                                     | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Creating a folder                                    | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Deleting a file                                      | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Deleting a folder                                    | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Downloading a file                                   | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Deleting files with multiple versions                | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Downloading files with multiple versions             | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Modifying object storage classes                     | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Restoring files                                      | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Undeleting a file                                    | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Deleting fragments                                   | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Controlling access to objects                        | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Configuring object metadata                          | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Obtaining object metadata                            | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing versioning                                  | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing logging                                     | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing event notifications                         | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing tags                                        | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing lifecycle rules                             | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing static website hosting                      | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing CORS rules                                  | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing URL validation                              | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing domain names                                | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing cross-region replication                    | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Configuring an object ACL                            | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Configuring ACL for an object of a specified version | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Obtaining an object ACL                              | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Obtaining the ACL of a specific object version       | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Performing a multipart upload                        | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Listing uploaded parts                               | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Canceling a multipart upload                         | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Configuring requester-pays                           | Yes                  | No           | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Obtaining requester-pays configuration information   | Yes                  | Yes          | Yes               | No                 | No                 | No                |
   +------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+

Application Scenarios of IAM Permissions
----------------------------------------

IAM permissions control IAM users under an account to access:

-  All cloud resources.
-  All OBS buckets and objects.
-  Specified OBS resources.

Policy Structure and Syntax
---------------------------

A policy consists of a version and one or more statements.


.. figure:: /_static/images/en-us_image_0257849924.png
   :alt: **Figure 1** Policy structure

   **Figure 1** Policy structure

Policy syntax example:

.. code-block::

   {
       "Version": "1.1",
       "Statement": [
                   {
               "Effect": "Allow",
               "Action": [
                   "obs:bucket:HeadBucket",
                   "obs:bucket:ListBucket",
                   "obs:bucket:GetBucketLocation"
               ],
               "Resource": [
                   "obs:*:*:bucket:*"
               ],
               "Condition": {
                   "StringEndWithIfExsits": {
                       "g:UserName": ["specialCharacter"]
                   },
                   "Bool": {
                       "g:MFAPresent": ["true"]
                   }
               }
           }
       ]
   }

.. table:: **Table 3** Policy syntax parameters

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   +===================================+===============================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | Version                           | The version number of a policy.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   | -  **1.0**: RBAC policy. An RBAC policy consists of permissions for an entire service. Users in a group with such a policy assigned are granted all of the permissions required for that service.                                                                                                                                                                                                                                                                                                                                             |
   |                                   | -  **1.1**: Fine-grained policy. A fine-grained policy consists of API-based permissions for operations on specific resource types. Fine-grained policies, as the name suggests, allow for more fine-grained control on specific operations and resources than RBAC policies. For example, you can restrict an IAM user to access only the objects in a specific directory of an OBS bucket.                                                                                                                                                  |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Statement                         | Descriptions of a policy, including **Effect**, **Action**, **Resource** (optional), and **Condition** (optional).                                                                                                                                                                                                                                                                                                                                                                                                                            |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   | -  **Effect**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    The value of **Effect** can be **Allow** or **Deny**. System policies contain only **Allow** statements. For custom policies containing both **Allow** and **Deny** statements, **Deny** statements take precedence over **Allow** statements.                                                                                                                                                                                                                                                                                             |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   | -  **Action**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    Actions allowed on resources. An action is in the format of *Service name*:*Resource type*:*Action*. A policy can contain one or more actions. You can use a wildcard (``*``) to indicate all services, resource types, or actions. There are two types of OBS resources: buckets and objects.                                                                                                                                                                                                                                             |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   | -  **Resource**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    Resources on which the policy takes effect. A resource is in the format of *Service name*:*Region*:*Domain ID*:*Resource type*:*Resource path*. You can use a wildcard (``*``) to indicate all services, regions, domain IDs, resource types, or resource paths. In the JSON view, if **Resource** is not specified, the policy applies to all resources.                                                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    The value of **Resource** can only contain uppercase (A to Z), lowercase (a to z) letters, digits (0 to 9), and the following characters: **-_*./\\**. If you want to specify unsupported characters, use the wildcard character (``*``).                                                                                                                                                                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    OBS is a global service. Therefore, set *Region* to **\***. *Domain ID* indicates the ID of the resource owner. Set it to **\*** to indicate the ID of the account that the resources belong to.                                                                                                                                                                                                                                                                                                                                           |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    Examples:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    -  **obs:*:*:bucket:\***: all OBS buckets                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |                                   |    -  **obs:*:*:object:my-bucket/my-object/\***: all objects in the **my-object** directory of bucket **my-bucket**                                                                                                                                                                                                                                                                                                                                                                                                                           |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   | -  **Condition**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    When creating a custom policy, you can add conditions to control when the policy takes effect. A condition consists of a condition key and an operator. Condition keys are either global or service-level. Global condition keys (starting with **g:**) are available for actions on all services, while service-level condition keys (starting with a service name acronym like **obs:**) are available only for actions on a specific service. An operator is used together with a condition key to form a complete condition statement. |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    OBS has predefined a group of condition keys for use in IAM. For example, you can use the condition key **obs:SourceIp** to allow access from a specific IP address.                                                                                                                                                                                                                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    The condition keys and operators supported by OBS are the same as those in the bucket policy. When configuring condition keys in IAM, start the condition keys and operators with **obs:**. For detailed conditions, see :ref:`Bucket Policy Parameters <obs_40_0041>`.                                                                                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    The value of **Condition** can only contain uppercase letters (A to Z), lowercase letters (a to z), digits (0 to 9), and the following characters: **-,./_@#$%&**. If you want to specify unsupported characters, use the condition operators (like StringMatch) for fuzzy match.                                                                                                                                                                                                                                                          |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    Examples:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                                   |    -  **StringEndWithIfExists":{"g:UserName":["specialCharacter"]}**: The statement is valid for users whose names end with **specialCharacter**.                                                                                                                                                                                                                                                                                                                                                                                             |
   |                                   |    -  **"StringLike":{"obs:prefix":["private/"]}**: When listing objects in a bucket, you need to set prefix to **private/** or include **private/**.                                                                                                                                                                                                                                                                                                                                                                                         |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Configuring IAM Permissions
---------------------------

-  `Creating a User and Granting OBS Permissions <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0122.html>`__
-  `Creating a Custom Policy <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0016.html>`__

Example Custom Policies
-----------------------

-  **Example 1: Grant permissions that allow full access to OBS.**

   This policy allows users to perform any operation on OBS using the API, SDKs, OBS Console, or tools.

   If a user logs in to OBS Console and also accesses resources of other services, such as audit information in CTS, acceleration domain names in CDN, and keys in KMS, in addition to the OBS permissions, you need to grant users the permissions to access these services. CDN is a global service. CTS, SMN, and KMS are regional services. You need to configure the **Tenant Guest** permission for the global project and regional projects based on the services and regions that you use.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:*:*"
                  ]
              }
          ]
      }

-  **Example 2: Grant permissions that allow read-only access to a bucket (any directory).**

   This policy allows users to list and download all objects from bucket **obs-example**.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:object:GetObject",
                      "obs:bucket:ListBucket"
                  ],
                  "Resource": [
                      "obs:*:*:object:obs-example/*",
                      "obs:*:*:bucket:obs-example"
                  ]
              }
          ]
      }

-  **Example 3: Grant permissions that allow read-only access to a bucket (a specified directory).**

   This policy allows users to download objects only from the **my-project/** directory of bucket **obs-example**. Objects in other directories can be listed but cannot be downloaded.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:object:GetObject",
                      "obs:bucket:ListBucket"
                  ],
                  "Resource": [
                      "obs:*:*:object:obs-example/my-project/*",
                      "obs:*:*:bucket:obs-example"
                  ]
              }
          ]
      }

-  **Example 4: Grant permissions that allow read and write access to a bucket (a specified directory).**

   This policy allows users to list, download, upload, and delete objects in the **my-project** directory of bucket **obs-example**.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:object:GetObject",
                      "obs:object:ListMultipartUploadParts",
                      "obs:bucket:ListBucket",
                      "obs:object:DeleteObject",
                      "obs:object:PutObject"
                  ],
                  "Resource": [
                      "obs:*:*:object:obs-example/my-project/*",
                      "obs:*:*:bucket:obs-example"
                  ]
              }
          ]
      }

-  **Example 5: Grant permissions that allow full access to a bucket.**

   This policy allows users to perform any operation on bucket **obs-example**.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:*:*"
                  ],
                  "Resource": [
                      "obs:*:*:bucket:obs-example",
                      "obs:*:*:object:obs-example/*"
                  ]
              }
          ]
      }

-  **Example 6: Deny object upload.**

   A policy with only **Deny** statements must be used together other policies. If the policy assigned to a user contains both **Allow** and **Deny** statements, the **Deny** statement take precedence over the **Allow** statement.

   If you need to assign **OBS OperateAccess** permissions to a user but prevent the user from uploading objects, you can create a custom policy to deny object upload, and assign this custom policy and **OBS OperateAccess** to the user. Then the user can perform all operations allowed by **OBS OperateAccess** except for uploading objects. The following is an example of a deny policy:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Deny",
                  "Action": [
                      "obs:object:PutObject"
                  ]
              }
          ]
      }

-  **Example 7: Grant the permissions to change a bucket's storage class and delete certain objects from the bucket.**

   This policy allows users to change the storage class of bucket **obs-example** and to delete object **my-object.txt** from the bucket.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:bucket:ListAllMyBuckets",
                      "obs:bucket:ListBucket"
                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:object:DeleteObject",
                      "obs:bucket:PutBucketStoragePolicy"
                  ],
                  "Resource": [
                      "OBS:*:*:object:obs-example/my-object.txt",
                      "OBS:*:*:bucket:obs-example"
                  ]
              }
          ]
      }
