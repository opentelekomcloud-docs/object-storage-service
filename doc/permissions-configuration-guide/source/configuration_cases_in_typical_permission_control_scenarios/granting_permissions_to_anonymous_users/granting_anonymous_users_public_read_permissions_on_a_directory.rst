:original_name: obs_40_0032.html

.. _obs_40_0032:

Granting Anonymous Users Public Read Permissions on a Directory
===============================================================

Scenario
--------

If all objects in a folder need to be accessible to anonymous users, you can configure a bucket policy to grant anonymous users the permission to access the folder.

Configuration Precautions
-------------------------

The preset read-only mode of OBS has the following permissions:

-  GetObject: downloading objects
-  GetObjectVersion: downloading versioned objects

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure parameters according to the following table, so that you can grant anonymous users the permission to access the folder and objects in it.


   .. figure:: /_static/images/en-us_image_0000001436146565.png
      :alt: **Figure 1** Granting public read permissions on a specific directory for anonymous users

      **Figure 1** Granting public read permissions on a specific directory for anonymous users

   .. table:: **Table 1** Parameters for granting the permission to access a specified directory

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Value                                                                                                                                 |
      +===================================+=======================================================================================================================================+
      | Policy Mode                       | Select **Read-only**.                                                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Choose **Include** > **Cloud service user**.                                                                                       |
      |                                   | -  **Account ID**: Enter **\*** to indicate all anonymous users.                                                                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  **Include**                                                                                                                        |
      |                                   | -  Select **Specific resources**.                                                                                                     |
      |                                   | -  Set this parameter to all objects in the selected folder. If the folder name is **folder-001**, enter the value **folder-001/\***. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Verification
------------

After the permission is set, click an object in the folder. Its URL is displayed under **Link**. Share the URL over the Internet, so that all users can access or download the object through the Internet.
