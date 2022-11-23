:original_name: obs_03_0136.html

.. _obs_03_0136:

Application Example 3: Authorizing Access Permissions Required for Adding an External Bucket Through the Custom Bucket Policy
=============================================================================================================================

A custom bucket policy can be used to grant the read and write access permissions to the bucket to be added.

If a custom bucket policy is used to authorize such permissions, the ListBucket, GetObject, and GetObjectVersion actions must be allowed. More actions can be allowed according to your actual needs.

Procedure
---------

#. Log in to OBS Console.
#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.
#. In the navigation pane on the left, click **Permissions** to go to the permission management page.
#. In the **Custom Bucket Policies** area, click **Create Bucket Policy**. The **Create Bucket Policy** dialog box is displayed.
#. Set the following parameters to authorize another account with the permission to access the bucket:

   .. table:: **Table 1** Parameters for authorizing the permission to access a specified bucket

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      +===================================+================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Policy Mode                       | **Customized**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | **Allow**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  **Include**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   | -  **Other account**: Enter the account ID. If you want to authorize the permissions all users, enter **\***.                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |    The account ID and user ID can be obtained on the **My Credentials** page of the account or user to be authorized. **Account ID** corresponds to **Domain ID** on the **My Credential** page. If you authorize the permission to only an account, you do not need to enter user IDs. If you want to authorize the permission to an IAM user, you need to enter the account ID and user ID. You can authorize the permission to multiple IAM users. Use commas (,) to separate the user IDs. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  **Include**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   | -  Leave it blank.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   | -  ListBucket                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
#. Create another bucket policy and set the parameters according to the following table to grant the authorized account with access permissions to resources in the bucket.

   .. table:: **Table 2** Parameters for authorizing the permission to access a specified bucket

      +-----------------------------------+------------------------------------------------------+
      | Parameter                         | Value                                                |
      +===================================+======================================================+
      | Policy Mode                       | **Customized**                                       |
      +-----------------------------------+------------------------------------------------------+
      | Effect                            | **Allow**                                            |
      +-----------------------------------+------------------------------------------------------+
      | **Principal**                     | Keep the value consistent with the preceding policy. |
      +-----------------------------------+------------------------------------------------------+
      | **Resources**                     | -  **Include**                                       |
      |                                   | -  Resource name: **\***                             |
      +-----------------------------------+------------------------------------------------------+
      | **Actions**                       | -  **Include**                                       |
      |                                   | -  GetObject                                         |
      |                                   | -  GetObjectVersion                                  |
      |                                   | -  PutObject                                         |
      |                                   | -  DeleteObject                                      |
      |                                   | -  DeleteObjectVersion                               |
      +-----------------------------------+------------------------------------------------------+

#. Click **OK**.

Verification
------------

#. Log in to OBS Browser.
#. Click **Add Bucket** on the upper left corner of the page. The **Add Bucket** dialog box is displayed.
#. Select **Add external bucket** and enter the bucket name.
#. Click **OK**. The external bucket is added successfully.
#. Click the newly added external bucket to open the bucket.
#. Click **Upload Object**, and objects can be successfully uploaded to the bucket.
#. Select an object in the bucket and click **Delete**. The object can be deleted successfully.
