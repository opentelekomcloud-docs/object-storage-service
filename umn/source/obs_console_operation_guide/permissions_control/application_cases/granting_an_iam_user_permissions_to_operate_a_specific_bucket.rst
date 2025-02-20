:original_name: obs_03_0080.html

.. _obs_03_0080:

Granting an IAM User Permissions to Operate a Specific Bucket
=============================================================

Create an IAM user under in an account. The IAM user has no permission to any resource before it is added to any user group. The bucket owner (root account) or other accounts and IAM users, who have the permission to set bucket policies, can configure bucket policies to grant the bucket operation permissions to IAM users.

The following is an example about how to grant an IAM user the bucket access and object upload permissions.

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.
#. In the navigation pane, choose **Permissions**.
#. Choose **Bucket Policies** > **Custom Bucket Policies**.
#. Click **Create Bucket Policy**.
#. Configure parameters listed in the table below to grant IAM users the permissions to access the bucket (to list objects in the bucket). Retain the default values for the other parameters.

   .. table:: **Table 1** Parameters for granting the object listing permission

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Value                                                                                                            |
      +===================================+==================================================================================================================+
      | Policy Mode                       | **Customized**                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------+
      | Effect                            | **Allow**                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  **Include**                                                                                                   |
      |                                   | -  **Cloud service user**. Select the current account, and in the account, select the IAM user to be authorized. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  **Include**                                                                                                   |
      |                                   | -  Leave it blank.                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                                   |
      |                                   | -  ListBucket                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
#. Click **Create Bucket Policy**. The **Create Bucket Policy** dialog box is displayed.
#. Configure parameters in the table below to grant an IAM user the permission to upload objects to a bucket.

   .. note::

      Before granting this permission to a user, ensure that the user has the permission to access the bucket.

   .. table:: **Table 2** Parameters for granting the object upload permission

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Value                                                                                                                                                                                                    |
      +===================================+==========================================================================================================================================================================================================+
      | Policy Mode                       | **Customized**                                                                                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | **Allow**                                                                                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  **Include**                                                                                                                                                                                           |
      |                                   | -  **Cloud service user**. Select the current account, and in the account, select the IAM user to be authorized.                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  **Include**                                                                                                                                                                                           |
      |                                   | -  Resource name: **\***                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                                                                                                                           |
      |                                   | -  PutObject                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                          |
      |                                   | .. note::                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                          |
      |                                   |    In this example, only the permission to upload objects is granted. You can also select other object actions to grant corresponding permissions if needed. The asterisk (``*``) indicates all actions. |
      |                                   |                                                                                                                                                                                                          |
      |                                   |    For details about the supported actions, see :ref:`Actions <obs_03_0051>`.                                                                                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
