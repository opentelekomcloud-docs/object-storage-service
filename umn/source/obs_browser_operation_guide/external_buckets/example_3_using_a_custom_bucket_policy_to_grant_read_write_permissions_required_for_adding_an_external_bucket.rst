:original_name: obs_03_0136.html

.. _obs_03_0136:

Example 3: Using a Custom Bucket Policy to Grant Read/Write Permissions Required for Adding an External Bucket
==============================================================================================================

A custom bucket policy can be used to grant the read and write access permissions to the bucket to be added.

If a custom bucket policy is used to authorize such permissions, the ListBucket, GetObject, and GetObjectVersion actions must be allowed. More actions can be allowed according to your actual needs.

Procedure
---------

#. Log in to OBS Console.
#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.
#. In the navigation pane on the left, click **Permissions** to go to the permission management page.
#. In the **Custom Bucket Policies** area, click **Create Bucket Policy**. The **Create Bucket Policy** dialog box is displayed.
#. Configure the parameters listed in the table below to grant other accounts the bucket access permissions.

   .. table:: **Table 1** Parameters for granting permissions to access the bucket

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      +===================================+================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Policy Mode                       | **Customized**                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | **Allow**                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  **Include**                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   | -  **Other account**: Enter an account ID. If you want to grant the permissions to all users, enter **\***.                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |    The account ID and user ID can be obtained on the **My Credentials** page of the account or user to be authorized. **Account ID** corresponds to **Domain ID** on the **My Credentials** page. If you grant the permission to only an account, you do not need to enter user IDs. If you want to grant the permission to IAM users of an account, you need to enter the account ID and user IDs. Multiple IAM user IDs should be separated with commas (,). |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  **Include**                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   | -  Leave it blank.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   | -  ListBucket                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
#. Create another bucket policy to grant the authorized account the permissions to access resources in the bucket. For details, see the table below.

   .. table:: **Table 2** Parameters for granting permissions to access resources in the bucket

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
