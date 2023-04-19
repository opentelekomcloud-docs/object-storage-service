:original_name: obs_40_0026.html

.. _obs_40_0026:

Granting an Account the Specified Permissions on a Bucket
=========================================================

Scenario
--------

This topic describes how to grant other accounts (excluding the IAM users under them) specific operation permissions on OBS buckets. For details about how to grant permissions to an IAM user, see :ref:`Granting IAM Users Under an Account the Access to a Bucket and Resources in the Bucket <obs_40_0027>`.

The following example explains how to grant the permissions to configure a bucket ACL and obtain the bucket ACL configuration information. If you need to configure other permissions, select the corresponding actions from the **Action Name** drop-down list in the bucket policy. For details about the actions supported by OBS, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.

Recommended Configuration
-------------------------

You are advised to use bucket policies to grant permissions to other accounts.

Configuration Precautions
-------------------------

After the configuration is complete, the authorized account can configure and obtain a bucket ACL by using APIs or SDKs or by adding external buckets through OBS Browser+. To do this by adding external buckets, the **ListBucket** permission is also required. Currently, access to buckets of other accounts is not allowed on OBS Console.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure parameters for a bucket policy.


   .. figure:: /_static/images/en-us_image_0000001385862242.png
      :alt: **Figure 1** Configuring parameters for a bucket policy

      **Figure 1** Configuring parameters for a bucket policy

   .. table:: **Table 1** Parameters for creating a bucket policy

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================+
      | Policy Mode                       | Select **Customized**.                                                                                                                                                                                    |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Allow**.                                                                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **Include** > **Other account**.                                                                                                                                                                |
      |                                   | -  **Account ID**: Enter the ID of the account which you want to grant permissions to. You can obtain it from the **My Credentials** page of the account.                                                 |
      |                                   | -  **User ID**: Enter the account ID, which can be obtained from the **My Credentials** page of the account.                                                                                              |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    .. note::                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                           |
      |                                   |       In this example, permissions are granted to an account, excluding any IAM user under the account. Therefore, the user ID is the same as the account ID.                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | Select **Include** > **Entire bucket**.                                                                                                                                                                   |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                                                                                                                            |
      |                                   | -  **Action Name**:                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    -  PutBucketAcl                                                                                                                                                                                        |
      |                                   |    -  GetBucketAcl                                                                                                                                                                                        |
      |                                   |    -  ListBucket (required when the authorized account wants to access the OBS bucket on OBS Browser+ by mounting an external bucket)                                                                     |
      |                                   |                                                                                                                                                                                                           |
      |                                   | To configure other permissions, select the corresponding actions. For details about the actions supported by OBS, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. The bucket policy is created.
