:original_name: obs_40_0025.html

.. _obs_40_0025:

Granting Other Accounts the Read/Write Permission for a Bucket
==============================================================

Scenario
--------

This topic describes how to grant other accounts (excluding the IAM users under them) the read/write permission for OBS buckets. For details about how to grant permissions to an IAM user, see :ref:`Granting IAM Users Under an Account the Access to a Bucket and the Resources in It <obs_40_0027>`.

Recommended Configuration
-------------------------

Use bucket policies to grant permissions to other accounts.

Precautions
-----------

After the configuration is complete, the authorized account can perform read and write operations (upload, download, or delete all objects in a bucket) by using APIs or by adding external buckets through OBS Browser+. Currently, access to buckets of other accounts is not allowed on OBS Console.

When you use OBS Browser+ to access the added external bucket, a message may still be displayed indicating that you do not have required permissions.

Error cause: The loading on the OBS Browser+ bucket details page invokes some other OBS APIs. However, such operations are not allowed by the read and write permissions. Therefore, a message "Access denied. Check the response permission" or "This operation is not allowed on the requested resource" is displayed, however, existing permissions are not affected.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000001436140385.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for creating a bucket policy

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                   |
      +===================================+===============================================================================================================================================================+
      | Policy Mode                       | Select **Read and write**.                                                                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **Include** > **Other account**.                                                                                                                    |
      |                                   | -  **Account ID**: Enter the ID of the account which you want to grant permissions to. You can obtain it from the **My Credentials** page of the account.     |
      |                                   | -  **User ID**: Enter the account ID. You can obtain it from the **My Credentials** page of the account.                                                      |
      |                                   |                                                                                                                                                               |
      |                                   |    .. note::                                                                                                                                                  |
      |                                   |                                                                                                                                                               |
      |                                   |       In this example, permissions are granted to an account, excluding any IAM user under the account. Therefore, the user ID is the same as the account ID. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  **Include**                                                                                                                                                |
      |                                   | -  Resource Name: Enter \*.                                                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

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

#. (Optional) Click **OK**.
