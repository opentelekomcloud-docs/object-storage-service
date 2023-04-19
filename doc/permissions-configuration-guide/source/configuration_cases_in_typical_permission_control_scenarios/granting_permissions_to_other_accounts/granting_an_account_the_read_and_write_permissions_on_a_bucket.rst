:original_name: obs_40_0025.html

.. _obs_40_0025:

Granting an Account the Read and Write Permissions on a Bucket
==============================================================

Scenario
--------

This topic describes how to grant other accounts (excluding the IAM users under them) the read and write permissions on OBS buckets. For details about how to grant permissions to an IAM user, see :ref:`Granting IAM Users Under an Account the Access to a Bucket and Resources in the Bucket <obs_40_0027>`.

Recommended Configuration
-------------------------

You are advised to use bucket policies to grant permissions to other accounts.

Configuration Precautions
-------------------------

The preset read/write mode of OBS has the following permissions:

-  GetObject: downloading objects
-  PutObject: uploading objects
-  GetObjectVersion: downloading versioned objects
-  DeleteObjectVersion: deleting objects versions
-  DeleteObject: deleting objects

After the configuration is complete, the authorized account can perform read and write operations (upload, download, or delete all objects in a bucket) by using APIs or by adding external buckets through OBS Browser+. To do this by adding external buckets, the **ListBucket** permission is also required. Currently, access to buckets of other accounts is not allowed on OBS Console.

After the ListBucket permission is configured, a message may still be displayed indicating that you do not have the permission to access the added external bucket through OBS Browser+.

Error cause: The loading on the OBS Browser+ bucket details page invokes some other OBS APIs. However, such operations are not allowed by the read and write permissions. Therefore, a message "Access denied. Check the response permission" or "This operation is not allowed on the requested resource" is displayed, however, existing permissions are not affected.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure parameters for a bucket policy.


   .. figure:: /_static/images/en-us_image_0000001436140385.png
      :alt: **Figure 1** Configuring parameters for a bucket policy

      **Figure 1** Configuring parameters for a bucket policy

   .. table:: **Table 1** Parameters for creating a bucket policy

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                   |
      +===================================+===============================================================================================================================================================+
      | Policy Mode                       | Select **Read and write**.                                                                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **Include** > **Other account**.                                                                                                                    |
      |                                   | -  **Account ID**: Enter the ID of the account which you want to grant permissions to. You can obtain it from the **My Credentials** page of the account.     |
      |                                   | -  **User ID**: Enter the account ID, which can be obtained from the **My Credentials** page of the account.                                                  |
      |                                   |                                                                                                                                                               |
      |                                   |    .. note::                                                                                                                                                  |
      |                                   |                                                                                                                                                               |
      |                                   |       In this example, permissions are granted to an account, excluding any IAM user under the account. Therefore, the user ID is the same as the account ID. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  **Include**                                                                                                                                                |
      |                                   | -  Resource Name: Enter \*.                                                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. The bucket policy is created.

#. (Optional) Click **Create Bucket Policy** again.

   If the authorized account wants to access the OBS bucket on OBS Browser+ by mounting an external bucket, you need to add a ListBucket permission.

#. (Optional) Configure the ListBucket permission.


   .. figure:: /_static/images/en-us_image_0000001435981085.png
      :alt: **Figure 2** Configuring the ListBucket permission

      **Figure 2** Configuring the ListBucket permission

   .. table:: **Table 2** Parameters for creating a bucket policy

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                   |
      +===================================+===============================================================================================================================================================+
      | Policy Mode                       | Select **Customized**.                                                                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Allow**.                                                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **Include** > **Other account**.                                                                                                                    |
      |                                   | -  **Account ID**: Enter the ID of the account which you want to grant permissions to. You can obtain it from the **My Credentials** page of the account.     |
      |                                   | -  **User ID**: Enter the account ID.                                                                                                                         |
      |                                   |                                                                                                                                                               |
      |                                   |    .. note::                                                                                                                                                  |
      |                                   |                                                                                                                                                               |
      |                                   |       In this example, permissions are granted to an account, excluding any IAM user under the account. Therefore, the user ID is the same as the account ID. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | Select **Include** > **Entire bucket**.                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                                                                                |
      |                                   | -  **Action Name**: ListBucket                                                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. (Optional) Click **OK**. The bucket policy is created.
