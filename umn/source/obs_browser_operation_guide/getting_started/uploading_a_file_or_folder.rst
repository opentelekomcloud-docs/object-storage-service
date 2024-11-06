:original_name: obs_03_0024.html

.. _obs_03_0024:

Uploading a File or Folder
==========================

Background Information
----------------------

-  Files are uploaded in multiparts on OBS Browser. OBS Browser supports the upload of a single file with the maximum size of 48.8 TB.
-  OBS Browser supports resumable transfer. If the upload task is suspended or fails, restart the task. According to the part information recorded in the task, the successfully uploaded parts will not be uploaded again, and other parts will be requested for uploading.
-  If you want to classify files, you can create folders and upload files to different folders. The procedure is as follows:

   #. Log in to OBS Browser.
   #. Click the bucket in which you want to create a folder. Click **Create Folder**.
   #. In the dialog box that is displayed, enter a folder name and click **OK**.
   #. In the displayed dialog box, click **OK** to close the dialog box.

Procedure
---------

#. Log in to OBS Browser.

#. Click the bucket to which the file or folder will be uploaded.

#. Click **Upload**. The **Upload Object** dialog box is displayed. For details, see :ref:`Figure 1 <obs_03_0024__fig1511502439>`.

   You can select either files or folders to upload. For details, see :ref:`4 <obs_03_0024__li1356818523426>` and :ref:`5 <obs_03_0024__li018223074620>`.

   .. _obs_03_0024__fig1511502439:

   .. figure:: /_static/images/en-us_image_0150044268.png
      :alt: **Figure 1** Uploading objects

      **Figure 1** Uploading objects

#. .. _obs_03_0024__li1356818523426:

   Click **Select File**. The local file browser dialog box is displayed. Select the file that you want to upload and click **Open**.

   You can upload a maximum of 500 files or folders at a time.

   .. note::

      If the files that you want to upload to OBS are stored in Microsoft OneDrive, it is recommended that the names of these files contain a maximum of 32 characters to ensure compatibility.

#. .. _obs_03_0024__li018223074620:

   Click **Select Folder**, select a folder, and click **OK**.

#. Select a storage class. If you do not specify a storage class, the objects you upload inherit the default storage class of the bucket.

#. Click **OK** to upload the file or folder.
