:original_name: obs_40_0029.html

.. _obs_40_0029:

Granting an Account the Specified Permissions on Certain Objects
================================================================

Scenario
--------

This case describes how to grant other accounts the specified operation permission on a specified object in an OBS bucket. The following describes how to grant the permission to download an object.

If you need to configure other permissions, select the corresponding actions from the **Action Name** drop-down list in the bucket policy. For details about the actions supported by OBS, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.

For details about how to grant permissions to an IAM user, see :ref:`Granting IAM Users Under an Account the Access to a Bucket and Resources in the Bucket <obs_40_0027>`.

Recommended Configuration
-------------------------

You are advised to use bucket policies to grant permissions to other accounts.

Configuration Precautions
-------------------------

After the configuration is complete, you can download objects using APIs. However, if you log in to OBS Console or OBS Browser+ to download an object, an error is reported indicating that you do not have required permissions.

This is because when you log in to OBS Console or OBS Browser+, APIs (such as **ListAllMyBuckets** and **ListBucket**) are called to load the bucket list and object list and some other APIs will also be called on other pages, but your permissions do not cover those APIs. In such case, your access is denied or your operation is not allowed.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure parameters for a bucket policy.


   .. figure:: /_static/images/en-us_image_0000001386185594.png
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

#. Click **OK**. The bucket policy is created.
