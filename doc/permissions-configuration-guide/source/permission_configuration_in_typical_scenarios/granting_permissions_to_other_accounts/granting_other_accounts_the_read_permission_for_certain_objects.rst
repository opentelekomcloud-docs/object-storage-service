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

When they log in to OBS Console or OBS Browser+, the **ListAllMyBuckets** API is called to load the bucket list and some other APIs will also be called on other pages, but their permissions do not cover those APIs. In such case, the message is displayed.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Objects** page.

#. In the navigation pane, choose **Permissions** > **Bucket Policies**.

#. On the **Bucket Policies** page, click **Create**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000002142310216.png
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
      | Resources                         | -  Select **Specified objects**.                                                                                                                                                                              |
      |                                   | -  Enter an object name prefix for the resource path.                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    .. note::                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                               |
      |                                   |       -  You can click **Add** to specify multiple resource paths.                                                                                                                                            |
      |                                   |                                                                                                                                                                                                               |
      |                                   |       -  You can specify a specific object, an object set, or a directory. **\*** indicates all objects in the bucket.                                                                                        |
      |                                   |                                                                                                                                                                                                               |
      |                                   |          To specify a specific object, enter the object name.                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                               |
      |                                   |          To specify a set of objects, enter *Object name prefix*\ **\***, **\***\ *Object name suffix*, or **\***.                                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  Choose **Use a template**.                                                                                                                                                                                 |
      |                                   | -  Select **Object Read-Only**.                                                                                                                                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm and click **Create**.
