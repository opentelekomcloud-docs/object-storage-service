:original_name: en-us_topic_0045853663.html

.. _en-us_topic_0045853663:

Uploading a File
================

This section describes how to upload local files to OBS over the Internet. These files can be texts, images, videos, or any other type of files.

Limitations and Constraints
---------------------------

-  OBS Console allows you to upload files in a batch. Up to 100 files can be uploaded at a time, with the total size of no more than 5 GB. If the file size exceeds 5 GB, use OBS Browser or the multipart upload of OBS SDKs and APIs for upload.
-  If versioning is disabled and the name of a newly uploaded file is the same as that of a file in the bucket, the newly uploaded file automatically overwrites the existing file and does not retain the ACL information of the existing file. If the name of the newly uploaded folder is the same as that of a folder in the bucket, the two folders will be merged, and files in the new folder will overwrite namesake files in the old folder.
-  If versioning is enabled and the name of a newly uploaded file is the same as that of a file in the bucket, a new version is added to the existing file. For details about versioning, see :ref:`Versioning Overview <en-us_topic_0045853504>`.

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

Related Operations
------------------

You can specify its storage class when uploading an object or change its storage class after the object is uploaded. The procedure is as follows:

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.
#. In the navigation pane, click **Objects**.
#. Select the target object and choose **More** > **Change Storage Class** on the right.
#. Select the desired storage class and click **OK**.

.. note::

   -  Objects can be changed from **Standard** to **Warm** or **Cold** storage class, or from **Warm** to **Standard** or **Cold** storage class, but objects in **Cold** storage class must be restored before being changed to **Standard** or **Warm** storage class. Changing from **Warm** or **Cold** to other storage classes incurs restoration fees. Select an appropriate change option based on your actual needs.
   -  When the storage class is changed to **Cold**, the object restoration status changes to **Unrestored**.
   -  You can also configure a lifecycle rule to change the storage class of an object. For details, see :ref:`Configuring a Lifecycle Rule <obs_03_0335>`.

Follow-up Procedure
-------------------

You can click **Copy Path** on the right of an object to copy the path of the object.

You can share the path with other users. Then they open the bucket where the object is stored and enter the path in the search box to find the object.
