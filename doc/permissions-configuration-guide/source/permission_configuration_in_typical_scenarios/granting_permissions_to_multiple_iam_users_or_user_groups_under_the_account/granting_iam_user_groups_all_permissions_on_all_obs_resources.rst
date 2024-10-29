:original_name: obs_40_0020.html

.. _obs_40_0020:

Granting IAM User Groups All Permissions on All OBS Resources
=============================================================

Scenario
--------

This topic describes how to grant multiple IAM users or user groups all permissions on all OBS resources. Users with this permission can perform any operations on OBS.

Recommended Configuration
-------------------------

Use an IAM custom policy to configure the permissions.

Procedure
---------

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**.

#. In the navigation pane, choose **Permissions**.

#. Click **Create Custom Policy** in the upper right corner.

#. Configure a custom policy.


   .. figure:: /_static/images/en-us_image_0000001385530212.png
      :alt: **Figure 1** Configuring a custom policy

      **Figure 1** Configuring a custom policy

   .. table:: **Table 1** Parameters for configuring a custom policy

      +-----------------------------------+----------------------------------------------------------------------+
      | Parameter                         | Description                                                          |
      +===================================+======================================================================+
      | Policy Name                       | Enter a policy name.                                                 |
      +-----------------------------------+----------------------------------------------------------------------+
      | Policy View                       | Select one based on your own habits. **Visual editor** is used here. |
      +-----------------------------------+----------------------------------------------------------------------+
      | Policy Content                    | -  Select **Allow**.                                                 |
      |                                   | -  Select **Object Storage Service (OBS)**.                          |
      |                                   | -  Select all actions.                                               |
      |                                   | -  Select **All** for resources.                                     |
      +-----------------------------------+----------------------------------------------------------------------+
      | Scope                             | The default value is **Global services**.                            |
      +-----------------------------------+----------------------------------------------------------------------+

#. Click **OK**.

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Apply the created custom policy to the user group by following the instructions in the IAM document.

#. `Add the IAM user you want to authorize to the created user group <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__.

   .. note::

      Due to data caching, it takes about 10 to 15 minutes for a custom policy to take effect.
