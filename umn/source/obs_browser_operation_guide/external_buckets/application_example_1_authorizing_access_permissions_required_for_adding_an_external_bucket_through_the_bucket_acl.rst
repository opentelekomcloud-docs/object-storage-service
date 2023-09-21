:original_name: obs_03_0134.html

.. _obs_03_0134:

Application Example 1: Authorizing Access Permissions Required for Adding an External Bucket Through the Bucket ACL
===================================================================================================================

A bucket ACL can be used to grant the read and write access to a bucket. If only the read access to the bucket is granted, the authorized user can only add the bucket and list objects in the bucket, but cannot upload objects to the bucket. If the read and write access to the bucket is granted, the authorized user can upload objects to the bucket. Permissions controlled by a bucket ACL are as follows:

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

Procedure
---------

#. Log in to OBS Console.
#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.
#. In the navigation pane on the left, click **Permissions** to go to the permission management page.
#. Click **Bucket ACL**. The **Bucket ACL** page is displayed.
#. Click **Add**, enter the account ID of the user that will add the bucket to OBS Browser, and select the read and write access to the bucket.

   .. note::

      If you want to authorize such access to all users, in the **Public Permissions** area, authorize the **Anonymous User** the read and write access to the bucket.

      **Account ID** corresponds to **Domain ID** on the **My Credential** page.

#. Click **Save**.

Verification
------------

#. Log in to OBS Browser.
#. Click **Add Bucket** on the upper left corner of the page. The **Add Bucket** dialog box is displayed.
#. Select **Add external bucket** and enter the bucket name.
#. Click **OK**. The external bucket is added successfully.
#. Click the newly added external bucket to open the bucket.
#. Click **Upload Object**, and objects can be successfully uploaded to the bucket.
#. Select an object in the bucket and click **Delete**. The object can be deleted successfully.
