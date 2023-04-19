:original_name: obs_40_0022.html

.. _obs_40_0022:

Granting IAM User Groups Specified Permissions on All OBS Resources
===================================================================

Scenario
--------

This topic describes how to grant multiple IAM users or user groups specific permissions on all OBS resources.

Recommended Configuration
-------------------------

IAM custom policies

Configuration Precautions
-------------------------

After the configuration is complete, you can perform allowed operations using APIs. However, if you log in to OBS Console or OBS Browser+ to perform those operations, an error is reported indicating that you do not have required permissions.

This is because when you log in to OBS Console or OBS Browser+, APIs (such as **ListAllMyBuckets** and **ListBucket**) are called to load the bucket list and object list and some other APIs will also be called on other pages, but your permissions do not cover those APIs. In such case, your access to OBS Console or OBS Browser+ is denied or your operation is not allowed.

To allow IAM users to operate buckets and objects on OBS Console or OBS Browser+, add at least the **obs:bucket:ListAllMyBuckets** and **obs:bucket:ListBucket** permissions to the custom policy.

Procedure
---------

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**. The IAM console is displayed.

#. In the navigation pane, choose **Permissions**.

#. Click **Create Custom Policy** in the upper right corner.

#. Configure parameters for a custom policy.


   .. figure:: /_static/images/en-us_image_0000001436253413.png
      :alt: **Figure 1** Configuring a custom policy

      **Figure 1** Configuring a custom policy

   .. table:: **Table 1** Parameters for configuring a custom policy

      +-----------------------------------+------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                  |
      +===================================+==============================================================================+
      | Policy Name                       | Name of the custom policy                                                    |
      +-----------------------------------+------------------------------------------------------------------------------+
      | Policy View                       | Set this parameter based on your own habits. **Visual editor** is used here. |
      +-----------------------------------+------------------------------------------------------------------------------+
      | Policy Content                    | -  Select **Allow**.                                                         |
      |                                   | -  Select **Object Storage Service (OBS)**.                                  |
      |                                   | -  Select the actions to be authorized.                                      |
      |                                   | -  Select **All** for resources.                                             |
      +-----------------------------------+------------------------------------------------------------------------------+
      | Scope                             | The default value is **Global services**.                                    |
      +-----------------------------------+------------------------------------------------------------------------------+

#. Click **OK**. The custom policy is created.

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Add the created custom policy to the user group by following the instructions in the IAM document.

#. Add the IAM user you want to authorize to the created user group by referring to `Creating a User and Adding the User to a User Group <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__.

   .. note::

      Due to data caching, it takes about 10 to 15 minutes for a custom policy to take effect after the authorization.
