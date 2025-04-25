:original_name: obs_40_0026.html

.. _obs_40_0026:

Granting Other Accounts the Specified Permissions for a Bucket
==============================================================

Scenario
--------

This topic describes how to grant other accounts (excluding the IAM users under them) specific permissions for OBS buckets. For details about how to grant permissions to an IAM user, see :ref:`Granting IAM Users Under an Account the Access to a Bucket and the Resources in It <obs_40_0027>`.

The following example explains how to grant the permissions to configure a bucket ACL and obtain the bucket ACL configuration information. To grant other permissions, select required actions from **Action Name** in the bucket policy. For details about the actions supported by OBS, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.

Recommended Configuration
-------------------------

Use bucket policies to grant permissions to other accounts.

Precautions
-----------

After configuration, the authorized account can configure and obtain a bucket ACL by using APIs or SDKs or by adding external buckets through OBS Browser+. To do this by adding external buckets, the **ListBucket** permission is also required. Currently, access to buckets of other accounts is not allowed on OBS Console.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Objects** page.

#. In the navigation pane, choose **Permissions** > **Bucket Policies**.

#. On the **Bucket Policies** page, click **Create**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000002142430154.png
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
      | Resources                         | -  Select **Current bucket**.                                                                                                                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  Choose **Customize**.                                                                                                                                                                                      |
      |                                   | -  Select actions:                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    -  PutBucketAcl (to configure a bucket ACL)                                                                                                                                                                |
      |                                   |    -  GetBucketAcl (to obtain the bucket ACL information)                                                                                                                                                     |
      |                                   |    -  (Optional) ListBucket (to list objects in the bucket and obtain the bucket metadata)                                                                                                                    |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    .. note::                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                               |
      |                                   |       To grant other permissions, select required actions based on :ref:`actions supported by OBS <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm and click **Create**.
