:original_name: obs_40_0015.html

.. _obs_40_0015:

Granting an IAM User the Read/Write Permission on a Bucket
==========================================================

Scenario
--------

This topic describes how to grant an IAM user the read/write permission on an OBS bucket.

Recommended Configuration
-------------------------

To grant resource-level permissions to an IAM user, use a bucket policy.

Precautions
-----------

After configuration, the IAM user can use APIs or SDKs to upload, download, and delete objects in the bucket. However, if they log in to OBS Console or OBS Browser+ to perform those operations, an error will be reported indicating that they do not have required permissions. .

If you still want the IAM user to perform read and write operations on OBS Console or OBS Browser+, you need to configure custom IAM policies. For details, see :ref:`Follow-up Procedure <obs_40_0015__section220405220511>`.

After configuration, the system still displays a message indicating that the IAM user does not have required permissions, because OBS Console also calls other APIs for advanced configurations. However, the IAM user can still perform read/write operations.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000001436220057.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for creating a bucket policy

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================+
      | Policy Mode                       | Select **Read and write**.                                                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Choose **Include** > **Cloud service user**.                                                                                                                               |
      |                                   | -  **Account ID**: Enter one account ID only, or enter an asterisk (*) to indicate that the policy takes effect on all users (including both registered and anonymous users). |
      |                                   | -  **User ID**: Enter one or more user IDs separated by a comma (,).                                                                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  **Include**                                                                                                                                                                |
      |                                   | -  **Resource Name**: Enter **\***.                                                                                                                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

.. _obs_40_0015__section220405220511:

Follow-up Procedure
-------------------

To perform read and write operations on OBS Console or OBS Browser+, you must add the **obs:bucket:ListAllMyBuckets** (for listing buckets) and **obs:bucket:ListBucket** (for listing objects in a bucket) permissions to the custom IAM policy.

.. note::

   **obs:bucket:ListAllMyBuckets** applies to all resources, while **obs:bucket:ListBucket** applies only to the authorized bucket. Therefore, you need to add these two permissions to the policy.

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**.

#. In the navigation pane, choose **Permissions**.

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
