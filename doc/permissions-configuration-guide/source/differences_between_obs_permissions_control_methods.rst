:original_name: obs_40_0001.html

.. _obs_40_0001:

Differences Between OBS Permissions Control Methods
===================================================

By default, OBS resources (buckets and objects) are private. Only resource owners can access their OBS resources. Other users cannot access such resources without authorization. OBS permission control helps you control access from other accounts or IAM users. For example, you can authorize another IAM user to upload objects to your bucket. You can also grant permissions to non-public cloud users, so that they can access your bucket over the Internet. OBS provides different methods for resource owners to grant permissions to others as needed.

OBS Permission Control Methods
------------------------------

OBS provides multiple permission control methods, including IAM permissions, bucket policies, object ACLs, and bucket ACLs. :ref:`Table 1 <obs_40_0001__table16110824101113>` describes the methods and their application scenarios.


.. figure:: /_static/images/en-us_image_0257815079.png
   :alt: **Figure 1** OBS permission control methods

   **Figure 1** OBS permission control methods

.. _obs_40_0001__table16110824101113:

.. table:: **Table 1** OBS permission control methods and application scenarios

   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Method                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                | Scenario                                                                                                                                                                                                                                                                                                                                                                           |
   +=======================+============================================================================================================================================================================================================================================================================================================================================================================================================================================+====================================================================================================================================================================================================================================================================================================================================================================================+
   | IAM permissions       | IAM permissions define the actions that can be performed on your cloud resources. In other words, IAM permissions specify what actions are allowed or denied. After an IAM user is created, the administrator needs to add the user to a group. IAM can grant the user group required permissions so that all users in the group automatically inherit the permissions of the user group.                                                  | -  Controlling access to all OBS buckets under an account                                                                                                                                                                                                                                                                                                                          |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                            | -  Controlling access to all OBS objects under an account                                                                                                                                                                                                                                                                                                                          |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                            | -  Controlling access to specified OBS resources under an account                                                                                                                                                                                                                                                                                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Bucket policies       | A bucket policy is attached to a bucket and objects in the bucket. Bucket owners can use bucket policies to grant IAM users or other accounts the permissions to operate buckets and objects in the buckets. ACLs of buckets and objects supplement bucket policies, and in many cases, bucket policies replace ACLs.                                                                                                                      | -  Granting other accounts the permissions to access buckets                                                                                                                                                                                                                                                                                                                       |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                            | -  Granting IAM users the permissions to access buckets                                                                                                                                                                                                                                                                                                                            |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Object ACLs           | Object owners can configure object access control lists (ACLs) to grant read and write permissions to specified accounts or user groups.                                                                                                                                                                                                                                                                                                   | -  If object-level access control is required, you can configure a bucket policy to grant the permissions to an object or a set of objects. If you have configured the permissions for a set of objects, it is not practical to configure a bucket policy to control access to each object separately. Instead, you can configure the object ACL to control access to each object. |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                            | -  An object can be accessed through a URL. If you want to grant anonymous users the permission to read an object through a URL, you can configure an object ACL.                                                                                                                                                                                                                  |
   |                       | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |    -  By default, an object ACL is created when the object is uploaded, granting the object owner the full control over the object.                                                                                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |    -  An object owner is the account that uploads the object and is not necessarily the owner of the bucket that stores the object. For example, account **B** is granted the permission to access a bucket of account **A**, and account **B** uploads a file to the bucket. In that case, account **B** is the owner of the object. By default, account A is not allowed to access this object and cannot read or modify the object ACL. |                                                                                                                                                                                                                                                                                                                                                                                    |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Bucket ACLs           | Bucket owners can configure bucket ACLs to grant read and write permissions to specified accounts or user groups.                                                                                                                                                                                                                                                                                                                          | -  Granting an account the read and write permissions to a bucket for sharing data in the bucket or adding external buckets. For example, after account **A** grants account **B** the read and write permissions to a bucket, account **B** can access the bucket by adding an external bucket through OBS Browser+ or using APIs and SDKs.                                       |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                            | -  Granting the log delivery user write permissions to the bucket that stores access logs.                                                                                                                                                                                                                                                                                         |
   |                       | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |    -  By default, a bucket ACL is created when the bucket is created, granting the bucket owner the full control over the bucket.                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |    -  Bucket ACLs do not provide fine-grained permission control. Generally, IAM permissions and bucket policies are recommended.                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                    |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Relationships Between OBS Permissions and IAM Permissions
---------------------------------------------------------

OBS provides multiple permission control methods, including time-limited access to objects, object ACLs, bucket ACLs, and bucket policies. Some service-level permissions (for example, creating a bucket and listing all buckets) cannot be configured through OBS and can only be configured on IAM. OBS permissions apply only to resources (buckets and objects). To grant both OBS service-level and resource-level permissions, you must use IAM permissions or both IAM and OBS permissions.


.. figure:: /_static/images/en-us_image_0257817646.png
   :alt: **Figure 2** Relationships between OBS permissions and IAM permissions

   **Figure 2** Relationships between OBS permissions and IAM permissions

OBS Permission Control Elements
-------------------------------

Authorization is determined by:

-  **Principal (authorized user)**
-  **Effect**
-  **Resource**
-  **Action**
-  **Condition**

For details about these elements, see :ref:`Bucket Policy Parameters <obs_40_0041>`.

:ref:`Table 2 <obs_40_0001__table260016521874>` describes the elements in different permission control methods.

.. _obs_40_0001__table260016521874:

.. table:: **Table 2** Elements in different OBS permission control methods

   +-----------------+-----------------------------+-----------+----------------------------------------------+-------------------------------------------------------------------------------------------+---------------+
   | Method          | Principal                   | Effect    | Resource                                     | Action                                                                                    | Condition     |
   +=================+=============================+===========+==============================================+===========================================================================================+===============+
   | IAM Permissions | IAM users                   | -  Allow  | All or specified OBS resources               | Access OBS                                                                                | Supported     |
   |                 |                             | -  Deny   |                                              |                                                                                           |               |
   +-----------------+-----------------------------+-----------+----------------------------------------------+-------------------------------------------------------------------------------------------+---------------+
   | Bucket Policies | -  Accounts                 | -  Allow  | Specified bucket and resources in the bucket | Access OBS                                                                                | Supported     |
   |                 | -  IAM users                | -  Deny   |                                              |                                                                                           |               |
   |                 | -  Anonymous users          |           |                                              |                                                                                           |               |
   +-----------------+-----------------------------+-----------+----------------------------------------------+-------------------------------------------------------------------------------------------+---------------+
   | Object ACLs     | -  Accounts                 | Allow     | Specified object                             | -  Obtain the content and metadata of a specified object.                                 | Not supported |
   |                 | -  Anonymous users          |           |                                              | -  Obtain the content and metadata of an object of a specified version.                   |               |
   |                 |                             |           |                                              | -  Obtain information about an object ACL.                                                |               |
   |                 |                             |           |                                              | -  Obtain information about the ACL for an object of a specified version.                 |               |
   |                 |                             |           |                                              | -  Configure an ACL for an object.                                                        |               |
   |                 |                             |           |                                              | -  Configure an ACL for an object of a specified version.                                 |               |
   +-----------------+-----------------------------+-----------+----------------------------------------------+-------------------------------------------------------------------------------------------+---------------+
   | Bucket ACLs     | -  Accounts                 | Allow     | Specified bucket                             | -  Identify whether a bucket exists.                                                      | Not supported |
   |                 | -  Anonymous users          |           |                                              | -  List objects in a bucket, and obtain the bucket metadata.                              |               |
   |                 | -  Log delivery user groups |           |                                              | -  List versioned objects in a bucket.                                                    |               |
   |                 |                             |           |                                              | -  List multipart uploads.                                                                |               |
   |                 |                             |           |                                              | -  Upload using PUT and POST, upload multiparts, and initialize and merge uploaded parts. |               |
   |                 |                             |           |                                              | -  Delete an object.                                                                      |               |
   |                 |                             |           |                                              | -  Delete an object of a specified version.                                               |               |
   |                 |                             |           |                                              | -  Obtain bucket ACL information.                                                         |               |
   |                 |                             |           |                                              | -  Configure a bucket ACL.                                                                |               |
   |                 |                             |           |                                              | -  Obtain object content.                                                                 |               |
   |                 |                             |           |                                              | -  Obtain object metadata.                                                                |               |
   +-----------------+-----------------------------+-----------+----------------------------------------------+-------------------------------------------------------------------------------------------+---------------+

Which Permissions Should I Select?
----------------------------------

Considering the advantages and disadvantages of the elements, you are advised to use IAM permissions and bucket policies.

-  Select IAM permissions to:

   -  Grant the same permissions to numerous IAM users under the same account.
   -  Grant the same permissions to all OBS resources or multiple buckets.
   -  Configure OBS service-level permissions, such as creating and listing buckets.
   -  Restrict the permissions of temporary access keys used for OBS access.

-  Select bucket policies to:

   -  Grant permissions across accounts or to anonymous users.
   -  Grant different permissions to different IAM users under the same account.

-  Are you still unsure what to select?

   Identify what you are most concerned about:

   -  If you want to control what a user can do, choose IAM permissions.

      You can search for an IAM user and check the permissions of the user group to which the user belongs to see what the user can do.

   -  If you want to control access to a bucket, choose bucket policies.

      You can query the bucket and check the bucket policy to know who can access the bucket.

.. note::

   To ensure easier permission maintenance, it is recommended to use the same method for permission control, especially as the number of IAM permissions and bucket policies grows.

**Configure an ACL if you want to:**

-  Grant permissions to a single object:

   If you already have IAM permissions and bucket policies configured for a set of objects, you can use an ACL to grant permissions to a single object in the set.

-  Allow an object to be accessible to all anonymous Internet users:

   You can use an ACL header to specify read and write permissions on an object during upload.

Relationships Between Bucket ACLs and Bucket Policies
-----------------------------------------------------

Bucket ACLs control read and write permissions on buckets. Custom bucket policies allow a more refined control over more actions on buckets. In many cases, bucket policies can replace bucket ACLs to manage access to buckets more precisely. :ref:`Relationship Between Bucket ACLs and Bucket Policies <obs_40_0043>` shows the mapping between bucket ACLs and bucket policies.

OBS Permission Control Principles
---------------------------------

-  Least privilege

   Grant IAM users only the minimum permissions needed to complete a task. For example, if an IAM user only needs to upload and download objects to a directory, grant this user only the permissions to do so.

-  Separation of duties

   Assign different IAM users to manage resources and permissions. For example, you can let one IAM user assign permissions, and let another IAM user manage OBS resources.

-  Restriction by condition

   To enhance the security of the resources in a bucket, you can configure specific conditions to control when a permission is applied. For example, you can configure a bucket policy for OBS to accept requests only from a specific IP address.

Which Permissions Apply When They Conflict?
-------------------------------------------

In the OBS permission control elements, there are allow and deny effects, which indicate the permission to allow or deny an action.

Following the least-privilege principle, the permission is defaulted to deny, and an explicit deny statement always takes precedence over an allow statement. For example, if IAM permissions grant a user access to an object, a bucket policy denies the user's access to that object, and there is no ACL, this user's access will be denied.

If no method specifies an allow statement, then the request will be denied by default. Only if no method specifies a deny statement and one or more methods specify an allow statement, will the request be allowed. For example, if a bucket has multiple bucket policies with allow statements, adding such a new bucket policy applies the allowed permissions to the bucket, but adding a new bucket policy with a deny statement will make the permissions work differently. The deny statement will take precedence over allow statements, even if the denied permissions are allowed in other bucket policies.


.. figure:: /_static/images/en-us_image_0000001664558420.png
   :alt: **Figure 3** Authorization process

   **Figure 3** Authorization process

:ref:`Figure 4 <obs_40_0001__fig2276143024512>` describes which action (allow or deny) to take when bucket policies, IAM permissions, and ACLs for the IAM users of your account conflict. ACLs are applied to accounts and do not control IAM users' read and write permissions for the buckets and their objects.

.. _obs_40_0001__fig2276143024512:

.. figure:: /_static/images/en-us_image_0000001479778546.png
   :alt: **Figure 4** Action (allow or deny) to take when bucket policies and IAM permissions for IAM users conflict under an account

   **Figure 4** Action (allow or deny) to take when bucket policies and IAM permissions for IAM users conflict under an account

:ref:`Figure 5 <obs_40_0001__fig1251114133010>` describes which action (allow or deny) to take when bucket policies, IAM permissions, and ACLs for any other account and the IAM users of this account conflict.

.. _obs_40_0001__fig1251114133010:

.. figure:: /_static/images/en-us_image_0000001555603997.png
   :alt: **Figure 5** Action (allow or deny) to take when bucket policies, IAM permissions, and ACLs conflict in cross-account scenarios

   **Figure 5** Action (allow or deny) to take when bucket policies, IAM permissions, and ACLs conflict in cross-account scenarios

.. note::

   -  If both the bucket policy and IAM policy are set to **Default Deny**, but the ACL is set to **Allow**, the final result is **Deny**. ACLs are used to supplement bucket policies.
   -  If both the bucket policy and ACL are set to **Default Deny** and the IAM policy is set to **Allow**, the final result is **Deny**. IAM policies are applied to users, while bucket policies are applied to resources. Even if the **Allow** permission is granted to users, they still cannot access the resources if the resources have the **Deny** permission configured.

Concepts
--------

-  Domain: An account that is automatically created during your registration. This account has full access control over its resources and IAM users.
-  IAM user: A user created by the administrator in IAM. An IAM user may be an employee, a system, or an application. An IAM user is usually granted the permissions to access specified resources. IAM users have identity credentials (passwords and access keys) and can log in to the management console or call APIs.
-  Anonymous user: A visitor who has not registered.
-  A log delivery user group: A user group that delivers access logs of buckets and objects to a specified bucket. OBS does not create or upload any file to a bucket automatically. If you want to record access logs for a bucket, you must grant the log delivery user group required permissions, so that OBS can write the access logs to the specified bucket. This user group is only used to record internal logs of OBS.
