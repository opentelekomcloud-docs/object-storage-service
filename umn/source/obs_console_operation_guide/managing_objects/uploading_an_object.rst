:original_name: en-us_topic_0045853663.html

.. _en-us_topic_0045853663:

Uploading an Object
===================

This section describes how to upload local files to OBS over the Internet. These files can be texts, images, videos, or any other type of files.

Limitations and Constraints
---------------------------

-  OBS Console allows you to upload files in a batch. Up to 100 files can be uploaded at a time, with the total size of no more than 5 GB. If the file size exceeds 5 GB, use OBS Browser or the multipart upload of OBS SDKs and APIs for upload.
-  If versioning is disabled for your bucket and you upload a new file with the same name as the one you previously uploaded to your bucket, the new file automatically overwrites the previous file and does not retain its ACL information. If you upload a new folder using the same name that was used with a previous folder in the bucket, the two folders will be merged, and files in the new folder will overwrite namesake files in the previous folder.
-  After versioning is enabled for your bucket, if the new file you upload has the same name as the one you previously uploaded to the bucket, a new file version will be added in the bucket. For details, see :ref:`Versioning Overview <en-us_topic_0045853504>`.

Prerequisites
-------------

-  At least one bucket has been created.
-  If you want to classify files, you can create folders and upload files to different folders. For details about how to create a folder, see :ref:`Creating a Folder <obs_03_0316>`

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.

#. In the navigation pane, choose **Objects**.

#. Go to the folder to which objects are uploaded. Click **Upload Object**. The **Upload Object** dialog box is displayed.

   .. note::

      If the files that you want to upload to OBS are stored in Microsoft OneDrive, it is recommended that the names of these files contain a maximum of 32 characters to ensure compatibility.


   .. figure:: /_static/images/en-us_image_0153827167.png
      :alt: **Figure 1** Uploading objects

      **Figure 1** Uploading objects

#. Select a storage class. If you do not specify a storage class, the object you upload inherits the default storage class of the bucket.

   .. note::

      An object can have a different storage class from its bucket. You can specify a storage class for an object when uploading it, or you can change the object storage class after the object is uploaded.

#. Add a file or folder to be uploaded by dragging it to the **Upload Object** area.

   You can also click **add file** in the **Upload Object** area to select files.

#. (Optional) Select **KMS encryption** to encrypt the uploaded file. For details, see :ref:`Uploading an Object in Server-Side Encryption Mode <obs_03_0322>`.

   .. note::

      If the default encryption has been enabled for the bucket, uploaded objects are automatically encrypted.

#. Click **Upload**.

Related Operations
------------------

When uploading an object, you can specify a storage class for it. After the object is uploaded, you can also change its storage class. The procedure is as follows:

#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.
#. In the navigation pane, choose **Objects**.
#. Select the target object and choose **More** > **Change Storage Class** on the right.
#. Select the desired storage class and click **OK**.

.. note::

   -  Objects can be changed from Standard to Warm or Cold storage class, or from Warm to Standard or Cold storage class, but objects in Cold storage class must be restored before being changed to Standard or Warm storage class. Changing from Warm or Cold to other storage classes incurs restore fees. Select an appropriate change option based on your actual needs.
   -  When the storage class is changed to Cold, the object restore status changes to **Unrestored**.
   -  You can also configure a lifecycle rule to change the storage class of an object. For details, see :ref:`Configuring a Lifecycle Rule <obs_03_0335>`.

Follow-up Procedure
-------------------

You can click **Copy Path** on the right of an object to copy its path.

You can share the path with other users. Then they open the bucket where the object is stored and enter the path in the search box to find the object.
