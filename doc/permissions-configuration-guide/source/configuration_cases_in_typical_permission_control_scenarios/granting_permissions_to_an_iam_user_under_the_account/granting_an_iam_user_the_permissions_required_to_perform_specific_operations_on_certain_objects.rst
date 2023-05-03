:original_name: obs_40_0018.html

.. _obs_40_0018:

Granting an IAM User the Permissions Required to Perform Specific Operations on Certain Objects
===============================================================================================

Scenario
--------

This topic describes how to grant an IAM user certain permissions on specific objects in a bucket. Below explains how to grant the object download permission.

If you need to configure other permissions, select the corresponding actions from the **Action Name** drop-down list in the bucket policy. For details about the actions supported by OBS, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.

Recommended Configuration
-------------------------

You are advised to use bucket policies to grant resource-level permissions to an IAM user.

Configuration Precautions
-------------------------

After the configuration is complete, you can download objects using APIs. However, if you log in to OBS Console or OBS Browser+ to download an object, an error is reported indicating that you do not have required permissions.

This is because when you log in to OBS Console or OBS Browser+, APIs (such as **ListAllMyBuckets** and **ListBucket**) are called to load the bucket list and object list and some other APIs will also be called on other pages, but your permissions do not cover those APIs. In such case, your access is denied or your operation is not allowed.

If you want an IAM user to successfully download objects on OBS Console or OBS Browser+, configure custom IAM policies by referring to :ref:`Follow-up Procedure <obs_40_0018__section220405220511>`.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure parameters for a bucket policy.


   .. figure:: /_static/images/en-us_image_0000001435889185.png
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
      | Principal                         | -  Choose **Include** > **Cloud service user**.                                                                                                                                                           |
      |                                   | -  **Account ID**: Enter one account ID only, or enter an asterisk (*) to indicate that the policy takes effect on all users (including both registered and anonymous users).                             |
      |                                   | -  **User ID**: Enter one or more user IDs separated by a comma (,).                                                                                                                                      |
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

.. _obs_40_0018__section220405220511:

Follow-up Procedure
-------------------

To perform specific operations on OBS Console or OBS Browser+, you must add the **obs:bucket:ListAllMyBuckets** (for listing buckets) and **obs:bucket:ListBucket** (for listing objects in a bucket) permissions to the custom IAM policy.

.. note::

   **obs:bucket:ListAllMyBuckets** applies to all resources, while **obs:bucket:ListBucket** applies to the authorized bucket only. Therefore, you need to add two permissions to the policy.

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**. The IAM console is displayed.

#. In the navigation pane, choose **Permissions**.

#. Click **Create Custom Policy** in the upper right corner.

#. Configure parameters for a custom policy.


   .. figure:: /_static/images/en-us_image_0000001385676688.png
      :alt: **Figure 2** Configuring a custom policy

      **Figure 2** Configuring a custom policy

   .. table:: **Table 2** Parameters for configuring a custom policy

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                     |
      +===================================+=================================================================================================================================================================================================================================================+
      | Policy Name                       | Name of the custom policy                                                                                                                                                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy View                       | Set this parameter based on your own habits. **Visual editor** is used here.                                                                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | [Permission 1]                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                 |
      |                                   | -  Select **Allow**.                                                                                                                                                                                                                            |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                                                                                     |
      |                                   | -  Select **obs:bucket:ListAllMyBuckets** from the actions.                                                                                                                                                                                     |
      |                                   | -  Select **All** for resources.                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                 |
      |                                   | [Permission 2]                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                 |
      |                                   | -  Select **Allow**.                                                                                                                                                                                                                            |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                                                                                     |
      |                                   | -  Select **obs:bucket:ListBucket** from the actions.                                                                                                                                                                                           |
      |                                   | -  For **Resources**, select **Specific**, and for **bucket**, select **Specify resource path**, and click **Add Resource Path**. Enter the bucket name in the **Path** text box, indicating that the policy takes effect only for this bucket. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scope                             | The default value is **Global services**.                                                                                                                                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. The custom policy is created.

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Add the created custom policy to the user group by following the instructions in the IAM document.

#. Add the IAM user you want to authorize to the created user group by referring to `Creating a User and Adding the User to a User Group <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__.

   .. note::

      Due to data caching, it takes about 10 to 15 minutes for a custom policy to take effect after the authorization.
