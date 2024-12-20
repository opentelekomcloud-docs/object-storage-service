:original_name: obs_40_0028.html

.. _obs_40_0028:

Granting Other Accounts the Read Permission for Certain Objects
===============================================================

Scenario
--------

This case describes how to grant other accounts (excluding IAM users under the account) the read permission for an object or a type of objects in an OBS bucket. For details about how to grant permissions to an IAM user, see :ref:`Granting IAM Users Under an Account the Access to a Bucket and the Resources in It <obs_40_0027>`.

Recommended Configuration
-------------------------

Use bucket policies to grant permissions to other accounts.

Precautions
-----------

After configuration, they can read (download) specific objects using APIs. However, if they download an object from OBS Console or OBS Browser+, a message will be displayed, indicating that they do not have required permissions.

When they log in to OBS Console or OBS Browser+, the **ListAllMyBuckets** APi is called to load the bucket list and some other APIs will also be called on other pages, but their permissions do not cover those APIs. In such case, the message is displayed.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000001385864766.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for creating a bucket policy

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                   |
      +===================================+===============================================================================================================================================================+
      | Policy Mode                       | Select **Read-only**.                                                                                                                                         |
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
      |                                   |                                                                                                                                                               |
      |                                   | -  **Resource Name**: Enter the object or the set of objects that will be accessed.                                                                           |
      |                                   |                                                                                                                                                               |
      |                                   |    For one object, enter *object name*.                                                                                                                       |
      |                                   |                                                                                                                                                               |
      |                                   |    For a set of objects, enter ``object name prefix + *, * + object name suffix, or *``.                                                                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
