:original_name: obs_40_0001.html

.. _obs_40_0001:

Introduction to OBS Access Control
==================================

By default, OBS resources (buckets and objects) are private. Only resource owners can access their OBS resources. Without authorization, other users cannot access OBS. OBS permission control refers to granting permissions to other accounts or IAM users by editing access policies. For example, if you have a bucket, you can authorize another IAM user to upload objects to your bucket. You can also open buckets to non-public cloud users, so that anyone can access your buckets as public resources over the Internet. OBS offers different methods to help resource owners grant resource permissions to others as required, keeping data secure.

OBS Permission Control Model
----------------------------

OBS provides multiple permission control mechanisms, including IAM permissions, bucket policies, object ACLs, and bucket ACLs. :ref:`Table 1 <obs_40_0001__table16110824101113>` describes the mechanisms and application scenarios.


.. figure:: /_static/images/en-us_image_0257815079.png
   :alt: **Figure 1** OBS permission control mechanisms

   **Figure 1** OBS permission control mechanisms

.. _obs_40_0001__table16110824101113:

.. table:: **Table 1** OBS permission control mechanisms and application scenarios

   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Method                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Scenario                                                                                                                                                                                                                                                                                                                                                                                                          |
   +=======================+================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+===================================================================================================================================================================================================================================================================================================================================================================================================================+
   | IAM permissions       | IAM permissions define the actions that can be performed on your cloud resources. In other words, IAM permissions specify what actions are allowed or denied. After an IAM user is created, the administrator needs to add the user to a group. IAM can grant the user group required OBS access permissions, and then all users in the group automatically inherit the permissions of the user group.                                                                         | -  Controlling access to all OBS buckets under an account                                                                                                                                                                                                                                                                                                                                                         |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | -  Controlling access to all OBS objects under an account                                                                                                                                                                                                                                                                                                                                                         |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | -  Controlling access to specified OBS resources under an account                                                                                                                                                                                                                                                                                                                                                 |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Bucket policies       | A bucket policy is attached to a bucket and objects in the bucket. Bucket owners can use bucket policies to grant IAM users or other accounts the permissions to operate buckets and objects in the buckets. ACLs of buckets and objects supplement bucket policies, and in many cases, bucket policies replace ACLs.                                                                                                                                                          | -  Granting other accounts the permissions to access OBS resources                                                                                                                                                                                                                                                                                                                                                |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | -  Configuring bucket policies to grant IAM users various access permissions to different buckets                                                                                                                                                                                                                                                                                                                 |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Object ACLs           | Controls access to objects for accounts or user groups. Object owners can configure the object access control list (ACL) to grant basic read and write permissions to specified accounts or user groups.                                                                                                                                                                                                                                                                       | -  If object-level access control is required, a bucket policy can be used to grant the access permission to an object or a set of objects. After the access permission is granted to an object set, it is not practical to configure a bucket policy to grant the access permission to an object in the object set separately. Then the object ACL is recommended for easier access control over single objects. |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | -  An object is accessed through a URL. Generally, if you want to grant anonymous users the permission to read an object through a URL, use the object ACL.                                                                                                                                                                                                                                                       |
   |                       | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |    -  By default, an object ACL is created upon the creation of the object. The object owner has full control over the object.                                                                                                                                                                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |    -  An object owner is the account that uploads the object, but may not be the owner of the bucket that stores the object. For example, account **B** is granted the permission to access a bucket of account **A**, and account **B** uploads a file to the bucket. In that case, instead of the bucket owner account **A**, account **B** is the owner of the object. By default, account A is not allowed to access this object and cannot read or modify the object ACL. |                                                                                                                                                                                                                                                                                                                                                                                                                   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Bucket ACLs           | Controls access to buckets for accounts or user groups. Bucket owners can configure the bucket ACL to grant basic read and write permissions to specified accounts or user groups.                                                                                                                                                                                                                                                                                             | -  Granting an account the read and write access to a bucket, so that data in the bucket can be shared or external buckets can be added. For example, after account **A** grants account **B** the read and write access to a bucket, account **B** can access the bucket by adding an external bucket through OBS Browser+ or using APIs and SDKs.                                                               |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | -  Grant the log delivery user group with the write access to the target bucket, so that access logs can be delivered to the target bucket.                                                                                                                                                                                                                                                                       |
   |                       | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |    -  By default, a bucket ACL is created upon the creation of the bucket. The bucket owner has full control over the bucket.                                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |    -  Bucket ACLs do not provide fine-grained permission control. Generally, IAM permissions and bucket policies are recommended.                                                                                                                                                                                                                                                                                                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Relationship Between OBS Permissions and IAM Permissions
--------------------------------------------------------

OBS provides multiple permission control mechanisms, including time-limited access to objects, object ACLs, bucket ACLs, and bucket policies. Some service-level permissions (for example, creating a bucket and listing all buckets) cannot be configured through OBS and can only be configured on IAM. OBS permissions apply only to resources (buckets and objects). To grant both OBS service-level and resource-level permissions, you must use IAM permissions or both IAM and OBS permissions.


.. figure:: /_static/images/en-us_image_0257817646.png
   :alt: **Figure 2** Relationship between OBS permissions and IAM permissions

   **Figure 2** Relationship between OBS permissions and IAM permissions

OBS Permission Control Elements
-------------------------------

The following factors determine the authorization result:

-  **Principal (authorized user)**
-  **Effect**
-  **Resource**
-  **Action**
-  **Condition**

For details about elements, see :ref:`Bucket Policy Parameters <obs_40_0041>`.

:ref:`Table 2 <obs_40_0001__table260016521874>` describes elements in different permission control mechanisms.

.. _obs_40_0001__table260016521874:

.. table:: **Table 2** OBS permission control elements in different permission control mechanisms

   +-----------------+-----------------------------+------------------+----------------------------------------------+----------------------------------------------------------------------------------------------------------------+-------------------------+
   | Method          | Principal                   | Supported Effect | Authorized Resource                          | Authorized Action                                                                                              | Condition Configuration |
   +=================+=============================+==================+==============================================+================================================================================================================+=========================+
   | IAM Permissions | IAM user                    | -  Allow         | All or specified OBS resources               | All permissions to access OBS                                                                                  | Supported               |
   |                 |                             | -  Deny          |                                              |                                                                                                                |                         |
   +-----------------+-----------------------------+------------------+----------------------------------------------+----------------------------------------------------------------------------------------------------------------+-------------------------+
   | Bucket Policy   | -  Account                  | -  Allow         | Specified bucket and resources in the bucket | All permissions to access OBS                                                                                  | Supported               |
   |                 | -  IAM user                 | -  Deny          |                                              |                                                                                                                |                         |
   |                 | -  Anonymous users          |                  |                                              |                                                                                                                |                         |
   +-----------------+-----------------------------+------------------+----------------------------------------------+----------------------------------------------------------------------------------------------------------------+-------------------------+
   | Object ACL      | -  Account                  | Allow            | Specified object                             | -  Obtains the content and metadata of a specified object.                                                     | Not supported           |
   |                 | -  Anonymous users          |                  |                                              | -  Obtains the content and metadata of an object with a specified version.                                     |                         |
   |                 |                             |                  |                                              | -  Obtains information about an object ACL.                                                                    |                         |
   |                 |                             |                  |                                              | -  Obtains information about the ACL for an object of a specified version.                                     |                         |
   |                 |                             |                  |                                              | -  Configures an object ACL.                                                                                   |                         |
   |                 |                             |                  |                                              | -  Configures the ACL for an object of a specified version.                                                    |                         |
   +-----------------+-----------------------------+------------------+----------------------------------------------+----------------------------------------------------------------------------------------------------------------+-------------------------+
   | Bucket ACL      | -  Account                  | Allow            | Specified bucket                             | -  Identifies whether a bucket exists.                                                                         | Not supported           |
   |                 | -  Anonymous users          |                  |                                              | -  Lists objects in a bucket, and gets the bucket metadata.                                                    |                         |
   |                 | -  Log delivery user groups |                  |                                              | -  Lists versioned objects in a bucket.                                                                        |                         |
   |                 |                             |                  |                                              | -  Lists multipart uploads.                                                                                    |                         |
   |                 |                             |                  |                                              | -  Performs PUT upload, POST upload, multipart upload, initialization of uploaded parts, and merging of parts. |                         |
   |                 |                             |                  |                                              | -  Deletes an Object.                                                                                          |                         |
   |                 |                             |                  |                                              | -  Deletes an object of a specified version.                                                                   |                         |
   |                 |                             |                  |                                              | -  Obtains bucket ACL information.                                                                             |                         |
   |                 |                             |                  |                                              | -  Configures a bucket ACL.                                                                                    |                         |
   |                 |                             |                  |                                              | -  Obtains object content.                                                                                     |                         |
   |                 |                             |                  |                                              | -  Obtains object metadata.                                                                                    |                         |
   +-----------------+-----------------------------+------------------+----------------------------------------------+----------------------------------------------------------------------------------------------------------------+-------------------------+

How to Select IAM Permissions, Bucket Policies, and ACLs
--------------------------------------------------------

Based on the advantages and disadvantages of the three elements, you are advised to preferentially use IAM permissions and bucket policies.

-  Select IAM permissions in the following scenarios:

   -  Grant the same permissions to numerous IAM users under the same account.
   -  Grant the same permissions to all OBS resources or multiple buckets.
   -  Configure OBS service-level permissions, such as creating and listing buckets.
   -  Restrict the permissions of temporary access keys used for temporarily authorized access to OBS.

-  Select bucket policies in the following scenarios:

   -  Grant permissions across accounts or grant permissions to anonymous users.
   -  Grant different permissions to different IAM users under the same account.

-  Still do not know what to select?

   Identify the problem you are most concerned with:

   -  What the user can do - IAM permissions recommended

      You can search for an IAM user and check the permissions of the user group to which the user belongs to know what the user can do.

   -  Who can access an OBS bucket - Bucket policies recommended

      You can query the bucket and check the bucket policy to know who can access the bucket.

.. note::

   It is better for you to use the same method for access control, because as the number of IAM permissions and bucket policies increase, access maintenance will become increasingly difficult.

**When to Select an ACL?**

-  As a supplement to IAM permissions and bucket policies:

   IAM permissions and bucket policies have granted access permissions to an object set, but you want to grant access permissions to a single object.

-  To allow an object to be accessible to all anonymous Internet users, configuring object ACL operations is more convenient.

   When uploading an object, you can use the ACL header to specify the read and write permissions of the object.

Relationship Between Bucket ACLs and Bucket Policies
----------------------------------------------------

Bucket ACLs are used to control basic read and write access to buckets. Custom settings of bucket policies support more actions that can be performed on buckets. Bucket ACLs supplement bucket policies. In many cases, bucket policies can replace bucket ACLs to manage access to buckets. :ref:`Relationship Between Bucket Policies and Bucket ACLs <obs_40_0043>` shows the mapping between bucket ACL access permissions and bucket policy actions.

OBS Permission Control Principles
---------------------------------

-  Least privilege

   Never grant IAM users more than the minimum level of access needed to complete a task. For example, if an IAM user only needs to upload and download objects to a directory, you do not need to assign the user the read and write permissions for the entire bucket.

-  Separation of duties

   Management of resources or of permissions can be assigned to different IAM users. For example, you can let one IAM user assign permissions, and let other IAM users manage OBS resources.

-  Restriction by condition

   To enhance the security of the resources in a bucket, specific conditions can be configured to control when a permission is applied. For example, a bucket policy with conditions contained can be configured for OBS to accept requests only from a specific IP address.

How Do Access Control Mechanisms Work When They Conflict?
---------------------------------------------------------

In the OBS permission control elements, there are allow and deny effects, which indicate the permission to allow or deny an operation.

Based on the least-privilege principle, decisions default to deny, and an explicit deny statement always takes precedence over an allow statement. For example, IAM permissions grant a user access to an object, a bucket policy denies the user's access to that object, and there is no ACL. Then access will be denied.

If no method specifies an allow statement, then the request will be denied by default. Only if no method specifies a deny statement and one or more methods specify an allow statement, will the request be allowed. For example, if a bucket has multiple bucket policies with allow statements, adding such a new bucket policy applies the allowed permissions to the bucket, but adding a new bucket policy with a deny statement will make the permissions work differently. The deny statement will take precedence over allow statements, even if the denied permissions are allowed in other bucket policies.


.. figure:: /_static/images/en-us_image_0000001335934590.png
   :alt: **Figure 3** Authorization process

   **Figure 3** Authorization process

:ref:`Figure 4 <obs_40_0001__fig2276143024512>` describes how bucket policies, IAM permissions, and ACLs work (allow or deny) when you grant the IAM users of your account the access to OBS buckets and resources in the buckets. ACLs are applied to accounts and do not control IAM users' read and write permissions for the buckets and the sources in the buckets under their account.

.. _obs_40_0001__fig2276143024512:

.. figure:: /_static/images/en-us_image_0000001479778546.png
   :alt: **Figure 4** Working mechanisms (allow or deny) of bucket policies and IAM permissions in the same account

   **Figure 4** Working mechanisms (allow or deny) of bucket policies and IAM permissions in the same account

:ref:`Figure 5 <obs_40_0001__fig1251114133010>` describes how bucket policies, IAM permissions, and ACLs work (allow or deny) when you grant any other account and the IAM users of this account the access to OBS buckets and resources in the buckets.

.. _obs_40_0001__fig1251114133010:

.. figure:: /_static/images/en-us_image_0000001555603997.png
   :alt: **Figure 5** Working mechanisms (allow or deny) of bucket policies, IAM permissions, and ACLs in cross-account access grant scenarios

   **Figure 5** Working mechanisms (allow or deny) of bucket policies, IAM permissions, and ACLs in cross-account access grant scenarios

.. note::

   -  If both the bucket policy and IAM policy are set to **Default Deny**, but the ACL is set to **Allow**, the final result is **Deny**. ACLs are used to supplement bucket policies.
   -  If both the bucket policy and ACL are set to **Default Deny** and the IAM policy is set to **Allow**, the final result is **Deny**. IAM policies are applied to users, while bucket policies are applied to resources. Even if the **Allow** permission is granted to users, they still cannot access the resources if the resources have the **Deny** permission configured.

Concepts
--------

-  Domain: An account that is automatically created during your registration. This account has full access control over its resources and IAM users.
-  IAM user: A user created by the administrator in IAM. An IAM user may be an employee, a system, or an application. An IAM user has access permissions to specified resources. IAM users have identity credentials (passwords and access keys) and can log in to the management console or call APIs.
-  Anonymous user: A common visitor who has not registered.
-  A log delivery user group: A user group who only delivers access logs of buckets and objects to the specified target bucket. OBS does not create or upload any file to a bucket automatically. If you want to record access logs for a bucket, you must grant the log delivery user group required permissions, so that OBS can write the access logs to the specified bucket. This user group is only used to record internal logs of OBS.
