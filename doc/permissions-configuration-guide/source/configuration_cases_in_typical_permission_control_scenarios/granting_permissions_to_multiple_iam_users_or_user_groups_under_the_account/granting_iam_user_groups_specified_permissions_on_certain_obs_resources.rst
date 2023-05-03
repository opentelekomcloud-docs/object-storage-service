:original_name: obs_40_0023.html

.. _obs_40_0023:

Granting IAM User Groups Specified Permissions on Certain OBS Resources
=======================================================================

Scenario
--------

This topic describes how to grant certain operation permissions on specific OBS resources (can be a bucket or an object) to multiple IAM users or user groups.

Recommended Configuration
-------------------------

IAM custom policies

Configuration Precautions
-------------------------

After the configuration is complete, you can perform allowed operations using APIs. However, if you log in to OBS Console or OBS Browser+ to perform those operations, an error is reported indicating that you do not have required permissions.

This is because when you log in to OBS Console or OBS Browser+, APIs (such as **ListAllMyBuckets** and **ListBucket**) are called to load the bucket list and object list and some other APIs will also be called on other pages, but your permissions do not cover those APIs. In such case, your access to OBS Console or OBS Browser+ is denied or your operation is not allowed.

To allow IAM users to operate buckets and objects on OBS Console or OBS Browser+, add at least the **obs:bucket:ListAllMyBuckets** and **obs:bucket:ListBucket** permissions to the custom policy.

.. note::

   **obs:bucket:ListAllMyBuckets** applies to all resources. You need to select all resources.

   **obs:bucket:ListBucket** applies only to the authorized bucket. You can select all resources or a specified bucket as needed.

Procedure
---------

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**. The IAM console is displayed.

#. In the navigation pane, choose **Permissions**.

#. Click **Create Custom Policy** in the upper right corner.

#. Configure parameters for a custom policy.


   .. figure:: /_static/images/en-us_image_0000001385859230.png
      :alt: **Figure 1** Configuring a custom policy

      **Figure 1** Configuring a custom policy

   .. table:: **Table 1** Parameters for configuring a custom policy

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================+
      | Policy Name                       | Name of the custom policy                                                                                                                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy View                       | Set this parameter based on your own habits. **Visual editor** is used here.                                                                                                   |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | [Permission 1] It is mandatory when an authorized user needs to perform operations on OBS Console or OBS Browser+.                                                             |
      |                                   |                                                                                                                                                                                |
      |                                   | -  Select **Allow**.                                                                                                                                                           |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                    |
      |                                   | -  Select **obs:bucket:ListAllMyBuckets** from the actions.                                                                                                                    |
      |                                   | -  Select **All** for resources.                                                                                                                                               |
      |                                   |                                                                                                                                                                                |
      |                                   | [Permission 2]                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                |
      |                                   | -  Select **Allow**.                                                                                                                                                           |
      |                                   |                                                                                                                                                                                |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                    |
      |                                   |                                                                                                                                                                                |
      |                                   | -  Select the actions to be authorized.                                                                                                                                        |
      |                                   |                                                                                                                                                                                |
      |                                   | -  Choose **Specific resources** > **Bucket** to specify bucket resources.                                                                                                     |
      |                                   |                                                                                                                                                                                |
      |                                   |    [Format]                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                |
      |                                   |    **obs:*:*:bucket:**\ *bucket name*                                                                                                                                          |
      |                                   |                                                                                                                                                                                |
      |                                   |    [Note]                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                |
      |                                   |    For bucket resources, IAM automatically generates the prefix of the resource path: **obs:*:*:bucket:**.                                                                     |
      |                                   |                                                                                                                                                                                |
      |                                   |    For the path of a specific bucket, add the *bucket name* to the end. You can also add a wildcard character (``*``) to indicate any bucket. Example:                         |
      |                                   |                                                                                                                                                                                |
      |                                   |    **obs:*:*:bucket:\***, indicating any OBS bucket.                                                                                                                           |
      |                                   |                                                                                                                                                                                |
      |                                   |    To perform operations on OBS Console or OBS Browser+, grant the **obs:bucket:ListBucket** permission to a specified bucket.                                                 |
      |                                   |                                                                                                                                                                                |
      |                                   | -  Choose **Specific resources** > **Object** to specify an object resource.                                                                                                   |
      |                                   |                                                                                                                                                                                |
      |                                   |    [Format]                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                |
      |                                   |    obs:*:*:object:\ *bucket name/object name*                                                                                                                                  |
      |                                   |                                                                                                                                                                                |
      |                                   |    [Note]                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                |
      |                                   |    For object resources, IAM automatically generates the prefix of the resource path: **obs:*:*:object:**                                                                      |
      |                                   |                                                                                                                                                                                |
      |                                   |    For the path of a specific object, add the *bucket name/object name* to the end. You can also add a wildcard character (``*``) to indicate any object in a bucket. Example: |
      |                                   |                                                                                                                                                                                |
      |                                   |    **obs:*:*:object:my-bucket/my-object/\***: any object in the **my-object** directory of the **my-bucket** bucket.                                                           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scope                             | The default value is **Global services**.                                                                                                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. The custom policy is created.

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Add the created custom policy to the user group by following the instructions in the IAM document.

#. Add the IAM user you want to authorize to the created user group by referring to `Creating a User and Adding the User to a User Group <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__.

   .. note::

      Due to data caching, it takes about 10 to 15 minutes for a custom policy to take effect after the authorization.
