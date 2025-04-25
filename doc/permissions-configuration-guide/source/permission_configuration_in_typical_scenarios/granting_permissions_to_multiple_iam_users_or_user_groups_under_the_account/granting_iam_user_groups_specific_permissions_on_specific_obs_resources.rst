:original_name: obs_40_0023.html

.. _obs_40_0023:

Granting IAM User Groups Specific Permissions on Specific OBS Resources
=======================================================================

Scenario
--------

This topic describes how to grant specific operation permissions on specific OBS resources (a bucket or an object) to multiple IAM users or user groups.

Recommended Configuration
-------------------------

Use an IAM custom policy to configure the permissions.

Precautions
-----------

After configuration, IAM user groups can perform allowed operations using APIs. If they log in to OBS Console or OBS Browser+ to perform those operations, a message will be displayed indicating that they do not have required permissions.

When they log in to OBS Console or OBS Browser+, APIs (such as **ListAllMyBuckets** and **ListBucket**) are called to load the bucket list and object list and some other APIs will also be called on other pages, but their permissions do not cover those APIs. In such case, the message is displayed.

To allow IAM users to operate buckets and objects on OBS Console or OBS Browser+, add at least the **obs:bucket:ListAllMyBuckets** and **obs:bucket:ListBucket** permissions to the custom policy.

.. note::

   **obs:bucket:ListAllMyBuckets** applies to all resources. You need to select all resources.

   **obs:bucket:ListBucket** applies only to the authorized bucket. You can select all resources or a specified bucket as needed.

Procedure
---------

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**.

#. In the navigation pane, choose **Permissions**.

#. Click **Create Custom Policy** in the upper right corner.

#. Configure a custom policy.


   .. figure:: /_static/images/en-us_image_0000001385859230.png
      :alt: **Figure 1** Configuring a custom policy

      **Figure 1** Configuring a custom policy

   .. table:: **Table 1** Parameters for configuring a custom policy

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                          |
      +===================================+======================================================================================================================================================================================================+
      | Policy Name                       | Enter a policy name.                                                                                                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy View                       | Select one based on your own habits. **Visual editor** is used here.                                                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | [Permission 1] It is mandatory when an authorized user needs to perform operations on OBS Console or OBS Browser+.                                                                                   |
      |                                   |                                                                                                                                                                                                      |
      |                                   | -  Select **Allow**.                                                                                                                                                                                 |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                                          |
      |                                   | -  Select **obs:bucket:ListAllMyBuckets** from the actions.                                                                                                                                          |
      |                                   | -  Select **All** for resources.                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                      |
      |                                   | [Permission 2]                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                      |
      |                                   | -  Select **Allow**.                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                      |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                      |
      |                                   | -  Select the actions to be authorized.                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                      |
      |                                   | -  Choose **Specific resources** > **Bucket** to specify bucket resources.                                                                                                                           |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    [Format]                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    **obs:*:*:bucket:**\ *bucket name*                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    [Note]                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    For bucket resources, IAM automatically generates the prefix of the resource path: **obs:*:*:bucket:**.                                                                                           |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    For the path of a specific bucket, add the *bucket name* to the end. You can also add a wildcard character (``*``) to indicate any bucket. Examples are given as follows:                         |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    -  **obs:*:*:bucket:\*** (indicating any OBS bucket)                                                                                                                                              |
      |                                   |    -  **obs:*:*:bucket:examplebucket** (indicating that the policy applies to bucket **examplebucket**)                                                                                              |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    To perform operations on OBS Console or OBS Browser+, grant the **obs:bucket:ListBucket** permission to a specified bucket.                                                                       |
      |                                   |                                                                                                                                                                                                      |
      |                                   | -  Choose **Specific resources** > **Object** to specify an object resource.                                                                                                                         |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    [Format]                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    Objects in a specified directory: **obs:*:*:object:**\ *Bucket name*\ **/**\ *Prefix*\ **/\***                                                                                                    |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    Specified object: **obs:*:*:object:**\ *Bucket name*\ **/**\ *Object name*                                                                                                                        |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    [Note]                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    For object resources, IAM automatically generates the prefix of the resource path: **obs:*:*:object:**                                                                                            |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    For the path of a specific object, add the *bucket name/object name* to the end. You can also add a wildcard character (``*``) to indicate any object in a bucket. Examples are given as follows: |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    -  **obs:*:*:object:my-bucket/my-object/\*** (indicating any object in the **my-object** directory of bucket **my-bucket**)                                                                       |
      |                                   |    -  **obs:*:*:object:my-bucket/exampleobject** (indicating object **exampleobject** in bucket **my-bucket**)                                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scope                             | The default value is **Global services**.                                                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Apply the created custom policy to the user group by following the instructions in the IAM document.

#. `Add the IAM user you want to authorize to the created user group <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__.

   .. note::

      Due to data caching, it takes about 10 to 15 minutes for a custom policy to take effect.
