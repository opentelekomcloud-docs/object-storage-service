:original_name: en-us_topic_0045853737.html

.. _en-us_topic_0045853737:

Adding External Buckets
=======================

OBS Browser supports the external bucket adding function.

Prerequisites
-------------

You have obtained the permissions to read and write the external bucket that you want to add.

For example: Account **A** wants to add bucket **testbucket** of account **B**. Account **B** must grant account **A** the permission to read bucket **testbucket**. If account **A** needs to upload object to bucket **testbucket**, account **B** needs to grant account **A** the permission to write the bucket. Account **A** is the owner of the uploaded objects, and needs to grant account **B** the permission to read and write the objects.

.. note::

   Only a bucket 3.0 or later can be added as an external bucket after its standard bucket policy is set to public read/write.

   Suppose a bucket's standard bucket policy is set to public read/write during the bucket creation. To add this bucket as an external bucket, its standard bucket policy must be manually changed to private and then changed back to public read/write.

Procedure
---------

#. Log in to OBS Browser.

#. Click **Add Bucket** on the upper left corner of the page. The **Add Bucket** dialog box is displayed.

#. Select **Add external bucket** and enter the bucket name.


   .. figure:: /_static/images/en-us_image_0129840536.png
      :alt: **Figure 1** Adding an external bucket

      **Figure 1** Adding an external bucket

   After successfully adding an external bucket, you can see the external bucket in the bucket list and have the ACL access permissions for the bucket.

#. Click **OK**.

#. In the displayed dialog box, click **Close** to close the dialog box.
