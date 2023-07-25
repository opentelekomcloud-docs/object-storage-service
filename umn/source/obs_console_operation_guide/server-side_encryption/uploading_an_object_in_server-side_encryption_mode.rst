:original_name: obs_03_0322.html

.. _obs_03_0322:

Uploading an Object in Server-Side Encryption Mode
==================================================

OBS allows you to encrypt objects with server-side encryption so that the objects can be securely stored in OBS.

In a bucket with server-side encryption disabled, objects uploaded to it are not encrypted by default. You can configure server-side encryption when uploading objects. In a bucket with server-side encryption enabled, objects uploaded to it inherit the encryption settings of the bucket. You can also separately configure encryption for the objects.

Limitations and Constraints
---------------------------

-  The object encryption status cannot be changed.
-  A key in use cannot be deleted. Otherwise, the object encrypted with this key cannot be downloaded.
-  Objects encrypted on the server side cannot be shared.

Prerequisites
-------------

In the region where OBS is deployed, the **KMS Administrator** permission has been added to the user group. For details about how to add permissions, see the *IAM User Guide*.

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.

#. In the navigation pane, choose **Objects**.

#. Click **Upload Object**. The **Upload Object** dialog box is displayed.

#. Add the files to be uploaded.

#. Select **KMS encryption** and select a key that you have created on KMS.

   .. note::

      If the default encryption has been enabled for the bucket, uploaded objects are automatically encrypted.

   After **KMS encryption** is selected, **obs/default** is selected by default as the key for the encryption. You can also click **Create KMS Key** to switch to the KMS management console and create a customer master key. Then go back to OBS Console and select the key from the drop-down list.


   .. figure:: /_static/images/en-us_image_0130187638.png
      :alt: **Figure 1** Encrypting an object to be uploaded

      **Figure 1** Encrypting an object to be uploaded

#. Click **Upload**.

   After the object is uploaded successfully, you can view its encryption status in the object list.
