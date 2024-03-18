:original_name: obs_03_0081.html

.. _obs_03_0081:

Granting Other Accounts Permissions to Operate a Specific Bucket
================================================================

The bucket owner (root account) or other accounts and IAM users, who have the permission to set bucket policies, can configure bucket policies to grant the bucket operation permissions to other accounts or IAM users under other accounts.

The following is an example about how to grant other accounts bucket access and object upload permissions.

.. note::

   To grant permissions to IAM users under other accounts, you need to configure both bucket policies and IAM policies.

   #. Configure a bucket policy to allow IAM users to access the bucket.
   #. Configure IAM policies for the account where authorized IAM users belong, to allow the IAM users to access the bucket.

   Only permissions that are allowed by both the bucket policy and IAM policies can take effect.

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.
#. In the navigation pane, choose **Permissions**.
#. Choose **Bucket Policies** > **Custom Bucket Policies**.
#. Click **Create Bucket Policy**. The **Create Bucket Policy** dialog box is displayed.
#. Configure the parameters listed in the table below to grant other accounts bucket access permission.

   .. table:: **Table 1** Parameters for granting bucket access permission

      +-----------------------------------+-------------------------------------------------------------------------------------------------+
      | Parameter                         | Value                                                                                           |
      +===================================+=================================================================================================+
      | Policy Mode                       | **Customized**                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------+
      | Effect                            | **Allow**                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------+
      | Principal                         | -  **Include**                                                                                  |
      |                                   |                                                                                                 |
      |                                   | -  **Cloud service user**. Select **Other account**, and enter the account ID and user ID.      |
      |                                   |                                                                                                 |
      |                                   |    For **Account ID**, enter the **Domain ID** that can be found on the **My Credential** page. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------+
      | Resources                         | -  **Include**                                                                                  |
      |                                   | -  Leave it blank.                                                                              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                  |
      |                                   | -  ListBucket                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------+

#. Click **OK**.
#. Click **Create Bucket Policy**. The **Create Bucket Policy** dialog box is displayed.
#. Configure the parameters listed in the table below to grant other accounts the object upload permission:

   .. note::

      Before granting this permission to a user, ensure that the user has the permission to access the bucket.

   .. table:: **Table 2** Parameters for granting permission to upload objects

      +-----------------------------------+-------------------------------------------------------------------------------------------------+
      | Parameter                         | Value                                                                                           |
      +===================================+=================================================================================================+
      | Policy Mode                       | **Customized**                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------+
      | Effect                            | **Allow**                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------+
      | Principal                         | -  **Include**                                                                                  |
      |                                   |                                                                                                 |
      |                                   | -  **Cloud service user**. Select **Other account**, and enter the account ID and user ID.      |
      |                                   |                                                                                                 |
      |                                   |    For **Account ID**, enter the **Domain ID** that can be found on the **My Credential** page. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------+
      | Resources                         | -  **Include**                                                                                  |
      |                                   | -  Resource name: **\***                                                                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                  |
      |                                   | -  PutObject                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------+

#. Click **OK**.
