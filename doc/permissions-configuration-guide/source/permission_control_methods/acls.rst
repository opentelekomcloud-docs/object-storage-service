:original_name: obs_40_0005.html

.. _obs_40_0005:

ACLs
====

An access control list (ACL) is a list of rules that specifies which users or systems are granted or denied access to a particular bucket or object.

Bucket and object ACLs are attached to accounts. By default, an ACL is created when a bucket or object is created, authorizing the owner the full control over the bucket or object.

To implement simple and practical authorization for users, OBS ACL has the following features:

-  An ACL applies to both the account and the users under the account.
-  If a bucket and its objects have the same owner, the ACL configured on the bucket also applies to the objects in the bucket by default.
-  An ACL can be created together with a bucket or its object. You can also configure one after the bucket or object is created.

ACLs are write and read permissions attached to accounts, and are not as fine-grained as bucket policies and IAM policies. It is recommended that you use IAM permissions and bucket policies for access control.

You can grant bucket access permissions to users or user groups listed in :ref:`Table 1 <obs_40_0005__table177445813209>` by configuring an ACL.

.. _obs_40_0005__table177445813209:

.. table:: **Table 1** Users for whom you can create an ACL to grant bucket access permissions

   +-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Principal                                                                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                          |
   +===================================================================================+======================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | Specific users                                                                    | ACLs can be used to grant accounts permissions to access buckets and objects. Once a specific account is granted such permissions, all IAM users under this account have the same permissions as this account.                                                                                                                                                                                                                       |
   |                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                                                                   | If you want to grant different permissions to different IAM users, you can configure bucket policies.                                                                                                                                                                                                                                                                                                                                |
   +-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Owner                                                                             | The owner of a bucket is the account that created the bucket. The bucket owner has all permissions for the bucket by default. The read and write permissions to the bucket ACL are permanently available to the bucket owner, and cannot be modified.                                                                                                                                                                                |
   |                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                                                                   | An object owner is the account that uploads the object and is not necessarily the owner of the bucket that stores the object. The object owner has all control over the object by default. The read and write permissions to the object ACL are permanently available to the object owner, and cannot be modified.                                                                                                                   |
   |                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                                                                   | .. important::                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                                                                   |    NOTICE:                                                                                                                                                                                                                                                                                                                                                                                                                           |
   |                                                                                   |    Do not modify the bucket owner's read and write permissions for the bucket.                                                                                                                                                                                                                                                                                                                                                       |
   +-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Anonymous users                                                                   | Visitors who have not registered.                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                                                                   | .. important::                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                                                                   |    NOTICE:                                                                                                                                                                                                                                                                                                                                                                                                                           |
   |                                                                                   |    If the permissions to access a bucket or an object are granted to anonymous users, everyone can access the bucket or an object without authentication.                                                                                                                                                                                                                                                                            |
   +-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Log delivery user groups                                                          | A log delivery user group only delivers access logs of buckets and objects to the configured target bucket. OBS does not create or upload any file to a bucket automatically. Therefore, if you want to record access logs for buckets, you need to grant the permission to a log delivery user group who will deliver the access logs to your specified target bucket. This user group is only used to record internal logs of OBS. |
   |                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   | .. note::                                                                         | .. important::                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |    Only the bucket ACL supports authorizing permissions to the log delivery user. |    NOTICE:                                                                                                                                                                                                                                                                                                                                                                                                                           |
   |                                                                                   |    After logging is enabled, the log delivery user will be automatically granted the permission to read the bucket ACL and write the bucket where logs are saved. If you manually disable such permissions, bucket logging fails.                                                                                                                                                                                                    |
   +-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Bucket ACL
----------

:ref:`Table 2 <obs_40_0005__table28226836>` lists the permissions of a bucket ACL.

.. _obs_40_0005__table28226836:

.. table:: **Table 2** Bucket ACL permissions

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
   | Permission            | Option                | Description                                                                                            |
   +=======================+=======================+========================================================================================================+
   | Access to bucket      | Read                  | A user with this permission can obtain the list of objects in a bucket and the metadata of the bucket. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
   |                       | Read                  | A user with this permission can obtain the object content and metadata.                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
   |                       | Write                 | A user with this permission can upload, overwrite, and delete any object in a bucket.                  |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
   | Access to ACL         | Read                  | A user with this permission can obtain the ACL of the bucket.                                          |
   |                       |                       |                                                                                                        |
   |                       |                       | The bucket owner has this permission permanently by default.                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
   |                       | Write                 | A user with this permission can update the ACL of the bucket.                                          |
   |                       |                       |                                                                                                        |
   |                       |                       | The bucket owner has this permission permanently by default.                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+

:ref:`Table 3 <obs_40_0005__table63381242464>` lists the permissions of an object ACL.

.. _obs_40_0005__table63381242464:

.. table:: **Table 3** Object ACL permissions

   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | Permission            | Option                | Description                                                                   |
   +=======================+=======================+===============================================================================+
   | Access to object      | Read                  | A user with this permission can obtain the content and metadata of an object. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   | Access to ACL         | Read                  | A user with this permission can obtain the object ACL.                        |
   |                       |                       |                                                                               |
   |                       |                       | The object owner has this permission permanently by default.                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+
   |                       | Write                 | A user with this permission can update the ACL of the object.                 |
   |                       |                       |                                                                               |
   |                       |                       | The object owner has this permission permanently by default.                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------+

.. note::

   Every time you change the permissions for a bucket or an object in an ACL, it overwrites the existing permissions instead of adding permissions to the bucket or object.

Application Scenarios of Bucket ACLs
------------------------------------

You can configure bucket ACLs to:

-  Grant an account the read and write permissions to a bucket, so that this account can add the bucket as an external one and access objects in the bucket. For example, if you grant an account the read and write permissions to a bucket, the account can access the bucket by adding it as an external bucket through OBS Browser+ or by using APIs.
-  Grant the log delivery user group the write permissions to a bucket that stores access logs.

Application Scenarios of Object ACLs
------------------------------------

You can configure object ACLs to:

-  Control access to objects. A bucket policy can control access to a single object or a set of objects. If you want to further control access to a single object in the set of objects for which a bucket policy has been configured, use the object ACL.
-  Access an object through a URL. If you want to grant anonymous users the permission to read an object through a URL, use the object ACL.

Configuring an ACL Using Header Fields
--------------------------------------

**Access Control Policies**

You can set an access control policy in a header when creating a bucket or uploading an object (for details, see `Creating a Bucket <https://docs.otc.t-systems.com/en-us/api/obs/obs_04_0021.html>`__ and `Uploading Objects - PUT <https://docs.otc.t-systems.com/en-us/api/obs/obs_04_0080.html>`__). Only the access control policies predefined in OBS are available. The **x-obs-acl** is special, which can be configured with six types of permissions. No matter what type of permissions is configured, the owner has full control permission for the buckets or objects. The following table lists the predefined policies.

.. table:: **Table 4** Predefined permissions in OBS

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Permission                        | Description                                                                                                                                                                                                                                     |
   +===================================+=================================================================================================================================================================================================================================================+
   | private                           | A bucket or an object can be accessed only by its owner.                                                                                                                                                                                        |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | public-read                       | If this permission is set for a bucket, everyone can obtain its object list, multipart tasks, and metadata.                                                                                                                                     |
   |                                   |                                                                                                                                                                                                                                                 |
   |                                   | If this permission is set for an object, everyone can obtain the content and metadata of the object.                                                                                                                                            |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | public-read-write                 | If this permission is configured for a bucket, everyone can:                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                 |
   |                                   | -  Obtain its object list, multipart uploads, and metadata.                                                                                                                                                                                     |
   |                                   | -  Upload, delete objects.                                                                                                                                                                                                                      |
   |                                   | -  Initiate, cancel multipart uploads, upload, assemble, and copy parts.                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                 |
   |                                   | If this permission is set for an object, everyone can obtain the content and metadata of the object.                                                                                                                                            |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | public-read-delivered             | If this permission is set for a bucket, everyone can obtain its object list, multipart tasks, metadata, and obtain the content and metadata of the objects in the bucket.                                                                       |
   |                                   |                                                                                                                                                                                                                                                 |
   |                                   | This permission does not apply to objects.                                                                                                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | public-read-write-delivered       | If this permission is configured for a bucket, everyone can:                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                 |
   |                                   | -  Obtain its object list, multipart uploads, and metadata.                                                                                                                                                                                     |
   |                                   | -  Upload, delete objects, and obtain content and metadata of objects in the bucket.                                                                                                                                                            |
   |                                   | -  Initiate, cancel multipart uploads, upload, assemble, and copy parts.                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                 |
   |                                   | This permission does not apply to objects.                                                                                                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bucket-owner-full-control         | If this permission is configured for an object, the bucket and object owners have the full control over the object.                                                                                                                             |
   |                                   |                                                                                                                                                                                                                                                 |
   |                                   | By default, if you upload an object to a bucket of any other user, the bucket owner does not have the permissions on your object. After you grant this permission to the bucket owner, the bucket owner can have full control over your object. |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   By default, the permission is **private**.

You can also use the following header fields to set permissions when creating a bucket or uploading an object.

.. table:: **Table 5** Header fields for setting bucket or object ACLs

   +------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                             | Description                                                                                                                                                      |
   +====================================+==================================================================================================================================================================+
   | x-obs-grant-read                   | Used to grant the READ permission to all users in a specific account.                                                                                            |
   +------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-grant-write                  | Used to grant the WRITE permission to all users in a specific account.                                                                                           |
   +------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-grant-read-acp               | Used to grant the READ_ACP permission to all users in a specific account.                                                                                        |
   +------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-grant-write-acp              | Used to grant the WRITE_ACP permission to all users in a specific account.                                                                                       |
   +------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-grant-full-control           | Used to grant the FULL_CONTROL permission to all users in a specific account.                                                                                    |
   +------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-grant-read-delivered         | Used to grant the READ permission for buckets and their objects to all users in a specific account, and objects inherit the permissions of their bucket.         |
   |                                    |                                                                                                                                                                  |
   |                                    | This permission does not apply to objects.                                                                                                                       |
   +------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-grant-full-control-delivered | Used to grant the FULL_CONTROL permission for buckets and their objects to all users in a specific account, and objects inherit the permissions of their bucket. |
   |                                    |                                                                                                                                                                  |
   |                                    | This permission does not apply to objects.                                                                                                                       |
   +------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
