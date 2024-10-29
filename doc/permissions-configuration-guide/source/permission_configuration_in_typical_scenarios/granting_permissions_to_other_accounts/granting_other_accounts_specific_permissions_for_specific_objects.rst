:original_name: obs_40_0029.html

.. _obs_40_0029:

Granting Other Accounts Specific Permissions for Specific Objects
=================================================================

Scenario
--------

This section describes how to grant other accounts the permissions to download an object from a bucket.

To grant other permissions, select required actions from **Action Name** in the bucket policy. For details about the actions supported by OBS, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.

For details about how to grant permissions to an IAM user, see :ref:`Granting IAM Users Under an Account the Access to a Bucket and the Resources in It <obs_40_0027>`.

Recommended Configuration
-------------------------

Use bucket policies to grant permissions to other accounts.

Precautions
-----------

After configuration, they can download objects using APIs. However, if they download objects using OBS Console or OBS Browser+, a message will be displayed indicating that they do not have required permissions.

When they log in to OBS Console or OBS Browser+, APIs (such as **ListAllMyBuckets** and **ListBucket**) are called to load the bucket list and object list and some other APIs will also be called on other pages, but their permissions do not cover those APIs. In such case, the message is displayed.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000001386185594.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

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
      |                                   | -  **User ID**: Enter the account ID. You can obtain it from the **My Credentials** page of the account.                                                                                                  |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    .. note::                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                           |
      |                                   |       In this example, permissions are granted to an account, excluding any IAM user under the account. Therefore, the user ID is the same as the account ID.                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  Choose **Include** > **Specific resources**.                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                           |
      |                                   | -  **Resource Name**: Enter the object or the set of objects that will be accessed.                                                                                                                       |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    For one object, enter *object name*.                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    For a set of objects, enter ``object name prefix + *, * + object name suffix, or *``.                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                                                                                                                            |
      |                                   | -  Action Name: Select **GetObject**.                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                           |
      |                                   | To configure other permissions, select the corresponding actions. For details about the actions supported by OBS, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
