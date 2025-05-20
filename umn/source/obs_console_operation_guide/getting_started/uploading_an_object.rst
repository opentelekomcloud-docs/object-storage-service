:original_name: obs_03_0307.html

.. _obs_03_0307:

Uploading an Object
===================

This section describes how to upload local files to OBS over the Internet. These files can be texts, images, videos, or any other type of files.

.. note::

   OBS Console allows you to upload files in a batch. Up to 100 files can be uploaded at a time, with the total size of no more than 5 GB. If the file size exceeds 5 GB, use OBS Browser or the multipart upload of OBS SDKs and APIs for upload.

   If versioning is disabled for your bucket and you upload a new file with the same name as the one you previously uploaded to your bucket, the new file automatically overwrites the previous one and does not retain its ACL information. If you upload a new folder using the same name that was used with a previous folder in the bucket, the two folders will be merged, and files in the new folder will overwrite those with the same name in the previous folder.

   After versioning is enabled for your bucket, if the new file you upload has the same name as the one you previously uploaded to the bucket, a new file version will be added in the bucket. For details about versioning, see :ref:`Versioning Overview <en-us_topic_0045853504>`.

Prerequisites
-------------

-  At least one bucket has been created.
-  If you want to classify files, you can create folders and upload files to different folders. For details, see :ref:`Creating a Folder <obs_03_0316>`.

Procedure
---------

#. In the bucket list, click the bucket you want to operate to go to the **Objects** page.

#. Go to the folder where you want to upload files and click **Upload Object**. The **Upload Object** dialog box is displayed.

#. Select a storage class. If you do not specify a storage class, the objects you upload inherit the default storage class of the bucket.

   .. note::

      An object can have a different storage class from its bucket. You can specify a storage class for an object when uploading it, or you can change the object storage class after the object is uploaded.

#. In the **Upload Object** area, drag and drop the files or folders you want to upload.

   You can also click **add files** to select files.

#. **Server-Side Encryption**: Choose **SSE-KMS** or **Disable**. For details, see :ref:`Enabling Server-Side Encryption When Uploading an Object <obs_03_0322>`.

   .. note::

      If the bucket has server-side encryption configured, the object you upload will inherit encryption from the bucket by default.

#. (Optional) To configure object tags, or metadata, click **Next: (Optional) Configure Advanced Settings**.

   Add metadata ContentDisposition, ContentLanguage, WebsiteRedirectLocation, ContentEncoding, or ContentType as needed. For more information, see :ref:`Object Metadata <en-us_topic_0049066876>`. Metadata is a set of name-value pairs. The metadata value cannot be left blank. You can add two or more metadata entries by clicking **Add**.

   Configuring tags: Tags are used to identify objects with tag keys and values. For details, see :ref:`Adding Tags to an Object <obs_41_0054>`.


   .. figure:: /_static/images/en-us_image_0000002235397602.png
      :alt: **Figure 1** Configuring metadata, WORM retention, or object tags

      **Figure 1** Configuring metadata, WORM retention, or object tags

#. Click **Upload**.
