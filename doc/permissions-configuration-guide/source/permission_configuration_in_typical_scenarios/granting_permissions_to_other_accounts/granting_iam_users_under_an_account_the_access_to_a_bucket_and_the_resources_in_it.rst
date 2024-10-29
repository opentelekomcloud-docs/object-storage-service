:original_name: obs_40_0027.html

.. _obs_40_0027:

Granting IAM Users Under an Account the Access to a Bucket and the Resources in It
==================================================================================

Scenario
--------

This topic describes how to grant IAM users the permissions to access OBS buckets and resources in them.

The following describes how to grant the permissions to upload and download objects in a bucket. If you need to configure other specified permissions, configure the corresponding permissions in the bucket policy and IAM permissions.

Recommended Configuration
-------------------------

To grant permissions to IAM users under an account, you need to configure both **bucket policies** and **IAM permissions**.

For example, to allow IAM user **A** of account **A** to access bucket **B** of account **B**, you need to:

#. Configure a bucket policy that allows IAM user **A** to access bucket **B**.
#. Configure IAM permissions for account **A** to allow IAM user **A** to access bucket **B**.

Precautions
-----------

After configuration, the IAM user can upload and download objects through APIs. In addition, the user can upload and download objects by mounting external buckets on OBS Browser+. To add external buckets, the **ListBucket** permission is also required. Currently, access to buckets of other accounts is not allowed on OBS Console.

Procedure 1: The Bucket Owner Configures a Bucket Policy.
---------------------------------------------------------

**The bucket owner or a user who has the permission to configure bucket policies needs to configure a bucket policy that allows IAM users under an account to perform specified operations on the bucket.**

In this example, account **B** (owner of bucket **B**) configures a bucket policy that allows IAM user **A** of account **A** to upload objects to and download objects from bucket **B** of account **B**.

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure a bucket policy that allows uploads and downloads.


   .. figure:: /_static/images/en-us_image_0000001386341906.png
      :alt: **Figure 1** Configuring a bucket policy that allows uploads and downloads

      **Figure 1** Configuring a bucket policy that allows uploads and downloads

   .. table:: **Table 1** Parameters for creating a bucket policy

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================================================================================================================================+
      | Policy Mode                       | Select **Customized**.                                                                                                                                                                                                                                                                                                                           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Allow**.                                                                                                                                                                                                                                                                                                                                |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **Include** > **Other account**.                                                                                                                                                                                                                                                                                                       |
      |                                   | -  **Account ID**: Enter the ID of the account which you want to grant permissions to. You can obtain it from the **My Credentials** page of the account or the IAM user. The ID of account **A** is used as an example here.                                                                                                                    |
      |                                   | -  **User ID**: Enter the ID of the IAM user under the authorized account. You can obtain the ID on the **My Credentials** page of the IAM user. The wildcard character (*) is supported, indicating that the setting takes effect for all IAM users under the account. The ID of IAM user **A** under account **A** is used as an example here. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  Choose **Include** > **Specific resources**.                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                  |
      |                                   | -  **Resource Name**: Enter the object or the set of objects that will be accessed.                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |    -  For one object, enter *object name*.                                                                                                                                                                                                                                                                                                       |
      |                                   |    -  For a set of objects, enter ``object name prefix + *, * + object name suffix, or *``.                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |    Set this parameter to **\*** if all objects need to be downloaded.                                                                                                                                                                                                                                                                            |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                                                                                                                                                                                                                                                                   |
      |                                   | -  **Action Name**:                                                                                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |    -  GetObject                                                                                                                                                                                                                                                                                                                                  |
      |                                   |    -  GetObjectVersion                                                                                                                                                                                                                                                                                                                           |
      |                                   |    -  PutObject                                                                                                                                                                                                                                                                                                                                  |
      |                                   |    -  (Optional) ListBucket: Select this operation if you need to use OBS Browser+ to add external buckets.                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                  |
      |                                   | To configure other specified operation permissions on objects, select the corresponding actions. For details about the actions supported by OBS, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.                                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. (Optional) Click **Create Bucket Policy** again to configure a bucket policy that allows objects in the bucket to be listed. (Perform this step when you need to use OBS Browser+ to add external buckets.)


   .. figure:: /_static/images/en-us_image_0000001436302073.png
      :alt: **Figure 2** Configuring a bucket policy that allows objects to be listed in a bucket

      **Figure 2** Configuring a bucket policy that allows objects to be listed in a bucket

   .. table:: **Table 2** Parameters for creating a bucket policy

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================================================================================================================================+
      | Policy Mode                       | Select **Customized**.                                                                                                                                                                                                                                                                                                                           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Allow**.                                                                                                                                                                                                                                                                                                                                |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **Include** > **Other account**.                                                                                                                                                                                                                                                                                                       |
      |                                   | -  **Account ID**: Enter the ID of the account which you want to grant permissions to. You can obtain it from the **My Credentials** page of the account or the IAM user. The ID of account **A** is used as an example here.                                                                                                                    |
      |                                   | -  **User ID**: Enter the ID of the IAM user under the authorized account. You can obtain the ID on the **My Credentials** page of the IAM user. The wildcard character (*) is supported, indicating that the setting takes effect for all IAM users under the account. The ID of IAM user **A** under account **A** is used as an example here. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | Select **Include** > **Entire bucket**.                                                                                                                                                                                                                                                                                                          |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                                                                                                                                                                                                                                                                   |
      |                                   | -  **Action Name**: ListBucket                                                                                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                                                  |
      |                                   | To configure other specified permissions on buckets, select the corresponding actions. For details about the actions supported by OBS, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.                                                                                                                   |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Procedure 2: The Account Grants Permissions to IAM Users Under It.
------------------------------------------------------------------

**The account (not the bucket owner) needs to grant permissions to its IAM users to perform specified operations on the bucket. (The allowed operations must be the same as those allowed in the bucket policy.)**

In this example, account **A** needs to grant IAM user **A** the permissions to upload objects to and download objects from bucket **B** of account **B**.

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**.

#. In the navigation pane, choose **Permissions**.

#. Click **Create Custom Policy** in the upper right corner.

#. Configure a custom policy.


   .. figure:: /_static/images/en-us_image_0000001436303585.png
      :alt: **Figure 3** Configuring a custom policy

      **Figure 3** Configuring a custom policy

   .. table:: **Table 3** Parameters for configuring a custom policy

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================================================+
      | Policy Name                       | Enter a policy name.                                                                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy View                       | Select one based on your own habits. **Visual editor** is used here.                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | -  Select **Allow**.                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                       |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                       |
      |                                   | -  Select the actions to be authorized.                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                       |
      |                                   |    -  ReadOnly > **obs:bucket:ListBucketVersions** and **obs:object:GetObjectVersion**                                                                                                                                |
      |                                   |    -  ReadWrite > **obs:object:PutObject**                                                                                                                                                                            |
      |                                   |    -  ListOnly > **obs:bucket:ListBucket** (Select this operation if you need to use OBS Browser+ to add external buckets.)                                                                                           |
      |                                   |                                                                                                                                                                                                                       |
      |                                   | -  Choose **Specific** > **object** to specify an object resource. The specified object or object set must be consistent with the bucket policy.                                                                      |
      |                                   |                                                                                                                                                                                                                       |
      |                                   |    -  Select **Any** if the resource set in the bucket policy is **\***.                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                       |
      |                                   |    -  If the resource specified in the bucket policy is a specified object or a set of objects, you need to specify the object or the set of objects the same as that in the bucket policy through the resource path. |
      |                                   |                                                                                                                                                                                                                       |
      |                                   |       [Format]                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                       |
      |                                   |       obs:``*``:``*``:object:*bucket name/object name*                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                       |
      |                                   |    Select **Any** as the bucket policy in this example is set to **\***.                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                       |
      |                                   | -  Choose **Specific** > **bucket** > **Specify resource path** to specify bucket resources.                                                                                                                          |
      |                                   |                                                                                                                                                                                                                       |
      |                                   |    Click **Add Resource Path** and enter the name of the authorized bucket in the **Path** text box, for example, **example-bucket**.                                                                                 |
      |                                   |                                                                                                                                                                                                                       |
      |                                   |    The complete path of the resource is as follows: **OBS:*:*:bucket:example-bucket**.                                                                                                                                |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scope                             | The default value is **Global services**.                                                                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Apply the created custom policy to the user group by following the instructions in the IAM document.

#. `Add the IAM user you want to authorize to the created user group <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__.

   .. note::

      Due to data caching, it takes about 10 to 15 minutes for a custom policy to take effect.
