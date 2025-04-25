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

#. In the bucket list, click the bucket name you want to go to the **Objects** page.

#. In the navigation pane, choose **Permissions** > **Bucket Policies**.

#. On the **Bucket Policies** page, click **Create**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000002177944385.png
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
      |                                   |       a. You can click **Add** to specify multiple resource paths.                                                                                                                                            |
      |                                   |                                                                                                                                                                                                               |
      |                                   |       b. You can specify a specific object, an object set, or a directory. **\*** indicates all objects in the bucket.                                                                                        |
      |                                   |                                                                                                                                                                                                               |
      |                                   |          To specify a specific object, enter the object name.                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                               |
      |                                   |          To specify a set of objects, enter *Object name prefix*\ **\***, **\***\ *Object name suffix*, or **\***.                                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  Choose **Customize**.                                                                                                                                                                                      |
      |                                   | -  Select GetObject (to obtain object content and metadata).                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    .. note::                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                               |
      |                                   |       To grant other permissions, select required actions based on :ref:`actions supported by OBS <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm and click **Create**.
