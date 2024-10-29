:original_name: obs_40_0016.html

.. _obs_40_0016:

Granting an IAM User the Specified Permissions for a Bucket
===========================================================

Scenario
--------

This topic describes how to grant an IAM user the permissions required to delete a bucket.

To grant other permissions, select required actions from **Action Name** in the bucket policy. For details, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.

Recommended Configuration
-------------------------

To grant resource-level permissions to an IAM user, use a bucket policy.

Precautions
-----------

After configuration, the IAM user can use APIs to delete buckets. However, if they log in to OBS Console or OBS Browser+ to delete buckets, a message will be displayed indicating that they do not have required permissions.

This is because when they log in to OBS Console or OBS Browser+, more APIs (such as **ListAllMyBuckets** and **ListBucketVersions**) will be called to load the list of buckets and versioned objects. In such case, the message is displayed.

If you want an IAM user to delete buckets on OBS Console or OBS Browser+, you need to allow the **ListBucketVersions** permission in the bucket policy and configure a custom IAM policy to grant the **ListAllMyBuckets** permission by referring to :ref:`Follow-up Procedure <obs_40_0016__section220405220511>`.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000001385678272.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for creating a bucket policy

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================+
      | Policy Mode                       | Select **Customized**.                                                                                                                                                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Allow**.                                                                                                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Choose **Include** > **Cloud service user**.                                                                                                                               |
      |                                   | -  **Account ID**: Enter one account ID only, or enter an asterisk (*) to indicate that the policy takes effect on all users (including both registered and anonymous users). |
      |                                   | -  **User ID**: Enter one or more user IDs separated by a comma (,).                                                                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | Select **Include** > **Entire bucket**.                                                                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                                                                                                |
      |                                   | -  **Action Name**:                                                                                                                                                           |
      |                                   |                                                                                                                                                                               |
      |                                   |    -  DeleteBucket                                                                                                                                                            |
      |                                   |    -  ListBucketVersions (required when an authorized user needs to access OBS from OBS Console or OBS Browser+)                                                              |
      |                                   |                                                                                                                                                                               |
      |                                   | To configure other permissions, select the corresponding actions. For details, see :ref:`Action/NotAction <obs_40_0041__en-us_topic_0118394684_section1623516525350>`.        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

.. _obs_40_0016__section220405220511:

Follow-up Procedure
-------------------

To delete buckets on OBS Console or OBS Browser+, you need to allow the **obs:bucket:ListAllMyBuckets** permission in the IAM policy.

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**.

#. In the navigation pane, choose **Permissions**.

#. Click **Create Custom Policy** in the upper right corner.

#. Configure a custom policy.


   .. figure:: /_static/images/en-us_image_0000001385362028.png
      :alt: **Figure 2** Configuring a custom policy

      **Figure 2** Configuring a custom policy

   .. table:: **Table 2** Parameters for configuring a custom policy

      +-----------------------------------+----------------------------------------------------------------------+
      | Parameter                         | Description                                                          |
      +===================================+======================================================================+
      | Policy Name                       | Enter a policy name.                                                 |
      +-----------------------------------+----------------------------------------------------------------------+
      | Policy View                       | Select one based on your own habits. **Visual editor** is used here. |
      +-----------------------------------+----------------------------------------------------------------------+
      | Policy Content                    | -  Select **Allow**.                                                 |
      |                                   | -  Select **Object Storage Service (OBS)**.                          |
      |                                   | -  Select **obs:bucket:ListAllMyBuckets** from the actions.          |
      |                                   | -  Select **All** for resources.                                     |
      +-----------------------------------+----------------------------------------------------------------------+
      | Scope                             | Use the default value **Global services**.                           |
      +-----------------------------------+----------------------------------------------------------------------+

#. Click **OK**.

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Apply the created custom policy to the user group by following the instructions in the IAM document.

#. `Add the IAM user you want to authorize to the created user group <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__.

   .. note::

      Due to data caching, it takes about 10 to 15 minutes for a custom policy to take effect.
