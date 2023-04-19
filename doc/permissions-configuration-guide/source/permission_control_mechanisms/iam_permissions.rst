:original_name: obs_40_0003.html

.. _obs_40_0003:

IAM Permissions
===============

IAM Permissions Overview
------------------------

By default, newly created IAM users do not have any permissions. You need to add the user to one or more groups, and attach permission policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

IAM permissions take effect on all OBS buckets and objects. To grant an IAM user the permission to operate OBS resources, you need to assign one or more OBS permission sets to the user group to which the user belongs.

OBS is a global service because it is available for all physical regions. IAM permissions are assigned to users in the global project, and users do not need to switch regions when accessing OBS.

You can grant permissions to users by roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism provides only a limited number of service-level roles for authorization. When using roles to grant permissions, you need to also assign other roles on which the permissions depend to take effect. However, roles are not an ideal choice for fine-grained authorization and secure access control.
-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant OBS users only the permissions for managing a certain type of OBS resources.

.. note::

   Due to data caching, a role and policy involving OBS actions will take effect 10 to 15 minutes after it is attached to a user, an enterprise project, and user group.

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
   | OBS Buckets Viewer   | Users with this permission can list buckets, obtain basic bucket information, and obtain bucket metadata.                                                                                                                                                                                          | System-defined role   | N/A             |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------+
   | OBS ReadOnlyAccess   | Users with this permission can list buckets, obtain basic bucket information, obtain bucket metadata, and list objects (not the objects that have been versioned).                                                                                                                                 | System-defined policy | N/A             |
   |                      |                                                                                                                                                                                                                                                                                                    |                       |                 |
   |                      | .. note::                                                                                                                                                                                                                                                                                          |                       |                 |
   |                      |                                                                                                                                                                                                                                                                                                    |                       |                 |
   |                      |    If a user with this permission fails to list objects on OBS Console, there may be multiple versions of objects in the bucket. In this case, you need to grant the user the **obs:bucket:ListBucketVersions** permission so that the user can view different versions of objects on OBS Console. |                       |                 |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------+
   | OBS OperateAccess    | Users with this permission can perform all OBS ReadOnlyAccess operations and perform basic object operations, such as uploading objects, downloading objects, deleting objects, and obtaining object ACLs.                                                                                         | System-defined policy | N/A             |
   |                      |                                                                                                                                                                                                                                                                                                    |                       |                 |
   |                      | .. note::                                                                                                                                                                                                                                                                                          |                       |                 |
   |                      |                                                                                                                                                                                                                                                                                                    |                       |                 |
   |                      |    If a user with this permission fails to list objects on OBS Console, there may be multiple versions of objects in the bucket. In this case, you need to grant the user the **obs:bucket:ListBucketVersions** permission so that the user can view different versions of objects on OBS Console. |                       |                 |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------+

The following table lists the common operations supported by each system-defined policy or role of OBS. Select the policies or roles as required.

.. table:: **Table 2** Permissions and the allowed operations on OBS resources

   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Operation                                                | Tenant Administrator | Tenant Guest | OBS Administrator | OBS Buckets Viewer | OBS ReadOnlyAccess | OBS OperateAccess |
   +==========================================================+======================+==============+===================+====================+====================+===================+
   | Listing buckets                                          | Yes                  | Yes          | Yes               | Yes                | Yes                | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Creating buckets                                         | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Deleting buckets                                         | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Obtaining basic bucket information                       | Yes                  | Yes          | Yes               | Yes                | Yes                | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Controlling bucket access                                | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing bucket policies                                 | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Modifying bucket storage classes                         | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Listing objects                                          | Yes                  | Yes          | Yes               | No                 | Yes                | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Listing versioned objects                                | Yes                  | Yes          | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Uploading a file                                         | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Creating a folder                                        | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Deleting a file                                          | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Deleting a folder                                        | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Downloading a file                                       | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Deleting files with multiple versions                    | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Downloading files with multiple versions                 | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Modifying object storage classes                         | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Restoring files                                          | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Undeleting a file                                        | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Deleting fragments                                       | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Controlling object access                                | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Configuring object metadata                              | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Obtaining object metadata                                | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing versioning                                      | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing logging                                         | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing event notifications                             | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing tags                                            | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing lifecycle rules                                 | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing static website hosting                          | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing CORS rules                                      | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing URL validation                                  | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Managing domain names                                    | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Configuring an object ACL                                | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Configuring the ACL for an object of a specified version | Yes                  | No           | Yes               | No                 | No                 | No                |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Obtaining an object ACL                                  | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Obtaining the ACL of a specified object version          | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Performing a multipart upload                            | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Listing uploaded parts                                   | Yes                  | Yes          | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+
   | Canceling a multipart upload                             | Yes                  | No           | Yes               | No                 | No                 | Yes               |
   +----------------------------------------------------------+----------------------+--------------+-------------------+--------------------+--------------------+-------------------+

Application Scenarios of IAM Permissions
----------------------------------------

IAM permissions are used to authorize IAM users under an account.

-  Controlling access to cloud resources as a whole under an account
-  Controlling access to all OBS buckets and objects under an account
-  Controlling access to specified OBS resources under an account

Policy Structure and Syntax
---------------------------

A policy consists of a version and statements. Each policy can have multiple statements.


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

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   +===================================+====================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | Version                           | The version number of a policy.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   | -  **1.0**: RBAC policies. An RBAC policy consists of permissions for an entire service. Users in a group with such a policy assigned are granted all of the permissions required for that service.                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                   | -  **1.1**: Fine-grained policies. A fine-grained policy consists of API-based permissions for operations on specific resource types. Fine-grained policies, as the name suggests, allow for more fine-grained control on specific operations and resources than RBAC policies. For example: You can restrict an IAM user to access only the objects in a specific directory of an OBS bucket.                                                                                                                                                                                                                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Statement                         | Detailed descriptions of a policy, including **Effect**, **Action**, **Resource**, and **Condition**. **Resource** and **Condition** are optional.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   | -  **Effect**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    The valid values for **Effect** are **Allow** and **Deny**. System policies contain only **Allow** statements. For custom policies containing both **Allow** and **Deny** statements, the **Deny** statements take precedence.                                                                                                                                                                                                                                                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   | -  **Action**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    Actions allowed on resources. An action is in the format of *Service name*:*Resource type*:*Action*. A policy can contain one or more actions. You can use a wildcard (``*``) to indicate all of the services, resource types, or actions depending on their location in the action. There are two types of OBS resources: buckets and objects.                                                                                                                                                                                                                                                                 |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   | -  **Resource**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    Resources on which the policy takes effect. A resource is in the format of *Service name*:*Region*:*Domain ID*:*Resource type*:*Resource path*. You can use a wildcard (``*``) to indicate all of the services, regions, domain IDs, resource types, or resource paths depending on their location in the resource. In the JSON view, if **Resource** is not specified, the policy takes effect for all resources.                                                                                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    The value of **Resource** supports uppercase (A to Z), lowercase (a to z) letters, digits (0 to 9), and the following characters: **-_*./\\**. If the value contains invalid characters, use the wildcard character (``*``).                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    OBS is a global service. Therefore, set **Region** to **\***. **Domain ID** indicates the ID of the resource owner. Set it to **\*** to indicate the ID of the account to which the resources belong.                                                                                                                                                                                                                                                                                                                                                                                                           |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    Examples:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    -  **obs:*:*:bucket:\***: all OBS buckets                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                                   |    -  **obs:*:*:object:my-bucket/my-object/\***: all objects in the **my-object** directory of the **my-bucket** bucket                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   | -  **Condition**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    When creating a custom policy, you can add condition elements to control when the policy takes effect. A condition consists of a condition key and an operator. Condition keys are either global or service-level and are used in the condition elements of a policy statement. Global condition keys (starting with **g:**) are available for actions of all services, while service-level condition keys (starting with a service name acronym like **obs:**) are available only for actions of a specific service. An operator is used together with a condition key to form a complete condition statement. |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    OBS has a group of predefined condition keys that can be used in IAM. For example, to define an allow permission, you can use the condition key **obs:SourceIp** to filter matching requesters by IP address.                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    The condition keys and operators supported by OBS are the same as those in the bucket policy. When configuring condition keys in IAM, start the condition keys and operators with **obs:**. For detailed condition information, see :ref:`Bucket Policy Parameters <obs_40_0041>`.                                                                                                                                                                                                                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    The value of **Condition** can contain only uppercase letters (A to Z), lowercase letters (a to z), digits (0 to 9), and the following characters: **-,./_@#$%&**. If the value contains unsupported characters, consider using the condition operators (such as StringLike and StringStartWith) for fuzzy match.                                                                                                                                                                                                                                                                                               |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    Examples:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |    -  **StringEndWithIfExists":{"g:UserName":["specialCharacter"]}**: The statement is valid for users whose names end with **specialCharacter**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |                                   |    -  **"StringLike":{"obs:prefix":["private/"]}**: When listing objects in a bucket, you need to set prefix to **private/** or include **private/**.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Configuring IAM Permissions
---------------------------

-  `Creating a User and Granting OBS Permissions <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0122.html>`__
-  `Creating a Custom Policy <https://docs.otc.t-systems.com/en-us/usermanual/iam/en-us_topic_0274187246.html>`__

Example Custom Policies
-----------------------

-  **Example 1: Grant all OBS permissions to users.**

   This policy allows users to perform any operation on OBS using the API, SDKs, OBS Console, or tools.

   When a user logs in to OBS Console, the user accesses resources of other services, such as audit information in CTS, acceleration domain names in CDN, and keys in KMS. Therefore, in addition to the OBS permissions, you need to grant users the permissions for other services. CDN is a global service, while CTS, SMN, and KMS are regional ones. You need to configure the **Tenant Guest** permission for the global project and regional projects based on the services and regions that you use.

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

-  **Example 2: Grant the read-only permission on a bucket to users (any directory).**

   This policy allows users to list and download all objects in bucket **obs-example**.

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

-  **Example 3: Grant the read-only permission on a bucket to users (specified directory).**

   This policy allows users to only download objects in the **my-project/** directory of bucket **obs-example**. Objects in other directories can be listed but cannot be downloaded.

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

-  **Example 4: Grant the read and write permissions on a bucket to users (specified directory).**

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

-  **Example 5: Grant all permissions on a bucket to users.**

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

-  **Example 6: Deny a user the permission to upload objects.**

   A policy with only "Deny" permissions must be used in conjunction with other policies to take effect. If the permissions assigned to a user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   The following method can be used if you need to assign permissions of the **OBS OperateAccess** policy to a user but also forbid the user from uploading objects. Create a custom policy for denying object upload, and assign both policies to the user. Then the user can perform all **OBS OperateAccess** permissions except uploading objects. The following is an example of a deny policy:

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

-  **Example 7: Grant users the permissions required to change a bucket's storage class and to delete certain objects in the bucket.**

   This policy allows users to change the storage class of bucket **obs-example** and to delete object **my-object.txt** in the bucket.

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
