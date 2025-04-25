:original_name: obs_40_0018.html

.. _obs_40_0018:

Granting an IAM User the Specific Permissions on Specific Objects
=================================================================

Scenario
--------

This topic describes how to grant an IAM user the permissions to download specific objects from a bucket.

To grant other permissions, select required actions from **Action Name** in the bucket policy. For details, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.

Recommended Configuration
-------------------------

To grant resource-level permissions to an IAM user, use a bucket policy.

Precautions
-----------

After configuration, the IAM user can download objects using APIs. However, if they download objects using OBS Console or OBS Browser+, a message will be displayed indicating that they do not have required permissions.

When they log in to OBS Console or OBS Browser+, APIs such as **ListAllMyBuckets** and **ListBucket** are called. **ListAllMyBuckets** loads the bucket list while **ListBucket** loads the object list. Some other APIs are also called on other pages. In such case, the message is displayed.

To allow an IAM user to download objects on OBS Console or OBS Browser+, you need to configure custom IAM policies. For details, see :ref:`Follow-up Procedure <obs_40_0018__section220405220511>`.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Objects** page.

#. In the navigation pane, choose **Permissions** > **Bucket Policies**.

#. On the **Bucket Policies** page, click **Create**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000002176507061.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for configuring a bucket policy

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================+
      | Policy view                       | Select **Visual Editor** or **JSON** based on your own habits. **Visual Editor** is used here.                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Enter a policy name.                                                                                                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Allow**.                                                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **Current account**.                                                                                                                                               |
      |                                   | -  Select an IAM user that you want to grant permissions to.                                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  Select **Specified objects**.                                                                                                                                             |
      |                                   | -  Enter an object name prefix for the resource path.                                                                                                                        |
      |                                   |                                                                                                                                                                              |
      |                                   |    .. note::                                                                                                                                                                 |
      |                                   |                                                                                                                                                                              |
      |                                   |       -  You can click **Add** to specify multiple resource paths.                                                                                                           |
      |                                   |                                                                                                                                                                              |
      |                                   |       -  You can specify a specific object, an object set, or a directory. **\*** indicates all objects in the bucket.                                                       |
      |                                   |                                                                                                                                                                              |
      |                                   |          To specify a specific object, enter the object name.                                                                                                                |
      |                                   |                                                                                                                                                                              |
      |                                   |          To specify a set of objects, enter *Object name prefix*\ **\***, **\***\ *Object name suffix*, or **\***.                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  Choose **Customize**.                                                                                                                                                     |
      |                                   | -  Select GetObject (to obtain object content and metadata).                                                                                                                 |
      |                                   |                                                                                                                                                                              |
      |                                   |    .. note::                                                                                                                                                                 |
      |                                   |                                                                                                                                                                              |
      |                                   |       To configure other permissions, select the corresponding actions. For details, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm and click **Create**.

.. _obs_40_0018__section220405220511:

Follow-up Procedure
-------------------

To perform specific operations on OBS Console or OBS Browser+, you must add the **obs:bucket:ListAllMyBuckets** and **obs:bucket:ListBucket** permissions to the custom IAM policy. **obs:bucket:ListAllMyBuckets** lists buckets while **obs:bucket:ListBucket** lists objects in a bucket.

.. note::

   **obs:bucket:ListAllMyBuckets** applies to all resources while **obs:bucket:ListBucket** applies only to the authorized bucket, so you need to add the two permissions to the policy.

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**.

#. In the navigation pane, choose **Permissions** > **Policies/Roles**.

#. Click **Create Custom Policy** in the upper right corner.

#. Configure a custom policy.


   .. figure:: /_static/images/en-us_image_0000001385676688.png
      :alt: **Figure 2** Configuring a custom policy

      **Figure 2** Configuring a custom policy

   .. table:: **Table 2** Parameters for configuring a custom policy

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================+
      | Policy Name                       | Enter a policy name.                                                                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy View                       | Select one based on your own habits. **Visual editor** is used here.                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | [Permission 1]                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                        |
      |                                   | -  Select **Allow**.                                                                                                                                                                                                   |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                                                            |
      |                                   | -  Select **obs:bucket:ListAllMyBuckets** from the actions.                                                                                                                                                            |
      |                                   | -  Select **All** for resources.                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                        |
      |                                   | [Permission 2]                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                        |
      |                                   | -  Select **Allow**.                                                                                                                                                                                                   |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                                                            |
      |                                   | -  Select **obs:bucket:ListBucket** from the actions.                                                                                                                                                                  |
      |                                   | -  Select **Specific** for **Resources** and select **Specify resource path** for **Bucket**. Click **Add Resource Path**. Enter the bucket name in the **Path** text box for applying the policy only to this bucket. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scope                             | Use the default value **Global services**.                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Apply the created custom policy to the user group by following the instructions in the IAM document.

#. `Add the IAM user you want to authorize to the created user group <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__.

   .. note::

      Due to data caching, it takes about 10 to 15 minutes for a custom policy to take effect.
