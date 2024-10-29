:original_name: obs_40_0031.html

.. _obs_40_0031:

Granting Anonymous Users the Public Read Permission for a Bucket
================================================================

Scenario
--------

If a bucket needs to be accessed by anonymous users, you can configure a bucket policy and bucket ACL to grant the access permission to anonymous users. The following uses a bucket policy as an example.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. On the **Bucket Policies** tab page, select the **Public Read** policy for the bucket in the **Standard Bucket Policies** area.


   .. figure:: /_static/images/en-us_image_0000001436305909.png
      :alt: **Figure 1** Granting public read permissions on buckets to anonymous users

      **Figure 1** Granting public read permissions on buckets to anonymous users

Verification
------------

#. After the permission is set, in the **Basic Information** area of the bucket overview page, locate **Access Domain Name**. Share the URL of the access domain name over the Internet so that all Internet users can access the bucket.
#. On the **Objects** tab page of the bucket, click the target object name and find the object link. Share the object link over the Internet so that all Internet users can access the object.
