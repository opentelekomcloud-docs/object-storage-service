:original_name: obs_40_0031.html

.. _obs_40_0031:

Granting Anonymous Users Public Read Permissions on a Bucket
============================================================

Scenario
--------

If a bucket needs to be accessed by anonymous users, you can configure a bucket policy and bucket ACL to grant the access permission to anonymous users. The following uses a bucket policy as an example.

Configuration Precautions
-------------------------

The **Public Read** policy allows any user to read objects in a bucket. **Public Read** has the following permissions:

-  GetObject: downloading objects
-  GetObjectVersion: downloading versioned objects
-  HeadBucket: checking whether a bucket exists
-  ListBucket: listing objects in a bucket and obtaining the bucket metadata

   .. note::

      When you access a bucket through its domain name, the ListBucket permission allows you to list all objects in the bucket. If you want to restrict this permission to specified users under an account, see :ref:`Related Scenario: Canceling the ListBucket Permission from the Public Read Policy <obs_40_0031__section191491712418>`.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** tab page, select the **Public Read** policy for the bucket in the **Standard Bucket Policies** area.


   .. figure:: /_static/images/en-us_image_0000001436305909.png
      :alt: **Figure 1** Granting public read permissions on buckets to anonymous users

      **Figure 1** Granting public read permissions on buckets to anonymous users

Verification
------------

#. After the permission is set, in the **Basic Information** area of the bucket details page, locate **Access Domain Name**. Share the URL of the access domain name over the Internet so that all Internet users can access the bucket.
#. On the **Objects** tab page of the bucket, click the target object name and find the object link. Share the object link over the Internet so that all Internet users can access the object.

.. _obs_40_0031__section191491712418:

Related Scenario: Canceling the ListBucket Permission from the Public Read Policy
---------------------------------------------------------------------------------

If you want to restrict the ListBucket permission to specified users under an account, you need to configure another bucket policy.

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure parameters for a bucket policy.


   .. figure:: /_static/images/en-us_image_0000001436265909.png
      :alt: **Figure 2** Configuring parameters for a bucket policy

      **Figure 2** Configuring parameters for a bucket policy

   .. table:: **Table 1** Parameters for creating a bucket policy

      +-----------------------------------+----------------------------------------------------------------------+
      | Parameter                         | Description                                                          |
      +===================================+======================================================================+
      | Policy Mode                       | Select **Customized**.                                               |
      +-----------------------------------+----------------------------------------------------------------------+
      | Effect                            | Select **Deny**.                                                     |
      +-----------------------------------+----------------------------------------------------------------------+
      | Principal                         | Select **Exclude**.                                                  |
      |                                   |                                                                      |
      |                                   | -  Select **Cloud service user**.                                    |
      |                                   | -  **Account ID**: Enter **\*** to indicate all anonymous users.     |
      |                                   | -  **User ID**: Enter one or more user IDs separated by a comma (,). |
      +-----------------------------------+----------------------------------------------------------------------+
      | Resources                         | Select **Include** > **Entire bucket**.                              |
      +-----------------------------------+----------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                       |
      |                                   | -  **Action Name**:                                                  |
      |                                   |                                                                      |
      |                                   |    -  ListBucket                                                     |
      +-----------------------------------+----------------------------------------------------------------------+

#. Click **OK**. The bucket policy is created.

**Verification**: After the permission is set, in the **Basic Information** area of the bucket details page, locate **Access Domain Name**. Publish the URL on the Internet, and verify that only specified users can list objects in the bucket.
