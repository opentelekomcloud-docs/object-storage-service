:original_name: obs_03_0434.html

.. _obs_03_0434:

External Bucket Overview
========================

After you are granted by a bucket owner the read and write access to a bucket, you can add this bucket on OBS Browser as your external bucket. You can then operate this external bucket on OBS Browser. For details about what actions you can perform, check the actions authorized during the permission configuration.

Granting Permissions Required for Adding an External Bucket
-----------------------------------------------------------

The read and write access to a bucket can be granted through the bucket ACL or bucket policy.

Permissions controlled by a bucket ACL are as follows:

.. table:: **Table 1** Permissions controlled by a bucket ACL

   +-----------------------+-----------------------+-----------------------------------------+
   | Bucket ACL            | Option                | Mapped Action in a Custom Bucket Policy |
   +=======================+=======================+=========================================+
   | Access to Bucket      | Read                  | -  ListBucket                           |
   |                       |                       | -  ListBucketVersions                   |
   |                       |                       | -  ListBucketMultipartUploads           |
   +-----------------------+-----------------------+-----------------------------------------+
   |                       | Write                 | -  PutObject                            |
   |                       |                       | -  DeleteObject                         |
   |                       |                       | -  DeleteObjectVersion                  |
   +-----------------------+-----------------------+-----------------------------------------+
   | Access to ACL         | Read                  | GetBucketAcl                            |
   +-----------------------+-----------------------+-----------------------------------------+
   |                       | Write                 | PutBucketAcl                            |
   +-----------------------+-----------------------+-----------------------------------------+

Permissions controlled by a standard bucket policy are as follows:

.. table:: **Table 2** Permissions controlled by a standard bucket policy

   +-----------------------+------------------------------+------------------------------+
   | Parameter             | Public Read                  | Public Read and Write        |
   +=======================+==============================+==============================+
   | Effect                | Allow                        | Allow                        |
   +-----------------------+------------------------------+------------------------------+
   | Principal             | \* (Any user)                | \* (Any user)                |
   +-----------------------+------------------------------+------------------------------+
   | Resources             | \* (All objects in a bucket) | \* (All objects in a bucket) |
   +-----------------------+------------------------------+------------------------------+
   | Actions               | -  GetObject                 | -  GetObject                 |
   |                       | -  GetObjectVersion          | -  GetObjectVersion          |
   |                       | -  ListBucket                | -  PutObject                 |
   |                       |                              | -  DeleteObject              |
   |                       |                              | -  DeleteObjectVersion       |
   |                       |                              | -  ListBucket                |
   +-----------------------+------------------------------+------------------------------+
   | Conditions            | N/A                          | N/A                          |
   +-----------------------+------------------------------+------------------------------+

If a custom bucket policy is used to authorize such permissions, the ListBucket, GetObject, and GetObjectVersion actions must be allowed. More actions can be allowed according to your actual needs.

Performing Operations on the External Bucket
--------------------------------------------

The following are some restrictions when you (the user who adds the bucket) operate the external bucket:

-  You cannot restore Cold objects that are not yours in the external bucket. You can view the object restore status only when the owner of those Cold objects grants you the read permission for the objects.
-  You can perform only authorized actions on existing objects in the external bucket. If you want to perform additional operations on an object, you need to get corresponding permissions granted by the object owner.
-  If you upload an object to the external bucket, the object ACL permissions will be automatically granted to the bucket owner, including the read permission for the object and the read and write permissions for the object ACL.
-  The encrypted objects you uploaded to the external bucket cannot be accessed by the bucket owner, because the bucket owner does not have the key.
-  To download an object from the external bucket, you must have the read permission for the object. You cannot download encrypted objects from the external bucket.
