:original_name: obs_40_0043.html

.. _obs_40_0043:

Relationship Between Bucket Policies and Bucket ACLs
====================================================

Mapping Between Bucket ACLs and Bucket Policies
-----------------------------------------------

Bucket ACLs are used to control basic read and write access to buckets. Custom settings of bucket policies support more actions that can be performed on buckets. Bucket ACLs supplement bucket policies, and in many cases, can be replaced by bucket policies to manage access to buckets. :ref:`Table 1 <obs_40_0043__table183716545593>` shows the mapping between bucket ACL access permissions and bucket policy actions.

.. _obs_40_0043__table183716545593:

.. table:: **Table 1** Mapping between bucket ACLs and bucket policies

   +-----------------------+-----------------------+-----------------------------------------+
   | ACL Permission        | Option                | Mapped Action in a Custom Bucket Policy |
   +=======================+=======================+=========================================+
   | Access to bucket      | Read                  | -  HeadBucket                           |
   |                       |                       | -  ListBucket                           |
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

Mapping Between Object ACLs and Bucket Policies
-----------------------------------------------

Object ACLs are used to control basic read and write access to objects. The custom settings of bucket policies allow you to specify more actions that can be performed on objects. :ref:`Table 2 <obs_40_0043__table4160714016>` describes the mapping between object ACL access permissions and bucket policy actions.

.. _obs_40_0043__table4160714016:

.. table:: **Table 2** Mapping between object ACLs and bucket policies

   +-----------------------+-----------------------+-----------------------------------------+
   | Object ACL Permission | Option                | Mapped Action in a Custom Bucket Policy |
   +=======================+=======================+=========================================+
   | Access to object      | Read                  | -  GetObject                            |
   |                       |                       | -  GetObjectVersion                     |
   +-----------------------+-----------------------+-----------------------------------------+
   | Access to ACL         | Read                  | -  GetObjectAcl                         |
   |                       |                       | -  GetObjectVersionAcl                  |
   +-----------------------+-----------------------+-----------------------------------------+
   |                       | Write                 | -  PutObjectAcl                         |
   |                       |                       | -  PutObjectVersionAcl                  |
   +-----------------------+-----------------------+-----------------------------------------+
