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

#. In the bucket list, click the bucket name you want to go to the **Objects** page.

#. In the navigation pane, choose **Permissions** > **Bucket Policies**.

#. On the **Bucket Policies** page, click **Create**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000002177832637.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for configuring a bucket policy

      +-----------------------------------+------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                    |
      +===================================+================================================================================================+
      | Policy view                       | Select **Visual Editor** or **JSON** based on your own habits. **Visual Editor** is used here. |
      +-----------------------------------+------------------------------------------------------------------------------------------------+
      | Policy Name                       | Enter a policy name.                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Allow**.                                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **All accounts**.                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------+
      | Resources                         | -  Select **Entire bucket (including the objects in it)**.                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------+
      | Actions                           | -  Choose **Use a template**.                                                                  |
      |                                   | -  Select **Public Read**.                                                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------+

#. Confirm and click **Create**.

Verification
------------

#. After the permission is set, in the **Domain Name Details** area of the bucket overview page, locate **Access Domain Name**. Share the URL of the access domain name over the Internet so that all Internet users can access the bucket.
#. On the **Objects** tab page of the bucket, click the target object name and find the object link. Share the object link over the Internet so that all Internet users can access the object.
