:original_name: obs_03_0434.html

.. _obs_03_0434:

External Bucket Overview
========================

The bucket owner can authorize other accounts the read and write access to the bucket. If you are authorized with such permissions, you can add the bucket on OBS Browser as an external bucket. After the external bucket is added successfully, you can operate the bucket on OBS Browser. For details about what actions you can perform on the external bucket, check the permission settings.

Authorizing Permissions Required for Adding a Bucket as an External Bucket on OBS Browser
-----------------------------------------------------------------------------------------

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

Operations That Can Be Performed on the External Bucket
-------------------------------------------------------

Operations that can be performed by the authorized user on the external bucket:

-  You can add an external bucket but cannot restore objects from the Cold storage class in the bucket. You can view the object restore status only when the owner of those objects authorizes you the permission to read the objects.
-  You (the user who adds the bucket) can perform only authorized actions on original objects in the bucket. If you want to have additional operation permissions for objects in the bucket, you need to have the permissions authorized by the object owner.
-  If you upload an object to the added external bucket, the read access to the object and the object ACL will be automatically authorized to the bucket owner and configured in the object ACL settings.
-  If you upload an encrypted object to the added external bucket, the bucket owner cannot access the object because the bucket owner does not have the key.
-  To download an object from the external bucket, the user who adds the bucket must be authorized the permission to read the object, and encrypted objects cannot be downloaded.
