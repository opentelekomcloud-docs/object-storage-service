:original_name: obs_03_0135.html

.. _obs_03_0135:

Application Example 2: Authorizing Access Permissions Required for Adding an External Bucket Through the Standard Bucket Policy
===============================================================================================================================

A standard bucket policy can be used to grant the read and write access to a bucket. The standard bucket policy grants the public read and write access to the bucket, that is, all users can access the bucket. Permissions controlled by a standard bucket policy are as follows:

.. table:: **Table 1** Permissions controlled by a standard bucket policy

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

Procedure
---------

#. Log in to OBS Console.
#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.
#. In the navigation pane on the left, click **Permissions** to go to the permission management page.
#. Select the **Public Read and Write** policy from the standard bucket policies that are pre-defined.
#. In the dialog box that is displayed, click **Yes**.

Verification
------------

#. Log in to OBS Browser.
#. Click **Add Bucket** on the upper left corner of the page. The **Add Bucket** dialog box is displayed.
#. Select **Add external bucket** and enter the bucket name.
#. Click **OK**. The external bucket is added successfully.
#. Click the newly added external bucket to open the bucket.
#. Click **Upload Object**, and objects can be successfully uploaded to the bucket.
#. Select an object in the bucket and click **Delete**. The object can be deleted successfully.
