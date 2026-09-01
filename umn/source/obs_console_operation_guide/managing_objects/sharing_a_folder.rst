:original_name: obs_03_0104.html

.. _obs_03_0104:

Sharing a Folder
================

Scenarios
---------

You can share your folders in OBS to other users.

Background Information
----------------------

Folder sharing is temporary and has a validity period. You need to specify a six-digit access code before creating a sharing task. After the sharing task is created, OBS aggregates the download links of all objects in the folder to a static website that is hosted by a public OBS bucket. Then anyone who has the created temporary URL and access code can access the static website and download the shared files.

Constraints
-----------

-  A folder shared from OBS Console can be valid for one minute to 18 hours. If you want the shared folder permanently valid, configure a :ref:`bucket policy or object policy <en-us_topic_0045853745>` to achieve that.
-  Folder sharing is restricted to a few regions only.
-  Only version 3.0 buckets support folder sharing. You can view the bucket version in the **Basic Information** area on the **Overview** page of a bucket.
-  Cold objects in the folder need to be restored in the bucket before they can be downloaded.

Procedure
---------

#. In the bucket list of OBS Console, click the desired bucket to go to the **Objects** page.
#. Locate the folder you want to share and click **Share** in the **Operation** column. The **Share Folder** dialog box is displayed.
#. Share the folder by access code or URL.
#. Method 1: Share the folder by access code.

   a. Choose **Access code** for **Share By**.
   b. Configure parameters.

      .. table:: **Table 1** Parameters for sharing a folder with an access code

         +-----------------------------------+--------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                          |
         +===================================+======================================================================================+
         | URL Validity Period               | A validity period is from one minute to 18 hours. The default value is five minutes. |
         |                                   |                                                                                      |
         |                                   | Within the URL validity period, anyone who has the URL can access the folder.        |
         +-----------------------------------+--------------------------------------------------------------------------------------+
         | Access Code                       | A six-digit code.                                                                    |
         |                                   |                                                                                      |
         |                                   | An access code is required to access objects in the shared folder.                   |
         +-----------------------------------+--------------------------------------------------------------------------------------+

   c. Click **Create Share** to generate a sharing URL for the folder.
   d. Send the shared URL and access code to other users for them to access the folder.
   e. Verify that they can perform the following operations:

      #. Open the shared URL in a web browser.
      #. In the dialog box that is displayed, enter the access code and access object in the shared folder.

#. Method 2: Share the folder by URL.

   a. Choose **URL** for **Share By**.

   b. Configure parameters.

      .. table:: **Table 2** Parameters for sharing a folder by URL

         +-----------------------------------+--------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                          |
         +===================================+======================================================================================+
         | URL Validity Period               | A validity period is from one minute to 18 hours. The default value is five minutes. |
         |                                   |                                                                                      |
         |                                   | Within the URL validity period, anyone who has the URL can access the folder.        |
         +-----------------------------------+--------------------------------------------------------------------------------------+

   c. Click **Copy Link** and share the link with another user. The user then can use this link to access all objects in this folder. The shared link consists of the bucket domain name (prefix) and signature information (suffix). Users can add an object path after the prefix of the shared link to access or download the specified object in the folder, as shown in :ref:`Figure 1 <obs_03_0104__fig4334102417599>`.

   d. Verify that a user can use the shared link to access all objects or a specified object in the folder.

      #. Open a browser.
      #. Enter the shared link in the address box and press **Enter** to list all objects in the folder.
      #. Copy the object path and paste it after the prefix.
      #. Press **Enter**. You can then access and download the specified object.

      .. _obs_03_0104__fig4334102417599:

      .. figure:: /_static/images/en-us_image_0000002540964116.png
         :alt: **Figure 1** Accessing an object with a shared link

         **Figure 1** Accessing an object with a shared link
