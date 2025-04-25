:original_name: obs_40_0032.html

.. _obs_40_0032:

Granting Anonymous Users the Read Permission for a Directory
============================================================

Scenario
--------

If all objects in a folder need to be accessible to anonymous users, you can configure a bucket policy to grant anonymous users the permission to access the folder.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Objects** page.

#. In the navigation pane, choose **Permissions** > **Bucket Policies**.

#. On the **Bucket Policies** page, click **Create**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000002142518978.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for configuring a bucket policy

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                         |
      +===================================+=====================================================================================================================+
      | Policy view                       | Select **Visual Editor** or **JSON** based on your own habits. **Visual Editor** is used here.                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Enter a policy name.                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Allow**.                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **All accounts**.                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  Select **Current bucket** and **Specified objects**.                                                             |
      |                                   | -  Set the resource path to **folder-001/\*** (as an example), indicating all objects in the **folder-001** folder. |
      |                                   |                                                                                                                     |
      |                                   |    .. note::                                                                                                        |
      |                                   |                                                                                                                     |
      |                                   |       You can click **Add** to specify multiple resource paths.                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  Choose **Use a template**.                                                                                       |
      |                                   | -  Select **Directory Read-Only**.                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+

#. Confirm and click **Create**.

Verification
------------

After the permission is set, click an object in the folder. Its URL is displayed under **Link**. Share the URL over the Internet, so that all users can access or download the object through the Internet.
