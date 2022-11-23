:original_name: obs_03_0307.html

.. _obs_03_0307:

Uploading a File
================

This section describes how to upload local files to OBS over the Internet. These files can be texts, images, videos, or any other type of files.

.. note::

   OBS Console allows you to upload files in a batch. Up to 100 files can be uploaded at a time, with the total size of no more than 5 GB. If the file size exceeds 5 GB, use OBS Browser or the multipart upload of OBS SDKs and APIs for upload.

   If versioning is disabled and the name of a newly uploaded file is the same as that of a file in the bucket, the newly uploaded file automatically overwrites the existing file and does not retain the ACL information of the existing file. If the name of the newly uploaded folder is the same as that of a folder in the bucket, the two folders will be merged, and files in the new folder will overwrite namesake files in the old folder.

   If versioning is enabled and the name of a newly uploaded file is the same as that of a file in the bucket, a new version is added to the existing file. For details about versioning, see :ref:`Versioning Overview <en-us_topic_0045853504>`.

Prerequisites
-------------

-  At least one bucket has been created.
-  If you want to classify files, you can create folders and upload files to different folders. For details about how to create a folder, see :ref:`Creating a Folder <obs_03_0316>`

Procedure
---------

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.

#. In the navigation pane, click **Objects**.

#. Go to the folder to which objects are uploaded. Click **Upload Object**. The **Upload Object** dialog box is displayed.

   .. note::

      If the files that you want to upload to OBS are stored in Microsoft OneDrive, it is recommended that the names of these files contain a maximum of 32 characters to ensure compatibility.


   .. figure:: /_static/images/en-us_image_0153827167.png
      :alt: **Figure 1** Uploading objects

      **Figure 1** Uploading objects

#. Select a storage class. If no storage class is selected, the file will inherit the storage class of the bucket.

#. Add a file or folder to be uploaded by dragging it to the Upload Object area.

   You can also click **add file** in the Upload Object area to select files.

#. **Optional**: Select KMS encryption to encrypt the uploaded file. For details, see :ref:`Uploading a File with Server-Side Encryption <obs_03_0322>`.

   .. note::

      If the default encryption is enabled for a bucket, uploaded objects are automatically encrypted.

#. Click **Upload**.
