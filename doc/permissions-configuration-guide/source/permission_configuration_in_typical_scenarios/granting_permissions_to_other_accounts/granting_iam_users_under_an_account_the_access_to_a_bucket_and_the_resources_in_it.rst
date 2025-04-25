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

#. In the bucket list, click the bucket name you want to go to the **Objects** page.

#. In the navigation pane, choose **Permissions** > **Bucket Policies**.

#. On the **Bucket Policies** page, click **Create**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000002142442622.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for configuring a bucket policy

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================+
      | Policy view                       | Select **Visual Editor** or **JSON** based on your own habits. **Visual Editor** is used here.                                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Enter a policy name.                                                                                                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Allow**.                                                                                                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **Other accounts**.                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    Enter the account ID and IAM user ID in the format of *Account ID/IAM user ID*. To specify multiple IAM users, enter each one on a separate line. An asterisk (``*``) indicates all accounts or IAM users. |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    .. note::                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                               |
      |                                   |       The account ID and IAM user ID can be obtained on the **My Credentials** page. The following describes different authorization scenarios:                                                               |
      |                                   |                                                                                                                                                                                                               |
      |                                   |       -  **Granting permissions to all accounts and IAM users**: Enter **\*/\***.                                                                                                                             |
      |                                   |       -  **Granting permissions to an account and all IAM users under the account**: Enter *Account ID*\ **/\***.                                                                                             |
      |                                   |       -  **Granting permissions to a specific IAM user under an account**: Enter *Account ID/IAM user ID*.                                                                                                    |
      |                                   |                                                                                                                                                                                                               |
      |                                   | -  **Delegated accounts**: Enter the ID of a delegating account and an agency name.                                                                                                                           |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    .. note::                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                               |
      |                                   |       The format is *Account ID/Agency name*. To specify multiple agencies, enter each one on a separate line.                                                                                                |
      |                                   |                                                                                                                                                                                                               |
      |                                   | -  You can specify one or more common accounts or delegated accounts. Either of the two types of accounts must be specified.                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  Select **Current bucket** and **Specified objects**.                                                                                                                                                       |
      |                                   | -  Enter an object name prefix for the resource path.                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    .. note::                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                               |
      |                                   |       a. You can click **Add** to specify multiple resource paths.                                                                                                                                            |
      |                                   |                                                                                                                                                                                                               |
      |                                   |       b. You can specify a specific object, an object set, or a directory. **\*** indicates all objects in the bucket.                                                                                        |
      |                                   |                                                                                                                                                                                                               |
      |                                   |          To specify a specific object, enter the object name.                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                               |
      |                                   |          To specify a set of objects, enter *Object name prefix*\ **\***, **\***\ *Object name suffix*, or **\***.                                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  Choose **Customize**.                                                                                                                                                                                      |
      |                                   | -  Select actions:                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    -  GetObject (to obtain object content and metadata)                                                                                                                                                       |
      |                                   |    -  GetObjectVersion (to obtain the content and metadata of a specified object version)                                                                                                                     |
      |                                   |    -  PutObject (to upload objects using PUT and POST, upload parts, initiate multipart uploads, and assemble parts)                                                                                          |
      |                                   |    -  (Optional) ListBucket (to list objects in the bucket and obtain the bucket metadata)                                                                                                                    |
      |                                   |                                                                                                                                                                                                               |
      |                                   |       .. note::                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                               |
      |                                   |          To grant other permissions, select required actions based on :ref:`actions supported by OBS <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm and click **Create**.

Procedure 2: The Account Grants Permissions to IAM Users Under It.
------------------------------------------------------------------

**The account (not the bucket owner) needs to grant permissions to its IAM users to perform specified operations on the bucket. (The allowed operations must be the same as those allowed in the bucket policy.)**

In this example, account **A** needs to grant IAM user **A** the permissions to upload objects to and download objects from bucket **B** of account **B**.

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**.

#. In the navigation pane, choose **Permissions** > **Policies/Roles**.

#. Click **Create Custom Policy** in the upper right corner.

#. Configure a custom policy.


   .. figure:: /_static/images/en-us_image_0000001436303585.png
      :alt: **Figure 2** Configuring a custom policy

      **Figure 2** Configuring a custom policy

   .. table:: **Table 2** Parameters for configuring a custom policy

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================================================+
      | Policy Name                       | Enter a policy name.                                                                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy View                       | Select **Visual editor** or **JSON** based on your own habits. **Visual editor** is used here.                                                                                                                        |
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
