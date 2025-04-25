:original_name: obs_40_0025.html

.. _obs_40_0025:

Granting Other Accounts the Read/Write Permission for a Bucket
==============================================================

Scenario
--------

This topic describes how to grant other accounts (excluding the IAM users under them) the read/write permission for OBS buckets. For details about how to grant permissions to an IAM user, see :ref:`Granting IAM Users Under an Account the Access to a Bucket and the Resources in It <obs_40_0027>`.

Recommended Configuration
-------------------------

Use bucket policies to grant permissions to other accounts.

Precautions
-----------

After the configuration is complete, the authorized account can perform read and write operations (upload, download, or delete all objects in a bucket) by using APIs or by adding external buckets through OBS Browser+. Currently, access to buckets of other accounts is not allowed on OBS Console.

When you use OBS Browser+ to access the added external bucket, a message may still be displayed indicating that you do not have required permissions.

Error cause: The loading on the OBS Browser+ bucket details page invokes some other OBS APIs. However, such operations are not allowed by the read and write permissions. Therefore, a message "Access denied. Check the response permission" or "This operation is not allowed on the requested resource" is displayed, however, existing permissions are not affected.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Buckets**.

#. In the bucket list, click the bucket name you want to go to the **Objects** page.

#. In the navigation pane, choose **Permissions** > **Bucket Policies**.

#. On the **Bucket Policies** page, click **Create**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000002141465550.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for configuring a bucket policy

      +----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                              | Description                                                                                                                                                                                                   |
      +========================================+===============================================================================================================================================================================================================+
      | Policy view                            | Select **Visual Editor** or **JSON** based on your own habits. **Visual Editor** is used here.                                                                                                                |
      +----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                            | Enter a policy name.                                                                                                                                                                                          |
      +----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                                 | Select **Allow**.                                                                                                                                                                                             |
      +----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                              | -  Select **Other accounts**.                                                                                                                                                                                 |
      |                                        |                                                                                                                                                                                                               |
      |                                        |    Enter the account ID and IAM user ID in the format of *Account ID/IAM user ID*. To specify multiple IAM users, enter each one on a separate line. An asterisk (``*``) indicates all accounts or IAM users. |
      |                                        |                                                                                                                                                                                                               |
      |                                        |    .. note::                                                                                                                                                                                                  |
      |                                        |                                                                                                                                                                                                               |
      |                                        |       The account ID and IAM user ID can be obtained on the **My Credentials** page. The following describes different authorization scenarios:                                                               |
      |                                        |                                                                                                                                                                                                               |
      |                                        |       -  **Granting permissions to all accounts and IAM users**: Enter **\*/\***.                                                                                                                             |
      |                                        |       -  **Granting permissions to an account and all IAM users under the account**: Enter *Account ID*\ **/\***.                                                                                             |
      |                                        |       -  **Granting permissions to a specific IAM user under an account**: Enter *Account ID/IAM user ID*.                                                                                                    |
      |                                        |                                                                                                                                                                                                               |
      |                                        | -  **Delegated accounts**: Enter the ID of a delegating account and an agency name.                                                                                                                           |
      |                                        |                                                                                                                                                                                                               |
      |                                        |    .. note::                                                                                                                                                                                                  |
      |                                        |                                                                                                                                                                                                               |
      |                                        |       The format is *Account ID/Agency name*. To specify multiple agencies, enter each one on a separate line.                                                                                                |
      |                                        |                                                                                                                                                                                                               |
      |                                        | -  You can specify one or more common accounts or delegated accounts. Either of the two types of accounts must be specified.                                                                                  |
      +----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                              | -  Select **Entire bucket (including the objects in it)**.                                                                                                                                                    |
      +----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                                | -  Choose **Use a template**.                                                                                                                                                                                 |
      |                                        | -  Select **Bucket Read/Write**.                                                                                                                                                                              |
      +----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Advanced Settings > Exclude (Optional) | -  **Specified actions** (selected by default)                                                                                                                                                                |
      +----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm and click **Create**.
